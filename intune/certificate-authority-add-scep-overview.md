---
title: Külső hitelesítésszolgáltatók (CA) használata SCEP-beli Microsoft Intune - ban |} A Microsoft Docs
description: A Microsoft Intune a gyártó vagy külső hitelesítésszolgáltató (CA) segítségével kiadhatók tanúsítványok az SCEP protokollt használó mobileszközök is hozzáadhat. Ebben az áttekintő cikkben egy Azure Active Directory (Azure AD) alkalmazás ad engedélyeket a Microsoft Intune-nak tanúsítványok hitelesítésére. Ezután az SCEP-kiszolgáló beállítása következik a tanúsítványok kiadásához, az alkalmazás azonosítója, a hitelesítési kulcs és az AAD-alkalmazás bérlőazonosítója alapján.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0c5ddb32502aa15f6eaf8f5866772ecd32e970d4
ms.sourcegitcommit: 1b7ee2164ac9490df4efa83c5479344622c181b5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/08/2019
ms.locfileid: "67648455"
---
# <a name="add-partner-certification-authority-in-intune-using-scep"></a>Partner hitelesítésszolgáltató hozzáadása az Intune-ban SCEP protokollal

Az Intune használatához a külső hitelesítésszolgáltatók (CA). Külső hitelesítésszolgáltatók is hozzon létre új vagy megújított tanúsítványokat a mobileszközök az egyszerű tanúsítványigénylési protokoll (SCEP) használatával, és a Windows, iOS, Android és macOS-eszközt támogathat.

A funkció használata két részből áll: a nyílt forráskódú API-val kapcsolatos és az Intune-rendszergazdai feladatokból.

**1. rész – Nyílt forráskódú API használata**  
A Microsoft hozott létre API-t integrálja az Intune-nal. Ellenőrizheti az API-t, ha a tanúsítványok, sikeres vagy sikertelen az értesítéseket küldeni, és SSL, kifejezetten SSL szoftvercsatorna gyári segítségével kommunikál az Intune-ban.

Az API az [Intune SCEP API nyilvános GitHub-tárházban](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation) érhető el, ahonnan letöltheti és felhasználhatja saját megoldásaiban. Ez az API használata külső SCEP-kiszolgálók egyéni leellenőrizni futtatásához Intune-ban, mielőtt SCEP építi ki egy tanúsítványt az eszközökre.

Az [Intune-integráció SCEP-felügyeleti megoldásról](scep-libraries-apis.md) szóló témakör részletesebben is leírja az API használatát, metódusait és az elkészített megoldások tesztelését.

**2. rész – Az alkalmazás és profil létrehozása**  
Azure Active Directory-alkalmazás használatakor az eszközökről érkező SCEP-kérelmek kezelésének jogosultságai az Intune-nak delegálhatók. Az Azure AD-alkalmazás a fejlesztő által létrehozott API-megoldásban használt alkalmazásazonosítót és hitelesítési kulcsot is tartalmazza. A rendszergazdák majd létrehozása és üzembe helyezése a SCEP-tanúsítványok profilokat az Intune-nal, és jelentéseket tekintheti meg az eszközön a telepítés állapota.

Ez a cikk rendszergazdai szempontból tekinti át ezt a funkciót, beleértve az Azure AD-alkalmazás létrehozását is.

## <a name="overview"></a>Áttekintés

A következő lépések áttekintést adnak a SCEP-tanúsítványok Intune-beli kiadásáról:

1. Az Intune-ban egy rendszergazda létrehoz egy SCEP-tanúsítványprofilt, majd a profil céljaként felhasználókat vagy eszközöket jelöl ki.
2. Az eszköz bejelentkezik az Intune-ba.
3. Az Intune létrehoz egy egyedi SCEP ellenőrző kérdést. További integritás-ellenőrző információkat is megad, például a várt tárgyat és SAN-t.
4. Az Intune az ellenőrző kérdést és az integritás-ellenőrző információkat is titkosítja és aláírja, majd az SCEP-kérelemmel együtt elküldi ezt az információt az eszköznek.
5. Az eszköz generál egy tanúsítvány-aláírási kérelmet (CSR) és egy nyilvános/titkos kulcspárt az eszközön az Intune-ból leküldött SCEP-tanúsítványprofil alapján.
6. A CSR és a titkosított/aláírt ellenőrző kérdés van elküldve a külső SCEP-kiszolgálói végponthoz.
7. Az SCEP-kiszolgáló elküldi a CSR-t és az ellenőrző kérdést az Intune-nak. Az Intune ekkor ellenőrzi az aláírást, visszafejti a tartalmat és összeveti a CSR-t az integritás-ellenőrző információval.
8. Az Intune választ küld az SCEP-kiszolgálónak, amelyben tudatja, hogy az ellenőrző kérdésen alapuló hitelesítés sikeres volt vagy sem.  
9. Ha az ellenőrző kérdésen alapuló hitelesítés sikeres, az SCEP-kiszolgáló kiadja a tanúsítványt az eszköznek.

Az alábbi diagram részletesen bemutatja a külső SCEP és az Intune integrációjának folyamatát:

![Külső hitelesítésszolgáltató SCEP-jének együttműködése a Microsoft Intune-nal](./media/scep-certificate-vendor-integration.png)

## <a name="set-up-third-party-ca-integration"></a>Külső hitelesítésszolgáltatóval való integráció beállítása

### <a name="validate-third-party-certification-authority"></a>Külső hitelesítésszolgáltató ellenőrzése

Külső hitelesítésszolgáltatók Intune-nal való integrálása előtt győződjön meg arról, hogy az igénybe vett hitelesítésszolgáltató támogatja az Intune-t. A [Külső hitelesítésszolgáltató partnerek](#third-party-certification-authority-partners) című szakasz (ebben a cikkben) tartalmazza ezek felsorolását. Alaposabban is tájékozódhat hitelesítésszolgáltatója útmutatója alapján. A hitelesítésszolgáltatók saját megvalósítási módjukra vonatkozó telepítési utasításokat is megadhatnak.

### <a name="authorize-communication-between-ca-and-intune"></a>A hitelesítésszolgáltató és az Intune közötti kommunikáció engedélyezése

Ahhoz, hogy egy külső SCEP-kiszolgáló egyéni kérdésen alapuló ellenőrzést végezhessen az Intune-nal, készítsen egy alkalmazást az Azure AD-ban. Ez az alkalmazás delegált jogosultságokat ad az Intune-nak az SCEP-kérelmek ellenőrzéséhez.

Ehhez mindenképpen rendelkeznie kell az Azure AD-alkalmazás regisztrálásához szükséges engedélyekkel. Lásd: [szükséges engedélyek](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions), az Azure AD dokumentációjában.

#### <a name="create-an-application-in-azure-active-directory"></a>Alkalmazás létrehozása az Azure Active Directoryban  

1. Az a [az Azure portal](https://portal.azure.com), lépjen a **Azure Active Directory** > **Alkalmazásregisztrációk**, majd válassza ki **új regisztrációs**.  

2. Az a **alkalmazás regisztrálása** csoportjában adja meg a következő adatokat:  
   - Az a **neve** területén adjon meg egy kifejező alkalmazásnevet.  
   - Az a **támogatott fióktípusok** szakaszban jelölje be **bármely szervezeti directory fiókok**.  
   - A **átirányítási URI-t**, hagyja meg az alapértelmezett Web, és adja meg a bejelentkezési URL-címet a külső SCEP-kiszolgáló.  

3. Válassza ki **regisztrálása** hozhat létre az alkalmazást, és az új alkalmazáshoz – Áttekintés lap megnyitásához.  

4. Az alkalmazás **áttekintése** lapon, másolja a **Alkalmazásazonosítót (ügyfél)** értékét, és jegyezze fel későbbi használat céljából. Ezt az értéket később még szüksége lesz.  

5. A navigációs ablaktáblán az alkalmazás Ugrás **tanúsítványok és titkos kulcsok** alatt **kezelése**. Válassza ki a **új titkos ügyfélkulcsot** gombra. Adjon meg egy értéket a leírás, az egyik lehetőséget sem **lejárat**, majd válassza **Hozzáadás** létrehozni egy *érték* a titkos. 
   > [!IMPORTANT]  
   > Mielőtt kilép az oldalról, másolja az értéket a titkos, és jegyezze fel a harmadik fél hitelesítésszolgáltató megvalósításra későbbi használatra. Ez az érték nem jelenik meg újból. Mindenképpen olvassa el a harmadik fél hitelesítésszolgáltató hogyan szeretnének az alkalmazás Azonosítóját, a hitelesítési kulcsot és a konfigurált bérlő azonosítója a útmutatást.  

6. Rekord a **Bérlőazonosító**. A Bérlőazonosító a tartomány szöveg után a @ karakter a fiókjában. Például, ha a fiókja *admin@name.onmicrosoft.com* , akkor a bérlő Azonosítóját **name.onmicrosoft.com**.  

7. Lépjen a navigációs ablaktáblán az alkalmazás **API-engedélyek** alatt **kezelés**, majd válassza ki **adjon hozzá egy engedélyt**.  

8. Az a **kérelem API-engedélyek** lapon jelölje be **Intune**, majd válassza ki **Alkalmazásengedélyek**. Jelölje be a **scep_challenge_provider** (SCEP leellenőrizni).  

   Válassza ki **engedélyek hozzáadása** a konfiguráció mentéséhez.  

9. Továbbra is a **API-engedélyek** lapon, és válassza ki **adja meg a Microsoft a rendszergazdai jóváhagyás**, majd válassza ki **Igen**.  
   
   Az Azure ad-ben az alkalmazás regisztrációs folyamat befejeződött.





### <a name="configure-and-deploy-a-scep-certificate-profile"></a>SCEP-tanúsítványprofil konfigurálása és telepítése
Rendszergazdaként hozzon létre egy felhasználóknak vagy eszközöknek szánt SCEP-tanúsítványprofilt. Ezt követően végezze el a profil hozzárendelését.

- [SCEP-tanúsítványprofil létrehozása](certificates-scep-configure.md#create-a-scep-certificate-profile)

- [A tanúsítványprofil felhasználókhoz vagy eszközökhöz rendelése](certificates-scep-configure.md#assign-the-certificate-profile)

## <a name="removing-certificates"></a>Tanúsítványok eltávolítása

Ha törli az eszköz regisztrációját vagy teljes tartalmát, a tanúsítványok törölve lesznek. A tanúsítványok nem lesznek visszavonva.

## <a name="third-party-certification-authority-partners"></a>Külső hitelesítésszolgáltató partnerek
Az alábbi külső hitelesítésszolgáltatók támogatják az Intune-t:

- [Entrust Datacard](https://info.entrustdatacard.com/pki-eval-tool)
- [EJBCA GitHub nyílt forráskódú verzió](https://github.com/agerbergt/intune-ejbca-connector)
- [EverTrust](https://evertrust.fr/en/products/)
- [GlobalSign](https://downloads.globalsign.com/acton/attachment/2674/f-6903f60b-9111-432d-b283-77823cc65500/1/-/-/-/-/globalsign-aeg-microsoft-intune-integration-guide.pdf)
- [IDnomic](https://www.idnomic.com/)
- [Sectigo](https://sectigo.com/products)
- [DigiCert](https://knowledge.digicert.com/tutorials/microsoft-intune.html)
- [SCEPman](https://azuremarketplace.microsoft.com/marketplace/apps/gluckkanja.scepman)

Ha Ön a terméke Intune-nal való integrálása iránt érdeklődő külső hitelesítésszolgáltatót képvisel, tekintse át az API-val kapcsolatos útmutatót:

- [Intune SCEP API GitHub-tárház](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Intune SCEP API útmutató külső hitelesítésszolgáltatóknak](scep-libraries-apis.md)

## <a name="see-also"></a>Lásd még:

- [Tanúsítványprofilok konfigurálása](certificates-scep-configure.md)
- [Intune SCEP API GitHub-tárház](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Intune SCEP API útmutató külső hitelesítésszolgáltatóknak](scep-libraries-apis.md)

---
title: Tanúsítványprofil létrehozása az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Az eszközökhöz SCEP- vagy PKCS-tanúsítványkörnyezet konfigurálásával, a nyilvános tanúsítvány exportálásával, a profil az Azure Portalon való létrehozásával, majd a SCEP vagy PKCS a tanúsítványprofilhoz való hozzárendelésével adhat hozzá tanúsítványprofilokat a Microsoft Intune-ban, az Azure Portalon
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 80be1d39d9a562dbc13b9384c6256eb02c9ef50e
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67530557"
---
# <a name="configure-a-certificate-profile-for-your-devices-in-microsoft-intune"></a>Eszközök tanúsítványprofiljainak konfigurálása a Microsoft Intune-ban

A céges erőforrásokhoz VPN-, Wi-Fi- vagy e-mail-profilok segítségével adhat hozzáférést a felhasználóknak. Tanúsítványok használatával a kapcsolatok hitelesítésére is van lehetőség. Tanúsítványok használatakor a végfelhasználóknak nem kell megadniuk a felhasználóneveket és a jelszavakat a hitelesítéshez.

Az Intune-nal hozzárendelheti ezeket a tanúsítványokat a felügyelt eszközökhöz. Az Intune a következő tanúsítványtípusok eszközökhöz rendelését és felügyeletét támogatja:

- SCEP protokoll
- PKCS#12 (vagy PFX)

Ezen tanúsítványtípusok mindegyikének megvannak a maga előfeltételei és infrastrukturális követelményei.


## <a name="overview"></a>Áttekintés

1. Ellenőrizze, hogy be van-e állítva a megfelelő tanúsítványinfrastruktúra. [SCEP-tanúsítványokat](certificates-scep-configure.md) és [PKCS-tanúsítványokat](certficates-pfx-configure.md) használhat.

2. Telepítsen egy főtanúsítványt vagy köztes hitelesítésszolgáltatói tanúsítványt minden eszközön, hogy az eszköz felismerje a hitelesítésszolgáltató (CA) érvényességét. A tanúsítvány telepítéséhez, létrehozása és hozzárendelése egy **megbízhatótanúsítvány-profil** adott eszközön. A profil hozzárendelésekor az Intune-nal felügyelt eszközök lekérik és megkapják a főtanúsítványt. Mindegyik platformhoz különálló profilt kell létrehoznia. A megbízható tanúsítványprofilok a következő platformokhoz érhetők el:

    - iOS 8.0 és újabb verziók
    - macOS 10.11 és újabb verziók
    - Android 4.0 és újabb verziók
    - Vállalati Android  
    - Windows 8.1 és újabb
    - Windows Phone 8.1 és újabb verziók
    - Windows 10 és újabb

    > [!NOTE]  
    > A tanúsítványprofilok nem támogatottak, amelyeken *dedikált eszközök az Android Enterprise*.

3. Hozza létre a VPN-, Wi-Fi- és e-mail-hozzáférés hitelesítésére szolgáló tanúsítványprofilokat. A következő típusok közül a különböző platformokhoz érhetők el:  

   | Platform     |PKCS-tanúsítvány|SCEP-tanúsítvány| PKCS importált tanúsítvány | 
   |--------------|----------------|----------------|-------------------|
   | Android                | Igen    | Igen    | Igen    |
   | Vállalati Android     | Igen    | Igen    | Igen    |
   | iOS                    | Igen    | Igen    | Igen    |
   | macOS                  |        | Igen    | Igen    |
   | Windows Phone 8.1      |        | Igen    | Igen    |
   | Windows 8.1 és újabb  |        | Igen    |        |
   | Windows 10 és újabb   | Igen    | Igen    | Igen    |

   Mindegyik eszközplatformhoz külön profilt kell létrehoznia. Létrehozásakor társítsa a profilt a már létrehozott megbízható főtanúsítvány-profilhoz.

### <a name="further-considerations"></a>További szempontok

- Ha nem rendelkezik vállalati hitelesítésszolgáltatóval, létre kell hoznia egyet
- SCEP-profilok használatakor konfigurálnia kell egy NDES-kiszolgálót is
- Mind az SCEP-, mind a PKCS-profilok használatához le kell töltenie és konfigurálnia kell a Microsoft Intune Tanúsítvány-összekötőt


## <a name="step-1-configure-your-certificate-infrastructure"></a>1\. lépés: A tanúsítványinfrastruktúra konfigurálása

Segítség az egyes tanúsítványprofil-típusok infrastruktúrájának konfigurálásához az alábbi cikkekben talál:

- [SCEP-tanúsítványok konfigurálása és kezelése az Intune-nal](certificates-scep-configure.md)
- [PKCS-tanúsítványok konfigurálása és kezelése az Intune-nal](certficates-pfx-configure.md)


## <a name="step-2-export-your-trusted-root-ca-certificate"></a>2\. lépés: A megbízható legfelső szintű hitelesítésszolgáltató tanúsítványának exportálása

Exportálja a megbízható legfelső szintű hitelesítésszolgáltató (CA) tanúsítványát nyilvános, (.cer) kiterjesztésű fájlként a kibocsátó hitelesítésszolgáltatóról vagy a vállalati hitelesítésszolgáltatóban megbízó bármelyik eszközről. A titkos kulcsot (.pfx) ne exportálja.

Ezt a tanúsítványt a megbízható tanúsítványprofil konfigurálásakor kell importálnia.

## <a name="step-3-create-trusted-certificate-profiles"></a>3\. lépés: A megbízható tanúsítványprofilok létrehozása
Ahhoz, hogy SCEP- vagy PKCS-tanúsítványprofilt hozhasson létre, először létre kell hoznia egy megbízható tanúsítványprofilt. Minden mobileszközplatformhoz külön megbízható tanúsítványprofil, illetve és SCEP- vagy PKCS-profil szükséges. A megbízható tanúsítványok létrehozása az összes eszközplatformon hasonlóan zajlik.

1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Válassza az **Eszközkonfiguráció** > **Kezelés** > **Profilok** > **Profil létrehozása** lehetőséget.
4. Adja meg a megbízható tanúsítványprofil **nevét** és **leírását**.
5. Válassza ki a megbízható tanúsítvány eszközplatformját a **Platform** legördülő listából. A választható lehetőségek:

    - **Android**
    - **Android Enterprise**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 és újabb**
    - **Windows 10 és újabb**

6. A **Profil típusa** legördülő listában válassza a **Megbízható tanúsítvány** lehetőséget.
7. Keresse meg a tanúsítvány mentett [2. lépés: A megbízható legfelső szintű hitelesítésszolgáltató tanúsítványának exportálása](#step-2-export-your-trusted-root-ca-certificate), majd **OK**.
8. Válassza ki – csak a Windows 8.1- és Windows 10-eszközök esetében – a megbízható tanúsítvány céltárolóját a **Céltároló** mezőben, a következő lehetőségek közül:

    - **Számítógép tanúsítványtárolója – fő**
    - **Számítógép tanúsítványtárolója – köztes**
    - **Felhasználói tanúsítványtároló – köztes**

9. Ha elkészült, válassza az **OK** gombot, lépjen vissza a **Profil létrehozása** panelre, és válassza a **Létrehozás** gombot.

Ekkor létrejön a profil, és megjelenik a listán. Ha csoportokhoz szeretné hozzárendelni a profilt, tekintse meg az [eszközprofilok hozzárendelését](device-profile-assign.md) ismertető cikket.

   >[!NOTE]
   > Az Android-eszközök megjeleníthetnek egy üzenetet arról, hogy egy harmadik fél megbízható tanúsítványt telepített.

## <a name="step-4-create-scep-or-pkcs-certificate-profiles"></a>4\. lépés: SCEP- vagy PKCS-tanúsítványprofilok létrehozása

Tekintse meg a következő cikkek segítséget konfigurálásához és eszközökhöz rendeléséhez az egyes tanúsítványprofil-típusok valamelyikét:

- [SCEP-tanúsítványok konfigurálása és kezelése az Intune-nal](certificates-scep-configure.md)
- [PKCS-tanúsítványok konfigurálása és kezelése az Intune-nal](certficates-pfx-configure.md)

Miután létrehozott egy megbízható hitelesítésszolgáltatói tanúsítványprofilt, létre kell hoznia a használni kívánt platformok SCEP- vagy PKCS-tanúsítványprofilját is. SCEP-tanúsítványprofil létrehozásakor adjon meg egy ugyanarra a platformra vonatkozó megbízható tanúsítványprofilt. Ez a művelet összeköti a két tanúsítványprofilt, de az egyes profilok hozzárendelését külön-külön kell elvégeznie.

## <a name="next-steps"></a>További lépések
[Eszközprofilok hozzárendelése](device-profile-assign.md)  
[S/MIME használata e-mailek aláírásához és titkosításához](certificates-s-mime-encryption-sign.md)  
[Külső hitelesítésszolgáltató használata](certificate-authority-add-scep-overview.md)

## <a name="see-also"></a>Lásd még:

[A Microsoft Intune tanúsítványprofiljai segítségével használható hibaelhárítási NDES-konfiguráció](https://support.microsoft.com/help/4459540)

[Hibaelhárítási SCEP tanúsítványprofilok azon központi telepítését a Microsoft Intune-ban](https://support.microsoft.com/help/4457481)

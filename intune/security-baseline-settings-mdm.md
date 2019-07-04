---
title: Az Intune biztonsági alapterveket beállítások Windows 10 rendszerhez
titleSuffix: Microsoft Intune
description: Az Intune biztonsági alapterv beállításainak kezelése Windows 10-es
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/20/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8fa5589f62900027b90659b8f570e7caa10b1cd8
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/03/2019
ms.locfileid: "67549064"
---
# <a name="mdm-security-baseline-settings-for-intune"></a>Mobileszköz-kezelési biztonsági Alapterv beállítások az Intune-hoz  

A mobileszköz-kezelési biztonsági Alapterv beállítások megjelenítéséhez a Windows 10 rendszerű eszközökhöz a Microsoft Intune által támogatott vagy újabb. Ez a alapvető beállítások alapértelmezett értékeit jelölik az ajánlott konfiguráció alkalmazható eszközökhöz, és nem egyeznek meg a referenciakonfiguráció alapértelmezett értékeket a többi biztonsági előírások.  

A legújabb alapkonfigurációt van **MDM biztonsági alapterv Spring 2019 frissítés (19 órával 1)**  

Ez a alapvető legújabb verziója megváltozott a korábbi verzióról kapcsolatos további információkért lásd: [változások az új sablon](#whats-changed-in-the-new-template).  

> [!NOTE]  
> A 2019. június, az előzetes verzió MDM biztonsági alapkonfiguráció megjelenésével értéke le lett cserélve a *Spring 2019 frissítés (19 órával 1) a mobileszköz-kezelési biztonsági alapterv* sablon, amely generaly (nem előzetes verzióban érhető el). Elérhetősége előtt létrehozott profilok a *Spring 2019 frissítés (19 órával 1) a mobileszköz-kezelési biztonsági alapterv* alapkonfiguráció megfelelően a beállításokat és a mobileszköz-kezelési biztonsági alapterv Spring 2019 frissítés (19 órával 1 szereplő értékek nem frissítése ) verziója.  Bár az előzetes verzió sablon alapján új profilt nem hozható létre, szerkesztheti, és továbbra is használhatja a korábban létrehozott profilok –, amelyek az előzetes verzió sablon alapján.   
  
Biztonsági alapterv használatával az Intune-nal kapcsolatos további információkért lásd: [használja a biztonsági előírások](security-baselines.md).  


   
## <a name="above-lock"></a>Zárolási felett  
További információkért lásd: [házirend CSP - AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) a Windows dokumentációjában.  

- **Bejelentési értesítések megjelenítésének letiltása**  
  Ez a házirend-beállítással megakadályozhatja, hogy a zárolási képernyőn megjelenő alkalmazás értesítéseit. Ha ez a szabályzatbeállítás engedélyezi, nem alkalmazásbeli értesítések jelennek meg a zárolási képernyőn. Ha letiltja vagy nem konfigurálja ezt a beállítást, felhasználók eldönthetik, hogy mely alkalmazások jelenít meg értesítéseket, a zárolási képernyőn.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067101)  

  **Alapértelmezett**: Igen  

- **Hangvezérelt alkalmazások zárolt képernyőn aktiválása**  

  **Alapértelmezett**: Letiltva

## <a name="app-runtime"></a>Alkalmazás-modul    
További információkért lásd: [házirend CSP - AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) a Windows dokumentációjában.  

- **Windows Store apps esetén nem kötelező Microsoft-fiókok**  
  Ez a házirend-beállítással szabályozhatja, hogy Microsoft-fiókok megadása nem kötelező, jelentkezzen be a fiók szükséges Windows Store-alkalmazások. Ez a szabályzat csak az azt támogató Windows Store apps van hatással. Ha ez a szabályzatbeállítás engedélyezi, amely általában egy Microsoft-fiókkal való bejelentkezéshez szükséges Windows Store apps segítségével a felhasználók ehelyett jelentkezzen be vállalati fiók. Ha letiltja vagy nem konfigurálja ezt a beállítást, felhasználók Microsoft-fiókkal kell bejelentkeznie.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067104)  
  
  **Alapértelmezett**: Enabled  

## <a name="application-management"></a>Alkalmazáskezelés   
További információkért lásd: [házirend CSP - ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) a Windows dokumentációjában.  

- **Telepítések letiltása felhasználói vezérlése**  
  A házirend-beállítás lehetővé teszi a felhasználók számára, amely jellemzően az csak a rendszergazdák számára érhető el a telepítés beállításainak módosításához. Ha ez a szabályzatbeállítás engedélyezi, a Windows Installer biztonsági funkcióit is telepítővarázslója kihagyja. Lehetővé teszi a telepítés befejezéséhez, ellenkező esetben kellene lennie le biztonság megsértése miatt. Ha letiltja vagy nem konfigurálja ezt a beállítást, a biztonsági funkciók a Windows Installer módosításának megakadályozása például adja meg a könyvtárat, amelyhez a fájlok települnek a rendszergazdák számára fenntartott telepítési beállításait. Windows Installer azt észleli, hogy egy csomag lehetővé teszi a felhasználó egy védett beállítást módosíthatja, ha leállítja a telepítést, és megjelenít egy üzenetet. Ezek a biztonsági funkciók csak ha a telepítési program fut a biztonsági környezet, amelyben a felhasználó nem jogosult könyvtárak hozzáféréssel rendelkezik. A házirend-beállítás kevésbé korlátozó környezetekhez lett kialakítva. A telepítőprogram, amely megakadályozza, hogy a szoftver telepítése folyamatban hibák megkerülésére használható.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067060)  

  **Alapértelmezett**: Igen

- **Emelt szintű jogosultságokkal letiltása az MSI-alkalmazások telepítésére**  
  A házirend-beállítás a Windows Installer emelt jogosultsági szintű használata, amikor telepíti a rendszer minden program irányítja.  
  - *Ha ez a szabályzatbeállítás engedélyezi*, jogosultságok bővítve lettek a programok. Ezek a jogosultságok általában a felhasználó (Asztalon felkínált), a számítógép (telepített automatikusan) f rendelt rendelt, vagy a Vezérlőpult Programok telepítése és a rendelkezésre bocsátott programok számára vannak fenntartva. Ez a profil-beállítás lehetővé teszi a felhasználóknak, hogy a felhasználó előfordulhat, hogy nincs engedélye megtekintése és módosítása, például a könyvtárak rendkívül korlátozott számítógépeken könyvtárak hozzáférést igénylő programok telepítése.
  - *Ha letiltja vagy nem konfigurálja a házirend-beállítás*, a rendszer az aktuális felhasználói engedélyek vonatkozik, amikor egy rendszergazda nem terjesztheti vagy ajánlat programok telepíti. Megjegyezés: A házirend-beállítás jelenik meg, a számítógép-konfiguráció és a felhasználói tartalmazó mappákat is. Ahhoz, hogy a házirend-beállítás érvényes, engedélyeznie kell azt mindkét mappában. Figyelmeztetés: Gyakorlott felhasználók kihasználhatja az engedélyeket a házirend-beállítás jogosultságait módosíthatja, és korlátozott fájlok és mappák állandó hozzáférést biztosít. Vegye figyelembe, hogy a házirend-beállítás felhasználói konfiguráció verziója nem garantált, hogy biztonságos legyen.  
  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067134)    

  **Alapértelmezett**: Igen

- **Játékvideó letiltása (csak asztali verzió)**  
  Annak konfigurálása, rögzítése és közvetítése játékok engedélyezett-e.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067056)  
  
  **Alapértelmezett**: Igen  

## <a name="auto-play"></a>Automatikus lejátszás   
További információkért lásd: [házirend CSP - lejátszás](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) a Windows dokumentációjában.  

- **Automatikus lejátszás alapértelmezett automatikus futtatási viselkedés**  
  Ez a beállítás hatással van az alapértelmezett viselkedést automatikus futtatási parancsok. Automatikus futtatási parancsok autorun.inf fájlokban van tárolva, és programokat vagy más módon indíthatja el. Amikor *engedélyezve*, a rendszergazdák módosíthatják az alapértelmezett automatikus futtatási viselkedés egy eszközön, amelyen a Windows Vista vagy újabb. Viselkedés értékre lehet beállítani: a) teljesen automatikus futtatási parancsok letiltja, vagy (b) térhet vissza a korábbi Windows Vista működése automatikusan a futtatási parancs végrehajtása. Ha a beállítása *letiltott* vagy *nincs konfigurálva*, Windows Vista rendszerű eszközök, vagy később kérdezzen rá, hogy a felhasználó egy automatikus futtatási parancs futtatva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067133)       
  
  **Alapértelmezett**: Nem hajtható végre  
  
- **Automatikus lejátszás üzemmódban**  
  A házirend-beállítás lehetővé teszi, hogy az automatikus lejátszás szolgáltatás kikapcsolása. Automatikus lejátszás megkezdi az adatok egy meghajtóról, amint helyezze adathordozót a meghajtóba. Ennek eredményeképpen a telepítőfájl a programok és a music hanganyag azonnali indítása. Windows XP SP2-t előtt automatikus lejátszás a cserélhető meghajtók, például a hajlékonylemez-meghajtó (de nem a CD-ROM-meghajtó) és a hálózati meghajtókon lévő alapértelmezés szerint le van tiltva. Windows XP SP2 verziótól kezdődően automatikus lejátszás engedélyezve van a cserélhető meghajtók, például a Zip-meghajtók és a egy USB-háttértár eszközök. Ha ez a szabályzatbeállítás engedélyezi, az automatikus lejátszás, a CD-ROM-ról és a cserélhető adathordozó meghajtó le van tiltva vagy le van tiltva az összes meghajtón. A házirend-beállítás letiltja az automatikus lejátszás további típusú meghajtókon. Ez a beállítás bekapcsolása a meghajtón, amelyen le van tiltva alapértelmezés szerint nem használható. Ha letiltja vagy nem konfigurálja ezt a beállítást, az automatikus lejátszás engedélyezve van. Megjegyezés: A házirend-beállítás jelenik meg a számítógép konfigurációja-és felhasználói konfigurációt. Ha a házirend-beállításokat ütközés lép fel, akkor a házirend-beállítás a számítógép konfigurációja élvez a házirend-beállítás a felhasználói konfigurációt.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2066793)  
  
  **Alapértelmezett**: Letiltva

- **Automatikus lejátszás a nem mennyiségi eszközök letiltása**  
  A házirend-beállítás tiltja a lejátszás MTP eszközökhöz, például fényképezőgépek vagy telefonok. Ha ez a szabályzatbeállítás engedélyezi, az automatikus lejátszás MTP eszközök például fényképezőgépek vagy telefonok esetén nem engedélyezett. Ha letiltja vagy nem konfigurálja ezt a beállítást, az automatikus lejátszás nem mennyiségi eszközök engedélyezve van.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067106)    
  
  **Alapértelmezett**: Enabled  

## <a name="bitlocker"></a>A BitLocker    
További információkért lásd: [házirend CSP - Bitlocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) a Windows dokumentációjában.  

- **Bit széfjét a cserélhető meghajtót házirend**  
  A titkosítási módszer vezérlőelemet, és cipher erőssége a házirend-beállítás szolgál. Az a szabályzat határozza meg, hogy a titkosítás a BitLocker titkosítási használó erősségét. Vállalatok előfordulhat, hogy kívánják vezérelni a titkosítás szintjét, a biztonság fokozása érdekében (AES-256-ot az AES-128-nál nagyobb). Ha engedélyezi ezt a beállítást, konfigurálhat egy titkosítási algoritmus és a fő erőssége a rögzített adatmeghajtók, operációsrendszer-meghajtók és a cserélhető adatmeghajtók egy külön-külön fogja. A rögzített és operációs rendszert tartalmazó meghajtókon azt javasoljuk az XTS-AES algoritmus használata. A cserélhető meghajtók használjon AES-CBC 128 bites vagy AES-CBC 256 bites Ha a meghajtó eszközöktől, amelyek nem futnak Windows 10-es, 1511-es vagy újabb verzióját használja. A titkosítási mód módosítása nem befolyásolja, ha a meghajtó már titkosítva van, vagy ha a titkosítás folyamatban van. Ebben az esetben figyelmen kívül ezt a beállítást.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067140) 

  Bit széfjét a cserélhető meghajtót házirend konfigurálja a következő beállítást:

    - **Titkosítás megkövetelése az írási hozzáférés**  
      **Alapértelmezett**: Igen  
  

## <a name="browser"></a>Browser  
További információkért lásd: [házirend CSP - böngésző](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) a Windows dokumentációjában.  

- **A Microsoft Edge SmartScreen megkövetelése**  
  A Microsoft Edge felhasználók megvédeni a potenciális adathalászattal és a kártevő szoftverek alapértelmezés szerint a Windows Defender SmartScreen (bekapcsolva) használja. Továbbá alapértelmezés szerint felhasználók nem tiltható le (kapcsolja ki) a Windows Defender SmartScreen. A szabályzat engedélyezése a Windows Defender SmartScreen kikapcsolja, és megakadályozza, hogy a felhasználók ne tudják bekapcsolni a. Ne konfigurálja ezt a házirendet, hogy a felhasználó, hogy a Windows defender SmartScreen engedélyezése vagy letiltása.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067029)   
  
  **Alapértelmezett**: Igen  
  
- **Rosszindulatú webhelyelérés letiltása**  
  Alapértelmezés szerint a Microsoft Edge lehetővé teszi a felhasználók kihagyhatják (figyelmen kívül hagyása) a Windows Defender SmartScreen-figyelmeztetések potenciálisan rosszindulatú webhelyekről, lehetővé téve számukra az, hogy a hely. Az ehhez a szabályzathoz, konfigurálhatja a Microsoft Edge megakadályozza, hogy a felhasználók a figyelmeztetések mellőzése letiltják őket a továbbra is a hely.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067040)   
  
  **Alapértelmezett**: Igen  
  
- **Ellenőrizetlen fájlletöltés letiltása**  
  Alapértelmezés szerint a Microsoft Edge lehetővé teszi a felhasználók kihagyhatják (figyelmen kívül hagyása) a Windows Defender SmartScreen-figyelmeztetések potenciálisan kártékony fájlokkal, lehetővé teheti, hogy továbbra is a nem ellenőrzött fájlok letöltésével kapcsolatos. E szabályzat engedélyezésével megakadályozza, hogy felhasználók letiltják őket a nem ellenőrzött fájlok letöltése a figyelmeztetések mellőzése.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067023)  
  
  **Alapértelmezett**: Igen  
  
- **Jelszókezelő letiltása**  
  Alapértelmezés szerint a Microsoft Edge jelszókezelő automatikusan használja, így a felhasználók helyi manager jelszavak. Jelszókezelő használatával a Microsoft Edge letiltja ezt a szabályzatot korlátozza. Ne konfigurálja ezt a házirendet, ha azt szeretné, hogy a felhasználók menteni, és jelszavak használatával helyben jelszókezelő kezelése.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067128)  
  
  **Alapértelmezett**: Igen  
  
- **Tanúsítvány hiba felülbírálások megakadályozása**  
  A házirend-beállítás megakadályozza, hogy a felhasználó Secure Sockets Layer/Transport Layer Security (SSL/TLS) tanúsítványt hibák működését zavaró, az Internet Explorer programban (mint például a "lejárt", "Visszavonva" vagy "neve tér" hibák) böngészés figyelmen kívül hagyásával. Ha ez a szabályzatbeállítás engedélyezi, a felhasználó böngészés nem folytatható. Ha letiltja vagy nem konfigurálja ezt a beállítást, a felhasználó választhat figyelmen kívül a hitelesítési hibák, és folytassa a böngészést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067126)  
  
  **Alapértelmezett**: Igen  

## <a name="connectivity"></a>Kapcsolat  
További információkért lásd: [házirend CSP - kapcsolat](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) a Windows dokumentációjában.  

- **Közzététel a weben és internetes rendelés varázsló blokk internetes letöltés**  
  A házirend-beállítás megadja a Windows letöltse-e a webes közzététel és az Internetes rendelés varázsló szolgáltatók listáját. Ezek a varázslók engedélyezése a felhasználók számára, például az online tárhelyen és photographic nyomtatási szolgáltatásokat nyújtó cégek listájából válassza ki. Alapértelmezés szerint a Windows a beállításjegyzékben megadott szolgáltatók mellett egy Windows webhelyéről letöltött szolgáltatókat jelenít meg. Ha ez a szabályzatbeállítás engedélyezi, Windows nem sikerül letölteni a szolgáltatók és csak a helyi beállításjegyzékben jelennek meg a gyorsítótárba helyezett szolgáltatók. Ha letiltja vagy nem konfigurálja ezt a beállítást, szolgáltatók listáját tölti le, amikor a felhasználó használja a webes közzététel vagy az Internetes rendelés varázsló. További információkért, amely tartalmazza a részleteket a szolgáltatói meghatározásáról a beállításjegyzékben dokumentációjában, a webes közzététel és az Internetes rendelés varázsló számára.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067136)  
  
  **Alapértelmezett**: Enabled  

- **Nyomtatóillesztők HTTP protokollon keresztüli letöltésének letiltása**  
  A házirend-beállítás megadja, hogy az ügyfél nyomtató-illesztőprogram-csomagok letöltése HTTP protokollon keresztül történő engedélyezéséhez. Állítsa be a HTTP-nyomtatás, nem beépített illesztőprogramokat kell HTTP protokollon keresztül tölthetők. Megjegyezés: A házirend-beállítás nem akadályozza meg az ügyfél nyomtatás az intraneten vagy az interneten nyomtatókhoz HTTP protokollon keresztül. Csak tiltja, illesztőprogramokat, amelyek nincsenek még telepítve helyileg letöltése. Ha ez a szabályzatbeállítás engedélyezi, nyomtatóillesztők HTTP protokollon keresztül nem lehet letölteni. Ha letiltja vagy nem konfigurálja ezt a beállítást, a felhasználók letölthetik nyomtatóillesztők HTTP protokollon keresztül.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067141)  
  
  **Alapértelmezett**: Enabled  

## <a name="credentials-delegation"></a>Hitelesítő adatok delegálása  
További információkért lásd: [házirend CSP - CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) a Windows dokumentációjában.  

- **Távoli állomás nem exportálható hitelesítő adatok delegálása**  
  Távoli állomás lehetővé teszi, hogy nem exportálható hitelesítő adatok delegálását. Hitelesítő adatok delegálása használatakor az eszközök a távoli gazdagéphez, amely elérhetővé teszi a felhasználók a hitelesítő adatok ellopásának kockázata a támadók a távoli gazdagépen adja meg hitelesítő adatokat egy exportálható verzióját. Ha ez a szabályzatbeállítás engedélyezi, a gazdagép támogatja a távoli Credential Guard vagy a korlátozott rendszergazdai mód. Ha letiltja vagy nem konfigurálja ezt a beállítást, a korlátozott felügyeleti és a távoli Credential Guard módban nem támogatottak. Felhasználói mindig kell megadnia a hitelesítő adataikat a gazdagépre.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067103)   
  
  **Alapértelmezett**: Enabled  

## <a name="credentials-ui"></a>Credentials UI  
További információkért lásd: [házirend CSP - CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) a Windows dokumentációjában.  

- **A rendszergazdák számbavétele** a házirend-beállítással megadható, hogy a rendszergazdai fiókok jelenít meg, amikor egy felhasználó megpróbál egy futó alkalmazás megszerzését. Alapértelmezés szerint a rendszergazdai fiókok nem jelennek meg, amikor a felhasználó megpróbál egy futó alkalmazás megszerzését. Ha ez a szabályzatbeállítás engedélyezi, a számítógép összes helyi rendszergazdai fiók jeleníti meg, így a felhasználó válasszon egyet, és adja meg a helyes jelszót. Ha letiltja ezt a beállítást, felhasználók mindig kell adjon meg egy felhasználónevet és a jelszó megszerzését.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067021)

  
  **Alapértelmezett**: Letiltva  

## <a name="data-protection"></a>Adatvédelem  
További információkért lásd: [házirend CSP - DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) a Windows dokumentációjában.  

- **Közvetlen memória-hozzáférés letiltása**  
  A házirend-beállítás lehetővé teszi, hogy, hogy közvetlen memória-hozzáférés (DMA) letiltása az összes gyakran használt adatok moduláris PCI alsóbb rétegbeli port mindaddig, amíg a felhasználó bejelentkezik a Windows. Miután egy felhasználó bejelentkezik, a Windows enumerálnia a PCI-eszköz csatlakozik a gazdagép beépülő PCI portokat. Minden alkalommal, amikor a felhasználó a gép zárolja, DMA le van tiltva a gyakori elérésű beépülő PCI portokon gyermekek eszközökkel nem rendelkező mindaddig, amíg a felhasználó újra bejelentkezik. Már enumerálták, amikor a számítógép zárolása fel lett oldva eszközök továbbra is működni, amíg nem választható le. A házirend-beállítás csak akkor lép érvénybe, ha a BitLocker vagy az eszköztitkosítás engedélyezve van.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067031)     
  
  **Alapértelmezett**: Igen  

## <a name="device-guard"></a>A Device Guard  
További információkért lásd: [házirend CSP - DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) a Windows dokumentációjában.  

- **Credential Guard**  
  Ez a beállítás lehetővé teszi, hogy a felhasználók bekapcsolása a Credential Guard virtualizálás-alapú biztonság a következő rendszerindításkor hitelesítő adatok védelme érdekében.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067044)
   
  **Alapértelmezett**: UEFI-zárolással engedélyezése 

- **A virtualizálás-alapú biztonság engedélyezése**   
  Kapcsolja be a virtualizálás-alapú biztonság (VBS a következő újraindításkor). A virtualizálás-alapú biztonság a Windows hipervizorral nyújt támogatást biztonsági szolgáltatásokhoz.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067066)  
  
  **Alapértelmezett**: Igen  


- **Indítsa el a rendszer őrfeltétel**    
  **Alapértelmezett**: Enabled  

## <a name="device-installation"></a>Eszköz telepítése  
További információkért lásd: [házirend CSP - DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) a Windows dokumentációjában.  

- **A készülékazonosítók hardver eszköz telepítése**  
  A házirend-beállítás lehetővé teszi, hogy adja meg a Plug and Play hardverazonosítók és, hogy Windows rendszer akadályozza eszközökhöz kompatibilis azonosítók listáját. A házirend-beállítás élvez bármely más házirend-beállítás lehetővé teszi, hogy a Windows eszköz telepítése. Ha ez a szabályzatbeállítás engedélyezi, Windows van akadályozza egy eszközt, amelynek hardveres vagy kompatibilis azonosítója megjelenik a listában hoz létre. Ha engedélyezi ezt a beállítást, a távoli asztali kiszolgálón, a házirend-beállítást befolyásolja irányíthassa át a megadott eszközök, a távoli asztali ügyfélhez a távoli asztali kiszolgálónak. Ha letiltja vagy nem konfigurálja ezt a beállítást, eszközökön telepítheti és engedélyezett vagy egyéb házirend-beállítás megakadályozta abban frissíteni.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2066794)  
  
  **Alapértelmezett**: Blokk hardveres eszköz telepítése  

    Amikor *hardveres eszköz telepítést* van kijelölve, a következő beállítások érhetők el.
  
    - **Megfelelő hardveres eszközök eltávolítása**   
    Ez a beállítás nem érhető el, csak ha *hardveres eszköz telepítése által készülékazonosítók* értékre van állítva *hardveres eszköz telepítést*.
      
      **Alapértelmezett**: Igen
  
    - **Hardver eszközök azonosítói nem futtatható**  
       Ez a beállítás nem érhető el, csak ha *hardveres eszköz telepítése által készülékazonosítók* értékre van állítva *hardveres eszköz telepítést*.
      
      **Alapértelmezett**: Igen  
  
- **A telepítő osztályok hardveres eszköz telepítése**  
  A házirend-beállítás lehetővé teszi, hogy az eszköz beállítása osztály globálisan egyedi azonosítóra (GUID, hogy Windows rendszer akadályozza az eszközillesztők) egy listában megadhatja a. A házirend-beállítás élvez bármely más házirend-beállítás lehetővé teszi, hogy a Windows eszköz telepítése. Ha ez a szabályzatbeállítás engedélyezi, Windows van ebben az esetben telepítésekor vagy frissítésekor az eszköz-illesztőprogramokat, amelyek osztályát GUID szerepelnek a listán hoz létre. Ha engedélyezi ezt a beállítást, a távoli asztali kiszolgálón, a házirend-beállítást befolyásolja irányíthassa át a megadott eszközök, a távoli asztali ügyfélhez a távoli asztali kiszolgálónak. Ha letiltja vagy nem konfigurálja ezt a beállítást, telepítheti a Windows és a frissítési eszközök engedélyezett, vagy egyéb házirend-beállítás megakadályozza.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067048)  
  
  **Alapértelmezett**: Blokk hardveres eszköz telepítése  

    Amikor *hardveres eszköz telepítést* van kijelölve, a következő beállítások érhetők el.
    - **Megfelelő hardveres eszközök eltávolítása**    
    Ez a beállítás nem érhető el, csak ha *hardveres eszköz telepítése a telepítő osztályok* értékre van állítva *hardveres eszköz telepítést*.  

      **Alapértelmezett**: *Alapértelmezett konfiguráció nélkül*  
  
    - **Hardver eszközök azonosítói nem futtatható**  
      Ez a beállítás nem érhető el, csak ha *hardveres eszköz telepítése a telepítő osztályok* értékre van állítva *hardveres eszköz telepítést*.
      
      **Alapértelmezett**: *Alapértelmezett konfiguráció nélkül*  

## <a name="device-lock"></a>Device Lock  
További információkért lásd: [házirend CSP - DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) a Windows dokumentációjában.  

- **Kamera használatának megakadályozása**  
  Letilthatja a zárolási képernyő kamera váltógomb kapcsolót a számítógép beállításait, és megakadályozza, hogy a fényképezőgép a zárolási képernyőn elindításának. Alapértelmezés szerint a felhasználók engedélyezhetik a zárolási képernyőn egy elérhető kamera lett meghívva. Ha engedélyezi ezt a beállítást, a felhasználók többé nem fognak tudni engedélyezése vagy letiltása a zárolási képernyő kamera-hozzáférés a PC-beállítások, és a kamera nem hívható meg a zárolási képernyőn.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067052)
  
  **Alapértelmezett**: Enabled  

- **Jelszó kérése**  
  Itt adhatja meg, hogy engedélyezve van-e az eszköz zárolása.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067049)  
  
  **Alapértelmezett**: Igen  
  
    Amikor *jelszó kérése* értékre van állítva *Igen*, a következő beállítások érhetők el.

    - **Jelszó minimális karakterkészlet száma**  
      Összetett elemtípusok (kis-és nagybetűk, számok és központozási), erős PIN-kód vagy jelszó szükséges számát. PIN-kód kikényszeríti a következő viselkedés, asztali és mobil eszközökhöz: 1 – számjegyek csak 2 - számokat és kisbetűket szükséges 3 - kisbetűk, számjegyek és nagybetűk szükség. Az asztali Microsoft-fiókok és a tartományi fiókok nem támogatott. 4 – számjegy, kisbetűk, nagybetűk és speciális karakterek szükség. Nem támogatott a desktopban. Az alapértelmezett érték az 1.  
      [További információ](https://go.microsoft.com/fwlink/?linkid=2067055)  
      
      **Alapértelmezett**: 3  
  
    - **Sikertelen bejelentkezések száma, mielőtt törlődne az eszközön lévő összes adat**  
      Az eszköz törlése előtt engedélyezett hitelesítési hibák száma. A 0 érték letiltja az eszköz törlési funkciót.  
      [További információ](https://go.microsoft.com/fwlink/?linkid=2067030)  
        
      **Alapértelmezett**: 10  
  
    - **Jelszó lejárata (nap)**  
      A maximális jelszó kora házirend-beállítás meghatározza, hogy az hogyan mennyi ideig (napokban), hogy egy jelszót is használható, mielőtt a rendszer a felhasználó módosíthatja azt igényli. Beállíthatja a jelszavak lejárnak egy 1 és 999 közötti napok számát, vagy megadhatja, hogy jelszavuk Sose járjon le a napok számát állítsa 0-ra. Ha jelszó maximális kora 1 és 999 nap közötti, a jelszó minimális kora jelszó maximális kora kisebbnek kell lennie. Ha a jelszó maximális kora 0 értékre van állítva, a jelszó minimális kora 0 és 998 nap között bármilyen érték lehet.  
      [További információ](https://go.microsoft.com/fwlink/?linkid=2067028)  
      
      **Alapértelmezett**: 60  
  
    - **Kötelező jelszótípus**  
      Határozza meg a PIN-kód vagy jelszó megadása kötelező.  
      [További információ](https://go.microsoft.com/fwlink/?linkid=2067027)  
      
      **Alapértelmezett**: Alfanumerikus karakterek  
  
    - **Jelszó minimális hossza**  
      A minimális jelszó hossza házirend-beállítás meghatározza, hogy legalább hány karakterből kell állnia egy felhasználói fiók jelszavát is alkotó. Beállíthatja a egy értéke 1 és 14 karakter között, vagy hozhat létre, hogy a karakterek száma 0-ra állításával jelszavát nem szükséges.  
      [További információ](https://go.microsoft.com/fwlink/?linkid=2067024)  
      
      **Alapértelmezett**: 8  
  
    - **Egyszerű jelszavak blokkolása**  
      Itt adhatja meg, hogy a PIN-kód vagy jelszó például a "1111" vagy "1234" engedélyezettek. Az asztal a képjelszavak használatát is meghatározza.  
      [További információ](https://go.microsoft.com/fwlink/?linkid=2067127) 
      
      **Alapértelmezett**: Igen  
        *Igen, egy beállítás megakadályozza, hogy az egyszerű jelszavak használatát.* 

  - **Korábbi jelszavak újbóli használatának tiltása**  
    Itt adhatja meg, hány jelszó tárolható az előzményeket, amely nem használható. Az érték a felhasználó jelenlegi jelszavának tartalmazza. Például a beállítását *1* a felhasználó nem használhatja az aktuális jelszó újra, amikor kiválasztja az új jelszót. A beállításnak *5* azt jelenti, hogy a felhasználó nem állíthatja be az új jelszóval az aktuális jelszó vagy bármely olyan az előző négy jelszavait.  
    [További információ](https://go.microsoft.com/fwlink/?linkid=2066795)  
    
    **Alapértelmezett**: 24  

- **Diavetítés megakadályozása**  
  Letiltása a zárolási képernyő diavetítés beállításai a számítógép beállításait, és megakadályozza, hogy Diavetítés lejátszása a zárolási képernyőn. Alapértelmezés szerint a felhasználók engedélyezhetik a diavetítés, akkor zárolja a gép után fog futni. Ha engedélyezi ezt a beállítást, a felhasználó nem módosíthatja a gépház diavetítés beállításait, és nincs diavetítés megkezdheti.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067105) 
  
  **Alapértelmezett**: Enabled  
  *Engedélyezett beállítás megakadályozza, hogy a diavetítések futását.* 

- **Jelszó minimális kora napokban**  
  A minimális jelszó kora házirend-beállítás határozza meg azt a időszakot (napokban), amely egy jelszónak kell lennie, mielőtt a felhasználó módosíthatná. Beállíthat egy 1 és 998 nap közötti értéket, vagy közvetlenül engedélyezheti a jelszó módosítására a napok száma 0-ra állításával. A jelszó minimális kora kisebbnek kell lennie a jelszó maximális kora, kivéve, ha a jelszó maximális kora értéke 0, amely azt jelzi, hogy jelszavuk Sose járjon le. Jelszó maximális kora értéke 0, ha a jelszó minimális kora 0 és 998 között bármilyen érték lehet állítani.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067022) 
  
  **Alapértelmezett**: 1  

## <a name="dma-guard"></a>DMA Guard  
További információkért lásd: [házirend CSP - DmaGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard) a Windows dokumentációjában.
- **A külső eszközök nem kompatibilisek a Kernel DMA védelmet enumerálási**  
  Ez a szabályzat funkcionalitást biztosít a további biztonsági külső DMA-kompatibilis eszközök ellen. Lehetővé teszi az enumerálás a külső DMA-kompatibilis eszközök felett több szabályozási nem kompatibilis a DMA Újramegfeleltetést/eszköz memória elkülönítése és az elszigetelés. Ez a szabályzat csak akkor lép érvénybe, ha Kernel DMA védelem támogatott, és a rendszer belső vezérlőprogramja által engedélyezett. Kernel DMA védelmi funkciója platform, amely nem vezérelhető, hogy egy házirend vagy a végfelhasználó. Gyártási alkalmával a rendszer által támogatott rendelkezik. Ellenőrizze, hogy ha a rendszer támogatja-e a Kernel DMA védelem, tekintse meg a Kernel DMA védelem mezője MSINFO32.exe összegzés lapján.  
  [További információ](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy)

  **Alapértelmezett**: Összes letiltása   

## <a name="event-log-service"></a>Event Log Service  
További információkért lásd: [házirend CSP - EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) a Windows dokumentációjában.  

- **Biztonsági napló maximális mérete KB-ban**  
  A házirend-beállítás meghatározza a naplófájl maximális méretét kilobájtban. Ha engedélyezi ezt a beállítást, konfigurálhatja a naplófájl maximális mérete 1 megabájt (1024 kilobájt) és 2 terabájt (2147483647 kilobájt) kilobájtoktól a petabájtokig lépésekben kell esnie. Ha letiltja vagy nem konfigurálja ezt a beállítást, a naplófájl maximális méretét a helyileg konfigurált értékre van állítva. A helyi rendszergazda, a napló tulajdonságai párbeszédpanelen módosíthatja ezt az értéket, és a rendszer alapértelmezés szerint 20 MB.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067042)  
  
   **Alapértelmezett**: 196608  

- **Rendszernapló fájl maximális mérete KB-ban**  
  A házirend-beállítás meghatározza a naplófájl maximális méretét kilobájtban. Ha engedélyezi ezt a beállítást, konfigurálhatja a naplófájl maximális mérete 1 megabájt (1024 kilobájt) és 2 terabájt (2147483647 kilobájt) kilobájtoktól a petabájtokig lépésekben kell esnie. Ha letiltja vagy nem konfigurálja ezt a beállítást, a naplófájl maximális méretét a helyileg konfigurált értékre van állítva. A helyi rendszergazda, a napló tulajdonságai párbeszédpanelen módosíthatja ezt az értéket, és a rendszer alapértelmezés szerint 20 MB.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2066798)  
  
  **Alapértelmezett**: 32768  

- **Alkalmazás log fájl maximális mérete KB-ban**  
  A házirend-beállítás meghatározza a naplófájl maximális méretét kilobájtban. Ha engedélyezi ezt a beállítást, konfigurálhatja a naplófájl maximális mérete 1 megabájt (1024 kilobájt) és 2 terabájt (2147483647 kilobájt) kilobájtoktól a petabájtokig lépésekben kell esnie. Ha letiltja vagy nem konfigurálja ezt a beállítást, a naplófájl maximális méretét a helyileg konfigurált értékre van állítva. A helyi rendszergazda, a napló tulajdonságai párbeszédpanelen módosíthatja ezt az értéket, és a rendszer alapértelmezés szerint 20 MB.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067125)  
  
  **Alapértelmezett**: 32768  

## <a name="experience"></a>Élmény  
További információkért lásd: [házirend CSP - élmény](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) a Windows dokumentációjában.  

- **Windows reflektorfény blokkolása**  
  Lehetővé teszi a rendszergazdáknak, hogy kapcsolja ki az összes Windows reflektorfény szolgáltatások - ablak reflektorfény a zárolási képernyő, Windows-tippek a Microsoft fogyasztói funkciók, és az egyéb kapcsolódó funkciókat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067037)  
  
  **Alapértelmezett**: Igen  

  Amikor *Windows reflektorfény blokkolása* értékre van állítva *Igen*, a következő beállítások érhetők el.
  
  - **Harmadik féltől származó javaslatok a Windows Reflektorfényben letiltása**  
    Itt adhatja meg, hogy a külső alkalmazások és tartalmak javaslatok engedélyezése a közzétevők a Windows reflektorfény szolgáltatások, mint például a reflektorfény a zárolási képernyő, a javasolt alkalmazások megjelenítése a Start menübe, és a Windows-tippek. Előfordulhat, hogy továbbra is látnak javaslatok Microsoft szolgáltatások, alkalmazások és szolgáltatások.  
    [További információ](https://go.microsoft.com/fwlink/?linkid=2067045)  
      
    **Alapértelmezett**: Igen  
  - **Fogyasztói funkciók letiltása**  
    Lehetővé teszi a rendszergazdáknak, hogy kapcsolja be, amelyek jellemzően a fogyasztók számára, például a kezdőképernyőn megjelenő javaslatok, a tagsági értesítések, a Kezdőélmény futtatása után alkalmazás telepítése, és átirányítási csempék.  
    [További információ](https://go.microsoft.com/fwlink/?linkid=2067054)  
     
    **Alapértelmezett**: Igen  

## <a name="exploit-guard"></a>Biztonsági rés kiaknázása  
További információkért lásd: [házirend CSP - ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) a Windows dokumentációjában.  

- **Biztonsági rés kiaknázása elleni védelem XML**  
  Lehetővé teszi a rendszergazda leküldenie egy konfigurációt, amely az átnézni kívánt rendszer és alkalmazás kockázatcsökkentési beállításokat a szervezet összes eszközre. A konfigurációs XML képviseli. Biztonsági rés kiaknázása elleni védelem segít eszközök védelme a kártevők, amelyek a biztonsági rések használatával elosztani és fertőznek. A Windows biztonsági alkalmazás vagy a PowerShell használatával létrehozhat egy csoportot (más néven a konfigurációs) megoldások. Ez a konfiguráció exportálása XML-fájlba, majd ossza meg több gépet a hálózaton úgy, hogy az összes ugyanazokat a kockázatcsökkentési beállításokat. Képes konvertálni, és egy meglévő EMET konfigurációs XML-fájl importálása egy biztonsági rés kiaknázása elleni védelem konfigurációs XML-jét.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067035)  
  
  **Alapértelmezett**: *A megadott minta xml* 
 
## <a name="file-explorer"></a>Fájlkezelő  
További információkért lásd: [házirend CSP - fájlkezelő](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) a Windows dokumentációjában.  

- **Adatvégrehajtás-megakadályozási letiltása**  
  Gyakori letiltása bizonyos örökölt beépülő modul alkalmazások nélküli megszakítást Explorer lehetővé teszi.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067043)  
  
  **Alapértelmezett**: Letiltva  
   
- **Sérülés blokk halommemória-lezárás**  
  Halommemória-lezárás sérülés letiltása bizonyos örökölt beépülő modul alkalmazások Explorer leállítása nélkül, azonnal működni engedélyezheti, bár Explorer továbbra is felmondhatja váratlanul később.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067107)  
  
  **Alapértelmezett**: Letiltva  
    

## <a name="internet-explorer"></a>Internet Explorer  
További információkért lásd: [házirend CSP - InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) a Windows dokumentációjában.  

- **Az Internet Explorer korlátozott zóna frissítései állapotsor parancsfájl használatával**  
  A házirend-beállítás lehetővé teszi, hogy kezelheti, hogy a parancsfájl engedélyezett a zónán belül az állapotsor frissítése. 
  - *Ha ez a szabályzatbeállítás engedélyezi*, parancsfájl engedélyezett az állapotsor frissítése.
  - *Ha letiltja vagy nem konfigurálja a házirend-beállítás*, parancsfájl az állapotsor frissítése nem engedélyezett.  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067074)  

  **Alapértelmezett**: Letiltva

- **Az Internet Explorer az internet zóna húzza és dobja el, vagy másolja és illessze be a fájlokat**  
  Ez a házirend-beállítással kezelheti, hogy a felhasználók húzással vagy másolással illessze be a zónán belüli forrásból származó fájlokat. Ha ez a szabályzatbeállítás engedélyezi, a felhasználók vagy másolással húzza át és illessze be a zóna fájlok automatikusan. Kérdés a legördülő mezőben válassza ki, ha a rendszer megkérdezi a felhasználókat, hogy e húzással, vagy a fájlok másolása a zóna. Ha letiltja ezt a beállítást, a rendszer megakadályozza a felhasználókat a fájlok húzással másolással és beillesztéssel fájlokat ebben a zónában. Ha nem konfigurálja ezt a beállítást, a felhasználók húzással vagy másolással és illessze be a zóna fájlok automatikusan.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067076)  

  **Alapértelmezett**: Letiltás

- **Az Internet Explorer korlátozott zóna .NET-keretrendszer tartománybeli összetevők**    
  Ez a házirend-beállítással kezelheti, hogy a .NET-keretrendszer összetevők, az Authenticode aláírással nem rendelkező hajthat végre az Internet Explorer. Ezen összetevők közé tartozik egy objektum címke és a egy hivatkozást a hivatkozott felügyelt végrehajtható fájlok a hivatkozott felügyelt szabályozza. Ha ez a szabályzatbeállítás engedélyezi, az Internet Explorer végrehajtja a aláíratlan felügyelt összetevőket. Kérdés a legördülő mezőben válassza ki, ha az Internet Explorer kéri a felhasználó határozza meg, hogy végrehajtásához előjel nélküli felügyelt összetevőket. Ha letiltja ezt a beállítást, az Internet Explorer nem hajtható végre aláíratlan felügyelt összetevőket. Ha nem adja meg a házirend-beállítás, az Internet Explorer nem hajtható végre aláíratlan felügyelt összetevőket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067077)

  **Alapértelmezett**: Letiltás


- **Az Internet Explorer helyi zónán nem futtathatnak kártevőirtó ActiveX-vezérlők**  
  A házirend-beállítás meghatározza, hogy az Internet Explorer fut-e kártevőirtó-programok ellen ActiveX-vezérlők annak ellenőrzéséhez, hogy azok biztonságos voltát oldalain betölteni. Ha ez a szabályzatbeállítás engedélyezi, az Internet Explorer nem egyeztessen a kártevőirtó programot, hogy hozzon létre egy példányt az ActiveX-vezérlő való biztonságos megtekintéséhez. Ha letiltja ezt a beállítást, az Internet Explorer mindig ellenőrzi a kártevőirtó programot, hogy hozzon létre egy példányt az ActiveX-vezérlő való biztonságos megtekintéséhez. Ha nem konfigurálja ezt a beállítást, az Internet Explorer nem egyeztessen a kártevőirtó programot, hogy hozzon létre egy példányt az ActiveX-vezérlő való biztonságos megtekintéséhez. Bármikor ezt a viselkedést be- vagy kikapcsolása az Internet Explorer biztonsági beállításokkal.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067152)

  **Alapértelmezett**: Letiltva

- **Az Internet Explorer internetes zóna hozzáférést az adatforrásokhoz**  
  Ez a házirend-beállítással kezelheti, hogy az Internet Explorer érhessék el az adatokat a Microsoft XML Parser (MSXML) vagy ActiveX Data Objects (ADO) használatával egy másik biztonsági zónából. Ha ez a szabályzatbeállítás engedélyezi, a felhasználók betölthetnek egy oldal, amely az MSXML vagy ADO használ a zóna egy másik helyről származó adatok eléréséhez a zónában. Kérdés a legördülő mezőben válassza ki, ha a rendszer megkérdezi a felhasználókat, döntse el, hogy engedélyezi, hogy a lap betöltése a zónában, amelyek az MSXML vagy ADO segítségével érheti el adatait a zónában egy másik helyről. Ha letiltja ezt a beállítást, a felhasználók nem tudják betölteni egy oldal, amely az MSXML vagy ADO használ a zóna egy másik helyről származó adatok eléréséhez a zónában. Ha nem konfigurálja ezt a beállítást, a felhasználók nem tudják betölteni egy oldal, amely az MSXML vagy ADO használ a zóna egy másik helyről származó adatok eléréséhez a zónában.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067078)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zóna tartalom húzza az eltérő tartományokban időkereten belül**  
  A házirend-beállítás lehetővé teszi a húzással tartalom egyik tartományból egy másik tartományba Ha a forrás- és ugyanabban az ablakban beállításainak megadása. Ha engedélyezi ezt a házirend-beállítást, és kattintson az engedélyezés, felhasználók húzhatja tartalom egyik tartományából egy másik tartományba, ha a forrás- és a rendszer ugyanabban az ablakban. Felhasználók nem módosíthatják ezt a beállítást. Ha engedélyezi ezt a házirend-beállítást, és kattintson a Letiltás elemre, felhasználók nem húzható tartalom egyik tartományából egy másik tartományba, ha a forrás- és a rendszer ugyanabban az ablakban. Felhasználók nem módosíthatják ezt a beállítást az Internetbeállítások párbeszédpanelt. Az Internet Explorer 10 Ha ezt a beállítást letiltja vagy nem konfigurálja, felhasználók nem húzható tartalom egyik tartományából egy másik tartományba Ha a forrás- és ugyanabban az ablakban. A felhasználók módosíthatják ezt a beállítást az Internetbeállítások párbeszédpanelt. Az Internet Explorer 9 és korábbi verzióiban Ha ezt a beállítást letiltja vagy nem konfigurálja, felhasználók húzhatja tartalom egyik tartományából egy másik tartományba, ha a forrás- és a rendszer ugyanabban az ablakban. Felhasználók nem módosíthatják ezt a beállítást az Internetbeállítások párbeszédpanelt.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067079)  
  
  **Alapértelmezett**: Letiltva
  
- **Az Internet Explorer tanúsítvány cím eltérés figyelmeztetés**  
  A házirend-beállítás lehetővé teszi, hogy kapcsolja be a tanúsítvány cím eltérő biztonsági figyelmeztetést. Ha a házirend-beállítás be van kapcsolva, a rendszer figyelmezteti a felhasználót szolgálhassanak HTTP Secure (HTTPS) webhelyek a jelenlegi, egy másik webhely címét kiállított tanúsítványok. Ez a figyelmeztetés megakadályozható, hogy olyan hamisítási támadásokat. Ha ez a szabályzatbeállítás engedélyezi, a tanúsítvány cím eltérés figyelmeztetés mindig megjelenik. Ha letiltja vagy nem konfigurálja ezt a beállítást, a felhasználó dönthet úgy, hogy megjelenik-e a tanúsítvány cím eltérés figyelmeztetés (a Speciális lap használatával az Internet Vezérlőpult).  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067153)  
  
  **Alapértelmezett**: Enabled 
  
- **Az Internet Explorer korlátozott zóna kevesebb jogosultsággal rendelkező helyek**  
  Ez a házirend-beállítással kezelheti, hogy kevesebb jogosultsággal rendelkező zónák, internetes webhelyekre, például a webhelyek navigálni a zóna. Ha ez a szabályzatbeállítás engedélyezi, kevesebb jogosultsággal rendelkező zónákban lévő webhelyekről nyissa meg az új windows vagy is ebbe a zónába lépjen. A biztonsági zóna a biztonsági réteggel is a zóna jogosultságszint-emelési biztonsági funkció védelmet által biztosított nélkül fog futni. Kérdés választja a legördülő mezőben, ha a rendszer figyelmezteti a felhasználót, hogy potenciálisan veszélyes navigációs arra készül, hogy történnek. Ha letiltja ezt a beállítást, esetleg káros navigációs miatt nem sikerült. Az Internet Explorer biztonsági funkció van kapcsolva a zóna védelmet állította be a zóna jogosultságszint-emelési szolgáltatásvezérlő. Ha nem konfigurálja ezt a beállítást, a potenciálisan veszélyes műveleteket ebben az esetben. Az Internet Explorer biztonsági funkció van kapcsolva a zóna védelmet állította be a zóna jogosultságszint-emelési szolgáltatásvezérlő.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067148)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zóna automatikus kérése fájl letöltése**  
  A házirend-beállítás határozza meg, hogy a rendszer kéri a fájl nem felhasználó által kezdeményezett letöltések. Ezt a beállítást, függetlenül a felhasználók kapnak a fájl letöltése párbeszédpanel letöltéseit felhasználó által kezdeményezett. Ha engedélyezi ezt a beállítást, a felhasználók kapnak a fájl letöltése párbeszédpanel automatikus letöltési kísérletek. Ha letiltja vagy nem konfigurálja ezt a beállítást, a letöltéseket, amelyek nem a felhasználó által kezdeményezett blokkolva vannak, és a felhasználók az értesítési sávban helyett a fájl letöltése párbeszédpanel jelenik meg. Felhasználók ezután kattintson az értesítési sávban, hogy a fájl letöltése használatával.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067150)  
  
  **Alapértelmezett**: Letiltva
  
- **Az Internet Explorer internetes zóna .NET-keretrendszer tartománybeli összetevők**  
  Ez a házirend-beállítással kezelheti, hogy a .NET-keretrendszer összetevők, amelyek nem Authenticode aláírással rendelkező hajthat végre az Internet Explorer. Ezen összetevők közé tartozik egy objektum címke és a egy hivatkozást a hivatkozott felügyelt végrehajtható fájlok a hivatkozott felügyelt szabályozza. Ha ez a szabályzatbeállítás engedélyezi, az Internet Explorer végrehajtja a aláíratlan felügyelt összetevőket. Kérdés a legördülő mezőben válassza ki, ha az Internet Explorer kéri a felhasználó határozza meg, hogy végrehajtásához előjel nélküli felügyelt összetevőket. Ha letiltja ezt a beállítást, az Internet Explorer nem futtatja az aláíratlan felügyelt összetevőket. Ha nem konfigurálja ezt a beállítást, az Internet Explorer végrehajtja a aláíratlan felügyelt összetevőket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067073)  
  
  **Alapértelmezett**: Letiltás 
  
- **Az Internet Explorer internetes zóna engedélyezése csak a jóváhagyott tartományok tdc ActiveX-vezérlők használata**  
  A házirend-beállítás szabályozza, ha a felhasználó futtathatja a webhelyeken a TDC ActiveX-vezérlőt. Ha ez a szabályzatbeállítás engedélyezi, a TDC ActiveX-vezérlőt futtatásának megakadályozása a zóna webhelyekről. Ha letiltja ezt a beállítást, a TDC Active X-vezérlés a zónában lévő összes webhelyről fog futni.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067151)
  
  **Alapértelmezett**: Enabled 
  
- **Az Internet Explorer korlátozott zóna parancsfájl indított windows**  
  A házirend-beállítás lehetővé teszi, hogy korlátozásokat előugró ablakok parancsfájl által kezdeményezett, és a title és az állapot sávok tartalmazó windows kezelheti. Ha ez a szabályzatbeállítás engedélyezi, biztonsági Windows korlátozásai nem vonatkoznak a zóna. A biztonsági zónában, ez a szolgáltatás által biztosított biztonsági réteggel nélkül futtatja. Ha letiltja ezt a beállítást, a parancsfájl által kezdeményezett előugró ablakok és a title és az állapot sávok tartalmazó windows lehetséges káros műveleteket nem futtatható. Az Internet Explorer biztonsági szolgáltatása megegyezik az ebben a zónában szolgáltatásvezérlő a Windows biztonsági korlátozások parancsprogrammal létrehozva a folyamat állítja. Ha nem konfigurálja ezt a beállítást, a parancsfájl által kezdeményezett előugró ablakok és a title és az állapot sávok tartalmazó windows lehetséges káros műveleteket nem futtatható. Az Internet Explorer biztonsági szolgáltatása megegyezik az ebben a zónában szolgáltatásvezérlő a Windows biztonsági korlátozások parancsprogrammal létrehozva a folyamat állítja.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067075)  
  
  **Alapértelmezett**: Letiltva 
  
- **A fájlok feltöltése a kiszolgáló szerepeljen az Internet Explorer az internet zóna helyi elérési útja**  
  Ez a házirend-beállítást vezérli, hogy a helyi elérési úttal kapcsolatos információkat küldi, ha a felhasználó tölti fel egy fájlt egy HTML-űrlapot. A helyi elérési út adatokat küld, ha néhány információt előfordulhat, hogy véletlenül is megjeleníthetők a kiszolgálóhoz. Például a felhasználó asztali küldött fájlokat tartalmazhat az elérési út részeként a felhasználó nevét. Amikor a felhasználó tölti fel egy fájlt egy HTML-űrlapot, ha ez a szabályzatbeállítás engedélyezi, a rendszer elküldi az elérési út adatokat. Amikor a felhasználó egy HTML-űrlapot egy fájlt tölt, ha letiltja ezt a beállítást, a rendszer eltávolítja az elérési úttal kapcsolatos információkat. Ha nem konfigurálja ezt a beállítást, a felhasználó dönthet úgy, hogy elérési úttal kapcsolatos információkat küldi, ha azok egy HTML-űrlapot fájl feltöltése. Alapértelmezés szerint az útvonal-információinak zajlik.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067072)  
  
  **Alapértelmezett**: Letiltva 
  
- **Az Internet Explorer fokozott védett módban folyamatok letiltása**  
  A házirend-beállítás meghatározza, hogy a Internet Explorer 11 Ha 64 bites folyamatokat (a nagyobb biztonság), vagy 32 bites folyamatok (a nagyobb kompatibilitás) használjon a fokozottan védett üzemmódban futó Windows 64 bites verziói. Fontos! Egyes ActiveX-vezérlők és eszköztárak előfordulhat, hogy nem érhető el 64 bites folyamatokat használatakor. Ha ez a szabályzatbeállítás engedélyezi, akkor amikor fokozottan védett üzemmód a Windows 64 bites verzióin futó Internet Explorer 11 64 bites fül folyamatai fogja használni. Ha letiltja ezt a beállítást, az Internet Explorer 11 32 bites fül folyamatai készítésére használ a fokozottan védett üzemmód Windows 64 bites verzióiban. Ha nem konfigurálja ezt a beállítást, a felhasználók bekapcsolják ezt a szolgáltatást, és ki az Internet Explorer beállításainak használatával. Ez a funkció alapértelmezés szerint ki van kapcsolva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067149)  
  
  **Alapértelmezett**: Enabled 
  
- **Az Internet Explorer figyelmen kívül hagyja a tanúsítvánnyal kapcsolatos hiba**  
  A házirend-beállítás megakadályozza, hogy a felhasználó Secure Sockets Layer/Transport Layer Security (SSL/TLS) tanúsítványt hibák működését zavaró, az Internet Explorer programban (mint például a "lejárt", "Visszavonva" vagy "neve tér" hibák) böngészés figyelmen kívül hagyásával. Ha ez a szabályzatbeállítás engedélyezi, a felhasználó böngészés nem folytatható. Ha letiltja vagy nem konfigurálja ezt a beállítást, a felhasználó választhat figyelmen kívül a hitelesítési hibák, és folytassa a böngészést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067071)  
  
  **Alapértelmezett**: Letiltva 
  
- **Az Internet Explorer internetes zóna betöltése XAML-fájlok**  
  Ezzel a szabályzatbeállítással kezelése Extensible Application Markup Language (XAML) a fájlok betöltését teszi lehetővé. XAML egy XML-alapú deklaratív jelölőnyelv gazdag felhasználói felületek és a grafikai, amelyek kihasználják a Windows Presentation Foundation létrehozása gyakran használják. Ha engedélyezi ezt a házirend-beállítást, és állítsa be a legördülő listában annak érdekében, XAML fájlok automatikusan betöltődnek az Internet Explorerben. A felhasználó nem módosíthatja ezt a viselkedést. Kérdés beállította a legördülő listából, ha a felhasználó a rendszer XAML fájlok betöltése. Ha letiltja ezt a beállítást, az XAML-fájlok az Internet Explorerben nem betöltve. A felhasználó nem módosíthatja ezt a viselkedést. Ha nem konfigurálja ezt a beállítást, a felhasználó eldöntheti XAML betölteni az Internet Explorerben.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067147)  
  
  **Alapértelmezett**: Letiltás 
  
- **Az Internet Explorer internetes zóna automatikus kérdés fájl letöltése**  
  A házirend-beállítás határozza meg, hogy a rendszer kéri a fájl nem felhasználó által kezdeményezett letöltések. Ezt a beállítást, függetlenül a felhasználók kapnak a fájl letöltése párbeszédpanel letöltéseit felhasználó által kezdeményezett. Ha engedélyezi ezt a beállítást, a felhasználók kapnak a fájl letöltése párbeszédpanel automatikus letöltési kísérletek. Ha letiltja vagy nem konfigurálja ezt a beállítást, a letöltéseket, amelyek nem a felhasználó által kezdeményezett blokkolva vannak, és a felhasználók az értesítési sávban helyett a fájl letöltése párbeszédpanel jelenik meg. Felhasználók ezután kattintson az értesítési sávban, hogy a fájl letöltése használatával.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067117)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zóna biztonsági figyelmeztetés a potenciálisan nem biztonságos fájlok**  
  A házirend-beállítás vezérli, hogy a "Nyissa meg a fájl – biztonsági figyelmeztetés" üzenet jelenik meg, amikor a felhasználó megpróbálja megnyitni a végrehajtható fájlok vagy más potenciálisan nem biztonságos fájlok (az intranetes a Fájlkezelővel, például fájlmegosztások). Ha engedélyezi ezt a házirend-beállítást, és állítsa be a legördülő listában annak érdekében, ezek a fájlok nyissa meg a biztonsági figyelmeztetés nélkül. Ha a legördülő listából a kérdés, biztonsági figyelmeztetés jelenik meg, a fájlok megnyitása előtt. Ha letiltja ezt a beállítást, az ezeket a fájlokat nem nyitnak meg. Ha nem konfigurálja ezt a beállítást, a felhasználó konfigurálhat a fájlok kezelésének. Alapértelmezés szerint ezeket a fájlokat a Tiltott helyek zónához, az intranetes és a helyi számítógép zónában, engedélyezve van a blokkolt és állítsa be az Internet és megbízható zónában kéréséhez.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2066797)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer az internet zóna keresztszűrő hely parancsfájl-kezelési**  
  Ez az irányelv szabályozza, ha a többhelyes parancsfájl-kezelési (XSS) szűrő érzékeli, és megakadályozza a webhelyközi parancsprogramot injektálások, websites, a zóna. Ha ez a szabályzatbeállítás engedélyezi, a XSS szűrő zónában is engedélyezve van, és a XSS-szűrő megpróbálja webhelyközi parancsprogramot injektálások letiltása. Ha letiltja ezt a beállítást, a XSS szűrő ki van kapcsolva a zónában, és az Internet Explorer lehetővé teszi a webhelyközi parancsprogramot injektálások.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067053) 
  
  **Alapértelmezett**: Enabled 
  
- **Az Internet Explorer tartalék SSL3**  
  A házirend-beállítás lehetővé teszi, hogy egy nem biztonságos tartalék SSL 3.0 letiltása. Ha ez a szabályzat engedélyezve van, az Internet Explorer megkísérli SSL 3.0-t használó helyek vagy alatt, ha sikertelen a TLS 1.0-s vagy nagyobb. Azt javasoljuk, hogy nincs-e nem biztonságos tartalék engedélyezése a man-in-the-middle támadások megelőzése érdekében. Ez a házirend nincs hatással, mely biztonsági protokollok engedélyezettek. Ha letiltja ezt a házirendet, a rendszer alapértelmezett értékeket használják.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067118)  
  
  **Alapértelmezett**: Nincsenek helyek  

- **Az Internet Explorer titkosítás támogatása**  
  A házirend-beállítás lehetővé teszi, hogy kapcsolja ki a böngészőben a Transport Layer Security (TLS) 1.0, TLS 1.1, TLS 1.2-es, Secure Sockets Layer (SSL) 2.0-s vagy az SSL 3.0 támogatása. A TLS és az SSL olyan protokollok, amelyek a böngésző és a célkiszolgáló közötti kommunikáció védelme érdekében. Amikor a böngésző megpróbál egy védett kommunikációt a célkiszolgáló beállítása, a böngésző és a kiszolgáló egyeztetni a mely protokoll és verzió használatára is. A böngésző és a kiszolgáló megkísérli minden más támogatott protokollok és listája verziók, és kiválasztják a leginkább előnyben részesített egyezést. Ha ez a szabályzatbeállítás engedélyezi, a böngésző egyezteti, vagy nem egyeztet titkosítási alagutat a legördülő listából kiválasztott titkosítási módszerrel. Ha letiltja vagy nem konfigurálja ezt a beállítást, a felhasználó kiválaszthat melyik titkosítási módszer a böngésző támogatja.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067057)

  **Alapértelmezett**: 2 elem:  A TLS 1.1 és TLS 1.2-es verzió  
  *Válassza ki a lefelé mutató nyílra, ez a beállítás választható beállítások megjelenítéséhez.*
  
- **Az Internet Explorer, az internet zóna intelligens képernyő zárolva**  
  Ez a házirend-beállítással megadható, hogy a SmartScreen szűrő megvizsgálja a rosszindulatú zóna oldalak. Ha ez a szabályzatbeállítás engedélyezi, a SmartScreen szűrő megvizsgálja a rosszindulatú zóna oldalak. Ha letiltja ezt a beállítást, a SmartScreen szűrő a rosszindulatú zóna oldal nem beolvasása. Ha nem konfigurálja ezt a beállítást, a felhasználó választhat megvizsgálja-e a SmartScreen szűrő az oldalakat a rosszindulatú zóna. Megjegyezés: Az Internet Explorer 7 a házirend-beállítás meghatározza, hogy megvizsgálja-e adathalász szűrő oldalak rosszindulatú zónában.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067059)  
  
  **Alapértelmezett**: Enabled 
  
- **Az Internet Explorer korlátozott zóna indítási alkalmazásokat és fájlokat egy IFRAME elembe**  
  Ez a házirend-beállítással kezelheti, hogy futtatható alkalmazások és a egy IFRAME-referencia a HTML-lapok ebben a zónában lévő fájlok letölthetők. Ha ez a szabályzatbeállítás engedélyezi, a felhasználók alkalmazásokat futtathat és IFRAME fájlok letöltése a zónában lévő lapok a felhasználói beavatkozás nélkül. Kérdés választja a legördülő mezőben, ha a rendszer megkérdezi a felhasználókat, hogy az alkalmazások futtatásához és IFRAME fájlok letöltése a zóna oldalain e. Ha letiltja ezt a beállítást, a rendszer megakadályozza a felhasználókat a futó alkalmazások és IFRAME fájlok letöltése a zóna oldalain. Ha nem konfigurálja ezt a beállítást, a rendszer megakadályozza a felhasználókat a futó alkalmazások és IFRAME fájlok letöltése a zóna oldalain.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067061)  
  
  **Alapértelmezett**: Letiltás 
  
- **Az Internet Explorer SmartScreen figyelmeztetések, ritka fájlok kihagyása**  
  Ez a szabályzatbeállítás határozza meg, hogy a felhasználó elkerülheti a SmartScreen szűrő figyelmeztetéseit. A SmartScreen szűrő figyelmezteti a felhasználót a végrehajtható fájlokat, az Internet Explorer-felhasználók gyakran nem letöltése az internetről. Ha ez a szabályzatbeállítás engedélyezi, a SmartScreen szűrő figyelmeztetéseit letiltása a felhasználó. Ha letiltja vagy nem konfigurálja ezt a beállítást, a felhasználó elkerülheti a SmartScreen szűrő figyelmeztetéseit.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067068)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer internetes zóna előugró ablakok blokkolása**  
  Ez a házirend-beállítással kezelheti, hogy nemkívánatos előugró ablak jelenik meg. Előugró ablakok nyílnak meg, amikor a végfelhasználó egy hivatkozásra kattint, nincsenek letiltva. Ha ez a szabályzatbeállítás engedélyezi, leggyakrabban nemkívánatos előugró ablakok ebben az esetben jelennek meg. Ha letiltja ezt a beállítást, az előugró windows nem nem jelenik meg. Ha nem konfigurálja ezt a beállítást, leggyakrabban nemkívánatos előugró ablakok ebben az esetben jelennek meg.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067069)  
  
  **Alapértelmezett**: Engedélyezés  
  
- **Az Internet Explorer dolgozza fel a konzisztens MIME-kezelés**  
  Az Internet Explorer tartalmaz dinamikus bináris viselkedéseket: összetevőket, amelyek bizonyos funkciók, amelyhez hozzá van rendelve a HTML-elemek magába foglalja. Ez a házirend-beállítással megadható, hogy a bináris viselkedés biztonsági korlátozása beállítást. Ebben az esetben, vagy engedélyezett. Ha ez a szabályzatbeállítás engedélyezi, a rendszer letiltja a bináris viselkedést a Fájlkezelőben és az Internet Explorer folyamatokat. Ha letiltja ezt a beállítást, a bináris viselkedéseket a Fájlkezelőben és az Internet Explorer-folyamatokhoz történő használata engedélyezett. Ha nem konfigurálja ezt a beállítást, a rendszer letiltja a bináris viselkedést a Fájlkezelőben és az Internet Explorer folyamatokat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067144)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer zóna java engedélyei korlátozottak**  
  A házirend-beállítás lehetővé teszi a Java-alkalmazások engedélyeinek kezelése. Ha ez a szabályzatbeállítás engedélyezi, beállítások választhat a legördülő listából. Egyéni engedélyek beállításait szabályozhatja a külön-külön. Alacsony biztonsági lehetővé teszi, hogy az alkalmazások összes műveletek végrehajtásához. Közepes biztonsági plusz szolgáltatásokat, például az ideiglenes terület (egy megbízható és biztonságos tároló terület az ügyfélszámítógépen) és a felhasználó általi fájl i/o lehetővé teszi alkalmazások futtatását a védőfal (egy területen kívül, ami a program nem hívásokat a memóriában). Magas biztonsági lehetővé teszi, hogy az alkalmazások futtatását a tesztkörnyezetben. Tiltsa le a Java használatával bármilyen kisalkalmazások tiltsa le a futását. Ha letiltja ezt a beállítást, a Java-alkalmazások nem futtatható. Ha nem konfigurálja ezt a beállítást, a Java-alkalmazások le vannak tiltva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067132)  
  
  **Alapértelmezett**: Tiltsa le a java  
    
  
- **Az Internet Explorer Active X-vezérlők védett módban**  
  A házirend-beállítás megakadályozza, hogy az ActiveX-vezérlők védett módban fut, amikor a fokozottan védett üzemmód engedélyezve van. Amikor a felhasználó rendelkezik ActiveX-vezérlő telepítve van, amely nem kompatibilis a fokozottan védett üzemmód, és egy webhely megkísérli betölteni a vezérlőt, az Internet Explorer értesíti a felhasználót, és lehetőséget ad arra, hogy a webhely rendszeres védett módban fusson. Ezzel a szabályzatbeállítással letiltja ezt az értesítést, és arra kényszeríti az összes webhely futtathat a fokozottan védett üzemmód. Fokozottan védett üzemmód rosszindulatú webhelyekre elleni további védelmet biztosít a 64 bites Windows 64 bites folyamatokat használatával. Vagy újabb rendszert futtató számítógépek Windows 8, a fokozottan védett üzemmóddal is korlátozza a helyeken, az Internet Explorer is olvasható, és a beállításjegyzék és a fájlrendszerhez. Fokozottan védett üzemmód engedélyezve van, és a egy felhasználó olyan webhely, amely megpróbálja az olyan ActiveX-vezérlőt, amely nem kompatibilis a fokozottan védett üzemmód között érhető el, ha az Internet Explorer értesíti a felhasználót, és lehetőséget ad arra, hogy tiltsa le a fokozottan védett üzemmód számára adott adott webhelyre. Ha ez a szabályzatbeállítás engedélyezi, az Internet Explorer nem lehetővé teheti a felhasználó a fokozottan védett üzemmód letiltása. Minden védett mód webhelyek fokozottan védett üzemmódban fog futni. Ha letiltja vagy nem konfigurálja ezt a beállítást, az Internet Explorer értesíti a felhasználókat, és futtassa a webhelyek rendszeres védett módban nem kompatibilis ActiveX-vezérlők lehetőséget biztosít.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067145)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zóna betöltése XAML-fájlok**  
  Ezzel a szabályzatbeállítással kezelése Extensible Application Markup Language (XAML) a fájlok betöltését teszi lehetővé. XAML egy XML-alapú deklaratív jelölőnyelv gazdag felhasználói felületek és a grafikai, amelyek kihasználják a Windows Presentation Foundation létrehozása gyakran használják. Ha engedélyezi ezt a házirend-beállítást, és állítsa be a legördülő listában annak érdekében, XAML fájlok automatikusan betöltődnek az Internet Explorerben. A felhasználó nem módosíthatja ezt a viselkedést. Kérdés beállította a legördülő listából, ha a felhasználó a rendszer XAML fájlok betöltése. Ha letiltja ezt a beállítást, az XAML-fájlok az Internet Explorerben nem betöltve. A felhasználó nem módosíthatja ezt a viselkedést. Ha nem konfigurálja ezt a beállítást, a felhasználó eldöntheti XAML betölteni az Internet Explorerben.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067070)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer parancsfájlalapú ablak biztonsági korlátozások dolgozza fel.**  
  Az Internet Explorer lehetővé teszi a parancsfájlok programozott módon megnyitásához, átméretezése és áthelyezése a windows a különféle fenyegetési típusokat. Az ablak korlátozó biztonsági szolgáltatás korlátozza az előugró ablakok, és megakadályozza, hogy a parancsfájlok, amelyben a title és az állapot sávok nem láthatók a felhasználó számára, vagy más Windows' címet és állapotsorairól rejtse windows megjelenítése. Ha ez a szabályzatbeállítás engedélyezi, parancsfájlalapú windows korlátozza a rendszer az összes folyamat. Ha letiltja vagy nem konfigurálja ezt a beállítást, a parancsfájl a windows nem korlátozott.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067146)  
  
  **Alapértelmezett**: Enabled   
  
- **Az Internet Explorer korlátozott zóna futtathat ActiveX-vezérlők és beépülő modulok**  
  A házirend-beállítás lehetővé teszi, hogy kezelheti-e az ActiveX-vezérlők és beépülő modulok futtatható oldalakon a megadott zónában. Ha ez a szabályzatbeállítás engedélyezi, vezérlők és beépülő modulok futtathatók, felhasználói beavatkozás nélkül. A legördülő listában kiválasztott kérése, ha a felhasználók, döntse el, hogy a vezérlőelemek a gyakori vagy a beépülő modul futtatása. Ha letiltja ezt a beállítást, vezérlők és beépülő modulok nem futtathatók. Ha nem konfigurálja ezt a beállítást, vezérlők és beépülő modulok nem futtathatók.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067114) 
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zóna parancsfájl Active X szabályozza biztonságosként megjelölt futtatása**  
  A házirend-beállítás lehetővé teszi, hogy kezelheti, hogy egy parancsfájl kommunikálhatnak a biztonságosként megjelölt ActiveX-vezérlőt. Ha ez a szabályzatbeállítás engedélyezi, parancsfájl interakció automatikusan történik, felhasználói beavatkozás nélkül. Kérdés választja a legördülő mezőben, ha a rendszer megkérdezi a felhasználókat, hogy a parancsfájl beavatkozás engedélyezése e. Ha letiltja ezt a beállítást, parancsfájl van megakadályozza a való együttműködést. Ha nem konfigurálja ezt a beállítást, parancsfájl van megakadályozza a való együttműködést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067062)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zóna bejelentkezési beállítások**  
  A házirend-beállítás lehetővé teszi, hogy a bejelentkezési lehetőségek beállításainak kezelése. Ha ez a szabályzatbeállítás engedélyezi, a következő bejelentkezési lehetőségek közül választhat. 
  - *Névtelen* – névtelen bejelentkezés a tiltsa le a HTTP-hitelesítést használja, és a Vendég fiók csak a Common Internet File System (CIFS) protokollt használja. 
  - *Kérdés* -tartozó felhasználói azonosítók és jelszavak felhasználónév és jelszó használata parancssort. Után a felhasználó lekérdezése követi, ezeket az értékeket a a munkamenet hátralevő beavatkozás nélkül is használni. 
  - *Csak az Intranet zónában bejelentkezés automatikus* -használja ezt a beállítást, a lekérdezés felhasználóinak felhasználói azonosítók és jelszavak a más zónákban. Után a felhasználó lekérdezése követi, ezeket az értékeket a a munkamenet hátralevő beavatkozás nélkül is használni. 
  - *Aktuális felhasználónév és jelszó automatikus bejelentkezés*-használja ezt a beállítást, próbálja meg a Windows NT kérdés-válasz (más néven az NTLM-hitelesítés) a bejelentkezéshez. Ha a kiszolgáló támogatja a Windows NT kérdés-válasz, a bejelentkezést a felhasználói hálózati felhasználónevet és jelszót a bejelentkezéshez használ. Ha a kiszolgáló nem támogatja a Windows NT kérdés-válasz, a felhasználó lekérdezése követi, a felhasználónév és a jelszót. 

  Ha letiltja ezt a beállítást, jelentkezzen be van állítva *automatikus bejelentkezés csak az Intranet zónában*. Ha nem konfigurálja ezt a beállítást, jelentkezzen be van állítva *Rákérdezés* felhasználóneve és jelszava.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067110)  
  
  **Alapértelmezett**: Névtelen  
  
- **Az Internet Explorer megbízható zóna inicializálása és parancsfájl Active X-vezérlők nem biztonságosként megjelölt**  
  Ez a szabályzatbeállítás nem biztonságosként megjelölt ActiveX-vezérlők kezelését teszi lehetővé. Ha ez a szabályzatbeállítás engedélyezi, az ActiveX-vezérlők, betöltött paraméterekkel és futtatása parancsfájlalapú objektum nem megbízható adatok vagy parancsfájlok biztonságának beállítása nélkül. Ezt a beállítást nem ajánlott, kivéve a biztonságos és felügyelt zónák. A beállítás hatására nem biztonságos, és a biztonságos vezérlők inicializálása és parancsprogrammal létrehozva, a rendszer figyelmen kívül hagyja az ActiveX-vezérlők biztonságosnak lehetőséget. Ha engedélyezi ezt a házirend-beállítást, és a legördülő mezőben válassza ki a kérdés, felhasználók kérdezhető le, hogy a vezérlő betöltés paramétereket az engedélyezi-e, vagy parancsprogram. Ha letiltja ezt a beállítást, a ActiveX-vezérlők nem tehető nem paraméterekkel betöltése vagy parancsprogrammal létrehozva. Ha nem konfigurálja ezt a beállítást, a felhasználók kérdezhető le, hogy a vezérlő betöltés paramétereket az engedélyezi-e vagy parancsprogrammal létrehozva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067137)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer ellenőrzés kiszolgálói tanúsítvány-visszavonás**  
  Ez a házirend-beállítással kezelheti-e az Internet Explorer-kiszolgálók tanúsítványok visszavonási állapotát ellenőrzi. Tanúsítványok visszavonódnak, sérült vagy már nem érvényes, és érvényességük bizalmas adatokat, amelyek rosszindulatú vagy nem biztonságos helyre küldjön. Ha ez a szabályzatbeállítás engedélyezi, az Internet Explorer ellenőrzi, ha a kiszolgálói tanúsítványok visszavonták. Ha letiltja ezt a beállítást, az Internet Explorer nem ellenőrzi kiszolgálói tanúsítványok megtekintéséhez, ha azok visszavonták. Ha nem konfigurálja ezt a beállítást, az Internet Explorer nem ellenőrizze kiszolgálói tanúsítványok megtekintéséhez, ha azok visszavonták.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067046)  
  
  **Alapértelmezett**: Enabled 
  
- **Az Internet Explorer az internet zóna kevesebb jogosultsággal rendelkező helyek**  
  Ez a házirend-beállítással kezelheti, hogy kevesebb jogosultsággal rendelkező zónák, például a Tiltott helyek, a webhelyek navigálni a zóna. Ha ez a szabályzatbeállítás engedélyezi, kevesebb jogosultsággal rendelkező zónákban lévő webhelyekről nyissa meg az új windows vagy is ebbe a zónába lépjen. A biztonsági zóna a biztonsági réteggel is a zóna jogosultságszint-emelési biztonsági funkció védelmet által biztosított nélkül fog futni. Kérdés választja a legördülő mezőben, ha a rendszer figyelmezteti a felhasználót, hogy potenciálisan veszélyes navigációs arra készül, hogy történnek. Ha letiltja ezt a beállítást, a potenciálisan veszélyes műveleteket ebben az esetben. Az Internet Explorer biztonsági funkció van kapcsolva a zóna védelmet állította be a zóna jogosultságszint-emelési szolgáltatásvezérlő. Ha nem konfigurálja ezt a beállítást, kevesebb jogosultsággal rendelkező zónákban lévő webhelyekről nyissa meg az új windows vagy is ebbe a zónába lépjen.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067109)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zóna fájlletöltések**  
  A házirend-beállítás lehetővé teszi, hogy kezelheti a fájlok letöltése a zónából engedélyezettek-e. Ezt a lehetőséget a letöltés, amelyről a fájl kézbesíti a rendszer a zóna nem okoz a hivatkozást tartalmazó lekérdezi határozza meg a zónát, az oldal. Ha ez a szabályzatbeállítás engedélyezi, fájlok, a zóna letölthető. Ha letiltja ezt a beállítást, a rendszer megakadályozza a fájlok letöltését a zónából. Ha nem konfigurálja ezt a beállítást, a rendszer megakadályozza a fájlok letöltését a zónából.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067038)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer az internet zóna futtatása a .NET-keretrendszer Authenticode aláírással rendelkező tartománybeli összetevők**  
  Ez a házirend-beállítással kezelheti, hogy a .NET-keretrendszer összetevők, az Authenticode aláírással rendelkező hajthat végre az Internet Explorer. Ezen összetevők közé tartozik egy objektum címke és a egy hivatkozást a hivatkozott felügyelt végrehajtható fájlok a hivatkozott felügyelt szabályozza. Ha ez a szabályzatbeállítás engedélyezi, az Internet Explorer végrehajtja a aláírt felügyelt összetevőket. Kérdés a legördülő mezőben válassza ki, ha az Internet Explorer kéri a felhasználó határozza meg, hogy aláírt felügyelt összetevőket végrehajtásához. Ha letiltja ezt a beállítást, az Internet Explorer aláírt felügyelt összetevőket nem hajtható végre. Ha nem konfigurálja ezt a beállítást, az Internet Explorer aláírt felügyelt összetevőket nem hajtható végre.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067033)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer minden felhasználó telepítéshez az ActiveX-vezérlők megakadályozása**  
  Ez a házirend-beállítással megakadályozhatja, hogy a telepítés, az ActiveX-vezérlők, felhasználónkénti alapon. Ha ez a szabályzatbeállítás engedélyezi, az ActiveX-vezérlők nem lehet telepíteni, felhasználónkénti alapon. Ha letiltja vagy nem konfigurálja ezt a beállítást, az ActiveX-vezérlők felhasználónkénti alapon is telepíthető.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067058)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer a SmartScreen szűrő kezelésének megakadályozása**  
  A házirend-beállítás megakadályozza, hogy a felhasználó kezelje a SmartScreen szűrő, amely figyelmezteti a felhasználót, ha megtekinti a webhely ismert rosszindulatú kísérletek "adathalász" keresztül személyes adatokat gyűjthet, vagy a gazdagép kártevő ismert. Ha ez a szabályzatbeállítás engedélyezi, a nem kéri a felhasználót, hogy a SmartScreen szűrő bekapcsolására. Az összes webhely címét, amelyek nem szerepelnek a szűrők engedélyezése listája automatikusan elküld a Microsoft a felhasználó értesítése nélkül. Ha letiltja vagy nem konfigurálja ezt a beállítást, a lekérdezi kéri a felhasználót, hogy az első rendszerindítás során a SmartScreen szűrő bekapcsolására kell-e.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067135)  
  
  **Alapértelmezett**: Engedélyezés  
  
- **Az Internet Explorer MIME elemzés biztonsági szolgáltatás dolgozza fel.**  
  A házirend-beállítás meghatározza, hogy e az Internet Explorer MIME-elemzése megakadályozza, hogy egy adott típusú fájl több veszélyes fájl típusra. Ha ez a szabályzatbeállítás engedélyezi, MIME-elemzése soha nem lépteti elő egy adott típusú fájlt egy több veszélyes fájl típusra. Ha letiltja ezt a beállítást, az Internet Explorer folyamatok lehetővé teszi egy adott típusú fájlt egy több veszélyes fájl típusra való előléptetése másikká. Ha nem konfigurálja ezt a beállítást, MIME-elemzése soha nem lépteti elő egy adott típusú fájlt egy több veszélyes fájl típusra.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067124)  
  
  **Alapértelmezett**: Enabled  
  
- **Aláírt ActiveX-vezérlők az Internet Explorer korlátozott zóna letöltése**  
  Ez a házirend-beállítással kezelheti, hogy a felhasználók letölthetnek aláírt ActiveX-vezérlők a zónában lévő oldal. Ha engedélyezi ezt a házirendet, a felhasználók letölthetik aláírt vezérlők felhasználói beavatkozás nélkül. Kérdés a legördülő mezőben válassza ki, ha a felhasználók dönthetik töltse le a nem megbízható közzétevők által aláírt szabályozza-e. Csendes letöltődik a megbízható közzétevők által aláírt kód. Ha letiltja a házirend-beállítást, a nem aláírt vezérlők tölthető le. Ha nem konfigurálja ezt a beállítást, a felhasználók dönthetik töltse le a nem megbízható közzétevők által aláírt szabályozza-e. Csendes letöltődik a megbízható közzétevők által aláírt kód.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067120) 
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer automatikus kiegészítés**  
  Az automatikus kiegészítés funkció ne felejtse el és a felhasználónevek és jelszavak űrlapokon javaslat. Ha engedélyezi ezt a beállítást, a felhasználó nem módosíthatja, "felhasználónevet és jelszót" vagy "Rákérdezés is menthetik a jelszavakat". A felhasználónevek és jelszavak űrlapokon automatikus teljes funkciót be van kapcsolva. Akkor válassza a "Rákérdezés is menthetik a jelszavakat" kell-e. Ha letiltja ezt a beállítást a nem módosítható az a felhasználó a "felhasználónevet és jelszót" vagy "Rákérdezés is menthetik a jelszavakat". A felhasználónevek és jelszavak űrlapokon automatikus teljes szolgáltatás ki van kapcsolva. A felhasználó még nem tilthatók le is menthetik a jelszavakat kéri. Ha nem konfigurálja ezt a beállítást, a felhasználók számára az, hogy automatikusan teljes felhasználónevet és a jelszavakat a képernyők és kéri a felhasználót, jelszavak mentése egyszerű lehetőséget szabadon. Megjelenítéséhez ezt a beállítást, a felhasználók az Internetbeállítások párbeszédpanel megnyitásához kattintson a tartalom lap és a beállítások gombra.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067122)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer az internet zóna VBScript-parancsprogramot futtatni engedélyezése**  
  A házirend-beállítás lehetővé teszi, hogy Ön döntse el, hogy a VBScript futtatható-e az adott Internet Explorer zónákban oldalain. A lehetőségek a következők: 
  - *Engedélyezése* -VBScript parancsfájlt futtat lapok adott zónákban, felhasználói beavatkozás nélkül. 
  - *Rákérdezés* -alkalmazottak a rendszer kéri-e, hogy a VBScript-parancsprogramot a zónában. 
  - *Tiltsa le* -VBScript megakadályozta a zóna fut. Ha letiltja vagy nem konfigurálja ezt a beállítást, VBScript parancsfájlt futtat, a megadott zónában felhasználói beavatkozás nélkül.    

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067119)  
  
  **Alapértelmezett**: Letiltás  
  
- **Tiltott helyek zónához engedélyezése az Internet Explorer csak a jóváhagyott tartományok tdc ActiveX-vezérlők használata**  
  A házirend-beállítás szabályozza, ha a felhasználó futtathatja a webhelyeken a TDC ActiveX-vezérlőt. Ha ez a szabályzatbeállítás engedélyezi, a TDC ActiveX-vezérlőt futtatásának megakadályozása a zóna webhelyekről. Ha letiltja ezt a beállítást, a TDC Active X-vezérlés a zónában lévő összes webhelyről fog futni.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067032)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer Megbízható helyek zónájába kártevőirtó ActiveX-vezérlők nem futtatásához**  
  A házirend-beállítás meghatározza, hogy az Internet Explorer fut-e kártevőirtó-programok ellen ActiveX-vezérlők annak ellenőrzéséhez, hogy azok biztonságos voltát oldalain betölteni. Ha ez a szabályzatbeállítás engedélyezi, az Internet Explorer nem egyeztessen a kártevőirtó programot, hogy hozzon létre egy példányt az ActiveX-vezérlő való biztonságos megtekintéséhez. Ha letiltja ezt a beállítást, az Internet Explorer mindig ellenőrzi a kártevőirtó programot, hogy hozzon létre egy példányt az ActiveX-vezérlő való biztonságos megtekintéséhez. Ha nem konfigurálja ezt a beállítást, az Internet Explorer mindig ellenőrzi a kártevőirtó programot, hogy hozzon létre egy példányt az ActiveX-vezérlő való biztonságos megtekintéséhez. Bármikor ezt a viselkedést be- vagy kikapcsolása az Internet Explorer biztonsági beállításokkal.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067115)  
  
  **Alapértelmezett**: Letiltva 
  
- **Az Internet Explorer helyi gép zóna java-engedélyek**  
  A házirend-beállítás lehetővé teszi a Java-alkalmazások engedélyeinek kezelése. Ha ez a szabályzatbeállítás engedélyezi, beállítások választhat a legördülő listából. Egyéni engedélyek beállításait szabályozhatja a külön-külön. Alacsony biztonsági lehetővé teszi, hogy az alkalmazások összes műveletek végrehajtásához. Közepes biztonsági plusz szolgáltatásokat, például az ideiglenes terület (egy megbízható és biztonságos tároló terület az ügyfélszámítógépen) és a felhasználó általi fájl i/o lehetővé teszi alkalmazások futtatását a védőfal (egy területen kívül, ami a program nem hívásokat a memóriában). Magas biztonsági lehetővé teszi, hogy az alkalmazások futtatását a tesztkörnyezetben. Tiltsa le a Java használatával bármilyen kisalkalmazások tiltsa le a futását. Ha letiltja ezt a beállítást, a Java-alkalmazások nem futtatható. Ha nem konfigurálja ezt a beállítást, az engedély értéke közepes biztonságát.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067113)  
  
  **Alapértelmezett**: Tiltsa le a java 
  
- **Az Internet Explorer intranetes zóna nem futtathatnak kártevőirtó ActiveX-vezérlők**  
  A házirend-beállítás meghatározza, hogy az Internet Explorer fut-e kártevőirtó-programok ellen ActiveX-vezérlők annak ellenőrzéséhez, hogy azok biztonságos voltát oldalain betölteni. Ha ez a szabályzatbeállítás engedélyezi, az Internet Explorer nem egyeztessen a kártevőirtó programot, hogy hozzon létre egy példányt az ActiveX-vezérlő való biztonságos megtekintéséhez. Ha letiltja ezt a beállítást, az Internet Explorer mindig ellenőrzi a kártevőirtó programot, hogy hozzon létre egy példányt az ActiveX-vezérlő való biztonságos megtekintéséhez. Ha nem konfigurálja ezt a beállítást, az Internet Explorer nem egyeztessen a kártevőirtó programot, hogy hozzon létre egy példányt az ActiveX-vezérlő való biztonságos megtekintéséhez. Bármikor ezt a viselkedést be- vagy kikapcsolása az Internet Explorer biztonsági beállításokkal.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067138)  
  
  **Alapértelmezett**: Letiltva  

- **Az Internet Explorer korlátozott zóna Szkriptletek**  
  Ez a házirend-beállítással kezelheti, hogy a felhasználó futtathatja a Szkriptletek. Ha ez a szabályzatbeállítás engedélyezi, akkor a felhasználó Szkriptletek futtathatja. Ha letiltja ezt a beállítást, a felhasználó Szkriptletek nem futtatható. Ha nem konfigurálja ezt a beállítást, a felhasználó engedélyezheti vagy letilthatja a Szkriptletek.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067112)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer folyamatok értesítési sáv**  
  Ez a házirend-beállítással kell kezelni az értesítési sáv jelenik meg az Internet Explorer folyamatok, ha a fájl-vagy kód korlátozva-e. Alapértelmezés szerint az értesítési sáv jelenik meg az Internet Explorer folyamatok. Ha ez a szabályzatbeállítás engedélyezi, az értesítési sáv az Internet Explorer folyamatok jeleníti meg. Ha letiltja ezt a beállítást, az értesítési sáv az Internet Explorer folyamatok nem jeleníthető meg. Ha nem konfigurálja ezt a beállítást, akkor az értesítési sávban a nem az Internet Explorer folyamatok jeleníti meg.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067139)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer internetes zóna letöltés aláírt ActiveX-vezérlők**  
  Ez a házirend-beállítással kezelheti, hogy a felhasználók letölthetnek aláírt ActiveX-vezérlők a zónában lévő oldal. Ha engedélyezi ezt a házirendet, a felhasználók letölthetik aláírt vezérlők felhasználói beavatkozás nélkül. Kérdés a legördülő mezőben válassza ki, ha a felhasználók dönthetik töltse le a nem megbízható közzétevők által aláírt szabályozza-e. Csendes letöltődik a megbízható közzétevők által aláírt kód. Ha letiltja a házirend-beállítást, a nem aláírt vezérlők tölthető le. Ha nem konfigurálja ezt a beállítást, a felhasználók dönthetik töltse le a nem megbízható közzétevők által aláírt szabályozza-e. Csendes letöltődik a megbízható közzétevők által aláírt kód.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067064)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zóna SmartScreen**  
  Ez a házirend-beállítással megadható, hogy a SmartScreen szűrő megvizsgálja a rosszindulatú zóna oldalak. Ha ez a szabályzatbeállítás engedélyezi, a SmartScreen szűrő megvizsgálja a rosszindulatú zóna oldalak. Ha letiltja ezt a beállítást, a SmartScreen szűrő a rosszindulatú zóna oldal nem beolvasása. Ha nem konfigurálja ezt a beállítást, a felhasználó választhat megvizsgálja-e a SmartScreen szűrő az oldalakat a rosszindulatú zóna. Megjegyezés: Az Internet Explorer 7 a házirend-beállítás meghatározza, hogy megvizsgálja-e adathalász szűrő oldalak rosszindulatú zónában.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067034)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer, távolítsa el az elavult ActiveX-vezérlők következő idő gomb futtatására**  
  A házirend-beállítás lehetővé teszi, hogy a felhasználók lássák a "Futtatás most" gomb és az Internet Explorer adott elavult ActiveX-vezérlők futását. Ha ez a szabályzatbeállítás engedélyezi, a felhasználók láthatják a "Futtatás most" gombra a figyelmeztető üzenet jelenik meg, amikor az Internet Explorer blokkolja az elavult ActiveX-vezérlők a. Ha letiltja vagy nem konfigurálja ezt a beállítást, a felhasználók látják a "Futtatás most" gombra a figyelmeztető üzenet jelenik meg, amikor az Internet Explorer blokkolja az elavult ActiveX-vezérlők a. Erre a gombra kattintva lehetővé teszi, hogy a felhasználó egyszeri futtatás a elavult ActiveX-vezérlőt. További információkért lásd: "Elavult ActiveX-vezérlők" az Internet Explorer TechNet könyvtárban.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067123)  
  
  **Alapértelmezett**: Enabled 
  
- **Az Internet Explorer internetes zóna indítási alkalmazásokat és fájlokat egy IFRAME elembe**  
  Ez a házirend-beállítással kezelheti, hogy futtatható alkalmazások és a egy IFRAME-referencia a HTML-lapok ebben a zónában lévő fájlok letölthetők. Ha ez a szabályzatbeállítás engedélyezi, a felhasználók alkalmazásokat futtathat és IFRAME fájlok letöltése a zónában lévő lapok a felhasználói beavatkozás nélkül. Kérdés választja a legördülő mezőben, ha a rendszer megkérdezi a felhasználókat, hogy az alkalmazások futtatásához és IFRAME fájlok letöltése a zóna oldalain e. Ha letiltja ezt a beállítást, a rendszer megakadályozza a felhasználókat a futó alkalmazások és IFRAME fájlok letöltése a zóna oldalain. Ha nem konfigurálja ezt a beállítást, a rendszer megkérdezi a felhasználókat, hogy az alkalmazások futtatásához és IFRAME fájlok letöltése a zóna oldalain e.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067020)  
  
  **Alapértelmezett**: Letiltás 
  
- **Keresse meg a windows és a keretek az Internet Explorer korlátozott zóna különböző tartományokban**  
  A házirend-beállítás lehetővé teszi a húzással tartalom egyik tartományból egy másik tartományba Ha a forrás- és a különböző windows beállításainak megadása. Ha engedélyezi ezt a házirend-beállítást, és kattintson az engedélyezés, felhasználók húzza tartalom egyik tartományból egy másik tartományba Ha a forrás- és a különböző windows. Felhasználók nem módosíthatják ezt a beállítást. Ha engedélyezi ezt a házirend-beállítást, és kattintson a Letiltás elemre, felhasználók nem húzható tartalom egyik tartományból egy másik tartományba Ha a forrás- és a különböző windows. Felhasználók nem módosíthatják ezt a beállítást. Az Internet Explorer 10 Ha ezt a beállítást letiltja vagy nem konfigurálja, felhasználók nem húzható tartalom egyik tartományából egy másik tartományba Ha a forrás- és a különböző windows. A felhasználók módosíthatják ezt a beállítást az Internetbeállítások párbeszédpanelt. Az Internet Explorer 9 és korábbi verzióiban Ha ez a szabályzat letiltja vagy nem konfigurálja, felhasználók húzhatja tartalom egyik tartományából egy másik tartományba Ha a forrás- és a különböző windows. Felhasználók nem módosíthatják ezt a beállítást.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067050)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer internetes zóna SmartScreen**  
  Ez a házirend-beállítással megadható, hogy a SmartScreen szűrő megvizsgálja a rosszindulatú zóna oldalak. Ha ez a szabályzatbeállítás engedélyezi, a SmartScreen szűrő megvizsgálja a rosszindulatú zóna oldalak. Ha letiltja ezt a beállítást, a SmartScreen szűrő a rosszindulatú zóna oldal nem beolvasása. Ha nem konfigurálja ezt a beállítást, a felhasználó választhat megvizsgálja-e a SmartScreen szűrő az oldalakat a rosszindulatú zóna. Megjegyezés: Az Internet Explorer 7 a házirend-beállítás meghatározza, hogy megvizsgálja-e adathalász szűrő oldalak rosszindulatú zónában.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067047)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer Megbízható helyek zónájába java engedélyek zárolva**  
  A házirend-beállítás lehetővé teszi a Java-alkalmazások engedélyeinek kezelése. Ha ez a szabályzatbeállítás engedélyezi, beállítások választhat a legördülő listából. Egyéni engedélyek beállításait szabályozhatja a külön-külön. Alacsony biztonsági lehetővé teszi, hogy az alkalmazások összes műveletek végrehajtásához. Közepes biztonsági plusz szolgáltatásokat, például az ideiglenes terület (egy megbízható és biztonságos tároló terület az ügyfélszámítógépen) és a felhasználó általi fájl i/o lehetővé teszi alkalmazások futtatását a védőfal (egy területen kívül, ami a program nem hívásokat a memóriában). Magas biztonsági lehetővé teszi, hogy az alkalmazások futtatását a tesztkörnyezetben. Tiltsa le a Java használatával bármilyen kisalkalmazások tiltsa le a futását. Ha letiltja ezt a beállítást, a Java-alkalmazások nem futtatható. Ha nem konfigurálja ezt a beállítást, a Java-alkalmazások le vannak tiltva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067142)  
  
  
  **Alapértelmezett**: Tiltsa le a java 
  
- **Az Internet Explorer letöltött programok aláírásának ellenőrzése**  
  Ez a házirend-beállítással kezelheti-e az Internet Explorer ellenőrzi a digitális aláírások (amely azonosítja a szoftver gyártóját, és ellenőrzi a még nem lettek módosítva vagy illetéktelenül) a felhasználó számítógépén végrehajtható programok letöltése előtt. Ha ez a szabályzatbeállítás engedélyezi, az Internet Explorer végrehajtható programok a digitális aláírások ellenőrzése és előtt a felhasználó számítógépére történő letöltésük megjelenítéséhez. Ha letiltja ezt a beállítást, az Internet Explorer nem a végrehajtható programok a digitális aláírások ellenőrzése vagy identitásuk megjelenítése előtt felhasználó számítógépére történő. Ha nem konfigurálja a házirendet, az Internet Explorer nem a végrehajtható programok a digitális aláírások ellenőrzése vagy identitásuk megjelenítése előtt felhasználó számítógépére történő.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067051)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer korlátozott webes böngészővezérlők parancsprogramok zóna**  
  A házirend-beállítás meghatározza, hogy e lap szabályozhatja a beágyazott WebBrowser vezérlők parancsfájl használatával. Ha ez a szabályzatbeállítás engedélyezi, a parancsfájl hozzáférést ovládací prvek WebBrowser engedélyezett. Ha letiltja ezt a beállítást, ovládací prvek WebBrowser parancsfájlok hozzáférése nem engedélyezett. Ha nem konfigurálja ezt a beállítást, a felhasználó engedélyezheti vagy letilthatja ovládací prvek WebBrowser parancsfájl-hozzáférését. Alapértelmezés szerint csak az intranetes zónák és helyi számítógép ovládací prvek WebBrowser parancsfájl hozzáférést engedélyezett.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067098)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zóna keresztszűrő hely parancsfájl-kezelési**  
  Ez az irányelv szabályozza, ha a többhelyes parancsfájl-kezelési (XSS) szűrő érzékeli, és megakadályozza a webhelyközi parancsprogramot injektálások, websites, a zóna. Ha ez a szabályzatbeállítás engedélyezi, a XSS szűrő zónában is engedélyezve van, és a XSS-szűrő megpróbálja webhelyközi parancsprogramot injektálások letiltása. Ha letiltja ezt a beállítást, a XSS szűrő ki van kapcsolva a zónában, és az Internet Explorer lehetővé teszi a webhelyközi parancsprogramot injektálások.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067178)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer korlátozott zóna bináris vagy parancsfájl viselkedések**  
  A házirend-beállítás lehetővé teszi, hogy a dinamikus bináris és parancsfájl viselkedéseinek kezeléséhez: magába foglalja a HTML-elemek, amelyhez csatolva vannak bizonyos funkciók összetevőket. Ha ez a szabályzatbeállítás engedélyezi, bináris és parancsfájl viselkedések érhetők el. Ha jóvá a legördülő listából a rendszergazda, csak a rendszergazda által jóváhagyott viselkedéseket a bináris viselkedéseket házirend szereplő viselkedések érhetők el. Ha letiltja ezt a beállítást, bináris és parancsfájl viselkedések nem érhetők el, csak alkalmazások rendelkeznek egy egyéni biztonsági manager. Ha nem konfigurálja ezt a beállítást, bináris és parancsfájl viselkedések nem érhetők el, csak alkalmazások rendelkeznek egy egyéni biztonsági manager.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067224)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer biztonsági beállítások ellenőrzése**  
  A házirend-beállítás a biztonsági beállítások ellenőrzése szolgáltatást, amely ellenőrzi az Internet Explorer biztonsági beállításokat határozza meg, amikor a beállítások veszélynek az Internet Explorer kikapcsolása. Ha ez a szabályzatbeállítás engedélyezi, a funkció ki van kapcsolva. Ha letiltja vagy nem konfigurálja ezt a beállítást, a funkció be van kapcsolva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067182)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer az internet zóna biztonsági figyelmeztetés a potenciálisan nem biztonságos fájlok**  
  A házirend-beállítás vezérli, hogy a "Nyissa meg a fájl – biztonsági figyelmeztetés" üzenet jelenik meg, amikor a felhasználó megpróbálja megnyitni a végrehajtható fájlok vagy más potenciálisan nem biztonságos fájlok (az intranetes a Fájlkezelővel, például fájlmegosztások). Ha engedélyezi ezt a házirend-beállítást, és állítsa be a legördülő listában annak érdekében, ezek a fájlok nyissa meg a biztonsági figyelmeztetés nélkül. Ha a legördülő listából a kérdés, biztonsági figyelmeztetés jelenik meg, a fájlok megnyitása előtt. Ha letiltja ezt a beállítást, az ezeket a fájlokat nem nyitnak meg. Ha nem konfigurálja ezt a beállítást, a felhasználó konfigurálhat a fájlok kezelésének. Alapértelmezés szerint ezeket a fájlokat a Tiltott helyek zónához, az intranetes és a helyi számítógép zónában, engedélyezve van a blokkolt és állítsa be az Internet és megbízható zónában kéréséhez.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067204)  
  
  **Alapértelmezett**: Kérdés  
  
- **Az Internet Explorer intranetes zóna java-engedélyek**  
  A házirend-beállítás lehetővé teszi a Java-alkalmazások engedélyeinek kezelése. Ha ez a szabályzatbeállítás engedélyezi, beállítások választhat a legördülő listából. Egyéni engedélyek beállításait szabályozhatja a külön-külön. Alacsony biztonsági lehetővé teszi, hogy az alkalmazások összes műveletek végrehajtásához. Közepes biztonsági plusz szolgáltatásokat, például az ideiglenes terület (egy megbízható és biztonságos tároló terület az ügyfélszámítógépen) és a felhasználó általi fájl i/o lehetővé teszi alkalmazások futtatását a védőfal (egy területen kívül, ami a program nem hívásokat a memóriában). Magas biztonsági lehetővé teszi, hogy az alkalmazások futtatását a tesztkörnyezetben. Tiltsa le a Java használatával bármilyen kisalkalmazások tiltsa le a futását. Ha letiltja ezt a beállítást, a Java-alkalmazások nem futtatható. Ha nem konfigurálja ezt a beállítást, az engedély értéke közepes biztonságát.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067206)  
  
  **Alapértelmezett**: Magas biztonsági 
  
- **Az Internet Explorer elavult blokk ActiveX-vezérlők**   
  A házirend-beállítás határozza meg, hogy az Internet Explorer blokkolja adott elavult ActiveX-vezérlők. Elavult ActiveX-vezérlők a rendszer soha nem blokkolja az Intranet zóna. Ha ez a szabályzatbeállítás engedélyezi, az Internet Explorer nem blokkolja az elavult ActiveX-vezérlőket. Ha letiltja vagy nem konfigurálja ezt a beállítást, az Internet Explorer továbbra is adott elavult ActiveX-vezérlők letiltása. További információkért lásd: "Elavult ActiveX-vezérlők" az Internet Explorer TechNet könyvtárban.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067203)  
  
  **Alapértelmezett**: Enabled  
  
- **Internet Explorer restricted zone popup blocker**  
  Ez a házirend-beállítással kezelheti, hogy nemkívánatos előugró ablak jelenik meg. Előugró ablakok nyílnak meg, amikor a végfelhasználó egy hivatkozásra kattint, nincsenek letiltva. Ha ez a szabályzatbeállítás engedélyezi, leggyakrabban nemkívánatos előugró ablakok ebben az esetben jelennek meg. Ha letiltja ezt a beállítást, az előugró windows nem nem jelenik meg. Ha nem konfigurálja ezt a beállítást, leggyakrabban nemkívánatos előugró ablakok ebben az esetben jelennek meg.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067180)  
  
  **Alapértelmezett**: Engedélyezés  
  
- **Az Internet Explorer folyamatok MK protokoll biztonsági korlátozása**  
  Az MK protokoll biztonsági korlátozása a házirend-beállítást csökkenti a támadási felület megakadályozzák, hogy az MK protokollt. Az MK protokollon sikertelen lesz. Ha ez a szabályzatbeállítás engedélyezi, a fájlkezelő és az Internet Explorer számára letiltja az MK protokollt, és az MK protokollon sikertelen lesz. Ha letiltja ezt a beállítást, az alkalmazások használhatják az MK-protokoll API-t. Az MK protokollon a Fájlkezelőben és az Internet Explorer folyamatok esetében működnek. Ha nem konfigurálja ezt a beállítást, a fájlkezelő és az Internet Explorer számára letiltja az MK protokollt, és az MK protokollon sikertelen lesz.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067179)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer megbízható zóna java-engedélyek**   
  A házirend-beállítás lehetővé teszi a Java-alkalmazások engedélyeinek kezelése. Ha ez a szabályzatbeállítás engedélyezi, beállítások választhat a legördülő listából. Egyéni engedélyek beállításait szabályozhatja a külön-külön. Alacsony biztonsági lehetővé teszi, hogy az alkalmazások összes műveletek végrehajtásához. Közepes biztonsági plusz szolgáltatásokat, például az ideiglenes terület (egy megbízható és biztonságos tároló terület az ügyfélszámítógépen) és a felhasználó általi fájl i/o lehetővé teszi alkalmazások futtatását a védőfal (egy területen kívül, ami a program nem hívásokat a memóriában). Magas biztonsági lehetővé teszi, hogy az alkalmazások futtatását a tesztkörnyezetben. Tiltsa le a Java használatával bármilyen kisalkalmazások tiltsa le a futását. Ha letiltja ezt a beállítást, a Java-alkalmazások nem futtatható. Ha nem konfigurálja ezt a beállítást, az engedély értéke alacsony biztonsági.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067200)  
  
  **Alapértelmezett**: Magas biztonsági  
  
- **Az Internet Explorer korlátozott kisalkalmazások parancsprogramok zóna**  
  A házirend-beállítás lehetővé teszi, hogy e kisalkalmazások érhetők el a zóna parancsfájlok kezelését. Ha ez a szabályzatbeállítás engedélyezi, a parancsfájlok kisalkalmazások automatikusan, felhasználói beavatkozás nélkül hozzáférhetnek. Kérdés választja a legördülő mezőben, ha a rendszer megkérdezi a felhasználókat, döntse el, hogy engedélyezi a parancsprogramokat alkalmazások eléréséhez. Ha letiltja ezt a beállítást, parancsfájlokat ebben az esetben a az alkalmazásainak elérését. Ha nem konfigurálja ezt a beállítást, parancsfájlokat ebben az esetben a az alkalmazásainak elérését.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067202)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer zárolja a Tiltott helyek zónához java-engedélyek**   
  A házirend-beállítás lehetővé teszi a Java-alkalmazások engedélyeinek kezelése. Ha ez a szabályzatbeállítás engedélyezi, beállítások választhat a legördülő listából. Egyéni engedélyek beállításait szabályozhatja a külön-külön. Alacsony biztonsági lehetővé teszi, hogy az alkalmazások összes műveletek végrehajtásához. Közepes biztonsági plusz szolgáltatásokat, például az ideiglenes terület (egy megbízható és biztonságos tároló terület az ügyfélszámítógépen) és a felhasználó általi fájl i/o lehetővé teszi alkalmazások futtatását a védőfal (egy területen kívül, ami a program nem hívásokat a memóriában). Magas biztonsági lehetővé teszi, hogy az alkalmazások futtatását a tesztkörnyezetben. Tiltsa le a Java használatával bármilyen kisalkalmazások tiltsa le a futását. Ha letiltja ezt a beállítást, a Java-alkalmazások nem futtatható. Ha nem konfigurálja ezt a beállítást, a Java-alkalmazások le vannak tiltva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067181)  
  
  **Alapértelmezett**: Tiltsa le a java 
  
- **Az Internet Explorer internetes zóna engedélyezése csak a jóváhagyott tartományok ActiveX-vezérlők használata**   
  A házirend-beállítás szabályozza, ha kéri a felhasználót, hogy engedélyezze az ActiveX-vezérlők futtathatók a webhelyeken a webhely, amelyen telepítve van az ActiveX-vezérlő nem. Ha ez a szabályzatbeállítás engedélyezi, kéri a felhasználót, az ActiveX-vezérlők a zóna webhelyekről futtatása előtt. A felhasználó választhat, hogy a vezérlő az aktuális helyről, vagy az összes helyről. Ha letiltja ezt a beállítást, a felhasználó nem látja a webhely szerinti ActiveX használatával, és a zónában lévő összes webhely ActiveX-vezérlők futtatható.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067091)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer minden hálózati elérési**  
  Az Internet Explorer az összes hálózati elérési utak közé tartozik.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067090)  
  
  **Alapértelmezett**: Letiltva 
  
- **Az Internet Explorer internetes zóna a védett mód**  
  A házirend-beállítás lehetővé teszi, hogy a védett mód bekapcsolása. A védett mód megvédi az Internet Explorer a kihasznált biztonsági réseket a helyeken, amelyek az Internet Explorer a beállításjegyzék és a fájlrendszerhez írhat csökkentésével. Ha ez a szabályzatbeállítás engedélyezi, védett üzemmód be van kapcsolva. A felhasználó nem a védett mód kikapcsolása. Ha letiltja ezt a beállítást, a védett mód ki van kapcsolva. A felhasználó nem a védett mód bekapcsolása. Ha nem konfigurálja ezt a beállítást, a felhasználó kapcsolja be, vagy kapcsolja ki a védett mód.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067171)  
  
  **Alapértelmezett**: Engedélyezés 
  
- **Az Internet Explorer az internet zóna inicializálása és parancsfájl Active X-vezérlők nem biztonságosként megjelölt**  
  Ez a szabályzatbeállítás nem biztonságosként megjelölt ActiveX-vezérlők kezelését teszi lehetővé. Ha ez a szabályzatbeállítás engedélyezi, az ActiveX-vezérlők, betöltött paraméterekkel és futtatása parancsfájlalapú objektum nem megbízható adatok vagy parancsfájlok biztonságának beállítása nélkül. Ezt a beállítást nem ajánlott, kivéve a biztonságos és felügyelt zónák. A beállítás hatására nem biztonságos, és a biztonságos vezérlők inicializálása és parancsprogrammal létrehozva, a rendszer figyelmen kívül hagyja az ActiveX-vezérlők biztonságosnak lehetőséget. Ha engedélyezi ezt a házirend-beállítást, és a legördülő mezőben válassza ki a kérdés, felhasználók kérdezhető le, hogy a vezérlő betöltés paramétereket az engedélyezi-e, vagy parancsprogram. Ha letiltja ezt a beállítást, a ActiveX-vezérlők nem tehető nem paraméterekkel betöltése vagy parancsprogrammal létrehozva. Ha nem konfigurálja ezt a beállítást, a ActiveX-vezérlők nem tehető nem paraméterekkel betöltése vagy parancsprogrammal létrehozva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067170)  
  
  **Alapértelmezett**: Letiltás 
  
- **Az Internet Explorer SmartScreen tiltott helyek zónához zárolva**   
  Ez a házirend-beállítással megadható, hogy a SmartScreen szűrő megvizsgálja a rosszindulatú zóna oldalak. Ha ez a szabályzatbeállítás engedélyezi, a SmartScreen szűrő megvizsgálja a rosszindulatú zóna oldalak. Ha letiltja ezt a beállítást, a SmartScreen szűrő a rosszindulatú zóna oldal nem beolvasása. Ha nem konfigurálja ezt a beállítást, a felhasználó választhat megvizsgálja-e a SmartScreen szűrő az oldalakat a rosszindulatú zóna. Megjegyezés: Az Internet Explorer 7 a házirend-beállítás meghatározza, hogy megvizsgálja-e adathalász szűrő oldalak rosszindulatú zónában.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067092)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer összeomlási észlelése**  
  A házirend-beállítás lehetővé teszi, hogy az összeomlási észlelési funkcióját kiegészítő felügyeleti kezelheti. Ha ez a szabályzatbeállítás engedélyezi, az Internet Explorer összeomlás verziójának megfelelően viselkedik a Windows XP Professional Service Pack 1 és korábbi verzióiban, nevezetesen meghívni a Windows hibajelentés. Az összes házirend-beállítások a Windows hibajelentés továbbra is a alkalmazni. Ha letiltja vagy nem konfigurálja ezt a beállítást, az összeomlási duplikálásészlelési szolgáltatását a kiegészítő felügyeleti működőképességét.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067094)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer internetes zóna java-engedélyek**  
  A házirend-beállítás lehetővé teszi a Java-alkalmazások engedélyeinek kezelése. Ha ez a szabályzatbeállítás engedélyezi, beállítások választhat a legördülő listából. Egyéni engedélyek beállításait szabályozhatja a külön-külön. Alacsony biztonsági lehetővé teszi, hogy az alkalmazások összes műveletek végrehajtásához. Közepes biztonsági plusz szolgáltatásokat, például az ideiglenes terület (egy megbízható és biztonságos tároló terület az ügyfélszámítógépen) és a felhasználó általi fájl i/o lehetővé teszi alkalmazások futtatását a védőfal (egy területen kívül, ami a program nem hívásokat a memóriában). Magas biztonsági lehetővé teszi, hogy az alkalmazások futtatását a tesztkörnyezetben. Tiltsa le a Java használatával bármilyen kisalkalmazások tiltsa le a futását. Ha letiltja ezt a beállítást, a Java-alkalmazások nem futtatható. Ha nem konfigurálja ezt a beállítást, az engedély értéke magas biztonsági.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067174)  
  
  **Alapértelmezett**: Tiltsa le a java  
  
- **Az Internet Explorer korlátozott zóna active scripting**  
  Ez a házirend-beállítással kezelheti, hogy fut a zónában lévő lapok a parancsfájl kód. Ha ez a szabályzatbeállítás engedélyezi, a zónában lévő lapok szkriptkódot automatikusan futtathatók. Kérdés a legördülő mezőben válassza ki, ha a rendszer megkérdezi a felhasználókat, hogy a parancsfájl kód futtatásához a zónában lévő lapok teszi lehetővé e. Ha letiltja a beállítást, a szkriptkód a lapok zónában nem futtathatók. Ha nem konfigurálja ezt a beállítást, a zónában lévő lapok szkriptkódot nem futtathatók.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067172)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer internetes zóna bejelentkezési beállítások**  
  A házirend-beállítás lehetővé teszi, hogy a bejelentkezési lehetőségek beállításainak kezelése. Ha ez a szabályzatbeállítás engedélyezi, a következő bejelentkezési lehetőségek közül választhat. Tiltsa le a HTTP-hitelesítést és -felhasználási névtelen bejelentkezés a Vendég fiók csak a Common Internet File System (CIFS) protokollhoz. Felhasználónév és jelszó kérése tartozó felhasználói azonosítók és jelszavak. Miután egy felhasználó kérdeznek le, ezeket az értékeket használható csendes a munkamenet hátralévő részére. Automatikus bejelentkezés csak az Intranet zónába tartozó felhasználói azonosítók és jelszavak a más zónákban lekérdezés felhasználóinak. Után a felhasználó lekérdezése követi, ezeket az értékeket a a munkamenet hátralevő beavatkozás nélkül is használni. Automatikus bejelentkezés aktuális felhasználónevet és jelszót megpróbálja bejelentkezés Windows NT kérdés-válasz (más néven az NTLM-hitelesítés) használatával. Ha a kiszolgáló támogatja a Windows NT kérdés-válasz, a bejelentkezést a felhasználói hálózati felhasználónevet és jelszót a bejelentkezéshez használ. Ha a kiszolgáló nem támogatja a Windows NT kérdés-válasz, a felhasználó lekérdezése követi, a felhasználónév és a jelszót. Ha letiltja ezt a beállítást, bejelentkezési értéke napló automatikus a csak az Intranet zónában. Ha nem konfigurálja ezt a beállítást, jelentkezzen be az automatikus bejelentkezési értéke csak az Intranet zóna.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067194)  
  
  **Alapértelmezett**: Kérdés  
  
- **Internet Explorer restricted zone allow vbscript to run**   
  Ez a házirend-beállítással kezelheti, hogy VBScript futtathatja a lapokon az Internet Explorerben a megadott zónában. A legördülő listában kiválasztott engedélyezése, ha a VBScript felhasználói beavatkozás nélkül futtatható. A legördülő listában kiválasztott kérése, ha rendszer kéri a felhasználóktól, hogy a VBScript futtatását engedélyezi-e. A legördülő listában kiválasztott tiltsa le, ha VBScript nem futtathatók. Ha nem konfigurálja, vagy tiltsa le a házirend-beállítás, VBScript nem futtathatók.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067173)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer az internet zóna húzza tartalmat más tartományokból keresztül windows**  
  A házirend-beállítás lehetővé teszi a húzással tartalom egyik tartományból egy másik tartományba Ha a forrás- és a különböző windows beállításainak megadása. Ha engedélyezi ezt a házirend-beállítást, és kattintson az engedélyezés, felhasználók húzza tartalom egyik tartományból egy másik tartományba Ha a forrás- és a különböző windows. Felhasználók nem módosíthatják ezt a beállítást. Ha engedélyezi ezt a házirend-beállítást, és kattintson a Letiltás elemre, felhasználók nem húzható tartalom egyik tartományból egy másik tartományba Ha a forrás- és a különböző windows. Felhasználók nem módosíthatják ezt a beállítást. Az Internet Explorer 10 Ha ezt a beállítást letiltja vagy nem konfigurálja, felhasználók nem húzható tartalom egyik tartományából egy másik tartományba Ha a forrás- és a különböző windows. A felhasználók módosíthatják ezt a beállítást az Internetbeállítások párbeszédpanelt. Az Internet Explorer 9 és korábbi verzióiban Ha ez a szabályzat letiltja vagy nem konfigurálja, felhasználók húzhatja tartalom egyik tartományából egy másik tartományba Ha a forrás- és a különböző windows. Felhasználók nem módosíthatják ezt a beállítást.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067093)  
  
  **Alapértelmezett**: Letiltva 
  
- **Az Internet Explorer intranetes zóna inicializálása és parancsfájl Active X-vezérlők nem biztonságosként megjelölt**  
  Ez a szabályzatbeállítás nem biztonságosként megjelölt ActiveX-vezérlők kezelését teszi lehetővé. Ha ez a szabályzatbeállítás engedélyezi, az ActiveX-vezérlők, betöltött paraméterekkel és futtatása parancsfájlalapú objektum nem megbízható adatok vagy parancsfájlok biztonságának beállítása nélkül. Ezt a beállítást nem ajánlott, kivéve a biztonságos és felügyelt zónák. A beállítás hatására nem biztonságos, és a biztonságos vezérlők inicializálása és parancsprogrammal létrehozva, a rendszer figyelmen kívül hagyja az ActiveX-vezérlők biztonságosnak lehetőséget. Ha engedélyezi ezt a házirend-beállítást, és a legördülő mezőben válassza ki a kérdés, felhasználók kérdezhető le, hogy a vezérlő betöltés paramétereket az engedélyezi-e, vagy parancsprogram. Ha letiltja ezt a beállítást, a ActiveX-vezérlők nem tehető nem paraméterekkel betöltése vagy parancsprogrammal létrehozva. Ha nem konfigurálja ezt a beállítást, a ActiveX-vezérlők nem tehető nem paraméterekkel betöltése vagy parancsprogrammal létrehozva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067175)  
  
  **Alapértelmezett**: Letiltás 
  
- **Az Internet Explorer letöltési ház**  
  A házirend-beállítás megakadályozza, hogy a felhasználó kellene (fájlmellékletek) házak letöltve az hírcsatorna a felhasználó számítógépén. Ha ez a szabályzatbeállítás engedélyezi, a felhasználó nem állítható be a hírcsatorna-szinkronizálási motor letölteni egy ház hírcsatorna tulajdonságok oldalán keresztül. A fejlesztő nem módosítható a letöltési beállítását a hírcsatorna-API-kon keresztül. Ha letiltja vagy nem konfigurálja ezt a beállítást, a felhasználó beállíthat egy ház hírcsatorna tulajdonságok oldalán keresztül letöltéséhez a hírcsatorna-szinkronizálási motor. A fejlesztők a letöltési beállítást a hírcsatorna-API-k segítségével módosíthatja.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067245)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zóna töltse le a nem aláírt ActiveX-vezérlők**  
  Ez a házirend-beállítással kezelheti, hogy a felhasználók letölthetnek aláíratlan ActiveX-vezérlők a zónából. Az ilyen kódja potenciálisan káros, különösen akkor, ha egy nem megbízható zóna származik. Ha ez a szabályzatbeállítás engedélyezi, az aláírás nélküli vezérlők felhasználói beavatkozás nélkül futtathatók. Kérdés a legördülő mezőben válassza ki, ha a rendszer megkérdezi a felhasználókat, döntse el, hogy az adott vezérlőt futtatásához. Ha letiltja ezt a beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket. Ha nem konfigurálja ezt a beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067177)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer az internet zóna tartalom húzza az eltérő tartományokban időkereten belül**  
  Ez a házirend-beállítással kezelheti, hogy a felhasználók letölthetnek aláíratlan ActiveX-vezérlők a zónából. Az ilyen kódja potenciálisan káros, különösen akkor, ha egy nem megbízható zóna származik. Ha ez a szabályzatbeállítás engedélyezi, az aláírás nélküli vezérlők felhasználói beavatkozás nélkül futtathatók. Kérdés a legördülő mezőben válassza ki, ha a rendszer megkérdezi a felhasználókat, döntse el, hogy az adott vezérlőt futtatásához. Ha letiltja ezt a beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket. Ha nem konfigurálja ezt a beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067095)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer folyamatok korlátozása Active X-telepítés**   
  A házirend-beállítás lehetővé teszi, hogy a webböngésző vezérlőt tartalmazó alkalmazások letiltása, az ActiveX-vezérlő telepítésére kérő üzenet automatikus. Ha ez a szabályzatbeállítás engedélyezi, a webböngésző vezérlő letiltja az összes folyamat ActiveX-vezérlő telepítésére kérő üzenet automatikus. Ha letiltja vagy nem konfigurálja ezt a beállítást, a webböngésző vezérlőelem nem blokkolja az összes folyamat ActiveX-vezérlő telepítésére kérő üzenet automatikus.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067250)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer internetes zóna Szkriptletek**  
  Ez a házirend-beállítással kezelheti, hogy a felhasználó futtathatja a Szkriptletek. Ha ez a szabályzatbeállítás engedélyezi, akkor a felhasználó Szkriptletek futtathatja. Ha letiltja ezt a beállítást, a felhasználó Szkriptletek nem futtatható. Ha nem konfigurálja ezt a beállítást, a felhasználó engedélyezheti vagy letilthatja a Szkriptletek.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067176)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zóna húzza és dobja el, vagy másolja és illessze be a fájlokat**  
  Ez a házirend-beállítással kezelheti, hogy a felhasználók húzással vagy másolással illessze be a zónán belüli forrásból származó fájlokat. Ha ez a szabályzatbeállítás engedélyezi, a felhasználók vagy másolással húzza át és illessze be a zóna fájlok automatikusan. Kérdés a legördülő mezőben válassza ki, ha a rendszer megkérdezi a felhasználókat, hogy e húzással, vagy a fájlok másolása a zóna. Ha letiltja ezt a beállítást, a rendszer megakadályozza a felhasználókat a fájlok húzással másolással és beillesztéssel fájlokat ebben a zónában. Ha nem konfigurálja ezt a beállítást, a rendszer megkérdezi a felhasználókat, hogy e húzással, vagy a fájlok másolása a zónában.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067096)  
  
  **Alapértelmezett**: Letiltás  
  
- **Ha az aláírás érvénytelen az Internet Explorer szoftver**  
  Ez a házirend-beállítással kezelheti, hogy a szoftverek, például az ActiveX-vezérlők és letöltéseket, telepítve van, vagy a felhasználó által futtatott, annak ellenére, hogy az aláírás érvénytelen. Az érvénytelen aláírása jelezheti, hogy valaki módosította a fájlt. Ha ez a szabályzatbeállítás engedélyezi, a gép telepítéséhez, vagy az érvénytelen aláírással rendelkező fájlok futtatásának felkéri a felhasználókat. Ha letiltja ezt a beállítást, a felhasználók nem futtatásához vagy az érvénytelen aláírással rendelkező fájlok telepítése. Ha nem konfigurálja a házirendet, felhasználók eldönthetik, vagy az érvénytelen aláírással rendelkező fájlok telepítése.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067201)
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zóna másolja be a parancsfájl-n keresztül**  
  Ez a házirend-beállítással kezelheti-e parancsfájlokat egy vágólapi műveletet (például a kivágási, másolási és beillesztési) hajthat végre egy meghatározott régióban. Ha ez a szabályzatbeállítás engedélyezi, akkor a parancsfájl egy vágólapra művelet hajtható végre. Ha a parancssorban a legördülő mezőben válassza ki, a rendszer megkérdezi a felhasználókat, hogy a vágólap műveletek végrehajtásához. Ha letiltja ezt a beállítást, akkor a parancsfájl egy vágólapra operaci nelze provést. Ha nem konfigurálja ezt a beállítást, akkor a parancsfájl egy vágólapra operaci nelze provést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067165)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zóna húzza tartalmat más tartományokból keresztül windows**  
  A házirend-beállítás lehetővé teszi a húzással tartalom egyik tartományból egy másik tartományba Ha a forrás- és a különböző windows beállításainak megadása. Ha engedélyezi ezt a házirend-beállítást, és kattintson az engedélyezés, felhasználók húzza tartalom egyik tartományból egy másik tartományba Ha a forrás- és a különböző windows. Felhasználók nem módosíthatják ezt a beállítást. Ha engedélyezi ezt a házirend-beállítást, és kattintson a Letiltás elemre, felhasználók nem húzható tartalom egyik tartományból egy másik tartományba Ha a forrás- és a különböző windows. Felhasználók nem módosíthatják ezt a beállítást. Az Internet Explorer 10 Ha ezt a beállítást letiltja vagy nem konfigurálja, felhasználók nem húzható tartalom egyik tartományából egy másik tartományba Ha a forrás- és a különböző windows. A felhasználók módosíthatják ezt a beállítást az Internetbeállítások párbeszédpanelt. Az Internet Explorer 9 és korábbi verzióiban Ha ez a szabályzat letiltja vagy nem konfigurálja, felhasználók húzhatja tartalom egyik tartományából egy másik tartományba Ha a forrás- és a különböző windows. Felhasználók nem módosíthatják ezt a beállítást.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067166)   

  **Alapértelmezett**: Letiltva  
  
- **Webhelyek hozzáadása az Internet Explorer-felhasználók**  
  Megakadályozza, hogy a felhasználók hozzáadásának vagy eltávolításának a helyek biztonsági zónából. A biztonsági zóna egy azonos biztonsági szintű webhelyek csoportja. Ha engedélyezi ezt a házirendet, a biztonsági zónák a hely felügyeleti beállítások le vannak tiltva. (Megtekintéséhez a hely felügyeleti biztonsági zónák Internetbeállítások párbeszédpanelen beállításait a biztonság lapon, és kattintson a helyek gombra.) Ha letiltja ezt a házirendet, vagy nem konfigurálja, a felhasználók hozzáadhatnak webhelyek vagy távolíthat el azokból a megbízható helyek és a Tiltott helyek zóna, és módosítsa a beállításokat a Helyi Intranet zónához. Ez a szabályzat megakadályozza, hogy a felhasználók megváltoztassák a hely felügyeleti beállításait a rendszergazda által létrehozott biztonsági zónák. Megjegyezés: A "Tiltsa le a Biztonság lap" házirend (\User Configuration\Administrative sablonok\Windows-összetevők\Internet Explorer\Internet Vezérlőpulton található), amely eltávolítja a biztonság lapon a felhasználói felületről, elsőbbséget élvez a szabályzat. Ha engedélyezve van, a rendszer figyelmen kívül hagyja ezt a házirendet. Lásd még a "biztonsági zónák: A szabályzat csak a számítógép beállításainak használata".  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067167)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer internetes zóna parancsfájl indított windows**  
  A házirend-beállítás lehetővé teszi, hogy korlátozásokat előugró ablakok parancsfájl által kezdeményezett, és a title és az állapot sávok tartalmazó windows kezelheti. Ha ez a szabályzatbeállítás engedélyezi, biztonsági Windows korlátozásai nem vonatkoznak a zóna. A biztonsági zónában, ez a szolgáltatás által biztosított biztonsági réteggel nélkül futtatja. Ha letiltja ezt a beállítást, a parancsfájl által kezdeményezett előugró ablakok és a title és az állapot sávok tartalmazó windows lehetséges káros műveleteket nem futtatható. Az Internet Explorer biztonsági szolgáltatása megegyezik az ebben a zónában szolgáltatásvezérlő a Windows biztonsági korlátozások parancsprogrammal létrehozva a folyamat állítja. Ha nem konfigurálja ezt a beállítást, a parancsfájl által kezdeményezett előugró ablakok és a title és az állapot sávok tartalmazó windows lehetséges káros műveleteket nem futtatható. Az Internet Explorer biztonsági szolgáltatása megegyezik az ebben a zónában szolgáltatásvezérlő a Windows biztonsági korlátozások parancsprogrammal létrehozva a folyamat állítja.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067088)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer biztonsági zónák használata csak a gép beállításait**  
  Információ a biztonsági zóna, az adott számítógép minden felhasználóra vonatkozik. A biztonsági zóna egy azonos biztonsági szintű webhelyek csoportja. Ha engedélyezi ezt a házirendet, a biztonsági zóna a felhasználó által végrehajtott módosítások az adott számítógép minden felhasználóra vonatkozni fog. Ha letiltja ezt a házirendet, vagy nem konfigurálja, ugyanazon a számítógépen a felhasználók a saját biztonsági zónájának beállításai is létrehozhat. Ez a szabályzat használatával győződjön meg arról, hogy biztonsági zónájának beállításai alkalmazása egységesen ugyanazon a számítógépen, és felhasználónként nem változnak. Lásd még a "biztonsági zónák: nem engedélyezi a felhasználók módosíthatják a szabályzatokat" szabályzat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067086)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer zárolja a helyi gép zóna java-engedélyek**  
  A házirend-beállítás lehetővé teszi a Java-alkalmazások engedélyeinek kezelése. Ha ez a szabályzatbeállítás engedélyezi, beállítások választhat a legördülő listából. Egyéni engedélyek beállításait szabályozhatja a külön-külön. Alacsony biztonsági lehetővé teszi, hogy az alkalmazások összes műveletek végrehajtásához. Közepes biztonsági plusz szolgáltatásokat, például az ideiglenes terület (egy megbízható és biztonságos tároló terület az ügyfélszámítógépen) és a felhasználó általi fájl i/o lehetővé teszi alkalmazások futtatását a védőfal (egy területen kívül, ami a program nem hívásokat a memóriában). Magas biztonsági lehetővé teszi, hogy az alkalmazások futtatását a tesztkörnyezetben. Tiltsa le a Java használatával bármilyen kisalkalmazások tiltsa le a futását. Ha letiltja ezt a beállítást, a Java-alkalmazások nem futtatható. Ha nem konfigurálja ezt a beállítást, a Java-alkalmazások le vannak tiltva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067253) 
  
  **Alapértelmezett**: Tiltsa le a java 
  
- **Az Internet Explorer korlátozott zóna nem futtatásához kártevőirtó ActiveX-vezérlők**   
  A házirend-beállítás meghatározza, hogy az Internet Explorer fut-e kártevőirtó-programok ellen ActiveX-vezérlők annak ellenőrzéséhez, hogy azok biztonságos voltát oldalain betölteni. Ha ez a szabályzatbeállítás engedélyezi, az Internet Explorer nem egyeztessen a kártevőirtó programot, hogy hozzon létre egy példányt az ActiveX-vezérlő való biztonságos megtekintéséhez. Ha letiltja ezt a beállítást, az Internet Explorer mindig ellenőrzi a kártevőirtó programot, hogy hozzon létre egy példányt az ActiveX-vezérlő való biztonságos megtekintéséhez. Ha nem konfigurálja ezt a beállítást, az Internet Explorer mindig ellenőrzi a kártevőirtó programot, hogy hozzon létre egy példányt az ActiveX-vezérlő való biztonságos megtekintéséhez. Bármikor ezt a viselkedést be- vagy kikapcsolása az Internet Explorer biztonsági beállításokkal.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067089)
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zóna futtatása a .NET-keretrendszer authenticode aláírással rendelkező tartománybeli összetevők**  
  Ez a házirend-beállítással kezelheti, hogy a .NET-keretrendszer összetevők, az Authenticode aláírással rendelkező hajthat végre az Internet Explorer. Ezen összetevők közé tartozik egy objektum címke és a egy hivatkozást a hivatkozott felügyelt végrehajtható fájlok a hivatkozott felügyelt szabályozza. Ha ez a szabályzatbeállítás engedélyezi, az Internet Explorer végrehajtja a aláírt felügyelt összetevőket. Kérdés a legördülő mezőben válassza ki, ha az Internet Explorer kéri a felhasználó határozza meg, hogy aláírt felügyelt összetevőket végrehajtásához. Ha letiltja ezt a beállítást, az Internet Explorer aláírt felügyelt összetevőket nem hajtható végre. Ha nem konfigurálja ezt a beállítást, az Internet Explorer aláírt felügyelt összetevőket nem hajtható végre.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067169)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer korlátozott zóna hozzáférés adatforrásokhoz**  
  Ez a házirend-beállítással kezelheti, hogy az Internet Explorer érhessék el az adatokat a Microsoft XML Parser (MSXML) vagy ActiveX Data Objects (ADO) használatával egy másik biztonsági zónából. Ha ez a szabályzatbeállítás engedélyezi, a felhasználók betölthetnek egy oldal, amely az MSXML vagy ADO használ a zóna egy másik helyről származó adatok eléréséhez a zónában. Kérdés a legördülő mezőben válassza ki, ha a rendszer megkérdezi a felhasználókat, döntse el, hogy engedélyezi, hogy a lap betöltése a zónában, amelyek az MSXML vagy ADO segítségével érheti el adatait a zónában egy másik helyről. Ha letiltja ezt a beállítást, a felhasználók nem tudják betölteni egy oldal, amely az MSXML vagy ADO használ a zóna egy másik helyről származó adatok eléréséhez a zónában. Ha nem konfigurálja ezt a beállítást, a felhasználók nem tudják betölteni egy oldal, amely az MSXML vagy ADO használ a zóna egy másik helyről származó adatok eléréséhez a zónában.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067161)  
  
  **Alapértelmezett**: Letiltás 
  
- **Az Internet Explorer az internet zóna nem kártevőirtó futtatásához ActiveX-vezérlők**  
  A házirend-beállítás meghatározza, hogy az Internet Explorer fut-e kártevőirtó-programok ellen ActiveX-vezérlők annak ellenőrzéséhez, hogy azok biztonságos voltát oldalain betölteni. Ha ez a szabályzatbeállítás engedélyezi, az Internet Explorer nem egyeztessen a kártevőirtó programot, hogy hozzon létre egy példányt az ActiveX-vezérlő való biztonságos megtekintéséhez. Ha letiltja ezt a beállítást, az Internet Explorer mindig ellenőrzi a kártevőirtó programot, hogy hozzon létre egy példányt az ActiveX-vezérlő való biztonságos megtekintéséhez. Ha nem konfigurálja ezt a beállítást, az Internet Explorer mindig ellenőrzi a kártevőirtó programot, hogy hozzon létre egy példányt az ActiveX-vezérlő való biztonságos megtekintéséhez. Bármikor ezt a viselkedést be- vagy kikapcsolása az Internet Explorer biztonsági beállításokkal.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067162)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer internetes zóna másolja be a parancsfájl-n keresztül**  
  Ez a házirend-beállítással kezelheti-e parancsfájlokat egy vágólapi műveletet (például a kivágási, másolási és beillesztési) hajthat végre egy meghatározott régióban. Ha ez a szabályzatbeállítás engedélyezi, akkor a parancsfájl egy vágólapra művelet hajtható végre. Ha a parancssorban a legördülő mezőben válassza ki, a rendszer megkérdezi a felhasználókat, hogy a vágólap műveletek végrehajtásához. Ha letiltja ezt a beállítást, akkor a parancsfájl egy vágólapra operaci nelze provést. Ha nem konfigurálja ezt a beállítást, akkor a parancsfájl egy vágólapra művelet hajtható végre.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067084)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer Active X-telepítő szolgáltatás használata**  
  A házirend-beállítás lehetővé teszi, hogy adja meg, hogyan legyenek telepítve a ActiveX-vezérlőket. Ha ez a szabályzatbeállítás engedélyezi, az ActiveX-vezérlők települnek, csak akkor, ha az ActiveX Telepítőszolgáltatás jelen, és az ActiveX-vezérlők telepítésének engedélyezésére van konfigurálva. Ha letiltja vagy nem konfigurálja ezt a beállítást, a ActiveX-vezérlők, felhasználónkénti vezérlőiket, beleértve a szabványos telepítési folyamat során lesz telepítve.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067163)
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer dolgozza fel a zóna jogok kiterjesztése elleni védelem**  
  Az Internet Explorer korlátozásokat minden lap nyílik meg. A korlátozások vonatkoznak (az Internet, intranetes, helyi zónán és így tovább) weblap helyétől. Például a helyi számítógépen weblapok rendelkezik korlátozásokat és a helyi számítógép zónában, ezek a helyi gép zónában egy rosszindulatú felhasználók a legkevesebb. Ha ez a szabályzatbeállítás engedélyezi, minden zónában is védeni kell az összes folyamat zóna jogosultságszint-emelési. Ha letiltja vagy nem konfigurálja ezt a beállítást, az Internet Explorer és a folyamat listán lévő folyamatok nincs ilyen védelem jelenik meg.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067160)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer az internet zóna előjel nélküli ActiveX-vezérlők letöltése**   
  Ez a házirend-beállítással kezelheti, hogy a felhasználók letölthetnek aláíratlan ActiveX-vezérlők a zónából. Az ilyen kódja potenciálisan káros, különösen akkor, ha egy nem megbízható zóna származik. Ha ez a szabályzatbeállítás engedélyezi, az aláírás nélküli vezérlők felhasználói beavatkozás nélkül futtathatók. Kérdés a legördülő mezőben válassza ki, ha a rendszer megkérdezi a felhasználókat, döntse el, hogy az adott vezérlőt futtatásához. Ha letiltja ezt a beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket. Ha nem konfigurálja ezt a beállítást, a felhasználók nem futtathatnak aláíratlan vezérlőket.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067325)
  
  **Alapértelmezett**: Letiltás  
  
- **Keresse meg a windows és a keretek az Internet Explorer az internet zóna különböző tartományokban**   
  A házirend-beállítás lehetővé teszi a különböző tartományokban nyithatja meg a windows és a keretek és alkalmazások kezelését. Ha ez a szabályzatbeállítás engedélyezi, felhasználó meg tudja nyitni a windows és a keretek más tartományok és más tartományokból alkalmazásokat. Ha kérdés választja a legördülő mezőben, megkérdezi a felhasználót, hogy a windows és más tartományokból alkalmazások eléréséhez keretek-e. Ha letiltja ezt a beállítást, a felhasználók nem tudják megnyitni, windows és bármely más tartományokból alkalmazások eléréséhez. Ha nem konfigurálja ezt a beállítást, felhasználó meg tudja nyitni a windows és a keretek más tartományok és más tartományokból alkalmazásokat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067083)  
  
  **Alapértelmezett**: Letiltás  
  
- **Az Internet Explorer internetes zóna frissítések állapotsor parancsfájl használatával**  
  Ezzel a szabályzatbeállítással kezelheti, hogy egy parancsfájl frissítheti a zónához állapotsorának teszi lehetővé. Ha ez a szabályzatbeállítás engedélyezi, a parancsfájlok frissítheti az állapotsorban. Ha letiltja vagy nem konfigurálja ezt a beállítást, parancsfájl az állapotsor frissítése nem engedélyezett.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067087)  
  
  **Alapértelmezett**: Letiltva  
  
- **A fájlok feltöltése a kiszolgáló szerepeljen az Internet Explorer korlátozott zóna helyi elérési útja**  
  Ez a házirend-beállítást vezérli, hogy a helyi elérési úttal kapcsolatos információkat akkor küldi a rendszer, amikor a felhasználó tölti fel egy fájlt egy HTML-űrlapot. A helyi elérési út adatokat küld, ha néhány információt előfordulhat, hogy véletlenül is megjeleníthetők a kiszolgálóhoz. Például a felhasználó asztali küldött fájlokat tartalmazhat az elérési út részeként a felhasználó nevét. Amikor a felhasználó tölti fel egy fájlt egy HTML-űrlapot, ha ez a szabályzatbeállítás engedélyezi, a rendszer elküldi az elérési út adatokat. Amikor a felhasználó egy HTML-űrlapot egy fájlt tölt, ha letiltja ezt a beállítást, a rendszer eltávolítja az elérési úttal kapcsolatos információkat. Ha nem konfigurálja ezt a beállítást, a felhasználó dönthet úgy, hogy küld-e elérési úttal kapcsolatos információkat, amikor egy fájl egy HTML-űrlaphoz keresztül töltenek. Alapértelmezés szerint az útvonal-információinak zajlik.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067085)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer folyamatok korlátozása fájl letöltése**   
  A házirend-beállítás lehetővé teszi, hogy a webböngésző vezérlőt tartalmazó alkalmazás blokkolja a fájlok letöltése, amely nem a felhasználó által kezdeményezett automatikus kérő üzenet. Ha ez a szabályzatbeállítás engedélyezi, a webböngésző vezérlő blokkolja a fájlok letöltése, amely nem a felhasználó által kezdeményezett összes folyamat automatikus kérő üzenet. Ha letiltja ezt a beállítást, a webböngésző vezérlő letiltása nem letöltéseket, amelyek nem a felhasználó által kezdeményezett összes folyamat automatikus kérő üzenet.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067164)  
  
  **Alapértelmezett**: Enabled  
  
- **Tiltott helyek zónához engedélyezése az Internet Explorer csak a jóváhagyott tartományok ActiveX-vezérlők használata**   
  A házirend-beállítás szabályozza, ha kéri a felhasználót, hogy engedélyezze az ActiveX-vezérlők futtathatók a webhelyeken a webhely, amelyen telepítve van az ActiveX-vezérlő nem. Ha ez a szabályzatbeállítás engedélyezi, kéri a felhasználót, az ActiveX-vezérlők a zóna webhelyekről futtatása előtt. A felhasználó választhat, hogy a vezérlő az aktuális helyről, vagy az összes helyről. Ha letiltja ezt a beállítást, a felhasználó nem látja a webhely szerinti ActiveX használatával, és a zónában lévő összes webhely ActiveX-vezérlők futtatható.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067233)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer korlátozott zóna inicializálása és parancsfájl Active X-vezérlők nem biztonságosként megjelölt**  
  Ez a szabályzatbeállítás nem biztonságosként megjelölt ActiveX-vezérlők kezelését teszi lehetővé. Ha ez a szabályzatbeállítás engedélyezi, az ActiveX-vezérlők, betöltött paraméterekkel és futtatása parancsfájlalapú objektum nem megbízható adatok vagy parancsfájlok biztonságának beállítása nélkül. Ezt a beállítást nem ajánlott, kivéve a biztonságos és felügyelt zónák. A beállítás hatására nem biztonságos, és a biztonságos vezérlők inicializálása és parancsprogrammal létrehozva, a rendszer figyelmen kívül hagyja az ActiveX-vezérlők biztonságosnak lehetőséget. Ha engedélyezi ezt a házirend-beállítást, és a legördülő mezőben válassza ki a kérdés, felhasználók kérdezhető le, hogy a vezérlő betöltés paramétereket az engedélyezi-e, vagy parancsprogram. Ha letiltja ezt a beállítást, a ActiveX-vezérlők nem tehető nem paraméterekkel betöltése vagy parancsprogrammal létrehozva. Ha nem konfigurálja ezt a beállítást, a ActiveX-vezérlők nem tehető nem paraméterekkel betöltése vagy parancsprogrammal létrehozva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067097)  
  
  **Alapértelmezett**: Letiltás  
  
- **Internet Explorer felhasználói házirendek módosítása**  
  A felhasználók nem módosíthatják a biztonsági zóna beállításait. A biztonsági zóna egy azonos biztonsági szintű webhelyek csoportja. Ha engedélyezi ezt a házirendet, az Egyéni szint gombra, és a biztonság lapon az Internetbeállítások párbeszédpanelen biztonsági szintű csúszka le vannak tiltva. Ha letiltja ezt a házirendet, vagy nem konfigurálja, a felhasználók megváltoztathatják a beállításokat a biztonsági zónák. Ez a szabályzat megakadályozza, hogy a felhasználók a rendszergazda által létrehozott biztonsági zónájának beállításai megváltoztassa. Megjegyezés: A "Letiltás a Biztonság lap" házirend (\User Configuration\Administrative sablonok\Windows-összetevők\Internet Explorer\Internet Vezérlőpult), amely eltávolítja a biztonság lapon a Vezérlőpult Internet Explorer, elsőbbséget élvez Ez a házirend. Ha engedélyezve van, a rendszer figyelmen kívül hagyja ezt a házirendet. Lásd még a "biztonsági zónák: A szabályzat csak a számítógép beállításainak használata".  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067155)  
    
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zóna a védett mód**  
  A házirend-beállítás lehetővé teszi, hogy a védett mód bekapcsolása. A védett mód megvédi az Internet Explorer a kihasznált biztonsági réseket a helyeken, amelyek az Internet Explorer a beállításjegyzék és a fájlrendszerhez írhat csökkentésével. Ha ez a szabályzatbeállítás engedélyezi, védett üzemmód be van kapcsolva. A felhasználó nem a védett mód kikapcsolása. Ha letiltja ezt a beállítást, a védett mód ki van kapcsolva. A felhasználó nem a védett mód bekapcsolása. Ha nem konfigurálja ezt a beállítást, a felhasználó kapcsolja be, vagy kapcsolja ki a védett mód.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067080)  
  
  **Alapértelmezett**: Engedélyezés  
  
- **Az Internet Explorer internetes zóna felhasználói adatmegőrzés**  
  Ez a házirend-beállítással kezelheti az a böngészési előzményeket, a Kedvencek, XML-tárolóban, vagy közvetlenül egy weblap, lemezre menti az adatok megőrzését. Amikor egy felhasználó egy megőrzött oldalhoz adja vissza, az oldal állapotát visszaállíthatók, ha megfelelően van-e konfigurálva a házirend-beállítás. Ha ez a szabályzatbeállítás engedélyezi, a felhasználó a böngészési előzményeket, a Kedvencek, XML-tárolóban, vagy közvetlenül egy weblap, lemezre menti az adatokat megőrizheti. Ha letiltja ezt a beállítást, a felhasználók nem megőrzése a böngészési előzményeket, a Kedvencek, XML-tárolóban, vagy közvetlenül egy weblap, lemezre menti az adatokat. Ha nem konfigurálja ezt a beállítást, a felhasználó a böngészési előzményeket, a Kedvencek, XML-tárolóban, vagy közvetlenül egy weblap, lemezre menti az adatokat megőrizheti.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067156)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer internetes zóna parancsprogramok webes böngészővezérlők**  
 
  A házirend-beállítás meghatározza, hogy e lap szabályozhatja a beágyazott WebBrowser vezérlők parancsfájl használatával. Ha ez a szabályzatbeállítás engedélyezi, a parancsfájl hozzáférést ovládací prvek WebBrowser engedélyezett. Ha letiltja ezt a beállítást, ovládací prvek WebBrowser parancsfájlok hozzáférése nem engedélyezett. Ha nem konfigurálja ezt a beállítást, a felhasználó engedélyezheti vagy letilthatja ovládací prvek WebBrowser parancsfájl-hozzáférését. Alapértelmezés szerint csak az intranetes zónák és helyi számítógép ovládací prvek WebBrowser parancsfájl hozzáférést engedélyezett.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067157)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zóna felhasználói adatok megőrzése**  
  Ez a házirend-beállítással kezelheti az a böngészési előzményeket, a Kedvencek, XML-tárolóban, vagy közvetlenül egy weblap, lemezre menti az adatok megőrzését. Amikor egy felhasználó egy megőrzött oldalhoz adja vissza, az oldal állapotát visszaállíthatók, ha megfelelően van-e konfigurálva a házirend-beállítás. Ha ez a szabályzatbeállítás engedélyezi, a felhasználó a böngészési előzményeket, a Kedvencek, XML-tárolóban, vagy közvetlenül egy weblap, lemezre menti az adatokat megőrizheti. Ha letiltja ezt a beállítást, a felhasználók nem megőrzése a böngészési előzményeket, a Kedvencek, XML-tárolóban, vagy közvetlenül egy weblap, lemezre menti az adatokat. Ha nem konfigurálja ezt a beállítást, a felhasználók nem megőrzése a böngészési előzményeket, a Kedvencek, XML-tárolóban, vagy közvetlenül egy weblap, lemezre menti az adatokat.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067081)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer intranetes zóna java engedélyek zárolva**  
  A házirend-beállítás lehetővé teszi a Java-alkalmazások engedélyeinek kezelése. Ha ez a szabályzatbeállítás engedélyezi, beállítások választhat a legördülő listából. Egyéni engedélyek beállításait szabályozhatja a külön-külön. Alacsony biztonsági lehetővé teszi, hogy az alkalmazások összes műveletek végrehajtásához. Közepes biztonsági plusz szolgáltatásokat, például az ideiglenes terület (egy megbízható és biztonságos tároló terület az ügyfélszámítógépen) és a felhasználó általi fájl i/o lehetővé teszi alkalmazások futtatását a védőfal (egy területen kívül, ami a program nem hívásokat a memóriában). Magas biztonsági lehetővé teszi, hogy az alkalmazások futtatását a tesztkörnyezetben. Tiltsa le a Java használatával bármilyen kisalkalmazások tiltsa le a futását. Ha letiltja ezt a beállítást, a Java-alkalmazások nem futtatható. Ha nem konfigurálja ezt a beállítást, a Java-alkalmazások le vannak tiltva.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067082)  
  
  **Alapértelmezett**: Tiltsa le a java  
  
- **Az Internet Explorer fokozott védett mód**  
  Fokozottan védett üzemmód rosszindulatú webhelyekre elleni további védelmet biztosít a 64 bites Windows 64 bites folyamatokat használatával. Vagy újabb rendszert futtató számítógépek Windows 8, a fokozottan védett üzemmóddal is korlátozza a helyeken, az Internet Explorer is olvasható, és a beállításjegyzék és a fájlrendszerhez. Ha ez a szabályzatbeállítás engedélyezi, fokozottan védett üzemmód be van kapcsolva. Minden zóna, amely a védett mód engedélyezve van a fokozottan védett üzemmód fogja használni. Felhasználók nem tudják fokozottan védett üzemmód letiltása. Ha letiltja ezt a beállítást, a fokozottan védett üzemmód ki van kapcsolva. Minden zóna, amely a védett mód engedélyezve van a védett mód a Windows Vista Internet Explorer 7-ben bevezetett verzióját fogja használni. Ha nem konfigurálja a házirendet, a felhasználók kapcsolja be vagy fokozottan védett üzemmód kikapcsolása az Internetbeállítások párbeszédpanel Speciális lapján.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067158)  
  
  **Alapértelmezett**: Enabled  
  
- **Az Internet Explorer SmartScreen-figyelmeztetések mellőzése**  
  Ez a szabályzatbeállítás határozza meg, hogy a felhasználó elkerülheti a SmartScreen szűrő figyelmeztetéseit. A SmartScreen szűrő figyelmezteti a felhasználót a végrehajtható fájlokat, az Internet Explorer-felhasználók gyakran nem letöltése az internetről. Ha ez a szabályzatbeállítás engedélyezi, a SmartScreen szűrő figyelmeztetéseit letiltása a felhasználó. Ha letiltja vagy nem konfigurálja ezt a beállítást, a felhasználó elkerülheti a SmartScreen szűrő figyelmeztetéseit.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067159)  
  
  **Alapértelmezett**: Letiltva  
  
- **Az Internet Explorer korlátozott zóna metaadat-frissítés**  
  Ez a házirend-beállítással kezelheti, hogy a felhasználók egy másik weblapon átirányíthatóak, ha a szerző, a weblap a metaadat-frissítési beállítást (címke) használ a böngésző átirányítja egy másik weblapon. Ha ez a szabályzatbeállítás engedélyezi, a felhasználó böngészője aktív metaadat-frissítési beállítást tartalmazó oldal betöltésekor átirányíthatóak egy másik weboldalra. Ha letiltja ezt a beállítást, a felhasználó böngészője aktív metaadat-frissítési beállítást tartalmazó oldal betöltésekor nem irányítható át egy másik weblapon. Ha nem konfigurálja ezt a beállítást, a felhasználó böngészője aktív metaadat-frissítési beállítást tartalmazó oldal betöltésekor nem irányítható át egy másik weblapon.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067154)  
  
  **Alapértelmezett**: Letiltva  
  
## <a name="local-policies-security-options"></a>A helyi házirendek-biztonsági beállítások
További információkért lásd: [házirend CSP - LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) a Windows dokumentációjában. 

- **Nevesített csövekhez és megosztások való névtelen hozzáférés korlátozása**  
  Ha engedélyezve van, ez a beállítás korlátozza a névtelen hozzáférés-megosztásokat és -csövek beállításai: (1) a named pipe-ok, hogy el névtelenül (2) megosztások névtelenül elérhető.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067212)  
  
  **Alapértelmezett**: Igen  
  
- **Munkamenet minimális biztonság az NTLM SSP alapú kiszolgálókról**  
  Ez a beállítás lehetővé teszi, hogy megkövetelje az 128 bites titkosítás és/vagy NTLMv2 munkamenet egy kiszolgálót. Ezeket az értékeket a LAN-kezelő hitelesítési szintje biztonsági beállítás értéke függenek. Az alábbi lehetőségek állnak rendelkezésére: NTLMv2 munkamenet megkövetelése: A kapcsolat nem jön létre, ha az üzenet sértetlenségének nem egyeztetett. 128 bites titkosítás használata. A kapcsolat nem jön létre, ha az erős titkosítás (128 bites) nem egyeztetett.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067246) 
  
  **Alapértelmezett**: Az NTLM V2 és 128 bites titkosítás megkövetelése  
  
- **Percek száma zárolási képernyőn a képernyőkímélő**  
  A Windows észleli a bejelentkezési munkamenetek tétlenségét, és ha a tétlenség ideje túllépi a tétlenségi korlátot, a rendszer futtatja a képernyőkímélőt és lezárja a munkamenetet.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067210)  
  
  **Alapértelmezett**: 15
  
- **Szükséges ügyfél-kommunikációhoz mindig digitális aláírására** a biztonsági beállítás határozza meg, hogy a tartományi tag által kezdeményezett összes biztonságos csatorna forgalmat kell kell aláírva vagy titkosítva. Ha a számítógép tartományhoz csatlakozik, egy számítógép-fiók jön létre. Ezt követően a rendszer indításakor használ a számítógép fiók jelszavát a hozzá tartozó tartomány tartományvezérlő biztonságos csatornát létrehozni. A biztonságos csatorna műveletek végrehajtásához, például a hitelesítést, LSA SID/keresése és további továbbítása NTLM használatos. Ez a beállítás határozza meg, ha a tartományi tag által kezdeményezett összes biztonságos csatorna forgalom megfelel a minimális biztonsági követelményeknek. Konkrétan meghatározza, hogy e indítja el a tartományi tag összes biztonságos csatorna forgalmat kell legyen aláírva vagy titkosítva. Ha ez a szabályzat engedélyezve van, majd a biztonságos csatorna nem létesíthető, ha aláírást vagy az összes biztonságos csatorna forgalom titkosítása egyeztetve van-e. Ha ez a házirend le van tiltva, akkor a titkosítási és aláírási biztonságos csatorna összes forgalom egyeztetve van-e a tartományvezérlővel, amely esetben aláírás és titkosítás szintjét attól függ, a tartományvezérlő verziója és a beállításokat a következő két házirendek: Tartományi tag: (Ha lehet) biztonságos csatornák adatainak digitális titkosítása tartományi tag: (Ha ez lehetséges) digitális aláírása.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067187) 
  
  **Alapértelmezett**: Igen
  
- **Hitelesítési szint**  
  Ez a beállítás meghatározza, hogy mely kérdés-válasz hitelesítési protokollt használják a hálózati bejelentkezést. Ez a választás hatással van a hitelesítési protokoll, amelyet az ügyfelek egyeztetett munkamenet biztonsági szintjét és a következőképpen fogadja el a kiszolgálók hitelesítési szintet szintje:  
  - *Az LM- és NTLM válaszok* -ügyfelek LM és az NTLM-hitelesítés használatára, és soha ne használja az NTLMv2 munkamenet; a tartományvezérlő, fogadja el az LM, NTLM és NTLMv2-alapú hitelesítés. 
  - *LM és az NTLM - NTLMv2 küldése, ha az egyeztetett* -ügyfelek LM és az NTLM-hitelesítés használatára, és NTLMv2 munkamenet használja, ha a kiszolgáló támogatja; a tartományvezérlők, fogadja el az LM, NTLM és NTLMv2-alapú hitelesítés. 
  - *Csak NTLM-válasz küldése* -ügyfelek csak NTLM-hitelesítést használ, és NTLMv2 munkamenet használja, ha a kiszolgáló támogatja; a tartományvezérlők, fogadja el az LM, NTLM és NTLMv2-alapú hitelesítést. 
  - *Csak az NTLMv2-válasz küldése* -ügyfelek csak NTLMv2-alapú hitelesítést használ, és NTLMv2 munkamenet használja, ha a kiszolgáló támogatja; a tartományvezérlők, fogadja el az LM, NTLM és NTLMv2-alapú hitelesítést. 
  - *Csak az NTLMv2-válasz küldése. Az LM utasítania* -ügyfelek csak NTLMv2-alapú hitelesítést használ, és NTLMv2 munkamenet használja, ha a kiszolgáló támogatja; a tartományvezérlő elutasítja az LM (Elfogadás csak NTLMv2- és NTLM-hitelesítés). 
  - *Csak az NTLMv2-válasz küldése. LM és az NTLM utasítania* -ügyfelek csak NTLMv2-alapú hitelesítést használ, és NTLMv2 munkamenet használja, ha a kiszolgáló támogatja; a tartományvezérlők elutasítják LM és az NTLM (Elfogadás csak NTLMv2-alapú hitelesítést).  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067189)   
    
  **Alapértelmezett**: Csak az NTLMv2-válasz küldése. Az LM- és NTLM utasítania
  
- **Megakadályozza a titkosítatlan jelszavak küldése külső SMB-kiszolgálóknak**  
  Ha ez a beállítás engedélyezve van, a Server Message Block (SMB) átirányító egyszerű szöveges jelszavakat küldhet nem Microsoft SMB-kiszolgálókra, amelyek nem támogatják a titkosítási jelszó a hitelesítés során. Titkosítatlan jelszavak küldése biztonsági kockázatot jelent.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067235)  
  
  **Alapértelmezett**: Igen
  
- **Digitális aláírás mindig kommunikációs server verziójának megkövetelése**  
  Ez a beállítás határozza meg, hogy az SMB-ügyfél megpróbálja-e egyeztetni az SMB-csomagaláírást. A server message block (SMB) protokoll a Microsoft-fájl- és nyomtatómegosztás alapját, és számos más hálózati műveletek, például a távoli Windows-felügyelet biztosít. SMB-csomagok továbbításához módosító man-in-the-middle támadások megelőzése érdekében az SMB protokoll támogatja az SMB-csomagokat digitális aláírását. A házirend-beállítás határozza meg, hogy az SMB-ügyfél összetevő megpróbál-e egyeztetni az SMB-csomagaláírás, amikor csatlakozik a SMB-kiszolgálón. Ha ez a beállítás engedélyezve van, a Microsoft hálózati ügyfél kéri a kiszolgálót az SMB-csomagaláírás munkamenet telepítés végrehajtásához. Ha a csomagaláírás engedélyezve van a kiszolgálón, a csomagaláírás egyeztetése megkezdődik. Ez a házirend le van tiltva, ha az SMB-ügyfél a soha nem egyezteti az SMB-csomagaláírást.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067319)  
  
  **Alapértelmezett**: Igen
  
- **Rendszergazda jogosultságszint-emelési kérés működése**  
  Ez a szabályzatbeállítás a jogosultságszint-emelési kérés rendszergazdák számára viselkedését szabályozza. Az alábbi lehetőségek állnak rendelkezésére: 
    - *Jogosultságszint-emelés rákérdezés nélkül* – lehetővé teszi a kiemelt jogosultságú fiókok jogosultságszint-emelési anélkül, hogy a hozzájárulási vagy hitelesítő adatokat igénylő művelet végrehajtásához. Megjegyezés: Használja ezt a beállítást csak a legnagyobb mértékben korlátozott környezetben. 
    - *A biztonsági asztal hitelesítő adatok kérése az* – Ha egy művelet megköveteli a jogok kiterjesztése, a felhasználó a biztonsági asztalon kéri, adja meg egy rendszergazdai engedéllyel rendelkező felhasználó nevét és jelszavát. Ha a felhasználó sikeresen Megadja, hogy érvényes hitelesítő adatokat, a művelet a felhasználó a elérhető legmagasabb szintű jogosultsággal rendelkező továbbra is. 
    - *A biztonsági asztalon jóváhagyás kérése* – Ha egy művelet megköveteli a jogok kiterjesztése, a felhasználó a biztonsági asztalon kéri, válassza ki, vagy engedélyezze. Ha a felhasználó engedélyt választja, a művelet a felhasználó a elérhető legmagasabb szintű jogosultsággal rendelkező továbbra is. 
    - *Hitelesítő adatok kérése az* – Ha egy művelethez megszerzését, kéri a felhasználót, hogy adjon meg egy rendszergazdai felhasználónevet és jelszót. Ha a felhasználó sikeresen Megadja, hogy érvényes hitelesítő adatokat, a megfelelő jogosultságokkal a művelet továbbra is. 
    - *Beleegyezés kérése* – Ha egy művelethez megszerzését, kéri a felhasználót, hogy válassza ki, vagy engedélyezze. Ha a felhasználó engedélyt választja, a művelet a felhasználó a elérhető legmagasabb szintű jogosultsággal rendelkező továbbra is.  
    - *Beleegyezés kérése nem Windows bináris fájlok azonnali* – Ha egy művelet egy nem Microsoft-alkalmazás szükséges jogok kiterjesztése, a felhasználó van a kiválasztásához, vagy engedélyezze a biztonsági asztalon kéri. Ha a felhasználó engedélyt választja, a művelet a felhasználó a elérhető legmagasabb szintű jogosultsággal rendelkező továbbra is. 
  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067215)   
  
  **Alapértelmezett**: Beleegyezés a biztonsági asztalon
  
- **Munkamenet minimális biztonság az NTLM SSP alapú ügyfelek**  
  Ez a beállítás lehetővé teszi, hogy az ügyfelek számára a 128 bites titkosítás és/vagy NTLMv2 munkamenet az egyeztetés. Ezeket az értékeket a LAN-kezelő hitelesítési szintje biztonsági beállítás értéke függenek. Az alábbi lehetőségek állnak rendelkezésére:
  - *Szükséges NTLMv2 munkamenet* – a kapcsolat nem jön létre, ha NTLMv2 protokoll egyeztetése nem. 
  - *128 bites titkosítás használata* – a kapcsolat nem jön létre, ha erős titkosítást (128 bites) nem egyeztetett.
  - *Az NTLMv2 és 128 bites titkosítás megkövetelése*.  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067324)  

  **Alapértelmezett**: Az NTLM V2 128-titkosítás megkövetelése
  
- **Viselkedés az intelligens kártya eltávolításakor**  
    Ez a beállítás határozza meg, mi történik, ha a bejelentkezett felhasználó intelligens kártyáját eltávolítják az intelligenskártya-olvasó. Az alábbi lehetőségek állnak rendelkezésére:
     - *Nincs művelet*. 
     - *Munkaállomás zárolása* – a munkaállomás zárolva van, az intelligens kártya eltávolítása, így a felhasználók a területen hagyja, az intelligens kártya velük, illetve egy védett munkamenet fenntartásához.
     - *Kijelentkezés kényszerítése* – a felhasználó automatikusan ki van jelentkezve az intelligens kártya eltávolításakor.
     - *Távoli asztali munkamenet leválasztása* – az intelligens kártya eltávolítása nélkül a felhasználó kijelentkeztetése leválasztja a munkamenetet. Ez lehetővé teszi a felhasználó az intelligens kártya Beszúrás, és folytatni a munkamenetet később, vagy egy másik intelligens kártyát olvasó felszerelt számítógép, anélkül, hogy jelentkezzen be újra kellene. Helyi munkamenet esetén ez a szabályzat pontosan úgy működik, mint a Munkaállomás zárolása.
  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067331) 
    
  **Alapértelmezett**: Munkaállomás zárolása
  
- **SAM-fiókok és -megosztások névtelen felsorolása letiltása**  
  A biztonsági beállítás határozza meg, hogy a fiókok és -megosztások névtelen felsorolása a SAM engedélyezett-e. Windows lehetővé teszi a névtelen felhasználók számára bizonyos műveletek végrehajtását, például a tartományi fiókok és a hálózati megosztások nevének felsorolását. Ez akkor hasznos, például, ha a rendszergazda szeretne hozzáférést biztosítani a felhasználók számára, melyek fenntartják a kölcsönös megbízhatósági kapcsolat nem megbízható tartományban. Ha nem szeretné, hogy névtelen felsorolása a SAM-fiókok és a megosztások, majd állítsa be ezt a házirendet *Igen*.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067191)  
  
  **Alapértelmezett**: Igen
  
- **Távoli bejelentkezés blokkolása üres jelszót**  
  Ez a beállítás határozza meg, hogy használható-e a helyi fiókok, amelyek nem jelszóval védett, jelentkezzen be a fizikai számítógép-konzolt eltérő helyekről. Ha engedélyezve van, helyi felhasználói fiókok, jelszóval védett nem kell használnia a számítógép jelentkezzen be. 

  *Figyelmeztetés*: Számítógépek, amelyek fizikailag biztonságos helyen nem kell mindig erős jelszót szabályzatok érvényesítését a minden helyi felhasználói fiókokhoz. Ellenkező esetben a számítógéphez fizikai hozzáféréssel rendelkező felhasználók jelentkezhetnek be a felhasználói fiókkal, amely nem rendelkezik a jelszó. Ez különösen fontos a hordozható számítógépekhez. 

  Ha a biztonsági házirendet alkalmaz a Mindenki csoportnak, nem jelentkezhetnek be a távoli asztali szolgáltatások használatával. Ez a beállítás nincs hatással a bejelentkezések, amelyek tartományi fiókokat használ. Ezzel a beállítással megkerülésére távoli interaktív bejelentkezést használó alkalmazások számára lehetőség.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067219)  
  
  **Alapértelmezett**: Igen
  
- **Jogosultságszint-emelési kérés működése általános jogú felhasználó**  
  Ez a szabályzatbeállítás a jogosultságszint-emelési kérés működése általános jogú felhasználók esetében viselkedését szabályozza. 
  - *Jogosultságszint-emelési kérések automatikus megtagadása* – Ha egy művelet megköveteli a jogok kiterjesztése, a konfigurálható hozzáférés megtagadva hiba jelenik meg. Vállalati futtató asztali számítógépek, az általános jogú felhasználó dönthet ezzel a beállítással csökkentheti a segélyszolgálatra beérkező hívások. 
  - *A biztonsági asztal hitelesítő adatok kérése az* – Ha egy művelet megköveteli a jogok kiterjesztése, a felhasználó a biztonsági asztalon kéri, adja meg egy másik felhasználónevet és jelszót. Ha a felhasználó sikeresen Megadja, hogy érvényes hitelesítő adatokat, a megfelelő jogosultságokkal a művelet továbbra is. 
  - *Hitelesítő adatok kérése az* – Ha egy művelethez megszerzését, kéri a felhasználót, hogy adjon meg egy rendszergazdai felhasználónevet és jelszót. Ha a felhasználó sikeresen Megadja, hogy érvényes hitelesítő adatokat, a megfelelő jogosultságokkal a művelet továbbra is.  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067183)  
  
  **Alapértelmezett**: Jogosultságszint-emelési kérések automatikus megtagadása
  
- **A rendszergazdák rendszergazdai engedélyezéses mód megkövetelése**  
  A házirend-beállítás a felhasználói fiókok felügyelete (UAC) szabályzatok minden beállítását, a számítógép viselkedését szabályozza. Ha módosítja ezt a beállítást, újra kell indítani a számítógépet. Az alábbi lehetőségek állnak rendelkezésére:   
  - *Nincs konfigurálva* -rendszergazdai engedélyezéses mód és az összes kapcsolódó felhasználói fiókok Felügyeletének házirend-beállítások le vannak tiltva. Megjegyezés: Ha a házirend-beállítás le van tiltva, a Security Center értesíti, hogy a teljes biztonsági az operációs rendszer e-mailjeiket. 
  - *Igen* -rendszergazdai engedélyezéses mód engedélyezve van. Ez a szabályzat engedélyezve kell lennie, és a kapcsolódó felhasználói fiókok Felügyeletének házirend beállításainak megfelelően kell állítani, hogy a beépített Rendszergazda fiók és minden egyéb felhasználó rendszergazdai engedélyezéses módban futtatásához a Rendszergazdák csoport tagjai.  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067184)  
  
  **Alapértelmezett**: Igen
  
- **Megakadályozza a SAM-fiókok névtelen felsorolása**  
  Ez a beállítás határozza meg, milyen további engedélyekkel a névtelen kapcsolódást a számítógéphez. Windows lehetővé teszi a névtelen felhasználók számára bizonyos műveletek végrehajtását, például a tartományi fiókok és a hálózati megosztások nevének felsorolását. Ez akkor hasznos, például, ha a rendszergazda szeretne hozzáférést biztosítani a felhasználók számára, melyek fenntartják a kölcsönös megbízhatósági kapcsolat nem megbízható tartományban. Ez a beállítás lehetővé teszi, hogy a névtelen kapcsolatok a következőképpen elhelyezését további korlátozások: 
  - *Igen* -nem SAM-fiókok felsorolása engedélyezett. Ez a beállítás lecseréli mindenki hitelesített felhasználók a biztonsági engedélyek az erőforrások.
  - *Nincs konfigurálva* – nincs további korlátozásokat. Alapértelmezett engedélyek támaszkodnak.  
  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067318)  

  **Alapértelmezett**: Igen
  
- **Lehetővé teszi a biztonsági fiókkezelő távoli hívások**  
  Ez a házirend-beállítással korlátozhatja a távoli rpc-kapcsolatok Sándornak. Ha nincs bejelölve, az alapértelmezett biztonsági leíró szolgál.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067209)  
  
  **Alapértelmezett**: *O:BAG:BAD:(A;; RC;; BA)*

- **Rendszergazdai engedélyezéses mód használata**  
  A házirend-beállítás szabályozza a rendszergazdai engedélyezéses mód a beépített rendszergazdai fiók viselkedését. Az alábbi lehetőségek állnak rendelkezésére: 
  - *Igen* – a beépített Rendszergazda fiók rendszergazdai engedélyezéses módban használja. Alapértelmezés szerint minden művelet, amely megköveteli a jogok kiterjesztése fogja kérni a felhasználót, hogy hagyja jóvá a műveletet. 
  - *Nincs konfigurálva* – a beépített rendszergazdai fiók teljes körű rendszergazdai jogosultságokkal rendelkező összes alkalmazások futnak. 

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067186)  

  **Alapértelmezett**: Igen
  
- **Felhasználói felület alkalmazásokat biztonságos hely engedélyezése**  
  Ez a házirend-beállítással megadható, hogy a felhasználói felület kisegítő (UIAccess vagy UIA) programok automatikusan letilthatják a jogosultságszint-emelési általános jogú felhasználók által használt biztonsági asztalt. 
  - *Igen* -UIA-programoknak, beleértve a Windows Távsegítség, automatikusan letilthatják a jogosultságszint-emelési kérések asztalt. Ha letiltja a nem a "felhasználói fiókok felügyelete: Jogosultságszint-emelési kérés során átváltás biztonsági asztalra"házirend-beállítás, a kérések a biztonsági asztal helyett az interaktív felhasználó asztalán jelennek meg. 
  - *Nincs konfigurálva*: – a biztonsági asztalt csak az interaktív asztal felhasználója vagy letiltásával tiltható a "felhasználói fiókok felügyelete: Jogosultságszint-emelési kérés során átváltás biztonsági asztalra"házirend-beállítást.  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067185)  

  **Alapértelmezett**: Igen

- **Észlelheti és figyelmeztetés a jogosultságszint-emeléshez**  
  Ezzel a szabályzatbeállítással az alkalmazások telepítésének észlelése a számítógép viselkedését szabályozza. Az alábbi lehetőségek állnak rendelkezésére: 
  - *Engedélyezett* – az alkalmazás telepítési csomagot észlelt, amely megköveteli, hogy megszerzését, kéri a felhasználót, hogy adjon meg egy rendszergazdai felhasználónevet és jelszót. Ha a felhasználó sikeresen Megadja, hogy érvényes hitelesítő adatokat, a megfelelő jogosultságokkal a művelet továbbra is. 
  - *Letiltott* -alkalmazáscsomagok telepítési nem észlelt, és kéri a jogosultságszint-emeléshez. Olyan vállalatok, amelyek általános jogú felhasználók futnak, és használja a telepítési technológiák, például a csoportházirend szoftvertelepítési meghatalmazott, vagy a Systems Management Server (SMS) tiltsa le a házirend-beállítás. Ebben az esetben a telepítő észlelése nem szükséges.  
  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067208)  

  **Alapértelmezett**: Igen
  
- **A következő jelszómódosításkor tárolja a LAN-kezelő üzenetkivonatát megakadályozása**  
  Ez a beállítás határozza meg, ha jelenleg a következő jelszómódosításkor az új jelszó LAN Manager-(LM-) ujjlenyomat értékét tárolja. Az LM-kivonat viszonylag gyenge, és a titkosítási szempontból erősebb Windows NT-kivonat szemben a hibalehetőség. Mivel az LM-kivonat a biztonsági adatbázisban a helyi számítógépen tárolt jelszavak is sérülhet, ha a biztonsági adatbázis megtámadott.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067213)  
  
  **Alapértelmezett**: Igen

- **Fájl- és beállításjegyzék-írási hibák száma a felhasználó tartózkodási helye virtualizálása**  
  Ez a házirend-beállítással megadható, hogy az alkalmazás-írási hibák a rendszer átirányítja megadott beállításjegyzékbeli és fájlrendszerbeli helyekre. Ezzel a szabályzatbeállítással csökkenti az alkalmazásokat, amelyek a Futtatás rendszergazdaként, és a futásidejű alkalmazások adatainak írása *% ProgramFiles %* , *% Windir %* , *%Windir%\system32*, vagy *HKLM\Software*.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067321)  
  
  **Alapértelmezett**: Igen

## <a name="ms-security-guide"></a>MS biztonsági útmutató  
További információkért lásd: [házirend CSP - MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) a Windows dokumentációjában.  

- **A felhasználói fiókok Felügyeletének korlátozásokat lehessen alkalmazni a hálózati bejelentkezés helyi fiókhoz**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067188)  

  **Alapértelmezett**: Enabled
  
- **SMB v1 ügyfél illesztőprogram kezdő konfigurálása**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067214) 
 
  **Alapértelmezett**: Letiltott illesztőprogram
  
- **SMB-kiszolgáló v1**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067190)  

  **Alapértelmezett**: Letiltva
  
- **Kivonatoló hitelesítés**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067193) 
 
  **Alapértelmezett**: Letiltva
  
- **Strukturált kivételkezelés védelmi felülírása**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067217)  

  **Alapértelmezett**: Enabled
  
## <a name="mss-legacy"></a>MSS örökölt  
További információkért lásd: [házirend CSP - MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) a Windows dokumentációjában.  

- **Hálózati IP-forrás védelmi szint Útválasztás**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067220)  
  
  **Alapértelmezett**: Legmagasabb szintű védelme  
  
- **Hálózati figyelmen kívül hagyja a NetBIOS név kiadás kivételével érkező kérelmeket a WINS-kiszolgálók**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067218)  
 
  **Alapértelmezett**: Enabled
  
- **Hálózati IPv6 forrás útválasztási védelmi szint**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067216)  

  **Alapértelmezett**: Legmagasabb szintű védelme

- **Hálózati ICMP átirányítások generált OSPF felülbírálása**  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067326)  

  **Alapértelmezett**: Letiltva
  
## <a name="power"></a>Energiagazdálkodási  
További információkért lásd: [házirend CSP - Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) a Windows dokumentációjában.  

- **Az ébresztési áramforráshoz jelszó kérése**  
  A házirend-beállítással megadható, ha a felhasználó kéri a jelszót, amikor a rendszer visszatér az alvó állapotból. Engedélyezi, vagy nem konfigurálja ezt a beállítást, ha a felhasználó értesítése a jelszót a rendszer visszatér az alvó állapotból. Ha letiltja ezt a beállítást, a felhasználónak nem kell megadnia egy jelszót, amikor a rendszer visszatér az alvó állapotból.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067221)  
  
  **Alapértelmezett**: Enabled
  
- **Az akkumulátor alvó állapotba helyezésekor készenléti állapotok**  
  Ezt a beállítást, ha a Windows készenléti állapotok használata a számítógép alvó állapotba helyezésekor kezeli. Engedélyezi, vagy nem konfigurálja ezt a beállítást, ha a Windows készenléti állapotok használ a számítógép alvó állapotba helyezni. Ha letiltja ezt a beállítást, készenléti állapotok (S1-S3) nem engedélyezett.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067195)  
  
  **Alapértelmezett**: Letiltva
  
- **Készenléti állapotok áramforráshoz alvó állapotba helyezésekor**  
  Ezt a beállítást, ha a Windows készenléti állapotok használata a számítógép alvó állapotba helyezésekor kezeli. Engedélyezi, vagy nem konfigurálja ezt a beállítást, ha a Windows készenléti állapotok használ a számítógép alvó állapotba helyezni. Ha letiltja ezt a beállítást, készenléti állapotok (S1-S3) nem engedélyezett.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067196)  
  
  **Alapértelmezett**: Letiltva
  
- **Az akkumulátor jelszót igényel**  
  A házirend-beállítással megadható, ha a felhasználó kéri a jelszót, amikor a rendszer visszatér az alvó állapotból. Engedélyezi, vagy nem konfigurálja ezt a beállítást, ha a felhasználó értesítése a jelszót a rendszer visszatér az alvó állapotból. Ha letiltja ezt a beállítást, a felhasználónak nem kell megadnia egy jelszót, amikor a rendszer visszatér az alvó állapotból.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067322)  
  
  **Alapértelmezett**: Enabled

## <a name="remote-assistance"></a>Távsegítség
- **A kért Távsegítség**  
  A házirend-beállítás lehetővé teszi, hogy kapcsolja be, vagy kapcsolja ki a Távsegítség Solicited (kérése) ezen a számítógépen. 
  - *Ha ez a szabályzatbeállítás engedélyezi*, ezen a számítógépen a felhasználók e-mailt vagy fájlt átviteli segítségével kérjen segítséget. Ezenkívül felhasználók csevegőprogramokon segítségével engedélyezze a kapcsolatokat ezen a számítógépen, és konfigurálhatja a további távsegítségre vonatkozó beállítások. 
  - *Ha letiltja ezt a beállítást*, a számítógép felhasználói e-mailek vagy fájlok átvitele nem használható kérjen segítséget. Ezenkívül az felhasználók nem használhatják az csevegőprogramokon számítógéphez való engedélyezéséhez. 
  - *Ha nem konfigurálja a házirend-beállítás*, felhasználók be- és kikapcsolása Solicited (kérése) Távsegítség magukat a Vezérlőpult Rendszer tulajdonságai. Felhasználók is konfigurálhatja a távsegítségre vonatkozó beállítások. 

  Ha ez a szabályzatbeállítás engedélyezi, akkor két módon lehet távsegítséget nyújtani a segítők: "A számítógép csak megtekinteni segítők" vagy "Segítők vezérelhetik a számítógépet." A "jegy maximális ideje" házirend-beállítás korlát beállítása idő, amely e-mailt vagy fájlt átvitellel létrehozott távsegítségkérést nyitva maradhat. A "kiválasztás a metódus az e-mailben meghívást" beállítás használatával Távsegítség meghívók küldése e-mailek szabványos határozza meg. Az e-mail program függően standard Mailto (az internetes kapcsolaton keresztül csatlakozik a meghívó a címzett) vagy a SMAPI-t (egyszerű MAPI) standard (a meghívót csatolva van az e-mail-üzenetet) is használhatja. A házirend-beállítás nem érhető a Windows Vista mivel a SMAPI-t az egyetlen módszer támogatott. Ha ez a szabályzatbeállítás engedélyezi, hogy a Távsegítség-kommunikáció megfelelő tűzfalkivételeket is engedélyeznie kell.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067198)

  **Alapértelmezett**: Tiltsa le a távoli segítségnyújtás

  Ha a beállítása *engedélyezése Távsegítség*, adja meg a következő további beállításokat:  
  - **A kért Távsegítség engedély**  
    **Alapértelmezett**: Nézet  

  - **Jegy maximális idő érték**  
    **Alapértelmezett**: *Nincs konfigurálva*  

  - **Jegy maximális időtartam**  
    **Alapértelmezett**: perc    

  - **E-mailben meghívást metódus**  
    **Alapértelmezett**: Simple MAPI

  
## <a name="remote-desktop-services"></a>Távoli asztali szolgáltatások  
További információkért lásd: [házirend CSP - RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) a Windows dokumentációjában.  

- **Jelszó mentésének letiltása**  
  Azt szabályozza, hogy jelszavakat menthetők-e ezen a számítógépen a távoli asztali kapcsolat. Ha engedélyezi ezt a beállítást a jelszó mentése jelölőnégyzetet a távoli asztali kapcsolat le van tiltva, és a felhasználók nem tudják menteni a jelszavakat. Ha egy felhasználó megnyitja a távoli asztali kapcsolattal egy RDP-fájlt, és menti a beállításokat, minden jelszót, amely korábban már létezett az RDP-fájlt az törlődnek. Ha letiltja ezt a beállítást, vagy hagyja üresen a nincs konfigurálva, a felhasználó menthetik jelszavaikat a távoli asztali kapcsolattal.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067301)  
  
   **Alapértelmezett**: Enabled
  
- **Biztonságos RPC-kommunikációhoz**  
  Itt adhatja meg, hogy egy távoli asztali munkamenetgazda-kiszolgáló összes ügyfél a biztonságos RPC-kommunikáció vagy lehetővé teszi a biztonságos kommunikációt. Ez a beállítás segítségével RPC-kommunikáció az ügyfelek biztonságának fokozását azáltal, hogy csak hitelesített és titkosított kérelmeket. Ha a beállítás engedélyezve van, a távoli asztali szolgáltatások, amelyek támogatják a biztonságos kérelmek RPC-ügyfelektől érkező kéréseket fogad, és nem biztonságos kommunikáció engedélyezése az ügyfelek nem megbízható. Ha a beállítás le van tiltva, a távoli asztali szolgáltatások mindig kérelmek biztonsági minden RPC-forgalom. Azonban nem biztonságos kommunikáció engedélyezett RPC-ügyfelek, amelyek nem válaszol a kérelemre. Ha a beállítás nincs konfigurálva, nem biztonságos kommunikáció engedélyezve van. Megjegyezés: Az RPC felület felügyelete és konfigurálása a távoli asztali szolgáltatások szolgál.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067248)  
  
  **Alapértelmezett**: Enabled
  
- **Meghajtó blokkátirányítás**  
  A házirend-beállítás megadja, hogy a leképezés egy távoli asztali szolgáltatások munkamenet (meghajtón átirányítást) ügyfélmeghajtók elkerülése érdekében. Alapértelmezés szerint egy távoli asztali munkamenetgazda-kiszolgálóhoz kapcsolódáskor automatikusan ügyfélmeghajtók képezi le. Csatlakoztatott meghajtók munkamenet ebben a mappafában levő a fájlkezelő vagy a számítógép a következő formátumban jelenik meg  *\<meghajtóbetűjel >* a  *\<számítógép_neve >* . A házirend-beállítás használatával bírálja felül ezt a viselkedést. Ha ez a szabályzatbeállítás engedélyezi, átirányítása a távoli asztali szolgáltatások munkamenetei nem engedélyezett, és a vágólapra másolás-átirányítási fájlt a Windows Server 2003, Windows 8 és Windows XP rendszert futtató számítógépeken nem engedélyezett. Ha letiltja ezt a beállítást, az ügyfél meghajtón átirányítást mindig engedélyezve van. Vágólapra másolás-átirányítási fájlt is, ha átirányítása a vágólap engedélyezett mindig engedélyezett. Ha nem konfigurálja ezt a beállítást, ügyfél meghajtón átirányítást és vágólapra másolás-átirányítási fájlt nem meg a csoportházirend szintjén.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067197)  
  
  **Alapértelmezett**: Enabled
  
- **Jelszó kérése**  
  A házirend-beállítás megadja-e a távoli asztali szolgáltatások mindig kérni fogja az ügyfél egy a jelszót. Ezzel a beállítással használhatja a kényszerítéséhez a felhasználók a távoli asztali szolgáltatásokhoz, a bejelentkezés jelszó megadására, akkor is, ha már megadta a jelszót a távoli asztali kapcsolat-ügyfél. Alapértelmezés szerint a távoli asztali szolgáltatások lehetővé teszi a felhasználóknak a jelszó beírásával a távoli asztali kapcsolat-ügyfél automatikus bejelentkezésre. Ha ez a szabályzatbeállítás engedélyezi, felhasználók nem lehet automatikusan jelentkezzen be a távoli asztali szolgáltatások a távoli asztali kapcsolat ügyfél jelszavuk megadásával. Ezek kéri, jelentkezzen be a jelszót. Ha letiltja ezt a beállítást, felhasználók is mindig jelentkezzen be a távoli asztali szolgáltatások automatikusan a távoli asztali kapcsolat ügyfél jelszavuk megadásával. Ha nem konfigurálja ezt a beállítást, az automatikus bejelentkezés nincs megadva, a csoportházirend szintjén.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067328)  
  
  **Alapértelmezett**: Enabled
  
- **A távoli asztali szolgáltatások ügyfél kapcsolat titkosítási szint**  
  Megadja, hogy az ügyfélszámítógépek és a távoli asztali munkamenetgazda-kiszolgálók közötti kommunikáció biztonságossá tételéhez a távoli asztal protokoll (RDP) kapcsolatokat során egy adott titkosítási szint használata szükséges. Ez a szabályzat csak akkor érvényes, ha natív RDP-titkosítást használ. Natív RDP-titkosítást (nem SSL-titkosítást) azonban nem ajánlott. Ez a szabályzat nem vonatkozik a SSL-titkosítást. Ha ez a szabályzatbeállítás engedélyezi, távoli kapcsolatok során az ügyfelek és távoli asztali munkamenetgazda-kiszolgálók közötti minden kommunikáció ebben a beállításban megadott titkosítási módszert kell használnia. Alapértelmezés szerint a magas titkosítási szint van beállítva. Az alábbi titkosítási módszerek érhetők el:  
  - *Magas* – a magas beállítást titkosítja az adatokat, az ügyfél és a kiszolgáló és a kiszolgáló az ügyfélnek küldött erős 128 bites titkosítás segítségével. A titkosítási szint csak 128 bites ügyfeleket (például futtató ügyfelek távoli asztali kapcsolat) környezetekben használható. Ügyfelek, amelyek nem támogatják a titkosítási szint nem tud kapcsolódni a távoli asztali munkamenetgazda-kiszolgálók.  
  - *Az ügyfél kompatibilis* – az ügyfél-kompatibilis beállítás titkosítja az ügyfél és a kiszolgáló, az ügyfél által támogatott legerősebb között küldött adatokat. A titkosítási szint környezetekben, beleértve az ügyfelek, amelyek nem támogatják a 128 bites titkosítás használata.  
  - *Alacsony* – az alacsony beállítással csak az ügyfél által küldött a kiszolgálónak 56-bites titkosítás segítségével adatokat titkosítja.  
  
  Ha letiltja vagy nem konfigurálja ezt a beállítást, a távoli asztali munkamenetgazda-kiszolgálók távoli kapcsolatokhoz használt titkosítási szint csoportházirend nincs kényszerítve. A FIPS fontos a rendszer-kriptográfia keresztül konfigurálhatók. A FIPS előírásainak megfelelő algoritmusok használata titkosításhoz, kivonatoláshoz és aláíráshoz (a Számítógép konfigurációja\A Windows beállításai\Biztonsági beállítások\Helyi házirend\Biztonsági beállítások.) a csoportházirend beállításai A FIPS előírásainak megfelelő beállítás titkosítja, és mindig visszafejti az adatokat az ügyfél és a kiszolgáló és a kiszolgáló az ügyfélnek a Federal Information Processing Standard (FIPS) 140 titkosítási algoritmussal küldött Microsoft titkosítási modulok használatával. Ügyfelek és a távoli asztali munkamenetgazda-kiszolgálók közötti kommunikációhoz szükséges a legmagasabb szintű titkosítást használni a titkosítási szint.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067222)  
  
  **Alapértelmezett**: Magas
  
## <a name="remote-management"></a>Távfelügyelet  
További információkért lásd: [házirend CSP - RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) a Windows dokumentációjában.  

- **A Blokkblob tárolás futtató tartozó hitelesítő adatok**  
  Ügyfél-hitelesítés alapszintű.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067300)  
  
  **Alapértelmezett**: Enabled
  
- **Alapszintű hitelesítés**  
  A házirend-beállítás lehetővé teszi, hogy kezelheti-e a Windows Rendszerfelügyeleti (webszolgáltatások WinRM) szolgáltatás fogad el az alapszintű hitelesítés, a távoli ügyfélhez. Ha ez a szabályzatbeállítás engedélyezi, a WinRM szolgáltatás alapszintű hitelesítés, a távoli ügyfélhez fogad el. Ha letiltja vagy nem konfigurálja ezt a beállítást, a WinRM szolgáltatás nem fogadja el a távoli ügyfélhez egyszerű hitelesítést.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067223)  
  
  **Alapértelmezett**: Letiltva
  
- **Ügyfél-kivonatoló hitelesítés letiltása**  
  Ez a házirend-beállítással kezelheti, hogy a Windows Rendszerfelügyeleti (webszolgáltatások WinRM) ügyfél használja a kivonatoló hitelesítés. Ha ez a szabályzatbeállítás engedélyezi, a WinRM-ügyfél a kivonatoló hitelesítés nem használ. Ha letiltja vagy nem konfigurálja ezt a beállítást, a WinRM-ügyfél használja a kivonatoló hitelesítés.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067302)  
  
  **Alapértelmezett**: Enabled
  
- **Nem titkosított forgalmat**  
  A házirend-beállítás lehetővé teszi, hogy szabályozhatja, hogy a Windows Rendszerfelügyeleti (webszolgáltatások WinRM) szolgáltatás elküldi a hálózaton keresztül nem titkosított üzeneteket fogad. Ha ez a szabályzatbeállítás engedélyezi, a WinRM-ügyfél küld, és nem titkosított üzeneteket fogad a hálózaton keresztül. Ha letiltja vagy nem konfigurálja ezt a beállítást, a WinRM-ügyfél üzeneteket küldő vagy fogadó csak titkosított a hálózaton keresztül.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067226)  
  
  **Alapértelmezett**: Letiltva
  
- **Titkosítatlan ügyfél forgalmát**  
  Ez a házirend-beállítással kezelheti, hogy a Windows Rendszerfelügyeleti (webszolgáltatások WinRM) ügyfél küld, és nem titkosított üzeneteket fogad a hálózaton keresztül. Ha ez a szabályzatbeállítás engedélyezi, a WinRM-ügyfél küld, és nem titkosított üzeneteket fogad a hálózaton keresztül. Ha letiltja vagy nem konfigurálja ezt a beállítást, a WinRM-ügyfél üzeneteket küldő vagy fogadó csak titkosított a hálózaton keresztül.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067304)  
  
  **Alapértelmezett**: Letiltva
  
- **Ügyfél alapszintű hitelesítés**  
  A házirend-beállítás lehetővé teszi, hogy kezelheti-e a Windows Rendszerfelügyeleti (webszolgáltatások WinRM) ügyfél egyszerű hitelesítést használ. Ha ez a szabályzatbeállítás engedélyezi, a WinRM-ügyfél alapszintű hitelesítést használ. Ha a Rendszerfelügyeleti webszolgáltatások HTTP protokollon használatára van konfigurálva, a felhasználónév és jelszó érkeznek a hálózaton egyszerű szövegként. Ha letiltja vagy nem konfigurálja ezt a beállítást, a WinRM-ügyfél az alapszintű hitelesítés nem használ.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067252)  
  
  **Alapértelmezett**: Letiltva
  
## <a name="remote-procedure-call"></a>A távoli eljáráshívás  
További információkért lásd: [házirend CSP - RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) a Windows dokumentációjában.  

- **Nem hitelesített RPC-ügyfél beállításai**  
  A házirend-beállítás határozza meg, hogyan kezeli az RPC-kiszolgáló modul a nem hitelesített RPC-ügyfelekhez RPC-kiszolgálók. A házirend-beállítás hatással van minden RPC-alkalmazást. Tartományi környezetben használja a házirend-beállítás körültekintően, mert hatással lehet számos különféle funkcióit, többek között a Csoportházirend általi feldolgozás magát. Visszaállítás a házirend-beállítás módosítása az összes érintett manuális beavatkozásra lehet szükség. A házirend-beállítás egy olyan tartományvezérlőre, amely soha nem kell alkalmazni. Ha letiltja ezt a beállítást, az RPC-kiszolgáló modul a Windows ügyfél és az értéke "None", amely támogatja a házirend-beállítás a Windows Server-verziók a "Hitelesített" értékét használja. Ha nem konfigurálja ezt a beállítást, azt letiltva marad. A kiszolgáló távoli Eljáráshívás futásideje viselkedik, mintha a következő értékkel: "Hitelesített" Windows ügyfél és az értéke "None" használt kiszolgáló SKU-k, amelyek támogatják a házirend-beállítás engedélyezve lett. Ha ez a szabályzatbeállítás engedélyezi, a távoli Eljáráshívás kiszolgálói futásideje korlátozása a nem hitelesített RPC-ügyfelekhez gépen futó RPC-kiszolgálók irányítja. Egy ügyfél egy hitelesített ügyfél számít, ha egy nevesített csövet a kiszolgálóval való kommunikációra használ, vagy ha eljáráshívást használ. Lehet, hogy kifejezetten kérte nem hitelesített ügyfelek számára érhető el RPC-interfészek kiválasztott házirend-beállítás értékétől függően ez a korlátozás alól.  
  - *Nincs* lehetővé teszi, hogy az összes RPC-ügyfelek, amelyeken a házirend-beállítást alkalmazza, a gépen futó RPC-kiszolgálókhoz való kapcsolódáshoz. 
  - *Hitelesített* lehetővé teszi, hogy csak hitelesített RPC-ügyfelek száma (a fenti definíció) RPC-kiszolgálóhoz csatlakozzon, amelyen a házirend-beállítást alkalmazza, a gépen futó. Kivételek megadott felületek, amelyek a kért őket. 
  - *Kivételek nélkül hitelesített* lehetővé teszi, hogy csak hitelesített RPC-ügyfelek száma (a fenti definíció) RPC-kiszolgálóhoz csatlakozzon, amelyen a házirend-beállítást alkalmazza, a gépen futó. Nincsenek kivételek engedélyezettek. Megjegyezés: A házirend-beállítás alkalmazza a rendszer újraindításáig.  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067225)  

  **Alapértelmezett**: Hitelesített

## <a name="search"></a>Keresés 
További információkért lásd: [házirend CSP - keresés](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) a Windows dokumentációjában.  

- **Titkosított elemek-indexelés letiltása**  
  Engedélyezi vagy tiltja az elemek indexelését. Ez a kapcsoló aktiválva van a Windows Search indexelő, amely meghatározza, hogy az indexeli a Windows Information Protection (WIP) által védett fájlok például olyan titkosított elemeket. A szabályzat engedélyezésekor a WIP által védett elemek indexelve lesznek, a velük kapcsolatos metaadatok pedig titkosítatlan helyen lesznek tárolva. A metaadatok között szerepel egyebek között a fájl elérési útja és módosításának dátuma. Ha a házirend le van tiltva, a WIP által védett elemek nem indexelt, és nem jelennek meg a Cortana vagy a fájlkezelő eredményez. A Fényképek és a Groove alkalmazás teljesítménye csökkenhet, ha nagy mennyiségű WIP-védelemmel ellátott médiafájl található az eszközön.  
  [További információ]( https://go.microsoft.com/fwlink/?linkid=2067303)  
  
  **Alapértelmezett**: Igen
  
## <a name="smart-screen"></a>SmartScreen  
További információkért lásd: [házirend CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) a Windows dokumentációjában.  

- **Nem ellenőrzött fájlok futtatásának letiltása**  
  A felhasználó nem futtathat ellenőrizetlen fájlokat. 
  - *Nincs konfigurálva* -alkalmazottak figyelmen kívül hagyja a SmartScreen-figyelmeztetéseket, és a kártevő fájlokat futtathat. 
  - *Igen* – alkalmazottak nem SmartScreen vonatkozó figyelmeztetések mellőzése és a kártevő fájlokat futtathat.

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067228)  
  
  **Alapértelmezett**: Igen

- **SmartScreen-üzenetek szükséges alkalmazások és fájlok**  
  Lehetővé teszi a rendszergazdáknak, hogy a Windows SmartScreen konfigurálása.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067168)  

  **Alapértelmezett**: Igen
  
## <a name="system"></a>Rendszer  
További információkért lásd: [házirend CSP - rendszer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) a Windows dokumentációjában.  

- **A rendszer rendszerindító kezdő illesztőprogram inicializációja**  
  A házirend-beállítás lehetővé teszi, hogy adja meg, milyen rendszerindítás illesztőprogramok inicializálása alapján határozza meg a rendszerindítás korai indítsa el a kártevőirtó vezető besorolást. A rendszerindítás korai indítsa el a kártevőirtó illesztőprogram adhat vissza minden egyes rendszerindítás illesztőprogram a következő besorolásokkal: 
  - *Jó* – az illesztőprogram aláírással rendelkezik, és nem módosították illetéktelenül.  
  - *Hibás* – az illesztőprogramot, kártevő szoftverek lett azonosítva. Azt javasoljuk, hogy ahhoz, hogy nem ismert hibás illesztőprogramok inicializálása. 
  - *Hibás, de a rendszerindításhoz szükséges* – az illesztőprogram kártevő néven azonosított, de a számítógép nem tudja sikeresen rendszerindítást anélkül, hogy az illesztőprogram betöltése. 
  - *Ismeretlen* – Ez az illesztőprogram még nem lett intézményében a kártevő-észlelési alkalmazását, és a rendszerindítás korai indítsa el a kártevőirtó illesztőprogram által még nem sorolták.  

  Ha ez a szabályzatbeállítás engedélyezi, választhat, mely rendszerindítás illesztőprogramok inicializálása a számítógép következő indításakor. Ha letiltja vagy nem konfigurálja ezt a házirendet beállítást, a rendszerindító kezdő illesztőprogramokkal minősül jó, ismeretlen vagy hibás, de rendszerindító kritikus inicializálva és minősül hibás illesztőprogramok inicializálása a rendszer kihagyta. Ha a kártevő-észlelési alkalmazását egy rendszerindítás korai indítsa el a kártevőirtó illesztőprogram nem tartalmaz, vagy ha a korai indítási kártevőirtó rendszerindítás illesztőprogram le van tiltva, ez a beállítás nem befolyásolja, és minden rendszerindítás illesztőprogramok inicializálása.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067307)   
  
  **Alapértelmezett**: Jó ismeretlen és a kritikus fontosságú hibás


## <a name="wi-fi"></a>Wi-Fi  
További információkért lásd: [házirend CSP - Wi-Fi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) a Windows dokumentációjában.  

- **Az internetmegosztás letiltása**  
  Megadja, hogy internetmegosztást az eszközön.   
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067327)   

  **Alapértelmezett**: Igen  

- **Blokk automatikus csatlakozás Wi-Fi elérési pontokhoz**  
  Engedélyezése vagy letiltása az eszközön való automatikus csatlakozás Wi-Fi elérési pontokhoz.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067320)   

  **Alapértelmezett**: Igen  
  
## <a name="windows-connection-manager"></a>Windows Connection Manager  
További információkért lásd: [házirend CSP - WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) a Windows dokumentációjában.  

- **Kapcsolat blokkolása, nem tartományi hálózatokon**  
  A házirend-beállítás megakadályozza, hogy a számítógép csatlakozik egy tartományalapú hálózattal és a egy tartományon kívüli alapú hálózati egyszerre. Ha a házirend-beállítás engedélyezve van, a számítógép válaszoljon a következő esetekben alapján automatikus és manuális hálózati csatlakozási kísérletek: 
  - Ha a számítógép tartományi hálózathoz, minden automatikus kapcsolódási kísérletek nem tartományi hálózathoz már csatlakoztatva van az automatikus csatlakozási kísérletek le vannak tiltva. Amikor a számítógép már csatlakozik egy tartományon kívüli alapú hálózati, tartományi hálózatokhoz automatikus csatlakozási kísérletek le lesznek tiltva. 
  - Manuális csatlakozási kísérletek, amikor a számítógép már csatlakozik vagy egy tartományhoz nem hálózati vagy a tartományi hálózaton keresztül media eltérő Ethernet és a egy felhasználó megpróbál egy további hálózathoz való manuális kapcsolat létrehozása ezen a jelen szabályzat megsértése beállítás, a meglévő hálózati kapcsolat megszakad, és a manuális kapcsolódás engedélyezett. Amikor a számítógép már csatlakozik vagy egy nem tartományi alapú hálózati vagy a tartományi hálózaton over Ethernet, és a egy felhasználó megpróbál egy további hálózathoz való manuális kapcsolat létrehozása szabályzatsértéséről, a házirend-beállítás, a meglévő Ethernet-kapcsolat szigorúan betartja, és a manuális csatlakozási kísérlet le van tiltva.  

  Ha a házirend-beállítás nincs konfigurálva, vagy le van tiltva, a számítógépek csatlakozni egyszerre a tartomány és a nem tartományi hálózatokon is engedélyezettek.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067323)  

  **Alapértelmezett**: Enabled
  
## <a name="windows-defender"></a>Windows Defender  
További információkért lásd: [házirend CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) a Windows dokumentációjában.  

- **A bejövő e-mailek vizsgálata**  
  Engedélyezi vagy letiltja az e-mailek vizsgálata.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067116)  
  
  **Alapértelmezett**: Igen  

- **Office-alkalmazások indítsa el a gyermek-folyamat típusa**  
  Office-alkalmazások nem engedélyezett az gyermekobjektum folyamatok létrehozása. Ez magában foglalja a Word, Excel, PowerPoint, a OneNote és a hozzáférés. Ez az egy tipikus kártevő szoftverek, különösen a makró-alapú támadásokkal szemben, amelyek az Office-alkalmazások elindításához, vagy letöltheti a rosszindulatú végrehajtható fájlok.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067121)  
  
  **Alapértelmezett**: Letiltás
  
- **Defender minta küldésének jóváhagyás típusa**  
  A felhasználó hozzájárul a szint a Windows Defender adatküldéshez. Ha már rendelkezik a szükséges feltételeket, a Windows Defender küldi el őket. Ha nem, (és ha a felhasználó soha nem szeretne feltenni által megadott), a felhasználói felület a felhasználó hozzájárulását (amikor a Defender/AllowCloudProtection engedélyezett) az adatok küldésének kérjen indul el.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067131)  
  
  **Alapértelmezett**: Biztonságos minták automatikus küldése 
  
- **Aláírás-frissítési időköz (óra)**  
  Defender aláírás-frissítési időköz (óra)
  
  **Alapértelmezett**: 4
  
- **Parancsfájl letöltött tartalom végrehajtási típusa**  
  Defender parancsfájl letöltött tartalom végrehajtási típusa
  
  **Alapértelmezett**: Letiltás
  
- **Hitelesítő adatok lopásának megjelölése típus megakadályozása**  
  Windows Defender Credential Guard virtualizálás-alapú biztonsági használatával elkülöníteni a titkos kódok, hogy csak a kiemelt jogosultságú rendszerszoftverek férhessenek hozzá őket. A titkos kódokhoz való illetéktelen hozzáférés a hitelesítési adatok ellopását okozó (például pass-the-hash vagy pass-the-ticket típusú) támadásokhoz vezethetnek. Windows Defender Credential Guard megakadályozza, hogy ezeket a támadásokat NTLM-jelszókivonatok, a Kerberos jegymegadási jegyek és a tartományi hitelesítő adatok, alkalmazások által tárolt hitelesítő adatok ellenőrzését.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067065)  
  
  **Alapértelmezett**: Engedélyezés

- **E-mailek tartalmának végrehajtási típus**  
  Ez a szabály letiltja a legyenek a következő fájltípusokat, futtatása vagy a Microsoft Outlook vagy a webes levelezésben (például Gmail.com vagy Outlook.com) látható e-mailt indított: Végrehajtható fájl (például .exe, .dll vagy .scr) fájlok, parancsfájlok (például egy PowerShell .ps, Basic .vbs vagy .js JavaScript-fájl) parancsfájl archív fájlokban.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067063)  
  
  **Alapértelmezett**: Letiltás

- **Az Adobe Reader indítsa el a gyermek folyamatban**  

  **Alapértelmezett**: Engedélyezés

- **Hálózati védelem típusa**  
  Ez a szabályzat lehetővé teszi a hálózatvédelem (blokk vagy naplózási) kapcsolja be vagy ki a Windows Defender Exploit Guard. Hálózatvédelem funkciója a Windows Defender Exploit Guard, amely védelmet biztosít az alkalmazottak az Internet elérésére folytathatnak, a biztonsági rés kiaknázása elleni futtató helyek és a rosszindulatú bármilyen alkalmazást használja. Ez magában foglalja, megakadályozza, hogy a külső böngészők veszélyes helyekre csatlakozzanak. Értéktípus: egész szám. Ha engedélyezi ezt a beállítást, hálózati védelem be van kapcsolva, és az alkalmazottak nem kapcsolhatja ki. A következő beállítások szabályozhatók működését: Blokk- és naplózási. Ha engedélyezi ezt a házirendet, a "Letiltása" beállítással, felhasználók vagy alkalmazások le lesznek tiltva veszélyes tartományokhoz csatlakozzon. Ezt a tevékenységet, a Windows Defender biztonsági központban tekintheti meg. Ha engedélyezi ezt a házirendet, a "Naplózási" beállítással, felhasználók vagy alkalmazások veszélyes tartományok csatlakozzanak nem tiltható le. Azonban továbbra is látni fogja ezt a tevékenységet, a Windows Defender biztonsági központban. Ha letiltja ezt a házirendet, felhasználók vagy alkalmazások veszélyes tartományok csatlakozzanak nem tiltható le. Nem láthatja minden olyan hálózati aktivitás a Windows Defender biztonsági központban. Ha nem konfigurálja a házirendet, blokkolja a hálózat le van tiltva alapértelmezés szerint.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067102)  
  
  **Alapértelmezett**: Engedélyezés
  
- **Defender vizsgálat napjának ütemezése**  
  Defender a vizsgálat napjának ütemezése.
  
  **Alapértelmezett**: mindennap
  
- **Felhőalapú védelem**  
  Legmagasabb szintű védelme érdekében a számítógépen, a Windows Defender küld adatokat a Microsoft kapcsolatos esetleges problémákról talál. A Microsoft elemzi ezt az információt, többet megtudhat, illetve más ügyfelek számára, és továbbfejlesztett megoldásokat kínálnak.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067039)
  
  **Alapértelmezett**:  Igen  

- **Defender potenciálisan nemkívánatos alkalmazás**  
  A Windows Defender víruskereső vélhetően nemkívánatos alkalmazások (elleni) védelmi szolgáltatása is azonosíthatja és letiltása végpontjaira való letöltését és telepítését a hálózaton. Ezek az alkalmazások nem tekinthető a vírusok, kártevők vagy egyéb fenyegetések típusú, de előfordulhat, hogy műveleteket hajthat végre, amelyek hátrányosan érintik a teljesítményük, vagy használjon végpontok. ELLENI is tekintse meg az alkalmazásokat, amelyek gyenge, hogy tekintendő. Tipikus elleni működés tartalmazza: Különböző típusú Ad injektálás illesztőprogram webböngészők és a beállításjegyzék optimalizálókat a kötegelés szoftverek, amely észleli a problémákat, javítsa ki a hibákat, de továbbra is a végponton, és nincs módosítása vagy optimalizálása (más néven "engedélytelen víruskereső" programok) kérelem fizetési. Ezek az alkalmazások növelheti a kockázat kártevő szoftverrel fertőzött folyamatban van a hálózati vezethetnek kártevőszoftver-fertőzések kell nehezebben azonosításához, és is éveim informatikai erőforrásokat az alkalmazások karbantartása.  
  [További információ](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)    
  
  **Alapértelmezett**: Letiltás  

- **Parancsfájl rejtjelezett makró kód típusa**  
  Kártevők és más fenyegetések ellen megkísérelheti rejtse, és a rosszindulatú kódot az egyes parancsfájl fájlok elrejtése. Ez a szabály megakadályozza a parancsfájlok, amelyek futtatását úgy tűnik, hogy rejtjelezett lehet.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067026)  
  
  **Alapértelmezett**: Letiltás
  
- **Cserélhető adathordozók vizsgálata teljes vizsgálat során**  
  Lehetővé teszi, hogy a Windows Defender egy teljes vizsgálatok során a cserélhető meghajtókon (például flash meghajtók) rosszindulatú vagy nemkívánatos szoftverek vizsgálata. A Windows Defender víruskereső USB-eszközök végrehajtása előtt az összes fájlt megvizsgálja.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067036)  
  
  **Alapértelmezett**: Igen  
  
- **Archív fájlok ellenőrzése**  
  Defender vizsgálat archív fájlokban.
  
  **Alapértelmezett**: Igen
  
- **Viselkedésfigyelés engedélyezése**  
  Engedélyezi vagy tiltja a funkciót a Windows Defender Viselkedésfigyelés engedélyezése. Beágyazott Windows 10, érzékelőktől gyűjtése és az operációs rendszer viselkedési jelek feldolgozásához és az érzékelő adatokat küld a Microsoft Defender ATP, elkülönített, privát felhő példányát.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067111)  
  
  **Alapértelmezett**: Igen

- **Hálózati mappákból megnyitott fájlok vizsgálata**  
  Ha a fájlok írásvédettek, felhasználó nem fog tudni eltávolítani az észlelt kártevőket.
  
  **Alapértelmezett**: Igen

- **Nem megbízható USB-folyamat típusa**  
  Erről a szabályról a rendszergazdák megakadályozhatják nem aláírt vagy nem megbízható végrehajtható fájlok USB cserélhető meghajtók, például SD-kártyán futtatja.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067100)  
  
  **Alapértelmezett**: Letiltás
  
- **Egyéb Office-alkalmazások feldolgozásához injektálási típusa**  
  Office-alkalmazásokban, beleértve a Word, Excel, PowerPoint és OneNote-ban, nem tudják injektovat kód más folyamatokba. Ez általában kártevő futtatására szolgál rosszindulatú kódot próbál a víruskereső vizsgálati motorokból tevékenység elrejtéséhez.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067019)  
  
  **Alapértelmezett**:  Letiltás
  
- **Office-makrók letiltására szolgáló kód engedélyezése Win32 importálás típusa**  
  Kártevő használatával makró kódot az Office-fájlok importálása és a Win32 dll-fájlok, amelyek ezután felhasználhatók az API-hívásokat, hogy további fertőzéstől során a rendszer betöltése. Ez a szabály megpróbálja letiltása az Office-fájlokat tartalmaz, amely képes Win32 dll-fájlok importálása a makró-kódot. Ez magában foglalja a Word, Excel, PowerPoint és OneNote-ban.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067130)  
  
  **Alapértelmezett**: Letiltás  
  
- **Defender felhőalapú blokkblob szintje**  
  Defender felhőalapú blokkblob szintje.
  
  **Alapértelmezett**: Nincs konfigurálva

- **Valós idejű figyelés**  
  Defender valós idejű figyelést igényel.
  
  **Alapértelmezett**: Igen
 
- **Az Office kommunikációs alkalmazások indítása egy gyermek folyamatban**  

  **Alapértelmezett**:  Engedélyezés

- **Office alkalmazások végrehajtható tartalom létrehozása vagy az indítási típusa**  
  Ez a szabály a gyanús és kártékony bővítményeket és parancsfájlokat (bővítmények), hogy hozzon létre, vagy indítsa el a végrehajtható fájlok által használt jellemző viselkedés célozza. Ez a jellemző kártevő technika. Bővítmények az Office-alkalmazások által használt le lesznek tiltva. Általában ezek használja a Windows Scripting Host (.wsh fájlok), amely bizonyos feladatok automatizálására, vagy adja meg a felhasználó által létrehozott bővítmény szolgáltatásai parancsfájlok futtatása.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067108)  
  
  **Alapértelmezett**: Letiltás

## <a name="windows-defender-firewall"></a>Windows Defender-tűzfal  
További információkért lásd: [2.2.2 FW_PROFILE_TYPOE]( https://docs.microsoft.com/openspecs/windows_protocols/ms-fasp/7704e238-174d-4a5e-b809-5f3787dd8acc) a a Windows Protocols dokumentáció.  

- **Tűzfal profil tartomány**  
  Megadja a profilok, amelyhez a szabály tartozik: Magánjellegű és nyilvános tartományokban. Ezt az értéket a profil-tartományokhoz csatlakozó hálózatok jelöli.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2066796)  

  - **Blokkolja a bejövő kapcsolatok**  
    **Alapértelmezett**: Igen

  - **Szükséges kimenő kapcsolatok**  
    **Alapértelmezett**: Igen 

  - **Bejövő értesítések letiltva**  
    **Alapértelmezett**: Igen

  - **Tűzfal engedélyezve van**  
    **Alapértelmezett**: Engedélyezett

- **Nyilvános tűzfalprofil**  
  Megadja a profilok, amelyhez a szabály tartozik: Magánjellegű és nyilvános tartományokban. Ez az érték a profilt a nyilvános hálózatok jelöli. Ezek a hálózatok besorolt nyilvános által a rendszergazdák a fogadó kiszolgálón. A besorolás akkor történik meg az első alkalommal a gazdagép csatlakozik a hálózathoz. Általában ezek a hálózatok megegyeznek, kávézóban – üzemelő hálózathoz, és más nyilvános helyeken, ha nem állnak megbízható hálózati vagy a rendszergazda a társaknak.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067143)  

  - **Blokkolja a bejövő kapcsolatok**  
    **Alapértelmezett**: Igen

  - **Szükséges kimenő kapcsolatok**  
    **Alapértelmezett**: Igen 

  - **Bejövő értesítések letiltva**  
    **Alapértelmezett**: Igen

  - **Tűzfal engedélyezve van**  
    **Alapértelmezett**: Engedélyezett

  - **A csoportházirend nem egyesített kapcsolatbiztonsági szabályok**  
    **Alapértelmezett**: Igen

  - **A csoportházirend nem egyesített házirend szabályai**  
    **Alapértelmezett**: Igen

- **Privát tűzfalprofil**  
  Megadja a profilok, amelyhez a szabály tartozik: Magánjellegű és nyilvános tartományokban. Ezt az értéket a profil magánhálózatok jelöli.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067041)  

   - **Blokkolja a bejövő kapcsolatok**  
    **Alapértelmezett**: Igen

  - **Szükséges kimenő kapcsolatok**  
    **Alapértelmezett**: Igen 

  - **Bejövő értesítések letiltva**  
    **Alapértelmezett**: Igen

  - **Tűzfal engedélyezve van**  
    **Alapértelmezett**: Engedélyezett

## <a name="windows-hello-for-business"></a>Vállalati Windows Hello  
- **Szükséges a kibővített hamisításszűrés, ha elérhető**  
  Ha igen, a eszközök fogja használni a hamisítások kibővített szűrését, ha elérhető. Ha nem, a hamisításszűrés tiltva lesz. Nincs konfigurálva lesz az ügyfél konfigurációja az irányadó.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067192)

  **Alapértelmezett**: Igen

- **A vállalati Windows Hello konfigurálása**   
  Windows Hello for Business egy alternatív módszer a azáltal, hogy a jelszavak, intelligens kártyák és a virtuális intelligens kártyák a Windows-ba történő bejelentkezéskor. Ha engedélyezi, vagy nem konfigurálja ezt a beállítást, az eszköz kiépítése Windows Hello for Business. Ha letiltja ezt a beállítást, az eszköz nem építhet ki Windows Hello for Business bármely felhasználó számára.

  **Alapértelmezett**: Igen

- **Kisbetűk használatának megkövetelése a PIN-kód**  
  Ha szükséges, a felhasználók PIN-kód tartalmaznia kell legalább egy kisbetű.

  **Alapértelmezett**: Engedélyezett

- **Speciális karakterek megkövetelése a PIN-kód**  
  Ha szükséges, a felhasználó PIN-kód legalább egy speciális karaktert használniuk kell.

  **Alapértelmezett**: Engedélyezett

- **PIN-kód minimális hossza**  
  PIN kód minimális hosszának 4 és 127 karakter között kell lennie.

  **Alapértelmezett**: 6

- **Nagybetűk használatának megkövetelése a PIN-kód**  
  Ha szükséges, a felhasználók PIN-kód tartalmaznia kell legalább egy nagybetű.

  **Alapértelmezett**: Engedélyezett

## <a name="windows-ink-workspace"></a>Windows Ink-munkaterület  
További információkért lásd: [házirend CSP - WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) a Windows dokumentációjában.  

- **Ink-munkaterület**  
  Itt adhatja meg, hogy a felhasználó számára az ink-munkaterület elérését engedélyezi-e. 
  - *Le van tiltva* -ink-munkaterületen való hozzáférés le van tiltva. A funkció ki van kapcsolva.
  - *Engedélyezett* – az Ink-munkaterületen a funkció be van kapcsolva, de a zárolási képernyőn a felhasználó nem tudja elérni.
  - *Nincs konfigurálva* – az Ink-munkaterületen a funkció be van kapcsolva, és a felhasználó használhatja a zárolási képernyője felett.  

  [További információ](https://go.microsoft.com/fwlink/?linkid=2067241)  

  **Alapértelmezett**: Enabled
 
## <a name="windows-powershell"></a>Windows PowerShell  
További információkért lásd: [házirend CSP - WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) a Windows dokumentációjában.  

- **A Power shell héjparancsfájlt naplózás letiltása**  
  A házirend-beállítás lehetővé teszi, hogy az összes PowerShell-parancsfájl bemenetében a Microsoft-Windows-PowerShell/műveleti eseménynaplóba naplózását. Ha ez a szabályzatbeállítás engedélyezi, Windows PowerShell parancsok, parancsfájl-blokkokban, funkciók és - szkriptek feldolgozása projekttárolóba interaktív módon vagy az automatizálás hív-e. Ha letiltja ezt a beállítást, a PowerShell parancsfájl bemenetében naplózása le van tiltva. A parancsfájl blokk meghívása a naplózás engedélyezése, a PowerShell emellett naplók eseményeket egy parancs, parancsfájl-blokkon, függvény vagy parancsfájl meghívását elindul vagy leáll. Eseménynaplók nagy mennyiségű meghívási naplózásának engedélyezéséről állít elő. Megjegyezés: A házirend-beállítás létezik, a számítógép konfigurációja és a felhasználói beállítást a csoportházirend-szerkesztőben. A számítógép-konfigurációs házirend-beállítás élvez a felhasználó-konfigurációs házirend-beállítást.  
  [További információ](https://go.microsoft.com/fwlink/?linkid=2067330)  

  **Alapértelmezett**: Enabled

## <a name="whats-changed-in-the-new-template"></a>Az új sablon változásai
A *Spring 2019 frissítés (19 órával 1) a mobileszköz-kezelési biztonsági alapterv* van a következő változásokat a sablonhoz a *előzetes* sablon.

### <a name="changes-to-the-baseline-settings"></a>Az alapkonfiguráció beállításainak módosítása
A következő beállításokat a következők egyikét:
- *Új* ezt az alaptervet legújabb verziójában.
- *Eltávolított* a a legújabb alapkonfigurációt, de jelen volt a korábbi verzióban.
- *Módosítás dátuma* valamilyen módon, hogyan a korábbi verzióban jelent meg a beállításokat. 

*[Új]*  [ **Fent zárolási**](#above-lock):
- **Hangvezérelt alkalmazások zárolt képernyőn aktiválása**    

*[Új]*  [ **Alkalmazáskezelés**](#application-management): 
- **Telepítések letiltása felhasználói vezérlése**  
- **Emelt szintű jogosultságokkal letiltása az MSI-alkalmazások telepítésére**  

*[Eltávolított]*  [ **Bitlocker**](#bitlocker):  
- Bit Széfjét a cserélhető meghajtót házirend > **titkosítási módszer**
- **Rögzített meghajtó házirend bit széfjének** *(összes beállítás)*
- **Tároló meghajtó Rendszerházirend bites** *(összes beállítás)*

*[Új]*  [ **Kapcsolat**](#connectivity):
- **Biztonságos hozzáférés az UNC elérési útvonalainak konfigurálása**

*[Új]*  [ **Device Guard**](#device-guard):
- **A virtualizálás-alapú biztonság**


*[Új]*  [ **DMA Guard**](#dma-guard):
- **A külső eszközök nem kompatibilisek a Kernel DMA védelmet enumerálási**  

*[Új]*  [ **Az Internet Explorer**](#internet-explorer):
- **Explorer az internet zóna frissítések állapotsor parancsfájl használatával**
- **Az Internet Explorer az internet zóna húzza és dobja el, vagy másolja és illessze be a fájlokat**  
- **Az Internet Explorer korlátozott zóna .NET-keretrendszer tartománybeli összetevők**  
- **Az Internet Explorer helyi zónán nem futtathatnak kártevőirtó ActiveX-vezérlők**
- **Az Internet Explorer titkosítás támogatása**  

*[Változat]*  [ **Az Internet Explorer**](#internet-explorer):
- **Az Internet Explorer internetes zóna automatikus kérése fájlletöltések** > az alapértelmezett értéke mostantól **letiltott**. Előzetes verzióban érhető el ez lett beállítva engedélyezve.

*[Új]*  [ **Távsegítség**](#remote-assistance):  
- **A kért Távsegítség** 
  - **A kért Távsegítség engedély**
  - **Jegy maximális idő érték**  
  - **Jegy maximális időtartam**  
  - **E-mailben meghívást metódus**


*[Új]*  [ **A WIndows Defender**](#windows-defender):
- **Az Adobe Reader indítsa el a gyermek folyamatban**  
- **Az Office kommunikációs alkalmazások indítása egy gyermek folyamatban** 

*[Új]*  [ **Windows Defender-tűzfal**](#windows-defender-firewall)
- **Tűzfal profil tartomány**  
  - **Blokkolja a bejövő kapcsolatok**  
  - **Szükséges kimenő kapcsolatok**  
  - **Bejövő értesítések letiltva**  
  - **Tűzfal engedélyezve van**  
- **Nyilvános tűzfalprofil**  
  - **Blokkolja a bejövő kapcsolatok**  
  - **Szükséges kimenő kapcsolatok**  
  - **Bejövő értesítések letiltva**  
  - **Tűzfal engedélyezve van** 
  - **A csoportházirend nem egyesített kapcsolatbiztonsági szabályok**   
  - **A csoportházirend nem egyesített házirend szabályai**  
- **Privát tűzfalprofil**  
  - **Blokkolja a bejövő kapcsolatok**  
  - **Szükséges kimenő kapcsolatok**  
  - **Bejövő értesítések letiltva**  
  - **Tűzfal engedélyezve van**  

*[Új]*  [ **Windows Hello for Business**](#windows-hello-for-business):  
- **Szükséges a kibővített hamisításszűrés, ha elérhető**  
- **A vállalati Windows Hello konfigurálása**  
- **Kisbetűk használatának megkövetelése a PIN-kód** 
- **Speciális karakterek megkövetelése a PIN-kód** 
- **PIN-kód minimális hossza**  
- **Nagybetűk használatának megkövetelése a PIN-kód** 



<!-- The following settings were available in the Preview Baseline.   

   
## Above Lock  
For more information, see [Policy CSP - AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) in the Windows documentation.  

- **Block display of toast notifications**  
  This policy setting allows you to prevent app notifications from appearing on the lock screen. If you enable this policy setting, no app notifications are displayed on the lock screen. If you disable or don't configure this policy setting, users can choose which apps display notifications on the lock screen.
  
  **Default**: Yes  

## App Runtime    
For more information, see [Policy CSP - AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) in the Windows documentation.  

- **Microsoft accounts optional for Windows Store apps**  
  This policy setting lets you control whether Microsoft accounts are optional for Windows Store apps that require an account to sign in. This policy only affects Windows Store apps that support it. If you enable this policy setting, Windows Store apps that typically require a Microsoft account to sign in will allow users to sign in with an enterprise account instead. If you disable or don't configure this policy setting, users must sign in with a Microsoft account.  
  
  **Default**: Enabled  

## Application Management   
For more information, see [Policy CSP - ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) in the Windows documentation.  

- **Block game DVR (desktop only)**  
  Configures whether recording and broadcasting of games is allowed.
  
  **Default**: Yes  

## Auto Play   
For more information, see [Policy CSP - Autoplay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) in the Windows documentation.  

- **Auto play default auto run behavior**  
  This setting affects the default behavior for Autorun commands. Autorun commands are stored in autorun.inf files and can launch installation programs or other routines. When *Enabled*, Administrators can change the default autorun behavior on a device that runs Windows Vista or later. Behavior can be set to: a) completely disable autorun commands, or b) revert back to pre-Windows Vista behavior of automatically executing the autorun command. When set to *Disabled* or *Not Configured*, devices that run Windows Vista or later prompt the user as to whether an autorun command should run.
  
  **Default**: Do not execute  
  
- **Auto play mode**  
  This policy setting allows you to turn off the Autoplay feature. Autoplay begins reading from a drive as soon as you insert media in the drive. As a result, the setup file of programs and the music on audio media start immediately. Prior to Windows XP SP2, Autoplay is disabled by default on removable drives, such as the floppy disk drive (but not the CD-ROM drive), and on network drives. Starting with Windows XP SP2, Autoplay is enabled for removable drives as well, including Zip drives and some USB mass storage devices. If you enable this policy setting, Autoplay is disabled on CD-ROM and removable media drives, or disabled on all drives. This policy setting disables Autoplay on additional types of drives. You can't use this setting to enable Autoplay on drives on which it's disabled by default. If you disable or don't configure this policy setting, AutoPlay is enabled. Note: This policy setting appears in both the Computer Configuration and User Configuration folders. If the policy settings conflict, the policy setting in Computer Configuration takes precedence over the policy setting in User Configuration.
  
  **Default**: Disabled

- **Block auto play for non-volume devices**  
  This policy setting disallows AutoPlay for MTP devices like cameras or phones. If you enable this policy setting, AutoPlay isn't allowed for MTP devices like cameras or phones. If you disable or don't configure this policy setting, AutoPlay is enabled for non-volume devices.
  
  **Default**: Enabled  

## Bitlocker    
For more information, see [Policy CSP - Bitlocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) in the Windows documentation.  

- **Bit locker removable drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you'll be able to configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.

  For Bit locker removable drive policy, configure the following settings:

    - **Require encryption for write access**  
      **Default**: Yes  
  
    - **Encryption method**  
      **Default**: AES 256bit CBC  

- **Bit locker fixed drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you can configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.  
 
   For Bit locker fixed drive policy, configure the following settings: 
   - **Encryption method**
     **Default**: AES 256bit XTS  

- **Bit locker system drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you can configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.  

   For Bit locker system drive policy, configure the following settings:
  - **Encryption method**  
    **Default**: AES 256bit XTS  

## Browser  
For more information, see [Policy CSP - Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) in the Windows documentation.  

- **Require SmartScreen for Microsoft Edge**  
  Microsoft Edge uses Windows Defender SmartScreen (turned on) to protect users from potential phishing scams and malicious software by default. Also, by default, users can't disable (turn off) Windows Defender SmartScreen. Enabling this policy turns off Windows Defender SmartScreen and prevent users from turning it on. Don’t configure this policy to let users choose to turn Windows defender SmartScreen on or off.  
  
  **Default**: Yes  
  
- **Block malicious site access**  
  By default, Microsoft Edge allows users to bypass (ignore) the Windows Defender SmartScreen warnings about potentially malicious sites, allowing them to continue to the site. With this policy though, you can configure Microsoft Edge to prevent users from bypassing the warnings, blocking them from continuing to the site.
  
  **Default**: Yes  
  
- **Block unverified file download**
  By default, Microsoft Edge allows users to bypass (ignore) the Windows Defender SmartScreen warnings about potentially malicious files, allowing them to continue downloading the unverified file(s). Enabling this policy prevents users from bypassing the warnings, blocking them from downloading of the unverified file(s).
  
  **Default**: Yes  
  
- **Block Password Manager**  
  By default, Microsoft Edge uses Password Manager automatically, allowing users to manager passwords locally. Disabling this policy restricts Microsoft Edge from using Password Manager. Don’t configure this policy if you want to let users choose to save and manage passwords locally using Password Manager.
  
  **Default**: Yes  
  
- **Prevent certificate error overrides**  
  This policy setting prevents the user from ignoring Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificate errors that interrupt browsing (such as "expired", "revoked", or "name mismatch" errors) in Internet Explorer. If you enable this policy setting, the user can't continue browsing. If you disable or don't configure this policy setting, the user can choose to ignore certificate errors and continue browsing.
  
  **Default**: Yes  

## Connectivity  
For more information, see [Policy CSP - Connectivity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) in the Windows documentation.  

- **Block Internet download for web publishing and online ordering wizards**  
  This policy setting specifies whether Windows should download a list of providers for the web publishing and online ordering wizards. These wizards allow users to select from a list of companies that provide services such as online storage and photographic printing. By default, Windows displays providers downloaded from a Windows website in addition to providers specified in the registry. If you enable this policy setting, Windows doesn't download providers, and only the service providers that are cached in the local registry display. If you disable or don't configure this policy setting, a list of providers downloads when the user uses the web publishing or online ordering wizards. For more information that includes details on specifying service providers in the registry, see the documentation for the web publishing and online ordering wizards.  
  
  **Default**: Enabled  

- **Block downloading of print drivers over HTTP**  
  This policy setting specifies whether to allow this client to download print driver packages over HTTP. To set up HTTP printing, non-inbox drivers need to be downloaded over HTTP. Note: This policy setting doesn't prevent the client from printing to printers on the Intranet or the Internet over HTTP. It only prohibits downloading drivers that aren't already installed locally. If you enable this policy setting, print drivers can't be downloaded over HTTP. If you disable or don't configure this policy setting, users can download print drivers over HTTP.
  
  **Default**: Enabled  

## Credentials Delegation  
For more information, see [Policy CSP - CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) in the Windows documentation.  

- **Remote host delegation of non-exportable credentials**  
  Remote host allows delegation of non-exportable credentials. When using credential delegation, devices provide an exportable version of credentials to the remote host, which exposes users to the risk of credential theft from attackers on the remote host. If you enable this policy setting, the host supports Restricted Admin or Remote Credential Guard mode. If you disable or don't configure this policy setting, Restricted Administration and Remote Credential Guard mode aren't supported. User will always need to pass their credentials to the host.  

  
  **Default**: Enabled  

## Credentials UI  
For more information, see [Policy CSP - CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) in the Windows documentation.  

- **Enumerate administrators** 
  This policy setting controls whether administrator accounts display when a user attempts to elevate a running application. By default, administrator accounts aren't displayed when the user attempts to elevate a running application. If you enable this policy setting, all local administrator accounts on the PC display so the user can choose one and enter the correct password. If you disable this policy setting, users will always be required to type a user name and password to elevate.  

  
  **Default**: Disabled  

## Data Protection  
For more information, see [Policy CSP - DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) in the Windows documentation.  

- **Block direct memory access**  
  This policy setting allows you to block direct memory access (DMA) for all hot pluggable PCI downstream ports until a user logs into Windows. Once a user logs in, Windows will enumerate the PCI devices connected to the host plug PCI ports. Every time the user locks the machine, DMA is blocked on hot plug PCI ports with no children devices until the user logs in again. Devices that were already enumerated when the machine was unlocked will continue to function until unplugged. This policy setting is only enforced when BitLocker or device encryption is enabled.
  
  
  **Default**: Yes  

## Device Guard  
For more information, see [Policy CSP - DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) in the Windows documentation.  

- **Credential Guard**  
  This setting lets users turn on Credential Guard with virtualization-based security to help protect credentials at next reboot.
   
  **Default**: Enable with UEFI lock 

- **Enable virtualization based security**   
  Turns on virtualization-based security (VBS) at the next reboot. Virtualization-based security uses the Windows Hypervisor to provide support for security services.
  
  **Default**: Yes  


- **Launch system guard**    
  **Default**: Enabled  

## Device Installation  
For more information, see [Policy CSP - DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) in the Windows documentation.  

- **Hardware device installation by device identifiers**  
  This policy setting allows you to specify a list of Plug and Play hardware IDs and compatible IDs for devices that Windows is prevented from installing. This policy setting takes precedence over any other policy setting that allows Windows to install a device. If you enable this policy setting, Windows is prevented from installing a device whose hardware ID or compatible ID appears in the list you create. If you enable this policy setting on a remote desktop server, the policy setting affects redirection of the specified devices from a remote desktop client to the remote desktop server. If you disable or don't configure this policy setting, devices can install and update as allowed or prevented by other policy settings.
  
  **Default**: Block hardware device installation  

    When *Block hardware device installation* is selected, the following settings are available.
  
    - **Remove matching hardware devices**   
    This setting is available only when *Hardware device installation by device identifiers* is set to *Block hardware device installation*.
      
      **Default**: Yes
  
    - **Hardware device identifiers that are blocked**  
       This setting is available only when *Hardware device installation by device identifiers* is set to *Block hardware device installation*.
      
      **Default**: Yes  
  
- **Hardware device installation by setup classes**  
  This policy setting allows you to specify a list of device setup class globally unique identifiers (GUIDs) for device drivers that Windows is prevented from installing. This policy setting takes precedence over any other policy setting that allows Windows to install a device. If you enable this policy setting, Windows is prevented from installing or updating device drivers whose device setup class GUIDs appear in the list you create. If you enable this policy setting on a remote desktop server, the policy setting affects redirection of the specified devices from a remote desktop client to the remote desktop server. If you disable or don't configure this policy setting, Windows can install and update devices as allowed or prevented by other policy settings.
  
  **Default**: Block hardware device installation  

    When *Block hardware device installation* is selected, the following settings are available.
    - **Remove matching hardware devices**    
    This setting is available only when *Hardware device installation by setup classes* is set to *Block hardware device installation*.  

      **Default**: *No default configuration*  
  
    - **Hardware device identifiers that are blocked**  
      This setting is available only when *Hardware device installation by setup classes* is set to *Block hardware device installation*.
      
      **Default**: *No default configuration*  

## Device Lock  
For more information, see [Policy CSP - DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) in the Windows documentation.  

- **Prevent use of camera**  
  Disables the lock screen camera toggle switch in PC Settings and prevents a camera from being invoked on the lock screen. By default, users can enable invocation of an available camera on the lock screen. If you enable this setting, users will no longer be able to enable or disable lock screen camera access in PC Settings, and the camera can't be invoked on the lock screen. 
  
  **Default**: Enabled  

- **Require password**  
  Specifies whether device lock is enabled.
  
  **Default**: Yes  
  
    When *Require password* is set to *Yes*, the following settings are available.

    - **Password minimum character set count**  
      The number of complex element types (uppercase and lowercase letters, numbers, and punctuation) required for a strong PIN or password. PIN enforces the following behavior for desktop and mobile devices: 1 - Digits only 2 - Digits and lowercase letters are required 3 - Digits, lowercase letters, and uppercase letters are required. Not supported in desktop Microsoft accounts and domain accounts. 4 - Digits, lowercase letters, uppercase letters, and special characters are required. Not supported in desktop. The default value is 1. 
      
      **Default**: 3  
  
    - **Number of sign-in failures before wiping device**  
      The number of authentication failures allowed before the device is wiped. A value of 0 disables device wipe functionality.
        
      **Default**: 10  
  
    - **Password expiration (days)**  
      The Maximum password age policy setting determines how long (in days) that a password can be used before the system requires the user to change it. You can set passwords to expire after a number of days between 1 and 999, or you can specify that passwords never expire by setting the number of days to 0. If Maximum password age is between 1 and 999 days, the minimum password age must be less than the maximum password age. If Maximum password age is set to 0, Minimum password age can be any value between 0 and 998 days.
      
      **Default**: 60  
  
    - **Required password type**  
      Determines the type of PIN or password required.
      
      **Default**: Alphanumeric  
  
    - **Minimum password length**  
      The Minimum password length policy setting determines the least number of characters that can make up a password for a user account. You can set a value of between 1 and 14 characters, or you can establish that no password is required by setting the number of characters to 0.
      
      **Default**: 8  
  
    - **Block simple passwords**  
      Specifies whether PINs or passwords such as "1111" or "1234" are allowed. For the desktop, it also controls the use of picture passwords.
      
      **Default**: Yes  
        *A setting of Yes prevents use of simple passwords.* 

  - **Prevent reuse of previous passwords**  
    Specifies how many passwords can be stored in the history that can’t be used. The value includes the user's current password. For example, with a setting of *1* the user can't reuse their current password when choosing a new password. A setting of *5* means that a user can't set their new password to their current password or any of their previous four passwords.
    
    **Default**: 24  

- **Prevent slide show**  
  Disables the lock screen slide show settings in PC Settings and prevents a slide show from playing on the lock screen. By default, users can enable a slide show that will run after they lock the machine. If you enable this setting, users can't modify slide show settings in PC Settings, and no slide show can start.
  
    **Default**: Enabled  
    *A setting of Enabled prevents slide shows from running.* 

- **Password minimum age in days**  
  The Minimum password age policy setting determines the period of time (in days) that a password must be used before the user can change it. You can set a value between 1 and 998 days, or you can allow password changes immediately by setting the number of days to 0. The minimum password age must be less than the Maximum password age, unless the maximum password age is set to 0, indicating that passwords will never expire. If the maximum password age is set to 0, the minimum password age can be set to any value between 0 and 998.
  
    **Default**: 1  

## Event Log Service  
For more information, see [Policy CSP - EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) in the Windows documentation.  

- **Security log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
   **Default**: 196608  

- **System log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
  **Default**: 32768  

- **Application log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
  **Default**: 32768  

## Experience  
For more information, see [Policy CSP - Experience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) in the Windows documentation.  

- **Block Windows Spotlight**  
  Allows IT admins to turn off all Windows Spotlight Features - Window spotlight on lock screen, Windows Tips, Microsoft consumer features, and other related features.
  
  **Default**: Yes  

  When *Block Windows Spotlight* is set to *Yes*, the following settings are available.
  
  - **Block third-party suggestions in Windows Spotlight**  
    Specifies whether to allow app and content suggestions from third-party software publishers in Windows spotlight features like lock screen spotlight, suggested apps in the Start menu, and Windows tips. Users may still see suggestions for Microsoft features, apps, and services.
      
    **Default**: Yes  
   - **Block consumer specific features**  
      Allows IT admins to turn on experiences that are typically for consumers only, such as Start suggestions, Membership notifications, Post-OOBE app install, and redirect tiles.
      
     **Default**: Yes  


## Exploit Guard  
For more information, see [Policy CSP - ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) in the Windows documentation.  

- **Exploit protection XML**  
  Enables the IT admin to push out a configuration that represents the desired system and application mitigation options to all the devices in the organization. The configuration is represented by an XML. Exploit protection helps protect devices from malware that use exploits to spread and infect. You use the Windows Security app or PowerShell to create a set of mitigations (known as a configuration). You can then export this configuration as an XML file and share it with multiple machines on your network so they all have the same set of mitigation settings. You can also convert and import an existing EMET configuration XML file into an exploit protection configuration XML.
  
  **Default**: *Sample xml is provided* 
 
## File Explorer  
For more information, see [Policy CSP - FileExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) in the Windows documentation.  

- **Block data execution prevention**  
  Disabling data execution prevention can allow certain legacy plug-in applications to function without terminating Explorer.
  
  **Default**: Disabled  
   
- **Block heap termination on corruption**  
  Disabling heap termination on corruption can allow certain legacy plug-in applications to function without terminating Explorer immediately, although Explorer may still terminate unexpectedly later.
  
  **Default**: Disabled  
    

## Internet Explorer  
For more information, see [Policy CSP - InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) in the Windows documentation.  


- **Internet Explorer internet zone access to data sources**  
  This policy setting allows you to manage whether Internet Explorer can access data from another security zone using the Microsoft XML Parser (MSXML) or ActiveX Data Objects (ADO). If you enable this policy setting, users can load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you select Prompt in the drop-down box, users are queried to choose whether to allow a page to load in the zone that uses MSXML or ADO to access data from another site in the zone. If you disable this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you don't configure this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag content from different domains within windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in the same window. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting in the Internet Options dialog. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in the same window. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy setting or don't configure it, users can drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting in the Internet Options dialog.
  
  **Default**: Disabled
  
- **Internet Explorer certificate address mismatch warning**  
  This policy setting allows you to turn on the certificate address mismatch security warning. When this policy setting is turned on, the user is warned when visiting Secure HTTP (HTTPS) websites that present certificates issued for a different website address. This warning helps prevent spoofing attacks. If you enable this policy setting, the certificate address mismatch warning always appears. If you disable or don't configure this policy setting, the user can choose whether the certificate address mismatch warning appears (by using the Advanced page in the Internet Control panel).
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone less privileged sites**  
  This policy setting allows you to manage whether Web sites from less privileged zones, such as Internet sites, can navigate into this zone. If you enable this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone. The security zone will run without the added layer of security that is provided by the Protection from Zone Elevation security feature. If you select Prompt in the drop-down box, a warning is issued to the user that potentially risky navigation is about to occur. If you disable this policy setting, possibly harmful navigation is prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control. If you don't configure this policy setting, the possibly harmful navigations are prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone automatic prompt for file downloads**  
  This policy setting determines whether users are prompted for non user-initiated file downloads. Regardless of this setting, users will receive file download dialogs for user-initiated downloads. If you enable this setting, users will receive a file download dialog for automatic download attempts. If you disable or don't configure this setting, file downloads that aren't user-initiated are blocked, and users will see the Notification bar instead of the file download dialog. Users can then click the Notification bar to allow the file download prompt.
  
  **Default**: Disabled
  
- **Internet Explorer internet zone .NET Framework reliant components**  
  This policy setting allows you to manage whether .NET Framework components that aren't signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute unsigned managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute unsigned managed components. If you disable this policy setting, Internet Explorer won't execute unsigned managed components. If you don't configure this policy setting, Internet Explorer will execute unsigned managed components.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone allow only approved domains to use tdc ActiveX controls**  
  This policy setting controls if the user can run the TDC ActiveX control on websites. If you enable this policy setting, the TDC ActiveX control won't run from websites in this zone. If you disable this policy setting, the TDC Active X control will run from all sites in this zone.
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone script initiated windows**  
  This policy setting allows you to manage restrictions on script-initiated pop-up windows and windows that include the title and status bars. If you enable this policy setting, Windows Restrictions security won't apply in this zone. The security zone runs without the added layer of security provided by this feature. If you disable this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process. If you don't configure this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process.
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone include local path when uploading files to server**  
  This policy setting controls if local path information gets sent when the user is uploading a file via an HTML form. If the local path information is sent, some information may be unintentionally revealed to the server. For instance, files sent from the user's desktop may contain the user name as a part of the path. If you enable this policy setting, path information is sent when the user is uploading a file via an HTML form. If you disable this policy setting, path information is removed when the user is uploading a file via an HTML form. If you don't configure this policy setting, the user can choose whether path information gets sent when they upload a file via an HTML form. By default, path information is sent.
  
  **Default**: Disabled 
  
- **Internet Explorer disable processes in enhanced protected mode**  
  This policy setting determines whether Internet Explorer 11 uses 64-bit processes (for greater security) or 32-bit processes (for greater compatibility) when running in Enhanced Protected Mode on 64-bit versions of Windows. Important: Some ActiveX controls and toolbars may not be available when 64-bit processes are used. If you enable this policy setting, Internet Explorer 11 will use 64-bit tab processes when running in Enhanced Protected Mode on 64-bit versions of Windows. If you disable this policy setting, Internet Explorer 11 will use 32-bit tab processes when running in Enhanced Protected Mode on 64-bit versions of Windows. If you don't configure this policy setting, users can turn this feature on or off using Internet Explorer settings. This feature is turned off by default.
  
  **Default**: Enabled 
  
- **Internet Explorer ignore certificate errors**  
  This policy setting prevents the user from ignoring Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificate errors that interrupt browsing (such as "expired", "revoked", or "name mismatch" errors) in Internet Explorer. If you enable this policy setting, the user can't continue browsing. If you disable or don't configure this policy setting, the user can choose to ignore certificate errors and continue browsing.
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone loading of XAML files**  
  This policy setting allows you to manage the loading of Extensible Application Markup Language (XAML) files. XAML is an XML-based declarative markup language commonly used for creating rich user interfaces and graphics that take advantage of the Windows Presentation Foundation. If you enable this policy setting and set the drop-down box to Enable, XAML files are automatically loaded inside Internet Explorer. The user can't change this behavior. If you set the drop-down box to Prompt, the user is prompted for loading XAML files. If you disable this policy setting, XAML files aren't loaded inside Internet Explorer. The user can't change this behavior. If you don't configure this policy setting, the user can decide whether to load XAML files inside Internet Explorer.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone automatic prompt for file downloads**  
  This policy setting determines whether users are prompted for non user-initiated file downloads. Regardless of this setting, users will receive file download dialogs for user-initiated downloads. If you enable this setting, users will receive a file download dialog for automatic download attempts. If you disable or don't configure this setting, file downloads that aren't user-initiated are blocked, and users will see the Notification bar instead of the file download dialog. Users can then click the Notification bar to allow the file download prompt.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone security warning for potentially unsafe files**  
  This policy setting controls if the "Open File - Security Warning" message appears when the user tries to open executable files or other potentially unsafe files (from an intranet file share by using File Explorer, for example). If you enable this policy setting and set the drop-down box to Enable, these files open without a security warning. If you set the drop-down box to Prompt, a security warning appears before the files open. If you disable this policy setting, these files don't open. If you don't configure this policy setting, the user can configure how the computer handles these files. By default, these files are blocked in the Restricted zone, enabled in the Intranet and Local Computer zones, and set to prompt in the Internet and Trusted zones.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone cross site scripting filter**  
  This policy controls if the Cross-Site Scripting (XSS) Filter will detect and prevent cross-site script injections into websites in this zone. If you enable this policy setting, the XSS Filter is turned on for sites in this zone, and the XSS Filter attempts to block cross-site script injections. If you disable this policy setting, the XSS Filter is turned off for sites in this zone, and Internet Explorer permits cross-site script injections.
  
  **Default**: Enabled 
  
- **Internet Explorer fallback to SSL3**  
  This policy setting allows you to block an insecure fallback to SSL 3.0. When this policy is enabled, Internet Explorer will attempt to connect to sites using SSL 3.0 or below when TLS 1.0 or greater fails. We recommend that you don't allow insecure fallback in order to prevent a man-in-the-middle attack. This policy doesn't affect which security protocols are enabled. If you disable this policy, system defaults are used.
  
  **Default**: No sites 
  
- **Internet Explorer locked down internet zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone launch applications and files in an iFrame**  
  This policy setting allows you to manage whether applications may be run and files may be downloaded from an IFRAME reference in the HTML of the pages in this zone. If you enable this policy setting, users can run applications and download files from IFRAMEs on the pages in this zone without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone. If you disable this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone. If you don't configure this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone.
  
  **Default**: Disable 
  
- **Internet Explorer bypass smart screen warnings about uncommon files**  
  This policy setting determines whether the user can bypass warnings from SmartScreen Filter. SmartScreen Filter warns the user about executable files that Internet Explorer users don't commonly download from the Internet. If you enable this policy setting, SmartScreen Filter warnings block the user. If you disable or don't configure this policy setting, the user can bypass SmartScreen Filter warnings.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone popup blocker**  
  This policy setting allows you to manage whether unwanted pop-up windows appear. Pop-up windows that are opened when the end user clicks a link aren't blocked. If you enable this policy setting, most unwanted pop-up windows are prevented from appearing. If you disable this policy setting, pop-up windows aren't prevented from appearing. If you don't configure this policy setting, most unwanted pop-up windows are prevented from appearing.
  
  **Default**: Enable  
  
- **Internet Explorer processes consistent MIME handling**  
  Internet Explorer contains dynamic binary behaviors: components that encapsulate specific functionality for the HTML elements to which they're attached. This policy setting controls whether the Binary Behavior Security Restriction setting is prevented or allowed. If you enable this policy setting, binary behaviors are prevented for the File Explorer and Internet Explorer processes. If you disable this policy setting, binary behaviors are allowed for the File Explorer and Internet Explorer processes. If you don't configure this policy setting, binary behaviors are prevented for the File Explorer and Internet Explorer processes.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java  
    
  
- **Internet Explorer Active X controls in protected mode**  
  This policy setting prevents ActiveX controls from running in Protected Mode when Enhanced Protected Mode is enabled. When a user has an ActiveX control installed that isn't compatible with Enhanced Protected Mode and a website attempts to load the control, Internet Explorer notifies the user and gives the option to run the website in regular Protected Mode. This policy setting disables this notification and forces all websites to run in Enhanced Protected Mode. Enhanced Protected Mode provides additional protection against malicious websites by using 64-bit processes on 64-bit versions of Windows. For computers running at least Windows 8, Enhanced Protected Mode also limits the locations Internet Explorer can read from in the registry and the file system. When Enhanced Protected Mode is enabled, and a user comes across a website that attempts to load an ActiveX control that isn't compatible with Enhanced Protected Mode, Internet Explorer notifies the user and gives the option to disable Enhanced Protected Mode for that particular website. If you enable this policy setting, Internet Explorer won't give the user the option to disable Enhanced Protected Mode. All Protected Mode websites will run in Enhanced Protected Mode. If you disable or don't configure this policy setting, Internet Explorer notifies users and provides an option to run websites with incompatible ActiveX controls in regular Protected Mode.  
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone loading of XAML files**  
  This policy setting allows you to manage the loading of Extensible Application Markup Language (XAML) files. XAML is an XML-based declarative markup language commonly used for creating rich user interfaces and graphics that take advantage of the Windows Presentation Foundation. If you enable this policy setting and set the drop-down box to Enable, XAML files are automatically loaded inside Internet Explorer. The user can't change this behavior. If you set the drop-down box to Prompt, the user is prompted for loading XAML files. If you disable this policy setting, XAML files aren't loaded inside Internet Explorer. The user can't change this behavior. If you don't configure this policy setting, the user can decide whether to load XAML files inside Internet Explorer.
  
  **Default**: Disable  
  
- **Internet Explorer processes scripted window security restrictions**  
  Internet Explorer allows scripts to programmatically open, resize, and reposition windows of various types. The Window Restrictions security feature restricts popup windows and prohibits scripts from displaying windows in which the title and status bars aren't visible to the user or obfuscate other Windows' title and status bars. If you enable this policy setting, scripted windows are restricted for all processes. If you disable or don't configure this policy setting, scripted windows aren't restricted.
  
  **Default**: Enabled   
  
- **Internet Explorer restricted zone run Active X controls and plugins**  
  This policy setting allows you to manage whether ActiveX controls and plug-ins can run on pages from the specified zone. If you enable this policy setting, controls and plug-ins can run without user intervention. If you selected Prompt in the drop-down box, users are asked to choose whether to allow the controls or plug-in to run. If you disable this policy setting, controls and plug-ins are prevented from running. If you don't configure this policy setting, controls and plug-ins are prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone script Active X controls marked safe for scripting**  
  This policy setting allows you to manage whether an ActiveX control marked safe for scripting can interact with a script. If you enable this policy setting, script interaction can occur automatically without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow script interaction. If you disable this policy setting, script interaction is prevented from occurring. If you don't configure this policy setting, script interaction is prevented from occurring.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone logon options**  
  This policy setting allows you to manage settings for sign in options. If you enable this policy setting, you can choose from the following sign in options. 
  - *Anonymous*  - Use anonymous sign in to disable HTTP authentication and use the guest account only for the Common Internet File System (CIFS) protocol. 
  - *Prompt* - Use prompt for user name and password to query users for user IDs and passwords. After a user is queried, these values can be used silently for the rest of the session. 
  - *Automatic sign in only in Intranet zone* - Use this option to query users for user IDs and passwords in other zones. After a user is queried, these values can be used silently for the rest of the session. 
  - *Automatic sign in with current user name and password*- Use this option to attempt sign in using Windows NT Challenge Response (also known as NTLM authentication). If the server supports Windows NT Challenge Response, the sign in uses the user's network user name and password for sign in. If the server doesn't support Windows NT Challenge Response, the user is queried to provide the user name and password. 

  If you disable this policy setting, sign-in is set to *Automatic sign in only in Intranet zone*. If you don't configure this policy setting, sign-in is set to *Prompt* for username and password.
  
  **Default**: Anonymous  
  
- **Internet Explorer trusted zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, users are queried whether to allow the control to load with parameters or scripted.
  
  **Default**: Disable  
  
- **Internet Explorer check server certificate revocation**  
  This policy setting allows you to manage whether Internet Explorer will check revocation status of servers' certificates. Certificates are revoked when they are compromised or no longer valid, and this option protects users from submitting confidential data to a site that may be fraudulent or not secure. If you enable this policy setting, Internet Explorer will check to see if server certificates have been revoked. If you disable this policy setting, Internet Explorer won't check server certificates to see if they have been revoked. If you don't configure this policy setting, Internet Explorer won't check server certificates to see if they have been revoked.
  
  **Default**: Enabled 
  
- **Internet Explorer internet zone less privileged sites**  
  This policy setting allows you to manage whether Web sites from less privileged zones, such as Restricted Sites, can navigate into this zone. If you enable this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone. The security zone will run without the added layer of security that is provided by the Protection from Zone Elevation security feature. If you select Prompt in the drop-down box, a warning is issued to the user that potentially risky navigation is about to occur. If you disable this policy setting, the possibly harmful navigations are prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control. If you don't configure this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone file downloads**  
  This policy setting allows you to manage whether file downloads are permitted from the zone. This option gets determined by the zone of the page with the link causing the download, not the zone from which the file is delivered. If you enable this policy setting, files can be downloaded from the zone. If you disable this policy setting, files are prevented from being downloaded from the zone. If you don't configure this policy setting, files are prevented from being downloaded from the zone.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone run .NET Framework reliant components signed with Authenticode**  
  This policy setting allows you to manage whether .NET Framework components that are signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute signed managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute signed managed components. If you disable this policy setting, Internet Explorer won't execute signed managed components. If you don't configure this policy setting, Internet Explorer won't execute signed managed components.
  
  **Default**: Disable  
  
- **Internet Explorer prevent per user installation of Active X controls**  
  This policy setting allows you to prevent the installation of ActiveX controls on a per-user basis. If you enable this policy setting, ActiveX controls can't be installed on a per-user basis. If you disable or don't configure this policy setting, ActiveX controls can be installed on a per-user basis.
  
  **Default**: Enabled  
  
- **Internet Explorer prevent managing smart screen filter**  
  This policy setting prevents the user from managing SmartScreen Filter, which warns the user if the website they visit is known for fraudulent attempts to gather personal information through "phishing," or is known to host malware. If you enable this policy setting, the user isn't prompted to turn on SmartScreen Filter. All website addresses that aren't on the filters allow list are sent automatically to Microsoft without prompting the user. If you disable or don't configure this policy setting, the user gets prompted to decide whether to turn on SmartScreen Filter during the first-run experience.
  
  **Default**: Enable  
  
- **Internet Explorer processes MIME sniffing safety feature**  
  This policy setting determines whether Internet Explorer MIME sniffing will prevent promotion of a file of one type to a more dangerous file type. If you enable this policy setting, MIME sniffing will never promote a file of one type to a more dangerous file type. If you disable this policy setting, Internet Explorer processes will allow a MIME sniff promoting a file of one type to a more dangerous file type. If you don't configure this policy setting, MIME sniffing will never promote a file of one type to a more dangerous file type.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone download signed Active X controls**  
  This policy setting allows you to manage whether users may download signed ActiveX controls from a page in the zone. If you enable this policy, users can download signed controls without user intervention. If you select Prompt in the drop-down box, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded. If you disable the policy setting, signed controls can't download. If you don't configure this policy setting, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded.
  
  **Default**: Disable  
  
- **Internet Explorer auto complete**  
  This Auto-Complete feature can remember and suggest User names and passwords on Forms. If you enable this setting, the user can't change "User name and passwords on forms" or "prompt me to save passwords". The Auto Complete feature for User names and passwords on Forms is turned on. You have to decide whether to select "prompt me to save passwords". If you disable this setting the user can't change "User name and passwords on forms" or "prompt me to save passwords". The Auto Complete feature for User names and passwords on Forms is turned off. The user also can't opt to be prompted to save passwords. If you don't configure this setting, the user has the freedom of turning on Auto complete for User name and passwords on forms and the option of prompting to save passwords. To display this option, the users open the Internet Options dialog box, click the Contents Tab, and click the Settings button.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone allow VBscript to run**  
  This policy setting lets you decide whether VBScript can run on pages in specific Internet Explorer zones. Options include: 
  - *Enable* - VBScript runs on pages in specific zones, without any interaction. 
  - *Prompt* - Employees are prompted whether to allow VBScript to run in the zone. 
  - *Disable* - VBScript is prevented from running in the zone. If you disable or don’t configure this policy setting, VBScript runs without any interaction in the specified zone. 
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone allow only approved domains to use tdc Active X controls**  
  This policy setting controls if the user can run the TDC ActiveX control on websites. If you enable this policy setting, the TDC ActiveX control won't run from websites in this zone. If you disable this policy setting, the TDC Active X control will run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer trusted zone don't run antimalware against Active X controls**  
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled 
  
- **Internet Explorer local machine zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Medium Safety.
  
  **Default**: Disable java 
  
- **Internet Explorer intranet zone do not run antimalware against Active X controls**
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  

- **Internet Explorer restricted zone scriptlets**  
  This policy setting allows you to manage whether the user can run scriptlets. If you enable this policy setting, the user can run scriptlets. If you disable this policy setting, the user can't run scriptlets. If you don't configure this policy setting, the user can enable or disable scriptlets.
  
  **Default**: Disabled  
  
- **Internet Explorer processes notification bar**  
  This policy setting allows you to manage whether the Notification bar is displayed for Internet Explorer processes when file or code installs are restricted. By default, the Notification bar is displayed for Internet Explorer processes. If you enable this policy setting, the Notification bar displays for the Internet Explorer Processes. If you disable this policy setting, the Notification bar won't be displayed for Internet Explorer processes. If you don't configure this policy setting, the Notification bar doesn't display for Internet Explorer Processes.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone download signed ActiveX controls**  
  This policy setting allows you to manage whether users may download signed ActiveX controls from a page in the zone. If you enable this policy, users can download signed controls without user intervention. If you select Prompt in the drop-down box, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded. If you disable the policy setting, signed controls can't download. If you don't configure this policy setting, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer remove run this time button for outdated Active X controls**  
  This policy setting allows you to stop users from seeing the "Run this time" button and from running specific outdated ActiveX controls in Internet Explorer. If you enable this policy setting, users won't see the "Run this time" button on the warning message that appears when Internet Explorer blocks an outdated ActiveX control. If you disable or don't configure this policy setting, users will see the "Run this time" button on the warning message that appears when Internet Explorer blocks an outdated ActiveX control. Clicking this button lets the user run the outdated ActiveX control once. For more information, see "Outdated ActiveX Controls" in the Internet Explorer TechNet library.
  
  **Default**: Enabled 
  
- **Internet Explorer internet zone launch applications and files in an iframe**  
  This policy setting allows you to manage whether applications may be run and files may be downloaded from an IFRAME reference in the HTML of the pages in this zone. If you enable this policy setting, users can run applications and download files from IFRAMEs on the pages in this zone without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone. If you disable this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone. If you don't configure this policy setting, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone
  
  **Default**: Disable 
  
- **Internet Explorer restricted zone navigate windows and frames across different domains**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer locked down trusted zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java 
  
- **Internet Explorer check signatures on downloaded programs**  
  This policy setting allows you to manage whether Internet Explorer checks for digital signatures (which identifies the publisher of signed software and verifies it hasn't been modified or tampered with) on user computers before downloading executable programs. If you enable this policy setting, Internet Explorer will check the digital signatures of executable programs and display their identities before downloading them to user computers. If you disable this policy setting, Internet Explorer won't check the digital signatures of executable programs or display their identities before downloading them to user computers. If you don't configure this policy, Internet Explorer won't check the digital signatures of executable programs or display their identities before downloading them to user computers.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone scripting of web browser controls**  
  This policy setting determines whether a page can control embedded WebBrowser controls via script. If you enable this policy setting, script access to the WebBrowser control is allowed. If you disable this policy setting, script access to the WebBrowser control isn't allowed. If you don't configure this policy setting, the user can enable or disable script access to the WebBrowser control. By default, script access to the WebBrowser control is allowed only in the Local Machine and Intranet zones.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone cross site scripting filter**  
  This policy controls if the Cross-Site Scripting (XSS) Filter will detect and prevent cross-site script injections into websites in this zone. If you enable this policy setting, the XSS Filter is turned on for sites in this zone, and the XSS Filter attempts to block cross-site script injections. If you disable this policy setting, the XSS Filter is turned off for sites in this zone, and Internet Explorer permits cross-site script injections.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone binary and script behaviors**  
  This policy setting allows you to manage dynamic binary and script behaviors: components that encapsulate specific functionality for HTML elements to which they were attached. If you enable this policy setting, binary and script behaviors are available. If you select Administrator approved in the drop-down box, only behaviors listed in the Admin-approved Behaviors under Binary Behaviors Security Restriction policy are available. If you disable this policy setting, binary and script behaviors aren't available unless applications have implemented a custom security manager. If you don't configure this policy setting, binary and script behaviors aren't available unless applications have implemented a custom security manager.
  
  **Default**: Disable  
  
- **Internet Explorer security settings check**  
  This policy setting turns off the Security Settings Check feature, which checks Internet Explorer security settings to determine when the settings put Internet Explorer at risk. If you enable this policy setting, the feature is turned off. If you disable or don't configure this policy setting, the feature is turned on.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone security warning for potentially unsafe files**  
  This policy setting controls if the "Open File - Security Warning" message appears when the user tries to open executable files or other potentially unsafe files (from an intranet file share by using File Explorer, for example). If you enable this policy setting and set the drop-down box to Enable, these files open without a security warning. If you set the drop-down box to Prompt, a security warning appears before the files open. If you disable this policy setting, these files don't open. If you don't configure this policy setting, the user can configure how the computer handles these files. By default, these files are blocked in the Restricted zone, enabled in the Intranet and Local Computer zones, and set to prompt in the Internet and Trusted zones.
  
  **Default**: Prompt  
  
- **Internet Explorer intranet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Medium Safety.
  
  **Default**: High safety 
  
- **Internet Explorer block outdated Active X controls**  
  This policy setting determines whether Internet Explorer blocks specific outdated ActiveX controls. Outdated ActiveX controls are never blocked in the Intranet Zone. If you enable this policy setting, Internet Explorer stops blocking outdated ActiveX controls. If you disable or don't configure this policy setting, Internet Explorer continues to block specific outdated ActiveX controls. For more information, see "Outdated ActiveX Controls" in the Internet Explorer TechNet library.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone popup blocker**  
  This policy setting allows you to manage whether unwanted pop-up windows appear. Pop-up windows that are opened when the end user clicks a link aren't blocked. If you enable this policy setting, most unwanted pop-up windows are prevented from appearing. If you disable this policy setting, pop-up windows aren't prevented from appearing. If you don't configure this policy setting, most unwanted pop-up windows are prevented from appearing.
  
  **Default**: Enable  
  
- **Internet Explorer processes MK protocol security restriction**  
  The MK Protocol Security Restriction policy setting reduces attack surface area by preventing the MK protocol. Resources hosted on the MK protocol will fail. If you enable this policy setting, the MK Protocol is prevented for File Explorer and Internet Explorer, and resources hosted on the MK protocol will fail. If you disable this policy setting, applications can use the MK protocol API. Resources hosted on the MK protocol will work for the File Explorer and Internet Explorer processes. If you don't configure this policy setting, the MK Protocol is prevented for File Explorer and Internet Explorer, and resources hosted on the MK protocol will fail.
  
  **Default**: Enabled  
  
- **Internet Explorer trusted zone java permissions**   
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Low Safety.
  
  **Default**: High safety  
  
- **Internet Explorer restricted zone scripting of java applets**  
  This policy setting allows you to manage whether applets are exposed to scripts within the zone. If you enable this policy setting, scripts can access applets automatically without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow scripts to access applets. If you disable this policy setting, scripts are prevented from accessing applets. If you don't configure this policy setting, scripts are prevented from accessing applets.
  
  **Default**: Disable  
  
- **Internet Explorer locked down restricted zone java permissions**   
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java 
  
- **Internet Explorer internet zone allow only approved domains to use ActiveX controls**   
  This policy setting controls if the user is prompted to allow ActiveX controls to run on websites other than the website that installed the ActiveX control. If you enable this policy setting, the user is prompted before ActiveX controls can run from websites in this zone. The user can choose to allow the control to run from the current site or from all sites. If you disable this policy setting, the user doesn't see the per-site ActiveX prompt, and ActiveX controls can run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer include all network paths**  
  Internet Explorer include all network paths
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone protected mode**  
  This policy setting allows you to turn on Protected Mode. Protected Mode helps protect Internet Explorer from exploited vulnerabilities by reducing the locations that Internet Explorer can write to in the registry and the file system. If you enable this policy setting, Protected Mode is turned on. The user can't turn off Protected Mode. If you disable this policy setting, Protected Mode is turned off. The user can't turn on Protected Mode. If you don't configure this policy setting, the user can turn on or turn off Protected Mode.
  
  **Default**: Enable 
  
- **Internet Explorer internet zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable 
  
- **Internet Explorer locked down restricted zone smart screen**   
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer crash detection**  
  This policy setting allows you to manage the crash detection feature of add-on Management. If you enable this policy setting, a crash in Internet Explorer will exhibit behavior found in Windows XP Professional Service Pack 1 and earlier, namely to invoke Windows Error Reporting. All policy settings for Windows Error Reporting continue to apply. If you disable or don't configure this policy setting, the crash detection feature for add-on management is functional.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to High Safety.
  
  **Default**: Disable java  
  
- **Internet Explorer restricted zone active scripting**  
  This policy setting allows you to manage whether script code on pages in the zone is run. If you enable this policy setting, script code on pages in the zone can run automatically. If you select Prompt in the drop-down box, users are queried to choose whether to allow script code on pages in the zone to run. If you disable this policy setting, script code on pages in the zone is prevented from running. If you don't configure this policy setting, script code on pages in the zone is prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone logon options**  
  This policy setting allows you to manage settings for sign in options. If you enable this policy setting, you can choose from the following sign in options. Anonymous log on to disable HTTP authentication and use the guest account only for the Common Internet File System (CIFS) protocol. Prompt for user name and password to query users for user IDs and passwords. After a user is queried, these values can be used silently for the remainder of the session. Automatic log on only in Intranet zone to query users for user IDs and passwords in other zones. After a user is queried, these values can be used silently for the rest of the session. Automatic sign in with current user name and password to attempt log on using Windows NT Challenge Response (also known as NTLM authentication). If the server supports Windows NT Challenge Response, the sign in uses the user's network user name and password for log on. If the server doesn't support Windows NT Challenge Response, the user is queried to provide the user name and password. If you disable this policy setting, sign in is set to Automatic log on only in Intranet zone. If you don't configure this policy setting, sign in is set to Automatic sign in only in Intranet zone.
  
  **Default**: Prompt  
  
- **Internet Explorer restricted zone allow vbscript to run**  
  This policy setting allows you to manage whether VBScript can be run on pages from the specified zone in Internet Explorer. If you selected Enable in the drop-down box, VBScript can run without user intervention. If you selected Prompt in the drop-down box, users are asked to choose whether to allow VBScript to run. If you selected Disable in the drop-down box, VBScript is prevented from running. If you don't configure or disable this policy setting, VBScript is prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone drag content from different domains across windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.
  
  **Default**: Disabled 
  
- **Internet Explorer intranet zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable 
  
- **Internet Explorer download enclosures**  
  This policy setting prevents the user from having enclosures (file attachments) downloaded from a feed to the user's computer. If you enable this policy setting, the user can't set the Feed Sync Engine to download an enclosure through the Feed property page. A developer can't change the download setting through the Feed APIs. If you disable or don't configure this policy setting, the user can set the Feed Sync Engine to download an enclosure through the Feed property page. A developer can change the download setting through the Feed APIs.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone download unsigned Active X controls**   
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone drag content from different domains within windows**  
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disabled  
  
- **Internet Explorer processes restrict Active X install**   
  This policy setting enables applications hosting the Web Browser Control to block automatic prompting of ActiveX control installation. If you enable this policy setting, the Web Browser Control will block automatic prompting of ActiveX control installation for all processes. If you disable or don't configure this policy setting, the Web Browser Control won't block automatic prompting of ActiveX control installation for all processes.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone scriptlets**
  This policy setting allows you to manage whether the user can run scriptlets. If you enable this policy setting, the user can run scriptlets. If you disable this policy setting, the user can't run scriptlets. If you don't configure this policy setting, the user can enable or disable scriptlets.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag and drop or copy and paste files**  
  This policy setting allows you to manage whether users can drag files or copy and paste files from a source within the zone. If you enable this policy setting, users can drag files or copy and paste files from this zone automatically. If you select Prompt in the drop-down box, users are queried to choose whether to drag or copy files from this zone. If you disable this policy setting, users are prevented from dragging files or copying and pasting files from this zone. If you don't configure this policy setting, users are queried to choose whether to drag or copy files from this zone.
  
  **Default**: Disable  
  
- **Internet Explorer software when signature is invalid**   
  This policy setting allows you to manage whether software, such as ActiveX controls and file downloads, can be installed or run by the user even though the signature is invalid. An invalid signature might indicate that someone has tampered with the file. If you enable this policy setting, users are prompted to install or run files with an invalid signature. If you disable this policy setting, users can't run or install files with an invalid signature. If you don't configure this policy, users can choose to run or install files with an invalid signature.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone copy and paste via script**   
  This policy setting allows you to manage whether scripts can perform a clipboard operation (for example, cut, copy, and paste) in a specified region. If you enable this policy setting, a script can perform a clipboard operation. If you select Prompt in the drop-down box, users are queried as to whether to perform clipboard operations. If you disable this policy setting, a script can't perform a clipboard operation. If you don't configure this policy setting, a script can't perform a clipboard operation.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag content from different domains across windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.   
  **Default**: Disabled  
  
- **Internet Explorer users adding sites**  
  Prevents users from adding or removing sites from security zones. A security zone is a group of Web sites with the same security level. If you enable this policy, the site management settings for security zones are disabled. (To see the site management settings for security zones, in the Internet Options dialog box, click the Security tab, and then click the Sites button.) If you disable this policy or don't configure it, users can add Web sites to or remove sites from the Trusted Sites and Restricted Sites zones, and alter settings for the Local Intranet zone. This policy prevents users from changing site management settings for security zones established by the administrator. Note: The "Disable the Security page" policy (located in \User Configuration\Administrative Templates\Windows Components\Internet Explorer\Internet Control Panel), which removes the Security tab from the interface, takes precedence over this policy. If it's enabled, this policy is ignored. Also, see the "Security zones: Use only machine settings" policy.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone script initiated windows**  
  This policy setting allows you to manage restrictions on script-initiated pop-up windows and windows that include the title and status bars. If you enable this policy setting, Windows Restrictions security won't apply in this zone. The security zone runs without the added layer of security provided by this feature. If you disable this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process. If you don't configure this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process.
  
  **Default**: Disabled  
  
- **Internet Explorer security zones use only machine settings**  
  Applies security zone information to all users of the same computer. A security zone is a group of Web sites with the same security level. If you enable this policy, changes that the user makes to a security zone will apply to all users of that computer. If you disable this policy or don't configure it, users of the same computer can establish their own security zone settings. Use this policy to ensure that security zone settings apply uniformly to the same computer and don't vary from user to user. Also, see the "Security zones: don't allow users to change policies" policy.
  
  **Default**: Enabled  
  
- **Internet Explorer locked down local machine zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled
  
  **Default**: Disable java 
  
- **Internet Explorer restricted zone do not run antimalware against Active X controls**   
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone run .NET Framework reliant components signed with authenticode**  
  This policy setting allows you to manage whether .NET Framework components that are signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute signed managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute signed managed components. If you disable this policy setting, Internet Explorer won't execute signed managed components. If you don't configure this policy setting, Internet Explorer won't execute signed managed components.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone access to data sources**  
  This policy setting allows you to manage whether Internet Explorer can access data from another security zone using the Microsoft XML Parser (MSXML) or ActiveX Data Objects (ADO). If you enable this policy setting, users can load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you select Prompt in the drop-down box, users are queried to choose whether to allow a page to load in the zone that uses MSXML or ADO to access data from another site in the zone. If you disable this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you don't configure this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone don't run antimalware against ActiveX controls**   
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone copy and paste via script**  
  This policy setting allows you to manage whether scripts can perform a clipboard operation (for example, cut, copy, and paste) in a specified region. If you enable this policy setting, a script can perform a clipboard operation. If you select Prompt in the drop-down box, users are queried as to whether to perform clipboard operations. If you disable this policy setting, a script can't perform a clipboard operation. If you don't configure this policy setting, a script can perform a clipboard operation.
  
  **Default**: Disable  
  
- **Internet Explorer use Active X installer service**   
  This policy setting allows you to specify how ActiveX controls are installed. If you enable this policy setting, ActiveX controls are installed only if the ActiveX Installer Service is present and has been configured to allow the installation of ActiveX controls. If you disable or don't configure this policy setting, ActiveX controls, including per-user controls, are installed through the standard installation process.
  
  **Default**: Enabled  
  
- **Internet Explorer processes protection from zone elevation**  
  Internet Explorer places restrictions on each Web page it opens. The restrictions are dependent upon the location of the Web page (Internet, Intranet, Local Machine zone, and so on). For example, Web pages on the local computer have the fewest security restrictions and are in the Local Machine zone, making the Local Machine security zone a prime target for malicious users. If you enable this policy setting, any zone can be protected from zone elevation for all processes. If you disable or don't configure this policy setting, processes other than Internet Explorer or those listed in the Process List receive no such protection.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone download unsigned ActiveX controls**   
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone navigate windows and frames across different domains**   
  This policy setting allows you to manage the opening of windows and frames and access of applications across different domains. If you enable this policy setting, users can open windows and frames from other domains and access applications from other domains. If you select Prompt in the drop-down box, users are queried whether to allow windows and frames to access applications from other domains. If you disable this policy setting, users can't open windows and frames to access applications from different domains. If you don't configure this policy setting, users can open windows and frames from other domains and access applications from other domains.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone updates to status bar via script**  
  This policy setting allows you to manage whether a script can update the status bar within the zone. If you enable this policy setting, scripts can update the status bar. If you disable or don't configure this policy setting, script isn't allowed to update the status bar.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone include local path when uploading files to server**  
  This policy setting controls if local path information is sent when the user is uploading a file via an HTML form. If the local path information is sent, some information may be unintentionally revealed to the server. For instance, files sent from the user's desktop may contain the user name as a part of the path. If you enable this policy setting, path information is sent when the user is uploading a file via an HTML form. If you disable this policy setting, path information is removed when the user is uploading a file via an HTML form. If you don't configure this policy setting, the user can choose whether path information is sent when they are uploading a file via an HTML form. By default, path information is sent.
  
  **Default**: Disabled  
  
- **Internet Explorer processes restrict file download**   
  This policy setting enables applications hosting the Web Browser Control to block automatic prompting of file downloads that aren't user initiated. If you enable this policy setting, the Web Browser Control will block automatic prompting of file downloads that aren't user initiated for all processes. If you disable this policy setting, the Web Browser Control won't block automatic prompting of file downloads that aren't user initiated for all processes.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone allow only approved domains to use Active X controls**   
  This policy setting controls if the user is prompted to allow ActiveX controls to run on websites other than the website that installed the ActiveX control. If you enable this policy setting, the user is prompted before ActiveX controls can run from websites in this zone. The user can choose to allow the control to run from the current site or from all sites. If you disable this policy setting, the user doesn't see the per-site ActiveX prompt, and ActiveX controls can run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable  
  
- **Internet Explorer users changing policies**  
    Prevents users from changing security zone settings. A security zone is a group of Web sites with the same security level. If you enable this policy, the Custom Level button and security-level slider on the Security tab in the Internet Options dialog box are disabled. If you disable this policy or don't configure it, users can change the settings for security zones. This policy prevents users from changing security zone settings established by the administrator. Note: The "Disable the Security page" policy (located in \User Configuration\Administrative Templates\Windows Components\Internet Explorer\Internet Control Panel), which removes the Security tab from Internet Explorer in Control Panel, takes precedence over this policy. If it's enabled, this policy is ignored. Also, see the "Security zones: Use only machine settings" policy.
    
  **Default**: Disabled  
  
- **Internet Explorer restricted zone protected mode**  
  This policy setting allows you to turn on Protected Mode. Protected Mode helps protect Internet Explorer from exploited vulnerabilities by reducing the locations that Internet Explorer can write to in the registry and the file system. If you enable this policy setting, Protected Mode is turned on. The user can't turn off Protected Mode. If you disable this policy setting, Protected Mode is turned off. The user can't turn on Protected Mode. If you don't configure this policy setting, the user can turn on or turn off Protected Mode.
  
  **Default**: Enable  
  
- **Internet Explorer internet zone user data persistence**  
  This policy setting allows you to manage the preservation of information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. When a user returns to a persisted page, the state of the page can be restored if this policy setting is appropriately configured. If you enable this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you disable this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you don't configure this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone scripting of web browser controls**  
 
  This policy setting determines whether a page can control embedded WebBrowser controls via script. If you enable this policy setting, script access to the WebBrowser control is allowed. If you disable this policy setting, script access to the WebBrowser control isn't allowed. If you don't configure this policy setting, the user can enable or disable script access to the WebBrowser control. By default, script access to the WebBrowser control is allowed only in the Local Machine and Intranet zones.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone user data persistence**  
    This policy setting allows you to manage the preservation of information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. When a user returns to a persisted page, the state of the page can be restored if this policy setting is appropriately configured. If you enable this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you disable this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you don't configure this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk.  
  
  **Default**: Disabled  
  
- **Internet Explorer locked down intranet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java  
  
- **Internet Explorer enhanced protected mode**  
  Enhanced Protected Mode provides additional protection against malicious websites by using 64-bit processes on 64-bit versions of Windows. For computers running at least Windows 8, Enhanced Protected Mode also limits the locations Internet Explorer can read from in the registry and the file system. If you enable this policy setting, Enhanced Protected Mode is turned on. Any zone that has Protected Mode enabled will use Enhanced Protected Mode. Users won't be able to disable Enhanced Protected Mode. If you disable this policy setting, Enhanced Protected Mode is turned off. Any zone that has Protected Mode enabled will use the version of Protected Mode introduced in Internet Explorer 7 for Windows Vista. If you don't configure this policy, users can turn on or turn off Enhanced Protected Mode on the Advanced tab of the Internet Options dialog.
  
  **Default**: Enabled  
  
- **Internet Explorer bypass smart screen warnings**  
  This policy setting determines whether the user can bypass warnings from SmartScreen Filter. SmartScreen Filter warns the user about executable files that Internet Explorer users don't commonly download from the Internet. If you enable this policy setting, SmartScreen Filter warnings block the user. If you disable or don't configure this policy setting, the user can bypass SmartScreen Filter warnings.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone meta refresh**  
  This policy setting allows you to manage whether a user's browser can be redirected to another Web page if the author of the Web page uses the Meta Refresh setting (tag) to redirect browsers to another Web page. If you enable this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can be redirected to another Web page. If you disable this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can't be redirected to another Web page. If you don't configure this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can't be redirected to another Web page.
  
  **Default**: Disabled  
  
## Local Policies Security Options
For more information, see [Policy CSP - LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) in the Windows documentation. 

- **Restrict anonymous access to named pipes and shares**  
  When enabled, this security setting restricts anonymous access to shares and pipes to the settings for: (1) Named pipes that can be accessed anonymously (2) Shares that can be accessed anonymously
  
  **Default**: Yes  
  
- **Minimum session security for NTLM SSP based servers**  
  This security setting allows a server to require the negotiation of 128-bit encryption and/or NTLMv2 session security. These values are dependent on the LAN Manager Authentication Level security setting value. The options are: Require NTLMv2 session security: The connection will fail if message integrity isn't negotiated. Require 128-bit encryption. The connection will fail if strong encryption (128-bit) isn't negotiated.
  
  **Default**: Require NTLM V2 and 128 bit encryption  
  
- **Minutes of lock screen inactivity until screen saver activates**  
  Windows notices inactivity of a logon session, and if the amount of inactive time exceeds the inactivity limit, then the screen saver will run, locking the session.
  
  **Default**: 15
  
- **Require client to always digitally sign communications** 
  This security setting determines whether all secure channel traffic initiated by the domain member must be signed or encrypted. When a computer joins a domain, a computer account is created. After that, when the system starts, it uses the computer account password to create a secure channel with a domain controller for its domain. This secure channel is used to perform operations such as NTLM pass through authentication, LSA SID/name Lookup and more. This setting determines if all secure channel traffic initiated by the domain member meets minimum security requirements. Specifically it determines whether all secure channel traffic started by the domain member must be signed or encrypted. If this policy is enabled, then the secure channel won't be established unless either signing or encryption of all secure channel traffic is negotiated. If this policy is disabled, then encryption and signing of all secure channel traffic is negotiated with the Domain Controller in which case the level of signing and encryption depends on the version of the Domain Controller and the settings of the following two policies: Domain member: Digitally encrypt secure channel data (when possible) Domain member: Digitally sign secure channel data (when possible)
  
  **Default**: Yes
  
- **Authentication level**  
  This security setting determines which challenge/response authentication protocol is used for network logons. This choice affects the level of authentication protocol used by clients, the level of session security negotiated, and the level of authentication accepted by servers as follows:  
  - *Send LM and NTLM responses*: Clients use LM and NTLM authentication and never use NTLMv2 session security; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send LM and NTLM - NTLMv2 if negotiated*: Clients use LM and NTLM authentication and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLM response only*: Clients use NTLM authentication only and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLMv2 response only*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLMv2 response only. Refuse LM*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers refuse LM (accept only NTLM and NTLMv2 authentication). 
  - *Send NTLMv2 response only. Refuse LM and NTLM*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers refuse LM and NTLM (accept only NTLMv2 authentication). 
    
  **Default**: Send NTLMv2 response only. Refuse LM and NTLM
  
- **Prevent clients from sending unencrypted passwords to third party SMB servers**  
  If this security setting is enabled, the Server Message Block (SMB) redirector can send plaintext passwords to non-Microsoft SMB servers that don't support password encryption during authentication. Sending unencrypted passwords is a security risk.
  
  **Default**: Yes
  
- **Disable server digitally signing communications always**  
  This security setting determines whether the SMB client attempts to negotiate SMB packet signing. The server message block (SMB) protocol provides the basis for Microsoft file and print sharing and many other networking operations, such as remote Windows administration. To prevent man-in-the-middle attacks that modify SMB packets in transit, the SMB protocol supports the digital signing of SMB packets. This policy setting determines whether the SMB client component attempts to negotiate SMB packet signing when it connects to an SMB server. If this setting is enabled, the Microsoft network client will ask the server to perform SMB packet signing upon session setup. If packet signing has been enabled on the server, packet signing is negotiated. If this policy is disabled, the SMB client will never negotiate SMB packet signing.
  
  **Default**: Yes
  
- **Administrator elevation prompt behavior**  
  This policy setting controls the behavior of the elevation prompt for administrators. The options are: 
    - *Elevate without prompting*: Allows privileged accounts to perform an operation that requires elevation without requiring consent or credentials. Note: Use this option only in the most constrained environments. 
    - *Prompt for credentials on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to enter a privileged user name and password. If the user enters valid credentials, the operation continues with the user's highest available privilege. 
    - *Prompt for consent on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege. 
    - *Prompt for credentials*: When an operation requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
    - *Prompt for consent*: When an operation requires elevation of privilege, the user is prompted to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege.  
    - *Prompt for consent for non-Windows binaries*: When an operation for a non-Microsoft application requires elevation of privilege, the user is prompted on the secure desktop to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege.   
  
  **Default**: Prompt for consent on the secure desktop
  
- **Minimum session security for NTLM SSP based clients**  
  This security setting allows a client to require the negotiation of 128-bit encryption and/or NTLMv2 session security. These values are dependent on the LAN Manager Authentication Level security setting value. The options are:
  - Require NTLMv2 session security: The connection will fail if NTLMv2 protocol isn't negotiated. 
  - *Require 128-bit encryption*: The connection will fail if strong encryption (128-bit) isn't negotiated.
  - *Require NTLMv2 and 128-bit encryption*. 

  **Default**: Require NTLM V2 128 encryption
  
- **Smart card removal behavior**  
    This security setting determines what happens when the smart card for a logged-on user is removed from the smart card reader. The options are:
     - *No action*. 
     - *Lock Workstation* - The workstation is locked when the smart card is removed, allowing users to leave the area, take their smart card with them, and still maintain a protected session.
     - *Force Logoff* - the user is automatically logged off when the smart card is removed.
     - *Disconnect Remote Desktop session* - Removal of the smart card disconnects the session without logging the user off. This allows the user to insert the smart card and resume the session later, or at another smart card reader-equipped computer, without having to log on again. If the session is local, this policy functions identically to Lock Workstation.   
    
  **Default**: Lock workstation
  
- **Block anonymous enumeration of SAM accounts and shares**  
  This security setting determines whether to allow anonymous enumeration of SAM accounts and shares. Windows allows anonymous users to perform certain activities, such as enumerating the names of domain accounts and network shares. This is convenient, for example, when an administrator wants to grant access to users in a trusted domain that doesn't maintain a reciprocal trust. If you don't want to allow anonymous enumeration of SAM accounts and shares, then set this policy to *Yes*.
  
  **Default**: Yes
  
- **Block remote logon with blank password**  
  This security setting determines whether local accounts that aren't password protected can be used to log on from locations other than the physical computer console. If enabled, local accounts that aren't password protected must use the computer's keyboard to log on. 

  *Warning*: Computers that aren't in physically secure locations should always enforce strong password policies for all local user accounts. Otherwise, anyone with physical access to the computer can log on by using a user account that doesn't have a password. This is especially important for portable computers. 

  If you apply this security policy to the Everyone group, no one can log on through Remote Desktop Services. This setting doesn't affect logons that use domain accounts. It's possible for applications that use remote interactive logons to bypass this setting.
  
  **Default**: Yes
  
- **Standard user elevation prompt behavior**  
  This policy setting controls the behavior of the elevation prompt for standard users. 
  - *Automatically deny elevation requests*: When an operation requires elevation of privilege, a configurable access denied error message is displayed. An enterprise that is running desktops as standard user may choose this setting to reduce help desk calls. 
  - *Prompt for credentials on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to enter a different user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
  - *Prompt for credentials*: When an operation requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege.  
  
  **Default**: Automatically deny elevation requests
  
- **Require admin approval mode for administrators**  
  This policy setting controls the behavior of all User Account Control (UAC) policy settings for the computer. If you change this policy setting, you must restart your computer. The options are:   
  - *Not configured*: Admin Approval Mode and all related UAC policy settings are disabled. Note: If this policy setting is disabled, the Security Center notifies you that the overall security of the operating system has been reduced. 
  - *Yes*: Admin Approval Mode is enabled. This policy must be enabled and related UAC policy settings must be set appropriately to allow the built-in Administrator account and all other users who are members of the Administrators group to run in Admin Approval Mode.  
  
  **Default**: Yes
  
- **Prevent anonymous enumeration of SAM accounts**  
  This security setting determines what additional permissions are granted for anonymous connections to the computer. Windows allows anonymous users to perform certain activities, such as enumerating the names of domain accounts and network shares. This is convenient, for example, when an administrator wants to grant access to users in a trusted domain that doesn't maintain a reciprocal trust. This security option allows additional restrictions to be placed on anonymous connections as follows: 
  - *Yes*: Don't allow enumeration of SAM accounts. This option replaces Everyone with Authenticated Users in the security permissions for resources.
  - *Not configured*: No additional restrictions. Rely on default permissions.  
  
  **Default**: Yes
  
- **Allow remote calls to security accounts manager**  
  This policy setting allows you to restrict remote rpc connections to SAM. If not selected, the default security descriptor is used.
  
  **Default**: *O:BAG:BAD:(A;;RC;;;BA)*

- **Use admin approval mode**  
  This policy setting controls the behavior of Admin Approval Mode for the built-in Administrator account. The options are: 
  - *Yes*: The built-in Administrator account uses Admin Approval Mode. By default, any operation that requires elevation of privilege will prompt the user to approve the operation. 
  - *Not Configured*: The built-in Administrator account runs all applications with full administrative privilege.  

  **Default**: Yes
  
- **Allow UI access applications for secure locations**  
  This policy setting controls whether User Interface Accessibility (UIAccess or UIA) programs can automatically disable the secure desktop for elevation prompts used by a standard user. 
  - *Yes*: UIA programs, including Windows Remote Assistance, automatically disable the secure desktop for elevation prompts. If you don't disable the "User Account Control: Switch to the secure desktop when prompting for elevation" policy setting, the prompts appear on the interactive user's desktop instead of the secure desktop. 
  - *Not Configured*: The secure desktop can be disabled only by the user of the interactive desktop or by disabling the "User Account Control: Switch to the secure desktop when prompting for elevation" policy setting.  

  **Default**: Yes

- **Detect application installations and prompt for elevation**  
  This policy setting controls the behavior of application installation detection for the computer. The options are: 
  - *Enabled*: When an application installation package is detected that requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
  - *Disabled*: Application installation packages aren't detected and prompted for elevation. Enterprises that are running standard user desktops and use delegated installation technologies such as Group Policy Software Installation or Systems Management Server (SMS) should disable this policy setting. In this case, installer detection is unnecessary.  
  
  **Default**: Yes
  
- **Prevent storing LAN manager hash value on next password change**  
  This security setting determines if, at the next password change, the LAN Manager (LM) hash value for the new password is stored. The LM hash is relatively weak and prone to attack, as compared with the cryptographically stronger Windows NT hash. Since the LM hash is stored on the local computer in the security database the passwords can be compromised if the security database is attacked.
  
  **Default**: Yes

- **Virtualize file and registry write failures to per user locations**  
  This policy setting controls whether application write failures are redirected to defined registry and file system locations. This policy setting mitigates applications that run as administrator and write run-time application data to *%ProgramFiles%*, *%Windir%*, *%Windir%\system32*, or *HKLM\Software*.
  
  **Default**: Yes

## MS Security Guide  
For more information, see [Policy CSP - MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) in the Windows documentation.  

- **Apply UAC restrictions to local accounts on network logon**  
  **Default**: Enabled
  
- **SMB v1 client driver start configuration**  
  **Default**: Disabled driver
  
- **SMB v1 server**  
  **Default**: Disabled
  
- **Digest authentication**  
  **Default**: Disabled
  
- **Structured exception handling overwrite protection**  
  **Default**: Enabled
  
## MSS Legacy  
For more information, see [Policy CSP - MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) in the Windows documentation.  

- **Network IP source routing protection level**  
  **Default**: Highest protection  
  
- **Network ignore NetBIOS name release requests except from WINS servers**  
  **Default**: Enabled
  
- **Network IPv6 source routing protection level**  
  **Default**: Highest protection

- **Network ICMP redirects override OSPF generated**  
  **Default**: Disabled
  
## Power  
For more information, see [Policy CSP - Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) in the Windows documentation.  

- **Require password on wake while plugged in**  
  This policy setting specifies if the user is prompted for a password when the system resumes from sleep. If you enable or don't configure this policy setting, the user is prompted for a password when the system resumes from sleep. If you disable this policy setting, the user isn't prompted for a password when the system resumes from sleep.
  
  **Default**: Enabled
  
- **Standby states when sleeping while on battery**  
  This policy setting manages if Windows can use standby states when putting the computer in a sleep state. If you enable or don't configure this policy setting, Windows uses standby states to put the computer in a sleep state. If you disable this policy setting, standby states (S1-S3) aren't allowed.
  
  **Default**: Disabled
  
- **Standby states when sleeping while plugged in**  
  This policy setting manages if Windows can use standby states when putting the computer in a sleep state. If you enable or don't configure this policy setting, Windows uses standby states to put the computer in a sleep state. If you disable this policy setting, standby states (S1-S3) aren't allowed.
  
  **Default**: Disabled
  
- **Require password on wake while on battery**  
  This policy setting specifies if the user is prompted for a password when the system resumes from sleep. If you enable or don't configure this policy setting, the user is prompted for a password when the system resumes from sleep. If you disable this policy setting, the user isn't prompted for a password when the system resumes from sleep.
  
  **Default**: Enabled
  
## Remote Desktop Services  
For more information, see [Policy CSP - RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) in the Windows documentation.  

- **Block password saving**  
  Controls whether passwords can be saved on this computer from Remote Desktop Connection. If you enable this setting the password saving checkbox in Remote Desktop Connection is disabled and users won't be able to save passwords. When a user opens an RDP file using Remote Desktop Connection and saves their settings, any password that previously existed in the RDP file are deleted. If you disable this setting or leave it not configured, the user can save passwords using Remote Desktop Connection.
  
   **Default**: Enabled
  
- **Secure RPC communication**  
  Specifies whether a Remote Desktop Session Host server requires secure RPC communication with all clients or allows unsecured communication. You can use this setting to strengthen the security of RPC communication with clients by allowing only authenticated and encrypted requests. If the status is set to Enabled, Remote Desktop Services accepts requests from RPC clients that support secure requests, and doesn't allow unsecured communication with untrusted clients. If the status is set to Disabled, Remote Desktop Services always requests security for all RPC traffic. However, unsecured communication is allowed for RPC clients that don't respond to the request. If the status is set to Not Configured, unsecured communication is allowed. Note: The RPC interface is used for administering and configuring Remote Desktop Services.
  
  **Default**: Enabled
  
- **Block drive redirection**  
  This policy setting specifies whether to prevent the mapping of client drives in a Remote Desktop Services session (drive redirection). By default, an RD Session Host server maps client drives automatically upon connection. Mapped drives appear in the session folder tree in File Explorer or Computer in the format *\<driveletter>* on *\<computername>*. You can use this policy setting to override this behavior. If you enable this policy setting, client drive redirection isn't allowed in Remote Desktop Services sessions, and Clipboard file copy redirection isn't allowed on computers running Windows Server 2003, Windows 8, and Windows XP. If you disable this policy setting, client drive redirection is always allowed. Also, Clipboard file copy redirection is always allowed if Clipboard redirection is allowed. If you don't configure this policy setting, client drive redirection and Clipboard file copy redirection aren't specified at the Group Policy level.
  
  **Default**: Enabled
  
- **Prompt for password upon connection**  
  This policy setting specifies whether Remote Desktop Services always prompts the client for a password upon connection. You can use this setting to enforce a password prompt for users logging on to Remote Desktop Services, even if they already provided the password in the Remote Desktop Connection client. By default, Remote Desktop Services allows users to automatically log on by entering a password in the Remote Desktop Connection client. If you enable this policy setting, users can't automatically log on to Remote Desktop Services by supplying their passwords in the Remote Desktop Connection client. they're prompted for a password to log on. If you disable this policy setting, users can always log on to Remote Desktop Services automatically by supplying their passwords in the Remote Desktop Connection client. If you don't configure this policy setting, automatic logon isn't specified at the Group Policy level. 
  
  **Default**: Enabled
  
- **Remote desktop services client connection encryption level**  
  Specifies whether to require the use of a specific encryption level to secure communications between client computers and RD Session Host servers during Remote Desktop Protocol (RDP) connections. This policy only applies when you're using native RDP encryption. However, native RDP encryption (as opposed to SSL encryption) isn't recommended. This policy doesn't apply to SSL encryption. If you enable this policy setting, all communications between clients and RD Session Host servers during remote connections must use the encryption method specified in this setting. By default, the encryption level is set to High. The following encryption methods are available:  
  - *High*: The High setting encrypts data sent from the client to the server and from the server to the client by using strong 128-bit encryption. Use this encryption level in environments that contain only 128-bit clients (for example, clients that run Remote Desktop Connection). Clients that don't support this encryption level can't connect to RD Session Host servers.  
  - *Client Compatible*: The Client Compatible setting encrypts data sent between the client and the server at the maximum key strength supported by the client. Use this encryption level in environments that include clients that don't support 128-bit encryption.  
  - *Low*: The Low setting encrypts only data sent from the client to the server by using 56-bit encryption.  
  
  If you disable or don't configure this setting, the encryption level to be used for remote connections to RD Session Host servers isn't enforced through Group Policy. Important FIPS compliance can be configured through the System cryptography. Use FIPS-compliant algorithms for encryption, hashing, and signing settings in Group Policy (under Computer Configuration\Windows Settings\Security Settings\Local Policies\Security Options.) The FIPS-compliant setting encrypts and decrypts data sent from the client to the server and from the server to the client, with the Federal Information Processing Standard (FIPS) 140 encryption algorithms, by using Microsoft cryptographic modules. Use this encryption level when communications between clients and RD Session Host servers requires the highest level of encryption.
  
  **Default**: High
  
## Remote Management  
For more information, see [Policy CSP - RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) in the Windows documentation.  

- **Block storing run as credentials**  
  Client basic authentication
  
  **Default**: Enabled
  
- **Basic authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) service accepts Basic authentication from a remote client. If you enable this policy setting, the WinRM service accepts Basic authentication from a remote client. If you disable or don't configure this policy setting, the WinRM service doesn't accept Basic authentication from a remote client.
  
  **Default**: Disabled
  
- **Block client digest authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client uses Digest authentication. If you enable this policy setting, the WinRM client doesn't use Digest authentication. If you disable or don't configure this policy setting, the WinRM client uses Digest authentication.
  
  **Default**: Enabled
  
- **Unencrypted traffic**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) service sends and receives unencrypted messages over the network. If you enable this policy setting, the WinRM client sends and receives unencrypted messages over the network. If you disable or don't configure this policy setting, the WinRM client sends or receives only encrypted messages over the network.  
  
  **Default**: Disabled
  
- **Client unencrypted traffic**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client sends and receives unencrypted messages over the network. If you enable this policy setting, the WinRM client sends and receives unencrypted messages over the network. If you disable or don't configure this policy setting, the WinRM client sends or receives only encrypted messages over the network.
  
  **Default**: Disabled
  
- **Client basic authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client uses Basic authentication. If you enable this policy setting, the WinRM client uses Basic authentication. If WinRM is configured to use HTTP transport, the user name and password are sent over the network as clear text. If you disable or don't configure this policy setting, the WinRM client doesn't use Basic authentication.
  
  **Default**: Disabled
  

## Remote Procedure Call  
For more information, see [Policy CSP - RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) in the Windows documentation.  

- **RPC unauthenticated client options**  
  This policy setting controls how the RPC server runtime handles unauthenticated RPC clients connecting to RPC servers. This policy setting impacts all RPC applications. In a domain environment, use this policy setting with caution as it can impact a wide range of functionality including group policy processing itself. Reverting a change to this policy setting can require manual intervention on each affected machine. This policy setting should never be applied to a domain controller. If you disable this policy setting, the RPC server runtime uses the value of "Authenticated" on Windows Client, and the value of "None" on Windows Server versions that support this policy setting. If you don't configure this policy setting, it remains disabled. The RPC server runtime behaves as though it was enabled with the value of "Authenticated" used for Windows Client and the value of "None" used for Server SKUs that support this policy setting. If you enable this policy setting, it directs the RPC server runtime to restrict unauthenticated RPC clients connecting to RPC servers running on a machine. A client is considered an authenticated client if it uses a named pipe to communicate with the server or if it uses RPC Security. RPC Interfaces that have specifically requested to be accessible by unauthenticated clients may be exempt from this restriction, depending on the selected value for this policy setting.  
  - *None* allows all RPC clients to connect to RPC Servers running on the machine on which the policy setting is applied. 
  - *Authenticated* allows only authenticated RPC Clients (per the definition above) to connect to RPC Servers running on the machine on which the policy setting is applied. Exemptions are granted to interfaces that have requested them. 
  - *Authenticated without exceptions* allows only authenticated RPC Clients (per the definition above) to connect to RPC Servers running on the machine on which the policy setting is applied. No exceptions are allowed. Note: This policy setting won't be applied until the system is rebooted.  

  **Default**: Authenticated

## Search 
For more information, see [Policy CSP - Search](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) in the Windows documentation.  

- **Disable indexing encrypted items**  
  Allows or disallows the indexing of items. This switch is for the Windows Search Indexer, which controls whether it will index items that are encrypted, such as the Windows Information Protection (WIP) protected files. When the policy is enabled, WIP protected items are indexed and the metadata about them are stored in an unencrypted location. The metadata includes things like file path and date modified. When the policy is disabled, the WIP protected items aren't indexed and don't show up in the results in Cortana or file explorer. There may also be a performance impact on photos and Groove apps if there are many WIP protected media files on the device.
  
**Default**: Yes
  
## Smart Screen  
For more information, see [Policy CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) in the Windows documentation.  

- **Block execution of unverified files**  
  Block user from running unverified files. 
  - *Not Configured* - Employees can ignore SmartScreen warnings and run malicious files. 
  - *Yes* – Employees can't ignore SmartScreen warnings and run malicious files.

  **Default**: Yes

- **Require SmartScreen for apps and files**  
  Allows IT Admins to configure SmartScreen for Windows.

  **Default**: Yes
  
## System  
For more information, see [Policy CSP - System](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) in the Windows documentation.  

- **System boot start driver initialization**  
  This policy setting allows you to specify which boot-start drivers are initialized based on a classification determined by an Early Launch Antimalware boot-start driver. The Early Launch Antimalware boot-start driver can return the following classifications for each boot-start driver: 
  - *Good*: The driver has been signed and hasn't been tampered with.  
  - *Bad* - The driver has been identified as malware. We recommend that you don't allow known bad drivers to be initialized. 
  - *Bad, but required for boot*: The driver has been identified as malware, but the computer can't successfully boot without loading this driver. 
  - *Unknown* - This driver hasn't been attested to by your malware detection application and hasn't been classified by the Early Launch Antimalware boot-start driver.  

  If you enable this policy setting, you can choose which boot-start drivers to initialize the next time the computer is started. If you disable or don't configure this policy setting, the boot start drivers determined to be Good, Unknown, or Bad but Boot Critical are initialized and the initialization of drivers determined to be Bad is skipped. If your malware detection application doesn't include an Early Launch Antimalware boot-start driver or if your Early Launch Antimalware boot-start driver has been disabled, this setting has no effect and all boot-start drivers are initialized.  
  
  **Default**: Good unknown and bad critical


## Wi-Fi  
For more information, see [Policy CSP - Wifi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) in the Windows documentation.  

- **Block Internet sharing**  
  Specifies whether internet sharing is possible on the device.  

  **Default**: Yes  

- **Block Automatically connecting to Wi-Fi hotspots**  
  Allow or disallow the device to automatically connect to Wi-Fi hotspots.  

  **Default**: Yes  
  
## Windows Connection Manager  
For more information, see [Policy CSP - WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) in the Windows documentation.  

- **Block connection to non-domain networks**  
  This policy setting prevents computers from connecting to both a domain-based network and a non-domain based network at the same time. If this policy setting is enabled, the computer responds to automatic and manual network connection attempts based on the following circumstances: 
  - Automatic connection attempts When the computer is already connected to a domain-based network, all automatic connection attempts to non-domain networks are blocked. When the computer is already connected to a non-domain based network, automatic connection attempts to domain-based networks are blocked. 
  - Manual connection attempts When the computer is already connected to either a non-domain based network or a domain-based network over media other than Ethernet, and a user attempts to create a manual connection to an additional network in violation of this policy setting, the existing network connection disconnects and the manual connection is allowed. When the computer is already connected to either a non-domain based network or a domain-based network over Ethernet, and a user attempts to create a manual connection to an additional network in violation of this policy setting, the existing Ethernet connection is maintained and the manual connection attempt is blocked.  

  If this policy setting isn't configured or is disabled, computers are allowed to connect simultaneously to both domain and non-domain networks.  

  **Default**: Enabled
  
## Windows Defender  
For more information, see [Policy CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) in the Windows documentation.  

- **Scan incoming mail messages**  
  Allows or disallows scanning of email.
  
  **Default**: Yes  

- **Office apps launch child process type**  
  Office apps won't be allowed to create child processes. This includes Word, Excel, PowerPoint, OneNote, and Access. This is a typical malware behavior, especially for macro-based attacks that attempt to use Office apps to launch or download malicious executables.
  
  **Default**: Block
  
- **Defender sample submission consent type**  
  Checks for the user consent level in Windows Defender to send data. If the required consent has already been granted, Windows Defender submits them. If not, (and if the user has specified never to ask), the UI is launched to ask for user consent (when Defender/AllowCloudProtection is allowed) before sending data.
  
  **Default**: Send safe samples automatically 
  
- **Signature update interval (in hours)**  
  Defender signature update interval in hours
  
  **Default**: 4
  
- **Script downloaded payload execution type**  
  Defender script downloaded payload execution type
  
  **Default**: Block
  
- **Prevent credential stealing type**  
  Windows Defender Credential Guard uses virtualization-based security to isolate secrets so that only privileged system software can access them. Unauthorized access to these secrets can lead to credential theft attacks, such as Pass-the-Hash or Pass-The-Ticket. Windows Defender Credential Guard prevents these attacks by protecting NTLM password hashes, Kerberos Ticket Granting Tickets, and credentials stored by applications as domain credentials.
  
  **Default**: Enable

- **Email content execution type**  
  This rule blocks the following file types from being run or launched from an email seen in either Microsoft Outlook or webmail (such as Gmail.com or Outlook.com): Executable files (such as .exe, .dll, or .scr) Script files (such as a PowerShell .ps, VisualBasic .vbs, or JavaScript .js file) Script archive files.
  
  **Default**: Block
  
- **Network protection type**  
  This policy allows you to turn on network protection (block/audit) or off in Windows Defender Exploit Guard. Network protection is a feature of Windows Defender Exploit Guard that protects employees using any app from accessing phishing scams, exploit-hosting sites, and malicious content on the Internet. This includes preventing third-party browsers from connecting to dangerous sites. Value type is integer. If you enable this setting, network protection is turned on and employees can't turn it off. Its behavior can be controlled by the following options: Block and Audit. If you enable this policy with the "Block" option, users and apps are blocked from connecting to dangerous domains. You can see this activity in Windows Defender Security Center. If you enable this policy with the "Audit" option, users/apps won't be blocked from connecting to dangerous domains. However, you'll still see this activity in Windows Defender Security Center. If you disable this policy, users/apps won't be blocked from connecting to dangerous domains. You'll not see any network activity in Windows Defender Security Center. If you don't configure this policy, network blocking is disabled by default.
  
  **Default**: Enable
  
- **Defender schedule scan day**  
  Defender schedule scan day.
  
  **Default**: Everyday
  
- **Cloud-delivered protection**  
  To best protect your PC, Windows Defender will send information to Microsoft about any problems it finds. Microsoft will analyze that information, learn more about problems affecting you and other customers, and offer improved solutions.
  
  **Default**:  Yes  

- **Defender potentially unwanted app action**  
  The potentially unwanted application (PUA) protection feature in Windows Defender Antivirus can identify and block PUAs from downloading and installing on endpoints in your network. These applications aren't considered viruses, malware, or other types of threats, but might perform actions on endpoints that adversely affect their performance or use. PUA can also refer to applications that are considered to have a poor reputation. Typical PUA behavior includes: Various types of software bundling Ad injection into web browsers Driver and registry optimizers that detect issues, request payment to fix the errors, but remain on the endpoint and make no changes or optimizations (also known as "rogue antivirus" programs). These applications can increase the risk of your network being infected with malware, cause malware infections to be harder to identify, and can waste IT resources in cleaning up the applications.  
  
  **Default**: Block  

- **Script obfuscated macro code type**  
  Malware and other threats can attempt to obfuscate or hide their malicious code in some script files. This rule prevents scripts that appear to be obfuscated from running.
  
  **Default**: Block
  
- **Scan removable drives during a full scan**  
  Allows Windows Defender to scan for malicious and unwanted software in removable drives (for example, flash drives) during a full scan. Windows Defender Antivirus scans all files on USB devices before execution.
  
  **Default**: Yes  
  
- **Scan archive files**  
  Defender scan archive files.
  
  **Default**: Yes
  
- **Behavior monitoring**  
  Allows or disallows Windows Defender Behavior Monitoring functionality.Embedded in Windows 10, these sensors collect and process behavioral signals from the operating system and sends this sensor data to your private, isolated, cloud instance of Microsoft Defender ATP.
  
  **Default**: Yes

- **Scan files opened from network folders**  
  If files are read-only, user won't be able to remove any detected malware.
  
  **Default**: Yes

- **Untrusted USB process type**  
  With this rule, admins can prevent unsigned or untrusted executable files from running from USB removable drives, including SD cards.
  
  **Default**: Block
  
- **Office apps other process injection type**  
  Office apps, including Word, Excel, PowerPoint, and OneNote, won't be able to inject code into other processes. This is typically used by malware to run malicious code in an attempt to hide the activity from antivirus scanning engines.
  
  **Default**:  Block
  
- **Office macro code allow Win32 imports type**  
  Malware can use macro code in Office files to import and load Win32 DLLs, which can then be used to make API calls to allow further infection throughout the system. This rule attempts to block Office files that contain macro code that is capable of importing Win32 DLLs. This includes Word, Excel, PowerPoint, and OneNote.
  
  **Default**: Block  
  
- **Defender cloud block level**  
  Defender cloud block level.
  
  **Default**: Not Configured

- **Real-time monitoring**  
  Defender requires real-time monitoring.
  
  **Default**: Yes
  
- **Office apps executable content creation or launch type**  
  This rule targets typical behaviors used by suspicious and malicious add-ons and scripts (extensions) that create or launch executable files. This is a typical malware technique. Extensions are blocked from being used by Office apps. Typically these extensions use the Windows Scripting Host (.wsh files) to run scripts that automate certain tasks or provide user-created add-on features
  
  **Default**: Block

## Windows Ink Workspace  
For more information, see [Policy CSP - WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) in the Windows documentation.  

- **Ink Workspace**  
  Specifies whether to allow the user to access the ink workspace. 
  - *Disabled* - access to ink workspace is disabled. The feature is turned off.
  - *Enabled* - The Ink Workspace feature is turned on, but the user can't access it above the lock screen.
  - *Not Configured* - The Ink Workspace feature is turned on, and the user can use it above the lock screen.  

  **Default**: Enabled
 
## Windows PowerShell  
For more information, see [Policy CSP - WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) in the Windows documentation.  

- **Power shell shell script block logging**  
  This policy setting enables logging of all PowerShell script input to the Microsoft-Windows-PowerShell/Operational event log. If you enable this policy setting, Windows PowerShell will log the processing of commands, script blocks, functions, and scripts - whether invoked interactively, or through automation. If you disable this policy setting, logging of PowerShell script input is disabled. If you enable the Script Block Invocation Logging, PowerShell additionally logs events when invocation of a command, script block, function, or script starts or stops. Enabling Invocation Logging generates a high volume of event logs. Note: This policy setting exists under both Computer Configuration and User Configuration in the Group Policy Editor. The Computer Configuration policy setting takes precedence over the User Configuration policy setting.
  
  **Default**: Enabled
 

End of PReview baseilne list  -->

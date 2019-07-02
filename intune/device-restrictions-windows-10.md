---
title: Eszközkorlátozási beállítások Windows 10 rendszerhez az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Megjelenítheti az összes beállítás és a hozzájuk tartozó leírások létrehozásához eszközkorlátozások Windows 10 és újabb rendszerű eszközök listáját. A konfigurációs profil ezek a beállítások segítségével szabályozhatja a képernyőképeket, jelszókövetelmények, a kioszkmód, a tárolóban, a Microsoft Edge böngésző, a Windows defender-alkalmazások, a felhőbe, a start menüben, és több Microsoft Intune-ban.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: fe155c5b2a18b1931894b05694b53bbc2c497e0b
ms.sourcegitcommit: 116ef72b9da4d114782d4b8dd9f57556c9b01511
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/01/2019
ms.locfileid: "67494479"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>A Windows 10 (és újabb) eszközbeállítások engedélyezett vagy korlátozott funkciók az Intune-nal

Ez a cikk és ismerteti a különböző beállításokkal szabályozhatja a Windows 10-es és újabb eszközökön. A mobileszköz-felügyelet (MDM) megoldás részeként használatával ezek a beállítások lehetővé teszik vagy szolgáltatásokat tilthat le, jelszószabályok beállítása, a zárolási képernyő testreszabása, használja a Windows Defender és a további.

Ezek a beállítások hozzá egy eszközkonfigurációs profilt az Intune-ban, és ezután hozzárendelt vagy a Windows 10-es eszközökre telepített.

> [!Note]
> Nem minden beállítás a Windows összes verzióján érhetők el. A támogatott kiadások megtekintéséhez tekintse meg a [házirend CSP-k](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (megnyílik egy másik Microsoft-webhely).

## <a name="before-you-begin"></a>Előkészületek

[Eszközkonfigurációs profil létrehozása](device-restrictions-configure.md#create-the-profile).

## <a name="app-store"></a>Alkalmazásáruház

Ezeket a beállításokat használja a [ApplicationManagement házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement), amely felsorolja a támogatott Windows-kiadások.

- **Alkalmazás-áruház** (csak mobil): **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a végfelhasználók az app Store-ban a mobileszközök a hozzáférést. **Blokk** megakadályozza, hogy az alkalmazás-áruház használatával.
- **Áruházból származó alkalmazások automatikus frissítése**: **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a Microsoft Store automatikusan frissíteni kell a telepített alkalmazások. **Blokk** megakadályozza, hogy a frissítések automatikus telepítése folyamatban.
- **Megbízható alkalmazás telepítése**: Válassza ki, ha a Microsoft Store lehet alkalmazásokat telepíteni, más néven a közvetlen telepítést. Közvetlen telepítési telepíti, és ezután fut vagy nem minősített által a Microsoft Store-alkalmazás tesztelése. Ha például egy alkalmazást, amely csak a vállalati belső. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Az operációs rendszer alapértelmezett használja.
  - **Blokk**: Megakadályozza, hogy a közvetlen telepítést. Nem – Microsoft Store-alkalmazások nem telepíthetők.
  - **Lehetővé teszi**: Lehetővé teszi a közvetlen telepítést. Nem – Microsoft Store-alkalmazások telepíthetők.
- **Fejlesztői zárolás feloldása**: Lehetővé teszi a Windows fejlesztői beállításait, például lehetővé teszi a közvetlenül telepített alkalmazások a végfelhasználók által módosítható. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Az operációs rendszer alapértelmezett használja.
  - **Blokk**: Megakadályozza, hogy a fejlesztői mód és a közvetlen telepítési alkalmazások.
  - **Lehetővé teszi**: Lehetővé teszi a fejlesztői mód és a közvetlen telepítési alkalmazások.

  [Engedélyezi az eszköz fejlesztési](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development) funkció további részleteket tartalmaz.

- **Megosztott felhasználói alkalmazásadatok**: Válasszon **engedélyezése** alkalmazásadatok ugyanazon az eszközön, és a többi példánya, amelyet az alkalmazás különböző felhasználók között megosztani. **Nincs konfigurálva** (alapértelmezett) megakadályozza, hogy a megosztás adatok más felhasználók és a többi példánya ugyanazt az alkalmazást.
- **Csak privát áruház használata**: **Lehetővé teszi** csak lehetővé teszi az alkalmazások privát áruházból letöltött, majd a nyilvános áruházból, például egy kiskereskedelmi katalógus nem tölti le. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy le egy privát áruház és a egy nyilvános áruházbeli alkalmazások.
- **Store származó alkalmazások indítása**: **Blokk** letiltja az összes alkalmazás, amely előre telepítve az eszközön, vagy a Microsoft Store-től letöltött. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ezek az alkalmazások megnyitásához.
- **Alkalmazásadatok telepítése a rendszerköteten**: **Blokk** leállítja az alkalmazások adatokat tároljanak az eszköz a rendszerköteten. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy az adatok tárolásához a lemezen rendszerköteten alkalmazásokat.
- **Alkalmazások telepítése a rendszermeghajtón**: **Blokk** letiltja az alkalmazások telepítése a rendszermeghajtón az eszközön. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy az alkalmazások telepítése a rendszermeghajtón.
- **Játékvideó-rögzítő** (csak asztali verzió): **Blokk** letiltja a Windows-játék rögzítése és közvetítése. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy rögzítése és közvetítése játékokat.
- **Csak áruházból származó alkalmazások**: Ez a beállítás határozza meg a felhasználói élmény, amikor a felhasználók telepítik az alkalmazásokat a Microsoft Store intézményeknek portálon kívülről származó. A választható lehetőségek:

  - **Nincs konfigurálva** (alapértelmezett): Lehetővé teszi a végfelhasználók számára, hogy a Microsoft Store, beleértve a más házirend-beállítások meghatározott alkalmazások intézményeknek portálon kívülről származó alkalmazások telepítése.  
  - **Bárhol**: Alkalmazás javaslatok kikapcsolja, és lehetővé teszi a felhasználók bárhonnan, az alkalmazások telepítéséhez.  
  - **Csak Store**: Csak telepíteni alkalmazásokat a Microsoft Store kényszeríti a végfelhasználók számára.
  - **Javaslatok**: Ha egy alkalmazás telepítése, amely elérhető a Microsoft Store webes, felhasználók javasolja, hogy töltse le a tároló üzenet jelenik meg.  
  - **Igény szerint Store**: A Microsoft Store intézményeknek portálon kívülről származó alkalmazások telepítésekor figyelmezteti a felhasználókat.

  [SmartScreen/EnableAppInstallControl CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen#smartscreen-enableappinstallcontrol)

- **Kényszerített újraindítás alkalmazások frissítési hiba esetén**: Amikor egy alkalmazás használatban van, akkor nem frissíthetők. Ez a beállítás segítségével kényszerítheti az alkalmazás újraindítása. **Nincs konfigurálva** (alapértelmezett) nem kényszerített újraindítása az alkalmazásokat. **Szükséges** lehetővé teszi a rendszergazdák indítja újra egy adott dátumot és időpontot, vagy ismétlődő ütemezés szerint. Ha a beállítása **megkövetelése**, is megadhatja:

  - **Indítsa el a dátum/idő**: Válasszon egy adott dátumot és időpontot, az alkalmazások újraindításához.
  - **Ismétlődési**: Napi, heti vagy havi.

  [ApplicationManagement/ScheduleForceRestartForUpdateFailures CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-scheduleforcerestartforupdatefailures)

- **Felhasználói vezérlése telepítések**: Ha a beállítása **nincs konfigurálva** (alapértelmezett), Windows Installer megakadályozhatja a felhasználókat a könyvtárban, a fájlok telepítéséhez írja be például a rendszergazdák általában fenntartott telepítési beállítások módosítása. **Blokk** lehetővé teszi a felhasználóknak, hogy ezen telepítési lehetőségekről, és a Windows Installer biztonsági funkcióit is telepítővarázslója kihagyja.

  [ApplicationManagement/MSIAllowUserControlOverInstall CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msiallowusercontroloverinstall)

- **Alkalmazások telepítéséhez emelt szintű jogosultságokkal**: Ha a beállítása **nincs konfigurálva** (alapértelmezett), a rendszer az aktuális felhasználó engedélyek alkalmazása a rendszergazdák nem üzembe helyezése vagy ajánlat programok telepítésekor. **Blokk** arra utasítja a Windows Installer emelt jogosultsági szintű használata, amikor telepíti a rendszer minden program. A programok ki vannak bővítve ezeket a jogosultságokat.

  [ApplicationManagement/MSIAlwaysInstallWithElevatedPrivileges CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msialwaysinstallwithelevatedprivileges)

- **Indítási alkalmazások**: Adja meg azokat az alkalmazásokat, miután egy felhasználó bejelentkezik az eszköz megnyitásához. Győződjön meg arról, pontosvesszővel tagolt listája, csomag Csomagcsalád nevének (pfn) Megkeresése Windows-alkalmazások használatához. A házirend működjön a jegyzékfájlt a Windows-alkalmazások egy indítási feladat kell használnia.

  [ApplicationManagement/LaunchAppAfterLogOn CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-launchappafterlogon)

Válassza ki **OK** a módosítások mentéséhez.

## <a name="cellular-and-connectivity"></a>Mobilhálózati és egyéb kapcsolatok

Ezeket a beállításokat használja a [csatlakozási házirend](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) és [Wi-Fi házirend](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) CSP-k, amely szintén a Windows támogatott kiadásainak listázása.

- [Wi-Fi házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi)

- **Mobilhálózati adatcsatorna**: Válassza ki, ha a végfelhasználók használhatnak-e adatokat, például a webböngészést, amikor csatlakozik a mobilhálózati. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Az operációs rendszer alapértelmezett, így a mobilhálózati adatcsatorna használja. A végfelhasználók kikapcsolhatja azt.
  - **Blokk**: A mobilhálózati adatcsatorna nem teszik lehetővé. A végfelhasználók nem kapcsolja be.
  - **Engedélyezése (nem szerkeszthető)** : Lehetővé teszi a mobil-adatcsatorna. A végfelhasználók nem kapcsolhatja ki.

- **Adatroaming**: **Blokk** megakadályozza, hogy a mobilhálózati adatroaming használatát az eszközön. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi az adatok elérése közben hálózatok közötti barangolás.
- **Mobilhálózati VPN**: **Blokk** megakadályozza, hogy az eszköz nem férhet hozzá a VPN-kapcsolatot mobilhálózat használata esetén. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a VPN bármilyen kapcsolatot, beleértve a mobilkapcsolatot is használhat.
- **A mobilhálózati barangolás VPN**: **Blokk** leállítja az eszköz nem férhet hozzá a VPN-kapcsolat mobilhálózati roaming esetén. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy VPN-kapcsolatok engedélyezése barangolás közben.
- **Csatlakoztatott eszközök szolgáltatás**: **Blokk** letiltja a csatlakoztatott eszközök Platform (CDP) összetevő. CDP lehetővé teszi, hogy észlelését és egyéb eszközök (a Bluetooth/LAN vagy a felhőben) támogatja a távoli alkalmazásindítási, üzenetküldési távoli, távoli munkamenetek és egyéb eszközök közötti. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a csatlakoztatott eszközök szolgáltatást, amely lehetővé teszi más Bluetooth-eszközök észlelését és.
- **NFC**: **Blokk** megakadályozza, hogy a mező kommunikáció (NFC) képességek mellett. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi a felhasználóknak engedélyezze és konfigurálja az NFC-funkciók az eszközön.
- **Wi-Fi**: **Blokk** megakadályozza, hogy a felhasználók és engedélyezése, konfigurálása és a Wi-Fi-kapcsolatok használatával az eszközön. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a Wi-Fi-kapcsolatok.
- **Automatikus csatlakozás Wi-Fi elérési pontokhoz**: **Blokk** megakadályozza, hogy az eszközök Wi-Fi elérési pontokhoz való automatikus csatlakozás. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy az eszközöket, ingyenes Wi-Fi elérési pontokhoz történő automatikus csatlakozás, és automatikusan elfogadja a és a feltételek a kapcsolathoz.
- **Manuális Wi-Fi konfigurációs**: **Blokk** megakadályozza, hogy a eszközök csatlakozzanak a Wi-Fi MDM server telepítve hálózatokon kívül. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a végfelhasználók számára, hogy hozzáadása és konfigurálása saját Wi-Fi-kapcsolatok hálózati SSID-k.
- **Wi-Fi-ellenőrzési időköz**: Adja meg a milyen gyakran eszközök Wi-Fi-hálózatok keresése. Adja meg az érték 1 (leggyakoribb) 500 (legritkább). Alapértelmezett érték a `0` (nulla).

### <a name="bluetooth"></a>Bluetooth

Ezeket a beállításokat használja a [Bluetooth-házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth); is a Windows támogatott kiadások listája látható.

- **Bluetooth**: **Blokk** megakadályozza, hogy a felhasználók Bluetooth engedélyezése. **Nincs konfigurálva** (alapértelmezett) az eszköz Bluetooth engedélyezése.
- **Bluetooth-észlelhetőség**: **Blokk** megakadályozza, hogy az eszközt más Bluetooth-kompatibilis eszközök által felderíthető. **Nincs konfigurálva** (alapértelmezett), lehetővé teszi más Bluetooth-kompatibilis eszközök, például az eszköz felderítése mikrofonos.
- **Előzetes bluetooth-párosítás**: **Blokk** megakadályozza, hogy a meghatározott Bluetooth-eszközök automatikus párosítását párosításuk. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy automatikus párosításának az állomás eszközzel.
- **Bluetooth-hirdetés**: **Blokk** megakadályozza, hogy az eszköz Bluetooth-hirdetési küldésére. **Nincs konfigurálva** (alapértelmezett), lehetővé teszi az eszköz Bluetooth-hirdetési küldése.
- **Bluetooth-engedélyezett szolgáltatások**: **Adjon hozzá** listáját engedélyezett Bluetooth-szolgáltatások és -profilok meghatározása hexadecimális karakterláncokként, mint például a `{782AFCFC-7CAA-436C-8BF0-78CD0FFBD4AF}`.

  [Használati útmutató ServicesAllowedList](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth#servicesallowedlist-usage-guide) rendelkezik a lista további tájékoztatást.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="cloud-and-storage"></a>Felhő és tárolás

Ezeket a beállításokat használja a [CSP házirend fiókok](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-accounts); is a Windows támogatott kiadások listája látható.

- **Microsoft-fiók**: **Blokk** megakadályozza, hogy a végfelhasználók számára egy Microsoft-fiók társítását az eszközön. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy hozzáadásával és a egy Microsoft-fiók használatával.
- **Nem Microsoft-fiók**: **Blokk** megakadályozza, hogy a végfelhasználók számára a felhasználói felülete nem Microsoft-fiókok hozzáadását. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a felhasználók számára, amelyek nem kapcsolódnak egy Microsoft-fiók e-mail fiókokat vegyen fel.
- **Microsoft-fiók beállításszinkronizálása**: **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy az eszköz- és Alkalmazásbeállítások szinkronizálását az eszközök között Microsoft-fiókkal társított. **Blokk** megakadályozza, hogy a szinkronizálás.
- **A Microsoft Account – bejelentkezési segéd**: Ha beállítása **nincs konfigurálva** (alapértelmezett), a végfelhasználók elindíthatja és leállíthatja a **Microsoft fiók bejelentkezési segédje** (wlidsvc) szolgáltatás. Az operációsrendszer-szolgáltatás lehetővé teszi a felhasználóknak a saját Microsoft-fiókjával bejelentkezni. **Tiltsa le** megakadályozza, hogy a végfelhasználók számára a Microsoft bejelentkezési segéd szolgáltatást (wlidsvc) szabályozása.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="cloud-printer"></a>Felhőbeli nyomtató

Ezeket a beállításokat használja a [EnterpriseCloudPrint házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-enterprisecloudprint); is a Windows támogatott kiadások listája látható.

- **Nyomtató-felderítési URL-cím**: Adja meg az URL-cím keresése a felhőbeli nyomtatók. Például írja be a következőt: `https://cloudprinterdiscovery.contoso.com`.
- **Nyomtató hozzáférés szolgáltató URL-címe**: Adja meg a hitelesítési végpont URL-címe, az OAuth-jogkivonatok beolvasásához. Például írja be a következőt: `https://azuretenant.contoso.com/adfs`.
- **Azure-beli natív ügyfélalkalmazás GUID**: Adja meg a szolgáltatótól OAuth-jogkivonatok kérhető ügyfélalkalmazás GUID-ja. Például írja be a következőt: `E1CF1107-FF90-4228-93BF-26052DD2C714`.
- **Nyomtatási szolgáltatás erőforrás-URI**: Adja meg a nyomtatási szolgáltatás az Azure Portal webhelyen konfigurált OAuth erőforrás URI azonosítója. Például írja be a következőt: `http://MicrosoftEnterpriseCloudPrint/CloudPrint`.
- **Lekérdezendő nyomtatók maximális száma**: Adja meg a lekérdezni kívánt nyomtatók maximális száma. Az alapértelmezett érték `20`.
- **Nyomtatófelderítési szolgáltatás erőforrás URI**: Adja meg az OAuth-erőforrás URI-nyomtató discovery szolgáltatás beállítása az Azure Portalon. Például írja be a következőt: `http://MopriaDiscoveryService/CloudPrint`.

> [!TIP]
> Miután beállította a [Windows Server hibrid Felhőbeli nyomtatás](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview), ezeket a beállításokat, és a Windows-eszközökre telepíteni.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="control-panel-and-settings"></a>Vezérlőpult és Gépház

- **Gépház alkalmazás**: **Blokk** megakadályozza, hogy a végfelhasználók a Windows gépház alkalmazás eléréséhez. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi a felhasználóknak nyissa meg a beállítások alkalmazást az eszközön.
  - **Rendszer**: **Blokk** megakadályozza a hozzáférést a gépház alkalmazás rendszer területéhez. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi a hozzáférést.
    - **Energiagazdálkodási és alvási beállítások módosítása** (csak asztali verzió): **Blokk** megakadályozza, hogy a végfelhasználók megváltoztassa az eszköz energiagazdálkodási és alvási beállításait. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a felhasználók módosíthatja és energiagazdálkodási beállításokat.
  - **eszközök**: **Blokk** megakadályozza a hozzáférést az eszközön a gépház alkalmazás eszközök területéhez. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi a hozzáférést.
  - **Hálózat és Internet**: **Blokk** megakadályozza a hozzáférést az eszközön a gépház alkalmazás hálózat és Internet területéhez. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi a hozzáférést.
  - **Személyre szabás**: **Blokk** megakadályozza a hozzáférést az eszközön a gépház alkalmazás személyre szabás területéhez. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi a hozzáférést.
  - **Alkalmazások**: **Blokk** megakadályozza a hozzáférést a gépház alkalmazás az eszközön lévő alkalmazások területéhez. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi a hozzáférést.
  - **Fiókok**: **Blokk** megakadályozza a hozzáférést az eszközön a gépház alkalmazás fiókok területéhez. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi a hozzáférést.
  - **Idő és nyelv**: **Blokk** megakadályozza a hozzáférést az eszközön a gépház alkalmazás idő és nyelv területéhez. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi a hozzáférést.
    - **Rendszeridő módosítása**: **Blokk** megakadályozza, hogy a végfelhasználók számára az eszköz dátum és idő beállításainak módosítása. **Nincs konfigurálva** lehetővé teszi a felhasználók a beállítások módosításához.
    - **Területi beállítások módosítása** (csak asztali verzió): **Blokk** megakadályozza, hogy a végfelhasználók megváltoztassa az eszköz területi beállításait. **Nincs konfigurálva** lehetővé teszi a felhasználók a beállítások módosításához.
    - **Nyelvi beállítások módosítása (csak asztali verzióban)** : **Blokk** megakadályozza, hogy a végfelhasználók számára az eszköz nyelvi beállításait módosítja. **Nincs konfigurálva** lehetővé teszi a felhasználók a beállítások módosításához.

      [CSP a beállítások házirend](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings)

  - **Játékok**: **Blokk** megakadályozza a hozzáférést az eszközön a gépház alkalmazás játékok területéhez. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi a hozzáférést.
  - **Könnyű elérés**: **Blokk** megakadályozza a hozzáférést a gépház alkalmazás az eszköz a könnyű kezelés területéhez. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi a hozzáférést.
  - **Adatvédelmi**: **Blokk** megakadályozza a hozzáférést az eszközön a gépház alkalmazás adatvédelem területéhez. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi a hozzáférést.
  - **Frissítés és biztonság**: **Blokk** megakadályozza a hozzáférést az eszközön a gépház alkalmazás frissítés és biztonság területéhez. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi a hozzáférést.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="display"></a>Megjelenítés

Ezeket a beállításokat használja a [CSP házirend megjelenítendő](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-display); is a Windows támogatott kiadások listája látható.

A GDI DPI-méretezés lehetővé teszi, hogy a nem DPI figyelembe értesülnek / figyelő DPI-alkalmazásokat.

- **Kapcsolja be a GDI-méretezés alkalmazások**: **Adjon hozzá** az örökölt alkalmazásokat, amelyeket szeretne van kapcsolva a GDI DPI-méretezés. Például írja be a következőt: `filename.exe` vagy `%ProgramFiles%\Path\Filename.exe`.

  A GDI DPI-méretezés be van kapcsolva a listában szereplő összes örökölt alkalmazások számára.

- **Kapcsolja ki a GDI-méretezés alkalmazások**: **Adjon hozzá** az örökölt alkalmazásokat, amelyeket szeretne a GDI DPI-méretezés ki van kapcsolva. Például írja be a következőt: `filename.exe` vagy `%ProgramFiles%\Path\Filename.exe`.

  A GDI DPI-méretezés ki van kapcsolva a listában szereplő összes örökölt alkalmazások számára.

Emellett **importálás** alkalmazások listája egy .csv-fájlt.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="general"></a>Általános

Ezeket a beállításokat használja a [házirend CSP élmény](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience); is a Windows támogatott kiadások listája látható. 

- **Képernyőfelvétel** (csak mobil): **Blokk** megakadályozza, hogy a végfelhasználók első lépésének képernyőképei az eszközön. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ez a funkció.
- **Másolás és beillesztés (csak mobileszköz)** : **Blokk** megakadályozza, hogy a végfelhasználók használják a másolás és beillesztés az eszközön lévő alkalmazások között. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ez a funkció.
- **Regisztráció manuális törlésének**: **Blokk** megakadályozza, hogy a végfelhasználók számára a munkahelyi Vezérlőpulton az eszközön a munkahelyi fiók törlése. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ez a funkció.

  A házirend-beállítás nem vonatkozik, ha a számítógép az Azure AD-hez és az automatikus igénylés engedélyezve van.

- **Főtanúsítvány manuális telepítésének** (csak mobil): **Blokk** megakadályozza, hogy a végfelhasználók legfelső szintű tanúsítványok és köztes szolgáltatói tanúsítványok manuális telepítése. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ez a funkció.
- **Kamera**: **Blokk** megakadályozza, hogy a végfelhasználók számára az eszközön a kamera használatával. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ez a funkció.
- **OneDrive-fájlszinkronizálás**: **Blokk** megakadályozza, hogy a végfelhasználók számára fájlok szinkronizálása a onedrive-bA az eszközről. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ez a funkció.
- **Cserélhető tároló**: **Blokk** megakadályozza, hogy a végfelhasználók használják a külső tárolóeszköz, például az eszköz SD-kártya. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ez a funkció.
- **Földrajzi hely meghatározásának**: **Blokk** megakadályozza, hogy a felhasználók ne tudják bekapcsolni a helyalapú szolgáltatásokat az eszközön. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ez a funkció.
- **Internetkapcsolat megosztása**: **Blokk** megakadályozza, hogy az internetkapcsolat megosztását az eszközön. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ez a funkció.
- **Telefon alaphelyzetbe állítása**: **Blokk** megakadályozza, hogy a végfelhasználók törlése, és ezzel az eszközt a gyári beállításokat. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ez a funkció.
- **USB-kapcsolat**: **Blokk** megakadályozza a külső tárolóeszközöket USB-kapcsolaton az eszközön keresztül. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ez a funkció. USB-töltésre Ez a beállítás nincs hatással.
- **Lopásgátló üzemmód** (csak mobil): **Blokk** megakadályozza, hogy a végfelhasználók számára az eszköz lopásgátló üzemmód-beállítás kiválasztásával. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ez a funkció.
- **Cortana**: **Blokk** az eszközön, a Cortana beszédfelismerési asszisztens letiltása. Cortana ki van kapcsolva, amikor a felhasználók továbbra is keresési elemek keresése az eszközön. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a Cortana.
- **Hangrögzítés** (csak mobil): **Blokk** megakadályozza, hogy a végfelhasználók számára az eszköz hangrögzítőjét használata az eszközön. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a hangrögzítés letltása alkalmazásokhoz.
- **Eszköznév módosításának** (csak mobil): **Blokk** megakadályozza, hogy a végfelhasználók számára az eszköz nevének módosítása. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ez a funkció.
- **Kiépítési csomagok hozzáadása**: **Blokk** megakadályozza, hogy a konfigurációs ügynök kiépítési csomagokat telepítő az eszközön. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ez a funkció.
- **Kiépítési csomagok eltávolítása**: **Blokk** megakadályozza, hogy a konfigurációs ügynök kiépítési csomagokat, amelyek a kiépítési csomagok eltávolítása az eszközről. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ez a funkció.
- **Eszközfelderítés**: **Blokk** megakadályozza, hogy az eszköz más eszközök általi felderíthetőségét. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ez a funkció.
- **Feladatváltó** (csak mobil): **Blokk** megakadályozza, hogy a feladatok közötti váltás az eszközön. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ez a funkció.
- **SIM-kártya hibaüzenet-panelje** (csak mobil): **Blokk** hibaüzenetek megjelenítése az eszközön, ha nincsenek SIM-kártya észlel. **Nincs konfigurálva** (alapértelmezett) hiba üzeneteket jeleníti meg.
- **Szabadkézi munkaterület**: Válassza ki, és ha igen, felhasználó férhet hozzá az ink-munkaterületen. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Bekapcsolja az ink-munkaterületen, és a felhasználó engedélyezett, használhatja azt a zárolási képernyőn.
  - **Le van tiltva a zárolási képernyőn**: A szabadkézi munkaterület engedélyezve van, és a funkció be van kapcsolva. De a zárolási képernyőn a felhasználó nem tudja elérni.
  - **Letiltott**: Szabadkézi munkaterület való hozzáférés le van tiltva. A funkció ki van kapcsolva.

  [CSP WindowsInkWorkspace házirend](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace)

- **Automatikus újbóli üzembe helyezés**: Válasszon **engedélyezése** , rendszergazdai jogosultságokkal rendelkező felhasználóknak törölheti az összes felhasználói adatot és beállítást **CTRL + Win + R** , az eszköz zárolási képernyőjén. Az eszköz automatikusan konfigurálni és felügyelet alá vonni. **Nincs konfigurálva** (alapértelmezett) megakadályozza, hogy ez a funkció.
- **Szeretne csatlakozni a hálózati eszköz telepítése során a felhasználók**: Válasszon **megkövetelése** , az eszköz csatlakozik a hálózathoz, mielőtt a korábbi a hálózat lap Windows-telepítés során. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy lejárt a hálózat lapot, hogy a felhasználók akkor is, ha az nem csatlakozik hálózathoz.

  A beállítás életbe lép az eszköz törlését vagy alaphelyzetbe állítása a következő alkalommal. További Intune konfigurációra, például az eszköz legyen regisztrálva és konfigurációs beállítások az Intune által felügyelt. De miután regisztrált, és házirendeket fogad, majd alaphelyzetbe állíthatja az eszközt a beállítás a következő Windows-telepítés során kényszeríti.

- **Közvetlen memória-hozzáférés**: **Blokk** megakadályozza, hogy közvetlen memória-hozzáférés (DMA) az összes gyakran használt adatok moduláris PCI alsóbb rétegbeli port mindaddig, amíg a felhasználó bejelentkezik a Windows. **Engedélyezett** (alapértelmezett) engedélyezi a hozzáférést közvetlen memória-Hozzáférést, akkor is, ha egy felhasználó nem jelentkezett be.

  CSP: [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)

- **Folyamatait a Feladatkezelőben**: Ez a beállítás meghatározza, hogy e nem rendszergazdák teljes feladat Feladatkezelő használható. **Blokk** általános jogú felhasználók (nem rendszergazda) megakadályozza, hogy egy folyamat vagy feladat az eszköz befejezi a Feladatkezelő használatát. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a folyamat leállítása, vagy a feladat a Feladatkezelő használatát általános jogú felhasználók.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="locked-screen-experience"></a>Zárolási képernyő felülete

- **Műveletközpont értesítései (csak mobil)** : **Blokk** megakadályozza, hogy a Műveletközpont értesítéseinek bemutató. Ez az eszköz zárolási képernyőjén. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a felhasználók eldönthetik, hogy mely alkalmazások értesítések megjelenítése a zárolási képernyőn.

  [AboveLock/AllowActionCenterNotifications CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowactioncenternotifications)

- **Zárolt képernyőn kép URL-címe (csak asztali verzióban)** : Adja meg a Windows zárolási képernyőjének háttérképeként használt JPG, JPEG vagy PNG formátumú kép URL. Például írja be a következőt: `https://contoso.com/image.png`. Ez a beállítás zárolja a lemezképet, és ezt követően nem módosítható.
- **Felhasználó által konfigurálható képernyő-időkorlát (csak mobil)** : **Lehetővé teszi** lehetővé teszi a felhasználók a képernyő-időkorlát konfigurálása. **Nincs konfigurálva** (alapértelmezett) nem ad a felhasználók ezt a beállítást.

  [DeviceLock/AllowScreenTimeoutWhileLockedUserConfig CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-allowscreentimeoutwhilelockeduserconfig)

- **Cortana zárolt képernyőn** (csak asztali verzió): **Blokk** megakadályozza, hogy a felhasználók a kezelheti a Cortanával, ha az eszköz zárolási képernyőjén. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a Cortana-szal.

  [AboveLock/AllowCortanaAboveLock CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowcortanaabovelock)

- **Bejelentési értesítések zárolt képernyőn**: **Blokk** megakadályozza, hogy a bejelentési értesítést bemutató. Ez az eszköz zárolási képernyőjén. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ezek az értesítések.

  [AboveLock/AllowToasts CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowtoasts)

- **Képernyő időkorlátja (csak mobil)** : Az időtartamot (másodpercben) a képernyő zárolásától a képernyő kikapcsolása. Támogatott értékek: 11-1800. Adja meg például `300` Ez az időkorlát beállítása 5 perc.

  [DeviceLock/ScreenTimeoutWhileLocked CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-screentimeoutwhilelocked)

Válassza ki **OK** a módosítások mentéséhez.

## <a name="messaging"></a>Üzenetkezelés

Ezeket a beállításokat használja a [házirend CSP üzenetkezelési](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-messaging); is a Windows támogatott kiadások listája látható.

- **Üzenetszinkronizálás (csak mobil)** : **Blokk** letiltja a szöveges üzenetek biztonsági mentése és visszaállítása, és a rendszer szinkronizálja a Windows-eszközök közötti üzenetek. Letiltás elkerülhetők az folyamatban van a szervezet vezérlő kívüli kiszolgálókon tárolt adatokat. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a felhasználók módosítani ezeket a beállításokat, és szinkronizálja azok üzenetek.
- **MMS (csak mobilon)** : **Blokk** letiltja az MMS küldése és fogadási funkciójának az eszközön. A nagyvállalatoknak Ez a szabályzat használatával MMS letiltása az eszközökön a naplózási vagy a kezelési követelmények részeként. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi az MMS küldése és fogadása.
- **RCS (csak mobil)** : **Blokk** letiltja a gazdag kommunikációs szolgáltatások (RCS) küldése és fogadási funkciójának az eszközön. A nagyvállalatoknak Ez a szabályzat használatával RCS letiltása az eszközökön a naplózási vagy a kezelési követelmények részeként. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy RCS küldése és fogadása.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="microsoft-edge-browser"></a>Microsoft Edge böngésző

Ezeket a beállításokat használja a [böngészőnek CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser), amely felsorolja a támogatott Windows-kiadások.

### <a name="use-microsoft-edge-kiosk-mode"></a>A Microsoft Edge-teljes képernyős mód használata

A rendelkezésre álló beállítások a kiválasztott beállításoktól függően módosítsa. A választható lehetőségek:

- **Nem** (alapértelmezett): Teljes képernyős mód nem futó Microsoft Edge. Módosíthatja, és konfigurálhatja a Microsoft Edge-beállítások érhetők el.
- **Digitális és interaktív aláírási (Egyalkalmazásos kioszk)** : Megfelelő digitális és interaktív aláírási a Microsoft Edge teljes képernyős mód a szűrők Microsoft Edge-beállítások csak a Windows 10-es Egyalkalmazásos kioszk használja. Ezzel a beállítással nyisson meg egy URL-cím teljes képernyőn válassza ki, és csak a tartalom megjelenítése az adott webhelyre. [Állítsa be a digitális jelentkezik](https://docs.microsoft.com/windows/configuration/setup-digital-signage) Ez a szolgáltatás további információkkal szolgál.
- **InPrivate-nyilvános böngészés (Egyalkalmazásos kioszk)** : Az InPrivate-nyilvános böngészés a Microsoft Edge teljes képernyős mód a szűrők Microsoft Edge-beállítások Windows 10-es Egyalkalmazásos kioszk használja. A Microsoft Edge több lapon verzióját futtatja.
- **Normál üzemmódban (többalkalmazásos kioszk)** : Microsoft Edge-beállítások, amelyek alkalmazhatók a normál Microsoft Edge kioszk mód szűri. A Microsoft Edge teljes-verziója fut az összes böngészési funkció.
- **Nyilvános tallózása (többalkalmazásos kioszk)** : Microsoft Edge-beállítások, amelyek alkalmazhatók a nyilvános-böngészést a Windows 10 rendszerű többalkalmazásos kioszk szűri.  A Microsoft Edge InPrivate több lapon verzióját futtatja.

> [!TIP]
> Ezek a beállítások mire a további információkért lásd: [Microsoft Edge kioszk mód konfigurációs típusok](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

Az eszközkorlátozások profiljának közvetlenül kapcsolódik ahhoz a teljes képernyős profil létrehozásakor használja a [Windows kioszkmód](kiosk-settings-windows.md). Összefoglalásképpen:

1. Hozzon létre a [Windows kioszkmód](kiosk-settings-windows.md) profil az eszköz kioszk módban futtatni. Válassza ki a Microsoft Edge, az alkalmazást, és állítsa be a Microsoft Edge teljes képernyős mód a teljes képernyős profilban.
2. A jelen cikkben ismertetett eszközkorlátozások profiljának létrehozása, és a funkciók és a Microsoft Edge-ben engedélyezett beállításainak konfigurálása. Ügyeljen arra, hogy válassza ki az ugyanazon Microsoft Edge teljes képernyős mód, a teljes képernyős profilban kijelölt ([Windows kioszkmód](kiosk-settings-windows.md)). 

    [Kioszk mód beállításainak támogatott](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-policies-for-kiosk-mode) egy nagyszerű forrás.

> [!IMPORTANT] 
> Ügyeljen arra, hogy a Microsoft Edge-profil hozzárendelése ugyanazokkal az eszközökkel, mint a teljes képernyős profil ([Windows kioszkmód](kiosk-settings-windows.md)).

[ConfigureKioskMode CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskmode)

### <a name="start-experience"></a>Indítsa el a felhasználói élményt

- **Indítsa el a Microsoft Edge**: Válassza ki, hogy mely lapok megnyitása a Microsoft Edge indításakor. A választható lehetőségek:
  - **Egyéni lapok start**: Adja meg például a kezdőlapokat `http://www.contoso.com`. A Microsoft Edge, adja meg azon kezdőlapok tölti be.
  - **Új lap**: A Microsoft Edge betölteni, bármi is meg kell adni a a **új lap URL-címe** beállítás.
  - **Utolsó munkamenet oldal**: A Microsoft Edge betölti az utolsó munkamenet-lapon.
  - **Indítsa el a lapok és helyi alkalmazások beállításai**: A Microsoft Edge az alapértelmezett start lap az operációs rendszer által meghatározott.

- **Lehetővé teszi a felhasználó módosíthatja a kezdőlapokat**: **Igen** (alapértelmezett) lehetővé teszi, hogy a felhasználók megváltoztassák az. A rendszergazdák használhatják a `EdgeHomepageUrls` , adja meg azon kezdőlapok, amelyeket a felhasználók alapértelmezés szerint amikor megnyitja a Microsoft Edge. **Nem** letiltja a felhasználók módosítsák a kezdőlapokat.
- **Új lap lehetővé teszi a webes tartalom**: Ha a beállítása **Igen** (alapértelmezett), a Microsoft Edge megnyitja az URL-címet adott meg a **új lap URL-címe** beállítás. Ha a **új lap URL-címe** beállítás üres, a Microsoft Edge szerepel a Microsoft Edge-beállítások új lap nyílik meg. Felhasználó módosíthatná. Ha a beállítása **nem**, a Microsoft Edge egy üres lapot egy új lapon nyílik meg. Felhasználó nem módosíthatja azt.
- **Új lap URL-címe**: Adja meg az URL-cím, az új lap megnyitásához. Például írja be a következőt: `https://www.bing.com` vagy `https://www.contoso.com`.

- **Kezdőlap gombjának**: Válassza ki, mi történik, a kezdőlap gombjának kiválasztásakor. A választható lehetőségek:
  - **Indítsa el a lapok**: A kiválasztott lehetőség nyílik a **indítsa el a Microsoft Edge-** beállítás
  - **Új lap**: Megnyitja az URL-címet adott meg a **új lap URL-címe** beállítás.
  - **Otthoni gomb URL-cím**: Adja meg az URL-cím megnyitásához. Például írja be a következőt: `https://www.bing.com` vagy `https://www.contoso.com`.
  - **Elrejtése kezdőképernyő gombra**: A kezdőlap gombjának elrejtése
- **Felhasználók módosíthatják a kezdőlap gombja**: **Igen** lehetővé teszi a felhasználóknak, módosítsa a home gombra. A felhasználó módosításait felülbírálása bármely rendszergazdai beállításait a home gombra. **Nem** (alapértelmezett) letiltja a felhasználók nem módosíthatják, hogy a rendszergazda hogyan konfigurálta a home gombra.
- **Első futtatás élmény lap (csak mobil) megjelenítése**: **Igen** (alapértelmezett) a használatát bemutató első lap bemutatja a Microsoft Edge-ben. **Nem** leállítja a bemutató lap megjelenítését az első alkalommal futtatása a Microsoft Edge. Ez a funkció lehetővé teszi, hogy vállalatok számára, például a nulla kibocsátás regisztrált szervezetek konfigurációk blokkolja ezen a lapon.
- **Első futtatás élmény URL helylistájának helye** (csak Windows 10 Mobile esetén): Adja meg az URL-cím, amely az első futtatási oldal URL-jét tartalmazó XML-fájlra mutat. Például írja be a következőt: `https://www.contoso.com/sites.xml`.

- **Üresjárati idő után frissítse a böngészőt**: Adja meg az üresjárati perc után a böngésző frissítése, a 0 – 1440 perc. Alapértelmezett érték a `5` perc. Ha a beállítása `0` (nulla), a böngésző nem frissül üresjárat után.

  Ez a beállítás csak akkor érhető el, ha a [nyilvános InPrivate-böngészés (Egyalkalmazásos kioszk)](#use-microsoft-edge-kiosk-mode).

- **Előugró ablakok engedélyezése** (csak asztali verzió): **Igen** (alapértelmezett) lehetővé teszi, hogy a az előugró ablakokat a böngészőben. **Nem** megakadályozza, hogy az előugró ablakokat a böngészőben.
- **Intranetes adatforgalom küldését az Internet Explorer** (csak asztali verzió): **Igen** lehetővé teszi a felhasználóknak az intranetes webhelyek megnyitását az Internet Explorer, a Microsoft Edge helyett. A beállítás értéke a visszamenőleges kompatibilitás. **Nem** (alapértelmezett) lehetővé teszi, hogy a felhasználók a Microsoft Edge.
- **Vállalati üzemmód webhelylistájának helye** (csak asztali verzió): Adja meg az URL-cím, amely az XML-fájl, amely tartalmazza a vállalati üzemmódban megnyíló webhelyek listája. Felhasználók nem módosíthatják ezt a listát. Például írja be a következőt: `https://www.contoso.com/sites.xml`.
- **Üzenet megnyitásakor webhelyek az Internet Explorer**: Ez a beállítás segítségével konfigurálhatja a Microsoft Edge az értesítések megjelenítése, mielőtt egy webhely megnyitása az Internet Explorer 11. A választható lehetőségek:
  - **Ne jelenjen meg üzenet**: Az operációs rendszer alapértelmezett viselkedést szolgál, amely előfordulhat, hogy jelenjen meg egy üzenet.
  - **A helyen üzenet megjelenítése megnyitása az Internet Explorer 11**: Az üzenet megjelenítése, ha az IE. Nyissa meg a helyek Internet Explorer. 
  - **Jelenjen meg üzenet kapcsolóval, hogy a Microsoft Edge-ben nyissa meg a helyek**: Az üzenet megjelenítése, amikor helyek megnyitása az Edge-ben. Az üzenet tartalmaz egy **folytathatja a munkát a Microsoft Edge-ben** hivatkozást, így a felhasználók eldönthetik, a Microsoft Edge helyett az Internet Explorer.

  > [!IMPORTANT]
  > Ez a beállítás megköveteli, hogy használjon a **vállalati üzemmód webhelylistájának helye** beállítást, a **intranetes forgalom küldése az Internet Explorer** beállítás, vagy mindkét beállítást.

- **Microsoft kompatibilitási listájának engedélyezése**: **Igen** (alapértelmezett) lehetővé teszi, hogy a Microsoft kompatibilitási lista használatával. **Nem** megakadályozza, hogy a Microsoft Edge-ben a Microsoft kompatibilitási listájának. A Microsoft ezen listája segítségével a Microsoft Edge megfelelően tudja megjeleníteni az ismert kompatibilitási problémákkal rendelkező webhelyeket.
- **Az előzetes betöltés kezdőlapokat és új lapot**: **Igen** (alapértelmezett) használ az operációs rendszer alapértelmezett viselkedést, akkor ezek az oldalak betöltésére. Betöltését minimalizálja a Microsoft Edge elindításához, és új lap betöltése. **Nem** megakadályozza, hogy a Microsoft Edge konfigurálások kezdőlapokat és az új lapon.
- **Prelaunch kezdőlapokat és új lapot**: **Igen** (alapértelmezett) az operációs rendszer az alapértelmezett viselkedést alkalmazza, a prelaunch, akkor ezeket az oldalakat. Előre indítása segít a Microsoft Edge teljesítményét, és minimálisra csökkenti a Microsoft Edge indításához szükséges időt. **Nem** megakadályozza, hogy a Microsoft Edge előre indítása a kezdőlapokat és új lapon.

Válassza ki **OK** a módosítások mentéséhez.

### <a name="favorites-and-search"></a>Kedvencek és keresés

- **Kedvencek sáv megjelenítése**: Válassza ki, mi történik a Kedvencek sávra, bármely Microsoft Edge lapján. A választható lehetőségek:
  - **A kezdés és új lapok**: A Kedvencek sáv a Microsoft Edge indításakor, és az összes lap látható. A végfelhasználók módosíthatja ezt a beállítást.
  - **Minden oldalon**: Az összes a Kedvencek sáv mutatja. A végfelhasználók a beállítás nem módosítható.
  - **Rejtett**: Elrejti a Kedvencek sáv minden oldalon. A végfelhasználók a beállítás nem módosítható.
- **Kedvencek módosításának engedélyezése**: **Igen** (alapértelmezett) használ az operációs rendszer alapértelmezett, amely lehetővé teszi a felhasználóknak, hogy a listában. **Nem** megakadályozza, hogy a végfelhasználók számára hozzáadása, importálás, rendezés vagy szerkesztését a Kedvencek listájához.
  - **Kedvencek lista**: Adja hozzá az URL-címek listáját a Kedvencek fájl. Hozzáadhat például `http://contoso.com/favorites.html`.
- **Kedvencek szinkronizálása a Microsoft-böngészők között** (csak asztali verzió): **Igen** arra kényszeríti a Windows Internet Explorer és Microsoft Edge között a Kedvencek szinkronizálása. Kiegészítést, törlést, a módosítások és a sorrend változásait böngészők között vannak megosztva.  **Nem** (alapértelmezett) használ az operációs rendszer alapértelmezett, amelyet is biztosíthat a felhasználók számára a kiválasztott Kedvencek szinkronizálása a böngészők között.
- **Alapértelmezett keresőmotor**: Válassza ki az eszközön az alapértelmezett keresőmotort. A végfelhasználók ezt az értéket bármikor módosíthatják. A választható lehetőségek:
  - Keresőmotor az ügyfél a Microsoft Edge-beállítások
  - A Bing
  - Google
  - Yahoo
  - Egyéni érték: A **OpenSearch Xml URL-cím**, HTTPS URL-címet adja meg a rövid nevét és a keresőmotor, legalább az URL-címet tartalmazó XML-fájllal. Például írja be a következőt: `https://www.contoso.com/opensearch.xml`.
- **Keresési javaslatok megjelenítésének**: **Igen** (alapértelmezett) lehetővé teszi, hogy a keresőmotor webhelyeket javasoljon a keresőkifejezések beírása címet a címsorba. **Nem** megakadályozza, hogy ez a funkció.
- **-Motor keresés engedélyezése**: **Igen** (alapértelmezett) lehetővé teszi a felhasználóknak új keresőmotorok felvétele vagy módosítása a Microsoft Edge-ben az alapértelmezett keresőmotort. Válasszon **nem** megakadályozza, hogy a felhasználók a keresőmotor testreszabása.

  Ez a beállítás csak akkor érhető el, ha a [normál módba (többalkalmazásos kioszk)](#use-microsoft-edge-kiosk-mode).

Válassza ki **OK** a módosítások mentéséhez.

### <a name="privacy-and-security"></a>Adatvédelem és biztonság

- **InPrivate-böngészés engedélyezése**: **Igen** (alapértelmezett) lehetővé teszi, hogy InPrivate-böngészés a Microsoft Edge-ben. Után minden InPrivate-lapok bezárása, a Microsoft Edge a böngészési adatok törlése az eszközről. **Nem** megakadályozza, hogy a végfelhasználók InPrivate-böngészési munkamenetet nyissanak.
- **Mentse a böngészési előzmények**: **Igen** (alapértelmezett) engedélyezése a Microsoft Edge-ben a böngészési előzményeket mentése. **Nem** megakadályozza, hogy a mentése folyamatban van a böngészési előzményeket.
- **Böngészési adatok kilépéskori törlése** (csak asztali verzió): **Igen** törli az előzmények és böngészési adatok, amikor a felhasználó bezárja a Microsoft Edge. **Nem** (alapértelmezett) használ az operációs rendszer alapértelmezett beállítás, amely előfordulhat, hogy gyorsítótárazza a böngészési adatok.
- **Szinkronizálja a böngésző beállításai között a felhasználó eszközei**: Válassza ki, hogyan szeretné böngésző beállítások eszközök közötti szinkronizálása. A választható lehetőségek:
  - **Lehetővé teszi**: A Microsoft Edge böngésző beállításai között a felhasználó-eszköz szinkronizálása engedélyezése
  - **Letiltása és engedélyezése a felhasználó felülbírálás**: Letiltása a Microsoft Edge böngésző beállításai között a felhasználó-eszköz szinkronizálása. Ezzel a beállítással a felhasználók felülbírálhatják.
  - **Blokk**: Letiltása a Microsoft Edge böngésző beállítás a felhasználói eszközök közötti szinkronizálását. Felhasználók nem bírálja felül ezt a beállítást.

Ha "letiltása és engedélyezése a felhasználó felülbírálás" meg van jelölve, a felhasználó felülbírálhatja a rendszergazda kijelölése.

- **Jelszókezelő engedélyezése**: **Igen** (alapértelmezett) lehetővé teszi, hogy a Microsoft Edge jelszókezelő, amely lehetővé teszi a felhasználók mentéséhez és az eszközön jelszavak kezelése automatikusan használandó. **Nem** megakadályozza, hogy a Microsoft Edge jelszókezelő használatával.
- **A cookie-k**: Válassza ki, hogyan kezelje a böngésző cookie-kat. A választható lehetőségek:
  - **Lehetővé teszi**: A cookie-k tárolódnak az eszközön.
  - **Az összes cookie blokkolása**: A cookie-k sehol nincsenek tárolva az eszközön.
  - **Csak harmadik féltől származó cookie blokkolása**: Harmadik féltől származó, vagy partner cookie-k sehol nincsenek tárolva az eszközön.
- **Automatikus kitöltés engedélyezése űrlapokon**: **Igen** (alapértelmezett) lehetővé teszi a felhasználóknak a böngésző automatikus kiegészítési funkciója beállításainak módosítását, és az űrlapmezők automatikus feltöltéséhez. **Nem** letiltja az automatikus kitöltés szolgáltatást a Microsoft Edge-ben.
- **"Do not track" fejlécek küldése**: **Igen** "do not track" fejlécek küld a (javasolt) követési információkat kérő webhelyeknek. **Nem** (alapértelmezett) nincs fejlécek küldése lehetővé teszi a webhelyek nyomon követhetik a felhasználót. Felhasználó konfigurálhat.
- **WebRTC localhost IP-cím megjelenítése**: **Igen** (alapértelmezett) lehetővé teszi, hogy a felhasználók localhost IP-cím jelennek meg a protokollt használó telefonhívások kezdeményezésekor. **Nem** megakadályozza, hogy a felhasználók localhost IP-cím nem jelenik meg. 
- **Adatgyűjtés élő csempéhez engedélyezése**: **Igen** (alapértelmezett) lehetővé teszi, hogy a Microsoft Edge, a start menübe rögzített élő Csempék-fájlokból gyűjt adatokat. **Nem** megakadályozza, hogy ezen információk gyűjtésére, amely előfordulhat, hogy felhasználók egy korlátozott felhasználói élményt biztosíthat.
- **Felhasználó felülbírálhatja a tanúsítványhibákat**: **Igen** (alapértelmezett) lehetővé teszi, hogy a felhasználók hozzáférhessenek a webhelyeket, amelyeket a Secure Sockets Layer/Transport Layer Security (SSL/TLS) hibákat. **Nem** (ajánlott a biztonság fokozása érdekében) megakadályozza, hogy a felhasználók hozzáférjenek a webhelyek SSL vagy TLS hibákkal.

Válassza ki **OK** a módosítások mentéséhez.

### <a name="additional"></a>Továbbiak

- **A Microsoft Edge böngésző engedélyezése** (csak mobil): **Igen** (alapértelmezett) lehetővé teszi, hogy a mobileszközön a Microsoft Edge webböngésző használatával. **Nem** megakadályozza, hogy a Microsoft Edge használata az eszközön. Ha úgy dönt, **nem**, a más egyes beállítások csak asztali vonatkoznak.
- **Cím sáv legördülő lista lehetővé**: **Igen** (alapértelmezett) lehetővé teszi, hogy a Microsoft Edge megjelenítéséhez a címsor legördülő javaslatok listája. **Nem** bemutató javaslatok listáját egy legördülő listában, amikor beírja a Microsoft Edge leáll. Ha a beállítása **nem**, hogy:
  - Üzemében a Microsoft Edge és a Microsoft-szolgáltatások közötti hálózati sávszélességet.
  - Tiltsa le a **keresés és a hely javaslatok megjelenítése a szöveg beírása közben** Microsoft Edge-ben > beállítások.
- **Teljes képernyős üzemmód engedélyezése**: **Igen** (alapértelmezett) lehetővé teszi, hogy a Microsoft Edge, a teljes képernyős módban működnek, amely csak a webes tartalom megjelenítése és elrejtése a Microsoft Edge felhasználói felület. **Nem** megakadályozza, hogy a teljes képernyős mód a Microsoft Edge-ben.
- **Jelzők oldalról engedélyezése**: **Igen** (alapértelmezett) használ az operációs rendszer alapértelmezett, így fér hozzá a `about:flags` lapot. A `about:flags` lap lehetővé teszi, hogy a felhasználók számára a fejlesztői beállítások módosítására és a kísérleti szolgáltatások engedélyezésére. **Nem** megakadályozza, hogy a végfelhasználók hozzáférjenek a `about:flags` oldal a Microsoft Edge-ben.
- **Fejlesztői eszközök engedélyezése**: **Igen** (alapértelmezett) lehetővé teszi a felhasználóknak fejlesztése és hibakeresése a weblapok alapértelmezés szerint az F12 billentyűt a fejlesztői eszközök használatával. **Nem** megakadályozza, hogy a végfelhasználók számára az F12 fejlesztői eszközökkel.
- **JavaScript engedélyezése**: **Igen** (alapértelmezett) lehetővé teszi, hogy a parancsprogramok, például a Javascript, a Microsoft Edge böngészőben. **Nem** megakadályozza, hogy a böngészőben a Java-parancsfájlok futtatását.
- **Felhasználó telepíthet-bővítmények**: **Igen** (alapértelmezett) lehetővé teszi, hogy a végfelhasználók számára, hogy a Microsoft Edge-bővítményeket telepítsenek az eszközön. **Nem** meggátolja a telepítést.
- **Lehetővé teszi a közvetlen telepítési developer Extensions**: **Igen** (alapértelmezett) használ az operációs rendszer alapértelmezett beállítás, amely közvetlen telepítést lehetővé teheti. Közvetlen telepítési telepíti, és futtat az ellenőrizetlen bővítmények. **Nem** megakadályozza, hogy a Microsoft Edge tesztcélú telepítés használatával a **bővítmények betöltése** funkció. Azt, hogy a közvetlen telepítési bővítmények más módokon, például a PowerShell használatával.
- **Bővítmények szükséges**: Válassza ki, hogy mely bővítmények a Microsoft Edge-ben a végfelhasználók számára nem kapcsolható ki. Adja meg a csomagcsaládok nevéről, és válassza ki **Hozzáadás**. [Keresse meg a csomagcsalád nevének (pfn Megkeresése)](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn) nyújt útmutatást.

  Emellett **importálás** CSV-fájl, amely tartalmazza a csomagcsaládok nevéről. Másik lehetőségként **exportálása** a csomagcsaládok nevéről, adja meg.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="network-proxy"></a>Hálózati proxy

Ezeket a beállításokat használja a [NetworkProxy házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/networkproxy-csp), amely felsorolja a támogatott Windows-kiadások.

- **Proxybeállítások automatikus észlelése**: **Blokk** letiltja az eszköz automatikusan észleli a proxy automatikus konfigurációs (PAC) parancsfájlt. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ez a funkció. Ha engedélyezve van, az eszköz megpróbálja megkeresni egy PAC-szkript elérési útját.
- **Proxyparancsfájl használata**: Válasszon **engedélyezése** , adjon meg útvonalat kell konfigurálni a proxykiszolgáló a PAC-szkript. **Nincs konfigurálva** (alapértelmezett) nem teszi lehetővé az URL-címet adja meg a PAC-szkript.
  - **Beállítási parancsfájl URL-címe**: Adja meg a proxykiszolgáló konfigurálásához használni kívánt PAC-szkript URL-CÍMÉT.
- **Manuális proxykiszolgáló használata**: Válasszon **engedélyezése** írják be a nevét vagy IP-cím és a proxy Server TCP-port száma. **Nincs konfigurálva** (alapértelmezett) nem teszi lehetővé, hogy manuálisan adja meg a proxykiszolgáló adatait.
  - **Cím**: Adja meg a nevét, vagy a proxykiszolgáló IP-címét.
  - **Portszám**: Adja meg a proxykiszolgáló portszámát.
  - **Proxyhasználat alóli kivételek**: Adjon meg semmilyen URL, amelyek nem használhatják a proxykiszolgálót. Az egyes címeket pontosvesszővel választhatja el egymástól.
  - **Proxykiszolgáló kihagyása helyi cím esetén**: **Nincs konfigurálva** (alapértelmezett) megakadályozza, hogy a proxykiszolgáló használata az intranet helyi címeinél. **Lehetővé teszi** proxykiszolgálót használ a helyi címek esetén.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="password"></a>Windows 10

Ezeket a beállításokat használja a [DeviceLock házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock), amely felsorolja a támogatott Windows-kiadások.

- **Jelszó**: **Szükséges** a végfelhasználó számára adjon meg egy jelszót az eszköz elérésére. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy az eszköz jelszó nélkül. Csak a helyi fiókok vonatkozik. Tartományi fiók jelszavak továbbra is az Active Directory (AD) és az Azure AD által konfigurált.

  - **Kötelező jelszótípus**: Válassza ki a jelszót. A választható lehetőségek:
    - **Nincs konfigurálva**: Jelszó számokat és betűket tartalmazhat.
    - **Numerikus**: Jelszó csak számnak kell lennie.
    - **Alphanumeric**: Jelszó számokat és betűket kell lennie.
  - **Jelszó minimális hossza**: Szükség esetén a 4 és 16 karakter vagy minimális számának megadása. Adja meg például `6` a jelszó hossza legalább hat karakter megkövetelése.
  
    > [!IMPORTANT]
    > A Windows asztalon megváltozik a jelszóra vonatkozó követelmény, amikor a felhasználó érintett a amikor legközelebb bejelentkeznek a módon, amely rendelkezik az eszköz visszatér az üresjárat aktív. Olyan jelszavakkal, amelyek megfelelnek a követelmény továbbra is kéri módosítsák jelszavukat.
    
  - **Bejelentkezési hibák eszköz törlése előtt**: Adja meg a megengedett, mielőtt törölné az eszközt is lehet, legfeljebb 11 hitelesítési hibák számát. A megadott érvényes számot kiadásától függ. [DeviceLock/MaxDevicePasswordFailedAttempts CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts) támogatott értékeit sorolja fel. `0` eszköz törlési funkcióit (nulla) letiltható.

    Ez a beállítás is az operációs rendszer kiadásától függően különböző hatással van. Ez a beállítás a konkrét részletekért lásd: a [DeviceLock/MaxDevicePasswordFailedAttempts CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts).

  - **Ennyi perc inaktivitás képernyőzárolás**: Adja meg, mennyi ideig eszközt kell inaktívnak lennie a képernyő zárolása előtt.
  - **Jelszó érvényessége (napokban)** : Ha a kell módosítani a jelszót, 1 – 365 nap mennyi ideig adja meg. Adja meg például `90` a 90 nap után lejár. ezt a jelszót.
  - **Korábbi jelszavak újbóli használatának tiltása**: Adja meg a korábban használt jelszavak számát, amelyeket nem használható, az 1-24. Adja meg például `5` így a felhasználók nem állítható be új jelszó a jelenlegi jelszavát, vagy az előző négy jelszavait.
  - **Jelszó kérése, ha az eszköz visszatér inaktív állapotból** (Mobile és Holographic): Válasszon **megkövetelése** így a felhasználóknak meg kell adniuk egy jelszót az eszköz zárolásának feloldásához üresjárat után. **Nincs konfigurálva** (alapértelmezett) nincs szükség a PIN-kódot vagy jelszót, amikor az eszköz visszatér inaktív állapotból, ha.
  - **Egyszerű jelszavak**: Állítsa be **blokk** így a felhasználók nem egyszerű jelszavakat használhassanak, mint például `1234` vagy `1111`. Állítsa be **nincs konfigurálva** (alapértelmezett), hogy a felhasználók például jelszavakat `1234` vagy `1111`. Ez a beállítás a Windows-képjelszavak használatát is engedélyezi vagy letiltja.
- **Automatikus titkosítás során AADJ**: **Blokk** automatikus BitLocker eszköztitkosítás megakadályozza, hogy ha az eszköz az első használatra kész, amikor az eszköz Azure AD-hez. **Nincs konfigurálva** (alapértelmezett) használ az operációs rendszer alapértelmezett beállítás, amely előfordulhat, hogy engedélyezze a titkosítást. A több [BitLocker eszköztitkosítás](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10#bitlocker-device-encryption).

  [Security/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-security#security-preventautomaticdeviceencryptionforazureadjoineddevices)

- **Federal Information Processing Standard (FIPS) házirend**: **Lehetővé teszi** használja a Federal Information Processing Standard (FIPS) szabályzatot, amely az USA kormányzati standard a titkosításhoz, kivonatoláshoz és aláíráshoz. **Nincs konfigurálva** (alapértelmezett) használ az operációs rendszer alapértelmezett beállítás, amely nem érvényes a FIPS használ.

  [Cryptography/AllowFipsAlgorithmPolicy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-cryptography#cryptography-allowfipsalgorithmpolicy)

- **Windows Hello eszközhitelesítés**: **Lehetővé teszi** felhasználók jelentkezzen be a Windows 10 rendszerű számítógép a Windows Hello társeszközt, például telefon, mentességre sávon, vagy IoT-eszköz használatával. **Nincs konfigurálva** (alapértelmezett) használ az operációs rendszer alapértelmezett, amely megakadályozhatja, hogy a Windows Hello appliances eszközök Windows való hitelesítés közben.

  [Authentication/AllowSecondaryAuthenticationDevice CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowsecondaryauthenticationdevice)

- **Webalkalmazás-bejelentkezési**: Lehetővé teszi a Windows bejelentkezési nem ADFS (Active Directory összevonási szolgáltatások) összevont szolgáltatók, például a Security Assertion Markup Language (SAML) támogatása. SAML használ a biztonságos jogkivonatok, amelyek egy egyszeri bejelentkezés (SSO) webböngészők élményt nyújtanak. A választható lehetőségek:

  - **Nincs konfigurálva** (alapértelmezett): Az operációs rendszer alapértelmezett használja az eszközön.
  - **Engedélyezett**: Bejelentkezés a webes hitelesítőadat-szolgáltató engedélyezve van.
  - **Letiltott**: A webes hitelesítőadat-szolgáltató le van tiltva, a bejelentkezéshez.

  [Authentication/EnableWebSignIn CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-enablewebsignin)

- **Az Azure AD-bérlői tartományán előnyben részesített**: Adja meg egy meglévő tartománynevet a szervezet Azure ad-ben. Amikor a felhasználók ebben a tartományban jelentkezzen be, nem kell a tartomány nevét. Például írja be a következőt: `contoso.com`. A felhasználók a `contoso.com` tartomány is jelentkezzen be a felhasználó nevét, például `abby`, helyett `abby@contoso.com`.

  [Authentication/PreferredAadTenantDomainName CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-preferredaadtenantdomainname)

Válassza ki **OK** a módosítások mentéséhez.

## <a name="per-app-privacy-exceptions"></a>Alkalmazásonkénti adatvédelmi kivételek

Hozzáadhat alkalmazásokat, amelyek rendelkeznie kell egy "Alapértelmezett adatvédelem" definiálása eltérő adatvédelmi működést.

- **Csomag neve**: Alkalmazás csomagcsaládjának neve.
- **Alkalmazásnév**: Az alkalmazás neve.

### <a name="exceptions"></a>Kivételek

- **Fiókadatok**: Adja meg, hogy az alkalmazás hozzáférhet-e a felhasználónév, képéhez és egyéb kapcsolattartási adataihoz.
- **Háttérben futó alkalmazások**: Adja meg, hogy az alkalmazás futtatható-e a háttérben.
- **Naptár**: Adja meg, hogy az alkalmazás hozzáférhet-e a naptárhoz.
- **Híváslista**: Adja meg, hogy az alkalmazás hozzáférhet-e a hívási előzményekhez.
- **Kamera**: Adja meg, hogy az alkalmazás hozzáférhet-e a kamerához.
- **Névjegyek**: Adja meg, hogy az alkalmazás hozzáférhet-e a névjegyekhez.
- **e-mailek**: Adja meg, hogy ez az alkalmazás hozzáférhessen-e-mailt.
- **Hely**: Adja meg, hogy az alkalmazás hozzáférhet-e a helyadatokhoz.
- **Üzenetküldési**: Határozza meg, hogy az alkalmazás olvashasson és küldhessen a szöveges vagy MMS-üzenetek.
- **Mikrofon**: Adja meg az alkalmazás használhatja-e a mikrofont.
- **Mozgásérzékelő**: Adja meg, hogy az alkalmazás hozzáférhet-e eszköz mozgáskövetési adataihoz.
- **Értesítések**: Határozza meg, hogy az alkalmazás hozzáférhet-e értesítéseket.
- **Telefonos**: Adja meg, hogy az alkalmazás hozzáférhet-e a telefonhoz.
- **Antennákhoz való**: Egyes alkalmazások rádiófrekvenciás (például Bluetooth) az eszköz küldhet és fogadhat adatokat, és ezeket a rádiófrekvenciás kapcsolatokat kapcsolhatja be és ki kell. Megadhatja, hogy az alkalmazás kezelheti-e ezeket az antennákat.
- **Feladatok**: Adja meg, hogy az alkalmazás hozzáférhet-e a feladatokhoz.
- **Megbízható eszközök**: Válassza ki, ha az alkalmazás használhat-e megbízható eszközöket. Megbízható eszközök lesznek a már csatlakoztatott hardver és a hardver, az eszköz. Például használja televízióra, projektorokat stb, megbízható eszközként.
- **Visszajelzés és diagnosztika**: Határozza meg, hogy az alkalmazás hozzáférhet-e diagnosztikai adatokat.
- **Szinkronizálás eszközökkel**: Válassza ki, ha az alkalmazás automatikusan megoszthatja és szinkronizálhat-e olyan vezeték nélküli eszközökkel, amelyek nincsenek kifejezetten párosítva az eszköz az adatokat.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="personalization"></a>Személyre szabás

Ezeket a beállításokat használja a [személyre szabása házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/personalization-csp), amely felsorolja a támogatott Windows-kiadások.

- **Asztali háttérkép URL-címe (csak asztali verzióban)** : Adja meg a Windows asztali háttérképeként használandó .jpg, .jpeg, vagy .png formátumú kép URL. A felhasználók nem módosíthatják a képet. Például írja be a következőt: `https://contoso.com/logo.png`.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="printer"></a>Nyomtató

- **Nyomtatók**: Hozzáadott helyi nyomtatók listája.
- **Alapértelmezett nyomtató**: Az alapértelmezett nyomtató beállítása.
- **Felhasználói hozzáférés új nyomtatók hozzáadásához**: Engedélyezi vagy letiltja a helyi nyomtatók használatának.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="privacy"></a>Személyes adatok védelme

Ezeket a beállításokat használja a [adatvédelmi szabályzat CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-privacy), amely felsorolja a támogatott Windows-kiadások.

- **Bemenet személyre szabása**: **Blokk** megakadályozza, hogy a szóbeli Diktálás és felvegye a Cortana és egyéb, a Microsoft felhőalapú beszédfelismerés használó alkalmazás használatával. Le van tiltva, és a felhasználók online beszédfelismerés beállításokkal nem lehet engedélyezni. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a felhasználóknak. Engedélyezi ezeket a szolgáltatásokat, ha a Microsoft a szolgáltatás javítására hangadatokat gyűjthet.
- **A társításra és adatvédelemre vonatkozó felhasználói beleegyezést kérő automatikus elfogadása**: Válasszon **engedélyezése** , a Windows képes automatikusan elfogadja a társítási és adatvédelmi beleegyezést kérő üzeneteket az alkalmazások futtatása közben. **Nincs konfigurálva** (alapértelmezett) megakadályozza, hogy a párosítási és adatvédelmi felhasználói jóváhagyás ablakának automatikus elfogadás alkalmazások megnyitásakor.
- **Felhasználói tevékenységek közzététele**: **Blokk** megakadályozza, hogy a megosztott élmények és a tevékenységi hírcsatorna a legutóbb használt erőforrások. **Nincs konfigurálva** (alapértelmezett) Ez a funkció lehetővé teszi, így az alkalmazások felhasználói tevékenységek teheti közzé.
- **Csak a helyi tevékenységek**: **Blokk** megakadályozza, hogy a megosztott élmények és a legutóbb használt erőforrások a feladatváltóban, csak a helyi tevékenység alapján. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ez a funkció.

Beállíthatja, hogy az eszközön lévő összes alkalmazás által elérhető információkat. Kivételeket is, meghatározni egy alkalmazásonkénti alapja az **alkalmazásonkénti adatvédelmi kivételek**.

Válassza ki **OK** a módosítások mentéséhez.

### <a name="exceptions"></a>Kivételek

- **Fiókadatok**: Adja meg, hogy az alkalmazás hozzáférhet-e a felhasználónév, képéhez és egyéb kapcsolattartási adataihoz.
- **Háttérben futó alkalmazások**: Adja meg, hogy az alkalmazás futtatható-e a háttérben.
- **Naptár**: Adja meg, hogy az alkalmazás hozzáférhet-e a naptárhoz.
- **Híváslista**: Adja meg, hogy az alkalmazás hozzáférhet-e a hívási előzményekhez.
- **Kamera**: Adja meg, hogy az alkalmazás hozzáférhet-e a kamerához.
- **Névjegyek**: Adja meg, hogy az alkalmazás hozzáférhet-e a névjegyekhez.
- **e-mailek**: Adja meg, hogy ez az alkalmazás hozzáférhessen-e-mailt.
- **Hely**: Adja meg, hogy az alkalmazás hozzáférhet-e a helyadatokhoz.
- **Üzenetküldési**: Határozza meg, hogy az alkalmazás olvashasson és küldhessen a szöveges vagy MMS-üzenetek.
- **Mikrofon**: Adja meg az alkalmazás használhatja-e a mikrofont.
- **Mozgásérzékelő**: Adja meg, hogy az alkalmazás hozzáférhet-e eszköz mozgáskövetési adataihoz.
- **Értesítések**: Határozza meg, hogy az alkalmazás hozzáférhet-e értesítéseket.
- **Telefonos**: Adja meg, hogy az alkalmazás hozzáférhet-e a telefonhoz.
- **Antennákhoz való**: Egyes alkalmazások rádiófrekvenciás (például Bluetooth) az eszköz küldhet és fogadhat adatokat, és ezeket a rádiófrekvenciás kapcsolatokat kapcsolhatja be és ki kell. Megadhatja, hogy az alkalmazás kezelheti-e ezeket az antennákat.
- **Feladatok**: Adja meg, hogy az alkalmazás hozzáférhet-e a feladatokhoz.
- **Megbízható eszközök**: Válassza ki, ha az alkalmazás használhat-e megbízható eszközöket. Megbízható eszközök lesznek a már csatlakoztatott hardver és a hardver, az eszköz az. Például használja televízióra, projektorokat stb, megbízható eszközként.
- **Visszajelzés és diagnosztika**: Válassza ki, ha az alkalmazás hozzáférhet-e diagnosztikai adatokat.
- **Szinkronizálás eszközökkel** – Megadhatja, hogy az alkalmazás oszthat-e meg és szinkronizálhat-e adatokat automatikusan olyan vezeték nélküli eszközökkel, amelyek nincsenek kifejezetten párosítva az adott PC-vel, táblagéppel vagy telefonnal.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="projection"></a>Kivetítés

Ezeket a beállításokat használja a [WirelessDisplay házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wirelessdisplay), amely felsorolja a támogatott Windows-kiadások.

- **Felhasználói bevitel vezeték nélküli kijelzők vevőegységeiről**: **Blokk** megakadályozza, hogy a felhasználói bevitel vezeték nélküli kijelzők vevőegységeiről. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a vezeték nélküli kijelző küldhet a billentyűzet, egér, tollal, és érintéses bevitel vissza az eszköz.
- **Kivetítés erre a számítógépre**: **Blokk** más eszközök megakadályozza, hogy az eszköz kivetítéshez keresése. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy az eszköz észlelhető, és az eszközön a zárolási képernyőn projektet is.
- **PIN-kód kérése párosításhoz**: Válasszon **megkövetelése** mindig kérése PIN-kód vetítőeszközhöz való csatlakozáskor. **Nincs konfigurálva** (alapértelmezett) nincs PIN-kódot az eszköz vetítőeszközhöz való párosítását.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="reporting-and-telemetry"></a>Jelentéskészítés és telemetria

- **Használati adatok megosztása**: Válassza ki a diagnosztikai adatok beküldése szintet. A választható lehetőségek:
  - **Nincs konfigurálva**: Nincs adat van osztva.
  - **Biztonsági**: Annak érdekében, hogy biztonságosabb, beleértve a kapcsolódó felhasználói élmény és a Telemetria összetevő beállításait, a kártevő-eltávolító eszköz és a Windows Defender adatait Windows szükséges információk.
  - **Alapszintű**: Alapszintű eszközinformáció, többek között a minőségi kapcsolatos adatokat, alkalmazás kompatibilitási, Alkalmazáshasználati adatokat és a biztonsági szint adatait.
  - **Továbbfejlesztett**: További elemzésekhez, beleértve: Windows, a Windows Server, a System Center és az alkalmazások használata, azok teljesítményét, speciális megbízhatósági adatok és az alapszintű és a biztonsági szintek adatait.
  - **Teljes**: Az összes azonosításához, és segít a problémák elhárításához szükséges adatokat, valamint a biztonság, az alapszintű és a bővített szint adatait.

  [System/AllowTelemetry CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry)

- **Böngészési adatok Microsoft 365 Analytics a Microsoft Edge küldése**: Ez a funkció használatához állítsa a **használati adatok megosztása** beállítások **bővített** vagy **teljes**. Ez a funkció szabályozza, mely adatok Microsoft Edge Microsoft 365 Analytics küld a vállalati eszközöknél a beállított kereskedelmi azonosítót. A választható lehetőségek:
  - **Nincs konfigurálva**: Az operációs rendszer alapértelmezett beállítás, amely előfordulhat, hogy ne küldjön böngészési előzmények adatokat használ.
  - **Csak az intranetes adatok küldése**: A rendszergazda az intranetes adatok előzményei küldése
  - **Csak internetes adatküldés**: Lehetővé teszi a rendszergazdák küldése az internet-adatok előzményei
  - **Intranetes és internetes adatküldés**: A rendszergazda az intranetes és internetes adatok előzményei küldése

  [Browser/ConfigureTelemetryForMicrosoft365Analytics CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configuretelemetryformicrosoft365analytics)

- **Telemetria proxykiszolgálója**: Adja meg a teljesen minősített tartománynevét (FQDN) vagy az összekapcsolt felhasználói élmények és Telemetria kérelmek, a Secure Sockets Layer (SSL)-kapcsolat használatával továbbítsa a proxykiszolgáló IP-címét. a következő formátumban: *kiszolgáló*:*port*. Ha az elnevezett proxy meghibásodik, vagy ha a proxy nem adott meg, ha e szabályzat engedélyezésével, az összekapcsolt felhasználói élmények és Telemetria-adatokat nem érkezik, és a helyi eszközön marad.

  Példák a formátumra:

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

  [System/TelemetryProxy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-telemetryproxy)

Válassza ki **OK** a módosítások mentéséhez.

## <a name="search"></a>Keresés

Ezeket a beállításokat használja a [keresni a házirend CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search), amely felsorolja a támogatott Windows-kiadások. 

- **Biztonságos keresés (csak mobil)** : Szabályozhatja, hogy Cortana hogyan szűrje a felnőtt tartalmat a keresési eredményekben. A választható lehetőségek:
  - **Felhasználó által definiált**: Lehetővé teszi a végfelhasználók számára, hogy a saját beállításait.
  - **A szigorú**: Felnőtt tartalom legmagasabb szűrése.
  - **Mérsékelt**: Közepes szintű, felnőtt tartalom szűrése. Érvényes keresési eredményeket nem szűri a rendszer.
- **Keresés webes eredményeinek megjelenítése**: Ha a beállítása **blokk**, a felhasználók nem tud keresni, és webes eredmények nem jelennek meg a keresés. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a felhasználók a weben való kereséshez, és az eredmények jelennek meg az eszközön.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="start"></a>Start

Ezeket a beállításokat használja a [indítsa el a szabályzat CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-start), amely felsorolja a támogatott Windows-kiadások.  

- **Start menü elrendezése**: Bírálja felül a kezdőképernyő alapértelmezett elrendezését, és testre szabhatja a start menüje olyan asztali eszközökön. A testre szabást, többek között a sorrendben, az alkalmazások szerepelnek, és további tartalmazó XML-fájl feltöltése. Felhasználók nem módosíthatják a start menü elrendezése, adja meg.
- **Rögzítheti a csempéket a webhelyek a Start menü**: Olyan képek importálását, amely a Windows Start menü asztali eszközök hivatkozásokként jelennek meg a Microsoft Edge-ből.
- **Levétele a tálcáról alkalmazások**: **Blokk** megakadályozza, hogy a felhasználó alkalmazásokat távolítson a tálcáról. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi a felhasználóknak levétele a tálcáról alkalmazásokat.
- **Gyors felhasználóváltás**: **Blokk** megakadályozza, hogy a Váltás egyidejűleg bejelentkezett kijelentkezés nélküli felhasználók között. **Nincs konfigurálva** (alapértelmezett) mutat be a **felhasználó váltása** felhasználói csempéjén.
- **Legtöbbet használt alkalmazások**: **Blokk** elrejti a start menü megjelenítése a leggyakrabban használt alkalmazásokat. A Gépház alkalmazásban is letiltja a megfelelő váltógombot. **Nincs konfigurálva** (alapértelmezett) jeleníti meg, hogy a legtöbbet használt alkalmazások.
- **Nemrég hozzáadott alkalmazások**: **Blokk** elrejti nemrégiben hozzáadott alkalmazások megjelenítése a start menüben. A Gépház alkalmazásban is letiltja a megfelelő váltógombot. **Nincs konfigurálva** (alapértelmezett) a start menüből a nemrégiben hozzáadott alkalmazásokat jeleníti meg.
- **Kezdőképernyő módja**: Válassza ki, hogyan jelenik meg a kezdőképernyőn. A választható lehetőségek:
  - **Felhasználó által definiált**: Nem kényszerített indítása méretét. Felhasználók állíthatja be a méretét.
  - **Teljes képernyős**: A kezdő nA celou obrazovku – méret kényszerítése.
  - **Nem teljes képernyős**: Kezdő mérete nem teljes képernyő kényszerítése.
- **A legutóbb megnyitott elemek a Gyorslistákban**: **Blokk** elrejti a legutóbbi gyorslistáiban nem jelenik meg a start menüben és tálcán. A Gépház alkalmazásban is letiltja a megfelelő váltógombot. **Nincs konfigurálva** (alapértelmezett) a legutóbb megnyitott elemek a jumplists jeleníti meg.
- **Alkalmazáslista**: Válassza ki, hogyan jelennek meg a minden alkalmazás lista. A választható lehetőségek:
  - **Felhasználó által definiált**: Nincs beállítás kötelező. Felhasználók kiválasztása az alkalmazáslistából hogyan jelenik meg az eszközön.
  - **Összecsukása**: Minden alkalmazás lista elrejtése.
  - **Összecsukása és letiltása a gépház alkalmazás**: Minden alkalmazás lista elrejtése, és tiltsa le **Alkalmazáslista megjelenítése a Start menüben** a gépház alkalmazásban.
  - **Eltávolítja, és letiltja a gépház alkalmazás**: Minden alkalmazás lista elrejtése, minden alkalmazás gomb eltávolítása és letiltása **Alkalmazáslista megjelenítése a Start menüben** a gépház alkalmazásban.
- **Főkapcsoló**: **Blokk** való megjelenítése a start menü főkapcsoló elrejtése. **Nincs konfigurálva** (alapértelmezett) főkapcsoló jeleníti meg.
- **Felhasználói csempe**: **Blokk** elrejti a start menü megjelenítése a felhasználói csempét. **Nincs konfigurálva** (alapértelmezett) jeleníti meg a felhasználói csempét, és beállítja a következő beállításokat:
  - **Zárolási**: **Blokk** elrejti a **zárolási** lehetőséget a start menü felhasználói csempéjén megjeleníthető. **Nincs konfigurálva** (alapértelmezett) mutat be a **zárolási** lehetőséget.
  - **Kijelentkezés**: **Blokk** elrejti a **Kijelentkezés** lehetőséget a start menü felhasználói csempéjén megjeleníthető. **Nincs konfigurálva** (alapértelmezett) mutat be a **Kijelentkezés** lehetőséget.
- **Állítsa le**: **Blokk** elrejti a **frissítés és leállítás** és **állítsa le** megjelenítése a start menü főkapcsoló elérhető beállításait. **Nincs konfigurálva** (alapértelmezett) bemutatja ezeket a beállításokat.
- **Alvó állapotba**: **Blokk** elrejti a **alvó** megjelenítése a start menü főkapcsoló lehetőségét. **Nincs konfigurálva** (alapértelmezett) jeleníti meg ezt a beállítást.
- **Hibernálásra**: **Blokk** elrejti a **hibernált** megjelenítése a start menü főkapcsoló lehetőségét. **Nincs konfigurálva** (alapértelmezett) jeleníti meg ezt a beállítást.
- **Váltás másik fiókra**: **Blokk** elrejti a **Váltás másik fiókra** csempére a felhasználók megjelenítése a start menüben. **Nincs konfigurálva** (alapértelmezett) jeleníti meg ezt a beállítást.
- **Újraindítási lehetőségek**:  **Blokk** elrejti a **frissítés és újraindítás** és **indítsa újra a** megjelenítése a start menü főkapcsoló elérhető beállításait. **Nincs konfigurálva** (alapértelmezett) bemutatja ezeket a beállításokat.
- **Dokumentumok a Start menüben**: A Windows Start menüjében a dokumentumok mappájának megjelenítése vagy elrejtése. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Nincs beállítás kötelező. Felhasználók megjelenítése vagy elrejtése a helyi válassza ki.
  - **Elrejtése**: A helyi rejtett, és letiltja a beállítást a gépház alkalmazásban.
  - **Megjelenítés**: A parancsikon jelenik meg, és letiltja a beállítást a gépház alkalmazásban.
- **Letöltések a Start menüben**: A Windows Start menü letöltések mappájának megjelenítése vagy elrejtése. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Nincs beállítás kötelező. Felhasználók megjelenítése vagy elrejtése a helyi válassza ki.
  - **Elrejtése**: A helyi rejtett, és letiltja a beállítást a gépház alkalmazásban.
  - **Megjelenítés**: A parancsikon jelenik meg, és letiltja a beállítást a gépház alkalmazásban.
- **Fájlkezelő a Start**: Fájlkezelő a Windows Start menü megjelenítése vagy elrejtése. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Nincs beállítás kötelező. Felhasználók megjelenítése vagy elrejtése a helyi válassza ki.
  - **Elrejtése**: A helyi rejtett, és letiltja a beállítást a gépház alkalmazásban.
  - **Megjelenítés**: A parancsikon jelenik meg, és letiltja a beállítást a gépház alkalmazásban.
- **Otthoni csoport a Start**: A Windows Start menü az otthoni csoport parancsikon megjelenítése vagy elrejtése. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Nincs beállítás kötelező. Felhasználók megjelenítése vagy elrejtése a helyi válassza ki.
  - **Elrejtése**: A helyi rejtett, és letiltja a beállítást a gépház alkalmazásban.
  - **Megjelenítés**: A parancsikon jelenik meg, és letiltja a beállítást a gépház alkalmazásban.
- **Zene a Start menüben**: A Windows Start menü zene mappájának megjelenítése vagy elrejtése. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Nincs beállítás kötelező. Felhasználók megjelenítése vagy elrejtése a helyi válassza ki.
  - **Elrejtése**: A helyi rejtett, és letiltja a beállítást a gépház alkalmazásban.
  - **Megjelenítés**: A parancsikon jelenik meg, és letiltja a beállítást a gépház alkalmazásban.
- **Hálózat a Start menüben**: A Windows Start menü hálózat megjelenítése vagy elrejtése. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Nincs beállítás kötelező. Felhasználók megjelenítése vagy elrejtése a helyi válassza ki.
  - **Elrejtése**: A helyi rejtett, és letiltja a beállítást a gépház alkalmazásban.
  - **Megjelenítés**: A parancsikon jelenik meg, és letiltja a beállítást a gépház alkalmazásban.
- **Személyes mappa a Start menüben**: A Windows Start menü személyes mappa megjelenítése vagy elrejtése. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Nincs beállítás kötelező. Felhasználók megjelenítése vagy elrejtése a helyi válassza ki.
  - **Elrejtése**: A helyi rejtett, és letiltja a beállítást a gépház alkalmazásban.
  - **Megjelenítés**: A parancsikon jelenik meg, és letiltja a beállítást a gépház alkalmazásban.
- **Képek a Start menüben**: A Windows Start menü képeket a mappa megjelenítése vagy elrejtése. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Nincs beállítás kötelező. Felhasználók megjelenítése vagy elrejtése a helyi válassza ki.
  - **Elrejtése**: A helyi rejtett, és letiltja a beállítást a gépház alkalmazásban.
  - **Megjelenítés**: A parancsikon jelenik meg, és letiltja a beállítást a gépház alkalmazásban.
- **Gépház a Start menüben**: A Windows Start menüjében a beállítások parancsikon megjelenítése vagy elrejtése. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Nincs beállítás kötelező. Felhasználók megjelenítése vagy elrejtése a helyi válassza ki.
  - **Elrejtése**: A helyi rejtett, és letiltja a beállítást a gépház alkalmazásban.
  - **Megjelenítés**: A parancsikon jelenik meg, és letiltja a beállítást a gépház alkalmazásban.
- **Videók a Start menüben**: A Windows Start menü videókat tartalmazó mappájának megjelenítése vagy elrejtése. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): Nincs beállítás kötelező. Felhasználók megjelenítése vagy elrejtése a helyi válassza ki.
  - **Elrejtése**: A helyi rejtett, és letiltja a beállítást a gépház alkalmazásban.
  - **Megjelenítés**: A parancsikon jelenik meg, és letiltja a beállítást a gépház alkalmazásban.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **A Microsoft Edge SmartScreen**: **Szükséges** kikapcsolja a Windows Defender SmartScreen, és megakadályozza, hogy a felhasználók ne tudják bekapcsolni a. **Nincs konfigurálva** SmartScreen bekapcsolása (alapértelmezett). Segít megvédeni a felhasználókat az esetleges fenyegetésektől és kikapcsolásával megakadályozhatja a felhasználókat.

  A Microsoft Edge (bekapcsolva) a Windows Defender SmartScreen felhasználók megvédeni a potenciális adathalászattal és a kártevő szoftverek használ.

  [Browser/AllowSmartScreen CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)

- **Rosszindulatú webhelyelérés**: **Blokk** megakadályozza, hogy a felhasználók figyelmen kívül hagyják a Windows Defender SmartScreen szűrő figyelmeztetéseit, és a hely webhelyelérés letiltja őket. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a felhasználók figyelmen kívül hagyhatja a figyelmeztetéseket, és lépjen tovább a webhelyre.

  [Browser/PreventSmartScreenPromptOverride CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

- **Ellenőrizetlen fájlletöltés**: **Blokk** megakadályozza, hogy a felhasználók figyelmen kívül hagyják a Windows Defender SmartScreen szűrő figyelmeztetéseit, és letiltja az ellenőrizetlen fájlok letöltésére. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a felhasználók figyelmen kívül hagyhatja a figyelmeztetéseket, és továbbra is a ellenőrizetlen fájlok letöltésére.

  [Browser/PreventSmartScreenPromptOverrideForFiles CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)

Válassza ki **OK** a módosítások mentéséhez.

## <a name="windows-spotlight"></a>Windows Reflektorfény

Ezeket a beállításokat használja a [házirend CSP élmény](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience), amely felsorolja a támogatott Windows-kiadások.

- **Windows reflektorfény**: **Blokk** kikapcsolja a Windows reflektorfény a zárolási képernyő, Windows-tippeket, a Microsoft fogyasztói funkciókat, és más kapcsolódó funkciókat. Ha a cél hálózati forgalmat eszközökről, állítsa ezt a beállítást **blokk**. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi a Windows reflektorfény funkciókat, és előfordulhat, hogy a végfelhasználók által szabályozható. Ha engedélyezve van, akkor is engedélyezheti vagy letilthatja a a következő beállításokat:

  - **Windows reflektorfény a zárolási képernyőn**: **Blokk** az eszköz zárolási képernyőjén információ megjelenítése a Windows reflektorfény leáll. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ez a funkció.
  - **Harmadik féltől származó javaslatok a Windows Reflektorfényben**: **Blokk** leállítja a Windows reflektorfény a nem Microsoft által közzétett tartalom javasol. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi az alkalmazás és a Windows reflektorfény funkciók – például a reflektorfény a zárolási képernyő, a partner szoftvergyártók tartalom javaslatok. a javasolt alkalmazások a Start menüben, és a Windows-tippeket.
  - **Fogyasztói funkciók**: **Blokk** kapcsolja ki, hogy általában csak, a fogyasztók számára kezdőképernyőn megjelenő javaslatok, például a tagsági értesítések, a box élmény alkalmazás telepítése utáni elavult, és átirányítási csempék. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ezeket a funkciókat.
  - **Windows-tippek**: **Blokk** letilthatja az előugró Windows-tippeket. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a Windows-tippek megjelenítése.
  - **Windows reflektorfény a Műveletközpontban**: **Blokk** megakadályozza, hogy a Windows reflektorfény értesítéseinek Műveletközpontban megjelenítése. **Nincs konfigurálva** (alapértelmezett) lehet, hogy értesítések megjelenítése, amelyek alkalmazásokat és szolgáltatásokat segítségével a felhasználók hatékonyságának növelése a Windows Műveletközpontban.
  - **Windows reflektorfény személyre szabása**: **Blokk** megakadályozza, hogy a Windows a diagnosztikai adatok felhasználásával testre szabja a felhasználó számára. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi diagnosztikai adatok felhasználhatók a személyre szabott javaslatokkal, tippek a Microsoft és a felhasználó igényei szerint testre szabni a Windows-ajánlatokat.
  - **Windows-üdvözlőképernyőn**: **Blokk** kapcsolja ki a Windows reflektorfény Windows üdvözlőprogramjának élmény funkciót. A Windows üdvözlőprogramjának nem jelennek meg, amikor a frissítések és a Windows és az alkalmazások módosítása. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi a Windows üdvözlőképernyőn új vagy frissített funkciók felhasználói információkat tekinthet meg.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="windows-defender-antivirus"></a>Windows Defender víruskereső

Ezeket a beállításokat használja a [defender szabályzat CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender), amely felsorolja a támogatott Windows-kiadások.

- **Valós idejű figyelés**: **Engedélyezése** megakadályozza, hogy a kártevők, kémprogramok és más nemkívánatos szoftverek valós idejű vizsgálatát. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ez a funkció.
- **Viselkedésfigyelés engedélyezése**: **Engedélyezése** megakadályozza, hogy a Defender ellenőrzés gyanús tevékenységekre utaló ismert mintákat keressen az eszközökön. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a Windows Defender viselkedésének figyelése.
- **Hálózatvizsgáló rendszer (NIS) hálózati**: NIS segít megvédeni az eszközöket a hálózatalapú biztonsági rések ellen. A Microsoft Endpoint Protection-központból származó ismert sebezhető pontok mintázatai alapján segít észlelni és blokkolni a rosszindulatú hálózati forgalmat.
- **Minden letöltött fájl vizsgálata**: Meghatározza, hogy a Defender az internetről letöltött összes fájlt megvizsgálja-e.
- **Microsoft-webböngészőkben betöltött szkriptek vizsgálata**: **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a Defender számára az Internet Explorer által használt parancsfájlok vizsgálatát. **Engedélyezése** megakadályozza, hogy ez az ellenőrzés.
- **Végfelhasználói hozzáférés a Defenderhez**: **Blokk** elrejti a végfelhasználók a Windows Defender kezelőfelülete. Minden értesítés, amely a Windows Defender is le lesznek tiltva. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a felhasználói hozzáférés a Windows Defender felhasználói felületre. Módosítás esetén a beállítás a felhasználó számítógépének következő újraindításakor lép érvénybe.
- **Aláírás-frissítési időköz (óra)** : Adja meg, hogy a Defender ellenőrzi a időköz keressen új aláírásfájlokat, 0 – 24-től. A választható lehetőségek:

  - **Nincs konfigurálva** (alapértelmezett)
  - **Ne legyen ellenőrzés**: Defender nem keressen új aláírásfájlokat.
  - **1-24**: `1` óránként ellenőrzi `2` két óránként keres `24` ellenőrzi, minden nap, és így tovább.
- **Fájl- és programtevékenység figyelése**: Engedélyezi a Defender számára az eszközökön zajló a fájl- és programtevékenységet.
- **Ennyi nap után törlődjenek karanténba zárt kártevők**: A követés folytatásához, adja meg, így manuálisan lehessen ellenőrizni a napok száma korábban érintett eszközök számára az ártalmatlanított kártevő szoftvereket. Ha a napok száma **0**, kártevő a karanténban marad, és nem törlődik automatikusan. Ha a beállítása `90`, karanténba helyezett elemeket a rendszer 90 napig tároljuk, és ezután eltávolítja.
- **CPU-használati korlát ellenőrzés közben**: Korlátozza a CPU, amelyek vizsgálatok használja, a **1** való **100**.
- **Archív fájlok ellenőrzése**: **Engedélyezése** megakadályozza, hogy a Defender vizsgálat archivált fájlok, például a Zip- vagy .cab-fájlok. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy ez az ellenőrzés.
- **A bejövő e-mailek vizsgálata**: **Engedélyezése** lehetővé teszi, hogy a Defender számára az eszközre érkező e-mailek. **Nincs konfigurálva** (alapértelmezett) megakadályozza, hogy e-mailek vizsgálatának.
- **Cserélhető adathordozók vizsgálata teljes vizsgálat során**: **Engedélyezése** megakadályozza, hogy a teljes vizsgálat a cserélhető meghajtók. **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a Defender számára a cserélhető meghajtók, például a pendrive vizsgálatát.
- **Csatlakoztatott hálózati meghajtók vizsgálata teljes vizsgálat során**: **Engedélyezése** lehetővé teszi, hogy a Defender számára a csatlakoztatott hálózati meghajtókon lévő fájlok vizsgálatát. **Nincs konfigurálva** (alapértelmezett) megakadályozza, hogy a teljes vizsgálat. Ha a meghajtó a fájlok írásvédettek, a Defender nem távolítható el a bennük talált kártevőket.
- **Hálózati mappákból megnyitott fájlok vizsgálata**: **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a Defender számára a megosztott hálózati meghajtókon, például a fájlok egy UNC elérési úton fájlok vizsgálatát. **Engedélyezése** megakadályozza, hogy ez az ellenőrzés. Ha a meghajtó a fájlok írásvédettek, a Defender nem távolítható el a bennük talált kártevőket.
- **A felhő védelmi**: **Nincs konfigurálva** (alapértelmezett) lehetővé teszi, hogy a Microsoft Active Protection Service olyan kártevőkről információkat kaphat a felügyelt eszközökről. **Engedélyezése** letiltja ezt a szolgáltatást.
- **Rákérdezés a mintaküldés előtt**: E vélhetően kártevő fájlokat, előfordulhat, hogy amelyeken további vizsgálat szükséges vezérlők a rendszer automatikusan elküldje a Microsoftnak. A választható lehetőségek:
  - **Nincs konfigurálva**
  - **Mindig legyen kérdés**
  - **Rákérdezés személyes adatok küldése előtt**
  - **Soha ne legyen adatküldés**
  - **Az összes adat elküldése rákérdezés nélkül**: Automatikusan adatokat küld

- **Napi Gyorsvizsgálat időpontja**: Válassza ki a napi Gyorsvizsgálat futtatása az órát. **Nincs konfigurálva** napi vizsgálat nem fut le. Ha azt szeretné, hogy további testreszabási, konfigurálja a **rendszervizsgálat típusa** beállítás.

  [Defender/ScheduleQuickScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime)

  > [!WARNING]
  > Ez a beállítás az Intune-ban az Azure Portalon lehet, hogy állapota sikertelen. Ez az a jelentési szolgáltatás hibája. Szaporodó viselkedését, és a hibaelhárítási, után a Intune-csoport megerősítette, hogy az állapot: sikeres ténylegesen. A jelentéskészítési hiba lesz kijavítva, egy soron következő kiadásban. Nem áll rendelkezésre a jelenlegi DRÓN ütemtervek módosítása esetén. Ez a funkció frissítéseit teszi közzé a [fejlesztés a Microsoft Intune](in-development.md).

- **Rendszervizsgálat típusa**: Ütemezett, beleértve a vizsgálata, és és az idő az ellenőrzési szintjét. A választható lehetőségek:
  - **Nincs konfigurálva**: Nem ütemezett az eszközön. A végfelhasználók manuálisan futtatható vizsgálatok szükséges vagy állásának saját eszközeiken.
  - **Tiltsa le**: Letiltja a bármely olyan rendszeren, az eszköz vizsgálatát. Válassza ezt a lehetőséget, ha egy víruskereső partnermegoldást, a eszközöket használ.
  - **Gyorsvizsgálat**: Úgy tűnik, közös helyen, ahol kártevők lehetnek regisztrálva, például a beállításkulcsok és az ismert indítási Windows-mappák.
    - **Ütemezett nap**: Válassza ki a vizsgálat futtatása a nap.
    - **Ütemezett időpont**: Válassza ki a órák futtatni a vizsgálatot.
  - **Teljes vizsgálat**: Úgy tűnik, közös helyen lévő ahol lehetséges, hogy kártevő regisztrálja, és szintén átvizsgálja a minden fájl és mappa az eszközön.
    - **Ütemezett nap**: Válassza ki a vizsgálat futtatása a nap.
    - **Ütemezett időpont**: Válassza ki a órák futtatni a vizsgálatot.

  Ez a beállítás ütközést idézhet elő a **napi Gyorsvizsgálat időpontja** beállítás. Néhány javaslat:

  - Napi Gyorsvizsgálat futtatása, konfigurálja a **napi Gyorsvizsgálat időpontja** beállítás.
  - Napi gyors vizsgálat és a egy teljes vizsgálat minden héten futtatásához, majd konfigurálja a **napi Gyorsvizsgálat időpontja**. Állítsa be **rendszervizsgálat típusa** , és az idő a teljes vizsgálat.
  - Ne konfigurálja a **napi Gyorsvizsgálat időpontja** beállítás egyidejűleg a a **rendszervizsgálat típusa** beállítása **Gyorsvizsgálat**. Ezek a beállítások ütközhetnek, és a vizsgálat nem fog futni.
  - Futtasson egy gyors vizsgálatot minden kedden reggel 6 Órakor, konfigurálja a **rendszervizsgálat típusa** beállítás.

  [Defender/ScanParameter CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter)  
  [Defender/ScheduleScanDay CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday)  
  [Defender/ScheduleScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime)

  > [!WARNING]
  > Ez a beállítás az Intune-ban az Azure Portalon lehet, hogy állapota sikertelen. Ez az a jelentési szolgáltatás hibája. Szaporodó viselkedését, és a hibaelhárítási, után a Intune-csoport megerősítette, hogy az állapot: sikeres ténylegesen. A jelentéskészítési hiba lesz kijavítva, egy soron következő kiadásban. Nem áll rendelkezésre a jelenlegi DRÓN ütemtervek módosítása esetén. Ez a funkció frissítéseit teszi közzé a [fejlesztés a Microsoft Intune](in-development.md).

- **Vélhetően nemkívánatos alkalmazások észlelése**: Válassza ki a védelmi szintet, ha a Windows észleli a vélhetően nemkívánatos alkalmazások. A választható lehetőségek:
  - **Nincs konfigurálva** (alapértelmezett): A Windows Defender potenciálisan nemkívánatos alkalmazások elleni védelem le van tiltva.
  - **Blokk**: A Windows Defender észleli a vélhetően nemkívánatos alkalmazások, és az észlelt elemek le vannak tiltva. Ezek az elemek megjelenítése az előzmények és más fenyegetések ellen.
  - **Naplózási**: A Windows Defender észleli a vélhetően nemkívánatos alkalmazások, de nem hajt végre semmilyen műveletet. Áttekintheti a Windows Defender igénybe ellen alkalmazásokkal kapcsolatos információkat. Például keresse meg a Windows Defender által létrehozott az megjelenítő eseményeket.

  Vélhetően nemkívánatos alkalmazásokkal kapcsolatos további információkért lásd: [észlelése és a blokk vélhetően nemkívánatos alkalmazások](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus).

- **Kártevők észlelése műveletek**: Válassza ki a műveleteket, amelyeket a Defender milyen észlelt fenyegetési szinteken: alacsony, közepes, magas és súlyos. Ha nem lehetséges, a Windows Defender úgy dönt, annak érdekében, hogy a fenyegetés kiküszöbölését követően a legjobb lehetőség. A választható lehetőségek:
  - **Tisztítás**
  - **Karantén**
  - **Eltávolítás**
  - **Engedélyezés**
  - **Felhasználó által definiált**
  - **Tiltás**

Válassza ki **OK** a módosítások mentéséhez.

### <a name="windows-defender-antivirus-exclusions"></a>Windows Defender víruskereső – kizárások

- **Fájlok és mappák kizárása a vizsgálatokból és a valós idejű védelem**: A kívánt fájlok és mappák – például **C:\Elérési_út** vagy **%ProgramFiles%\Elérési_út\fájlnév.exe** – felvétele a kivételek listájára. A rendszer a valós idejű és ütemezett vizsgálatok során nem vizsgálja ezeket a fájlokat és mappákat.
- **A vizsgálatokból és a valós idejű védelemből kizárandó fájlkiterjesztések**: Vegye fel a kívánt fájlkiterjesztéseket – például **jpg** vagy **txt** – a kivételek listájára. A valós idejű és ütemezett vizsgálatok során nem vizsgálja az ilyen kiterjesztésű fájlokat.
- **A vizsgálatokból és a valós idejű védelemből kizárandó folyamatok**: Vegye fel a kívánt típusú folyamatokat – **.exe**, **.com** vagy **.scr** – a kivételek listájára. A valós idejű és ütemezett vizsgálatok során nem vizsgálja ezeket a folyamatokat.

Válassza ki **OK** a módosítások mentéséhez.

## <a name="next-steps"></a>További lépések

További technikai részleteket az egyes beállításokról és a Windows támogatott kiadásairól a [Windows 10 szabályzatkonfigurációs szolgáltatói referenciájában](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) talál.

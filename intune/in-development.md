---
title: A fejlesztés – Microsoft Intune
titleSuffix: ''
description: Fejlesztés a Microsoft Intune-funkciók
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f7dd6f62cb53dd0cc373fb3f2ffa7d9434b135cd
ms.sourcegitcommit: 116ef72b9da4d114782d4b8dd9f57556c9b01511
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/01/2019
ms.locfileid: "67494245"
---
# <a name="in-development-for-microsoft-intune---july-2019"></a>A Microsoft Intune-hoz – július 2019 fejlesztés alatt

Segítség a készültségi és tervezési, ezen a lapon listák Intune felhasználói felület frissíti, és a szolgáltatásokat, fejlesztés alatt állnak, de még nem elérhető. Továbbá:

- Ha várhatóan tovább fogjuk, hogy intézkedjen módosítása előtt kell, tesszük közzé egy kiegészítő Office-Üzenetközpontban post.
- Ha egy szolgáltatás vagy előzetes elindul, éles környezetben, vagy általánosan elérhető, a szolgáltatás leírása áthelyezi ezt oldal ki, majd onnan az [Újdonságok oldalát](whats-new.md).
- Ezen a lapon, és a [Újdonságok oldalát](whats-new.md) rendszeresen frissül. További hírekért látogasson vissza.
- Tekintse meg a [M365 ütemterv](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) stratégiai le és ütemterveket.

> [!Note]
> Ezek az elemek tükrözik a Microsoft jelenlegi verziójával kapcsolatos elvárások hamarosan egy későbbi kiadásban az Intune funkcióival kapcsolatos. Dátumok és az egyes szolgáltatások változhatnak. Nem minden eleme fejlesztési rendelkeznie a szolgáltatás ezen az oldalon.

**RSS-hírcsatorna**: Értesítés küldése, amikor ezen a lapon frissül, másolása és beillesztése a következő URL-címet a hírcsatorna olvasóba szerint: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
#### App management
#### Device configuration
#### Device enrollment
#### Device management
#### Intune apps
#### Monitor and troubleshoot
#### Role-based access control
#### Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Alkalmazáskezelés


### <a name="customized-notifications-for-users-and-groups-------16766574-----"></a>Felhasználók és csoportok számára személyre szabott értesítések    <!-- 16766574   -->
Hamarosan fogja egyéni ad hoc leküldéses értesítéseket küldhessen a felhasználók számára az iOS- és Android-eszközök Intune-nal felügyelt vállalati portál alkalmazásból. Ezek az egyéni értesítések nem kötődnek, speciális Intune-funkciókat, és bármilyen célra van szüksége, beleértve az általános értesítést is szeretne küldeni bizonyos használható, vagy minden alkalmazott.  

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Értesítési tartalmat a szervezeti fiókok konfigurálása <!-- 2576686 -->
Az Intune alkalmazásvédelmi szabályzatai (alkalmazás) Android és IOS rendszerű eszközökön lehetővé teszi a vezérlő alkalmazás értesítési tartalmáról szervezeti fiókok esetében. Ez a funkció alkalmazások támogatásra van szükség, és nem lehet elérhető az összes engedélyezett alkalmazás alkalmazáshoz. Alkalmazással kapcsolatos további információkért lásd: [Mik azok az alkalmazásvédelmi szabályzatok?](app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Az Androidos munkahelyi profil reporting elérhető Google Play alkalmazás <!-- 3041956  -->
Az Android munkahelyi profilos eszközök alkalmazástelepítések érhető el megtekintheti az alkalmazás telepítési állapotát, valamint a felügyelt Google Play-alkalmazások telepített verzióját. További információkért lásd: [alkalmazásvédelmi szabályzatok figyelése](app-protection-policies-monitor.md), [kezelése Android munkahelyi profilos eszközök az Intune-nal](android-enterprise-overview.md) és [alkalmazástípus felügyelt Google Play](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Eszközök konfigurálása


### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Az IKEv2 VPN-profilok támogatása <!-- 1943438 -->
VPN-profilok létrehozása az IOS-es natív VPN-ügyfél az IKEv2 protokoll használatával képes lesz. IKEv2 rendszer az új kapcsolattípus **eszközkonfiguráció** > **profilok** > **profil létrehozása** > **iOS**  tartozó platform > **VPN** profiltípus > **beállítások**.

A VPN-profilok a natív VPN-ügyfél konfigurálásához. Így nem VPN ügyfél alkalmazások telepítésekor vagy leküldve a felügyelt eszközökre. A szolgáltatás használatához szükséges eszközök regisztrálhatók az Intune-ban (MDM-regisztráció).

Tekintse meg az aktuális VPN-beállításokat konfigurálhat, lépjen a [konfigurálása VPN-beállítások iOS-eszközökön a Microsoft Intune-ban](vpn-settings-ios.md).

A következőre vonatkozik: iOS

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Ha használja a "alkalmazhatósági szabályok" konfigurációs profilok létrehozása a Windows 10 rendszerű eszköz <!-- 2549910 -->
Windows 10-es eszközkonfigurációs profilok létrehozása (**eszközkonfiguráció** > **profilok** > **profil létrehozása**  >  **Windows 10-es** tartozó platform). Is elérheti, hozzon létre egy **alkalmazhatósági szabály** , a profil csak egy adott kiadását vagy egy adott verzió érvényes. Például hozzon létre egy profilt, amely lehetővé teszi egy BitLocker-beállítások. Miután hozzáadta a profil, használjon egy alkalmazhatósági szabályt, hogy a profil csak Windows 10 Enterprise rendszert futtató eszközökre vonatkozik.

Érintett kiadások: 
- Windows 10 és újabb

### <a name="administrative-templates-for-group-policy---------3510695---"></a>Csoportházirend-felügyeleti sablonok     <!--  3510695 -->
Felhőbeli eszközök biztonságának javítása érdekében, hogy felügyeleti sablonok, amely lehetővé teszi a Windows rendszerű számítógépekhez jelölje be a csoportházirend-beállítások konfigurálása az Intune-nal adunk ki.  Ezek a sablonok a szabályzat konfigurációs szolgáltató (CSP) használatával legfeljebb 2500 további beállításokat, az Office, a Windows és a onedrive vállalati verzió.

### <a name="manage-filevault-for-macos-------3858502--1210104-----"></a>MacOS-hez készült FileVault kezelése   <!--  3858502 + 1210104   -->
Fogja tudni használni az Intune endpoint protection eszközkonfigurációs profil FileVault kulcstitkosítási macOS-eszközök kezeléséhez. Ez magában foglalja a letéti megtekintését és a titkosítási kulcsok a vállalati eszközök. A végfelhasználók fogja tudni beolvasni ezeket a kulcsokat, a céges portál webhelyen keresztül.

### <a name="advanced-settings-for-windows-defender-firewall-------1311949-------"></a>Speciális beállítások a Windows Defender-tűzfal   <!--  1311949     -->
A nyilvános előzetes verzió meg fogjuk hamarosan, az ügyfeleken a Windows Defender az egyéni tűzfalszabályok kezelése az Intune-nal.  

### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769----"></a>Új configuration designer Android Enterprise-OEMConfig profil létrehozásakor <!-- 3712769  -->
Az Intune-ban létrehozhat egy eszközkonfigurációs profilt, amely egy OEMConfig alkalmazást használ (eszközkonfiguráció > profilok > profil létrehozása > Android enterprise tartozó platform > profiltípus OEMConfig). Ha így tesz, egy JSON-szerkesztő megnyílik egy sablon és értékeit módosíthatja. A frissítés tartalmazza a Configuration Designer jobb felhasználói élményt ágyazva az alkalmazást, beleértve a címét, leírását és további részleteket jeleníti meg. A JSON-szerkesztő továbbra is elérhető, és választja ki a Configuration Designer módosításokat jeleníti meg.

A jelenlegi beállítások megtekintéséhez lépjen a [használatát és OEMConfig Android Enterprise-eszközök felügyeletéhez](android-oem-configuration-overview.md).

Érintett kiadások: Vállalati Android


<!-- ***********************************************-->
## <a name="device-management"></a>Eszközkezelés

### <a name="improve-device-location---3855417---"></a>Eszköz helye javítása<!-- 3855417 -->
Egy eszköz a pontos koordinátáit nagyítás lesz a **eszköz megkeresése** művelet. Elveszett iOS-eszközök megkeresése kapcsolatos további információkért lásd: [elveszett iOS-eszközök Find](device-locate.md).

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Automatikus karbantartás időbeli korlát csak 30 napig konfigurálása <!--4231059  -->
Beállíthatja a automatikus karbantartás időkorlát mindössze 30 nap (nem a jelenlegi legfeljebb 90 nap) az utolsó bejelentkezés után lesz. Ehhez nyissa meg **Intune** > **eszközök** > **telepítő** > **tiszta mentése Eszközszabályok**.


<!-- ***********************************************-->
## <a name="security"></a>Biztonság

### <a name="import-and-export-security-baselines------3408610------------"></a>Importálási és exportálási biztonsági előírások    <!--3408610          -->  
A funkció exportálásáról és importálásáról a biztonsági előírások, így a testre szabást Önnel venni, és megoszthatja őket az Intune-környezetek között adunk hozzá.



<!-- ***********************************************-->
## <a name="notices"></a>Értesítések

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Lásd még:
A közelmúltbeli fejlesztésekkel kapcsolatban lásd: [Újdonságok a Microsoft Intune-ban](whats-new.md).



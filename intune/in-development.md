---
title: Fejlesztés – Microsoft Intune
titleSuffix: ''
description: A fejlesztés Microsoft Intune szolgáltatásai
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9b02deb529bd6a9bca882fecb3d55d9db513191
ms.sourcegitcommit: 614c4c36cfe544569db998e17e29feeaefbb7a2e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68427167"
---
# <a name="in-development-for-microsoft-intune---july-2019"></a>Fejlesztés a Microsoft Intune – július 2019

A készültség és a tervezés elősegítése érdekében ez az oldal felsorolja az Intune felhasználói felületének frissítéseit és a fejlesztés alatt álló, de még nem kiadott funkciókat. Továbbá:

- Ha várható, hogy a módosítás előtt végre kell hajtania a lépéseket, közzé kell tenni egy kiegészítő Office Message Center-bejegyzést.
- Ha egy szolgáltatás éles környezetben, előzetes verzióként vagy általánosan elérhetőként van elindítva, a szolgáltatás leírása kikerül ezen az oldalon, [](whats-new.md)és az Újdonságok oldalára kerül.
- Ez az oldal és az [új oldal](whats-new.md) rendszeresen frissül. További hírekért látogasson vissza.
- Tekintse meg a [M365 ütemtervet](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) a stratégiai termékekhez és a határidőkhöz.

> [!Note]
> Ezek az elemek tükrözik a Microsoft aktuális elvárásait az Intune-képességekről a jövőbeli kiadásokban. A dátumok és az egyes funkciók változhatnak. A fejlesztés nem minden eleme rendelkezik a funkció leírásával ezen a lapon.

**RSS-hírcsatorna**: Értesítést kaphat az oldal frissítésekor, ha a következő URL-címet másolja és beillesztette a hírcsatorna-olvasóba:`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

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

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Alkalmazás-értesítési tartalom konfigurálása a szervezeti fiókokhoz <!-- 2576686 -->
Az Intune app Protection-szabályzatok (alkalmazás) Android és iOS rendszerű eszközökön lehetővé teszik a szervezeti fiókok alkalmazás-értesítési tartalmának szabályozását. Ennek a funkciónak támogatásra van szüksége az alkalmazásoktól, és előfordulhat, hogy nem érhető el az összes alkalmazás-kompatibilis alkalmazáshoz. További információ az ALKALMAZÁSról: [Mi az az App Protection-szabályzat?](app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Elérhető Google Play-alkalmazások jelentéskészítése androidos munkahelyi profilokhoz <!-- 3041956  -->
Az androidos munkahelyi Profilos eszközökön elérhető alkalmazások telepítéséhez megtekintheti az alkalmazás telepítési állapotát, valamint a felügyelt Google Play-alkalmazások telepített verzióját. További információ: [az alkalmazás-védelmi szabályzatok figyelése](app-protection-policies-monitor.md), [androidos munkahelyi profilú eszközök kezelése az Intune](android-enterprise-overview.md) -nal és a [felügyelt Google Play-alkalmazás típusa](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Eszközök konfigurálása

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Az iOS rendszerhez készült IKEv2 VPN-profilok támogatása <!-- 1943438 -->
A IKEv2 protokoll használatával VPN-profilokat hozhat létre az iOS natív VPN-ügyfél számára. A IKEv2 egy új kapcsolattípus az **eszköz konfigurációs** > **profiljaiban** > **profil** > létrehozása**iOS** for platform > **VPN** a profil típusa > **Beállítások**.

Ezek a VPN-profilok a natív VPN-ügyfelet konfigurálja. Tehát a felügyelt eszközökre nincs telepítve vagy leküldve VPN-ügyfélalkalmazások. Ehhez a szolgáltatáshoz regisztrálni kell az eszközöket az Intune-ban (MDM-regisztráció).

Az aktuálisan konfigurálható VPN-beállítások megjelenítéséhez nyissa [meg a VPN-beállítások konfigurálása iOS](vpn-settings-ios.md)-eszközökön a Microsoft Intune.

A következőre vonatkozik: iOS


<!-- ***********************************************-->
## <a name="device-management"></a>Eszközkezelés

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Az eszköz automatikus törlési időkorlátjának beállítása 30 nap alatt <!--4231059  -->
Az automatikus eszköz kitakarítási időkorlátja az utolsó bejelentkezés után 30 nap (az aktuális korlát helyett a 90 nap) állítható be. Ehhez nyissa meg az **Intune** > -**eszközök** > **telepítő** > **eszközének karbantartási szabályait**.

<!-- ***********************************************-->
## <a name="security"></a>Biztonság

### <a name="import-and-export-security-baselines------3408610------------"></a>Biztonsági alaptervek importálása és exportálása    <!--3408610          -->  
Lehetőség van a biztonsági alapkonfigurációk exportálására és importálására, így Ön testreszabhatja és megoszthatja őket az Intune-környezetek között.


<!-- ***********************************************-->
## <a name="notices"></a>Értesítések

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Lásd még:
A közelmúltbeli fejlesztésekkel kapcsolatban lásd: [Újdonságok a Microsoft Intune-ban](whats-new.md).



---
title: Better Mobile Threat Defense-összekötő az Intune-hoz
titleSuffix: Intune on Azure
description: A Better Mobile Threat Defense-összekötő beállítása az Intune-hoz.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 55d4e327d99c8987e6fdc0dea0ac046dd0dc167e
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67883810"
---
# <a name="better-mobile-threat-defense-connector-with-intune"></a>Better Mobile Threat Defense-összekötő az Intune-hoz

A mobileszköz-hozzáférés a vállalati erőforrásokhoz a feltételes hozzáférés használatával szabályozható a jobb Mobile, a Mobile Threat Defense (MTD) által a Microsoft Intune-nal integrálható megoldás alapján. A kockázatfelmérés a Better Mobile alkalmazást futtató eszközökről gyűjtött telemetriai adatokon alapul.

A feltételes hozzáférési szabályzatokat az Intune-eszközök megfelelőségi házirendjein keresztül engedélyező, jobb mobileszköz-kockázatértékelés alapján konfigurálhatja, amellyel engedélyezheti vagy letilthatja a nem megfelelő eszközök hozzáférését a vállalati erőforrásokhoz az észlelt fenyegetések alapján.

## <a name="how-do-intune-and-better-mobile-help-protect-your-company-resources"></a>Hogyan segíti az Intune és a Better Mobile a vállalati erőforrások védelmét?

A Better Mobile alkalmazás mobileszközökön telepíthető és futtatható. Az alkalmazás rögzíti a fájlrendszer, a hálózati verem, valamint az eszközök és az alkalmazások telemetriai adatait, ha elérhetők, és továbbítja őket a Better Mobile felhőszolgáltatásnak, amely felméri, hogy milyen mértékben van kitéve az eszköz a mobil megoldásokat fenyegető veszélyeknek.

Az Intune eszközmegfelelőségi szabályzata tartalmaz egy, a Mobile Threat Defense-re vonatkozó szabályt, amely a Better Mobile kockázatfelmérésén alapul. Ha ez a szabály engedélyezve van, az Intune az engedélyezett szabályzat alapján értékeli az eszköz megfelelőségét. Amennyiben az eszköz nem megfelelőnek minősül, akkor megszűnik a felhasználók hozzáférése az olyan erőforrásokhoz, mint az Exchange Online és a SharePoint Online. A mobileszközeikre telepített Better Mobile segítséget nyújt a felhasználóknak abban, hogy elháríthassák a felmerülő problémákat, és újból hozzáférést nyerhessenek a vállalati erőforrásokhoz.

## <a name="sample-scenarios"></a>Mintaforgatókönyvek

Néhány gyakori helyzet:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Hozzáférés vezérlése rosszindulatú alkalmazások jelentette fenyegetés alapján

Ha az eszközön rosszindulatú alkalmazásokat, például kártevőket észlel a rendszer, a probléma megoldásáig az eszközön letilthatók az alábbi műveletek:

- Hozzáférés a vállalati e-mailekhez

- A vállalati fájlok szinkronizálása a OneDrive for Work alkalmazással

- Hozzáférés vállalati alkalmazásokhoz

**Letiltás kártékony alkalmazás észlelése esetén:**

![Az észlelt kártékony alkalmazásokat bemutató rendszerkép](./media/better_mobile_maliciousapps_blocked.png)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![A program kártevőt észlelt, hozzáférés megadva](./media/better_mobile_maliciousapps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Hozzáférés vezérlése hálózati fenyegetés alapján

Észleli a hálózat elleni támadásokat, például a **közbeékelődéses (man-in-the-middle)** támadásokat, és az eszközkockázat alapján biztosítja a Wi-Fi-hálózatok elérésének védelmét.

**Wi-Fi-s hálózati elérés letiltása:**

![Wi-Fi-s hálózati elérés letiltása](./media/better_mobile_network_wifi_blocked.png)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![A szervizeléshez megadott hozzáférést megjelenítő rendszerkép](./media/better_mobile_network_wifi_unblocked.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Hozzáférés vezérlése a SharePoint Online-hoz hálózati fenyegetés alapján

Észleli a hálózat elleni támadásokat, például a **közbeékelődéses (man-in-the-middle)** támadásokat és az eszköz jelentette kockázat alapján megakadályozza a vállalati fájlok szinkronizálását.

**A SharePoint Online letiltása hálózati fenyegetések észlelése esetén:**

![A SharePoint Online letiltása hálózati fenyegetések észlelése esetén](./media/better_mobile_network_spo_blocked.png)

**A fenyegetés kiküszöbölését követően a hozzáférés ismét biztosított:**

![A fenyegetés kiküszöbölését követően a SharePoint-hozzáférés ismét biztosított – példa](./media/better_mobile_network_spo_unblocked.png)

## <a name="supported-platforms"></a>Támogatott platformok

- **Android 4.1 és újabb verziók**

- **iOS 8.0 vagy újabb**

## <a name="prerequisites"></a>Előfeltételek

- Prémium szintű Azure Active Directory

- Microsoft Intune-előfizetés

- Better Mobile Threat Defense-előfizetés

  - További információkért lásd a [Better Mobile webhelyét](https://www.better.mobi/).

## <a name="next-steps"></a>További lépések

- [A Better Mobile és az Intune integrálása](better-mobile-mtd-connector-integration.md)

- [Better Mobile-alkalmazások beállítása](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Better Mobile eszközmegfelelőségi szabályzat létrehozása](mtd-device-compliance-policy-create.md)

- [A Better Mobile MTD-összekötő engedélyezése](mtd-connector-enable.md)

---
title: Az iOS-alkalmazások közötti adatátvitel kezelése
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan használhatja a Microsoft Intune mobilalkalmazás-kezelési házirendjeit az alkalmazások közötti adatátvitel kezeléséhez.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 91633aee190b5fb5bda9495f66d4503042aa6a80
ms.sourcegitcommit: 63b55e81122e5c15893302b109ae137c30855b55
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67713320"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>iOS-alkalmazások közti adatátvitel felügyelete a Microsoft Intune-ban

A vállalati adatok védelme érdekében korlátozza a fájlátvitelek csak a felügyelt alkalmazások. Az iOS-alkalmazásokat az alábbi módokon felügyelheti:

- Vállalati adatvesztés megelőzése alkalmazásvédelmi szabályzatot az alkalmazások, amelyek nevezzük konfigurálásával **szabályzat által felügyelt** alkalmazásokat. [Az Intune által kezelt alkalmazásvédelmi szabályzattal védhető alkalmazások listája](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

- Segítségével az alkalmazások telepítését és kezelését a **MDM-csatornával**, ami megköveteli, hogy egy mobileszköz-felügyeleti (MDM) megoldásban regisztrálni kívánt eszközöket. Az alkalmazások központi telepítése lehet **szabályzat által felügyelt** alkalmazások vagy más felügyelt alkalmazások.

Az iOS-eszközök **Megnyitási engedélyek felügyelete** szolgáltatásával a fájlátvitel az **MDM-csatornával** telepített alkalmazásokra korlátozható. Állítsa be *megnyitási engedélyek felügyelete* korlátozások a konfigurációs beállításokat, illetve telepítheti őket az MDM-megoldás használatával.  Amikor egy felhasználó telepíti az telepített alkalmazást, a rendszer alkalmazza a beállított korlátozásokat.

## <a name="use-app-protection-with-ios-apps"></a>Alkalmazásvédelem használata iOS-alkalmazások
Az alkalmazásvédelmi szabályzatok használata az IOS-es **megnyitási engedélyek felügyelete** funkció a vállalati adatok védelme érdekében a következő módon:

- **Alkalmazottak tulajdonában lévő, mobileszköz-kezelési megoldás által nem kezelt eszközök:** Az alkalmazásvédelmi szabályzat beállításait beállíthatja **///az alkalmazás átadhat adatokat csak a szabályzattal felügyelt alkalmazások**. A *Megnyitás a következőben* viselkedését egy házirend által kezelt alkalmazás megosztási lehetőségek, csak más szabályzattal felügyelt alkalmazások mutat be. Ha egy felhasználó próbál küldeni egy szabályzat által védett fájlt mellékletként a onedrive-ról a natív levelezőalkalmazást, a fájl nem olvasható.

- **Mobileszköz-kezelési megoldások által felügyelt eszközök**: Az Intune vagy külső MDM-megoldásban regisztrált eszközök esetén az alkalmazásvédelmi szabályzatokkal védett alkalmazások és az MDM-mel telepített egyéb felügyelt iOS-alkalmazások közötti adatmegosztás és határozza meg az Intune alkalmazás-szabályzatok az IOS-es **megnyitási engedélyek felügyelete** a szolgáltatás. Győződjön meg arról, hogy egy mobileszköz-kezelési megoldás segítségével központilag alkalmazásokat az Intune alkalmazásvédelmi szabályzatokat is tartoznak, konfigurálja a felhasználói UPN-beállítás a következő szakaszban leírtak szerint [konfigurálása felhasználói UPN-beállítás](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm). Adja meg, hogyan más alkalmazásokból való adatátvitel, engedélyezze az **Org küldhet adatokat más alkalmazásokból** majd válassza az Ön által választott értékét a megosztási. Adja meg, hogyan, az alkalmazás fogadhat adatokat más alkalmazásokból, engedélyezze az **fogadhat adatokat más alkalmazásokból** majd kapja az adatokat az Ön által választott értékét. Az alkalmazásadatok fogadására és megosztására vonatkozó további információért lásd az [Adatáthelyezési beállítások](app-protection-policy-settings-ios.md#data-protection) szakaszt.

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Az egyszerű felhasználónév beállításának konfigurálása a Microsoft Intune-hoz vagy külső EMM-megoldáshoz
Az egyszerű felhasználónév beállítását **kötelező** megadni olyan eszközök esetében, amelyek az Intune-nal vagy külső EMM-megoldással vannak kezelve. Az UPN-konfiguráció működik együtt az alkalmazás-alkalmazásvédelmi szabályzatok az Intune-ból telepít. Az alábbi eljárás egy általános folyamat az UPN-beállítás és az eredményül kapott felhasználói élmény konfigurálásával:

1. Az [Azure Portalon](https://portal.azure.com) [hozzon létre és osszon ki alkalmazásvédelmi szabályzatot](app-protection-policies.md) az iOS-nek. A vállalati igényeknek megfelelően konfigurálja a szabályzat beállításait, majd válassza ki azokat az iOS-es alkalmazásokat, amelyekre ennek a szabályzatnak kell vonatkoznia.

2. Az alkalmazások és az Intune vagy a külső MDM-megoldás az alábbi, általánosságban ismertetett lépések segítségével felügyelni kívánt e-mail-profil központi telepítése. Ez a tapasztalat is foglalkozik *1. példa*.

3. A felügyelt eszközök az alkalmazás a következő alkalmazáskonfigurációs beállításokkal telepítse:

      **kulcs** = IntuneMAMUPN, **érték** = <username@company.com>

      Példa: [‘IntuneMAMUPN’, ‘janellecraig@contoso.com’]
      
     > [!NOTE]
     > Az Intune-ban, az alkalmazás-konfigurációs házirend eszközregisztráció típusa értékre kell állítani **által kezelt eszköz**.
     > Ezenkívül az alkalmazás kell lennie, vagy az Intune vállalati portálról telepített (ha elérhetőként beállítása), vagy szükség szerint leküldeni az eszközre. 

4. Telepítse a regisztrált eszközökre a **Megnyitási engedélyek felügyelete** szabályzatot a az Intune vagy külső MDM-szolgáltató segítségével.


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>1\. példa: A rendszergazda teendői az Intune vagy harmadik fél mobileszköz-kezelési konzolon

1. Nyissa meg az Intune vagy a külső MDM-szolgáltató felügyeleti konzolját. Nyissa meg a konzolnak azt a szakaszát, ahol a regisztrált iOS-eszközökre érvényes alkalmazáskonfigurációs beállításokat adja meg.

2. Az alkalmazások konfigurációjának megadására szolgáló szakaszban adja meg a következő beállítást:

   **kulcs** = IntuneMAMUPN, **érték** = <username@company.com>

   A kulcs-érték pár pontos szintaxisa függ a külső MDM-szolgáltatótól. Az alábbi táblázat külső MDM-szolgáltató példákat és a pontos értékeket kell megadnia a kulcs/érték pár.

   |Külső MDM-szolgáltató| Konfigurációs kulcs | Érték típusa | Konfigurációs érték|
   | ------- | ---- | ---- | ---- |
   |Microsoft Intune| IntuneMAMUPN | Sztring | {{UserPrincipalName}}|
   |VMware AirWatch| IntuneMAMUPN | Sztring | {UserPrincipalName}|
   |MobileIron | IntuneMAMUPN | Sztring | ${userUPN} **vagy** ${userEmailAddress} |
   |A Citrix végpont kezelése | IntuneMAMUPN | Sztring | ${user.userprincipalname} |
   |ManageEngine Mobile Device Manager | IntuneMAMUPN | Sztring | %upn% |

> [!NOTE]  
> Az Outlook alkalmazás az IOS-es alkalmazáskonfigurációs szabályzat a "Using configuration designer" beállítással telepít a konfigurációs kulcs IntuneMAMUPN történik meg automatikusan a szabályzat a háttérben. További információt lásd: gyakori kérdések című [új Outlook IOS-es és Androidos konfigurációs házirend Alkalmazásélményről – általános alkalmazás-konfigurációs](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Outlook-for-iOS-and-Android-App-Configuration-Policy/ba-p/370481). 


### <a name="example-2-end-user-experience"></a>2\. példa: Végfelhasználói élmény

1. A felhasználó telepíti a Microsoft Word alkalmazást az eszközön.

2. A felhasználó elindítja a felügyelt natív levelezőalkalmazást az e mailjei eléréséhez.

3. A felhasználó megpróbál megnyitni egy dokumentumot egy natív levélből a Microsoft Word.

4. Amikor elindítja a Word alkalmazást, a rendszer kéri a felhasználót, hogy jelentkezzen be munkahelyi fiókjával. A felhasználó megadja a fióknak egyeznie kell a Microsoft Word alkalmazás számára az alkalmazás konfigurációs beállításaiban megadott fiók.

    > [!NOTE]
    > A felhasználó hozzáadhat és használhat személyes szóra. Az alkalmazásvédelmi szabályzatok nem érvényesek, ha a felhasználó Word használ a munkahelyi környezeten kívülre történő. 

5. Bejelentkezést követően alkalmazásvédelmi szabályzat beállításait a Word alkalmazásra vonatkoznak.

6. Mostantól az adatátvitel sikeres lesz, és a dokumentum egy vállalati identitással van megjelölve az alkalmazásban.  A rendszer munkahelyi környezetben kezeli az adatokat, és a házirend-beállítások a alkalmazni. 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Külső EMM-megoldásban megadott UPN-beállítás ellenőrzése

Miután a felhasználói UPN-beállítást, az iOS-alkalmazás megkapja és betartja-Intune alkalmazásvédelmi szabályzata lehetővé teszi érvényesítése.

Ha például a **alkalmazás PIN-kód megkövetelése** egyszerű tesztelése. Ha a házirend-beállítást egyenlő **Igen**, a felhasználó látja-e egy parancssort, állítsa be, vagy PIN-kód megadását, mielőtt hozzáférhetnek a vállalati adatokat.

Először [hozzon létre és osszon ki egy alkalmazásvédelmi szabályzatot](app-protection-policies.md) az iOS-alkalmazásnak. Alkalmazásvédelmi szabályzat teszteléséről további információkért lásd: [alkalmazásvédelmi szabályzatok ellenőrzése](app-protection-policies-validate.md).


### <a name="see-also"></a>Lásd még:
[Mi az Intune alkalmazásvédelmi szabályzat?](app-protection-policy.md)

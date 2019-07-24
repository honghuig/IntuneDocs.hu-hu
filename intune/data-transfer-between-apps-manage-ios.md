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
ms.openlocfilehash: 9a1e370b65d8bfd7e61562347323bf1455dfe55b
ms.sourcegitcommit: bd09decb754a832574d7f7375bad0186a22a15ab
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68354298"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>iOS-alkalmazások közti adatátvitel felügyelete a Microsoft Intune-ban

A vállalati adatai védelme érdekében korlátozza a fájlátvitelt csak a felügyelt alkalmazásokra. Az iOS-alkalmazásokat az alábbi módokon felügyelheti:

- A vállalat adatvesztésének megakadályozása az alkalmazásokra vonatkozó adatvédelmi szabályzat konfigurálásával, amelyet  a szabályzattal felügyelt alkalmazások hívására hívunk. [Az Intune által kezelt alkalmazásvédelmi szabályzattal védhető alkalmazások listája](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

- Alkalmazások üzembe helyezése és kezelése a **Mdm**-csatornán keresztül, amely az eszközök regisztrálását igényli mobileszköz-kezelési (Mdm) megoldásban. Az Ön által telepített alkalmazások **házirend által felügyelt** alkalmazások vagy más felügyelt alkalmazások lehetnek.

Az iOS-eszközök **Megnyitási engedélyek felügyelete** szolgáltatásával a fájlátvitel az **MDM-csatornával** telepített alkalmazásokra korlátozható. Állítsa be a *Megnyitás a felügyeleti* korlátozásokban beállítást a konfigurációs beállításokban, majd telepítse őket a Mdm-megoldás használatával.  Amikor egy felhasználó telepíti az üzembe helyezett alkalmazást, a rendszer alkalmazza a megadott korlátozásokat.

## <a name="use-app-protection-with-ios-apps"></a>Az App Protection használata iOS-alkalmazásokkal
A vállalati adatvédelmet a következő módokon végezheti el az alkalmazás-védelmi házirendek és az iOS **megnyitási felügyeleti** funkciójának használatával:

- **Az alkalmazottak tulajdonában lévő eszközök, amelyeket nem egyetlen MDM-megoldás felügyel:** Beállíthatja, hogy az alkalmazás **csak a szabályzat által felügyelt alkalmazások számára engedélyezze**az alkalmazások adatátvitelét. A  házirend által felügyelt alkalmazásokban a megnyitási viselkedés csak más szabályzat által felügyelt alkalmazásokat jelenít meg megosztási lehetőségként. Ha a felhasználó egy, a natív posta alkalmazásban található OneDrive mellékletként próbál meg egy szabályzattal védett fájlt küldeni, a fájl nem olvasható.

- **Mdm-megoldások által felügyelt eszközök**: Az Intune-ban vagy harmadik féltől származó MDM-megoldásokban regisztrált eszközökön az alkalmazások közötti adatmegosztást az alkalmazás-védelmi szabályzatokkal és az MDM-n keresztül telepített egyéb felügyelt iOS-alkalmazásokkal az Intune APP policys és az iOS **Open in Management** szolgáltatás vezérli. Annak biztosításához, hogy a MDM-megoldással telepített alkalmazások is társítva legyenek az Intune app Protection-szabályzatokhoz, konfigurálja a felhasználói UPN-beállítást a következő szakaszban leírtak szerint, [konfigurálja a felhasználói UPN-beállítást](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm). Annak megadásához, hogy hogyan kívánja engedélyezni a más alkalmazásoknak való adatátvitelt, engedélyezze a **szervezeti adatok más alkalmazásokba való küldését** , majd válassza ki az előnyben részesített megosztási szintet. Annak megadásához, hogy az alkalmazások hogyan fogadhatnak más alkalmazásokból származó adatfogadást, engedélyezze a **más alkalmazásokból** érkező adatok fogadását, majd válassza ki az adatok fogadásának kívánt szintjét. Az alkalmazásadatok fogadására és megosztására vonatkozó további információért lásd az [Adatáthelyezési beállítások](app-protection-policy-settings-ios.md#data-protection) szakaszt.

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Az egyszerű felhasználónév beállításának konfigurálása a Microsoft Intune-hoz vagy külső EMM-megoldáshoz
Az egyszerű felhasználónév beállítását **kötelező** megadni olyan eszközök esetében, amelyek az Intune-nal vagy külső EMM-megoldással vannak kezelve. Az UPN-konfiguráció az Intune-ból üzembe helyezett alkalmazás-védelmi házirendekkel működik. Az alábbi eljárás az UPN-beállítás és az eredményül kapott felhasználói élmény konfigurálásának általános folyamata:

1. Az [Azure Portalon](https://portal.azure.com) [hozzon létre és osszon ki alkalmazásvédelmi szabályzatot](app-protection-policies.md) az iOS-nek. A vállalati igényeknek megfelelően konfigurálja a szabályzat beállításait, majd válassza ki azokat az iOS-es alkalmazásokat, amelyekre ennek a szabályzatnak kell vonatkoznia.

2. Telepítse az Intune-ban vagy a külső MDM-megoldáson keresztül felügyelni kívánt alkalmazásokat és e-mail-profilt az alábbi általánosított lépések segítségével. Ezt a folyamatot az 1. *példa*is tárgyalja.

3. Telepítse az alkalmazást a következő alkalmazás-konfigurációs beállításokkal a felügyelt eszközre:

      **kulcs** = IntuneMAMUPN, **érték** = <username@company.com>

      Példa: [‘IntuneMAMUPN’, ‘janellecraig@contoso.com’]
      
     > [!NOTE]
     > Az Intune-ban az alkalmazás-konfigurációs házirend beléptetési típusát **felügyelt eszközökre**kell beállítani.
     > Emellett az alkalmazást telepíteni kell a Intune Céges portálról (ha az elérhetőként van beállítva), vagy az eszköznek megfelelően leküldve. 

4. Telepítse a regisztrált eszközökre a **Megnyitási engedélyek felügyelete** szabályzatot a az Intune vagy külső MDM-szolgáltató segítségével.


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>1\. példa: Rendszergazdai élmény az Intune-ban vagy külső MDM-konzolon

1. Nyissa meg az Intune vagy a külső MDM-szolgáltató felügyeleti konzolját. Nyissa meg a konzolnak azt a szakaszát, ahol a regisztrált iOS-eszközökre érvényes alkalmazáskonfigurációs beállításokat adja meg.

2. Az alkalmazások konfigurációjának megadására szolgáló szakaszban adja meg a következő beállítást:

   **kulcs** = IntuneMAMUPN, **érték** = <username@company.com>

   A kulcs-érték pár pontos szintaxisa függ a külső MDM-szolgáltatótól. A következő táblázat példákat mutat be a harmadik féltől származó MDM-szolgáltatókra, valamint a kulcs/érték párokhoz megadott pontos értékekre.

   |Külső MDM-szolgáltató| Konfigurációs kulcs | Érték típusa | Konfigurációs érték|
   | ------- | ---- | ---- | ---- |
   |Microsoft Intune| IntuneMAMUPN | Sztring | {{UserPrincipalName}}|
   |VMware AirWatch| IntuneMAMUPN | Karakterlánc | {UserPrincipalName}|
   |MobileIron | IntuneMAMUPN | Sztring | ${userUPN} **vagy** ${userEmailAddress} |
   |Citrix Endpoint Management | IntuneMAMUPN | Sztring | $ {User. userPrincipalName} |
   |ManageEngine Mobile Device Manager | IntuneMAMUPN | Sztring | %upn% |

> [!NOTE]  
> Az iOS rendszerhez készült Outlook alkalmazás esetén, ha az alkalmazás-konfigurációs szabályzatot "a Configuration Designer használata" beállítással telepíti, a IntuneMAMUPN konfigurációs kulcsát a rendszer automatikusan beállítja a háttérben a házirendhez. További részletek az [iOS-és Android-alkalmazások konfigurációs házirendje – általános alkalmazás-konfiguráció – az új Outlook for iOS és az Android alkalmazás konfigurációs szabályzata –](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Outlook-for-iOS-and-Android-App-Configuration-Policy/ba-p/370481)gyakori kérdések 


### <a name="example-2-end-user-experience"></a>2\. példa: Végfelhasználói élmény

1. A felhasználó egy eszközön telepíti a Microsoft Word alkalmazást.

2. A felhasználó elindítja a felügyelt natív e-mail-alkalmazást az e-mailek eléréséhez.

3. A felhasználó megpróbál megnyitni egy dokumentumot a natív levelekből a Microsoft Wordben.

4. A Word alkalmazás indításakor a rendszer felszólítja a felhasználót, hogy jelentkezzen be a munkahelyi fiókjával. A felhasználó által megadott fióknak meg kell egyeznie a Microsoft Word alkalmazás alkalmazás-konfigurációs beállításaiban megadott fiókkal.

    > [!NOTE]
    > A felhasználók hozzáadhatnak és használhatnak személyes fiókjaikat a Word használatával. Az alkalmazás-védelmi szabályzatok nem érvényesek, ha a felhasználó a Word alkalmazást a munkahelyi környezeten kívül használja. 

5. A bejelentkezést követően az alkalmazás védelmi házirend-beállításai a Word alkalmazásra vonatkoznak.

6. Mostantól az adatátvitel sikeres lesz, és a dokumentum egy vállalati identitással van megjelölve az alkalmazásban.  Az adatkezelés munkahelyi kontextusban történik, és a házirend-beállítások érvényesek. 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Külső EMM-megoldásban megadott UPN-beállítás ellenőrzése

A felhasználói UPN-beállítás konfigurálása után ellenőrizze, hogy az iOS-alkalmazás képes-e az Intune app Protection-szabályzat fogadására és betartására.

Az **alkalmazás PIN** -kódjának megkövetelése házirend-beállítás például egyszerűen tesztelhető. Ha a házirend-beállítás értéke **Igen**, a felhasználónak meg kell jelennie a PIN-kód beállításához vagy megadásához, mielőtt hozzá tudnak férni a vállalati információkhoz.

Először [hozzon létre és osszon ki egy alkalmazásvédelmi szabályzatot](app-protection-policies.md) az iOS-alkalmazásnak. Az alkalmazás-védelmi szabályzat tesztelésével kapcsolatos további információkért lásd: az [alkalmazás-védelmi házirendek érvényesítése](app-protection-policies-validate.md).


## <a name="see-also"></a>Lásd még:
[Mi az Intune alkalmazásvédelmi szabályzat?](app-protection-policy.md)

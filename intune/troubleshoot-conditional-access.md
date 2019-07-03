---
title: A feltételes hozzáférés hibaelhárítása
titleSuffix: Microsoft Intune
description: Mi a teendő, ha a felhasználók nem tudnak hozzáférni az erőforrásokhoz az Intune feltételes hozzáférésével.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/25/2018
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5fa59501-5f33-46b7-a5f5-75eeae9f1209
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e8ebc708f76ed1f55f512edda75206d3ed5890a0
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67530730"
---
# <a name="troubleshoot-conditional-access"></a>A feltételes hozzáférés hibaelhárítása

Hozzáférés az Office 365-szolgáltatásokhoz, például az Exchange Online, SharePoint online-hoz, a Skype vállalati Online védelme is, a helyszínen és egyéb szolgáltatások Exchange Intune és a feltételes hozzáférés használatával. Ez a funkció lehetővé teszi, hogy ellenőrizze, hogy a vállalati erőforrásokhoz való hozzáférést az Intune-ban regisztrált eszközökre korlátozva, és megfeleljenek a feltételes hozzáférési szabályokat állíthat be az Intune felügyeleti konzol vagy az Azure Active Directory. Ez a cikk azt ismerteti, mi a teendő, ha a felhasználók nem tudnak hozzáférni az erőforrásokhoz a feltételes hozzáférés védett, vagy ha a felhasználók hozzáférhetnek a védett erőforrásokhoz, de le kell tiltani.

## <a name="requirements-for-conditional-access"></a>Feltételes hozzáférés követelményeinek

Az alábbi követelményeknek kell teljesülniük a feltételes hozzáférés működjön:

- Az eszközt regisztrálni kell az Intune-ban, és annak kell felügyelnie.
- A felhasználónak és az eszköznek is meg kell felelnie az Intune-ban hozzájuk rendelt megfelelőségi szabályzatoknak.
- Alapértelmezés szerint lennie kell egy, a felhasználóhoz hozzárendelt eszközmegfelelőségi szabályzatnak. Ez attól függhet, hogyan van konfigurálva **A hozzárendelt megfelelőségi szabályzat nélküli eszközök megjelölése a következőként** beállítás az Intune rendszergazdai portáljának **Eszközmegfelelőség** > **Megfelelőségi szabályzat beállításai** szakaszában.
- Az eszközön aktiválni kell az Exchange ActiveSync protokollt, ha a felhasználó nem az Outlookot, hanem az eszköz natív levelezőprogramját használja. iOS-, Windows Phone- és Android-eszközök esetében ez automatikusan történik.
- Az Intune Exchange Connectort megfelelően konfigurálni kell. További információkért lásd az [Az Exchange Connector hibaelhárítása a Microsoft Intune-ban](troubleshoot-exchange-connector.md) című ismertetőt.

Az egyes eszközökre vonatkozó feltételek megtekinthetők az Azure Portalon, valamint a Mobileszközkészlet-jelentésben.

## <a name="devices-appear-compliant-but-users-are-still-blocked"></a>Az eszközök megfelelőként jelennek meg, de a felhasználók továbbra is le vannak tiltva

- A Knoxszal nem rendelkező Android-eszközök nem kapnak hozzáférési jogosultságot, amíg a felhasználó rá nem kattint a **Kezdés most** hivatkozásra a kapott karantén-e-mailben. Ez akkor is érvényes, ha a felhasználó már regisztrálva van az Intune-ban. Ha a felhasználó nem kapja meg a hivatkozást tartalmazó e-mailt a telefonján, akkor használhatja a számítógépét az e-mail elérésére és az eszközének az e-mail-fiókjába való továbbításra.
- Az eszköz első regisztrálásakor a megfelelőségi adatok rögzítése az eszközhöz időbe telhet. Várjon néhány percet, és próbálkozzon újra.
- iOS-eszközöknél egy meglévő e-mail-profil megakadályozhatja az Intune-rendszergazda által létrehozott, a felhasználóhoz rendelt e-mail-profil központi telepítését, ezáltal nem megfelelővé téve az eszközt. Ebben a forgatókönyvben a Céges portál alkalmazás tájékoztatja a felhasználót, hogy a manuálisan beállított e-mail-profil nem megfelelő, és megkéri, hogy távolítsa el a profilt. Miután a felhasználó eltávolította a meglévő e-mail-profilt, az Intune-ban készített e-mail-profil központi telepítése sikerülni fog. A probléma megelőzése érdekében kérje meg a felhasználókat, hogy regisztráció előtt távolítsanak el minden meglévő e-mail-profilt az eszközről.
- Az eszközök esetében előfordulhat, hogy elakadnak a megfelelőség-ellenőrzési állapotban, és megakadályozzák, hogy a felhasználó újabb bejelentkezést kezdeményezzen. Ha egy eszköz ebben az állapotban van, megpróbálkozhat a következőkkel:
  - Győződjön meg róla, hogy az eszköz a Céges portál alkalmazás legújabb verzióját használja.
  - Indítsa újra az eszközt.
  - Tekintse meg, ha a probléma fennáll-e tartósan más hálózatokon (pl. mobil, Wi-Fi stb.).

  Ha a probléma nem szűnik meg, lépjen kapcsolatba a Microsoft ügyfélszolgálatával a [támogatás kérése a Microsoft Intune-hoz](get-support.md) szakaszban leírtak szerint.
- Előfordulhat, hogy bizonyos androidos eszközök titkosítottnak tűnnek, de a Céges portál alkalmazás nem titkosítottként ismeri fel és nem megfelelőként jelöli meg azokat. Ebben a forgatókönyvben a felhasználó számára a Céges portál alkalmazás értesítést jelenít meg, kérve egy indítási PIN-kód beállítását az eszközhöz. Koppintson az értesítésre, és a meglévő PIN-kód vagy a jelszó ellenőrzése után válassza a **Require PIN to start device** (PIN-kód kérése az eszköz indításához) beállítást a **Secure start-up** (Biztonságos indítás) képernyőn, majd koppintson a Céges portál alkalmazásban a **Megfelelőség ellenőrzése** gombra az eszköznél. Az eszközt ettől kezdve titkosítottként kell, hogy észlelje a program. 
  > [!NOTE]
  > Egyes eszközgyártók alapértelmezett PIN-kód használatával titkosítják eszközeiket a felhasználó által megadott PIN-kód helyett. Az Intune az alapértelmezett PIN-kóddal titkosított eszközöket nem tekinti biztonságosnak, és ezeket nem megfelelőként jelöli meg, amíg a felhasználó létre nem hoz egy új, nem alapértelmezett PIN-kódot.
- A rendszer a regisztrált és megfelelő Android-eszközöket is letilthatja, és kaphatnak karanténba helyezésről szóló értesítést, amikor először próbálják elérni a vállalati erőforrásokat. Ha ez történik, győződjön meg róla, hogy a Céges portál alkalmazás nem fut, majd a kiértékelés aktiválásához kattintson a karantén-e-mailben a **Kezdés most** hivatkozásra. Ez csak kell elvégezni, amikor először engedélyezve a feltételes hozzáférés.

## <a name="devices-are-blocked-and-no-quarantine-email-is-received"></a>Az eszközök le vannak tiltva, és nem érkezett karanténba helyezési e-mail

- Ellenőrizze, hogy az eszköz az Intune felügyeleti konzolján Exchange ActiveSync-eszközként jelenik-e meg. Ha nem, akkor valószínű, hogy az eszköz felderítése sikertelen, feltehetően egy Exchange Connectorral kapcsolatos probléma miatt. További információért tekintse át [A helyszíni Intune Exchange Connector hibaelhárítása](troubleshoot-exchange-connector.md) szakaszt.
- Mielőtt az Exchange Connector zárolná az eszközt, aktiválási (karantén) e-mailt küld. Ha az eszköz offline állapotban van, előfordulhat, hogy nem kapja meg az aktiválási e-mailt. 
- Ellenőrizze, hogy az eszköz levelező alkalmazásában az e-mailek fogadásának beállításaként a **Leküldéses** van-e megadva a **Lekérdezéses** helyett. Ha igen, ez okozhatja, hogy a felhasználó nem kapja meg az e-mailt. Váltson **Lekérdezéses** módra, és ellenőrizze, hogy az eszköz megkapja-e az e-mailt.

## <a name="devices-are-noncompliant-but-users-are-not-blocked"></a>Az eszközök nem megfelelőek, de a felhasználók nincsenek letiltva

- Windows rendszerű számítógépekhez a feltételes hozzáférés csak letiltja a a natív e-mail alkalmazás, Office 2013 Modern hitelesítés vagy az Office 2016. Az Outlook vagy a Windows rendszerű számítógépek összes levelezőalkalmazásait blokkoló korábbi verzióiban szükség AAD Eszközregisztráció és az Active Directory összevonási szolgáltatások (AD FS) konfigurációk megfelelően [az Azure Active Directory beállítása a SharePoint Online és Exchange online-hoz Feltételes hozzáférés](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication). 
- Ha egy kiválasztott eszköz összes adatát törli vagy kivonja azt az Intune felügyelete alól, a kivonást követően még több órán keresztül rendelkezhet hozzáféréssel. Ennek az az oka, hogy az Exchange hat órán át gyorsítótárazza a hozzáférési jogosultságokat. Ebben az esetben érdemes más adatvédelmi megoldást keresnie a kivont eszközökre.
- Surface Hub-eszközök támogatják a feltételes hozzáférést; a megfelelőségi szabályzat azonban eszközcsoportokra (nem a felhasználói csoportok) megfelelő tesztelési kell telepítenie.
- A megfelelőségi szabályzatokról és a feltételes hozzáférési szabályzatok hozzárendeléseinek ellenőrzése. Ha a felhasználó nem olyan csoportba tartozik, amelyhez hozzá vannak rendelve a szabályzatok, vagy ha kizárt csoportban van, akkor a felhasználó nem lesz letiltva. A rendszer csak a hozzárendelt csoportban lévő felhasználók eszközeinek megfelelőségét ellenőrzi.

## <a name="noncompliant-device-is-not-blocked"></a>A nem megfelelő eszköz nincs letiltva

Ha olyan eszközzel találkozik, amely nem megfelelő, mégis rendelkezik hozzáféréssel, hajtsa végre a következőket.
- Tekintse át a cél- és kizárási csoportokat. Ha a felhasználó nem szerepel a megfelelő cél- vagy kizárási csoportban, akkor nem tiltható le. A rendszer csak a célcsoportban lévő felhasználók eszközeinek megfelelőségét ellenőrzi.
- Gondoskodjon az eszköz felderítéséről. Az Exchange Connector egy Exchange 2010-es CAS-kiszolgálóra mutat, a felhasználó pedig egy Exchange 2013-kiszolgálón van? Ebben az esetben, ha az alapértelmezett Exchange-szabály az Engedélyezés, az Intune nem észleli az eszköz kapcsolatát az Exchange szolgáltatással, még akkor sem, ha a felhasználó a célcsoportban van.
- Ellenőrizze az eszköz meglétét/hozzáférési állapotát az Exchange-ben:
  - A PowerShell-parancsmag használatával postaládához tartozó valamennyi mobileszköz listáját: "Get-ActiveSyncDeviceStatistics -mailbox mbx'. Ha az eszköz nem szerepel a listán, akkor nem fér hozzá az Exchange-hez.
  - Ha az eszköz szerepel a listán, használja a Get-CASmailbox-identity:’upn’ | fl parancsmagot az eszköz hozzáférési állapota részletes információinak lekérdezéséhez, majd az információkat adja meg a Microsoft támogatási szolgálatának.

## <a name="next-steps"></a>További lépések
Ha ezek az információk nem segítettek, akkor [Támogatást kérhet a Microsoft Intune-hoz](get-support.md).

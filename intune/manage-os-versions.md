---
title: Operációsrendszer-verziók kezelése a Microsoft Intune-nal
titleSuffix: Microsoft Intune
description: Megtudhatja, hogyan kezelhetők a különböző platformokon futó operációsrendszer-verziók a Microsoft Intune-nal.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 361ef17b-1ee0-4879-b7b1-d678b0787f5a
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: bc785e7f714320d410d20e254125858f44131677
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/03/2019
ms.locfileid: "67548757"
---
# <a name="manage-operating-system-versions-with-intune"></a>Operációsrendszer-verziók kezelése az Intune-nal
A korszerű mobil- és asztali platformokon gyors ütemben követik egymást az operációs rendszerek főbb részeit érintő frissítések, javítások és új kiadások. A Windows platform frissítéseinek és javításainak bevezetése teljes mértékben kezelhető központilag. Más platformok, például az iOS és a Android esetében azonban a végfelhasználóknak is részt kell vennie a folyamatban.  A Microsoft Intune-nal könnyedén kialakíthatja a különböző platformokon futó operációsrendszer-verziók felügyeleti rendszerét.

Az Intune segítséget nyújt az alábbi, gyakran előforduló feladatok kivitelezéséhez: 
- A végfelhasználók eszközein található operációsrendszer-verziók meghatározása
- Szervezeti adatokhoz történő hozzáférés szabályozása az operációs rendszer új kiadásának érvényesítése során
- A szervezet által jóváhagyott legújabb operációsrendszer-verzióra történő áttérés ösztönzése/kötelezővé tétele a végfelhasználók körében
- Egy új operációsrendszer-verzió szervezeti szintű bevezetésének kezelése
  
## <a name="operating-system-version-control-using-intune-mobile-device-management-mdm-enrollment-restrictions"></a>Operációsrendszer-verziók követésének szabályozása az Intune MDM- (mobileszköz-kezelés) regisztráció korlátozásával
Az Intune MDM-regisztráció kapcsán megadható, hogy egy ügyféleszköznek milyen követelményeknek kell megfelelnie ahhoz, hogy regisztrálni lehessen az Intune általi felügyelethez. Így biztosítható, hogy a felhasználók csak a szabályozásoknak megfelelő eszközöket tudjanak regisztrálni, mielőtt hozzáférnek a szervezeti erőforrásokhoz. Az eszközökkel kapcsolatos követelmények között, a legalacsonyabb és legmagasabb verziók számával megadható, hogy a támogatott platformok operációs rendszerének mely verziói engedélyezettek.
 
![Platformkonfigurációkra vonatkozó korlátozások panelje](./media/os-version-platform-configurations.png) 
 
### <a name="in-practice"></a>A gyakorlatban
A szervezetek az alábbi beállításokkal szabályozhatják, hogy a különböző típusú eszközöknek milyen követelményeknek kell megfelelnie ahhoz, hogy azokról hozzá lehessen férni a szervezeti erőforrásokhoz: 
1. A minimális verziószám megadásával biztosítható, hogy a végfelhasználók a támogatott platformok közül az aktuálisan érvényben lévő verziót használják a szervezeten belül. 
2. Dönthet úgy, hogy a legmagasabb verziószámot nem adja meg (nem korlátozza), vagy megadhatja a szervezetben utoljára érvényesített verzió számát maximumként, időt hagyva az új operációsrendszer-verziók belső tesztelésére.

Ha a fentiekkel kapcsolatban további információkra van szüksége, olvassa át a [Típus szerinti korlátozás beállításának](https://docs.microsoft.com/intune/enrollment-restrictions-set#set-device-type-restrictions) leírását.
 
## <a name="operating-system-version-reporting-and-compliance-with-intune-mdm-device-compliance-policies"></a>Az operációsrendszer-verziók jelentése és megfelelőségük ellenőrzése Intune MDM eszközmegfelelőségi szabályzatokkal
Az Intune MDM eszközmegfelelőségi szabályzatai a következő feladatok végrehajtásához biztosítanak eszközöket: 
- Megfelelőségi szabályok meghatározása
- Megfelelőségi állapot megtekintése jelentéskészítéssel
- Eszköz karanténba helyezésével és feltételes hozzáférési megfelelőség hiányának kezelése

Hasonlóan ahhoz, ahogy a regisztrációs korlátozásoknál, a megfelelőségi szabályok között is megadható a legalacsonyabb és legmagasabb támogatott operációsrendszer-verzió. Az szabályzatokhoz ezenkívül határidők is definiálhatók, türelmi időt biztosítva a felhasználóknak arra, hogy gondoskodjanak eszközük megfelelőségéről. Az eszközmegfelelőségi szabályzatok segítenek elérni azt, hogy a végfelhasználók eszközei megfeleljenek a szervezeti szabályozásoknak.

![Eszközmegfelelőség – műveletek nem megfelelő eszközök észlelése esetén](./media/os-version-actions-noncompliance.png) 

### <a name="in-practice"></a>A gyakorlatban
Az eszközmegfelelési szabályzatok ugyanazokban az esetekben használhatók jól, mint a regisztrációs korlátozások. Ezek a szabályzatok segítenek elérni azt, hogy a szervezet felhasználói az operációs rendszerek aktuálisan érvényesített verzióit használják. Végfelhasználói eszközök megfelelőségi definiálásával, amikor vállalati erőforrásokhoz való hozzáférés blokkolva lesz feltételes hozzáférést addig, amíg a végfelhasználók a támogatott operációs rendszer tartományba, a szervezet számára. A felhasználókat a rendszer értesíti a megfelelőség hiányáról és arról, hogy milyen lépéseket kell tenniük annak érdekében, hogy ismét hozzáférjenek az erőforrásokhoz.   

Ha a fentiekkel kapcsolatban további információkra van szüksége, olvassa át az [Eszközmegfelelőségi szabályzatok – első lépések](https://docs.microsoft.com/intune/device-compliance-get-started) című témát.
 
## <a name="operating-system-version-controls-using-intune-app-protection-policies"></a>Operációsrendszer-verziók követése az Intune alkalmazásvédelmi szabályzataival    
Az Intune alkalmazásvédelmi szabályzataival és mobilalkalmazás-kezelési (MAM) beállításaival az alkalmazás szintjén adható meg, hogy minimálisan melyik operációrendszer-verzió szükséges. Így felhívhatja végfelhasználói figyelmét a megfelelőség hiányára, és ösztönözheti őket operációs rendszerük legalább ezen verzióra történő frissítésére.
 
Két lehetőség van: 
- **Figyelmeztetés** – figyelmeztetés értesíti arról, hogy frissítenie kell, ha azok alkalmazást nyit meg egy alkalmazásvédelmi szabályzattal vagy MAM hozzáférési beállítással olyan operációsrendszer-verzió fut az eszközön a végfelhasználó. Az alkalmazás adatait és a szervezeti adatokat ettől függetlenül el fogja tudni érni.
  ![Az Android frissítésére figyelmeztető párbeszédpanel képe](./media/os-version-update-warning.png) 

- **Blokk** -letiltása a végfelhasználó számára, hogy frissítenie kell egy alkalmazásvédelmi szabályzattal vagy MAM hozzáférési beállítással olyan operációsrendszer-verzió fut az eszközön az alkalmazás megnyitásakor tájékoztatja. Az alkalmazásadatokat és a szervezeti adatokat nem fogja tudni elérni.
  ![Kép az alkalmazás-hozzáférés blokkolva párbeszédpanel](./media/os-version-access-blocked.png)

### <a name="in-practice"></a>A gyakorlatban
Az alkalmazásvédelmi szabályzatokat legtöbbször akkor használják a különböző szervezetek, ha az alkalmazások nyitottak, vagy ha szeretnék elérni, hogy a végfelhasználók mindig az alkalmazások aktuális verzióját használják. Gyakran alkalmazott konfiguráció például, hogy a végfelhasználókat figyelmezteti a rendszer, ha az aktuálisnál eggyel korábbi verziót használnak, és letiltja, ha kettővel korábbi verziót.
 
Ha a fentiekkel kapcsolatban további információkra van szüksége, tekintse át az [Alkalmazásvédelmi szabályzatok létrehozása és hozzárendelése](https://docs.microsoft.com/intune/app-protection-policies) című cikket.

## <a name="managing-a-new-operating-system-version-rollout"></a>Új operációsrendszer-verzió bevezetésének kezelése
Az ebben a cikkben bemutatott Intune-funkciók segítséget nyújtanak ahhoz, hogy a szervezet áttérjen az operációs rendszer újabb verziójának használatára megadott időkereten belül. Az alábbi lépések a v1 operációs rendszerről a v2 operációs rendszerre 7 nap alatt történő áttérést modellezik.
- **1. lépés**: Regisztrációs korlátozások használatával az operációs rendszer v2 szükséges minimális verzióként, hogy regisztrálja az eszközt. Így gondoskodhat arról, hogy az újonnan regisztrált végfelhasználói eszközök megfeleljenek a szabályozásoknak.
- **2/a. lépés**: Használja az Intune alkalmazásvédelmi szabályzatok figyelmeztesse a végfelhasználókat, ha az alkalmazás megnyitásakor illetve újraindításakor az adott operációs rendszer v2-es megadása kötelező.
- **2/b. lépés**. Az eszközmegfelelőségi szabályzatoknál adja meg, hogy az eszközök megfelelőségéhez legalább az operációs rendszer v2-es verziója szükséges. A **Meg nem felelés esetén végrehajtandó műveletek** lehetőségnél adjon meg 7 napos türelmi időszakot, és határozza meg olyan e-mail-értesítés küldését, amely tartalmazza a határidőt és a követelményeket.
  - Ezeknek a szabályzatoknak a megadása esetén a rendszer e-mailben, az Intune céges portálon keresztül, alkalmazásvédelmi szabályzattal védett alkalmazás esetén pedig az alkalmazás megnyitásakor tájékoztatja a végfelhasználókat arról, hogy frissíteniük kell az eszköz operációs rendszerét.
  - A nem megfelelő felhasználók azonosításához kérheti egy megfelelőségi jelentés készítését a rendszertől. 
- **3a. lépés:** : Használja az Intune alkalmazásvédelmi szabályzatokat felhasználók blokkolása, ha az alkalmazás megnyílik, vagy folytatódik, ha az eszköz nem fut az operációs rendszer v2-es.
- **3/b. lépés**: Az eszközmegfelelőségi szabályzatoknál adja meg, hogy az eszközök megfelelőségéhez legalább az operációs rendszer v2-es verziója szükséges.
  - Ezeknek a szabályzatoknak a meghatározása esetén az eszközöket frissíteni kell ahhoz, hogy továbbra is el lehessen róluk érni a szervezeti adatokat. Védett szolgáltatások le vannak tiltva, az eszköz a feltételes hozzáférés használatakor. Az alkalmazásvédelmi szabályzatokkal védett alkalmazások használatát a rendszer megnyitásukkor vagy akkor tiltja le, amikor azok megpróbálják elérni a szervezeti adatokat.

## <a name="next-steps"></a>További lépések
A szervezeten belül használt operációsrendszer-verziók felügyeletével kapcsolatban az alábbi témáknál talál további információkat: 

- [Típus szerinti korlátozás beállítása](https://docs.microsoft.com/intune/enrollment-restrictions-set#set-device-type-restrictions)
- [Eszközmegfelelőségi szabályzatok – első lépések](https://docs.microsoft.com/intune/device-compliance-get-started)
- [Alkalmazásvédelmi szabályzatok létrehozása és hozzárendelése](https://docs.microsoft.com/intune/app-protection-policies)

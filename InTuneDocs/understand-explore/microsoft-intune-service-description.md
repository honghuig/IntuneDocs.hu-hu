---
title: "A szolgáltatás leírása | Microsoft Docs"
description: "Az Intune egy felhőalapú szolgáltatás, amellyel Windows, iOS, Mac OS X, Android és Windows Mobile rendszerű eszközök felügyelhetők."
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 09/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 40fa5a2e-6c0f-4150-9740-d5ddc0cdbda0
ms.reviewer: cacamp
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: f268cf29461447306d0f5c3ca06d541d9a03a49d
ms.openlocfilehash: 8e8257a426bd6b9a99e21e928b08c84f162d5da3
ms.lasthandoff: 12/16/2016


---

# <a name="microsoft-intune-service-description"></a>A Microsoft Intune szolgáltatás leírása

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

A Microsoft Intune egy felhőalapú szolgáltatás, amellyel Windows, Mac OS X, iOS, Android vagy Windows Mobile rendszert futtató eszközök felügyelhetők. Az Intune ezenkívül a vállalati alkalmazások és adatok védelmét is biztosítja. Használható önállóan, vagy a kezelési lehetőségek bővítése céljából a System Center Configuration Managerrel integrálva.

A Microsoft az Intune bevezetési értékelemet a jogosult csomagokban foglalt jogosult szolgáltatások esetében kínálja. Ez lehetővé teszi, hogy távoli segítséget kérjen a Microsoft szakértőitől az Intune-környezet üzembe helyezéséhez. A bevezetési értékelemmel kapcsolatos további információkért lásd: [A Microsoft Intune bevezetési értékelemének leírása](http://go.microsoft.com/fwlink/?LinkId=619281).

Az Intune használatát egy 30 napos ingyenes próbaverzióval kezdheti meg, amely 100 felhasználói licencet tartalmaz. Az ingyenes próbaverzió elindításához [látogasson el az Intune bejelentkezési oldalára](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/). Ha munkahelye vállalati szerződéssel vagy egy egyenértékű mennyiségi licencszerződéssel rendelkezik, az ingyenes próbaverzió beállítását bízza Microsoft-képviselőjére.

> [!NOTE]
> Ha munkahelyének van munkahelyi vagy iskolai Microsoft Online Services-fiókja, és előfordulhat, hogy a próbaidőszak leteltével élesben folytatja ennek az Intune-előfizetésnek a használatát, akkor az oldalon válassza a **Bejelentkezés** lehetőséget, és a hitelesítéshez használja a munkahelye globális rendszergazdai fiókját. Ez a művelet gondoskodik arról, hogy az Intune próbaverzió a meglévő munkahelyi vagy iskolai fiókhoz kapcsolódjon.

A mobileszközökön konfigurálható beállítások listáját itt találja:

-   [A Microsoft Intune regisztrált eszközök kezelésével kapcsolatos képességei](/intune/get-started/mobile-device-management-capabilities-in-microsoft-intune)

-   [Hibrid mobileszköz-felügyelet a System Center Configuration Managerrel és a Microsoft Intune-nal](https://technet.microsoft.com/library/mt627883.aspx)

A System Center Configuration Managerrel kapcsolatos további információkért lásd: [A System Center  Configuration Manager dokumentációja](https://technet.microsoft.com/library/mt346023.aspx).

## <a name="learn-how-intune-service-updates-affect-you"></a>Az Intune szolgáltatásfrissítéseinek hatása a felhasználókra
Mivel az Intune online szolgáltatásként működik, a Microsoft rendszeresen frissítéseket ad ki hozzá.

Ebből a cikkből megtudhatja, hogy milyen gyakran jelennek meg ezek a szolgáltatásfrissítések, és megismerkedhet azzal az előzetes értesítéssel, amelyben tudatjuk a felhasználókkal, hogy egy adott frissítés hatással lehet a szolgáltatás működésére.

Az Intune szolgáltatás változásainak megismeréséhez lásd az [Újdonságok a Microsoft Intune-ban](/intune/deploy-use/whats-new-in-microsoft-intune) című témakört. A [Microsoft Intune blog](http://blogs.technet.com/b/microsoftintune/) ugyancsak ismerteti a szolgáltatást érintő változásokat, ezenkívül hasznos tippekkel szolgál az Intune minél hatékonyabb használatához.

Az [Office 365 felügyeleti portál](https://portal.office.com/Admin/Default.aspx) üzenetközpontja ezenfelül a fontos szolgáltatásfrissítésekről is tájékoztatást nyújt. Az [Office 365 felügyeleti társalkalmazás](https://support.office.com/article/Office-365-Admin-Mobile-App-e16f6421-2a1a-4142-bf9d-9846600a060a) telepítésével mobileszközén is fogadhatja az értesítéseket.

> [!NOTE]
> Az [Office 365 felügyeleti portálon](https://portal.office.com/Admin/Default.aspx) az Intune szolgáltatás állapota is figyelemmel követhető. Válassza a bal oldali panel **Szolgáltatás állapota** elemét.  

A Microsoft Intune szolgáltatással kapcsolatos figyelmeztetéseinek típusai a következők:
-   Hogy fel tudjon készülni a szolgáltatás változásaira, a szolgáltatásfrissítést megelőzően legalább 30–90 nappal értesítjük, annak függvényében, hogy milyen hatású a változtatás. Erre a terméken belüli kommunikációs csatornákon (például a hirdetőtáblán közzétett értesítéseken) keresztül kerül majd sor. Ezek a változások a következők lehetnek:
    * Megfelelőségi vagy jogszabályi megfeleléssel összefüggő frissítések
    * A végfelhasználói élmény, a felhasználói felület és a munkafolyamatok változásai
    * Új vagy módosult API-k (értesítés arról, hogy tesztelni kell az egyéni alkalmazások visszamenőleges kompatibilitását)
    * A rendszerkövetelmények változásai, például a minimálisan szükséges böngészőverzió
    * Minden olyan frissítés, amely felhasználói beavatkozást igényel a funkció engedélyezéséhez vagy a funkció működésének zavartalanságához.
-   A Microsoft a havonta esedékes szolgáltatásfrissítés részeként az új szolgáltatásokkal, új funkciókkal és a meglévő funkciók fejlesztéseivel kapcsolatos információkat is biztosít. A Microsoft rendszerint minden hónap 15-e körül adja ki a szolgáltatásfrissítéseket. A frissítések leírását az [Újdonságok a Microsoft Intune-ban](/intune/deploy-use/whats-new-in-microsoft-intune) című témakörben találja.
    -   Az Intune szolgáltatás kivonása esetén 12 hónappal korábban értesítjük.

## <a name="choose-the-management-solution-thats-right-for-you"></a>Válassza ki az Ön számára megfelelő felügyeleti megoldást
Az Intune többféleképpen is beállítható annak érdekében, hogy biztosítható legyen (az ebben a cikkben **eszközöknek** nevezett) munkahelyi mobileszközök és számítógépek felügyelete és védelme.

-**Az Intune önálló konfigurációja.** A munkahelye mobileszközeinek felügyelete az Intune webalapú felügyeleti konzoljával végezhető. Az Intune bármilyen helyszíni informatikai infrastruktúra nélkül használható. Ha azonban az Intune-t az Active Directory Domain Services szolgáltatással együtt használja, a Domain Services által felügyelt tartományi felhasználói fiókokat az Intune-nal is használhatja.

-**Az Intune és a System Center Configuration Manager együttes használata.** A Configuration Manager-kezelőkonzollal felügyelheti a vállalat számítógépeit és mobileszközeit. Ezzel a konfigurációval a munkahelye összes eszközét egyetlen konzolon, a Configuration Manager felügyeleti konzolján felügyelheti. A Configuration Manager nagyszámú mobileszköz, kiszolgáló és számítógép felügyeletét támogatja. A Configuration Managerrel kapcsolatos további információkért lásd: [Hibrid mobileszköz-felügyelet a System Center Configuration Managerrel és a Microsoft Intune-nal](https://technet.microsoft.com/library/mt627883.aspx). Az Ön számára leginkább megfelelő módszer kiválasztásához további segítséget talál a [Választás a Microsoft Intune önálló és hibrid mobileszköz-kezelése között a Configuration Manager segítségével](https://technet.microsoft.com/en-us/library/mt706478.aspx).


## <a name="learn-more-about-intune"></a>További tudnivalók az Intune-ról
Az alábbi forrásokból többet is megtudhat az Intune-ról:

- A [Microsoft Intune Adatvédelmi központja](http://www.microsoft.com/en-us/server-cloud/products/intune-trust-center/) információkkal szolgál az Intune biztonsági, adatvédelmi és megfelelőségi vonatkozásairól, ezenkívül az Intune minősítései közül is bemutat néhányat.

- [A Microsoft Intune regisztrált eszközök kezelésével kapcsolatos képességei](/intune/get-started/mobile-device-management-capabilities-in-microsoft-intune)

### <a name="see-also"></a>További információ
[Microsoft Intune](https://docs.microsoft.com/intune/)
[A System Center 2012 Configuration Manager dokumentumkönyvtára](https://technet.microsoft.com/library/gg682041.aspx)

[Újdonságok a Microsoft Intune-ban](/intune/deploy-use/whats-new-in-microsoft-intune)

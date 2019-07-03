---
title: Eszközalapú feltételes hozzáférés az Intune beállítása
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan hozhat létre a Microsoft Intune eszközmegfelelőségi és mobilalkalmazás-kezelési alapján eszközalapú feltételes hozzáférési szabályzat.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ed6259c996772817ceaa8ec827c8ac506adfd399
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67530467"
---
# <a name="create-a-device-based-conditional-access-policy"></a>Eszközalapú feltételes hozzáférési szabályzat létrehozása

Az Intune-nal a feltételes hozzáférés az Azure Active Directory fokozva mobileszköz-megfelelőség ad hozzá a hozzáférés-vezérlést. Ha létrehozta az Intune eszközmegfelelőségi szabályzataival, amely meghatározza az eszközök megfelelőségéhez követelményeit, egy eszköz megfelelőségi állapota segítségével engedélyezi vagy letiltja a hozzáférést az alkalmazásokhoz és szolgáltatásokhoz. Ezt megteheti, hogy a beállítást használja a feltételes hozzáférési szabályzat létrehozásával is **megfelelőként megjelölt eszköz megkövetelése**.  

Feltételes hozzáférési szabályzat meghatározza az alkalmazás vagy védeni kívánt szolgáltatások, a feltételeket, amelyek alapján az alkalmazások vagy szolgáltatások érhető el, és a felhasználókat, akiknek a szabályzat vonatkozik. Feltételes hozzáférés egy Azure AD premium-funkció, amely konfigurálható az Azure Active Directoryban, de beállíthatja az Intune-portálon belül e ugyanazon házirendek is. Az *Intune-ból* elérhető feltételes hozzáférési csomópont ugyanaz a csomópont, amelyet az *Azure AD-ből* is el lehet érni.  

> [!IMPORTANT]
> Feltételes hozzáférés beállítása előtt kell eszközöket, hogy megfelelnek-e különleges követelmények alapján kiértékelheti, hogy az Intune eszközmegfelelőségi szabályzatai beállítása. Lásd: [az Intune eszközmegfelelőségi szabályzatai – első lépések](device-compliance-get-started.md).

## <a name="create-conditional-access-policy"></a>Feltételes hozzáférési szabályzat létrehozása

1. Az Intune-portálon válassza **feltételes hozzáférési** > **házirendek** > **új szabályzat**.
   
    ![Új feltételes hozzáférési szabályzat létrehozása](media/create-conditional-access-intune/create-ca.png)
 
2. A **Hozzárendelések** alatt válassza a **Felhasználók és csoportok** lehetőséget. 
3. Az a **Belefoglalás** lapra, és keresse meg a felhasználókat és csoportokat, akiknek a feltételes hozzáférési szabályzatot a alkalmazni kíván. Miután kiválasztotta, akinek tartalmazza, a **kizárása** lapon, ha minden olyan felhasználók, szerepkörök vagy csoportok ki szeretné zárni a szabályzatból.  
    - **Minden felhasználó**: Válassza ki ezt a beállítást, a alkalmazni a szabályzatot minden felhasználó és csoport, beleértve a belső és vendégfelhasználókat.
  
    - **Válassza ki a felhasználók és csoportok**: Válassza ezt a lehetőséget, és adja meg a következő lehetőségek közül:
  
      a. **Minden vendégfelhasználó**: Válassza ezt a lehetőséget, hogy belefoglalja vagy kizárja a külső vendégfelhasználóknak (például a partnerek, a külső együttműködők)
       
      b. **Címtárbeli szerepkörök**: Válassza ki egy vagy több bevonhat vagy kizárhat felhasználókat, akikhez hozzá van rendelve, hogy ezek a szerepkörök az Azure AD-szerepkörök.
      
      c. **Felhasználók és csoportok**: Válassza ki ezt a lehetőséget, keresse meg és válassza az egyéni felhasználók vagy csoportok belefoglalása vagy kizárása.
     
       > [!TIP]  
       > Tesztelje a szabályzatot egy kisebb csoporton ellenőrizze, hogy a várt módon működik a felhasználók.
4. Válassza a **Done** (Kész) lehetőséget.
5. A **Hozzárendelések** alatt válassza a **Felhőalkalmazások** lehetőséget. 
6. Az a **Belefoglalás lapjáról**, az alkalmazások és szolgáltatások, a feltételes hozzáférési szabályzattal védeni kívánt azonosításához. Ezt követően használhatja a **kizárása** lapon, ha vannak azokhoz az alkalmazásokhoz és szolgáltatásokhoz szeretne zárni a szabályzatból.
    - **Az összes felhőalapú alkalmazások**: Válassza ki ezt a beállítást, a házirend vonatkozik minden alkalmazásra.
      > [!IMPORTANT]  
      > Ez a lista tartalmazza az Azure portal eléréséhez a Microsoft Azure Management app. Ügyeljen arra, hogy a **kizárása** lap vagy az ide vagy a a **felhasználók és csoportok** lehetőségek, hogy Ön (vagy a felhasználókat vagy csoportokat úgy) fog tudni bejelentkezni az Azure Portalon. 

    - **Alkalmazások kiválasztása**: Válassza ezt a lehetőséget, válassza a **kiválasztása**, majd az alkalmazások listáját segítségével keresse meg és válassza ki a védeni kívánt szolgáltatásokat.
    
      ![Új feltételes hozzáférési szabályzat létrehozása](media/create-conditional-access-intune/create-ca-select-apps.png)

7. Válassza a **Done** (Kész) lehetőséget.
8. A **hozzárendelések**válassza **feltételek**.
    - **Bejelentkezési kockázati**: Ez a szabályzat az Azure AD Identity Protection bejelentkezési kockázat észlelési használata az Igen gombra, és válassza a alkalmazni kell a szabályzatot bejelentkezési kockázati szintek.
    - **Eszközplatformok**: Az a **Belefoglalás** lapra, és keresse meg azokat az eszközplatformokat, a alkalmazni szeretné a feltételes hozzáférési szabályzat. Használja a **kizárása** platformok kizárását a szabályzat lapján.
    - **Helyek**: Az a **Belefoglalás** lapra, adja meg, hogy a szabályzat minden olyan hely, a megbízható hálózati helyek, az informatikai részleg felügyelete alatt álló vagy a megfelelő hálózati helyeket az érvényes. Használja a **kizárása** szabályzatból kizárandó hálózati helyek lapon. 
    - **Ügyfélalkalmazások**: Válasszon **Igen** , adja meg, ha a böngészőben megjelenő alkalmazásokba, mobilalkalmazások és asztali ügyfelek vonatkozzon a szabályzat. Lehetőség kiválasztásával **Modern hitelesítési ügyfelek** (például az Outlook iOS-es vagy androidos Outlook) és **Exchange ActiveSync-ügyfelek**.
    - **Az eszköz állapotát**: A feltételes hozzáférési szabályzat hatálya minden eszköz állapot, ha az Igen gombra, és kifejezetten kizárja az államok eszközök hibrid Azure AD-csatlakoztatott vagy megfelelőként megjelölt eszköz (vagy mindkettő).
    
      ![Új feltételes hozzáférési szabályzat létrehozása](media/create-conditional-access-intune/create-ca-device-platforms.png)

      > [!TIP]  
      > Ha mind a védeni kívánt **Modern hitelesítést** ügyfelek és **Exchange ActiveSync-ügyfelek**, hozzon létre két külön feltételes hozzáférési házirendeket, egyet az egyes ügyfél. Bár a modern hitelesítést támogatja az Exchange ActiveSync, az csak az Exchange ActiveSync által támogatott feltétele platform. Egyéb feltételek, beleértve a multi-factor authentication használata nem támogatott. Hatékony hozzáférés védelme az Exchange online-hoz az Exchange ActiveSync, hozzon létre egy feltételes hozzáférési szabályzatot, amely meghatározza az Office 365 Exchange online-hoz felhőalapú alkalmazás és az ügyfélalkalmazás az Exchange ActiveSync alkalmaz szabályzat csak a kiválasztott támogatott platformokkal.

9. Válassza a **Done** (Kész) lehetőséget.
10. A **Hozzáférés-vezérlés** alatt válassza ki az **Engedélyezés** elemet. Mi történik, megfelelően beállította feltételek megadása  Az alábbi lehetőségek közül választhat:
    - **Hozzáférés letiltása**: Az ebben a házirendben megadott felhasználónak sem lesz a megadott feltételek alapján az alkalmazásokhoz való hozzáférés.
    - **Hozzáférés biztosítása**: Az ebben a szabályzatban meghatározott felhasználók kapnak hozzáférést, de megkövetelheti a következő további műveletek:
      - **Többtényezős hitelesítés megkövetelése**: A felhasználó további biztonsági követelményeket, például telefonhívást vagy SMS végrehajtásához kell.
      - **Megfelelőként megjelölt eszköz megkövetelése**: Az eszköz Intune-kompatibilis kell lennie. Az eszköz nem megfelelő, ha a felhasználó kap arra, hogy regisztrálja az eszközt az Intune-ban. 
      - **Hibrid Azure AD-csatlakoztatott eszköz megkövetelése**: Eszközök hibrid Azure AD-hez kell lennie.
      - **Jóváhagyott ügyfélalkalmazás megkövetelése**: Az eszköz jóváhagyott ügyfélalkalmazásokat kell használnia. 
      - **Több vezérlő esetén**: Válassza ki **az összes kijelölt vezérlő megkövetelése** úgy, hogy az összes fenti követelményt kényszerítettek, ha egy eszköz próbál hozzáférni az alkalmazáshoz.
    
      ![Hozzáférés-vezérlés beállításainak megadása](media/create-conditional-access-intune/create-ca-grant-access-settings.png)
 
11. A **Szabályzat engedélyezése** alatt válassza a **Bekapcsolás** elemet.
     
     ![A szabályzat engedélyezése](media/create-conditional-access-intune/enable-policy.png)

12. Kattintson a **Létrehozás** gombra.

## <a name="see-also"></a>Lásd még:
[alkalmazásalapú feltételes hozzáférés Intune-nal](app-based-conditional-access-intune.md)

[Intune-beli feltételes hozzáférés hibaelhárítása](https://support.microsoft.com/help/4456106)

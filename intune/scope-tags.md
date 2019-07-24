---
title: Szűrési szabályzatok hatókörcímkékkel a Microsoft Intune-ban – Azure | Microsoft Docs
description: Hatókörcímkékkel a konfigurációs profilokat meghatározott szerepkörök szerint szűrheti.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2019
ms.topic: article
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 627899eafb2175b2d3034045bd765a10f4a203d6
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882507"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>A szerepköralapú hozzáférés-vezérlés (RBAC) és a hatókör-címkék használata a terjesztéshez

A szerepköralapú hozzáférés-vezérlés és a hatókör-címkék használatával ellenőrizheti, hogy a megfelelő rendszergazdák rendelkeznek-e megfelelő hozzáféréssel, és hogy láthatók-e a megfelelő Intune-objektumok. A szerepkörök határozzák meg, hogy mely hozzáférési rendszergazdák rendelkezzenek az objektumokkal. A hatókör-címkék határozzák meg, hogy mely objektumok adminisztrátorai láthatják.

Tegyük fel például, hogy a Seattle regionális iroda rendszergazdája hozzá van rendelve a házirend és a profil Manager szerepkörhöz. Azt szeretné, hogy ez a rendszergazda csak a Seattle-eszközökre érvényes profilokat és házirendeket tekintse meg és kezelje. Ehhez tegye a következőket:

1. Hozzon létre egy Seattle nevű hatókör-címkét.
2. Hozzon létre egy szerepkör-hozzárendelést a házirend és a profil-kezelő szerepkörhöz a következővel: 
    - Tagok (csoportok) = egy Seattle informatikai rendszergazdák nevű biztonsági csoport. Az ebben a csoportban található összes rendszergazda jogosult a házirendek és profilok kezelésére a hatókörben (csoportok) lévő felhasználók és eszközök számára.
    - Hatókör (csoportok) = egy Seattle-felhasználók nevű biztonsági csoport. A csoportban lévő összes felhasználó/eszköz rendelkezhet a tagok (csoportok) rendszergazdái által felügyelt profilokkal és szabályzatokkal. 
    - Hatókör (címkék) = Seattle. A tag (csoportok) rendszergazdái láthatják a Seattle hatókör címkével is rendelkező eszközöket.
3. Adja hozzá a Seattle-hatókör címkét olyan házirendekhez és profilokhoz, amelyeket a rendszergazdák a tagok (csoportok) számára kívánnak elérni.
4. Adja hozzá a Seattle scope címkét a tagok (csoportok) rendszergazdái számára megjeleníteni kívánt eszközökhöz. 


## <a name="to-create-a-scope-tag"></a>Hatókörcímke létrehozása

1. Az Intune-ban válassza a **szerepkörök** > **hatóköre (címkék)**  > **Létrehozás**elemet.

    ![Képernyőkép a hatókör-címke létrehozásáról.](./media/scope-tags/create-scope-tag.png)

3. Ha azt szeretné, hogy az összes eszköz adott csoportokban legyen, válassza **a hatókör címke kiosztása a kijelölt csoportokban lévő összes eszközhöz**lehetőséget.
    1. A szerepeltetni kívánt **csoportok kiválasztása** lapon válassza ki azokat az eszközöket, amelyekhez hozzá szeretné rendelni a hatókör címkéjét.
    2. Válassza a **Kiválasztás** lehetőséget
4. Válassza a **Létrehozás** lehetőséget.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Hatókörcímke hozzárendelése egy szerepkörhöz

1. Az Intune-ban válassza a **szerepkörök** > **minden szerepkör** lehetőséget > Válassza ki a szerepkör > **hozzárendelések** > hozzárendelését.

    ![Képernyőfelvétel a hatókör hozzárendeléséről egy szerepkörhöz.](./media/scope-tags/assign-scope-to-role.png)

2. Adja meg a **hozzárendelés nevét** és **leírását**.
3. Válassza a **Tagok (csoportok)**  > **Hozzáadás** > a hozzárendelés részeként válassza ki a kívánt csoportokat > **válassza** > az**OK**gombot. az ebben a csoportban található mUsers jogosultak a házirendek és profilok kezelésére a hatókörben (csoportokban) lévő felhasználók és eszközök számára.

    ![Képernyőfelvétel a csoporttag kiválasztásáról.](./media/scope-tags/select-member-groups.png)

4. Ha egy adott csoportba tartozó felhasználókat vagy eszközöket szeretne felügyelni, válassza a **hatókör (csoportok)**  > **kijelölt csoportok** > **lehetőséget, majd válassza ki** a csoportokat a csoportok kiválasztásához > Válassza ki a csoportokat > **válassza** > az OK gombot. A csoportban lévő összes felhasználó/eszköz rendelkezhet a tagok (csoport) rendszergazdái által felügyelt profilokkal és szabályzatokkal.

    ![Képernyőkép a hatókör-csoportok kiválasztásáról.](./media/scope-tags/select-scope-groups.png)

    Másik lehetőségként kiválaszthatja **az**összes eszközt, **az összes felhasználót**vagy **az összes felhasználót & minden eszközön**.

    ![Képernyőkép a hatókör-csoportok kiválasztásának egyéb lehetőségeiről.](./media/scope-tags/scope-group-other-options.png)
    
5. Válassza a **hatókör (címkék)**  > **Hozzáadás** lehetőséget > Válassza ki a szerepkörhöz hozzáadni kívánt címkéket > **válassza** > az**OK gombot**. A tagok (csoportok) felhasználói hozzáférhetnek a szabályzatokhoz és a profilokhoz, amelyek szintén rendelkeznek ugyanazzal a hatóköri címkével.

    ![Képernyőkép a hatóköri címkék kiválasztásáról.](./media/scope-tags/select-scope-tags.png)

6. Válassza az **OK** gombot. 

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>Hatókörcímke hozzáadása egy konfigurációs profilhoz
1. Az Intune-ban válassza az **eszköz konfigurációs** > **profilok** > a profil kiválasztása lehetőséget.

    ![Képernyőkép a profil kiválasztása lehetőségről.](./media/scope-tags/choose-profile.png)

2. Válassza a **Tulajdonságok** > **hatókör (címkék)**  > **Hozzáadás**elemet.

    ![Képernyőkép a hatókör-címkék hozzáadásáról.](./media/scope-tags/add-scope-tags.png)

3. A **címkék kiválasztása**területen válassza ki azokat a címkéket, amelyeket hozzá szeretne adni a profilhoz.
4. Válassza  > **az**okMentés > kiválasztása lehetőséget.

## <a name="to-assign-a-scope-tag-to-an-app-configuration-policy"></a>Hatókör-címke társítása alkalmazás-konfigurációs házirendhez
A **felügyelt eszközökre**beállított eszközök beléptetési **típusával** :
1. Válassza az **ügyfélalkalmazások** > **alkalmazás-konfigurációs szabályzatok** lehetőséget, > válasszon egy alkalmazás-konfigurációs házirendet.
2. Válassza a **Tulajdonságok** > **hatóköre (címkék)** > Válassza ki a Szabályzathoz hozzárendelni kívánt címkéket.

A **felügyelt alkalmazásokhoz**beállított eszközök beléptetési **típusával** :
1. Válassza az **ügyfélalkalmazások** > **alkalmazás-konfigurációs szabályzatok** lehetőséget, > válasszon egy alkalmazás-konfigurációs házirendet.
2. Válassza a **hatókör (címkék)** lehetőséget > Válassza ki a Szabályzathoz hozzárendelni kívánt címkéket.


## <a name="to-assign-a-scope-tag-to-an-ios-app-provisioning-profile"></a>Hatókör-címke társítása iOS-alkalmazás létesítési profiljához
1. Az Intune-ban válassza az **ügyfélalkalmazások** > **iOS-alkalmazások létesítési profiljai** lehetőséget > válasszon egy profilt.
2. Válassza a **Tulajdonságok** > **hatóköre (címkék)** > Válassza ki a profilhoz hozzárendelni kívánt címkéket.
3. Válassza  > **az**okMentés > kiválasztása lehetőséget.

## <a name="to-assign-a-scope-tag-to-an-apple-volume-purchase-program-vpp-token"></a>Hatókör-címke társítása Apple Volume Purchase Program (VPP) jogkivonathoz
1. Az Intune-ban válassza az **ügyfélalkalmazások** > **Apple VPP** -tokenek > Válassza ki a VPP-tokent.
2. Válassza a **hatókör (címkék)** lehetőséget > Válassza ki a profilhoz hozzárendelni kívánt címkéket. A VPP-tokenhez társított VPP-alkalmazások és-e-könyvek öröklik a hozzárendelt címkéket.
3. Válassza  > **az**okMentés > kiválasztása lehetőséget.

## <a name="scope-tag-details"></a>Hatóköri címke részletei
A hatókör-címkék használatakor jegyezze fel ezeket a részleteket:

- A hatókörhöz tartozó címkéket jelenleg a következőhöz rendelheti hozzá:
  - Szerepkör-hozzárendelések
  - Eszközmegfelelőségi szabályzatok
  - Eszközkonfigurációs profilok
  - Windows 10-es frissítések – gyűrűk
  - Felügyelt eszközök
  - Alkalmazások
  - Alkalmazás-konfigurációs házirendek – felügyelt eszközök
  - PowerShell-parancsfájlok
  - DEP-tokenek
  - iOS-alkalmazás létesítési profilja
  - Volume Purchase program-(VPP-) tokenek
- Amikor egy rendszergazda létrehoz egy objektumot az Intune-ban, a rendszergazda számára hozzárendelt összes hatókör-címke automatikusan hozzá lesz rendelve az új objektumhoz.
- Az Intune-RBAC nem vonatkozik Azure Active Directory szerepkörökre. Így az Intune szolgáltatás-rendszergazdák és a globális rendszergazdák szerepkörök teljes körű rendszergazdai hozzáféréssel rendelkeznek az Intune-hoz, függetlenül attól, hogy milyen hatókörű címkéket használnak.
- A hatókör címkékkel rendelkező szerepkör-hozzárendelés rendszergazdái a hatóköri címkék nélküli Intune-objektumokat is láthatják.
- Csak a szerepkör-hozzárendelésekben található hatókör-címkét lehet hozzárendelni.
- Csak azok a csoportok jelennek meg, amelyek szerepelnek a szerepkör-hozzárendelés hatókörében (csoportokban).
- Ha a szerepkörhöz hozzárendelt hatókör-címkével rendelkezik, nem törölheti az összes hatókör-címkét egy Intune-objektumon. Legalább egy hatókör-címkét kötelező megadni.

## <a name="next-steps"></a>További lépések

A [szerepkörök](role-based-access-control.md) és a [profilok](device-profile-assign.md) kezelése.

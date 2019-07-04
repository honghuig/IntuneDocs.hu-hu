---
title: Feltételes hozzáférés áttelepítése az Azure Portalon
titleSuffix: Microsoft Intune
description: Az az Azure Portalon az Intune klasszikus portálján korábban létrehozott feltételes hozzáférési szabályzatok ismételt hozzárendelése.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 301159ad-5f7e-4fcc-86c7-f72a71701ff4
ms.reviewer: chrisgree
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8bcc9aa527ed27ef35db901117ceb8f4c8d10c97
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/03/2019
ms.locfileid: "67546883"
---
# <a name="reassign-conditional-access-policies-from-intune-classic-portal-to-the-azure-portal"></a>Feltételes hozzáférési szabályzatokat az Intune klasszikus portáljáról az Azure Portalra való újbóli hozzárendelése

Kezdve az új Azure Portalon, a feltételes hozzáférési ajánlatok alkalmazásonként több testreszabhatóság és szabályzatot is támogatnak. Ha korábban létrehozott feltételes hozzáférési szabályzatokat az Intune klasszikus portálján, áttelepítheti azokat az Azure Portalra. 

## <a name="before-you-begin"></a>Előkészületek

Ha készen áll az Azure Portalra, kövesse az ebben a témakörben a az Intune klasszikus portálján korábban létrehozott feltételes hozzáférési szabályzatok ismételt hozzárendelése:

- Gyűjtse össze a korábban létrehozott feltételes hozzáférési szabályzatokat, hogy tudja, milyen beállításokat kell később újra társítania.

- Az ebben a témakörben leírt lépéseket követve újraalkothatja ezeket a szabályzatokat az Azure Portalon.

- Miután meggyőződött róla, hogy az új szabályzatok a várt módon működnek az Azure Portalon, tiltsa le a feltételes szabályzatokat az Intune klasszikus portálján.
<br /><br />
    - **Mielőtt letiltaná** a feltételes hozzáférési szabályzatokat az Intune klasszikus portálján, megtervezése, hogyan helyezi át felhasználók, az új házirendet. Két módszer létezik:
<br /><br />
        - **Használhatja ugyanazt a belefoglaló csoportot az Azure Portalon létrehozott szabályzatok alkalmazására úgy, hogy létrehoz egy új kizárt csoportot az Intune klasszikus portál által alkalmazott szabályzatokhoz**.
            - A felhasználók egy részét fokozatosan helyezze át a klasszikus portálon megadott kizárt csoportba. Ez megakadályozza az Intune klasszikus portálja által meghatározott szabályzatok alkalmazását. Az ugyanazon felhasználói csoporthoz az Azure Portalon létrehozott szabályzatok az Intune klasszikus portálon alkalmazottak mellett érvényesülnek. 
<br /><br />
        - **Hozzon létre egy új csoportot, amelyre alkalmazza a feltételes hozzáférési szabályzatokat az Azure Portalon**. Ha ezt a módszert választja, akkor a következőket kell tennie:
            - Fokozatosan távolítsa el a felhasználók a biztonsági csoportokból, amelyekre feltételes hozzáférési szabályzatok az Intune klasszikus portálján célzó.
            - Miután meggyőződött róla, hogy az új szabályzat ezen felhasználók esetében működik, letilthatja a szabályzatot az Intune klasszikus portálján. 
<br /><br />
- Ha a feltételes hozzáférési házirend-beállítások használatára van konfigurálva az Exchange ActiveSync (EAS) az Intune klasszikus portálján, tekintse meg a [ebben a témakörben megadott utasítások](#reassign-intune-device-based-conditional-access-policies-for-eas-clients) való **ismételt hozzárendelése EAS feltételes hozzáférési szabályzat beállításait az az Azure Portalon**.

### <a name="to-verify-your-device-based-conditional-access-policies-in-the-intune-classic-portal"></a>Ellenőrizze a eszközalapú feltételes hozzáférési szabályzatokat az Intune klasszikus portálján

1. Jelentkezzen be hitelesítő adataival az [Intune klasszikus portálon](https://manage.microsoft.com).

2. Válassza a bal oldali menü **Szabályzat** pontját.

3. Válasszon **feltételes hozzáférési**, majd válassza ki a Microsoft felhőszolgáltatást (például az Exchange Online vagy SharePoint Online), a feltételes hozzáférési szabályzatot hozott létre, és.

4. Jegyezze fel a feltételes hozzáférés beállításait, és tekintse át ezeket, amikor az Azure Portalon ugyanezeket a feltételes hozzáférési szabályzatokat hoz létre.

### <a name="app-and-device-based-conditional-access-policies-working-together"></a>Alkalmazás- és eszközalapú feltételes hozzáférési szabályzatok együttműködése

Az Azure Portal **Intune App Protection** paneljén a rendszergazdák alkalmazásalapú feltételes szabályokat állíthatnak be, így csak az Intune alkalmazásvédelmi szabályzatait támogató alkalmazások férhetnek hozzá a vállalati erőforrásokhoz. Kiválaszthatja, hogy ezek alapján az alkalmazásalapú feltételes hozzáférési szabályzatok átfedésben eszközalapú feltételes hozzáférési szabályzatok használatával. Az eszközalapú és alkalmazásalapú feltételes szabályzatokat kombinálhatja (logikai ÉS) vagy választási lehetőséget kínálhat fel (logikai VAGY). Ha a feltételes hozzáférési szabályzat követelményei szerint:

- Követelmény a megfelelő eszköz **ÉS** az engedélyezett alkalmazás használata.
    - A feltételes hozzáférési szabályzat segítségével kell beállítania a [Azure Active Directory feltételes hozzáférés paneljén](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) és a [Intune App Protection paneljén](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0).
<br /><br />
- Követelmény a megfelelő eszköz **VAGY** az engedélyezett alkalmazás használata.
    - A feltételes hozzáférési szabályzat segítségével kell beállítania a [Intune klasszikus portálján](https://manage.microsoft.com) és a [Intune App Protection paneljén](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0).

> [!TIP] 
> Ezt a témakört az Intune klasszikus portál és az Azure Portal felhasználói felületét összehasonlító képernyőképek illusztrálják.

## <a name="reassign-intune-device-based-conditional-access-policies"></a>Az Intune eszközalapú feltételes hozzáférési szabályzatok ismételt hozzárendelése

1. Lépjen a [feltételes hozzáférés az Azure Portalon](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies), és jelentkezzen be a hitelesítő adataival.

2. Válassza az **Új szabályzat** lehetőséget.

3. Adja meg a szabályzat nevét.

4. Alatt a **hozzárendelések**, válassza a **felhasználók és csoportok** lehetőséget az új feltételes hozzáférési szabályzat.

    ![Kép, hogy összehasonlítja felhasználói csoport felhasználói felület az Intune és az Azure Portalon](./media/reassign-ca-1.png)

    > [!IMPORTANT] 
    > Az Azure Portalon és a klasszikus portálon végzett kiválasztásnak meg kell egyeznie. Például ha a Minden felhasználó lehetőséget jelölte meg az Intune klasszikus portálján, akkor az Azure Portalon is a **Minden felhasználó** lehetőséget válassza. Ezen kívül, ha használta a **Kivételt képző csoportok** lehetőséget az Intune klasszikus portálon, akkor az ott kijelölt csoportokat ki kell zárnia az Azure Portalon is.

5. A csoport kijelölése után kattintson a **Kiválaszt**, majd a **Kész** gombra.

6. A **Hozzárendelések** szakaszban válassza a **Felhőalkalmazások** lehetőséget.

7. A **Felhőalkalmazások** panelen válassza az **Alkalmazások kijelölése** lehetőséget.

8. Válassza ki az alkalmazást az új feltételes hozzáférési szabályzatot a alkalmazni, és kattintson a kívánt **kiválasztása**.

9. Kattintson a **Done** (Kész) gombra.

    ![Egy felhőalapú kezelőfelületének összehasonlítása az Intune és az Azure Portalon képe](./media/reassign-ca-3.png)

    > [!TIP] 
    > Ha több alkalmazásra ugyanaz a szabályzat vonatkozik, akkor érdemes lehet egyetlen szabályzatba összevonni őket az Azure Portalon.

10. A **Hozzárendelések** szakaszban válassza a **Feltételek** lehetőséget.

11. A **Feltételek** panelen az **Eszközplatformok** alatt válassza ki az alkalmazható eszközplatformokat.

12. Ha végzett az eszközplatformok kijelölésével, kattintson kétszer a **Kész** gombra.

    ![Kép, amely összehasonlítja az Intune és az Azure portálon a felhasználói felület eszközplatform](./media/reassign-ca-4.png)

    > [!TIP] 
    > Ha egyedi platformokat jelölt ki az Intune klasszikus portálon, akkor az Azure Portalon is válassza ki az egyes platformokat.

    > [!NOTE] 
    > A tartományhoz való csatlakozás és a Windows megfelelőség beállításait később is megadhatja.

13. A **Hozzárendelések** szakaszban válassza a **Feltételek** lehetőséget.

14. A **Feltételek** panelen az **Ügyfélalkalmazások** alatt válassza ki a megfelelő ügyfélalkalmazást.

15. Ha végzett az ügyfélalkalmazás kijelölésével, kattintson kétszer a **Kész** gombra.

    ![Kép, amely összehasonlítja az ügyfélalkalmazások felhasználói felület az Intune és az Azure Portalon](./media/reassign-ca-6.png)

16. Ha kijelölte a böngészőbeállításokat az Intune klasszikus portálon, akkor az Azure Portalon jelölje ki a **Böngésző** és a **Mobilalkalmazások és asztali ügyfelek** lehetőséget is. Ha nem jelölte ki a böngészőbeállításokat az Intune klasszikus portálon, akkor csak a **Mobilalkalmazások és asztali ügyfelek** lehetőséget jelölje meg. 

17. A **Hozzáférés-vezérlés** területen válassza az **Engedélyezés** elemet.

18. A **Hozzáférési engedély feltételei** alatt jelölje ki a **Eszköz megfelelőként való megjelölésének megkövetelése** lehetőséget, majd kattintson a **Kiválaszt** gombra.

19. Ha van tartományba léptetett Windows-eszközöket megkövetelő szabályzata, és engedélyezi az Intune-ban regisztrált és megfelelő Windows-eszközöket is, akkor válassza a **Tartományba léptetett eszköz megkövetelése** és a **Megfelelőként megjelölt eszköz megkövetelése** feltételt, valamint **A kijelölt feltételek egyikének megkövetelése** lehetőséget.

20. Ha nem engedélyezi az Intune-ban regisztrált és megfelelő Windows-eszközöket, zárja ki a Windows-szabályzatot a jelenlegiből. Ezután hozzon létre külön szabályzatot az **Eszközplatform** értékét **Windows**ra állítva, belefoglalva a fentiek szerint beállított többi feltételt, és válassza a **Tartományba léptetett eszköz megkövetelése** feltételt a **Hozzáférési engedély feltételei** alatt.

21. A a **új** feltételes hozzáférési szabályzat panelen kapcsolja be a **házirend engedélyezése** váltsa át, és kattintson a **létrehozás**.

    ![Engedélyezi a feltételes hozzáférési szabályzat felhasználói Felületére az Intune és az Azure közötti összehasonlítása](./media/reassign-ca-11.png)

## <a name="reassign-intune-device-based-conditional-access-policies-for-eas-clients"></a>Az Intune eszközalapú feltételes hozzáférési szabályzatok ismételt hozzárendelése EAS-ügyfelek

Ha konfigurálta az Exchange ActiveSync-beállítások az Intune klasszikus portálján az Exchange Online-szabályzat részeként, meg kell egy második feltételes hozzáférési szabályzat létrehozása az Azure Portalon.

1. Lépjen a [feltételes hozzáférés az Azure Portalon](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies), és jelentkezzen be a hitelesítő adataival.

2. Válassza az **Új szabályzat** lehetőséget.

3. Adja meg a szabályzat nevét.

4. Alatt a **hozzárendelések** válassza **felhasználók és csoportok** lehetőséget az új feltételes hozzáférési szabályzat.

    ![A kép egy felhasználói csoportok Kezelőfelületének összehasonlítása az Azure és az Intune-portálokon](./media/reassign-ca-12.png)

    > [!IMPORTANT] 
    > Az Azure Portalon és az Intune-portálon végzett kiválasztásnak meg kell egyeznie. Például ha a Minden felhasználó lehetőséget jelölte meg az Intune klasszikus portálján, akkor az Azure Portalon is a **Minden felhasználó** lehetőséget válassza. Ezen kívül, ha használta a **Kivételt képző csoportok** lehetőséget az Intune klasszikus portálon, akkor az ott kijelölt csoportokat ki kell zárnia az Azure Portalon is.

5. A csoport kijelölése után kattintson a **Kiválaszt**, majd a **Kész** gombra.

6. A **Hozzárendelések** szakaszban válassza a **Felhőalkalmazások** lehetőséget.

7. A **Felhőalkalmazások** panelen kattintson a **Kijelölt alkalmazások**, majd az **Exchange Online** elemre. Kattintson a **Kiválaszt**, majd a **Kész** gombra.

    ![A felhőalapú alkalmazások Kezelőfelületének összehasonlítása az Intune és az Azure Portalon képe](./media/reassign-ca-14.png)

    > [!IMPORTANT] 
    > Az EAS-ügyfelek feltételes hozzáférési szabályzatai nem vonatkozhatnak másik felhőalkalmazásra.

8. A **Feltételek** panelen az **Ügyfélalkalmazások** alatt válassza ki a megfelelő ügyfélalkalmazást. Ha az Intune által nem támogatott ügyfelek kitiltása mellett döntött, akkor válassza a **Szabályzat alkalmazása csak a támogatott platformokon** lehetőséget.

    ![Kép egy ügyfélalkalmazás Kezelőfelületének összehasonlítása az Azure és az Intune-portálokon](./media/reassign-ca-15.png)

9. Ha végzett az ügyfélalkalmazás kijelölésével, kattintson kétszer a **Kész** gombra.

10. A **Hozzáférés-vezérlés** területen válassza az **Engedélyezés** elemet.

11. A **Hozzáférési engedély feltételei** alatt jelölje ki a **Eszköz megfelelőként való megjelölésének megkövetelése** lehetőséget, majd kattintson a **Kiválaszt** gombra.

    ![Kép, amely összehasonlítja a hozzáférés biztosítása a felhasználói felület az Intune és az Azure Portalon](./media/reassign-ca-16.png)

12. A a **új** feltételes hozzáférési szabályzat panelen kapcsolja be a **házirend engedélyezése** váltsa át, és kattintson a **létrehozás**.

    ![Engedélyezi a feltételes hozzáférési szabályzat felhasználói Felületére az Intune és az Azure közötti összehasonlítása](./media/reassign-ca-17.png)

> [!NOTE]
> Ha konfigurálja az **Eszközplatformokat**, a szabályzat mentése sikertelen lesz, és a „Szabályzat konfigurálása nem támogatott” üzenetet kapja. Az Exchange ActiveSync nem tudja azonosítani a csatlakozó eszköz által használt platformot. Az egyes eszközplatformok konfigurálása ezért nem támogatott az Exchange ActiveSync-eszközök szabályzatainak létrehozásakor.

## <a name="disable-conditional-access-policies-in-the-intune-classic-portal"></a>Tiltsa le a feltételes hozzáférési szabályzatokat az Intune klasszikus portálján

Miután újra hozzárendelte a feltételes hozzáférési szabályzatokat az Azure Portalon rendelkezik, fontos fokozatosan letiltsa az Intune klasszikus portálján korábban létrehozott feltételes hozzáférési szabályzatokat. Emellett szüksége lehet használhatja ugyanazt a biztonsági csoportot az Azure Portalon létrehozott feltételes hozzáférési szabályzatok alkalmazásához.

> [!NOTE]
> Mielőtt letiltaná a feltételes hozzáférési szabályzatokat az Intune klasszikus portálján, tekintse meg a [megkezdése előtt](#before-you-begin) Ez a témakör elején található szakaszában.

### <a name="to-disable-the-conditional-access-policies"></a>A feltételes hozzáférési szabályzatok letiltása

1. Jelentkezzen be hitelesítő adataival az [Intune klasszikus portálon](https://manage.microsoft.com).

2. Válassza a bal oldali menü **Szabályzat** pontját.

3. Válasszon **feltételes hozzáférési**, majd válassza ki a Microsoft felhőszolgáltatást (például Exchange Online vagy SharePoint online-hoz), létrehozott egy feltételes hozzáférési szabályzatot.

4. A jelet **engedélyezése feltételes hozzáférési szabályzat**, és kattintson a **mentése**.

    ![Tiltsa le a feltételes hozzáférési szabályzatokat az Intune klasszikus portálján képe](./media/reassign-ca-18.png)

## <a name="see-also"></a>Lásd még:

- [Az Intune-nal feltételes hozzáférés használatának szokásos módjai](conditional-access-intune-common-ways-use.md)
- [alkalmazásalapú feltételes hozzáférés Intune-nal](app-based-conditional-access-intune.md)
- [Feltételes hozzáférés az Azure Active Directoryban](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)

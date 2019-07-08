---
title: Oktatóanyag – az Intune-nal EMM és az alkalmazás konfigurációjának Slack konfigurálása
titleSuffix: Microsoft Intune
description: Ebben az oktatóanyagban konfigurálhatja az Intune-nal EMM és az alkalmazás konfigurációjának Slack.
keywords: ''
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 06/11/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 55db37c5-0da7-4d9c-8027-525afb1c6349
Customer intent: As an Intune admin, I want to learn how to configure Slack to use Intune for EMM and app configuration..
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e7ff4e1fd9f055268a461d1a81b8a2e31fe3d32b
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/03/2019
ms.locfileid: "67548988"
---
# <a name="tutorial-configure-slack-to-use-intune-for-emm-and-app-configuration"></a>Oktatóanyag: Az Intune-nal EMM és az alkalmazás konfigurációjának Slack konfigurálása

Slack egy csoportmunka-alkalmazás, amely a Microsoft Intune-nal is használhatja.   

Az oktatóanyag során az alábbi lépéseket fogja végrehajtani:
> [!div class="checklist"]
> - Az Intune állítja be a nagyvállalati mobilitási felügyeleti (EMM) provider a Slack vállalati rácsra. Láthatja, hogy a rács terv munkaterületek Intune által felügyelt eszközökhöz való hozzáférés korlátozására.
> - Létrehozhat alkalmazáskonfigurációs szabályzatokat a Slack EMM alkalmazás IOS rendszerű eszközökön és a Slack alkalmazást Android munkahelyi profilos eszközök kezeléséhez.
> - Az Intune beállítása az Android feltételek eszközmegfelelőségi szabályzatokat létrehoznia, és az iOS-eszközök megfelelőségéhez kell megfelelnie.

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon egy ingyenes próbafiókkal](free-trial-sign-up.md).

## <a name="prerequisites"></a>Előfeltételek
Az oktatóanyag végrehajtásához szüksége lesz egy tesztelési bérlőre a következő előfizetésekkel:
- Prémium szintű Azure Active Directory ([ingyenes próbaverzió](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
- Intune-előfizetés ([az ingyenes próbaidőszak](free-trial-sign-up.md))

Is szüksége lesz egy [Slack vállalati rács](https://get.slack.help/hc/articles/360004150931-What-is-Slack-Enterprise-Grid-) tervet.

## <a name="configure-your-slack-enterprise-grid-plan"></a>Az Enterprise rács Slack-csomag konfigurálása
Kapcsolja be a EMM a Slack vállalati rács csomag a következő [Slack a utasításokat](https://get.slack.help/hc/articles/115002579426-Enable-Enterprise-Mobility-Management-for-your-org#step-2:-turn-on-emm) és [Azure Active Directory connect](https://docs.microsoft.com/azure/active-directory/saas-apps/slack-tutorial) , a rács terv identitásszolgáltató (IDP).

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba
Jelentkezzen be az [Intune-ba](https://go.microsoft.com/fwlink/?linkid=2090973) globális rendszergazdaként vagy Intune-beli szolgáltatásadminisztrátorként. Ha létrehozott egy Intune próba-előfizetést, az a fiók lesz a globális rendszergazda, amelyikkel azt létrehozta.

## <a name="set-up-slack-for-emm-on-ios-devices"></a>Állítsa be a Slack for EMM, iOS-eszközök
Az iOS-alkalmazás Slack for EMM hozzáadása az Intune-bérlőhöz, és ahhoz, hogy a szervezet iOS felhasználók férhetnek hozzá a Slack-EMM-szolgáltatóként az Intune-nal konfigurációs szabályzat létrehozása.

### <a name="add-slack-for-emm-to-intune"></a>EMM Slack hozzáadása az Intune-hoz
Slack for EMM hozzáadása egy felügyelt iOS-alkalmazás az Intune-ban, és rendelje hozzá a Slack felhasználók. Alkalmazások platformfüggőek, így Önnek kell egy különálló Intune-alkalmazást a Slack-felhasználók hozzáadása az Android-eszközökön.
1. Válassza ki az Intune-ban **ügyfélalkalmazás** > **alkalmazások** > **Hozzáadás**.
2. Alkalmazás típusa területen, válassza a **Store-alkalmazás – iOS**.
3. Válassza a **Keresés az App Store-ban** lehetőséget. Adja meg a keresési kifejezés "Slack for EMM", és válassza ki az alkalmazást.
4. Válassza ki **alkalmazásadatok** és tetszés szerint állítsa be a módosításokat.
5. Válassza a **Hozzáadás** lehetőséget.
6. A keresősávba írja be a "Slack for EMM", és válassza ki az imént hozzáadott alkalmazás.
7. A kezelés, válassza ki a **hozzárendelések**.
8. Válassza ki **csoport hozzáadása**. Attól függően, akik úgy döntött, hogy hatással lesz, ha be van kapcsolva a Slack, EMM alatt **hozzárendelés-típus** érdemes kiválasztása:
    - **Regisztrált eszközök esetében elérhető** választotta, ha az "Összes tag (beleértve a vendégeket)" vagy a
    - **Elérhető regisztrációval és anélkül** választotta, ha az "Összes tagok (a vendégeket kivéve)" vagy "nem kötelező megadni".
9. Válassza ki **belefoglalt csoportok** , és ellenőrizze az alkalmazás minden felhasználó számára elérhető válassza **Igen**.
10. Kattintson a **OK**, és kattintson a **OK** újra.
11. Kattintson a **Save** (Mentés) gombra.

### <a name="add-an-app-configuration-policy-for-slack-for-emm"></a>A Slack-alkalmazáskonfigurációs szabályzat felvételéhez for EMM-Megoldáshoz
A Slack EMM iOS-es alkalmazáskonfigurációs szabályzat hozzáadása Alkalmazáskonfigurációs szabályzatok felügyelt eszközökön a platform-specifikus, így az Android-eszközökön a Slack-felhasználók számára külön szabályzatot hozzá kell.
1. Válassza ki az Intune-ban **ügyfélalkalmazás** > **alkalmazáskonfigurációs szabályzatok** > **Hozzáadás**.
2. A név adja meg a Slack alkalmazást konfigurációs házirend tesztelése.
3. Eszközregisztráció típusa, válassza a **felügyelt eszközök**.
4. Válassza a Platform, **iOS**.
5. Válassza ki **társított alkalmazás**.
6. A keresősávba írja be a "Slack for EMM", és válassza ki az alkalmazást.
7. Kattintson a **OK**, majd válassza ki **konfigurációs beállítások**. 
    - Információ konfigurációs kulcsokat és azok értékeit, tekintse át a dokumentációt, a "Műszaki" lapján [Slack az AppConfig weblap](https://www.appconfig.org/company/slack/).
8. Válassza ki **OK**, majd válassza ki **Hozzáadás**.
9. A keresősávba írja be a "test a Slack alkalmazást konfigurációs házirend", és válassza ki az imént hozzáadott házirend.
10. A kezelés, válassza ki a **hozzárendelések**.
11. Hozzárendelés a, válassza ki a **minden felhasználó és minden eszköz**.
12. Kattintson a **Save** (Mentés) gombra.

### <a name="optional-create-an-ios-device-compliance-policy"></a>(Nem kötelező) IOS-eszközmegfelelőségi szabályzat létrehozása
Hozzon létre egy Intune eszközmegfelelőségi szabályzatot, ahol megadja, hogy milyen feltételeknek kell teljesülnie ahhoz, hogy az eszköz megfelelő legyen. Ebben az oktatóanyagban iOS-eszközökhöz hozunk létre eszközmegfelelőségi szabályzatot. A megfelelőségi szabályzatok olyan platformspecifikus, így Önnek kell a Slack-felhasználók számára külön szabályzat létrehozása Android-eszközökön.
1. Az Intune-ban válassza az **Eszközmegfelelőség** > **Szabályzatok** > **Szabályzat létrehozása** lehetőséget.
2. A név adja meg az "IOS-es megfelelőségi szabályzat test".
3. A leírás adja meg az "IOS-es megfelelőségi szabályzat test".
4. Válassza a Platform, **iOS**.
5. Válassza az **Eszközállapot** lehetőséget. Jailbreakelt eszközök mellett jelölje ki **blokk**, majd válassza ki **OK**.
6. Válassza ki **rendszerbiztonság** , és adja meg a jelszó-beállításokat. Az oktatóanyag végrehajtásához válassza a következő ajánlott beállításokat:
    - Válassza ki a mobileszközök zárolásának feloldásához jelszó szükséges a **megkövetelése**.
    - Egyszerű jelszavak, válasszon **blokk**.
    - Jelszó minimális hossza adja meg a 4.
    - Kötelező jelszótípus kiválasztása **alfanumerikus**.
    - A képernyőzárolás után perc jelszó kérése ennyi, válassza **azonnal**.
    - A jelszó lejárata (nap), adja meg a 41-es.
    - Hány korábbi jelszó ne legyen újra felhasználhatja, adja meg az 5.
7. Kattintson a **OK**, majd válassza ki **OK** újra.
8. Kattintson a **Create** (Létrehozás) gombra.

## <a name="set-up-slack-on-android-work-profile-devices"></a>Állítsa be a Slack, az Android munkahelyi profilos eszközök
A Slack felügyelt Google Play alkalmazás hozzáadása az Intune-bérlőhöz, és hozzon létre egy konfigurációs szabályzatot ahhoz, hogy a szervezetek számára Androidos felhasználók férhetnek hozzá a Slack-EMM-szolgáltatóként az Intune-nal.

### <a name="add-slack-to-intune"></a>Slack hozzáadása az Intune-hoz
Adja hozzá a Slack, a felügyelt Google play alkalmazás az Intune-ban, és a Slack felhasználók hozzárendelése. Alkalmazások platformfüggőek, így kell hozzáadnia a különálló Intune-alkalmazást a Slack-felhasználók számára az iOS-eszközökön.
1. Válassza ki az Intune-ban **ügyfélalkalmazás** > **alkalmazások** > **Hozzáadás**.
2. Alkalmazás típusa területen, válassza a **Store alkalmazás – felügyelt Google Play**.
3. Válassza ki **jóváhagyása a felügyelt Google Play -** . Adja meg a keresési kifejezés "Slack for EMM", és válassza ki az alkalmazást.
4. Válassza ki **jóváhagyása**.
5. A keresősávba írja be a "Slack", és válassza ki az imént hozzáadott alkalmazás.
6. A kezelés, válassza ki a **hozzárendelések**.
7. Válassza ki **csoport hozzáadása**. Attól függően, akik úgy döntött, hogy hatással lesz, ha be van kapcsolva a Slack, EMM alatt **hozzárendelés-típus** érdemes kiválasztása:
    - **Regisztrált eszközök esetében elérhető** választotta, ha az "Összes tag (beleértve a vendégeket)" vagy a
    - **Elérhető regisztrációval és anélkül** választotta, ha az "Összes tagok (a vendégeket kivéve)" vagy "nem kötelező megadni".
8. Válassza ki a belefoglalt csoportok és a az alkalmazás legyen elérhető minden felhasználó válassza **Igen**.
9. Kattintson a **OK**, és kattintson a **OK** újra.
10. Kattintson a **Save** (Mentés) gombra.

### <a name="add-an-app-configuration-policy-for-slack"></a>A Slack-alkalmazáskonfigurációs szabályzat felvételéhez
A Slack-alkalmazáskonfigurációs szabályzat felvételéhez. Alkalmazáskonfigurációs szabályzatok felügyelt eszközökön a platform-specifikus, így az iOS-eszközökön a Slack-felhasználók számára külön szabályzatot hozzá kell.
1. Válassza ki az Intune-ban **ügyfélalkalmazás** > **alkalmazáskonfigurációs szabályzatok** > **Hozzáadás**.
2. A név adja meg a Slack alkalmazást konfigurációs házirend tesztelése.
3. Eszközregisztráció típusa, válassza a **felügyelt eszközök**.
4. Válassza a Platform, **Android**.
5. Válassza ki **társított alkalmazás**.
6. A keresősávba írja be a "Slack", és válassza ki az alkalmazást.
7. Válassza ki **OK**, majd válassza ki **konfigurációs beállítások**.
    - Információ konfigurációs kulcsokat és azok értékeit, tekintse át a dokumentációt, a "Műszaki" lapján [Slack az AppConfig weblap](https://www.appconfig.org/company/slack/).
8. Kattintson a **OK**, majd válassza ki **Hozzáadás**.
9. A keresősávba írja be a "test a Slack alkalmazást konfigurációs házirend", és válassza ki az imént hozzáadott házirend.
10. A kezelés, válassza ki a **hozzárendelések**.
11. Hozzárendelés a, válassza ki a **minden felhasználó és minden eszköz**.
12. Kattintson a **Save** (Mentés) gombra.

### <a name="optional-create-an-android-device-compliance-policy"></a>(Nem kötelező) Egy Android-eszközök eszközmegfelelőségi szabályzatának létrehozása
Hozzon létre egy Intune eszközmegfelelőségi szabályzatot, ahol megadja, hogy milyen feltételeknek kell teljesülnie ahhoz, hogy az eszköz megfelelő legyen. Ebben az oktatóanyagban létrehozunk egy Android-eszközök eszközmegfelelőségi szabályzatának. A megfelelőségi szabályzatok olyan platformspecifikus, így Önnek kell hozzon létre külön szabályzatot a Slack-felhasználók számára az iOS-eszközökön.
1. Az Intune-ban válassza az **Eszközmegfelelőség** > **Szabályzatok** > **Szabályzat létrehozása** lehetőséget.
2. A nevet írja be a "Androidos megfelelőségi szabályzat test".
3. A leírás adja meg a "Androidos megfelelőségi szabályzat test".
4. Válassza a Platform, **Android Enterprise**.
5. Profil típusa alatt válassza ki a **munkahelyi profil**.
6. Válassza az **Eszközállapot** lehetőséget. A Rootolt eszközök mellett válassza ki a **blokk**, majd válassza ki **OK**.
7. Válassza ki **rendszerbiztonság** , és adja meg **jelszóbeállítások**. Az oktatóanyag végrehajtásához válassza a következő ajánlott beállításokat:
    - Válassza ki a mobileszközök zárolásának feloldásához jelszó szükséges a **megkövetelése**.
    - Kötelező jelszótípus kiválasztása **legalább alfanumerikus karakterek**.
    - Jelszó minimális hossza adja meg a 4.
    - A képernyőzárolás után perc jelszó kérése ennyi, válassza **15 perc**.
    - A jelszó lejárata (nap), adja meg a 41-es.
    - Hány korábbi jelszó ne legyen újra felhasználhatja, adja meg az 5.
8. Kattintson a **OK**, és kattintson a **OK** újra.
9. Kattintson a **Create** (Létrehozás) gombra.

## <a name="launch-slack"></a>Indítsa el a Slack

Szabályzatokkal az imént létrehozott, bármely iOS vagy Android munkahelyi profilos eszközök, amelyek megpróbálnak bejelentkezni egy munkaterületről kell lennie az Intune-ban regisztrált. A forgatókönyv teszteléséhez, próbálja meg egy iOS-eszköz Intune-ban regisztrált vagy az Intune-ban regisztrált Androidos munkahelyi profil eszköz az indításakor Slack EMM Slack indítását. 

## <a name="next-steps"></a>További lépések

Ebben az oktatóanyagban:
- Az Intune a nagyvállalati mobilitási felügyeleti (EMM) provider beállítani a Slack vállalati rácsra. 
- Alkalmazáskonfigurációs szabályzatok kezeléséhez a Slack EMM alkalmazás IOS rendszerű eszközökön és a Slack alkalmazást Android munkahelyi profilos eszközök hozott létre.
- Megfelelőségi szabályzatok beállítása az Android feltételek létrehozott Intune-eszközt, és az iOS-eszközök megfelelőségéhez meg kell felelnie.

Alkalmazáskonfigurációs szabályzatok kapcsolatos további információkért lásd: [a Microsoft Intune alkalmazáskonfigurációs szabályzatai](app-configuration-policies-overview.md). Eszközmegfelelőségi szabályzatokkal kapcsolatos további tudnivalókért lásd: [beállíthat szabályokat az erőforrásokhoz való hozzáférés engedélyezése a munkahelyi Intune-eszközök](device-compliance-get-started.md).
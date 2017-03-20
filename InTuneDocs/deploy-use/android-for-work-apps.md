---
title: "Alkalmazások telepítése Android for Work-eszközökre | Microsoft Docs"
description: "Itt megtudhatja, hogyan szinkronizáljon és telepítsen alkalmazásokat Android for Work-eszközökre a Google Play for Work áruházból."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd0bbd90-d3fe-4efc-83fd-d1f3f86800d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 0936051b5c33a2e98f275ef7a3a32be2e8f5a8b0
ms.openlocfilehash: 3b608d42f04b9fce457b6b61587d05ab5d59bb0a
ms.lasthandoff: 03/10/2017


---

# <a name="how-to-deploy-apps-to-android-for-work-devices-with-intune"></a>Alkalmazások telepítése Android for Work-eszközökre | Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Az alkalmazások Android for Work-eszközökre való telepítése eltér a hagyományos androidos eszközökre való telepítéstől. Minden olyan alkalmazás, amelyet az Android for Work részeként telepít, a Google Play for Work áruházból szerezhető be. Jelentkezzen be az áruházba, keresse meg a kívánt alkalmazást, majd hagyja jóvá a választást.
Az alkalmazás ezt követően a **Mennyiségi licencszerződés keretében vásárolt alkalmazások** csomópontban jelenik meg az Intune-konzolon. Ezen a felületen kezelheti az alkalmazások telepítését, ami ugyanúgy zajlik, mint a hagyományos alkalmazásoknál.

Ha saját üzletági (LOB) alkalmazásokat hozott létre, azokat is telepítheti. Ehhez hozzon létre egy Google Developer-fiókot, amellyel saját területen tehet közzé alkalmazásokat a Google Play áruházban, majd szinkronizálhatja őket az Intune-nal.

## <a name="before-you-start"></a>Előkészületek

1. Győződjön meg róla, hogy az Intune-t és az Android for Work-öt is beállította a közös munkára az Intune-konzol **Felügyelet** lapján.

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Google Play for Work áruházbeli alkalmazások szinkronizálása


1. Nyissa meg a [Google Play for Work áruházat](https://play.google.com/work). Ugyanazzal a fiókkal jelentkezzen be, amellyel beállította az Intune és az Android for Work közötti kapcsolatot.
2. Az áruházban keresse meg az alkalmazást, amelyet telepíteni kíván az Intune-nal.
3. A kiválasztott alkalmazás lapján válassza a **Jóváhagyás** elemet. Ebben a példában a Microsoft Excel alkalmazást választotta.<br>
  ![Alkalmazás jóváhagyása – példa](media/approve.png)
4. Ekkor megjelenik egy ablak, amelyben az alkalmazás engedélyt kér bizonyos műveletek végrehajtására. Válassza ismét a **Jóváhagyás** lehetőséget.<br>
  ![Alkalmazásengedélyek jóváhagyása – példa](media/approve-app-permissions.png)
5. Ezután egy üzenet érkezik, amely megerősíti, hogy az alkalmazás jóvá lett hagyva és elérhető a rendszergazdai konzolon.

## <a name="publish-then-synchronize-a-line-of-business-app-from-the-google-play-for-work-store"></a>Üzletági alkalmazások közzététele és szinkronizálása a Google Play for Work áruházban

1. Nyissa meg a Google Play Developer Console-t a [play.google.com/apps/publish](https://play.google.com/apps/publish) címen.
2. Ugyanazzal a fiókkal jelentkezzen be, amellyel beállította az Intune és az Android for Work közötti kapcsolatot. Az első bejelentkezés előtt regisztrálni kell, továbbá megfizetni a Google Developer-program regisztrációs díját.
3. A konzolon válassza az **Add new application** (Új alkalmazás hozzáadása) elemet.
4. Az alkalmazások és azok információinak feltöltése ugyanúgy történik, mint bármelyik alkalmazás közzététele a Google Play áruházban. Ugyanakkor ki kell választani az **Only make this application available to my organization (<*organization name*>)** (Az alkalmazás elérhetővé tétele csak a saját szervezet tagjai számára (<szervezet neve>)**) lehetőséget, ahogy alább is látható.<br>
  ![Az alkalmazás elérhetővé tétele csak a saját szervezet számára beállítás](media/restrict.png)<br>
Ezzel gondoskodhat róla, hogy az alkalmazás csak az Ön szervezete számára legyen elérhető, a Google Play áruház nyilvános területein ne.
További információt az androidos alkalmazások feltöltéséről és közzétételéről a [Google Developer Console Help](https://support.google.com/googleplay/android-developer/answer/113469) súgóközpontban talál.
5. Miután feltöltötte az alkalmazást, lépjen be a [Google Play for Work áruházba](https://play.google.com/work). Ugyanazzal a fiókkal jelentkezzen be, amellyel beállította az Intune és az Android for Work közötti kapcsolatot.
6. Az áruház **Alkalmazások** csomópontjában ellenőrizze, hogy látja-e a közzétett alkalmazást. Vegye figyelembe, hogy az alkalmazás automatikusan megkapta az engedélyt arra, hogy szinkronizáljon az Intune-nal.

## <a name="deploy-an-android-for-work-app"></a>Android for Work-alkalmazások telepítése

Ha jóváhagyott egy áruházból beszerzett alkalmazást, de nem látja az **Alkalmazások** munkaterület **Mennyiségi licencszerződés keretében vásárolt alkalmazások** csomópontjában, az alábbi lépésekkel kényszerítheti a szinkronizálást:

1. Az [Intune felügyeleti konzolon](https://manage.microsoft.com) kattintson a **Felügyelet** > **Mobileszköz-kezelés** > **Android for Work** elemre.
2. **Az Android for Work mobileszköz-kezelési beállításai** lapon válassza a **Szinkronizálás most** lehetőséget.
3. A lapon látható az utolsó szinkronizálás időpontja és állapota is.

Ha az alkalmazás megjelenik az **Alkalmazások** munkaterület **Mennyiségi licencszerződés keretében vásárolt alkalmazások** csomópontjában, akkor [ugyanúgy telepítheti, mint bármelyik alkalmazást](deploy-apps-in-microsoft-intune.md). Az alkalmazások úgy is telepíthetők, hogy csak bizonyos felhasználói csoportok érjék el. Egyelőre csak a **Kötelező** és az **Eltávolítás** lehetőségek elérhetők.

Az alkalmazások **Elérhetőként** való telepítésének lehetősége már az új csoportosítási és célzási megoldást használja. Az újonnan létrehozott Intune-szolgáltatásfiókok használhatják ezt a funkciót, amint az megjelenik. A meglévő Intune-ügyfelek azt követően használhatják élesben ezt a funkciót, hogy a bérlőjüket áttelepítették az Intune Azure-portálra. Meglévő ügyfeleinknek azt a lehetőséget kínáljuk, hogy egy próba Intune-fiók segítségével tervezzék meg és teszteljék ezt a funkciót, amíg sor nem kerül a bérlőjük migrálására.

A telepítés után az alkalmazás elérhető lesz a kijelölt eszközökön. Az eszköz használójának a hozzájárulását a rendszer nem kéri.

## <a name="manage-app-permissions"></a>Alkalmazásengedélyek kezelése
Az Android for Work használatához jóvá kell hagynia az alkalmazásokat a Google által felügyelt Play webkonzolon, mielőtt az Intune-ba szinkronizálná és a felhasználók számára üzembe helyezné azokat.  Mivel az Android for Work lehetővé teszi az alkalmazások automatikus és csendes leküldését a felhasználói eszközökre, az alkalmazások által kért engedélyeket el kell fogadnia az összes felhasználó nevében.  A felhasználók számára a telepítésnél nem jelennek meg alkalmazásengedélyek, ezért fontos, hogy Ön elolvassa és megértse ezeket az engedélyeket.

Ha az alkalmazás fejlesztője megváltozott engedélyekkel rendelkező új alkalmazásverziót tesz közzé, az új engedélyek nem lesznek automatikusan elfogadva akkor sem, ha Ön az előző verzió engedélykéréseit elfogadta. Az alkalmazás régebbi verzióját futtató eszközök továbbra is használhatják az alkalmazást, de frissítésre nem kerül sor, amíg el nem fogadja az új engedélyeket. Az alkalmazással még nem rendelkező eszközökre nem telepíthető az alkalmazás, amíg el nem fogadja az új alkalmazásengedélyeket.

### <a name="how-to-update-app-permissions"></a>Alkalmazásengedélyek frissítése

Javasolt rendszeresen ellenőrizni a felügyelt Google Play konzolon, hogy vannak-e új alkalmazásengedélyek. Ha egy alkalmazás központi telepítés után sincs telepítve, az alábbi lépéseket követve ellenőrizze, hogy vannak-e új alkalmazásengedélyek:

1. Keresse fel a http://play.google.com/work webhelyet
2. Jelentkezzen be azzal a Google-fiókkal, amelyet az alkalmazások közzétételénél és jóváhagyásánál használt.
3. A **Frissítések** lapon ellenőrizze, hogy szükséges-e alkalmazásokat frissíteni.  A listában szereplő összes alkalmazás új engedélyeket kér, és nem telepíthető, amíg azokat el nem fogadják.  

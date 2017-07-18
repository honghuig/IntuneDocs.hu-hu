---
title: "Bevezetés a Microsoft Intune App SDK használatába"
description: "A mobilalkalmazások gyors engedélyezése a Microsoft Intune-beli mobilalkalmazás-felügyelet (MAM) használatához."
keywords: 
author: mtillman
manager: angrobe
ms.author: oydang
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1d61432eafef67ca997d4e03d305e1c068ac5fd6
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/01/2017
---
# <a name="get-started-with-the-microsoft-intune-app-sdk"></a>Bevezetés a Microsoft Intune App SDK használatába

Ez az útmutató segítséget nyújt a mobilalkalmazás gyors engedélyezéséhez a Microsoft Intune-beli mobilalkalmazás-felügyelet használatához. Javasoljuk, hogy először tájékozódjon az Intune App SDK előnyeiről, amelyekről [Az Intune App SDK áttekintése](app-sdk.md) című témakörben olvashat bővebben.

Az Intune App SDK hasonló lehetőségeket támogat az Android és az iOS esetében is, és célja, hogy egységes, platformfüggetlen felhasználói élményt teremtsen a rendszergazdáknak. A platformok korlátozásai miatt azonban bizonyos funkciók támogatásában kisebb különbségek vannak.

## <a name="register-your-store-app-with-microsoft"></a>Áruházbeli alkalmazás regisztrálása a Microsoftnál

### <a name="if-your-app-is-internal-to-your-organization-and-will-not-be-publicly-available"></a>Ha az alkalmazás a munkahelyén belüli, és nem lesz nyilvánosan elérhető:

*Nem kell* regisztrálnia az alkalmazást. Belső, saját üzleti használatra való alkalmazások esetében a rendszergazda fogja a cégen belül telepíteni az alkalmazást. Az Intune észlelni fogja, hogy az alkalmazást az SDK-val állították össze, és lehetővé teszi a rendszergazda számára, hogy az alkalmazásra vonatkozó alkalmazásvédelmi szabályzatot léptessen érvénybe. Lépjen az [iOS vagy Android rendszerhez készült alkalmazás engedélyezése alkalmazásvédelmi szabályzat használatához](#enable-your-iOS-or-Android-app-for-app-protection-policy) című részre.

### <a name="if-your-app-will-be-released-to-a-public-app-store-like-the-apple-app-store-or-google-play"></a>Ha az alkalmazás elérhető lesz nyilvános alkalmazás-áruházban, például az Apple App Store-ban vagy a Google Play áruházban:

Először _**regisztrálnia kell**_ az alkalmazást a Microsoft Intune-nál, és el kell fogadnia a regisztrációs feltételeket. Ezt követően a rendszergazdák alkalmazásvédelmi szabályzatot alkalmazhatnak a felkészített alkalmazásra, amely Intune-alkalmazáspartnerként lesz látható.

Az Intune-rendszergazdák nem alkalmazhatják az alkalmazásvédelmi szabályzatot az alkalmazás mélyhivatkozására, amíg el nem végezte a regisztrációt, és a Microsoft Intune-csapat meg nem erősítette azt. A Microsoft felveszi az alkalmazást a [Microsoft Intune-partnerek lapjára](https://www.microsoft.com/cloud-platform/microsoft-intune-apps). Az alkalmazás ikonja jelzi, hogy az alkalmazás támogatja az Intune alkalmazásvédelmi szabályzatait.

A regisztráció megkezdéséhez töltse ki a [Microsoft Intune alkalmazás partnerkérdőívét](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR6oOVGFZ3pxJmwSN1N_eXwJUQUc5Mkw2UVU0VzI5WkhQOEYyMENWNDBWRS4u).

A kérdőívben megadott e-mail-címek egyikén felvesszük Önnel a kapcsolatot, és elindítjuk a regisztráció folyamatát. Emellett regisztrációs e-mail-címén is felvesszük a kapcsolatot Önnel, ha bármilyen kétségeink lennének.

> [!NOTE]
> A Microsoft a fenti kérdőívről és az Intune csapatával váltott e-mailekből gyűjtött összes adat esetében betartja a [Microsoft adatvédelmi nyilatkozatát](https://www.microsoft.com/privacystatement/default.aspx).

**Mire számítson a regisztrációs folyamat során**:

1. Miután elküldte a kérdőívet, a megadott regisztrációs e-mail-címen felveszük Önnel a kapcsolatot, hogy ellenőrizzük, elérjük-e Önt ezen a címen, vagy hogy további információkat kérjünk a regisztráció befejezéséhez.

2. Ha minden szükséges információ beérkezett, elküldjük aláírásra a Microsoft Intune alkalmazás partnerszerződését. Ez a szerződés tartalmazza azokat a feltételeket, amelyeket vállalatának el kell fogadnia ahhoz, hogy Microsoft Intune-alkalmazáspartner lehessen.

3. Akkor is értesítjük, ha megtörtént az alkalmazás regisztrációja a Microsoft Intune rendszerében, és az alkalmazás megjelent a [Microsoft Intune-partnerek](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) webhelyén.

4. Ezenfelül az alkalmazás mélyhivatkozását felvesszük a következő havi Intune-szolgáltatásfrissítésbe is. Ha például a regisztrációs adatokat júliusban töltötte ki, az alkalmazás mélyhivatkozása augusztus közepétől támogatott.

Ha a jövőben változik az alkalmazás mélyhivatkozása, újra kell regisztrálnia az alkalmazást.

> [!NOTE]
> Kérjük, értesítsen minket, ha az alkalmazást az Intune App SDK új verziójával frissíti.



## <a name="download-the-sdk-files"></a>Az SDK-fájlok letöltése

A natív iOS-hez, illetve Androidhoz készült Intune App SDK-k egy Microsoft GitHub-fiókban találhatók. Az alábbi két nyilvános adattár tartalmazza a natív iOS-hez, illetve Androidhoz készült SDK-fájlokat:

* [Intune App SDK iOS rendszerhez](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)
* [Intune App SDK Android rendszerhez](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)

Ha Xamarin- vagy Cordova-alkalmazást kíván felvenni, használja a következő SDK-változatokat:

* [Intune App SDK Xamarin összetevő](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)
* [Intune App SDK Cordova beépülő modul](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)

Érdemes regisztrálnia egy GitHub-fiókot, hogy leágazhasson az adattárakból, és lehúzhassa a változásokat. A GitHub révén a fejlesztők kommunikálni tudnak a termékcsapattal, hibákat jelenthetnek, és gyors válaszokat kaphatnak, elolvashatják a kibocsátási megjegyzéseket, valamint visszajelzést adhatnak a Microsoftnak. Az Intune App SDK GitHubra vonatkozó kérdései az msintuneappsdk@microsoft.com címen teheti fel.





## <a name="enable-your-ios-or-android-app-for-app-protection-policy"></a>IOS vagy Android rendszerhez készült alkalmazás engedélyezése alkalmazásvédelmi szabályzat használatához

A következő fejlesztői útmutatók segítséget nyújtanak az Intune App SDK integrálásához az alkalmazásába:

* **[iOS-hez készült Intune App SDK – fejlesztői útmutató](app-sdk-ios.md)**: Ez a dokumentum részletesen ismerteti a natív iOS-alkalmazásnak az Intune App SDK-val való engedélyezésének lépéseit.

* **[Androidhoz készült Intune App SDK – fejlesztői útmutató](app-sdk-android.md)**: Ez a dokumentum részletesen ismerteti a natív androidos alkalmazásnak az Intune App SDK-val való engedélyezésének lépéseit.

* **[Az Intune App SDK Cordova beépülő moduljának útmutatója](app-sdk-cordova.md)**: Ez a dokumentum segít iOS- és Android-alkalmazások összeállításában a Cordova használatával az Intune alkalmazásvédelmi szabályzataihoz.

* **[Az Intune App SDK Xamarin összetevőjének útmutatója](app-sdk-xamarin.md)**: Ez a dokumentum segít iOS- és Android-alkalmazások összeállításában a Cordova használatával az Intune alkalmazásvédelmi szabályzataihoz.




## <a name="configure-telemetry-for-your-app"></a>Telemetria konfigurálása az alkalmazásra vonatkozóan

A Microsoft Intune statisztikát gyűjt az alkalmazás használatáról.

* **iOS-hez készült Intune App SDK**: Az SDK alapértelmezés szerint naplózza a használati események SDK-telemetriai adatait. Az adatokat az SDK a Microsoft Intune-nak küldi el.

    * Ha úgy dönt, hogy nem kíván SDK-ból származó telemetriai adatokat küldeni a Microsoft Intune-nak az alkalmazásából, le kell tiltania az SDK-ban a telemetria-átvitelt az IntuneMAMSetting könyvtárban található `MAMTelemetryDisabled` tulajdonság „YES” értékre való állításával.


* **Androidhoz készült Intune App SDK**: A telemetriai adatokat a program nem naplózza az SDK használatával.

## <a name="next-steps-after-integration"></a>Az integrációt követő lépések

### <a name="test-your-app"></a>Az alkalmazás tesztelése
Miután elvégezte az iOS vagy Android alkalmazásnak az Intune App SDK-való integrálásához szükséges lépéseket, meg kell győződnie arról, hogy a felhasználóknál és a rendszergazdánál engedélyezve vannak és működnek az alkalmazásvédelmi szabályzatok. Az integrált alkalmazás teszteléséhez a következőkre lesz szüksége:

* **Microsoft Intune-tesztfiók**: Az Intune használatára előkészített alkalmazása Intune-beli alkalmazásvédelmi funkcióinak teszteléséhez Microsoft Intune-fiók szükséges.

    * Ha független szoftverszállítóként engedélyezi az Intune alkalmazásvédelmi szabályzatának használatához az iOS vagy Android rendszerhez készült áruházbeli alkalmazásait, a regisztráció (az ezt ismertető lépésben leírt módon történő) befejezése után kapni fog egy promóciós kódot. A promóciós kód lehetővé teszi, hogy feliratkozzon a Microsoft Intune próbaverziójának 1 évig meghosszabbított használatára.

    * Az áruházban nem közzéteendő üzleti alkalmazások fejlesztői az adott szervezeten keresztül kaphatnak hozzáférést a Microsoft Intune-hoz. Emellett feliratkozhat a [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0) egyhónapos ingyenes próbaidőszakára is.

* **Az Intune alkalmazásvédelmi szabályzatai**: Ha az alkalmazását az összes Intune-beli alkalmazásvédelmi szabályzattal tesztelni szeretné, akkor minden szabályzatbeállításnál tudnia kell, mi a várt viselkedés. Lásd az [iOS alkalmazásvédelmi szabályzatainak](/intune-classic/deploy-use/ios-mam-policy-settings) és az [Android alkalmazásvédelmi szabályzatainak](/intune-classic/deploy-use/android-mam-policy-settings) ismertetését.

* **Hibaelhárítás**: Ha problémákat tapasztal az alkalmazás használata során tapasztalható felhasználói élmény manuális tesztelésekor, nézze át [A MAM hibaelhárítása](/intune-classic/troubleshoot/troubleshoot-mam) című szakaszt. Ez a cikk az Intune-hoz előkészített alkalmazásokban esetleg előforduló gyakoribb problémákhoz, párbeszédpanelekhez és hibaüzenetekhez nyújt segítséget. 

### <a name="badge-your-app-optional"></a>Az alkalmazás megjelölése jelvénnyel (nem kötelező)

Miután meggyőződött róla, hogy az Intune alkalmazásvédelmi szabályzatai működnek az alkalmazásában megjelölheti az alkalmazás ikonját az Intune alkalmazásvédelmi emblémájával.

Ez a jelvény jelzi a rendszergazdáknak, végfelhasználóknak és a leendő Intune-ügyfeleknek, hogy az alkalmazása az Intune alkalmazásvédelmi szabályzataival működik. Ezáltal elősegíti az alkalmazás Intune-ügyfelek általi használatát és adoptálását.

A jelvény egy aktatáska formájú ikon, amely az alábbi mintákon látható:

![Jelvény, 1. példa](./media/badge-example-1.png) ![Jelvény, 2. példa](./media/badge-example-2.png)

**Az alkalmazás jelvénnyel való megjelöléséhez az alábbiak szükségesek**:

* Egy képszerkesztő alkalmazás, amely képes olvasni az **.eps** kiterjesztésű fájlokat, vagy egy Adobe-alkalmazás, amely képes olvasni az **.ai**-fájlokat.

* Az [Intune alkalmazásjelvény erőforrásait és irányelveit](https://github.com/msintuneappsdk/intune-app-partner-badge) a Microsoft Intune GitHubban találja.
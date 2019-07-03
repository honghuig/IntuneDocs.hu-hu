---
title: Bevezetés a Microsoft Intune App SDK használatába
description: A mobilalkalmazások gyors engedélyezése a Microsoft Intune-beli mobilalkalmazás-felügyelet (MAM) használatához.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9e9a50855a26b72b2f6589d9f44ce6deea0588fa
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67529181"
---
# <a name="get-started-with-the-microsoft-intune-app-sdk"></a>Bevezetés a Microsoft Intune App SDK használatába

Ez az útmutató segítséget nyújt az alkalmazásvédelmi szabályzatok Microsoft Intune-nal támogatásához a mobilalkalmazás gyors engedélyezéséhez. Javasoljuk, hogy először tájékozódjon az Intune App SDK előnyeiről, amelyekről [Az Intune App SDK áttekintése](app-sdk.md) című témakörben olvashat bővebben.

Az Intune App SDK hasonló lehetőségeket támogat az Android és az iOS esetében is, és célja, hogy egységes, platformfüggetlen felhasználói élményt teremtsen a rendszergazdáknak. Azonban bizonyos funkciók támogatásában kisebb különbségek vannak platform eltérés és korlátozás miatt.

## <a name="register-your-store-app-with-microsoft"></a>Áruházbeli alkalmazás regisztrálása a Microsoftnál

### <a name="if-your-app-is-internal-to-your-organization-and-will-not-be-publicly-available"></a>Ha az alkalmazás a munkahelyén belüli, és nem lesz nyilvánosan elérhető:

Ön _**nem kell**_ regisztrálnia az alkalmazást. A belső [üzletági (LOB) alkalmazások](apps-add.md#app-types-in-microsoft-intune) , amely úgy írtak szerint, vagy a vállalat a rendszergazda fogja cégen belül telepíteni az alkalmazást. Az Intune észlelni fogja, hogy az alkalmazás az SDK-val állították össze, és lehetővé teszi a rendszergazda alkalmazásvédelmi szabályzatok vonatkoznak rá. Lépjen az [iOS vagy Android rendszerhez készült alkalmazás engedélyezése alkalmazásvédelmi szabályzat használatához](#enable-your-ios-or-android-app-for-app-protection-policy) című részre.

### <a name="if-your-app-will-be-released-to-a-public-app-store-like-the-apple-app-store-or-google-play"></a>Ha az alkalmazás elérhető lesz nyilvános alkalmazás-áruházban, például az Apple App Store-ban vagy a Google Play áruházban:

Először _**regisztrálnia kell**_ az alkalmazást a Microsoft Intune-nál, és el kell fogadnia a regisztrációs feltételeket. A rendszergazdák alkalmazásvédelmi szabályzatot alkalmazhatja a felügyelt alkalmazást, amely lesz látható, hogy egy [az Intune által védett alkalmazás partner](apps-supported-intune-apps.md#partner-apps).

Az Intune-rendszergazdák nem alkalmazhatják az alkalmazásvédelmi szabályzatot az alkalmazás mélyhivatkozására, amíg el nem végezte a regisztrációt, és a Microsoft Intune-csapat meg nem erősítette azt. A Microsoft felveszi az alkalmazást a [Microsoft Intune-partnerek lapjára](https://www.microsoft.com/cloud-platform/microsoft-intune-apps). Az alkalmazás ikonja jelzi, hogy az alkalmazás támogatja az Intune alkalmazásvédelmi szabályzatait.

### <a name="the-registration-process"></a>A regisztrációs folyamat
A regisztrációs folyamat megkezdéséhez, ha még nem működik együtt a Microsoft egy kapcsolattartójával, töltse ki a [Microsoft Intune-alkalmazáspartneri kérdőívet](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR80SNPjnVA1KsGiZ89UxSdVUMEpZNUFEUzdENENOVEdRMjM5UEpWWjJFVi4u).

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

Ha Xamarin-alkalmazásról van szó, használja a következő SDK-változatot:

* [Intune App SDK Xamarin-kötések](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)

Érdemes regisztrálnia egy GitHub-fiókot, hogy leágazhasson az adattárakból, és lehúzhassa a változásokat. A GitHub révén a fejlesztők kommunikálni tudnak a termékcsapattal, hibákat jelenthetnek, és gyors válaszokat kaphatnak, elolvashatják a kibocsátási megjegyzéseket, valamint visszajelzést adhatnak a Microsoftnak. Az Intune App SDK GitHubra vonatkozó kérdései az msintuneappsdk@microsoft.com címen teheti fel.

## <a name="enable-your-ios-or-android-app-for-app-protection-policy"></a>IOS vagy Android rendszerhez készült alkalmazás engedélyezése alkalmazásvédelmi szabályzat használatához

A következő fejlesztői útmutatók segítséget nyújtanak az Intune App SDK integrálásához az alkalmazásába:

* **[Intune App SDK – Fejlesztői útmutató iOS](app-sdk-ios.md)** : Ez a dokumentum részletesen ismerteti a natív iOS-alkalmazásnak az Intune App SDK-val való engedélyezésének.

* **[Intune App SDK Androidon – útmutató fejlesztőknek](app-sdk-android.md)** : Ez a dokumentum részletesen ismerteti a natív Androidos alkalmazásnak az Intune App SDK-val való engedélyezésének.

* **[Útmutató az Intune App SDK Xamarin Bindings](app-sdk-xamarin.md)** : Ez a dokumentum segít iOS és Android-alkalmazások Xamarin használatával az Intune alkalmazásvédelmi szabályzatokat hozhat létre.



## <a name="enable-your-ios-or-android-app-for-app-based-conditional-access"></a>Engedélyezze az iOS vagy Android alkalmazásnak az alkalmazásalapú feltételes hozzáférés
 
 Alkalmazásvédelmi szabályzat az alkalmazás egyrészt az alábbi szükség az alkalmazás megfelelően függvényt az Azure Active Directory (AAD) alkalmazás alapú feltételes hozzáférés:
 
 * Az alkalmazást az [Azure ActiveDirectory Authentication Library](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) használatával hozták létre, és engedélyezve van az AAD-brokerrel történő hitelesítéshez.
 
 * Az alkalmazás [AAD-ügyfélazonosítójának](https://docs.microsoft.com/azure/app-service/app-service-mobile-how-to-configure-active-directory-authentication#configure-a-native-client-application) egyedinek kell lennie az iOS-es és androidos platformokon egyaránt.
 
## <a name="configure-telemetry-for-your-app"></a>Telemetria konfigurálása az alkalmazásra vonatkozóan

A Microsoft Intune statisztikát gyűjt az alkalmazás használatáról.

* **IOS-hez készült Intune App SDK**: Az SDK alapértelmezés szerint naplózza a használati események SDK-telemetriai adatokat. Az adatokat az SDK a Microsoft Intune-nak küldi el.

    * Ha úgy dönt, hogy nem kíván SDK-ból származó telemetriai adatokat küldeni a Microsoft Intune-nak az alkalmazásából, le kell tiltania az SDK-ban a telemetria-átvitelt az IntuneMAMSetting könyvtárban található `MAMTelemetryDisabled` tulajdonság „YES” értékre való állításával.

* **Androidhoz készült Intune App SDK**: Az Androidhoz készült Intune App SDK nem szabályozza az alkalmazásából való adatgyűjtést. Az Céges portál alkalmazás alapértelmezés szerint telemetriai adatokat naplóz. Az adatokat az SDK a Microsoft Intune-nak küldi el. A Microsoft szabályzatának megfelelően nem gyűjtünk személyazonosításra alkalmas adatokat (PII). 

    * Ha a végfelhasználók nem szeretnének ilyen adatokat küldeni, ki kell kapcsolniuk a telemetriát a Céges portál alkalmazás Beállítások menüpontjában. További információt [A használatra vonatkozó adatok Microsoft általi gyűjtésének kikapcsolása](https://docs.microsoft.com/intune-user-help/turn-off-microsoft-usage-data-collection-android) című témakörben találhat. 

## <a name="line-of-business-app-version-numbers"></a>Üzletági alkalmazások verziószámai

Az Intune üzletági alkalmazásai mostantól megjelenítik az iOS- és Android-alkalmazások verziószámait. A számok az Azure Portal alkalmazáslistáján, valamint az Alkalmazás áttekintése panelen jelennek meg. A végfelhasználók az alkalmazásszámot a céges portál alkalmazásban és a webportálon tekinthetik meg.

### <a name="full-version-number"></a>Teljes verziószám

A teljes verziószám az alkalmazás egy adott verzióját azonosítja. A szám az alábbi formátumban jelenik meg: _Verzió_(_Build_). Például: 2.2(2.2.17560800). 

A teljes verziószám két részből áll:

 - **Verzió**  
   A verziószám az alkalmazás természetes nyelven olvasható kiadási száma. A végfelhasználók ezzel azonosítják az alkalmazás különböző kiadásait.

 - **Buildszám**  
    A buildszám egy olyan belső szám, amelyet alkalmazásdetektáláshoz és az alkalmazások szoftveres felügyeletéhez használnak. A buildszám az alkalmazás olyan iterációira vonatkozik, amely a kód változásaira hivatkozik.

### <a name="version-and-build-number-in-android-and-ios"></a>Verzió- és buildszám az Android és az iOS rendszerben

Az Android és az iOS is verzió- és buildszámokkal hivatkozik az alkalmazásokra. Azonban mindkét operációs rendszer rendelkezik kizárólag az operációs rendszerre vonatkozó jelentésekkel. Az alábbi táblázat ismerteti, milyen kapcsolatban állnak egymással ezek a kifejezések.

Az Intune-ban használandó üzletági alkalmazások fejlesztésekor ne feledje a verzió- és a buildszámot is használni. Az Intune alkalmazásfelügyeleti funkciói egy kifejező **CFBundleVersion**- (iOS) és egy **PackageVersionCode**-számot (Android) használnak. Ezek a számok megtalálhatók az alkalmazásjegyzékben. 

Intune|iOS|Android|Leírás|
|---|---|---|---|
Verziószám|CFBundleShortVersionString|PackageVersionName |Ez a szám az alkalmazás egy adott kiadását jelzi a végfelhasználóknak.|
Buildszám|CFBundleVersion|PackageVersionCode |Ez a szám az alkalmazáskód egy iterációját jelzi.|

#### <a name="ios"></a>iOS

- **CFBundleShortVersionString**  
    A csomag kiadási verziószámát határozza meg. Ez a szám az alkalmazás egy megjelent verzióját azonosítja. A végfelhasználók ezzel hivatkoznak az alkalmazásra.
- **CFBundleVersion**  
    A csomag buildverziója, amely a csomag egy iterációját azonosítja. A szám egy kiadott vagy még meg nem jelent csomagot is azonosíthat. A számot alkalmazásdetektáláshoz használják.

#### <a name="android"></a>Android

 - **PackageVersionName**  
    A felhasználók számára megjelenő verziószám. Ez az attribútum megadható nyers sztringként vagy egy sztringerőforrás hivatkozásaként is. A sztringnek a felhasználók számára való megjelenésen kívül nincs célja.
 - **PackageVersionCode**  
    Belső verziószám. Ezzel a számmal határozható meg, hogy egy verzió újabb-e egy másiknál. A magasabb számok újabb verziókat jelentenek. Ez nem az a verzió 

## <a name="next-steps-after-integration"></a>Az integrációt követő lépések

### <a name="test-your-app"></a>Az alkalmazás tesztelése
Miután elvégezte az iOS vagy Android alkalmazásnak az Intune App SDK-való integrálásához szükséges lépéseket, meg kell győződnie arról, hogy a felhasználóknál és a rendszergazdánál engedélyezve vannak és működnek az alkalmazásvédelmi szabályzatok. Az integrált alkalmazás teszteléséhez a következőkre lesz szüksége:

* **A Microsoft Intune-tesztfiók**: Az Intune által kezelt alkalmazás az Intune alkalmazásvédelmi funkcióinak teszteléséhez szüksége lesz egy Microsoft Intune-fiók.

    * Ha független szoftverszállítóként engedélyezi az Intune alkalmazásvédelmi szabályzatának használatához az iOS vagy Android rendszerhez készült áruházbeli alkalmazásait, a regisztráció (az ezt ismertető lépésben leírt módon történő) befejezése után kapni fog egy promóciós kódot. A promóciós kód lehetővé teszi, hogy feliratkozzon a Microsoft Intune próbaverziójának 1 évig meghosszabbított használatára.

    * Az áruházban nem közzéteendő üzleti alkalmazások fejlesztői az adott szervezeten keresztül kaphatnak hozzáférést a Microsoft Intune-hoz. Emellett feliratkozhat a [Microsoft Intune](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0) egyhónapos ingyenes próbaidőszakára is.

    * Ha teszteli az alkalmazás egy mobileszközön, egy olyan felhasználói fiókkal, győződjön meg arról, hogy az adott fiók által az Intune-licencet a Microsoft 365 felügyeleti központ webhelyen Ha egy rendszergazdai fiókkal bejelentkezik, lásd: [licenc hozzárendelése a Microsoft Intune-ban ](https://docs.microsoft.com/intune/licenses-assign).

* **Az Intune alkalmazásvédelmi szabályzatai**: Tesztelje az alkalmazását az Intune alkalmazásvédelmi szabályzatok, ismernie kell, az elvárt viselkedés mi minden egyes házirend-beállítás. Lásd az [iOS alkalmazásvédelmi szabályzatainak](app-protection-policy-settings-ios.md) és az [Android alkalmazásvédelmi szabályzatainak](app-protection-policy-settings-android.md) ismertetését. Ha az alkalmazás integrálva van az Intune SDK-t, de nem szerepel az Azure Portalon célzott alkalmazásként még, is cél szabályzat kiválasztásával a "+ további alkalmazásokat" beállítás, és az alkalmazásköteg-azonosító (iOS) vagy csomagnév (Android) a szövegmezőbe.

* **Hibaelhárítás**: Ha problémákat tapasztal az alkalmazás telepítési felhasználói élmény manuális tesztelésekor közben, lásd: [alkalmazás telepítési problémák elhárítása](troubleshoot-app-install.md). 

### <a name="give-your-app-access-to-the-intune-app-protection-service-optional"></a>Az alkalmazás-hozzáférést biztosít az Intune app protection szolgáltatás (nem kötelező)

Ha az alkalmazás a saját egyéni Azure Active Directory (AAD) beállításokat használja a hitelesítéshez, majd az alábbi lépéseket kell tenni mind nyilvános áruházbeli alkalmazások, valamint belső ÜZLETÁGI alkalmazásokat. A lépések **nem kell tenni, ha az alkalmazás az Intune SDK alapértelmezett ügyfél-Azonosítót használja**. 

Miután regisztrálta az alkalmazást egy Azure-bérlő belül, és alatt látható **minden alkalmazás**, meg kell adni az alkalmazás hozzáférjen az Intune app protection szolgáltatáshoz (korábbi nevén MAM-szolgáltatásban). Az Azure Portalon:

1. Nyissa meg a **Azure Active Directory** panelen.
2. A **alkalmazásregisztrációk**, nyissa meg a listában állítsa be az alkalmazáshoz.
3. Kattintson a **+ adjon hozzá egy engedélyt**.
4. Kattintson a **API-k saját szervezete**. 
5. A keresőmezőbe írja be a **Microsoft Mobile Application Management** (Microsoft mobilalkalmazás-kezelés) kifejezést.
6. A **delegált engedélyek**, jelölje be a **DeviceManagementManagedApps.ReadWrite: A felhasználó alkalmazás-felügyeleti adatok olvasását és írását*** jelölőnégyzetet.
7. Kattintson a **engedélyek hozzáadása**.

### <a name="badge-your-app-optional"></a>Az alkalmazás megjelölése jelvénnyel (nem kötelező)

Miután meggyőződött róla, hogy az Intune alkalmazásvédelmi szabályzatai működnek az alkalmazásában megjelölheti az alkalmazás ikonját az Intune alkalmazásvédelmi emblémájával.

Ez a jelvény jelzi a rendszergazdáknak, végfelhasználóknak és a leendő Intune-ügyfeleknek, hogy az alkalmazása az Intune alkalmazásvédelmi szabályzataival működik. Ezáltal elősegíti az alkalmazás Intune-ügyfelek általi használatát és adoptálását.

A jelvény egy aktatáska formájú ikon, amely az alábbi mintákon látható:

![Az Intune alkalmazásvédelmi szabályzatai - jelvény, 1. példa](./media/badge-example-1.png) ![Az Intune alkalmazásvédelmi szabályzatai - jelvény, 2. példa](./media/badge-example-2.png)

**Az alkalmazás jelvénnyel való megjelöléséhez az alábbiak szükségesek**:

* Egy képszerkesztő alkalmazás, amely képes olvasni az **.eps** kiterjesztésű fájlokat, vagy egy Adobe-alkalmazás, amely képes olvasni az **.ai**-fájlokat.

* Az [Intune alkalmazásjelvény erőforrásait és irányelveit](https://github.com/msintuneappsdk/intune-app-partner-badge) a Microsoft Intune GitHubban találja.

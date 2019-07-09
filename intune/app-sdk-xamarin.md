---
title: Microsoft Intune App SDK Xamarin Bindings
description: Az Intune App SDK Xamarin Bindings lehetővé teszik az Intune alkalmazásvédelmi szabályzatok használatát a Xamarinnal készített iOS- és Android-alkalmazásokban.
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 80b6272c6e1f2efc1687fa25216487595a9ddd9f
ms.sourcegitcommit: 1b7ee2164ac9490df4efa83c5479344622c181b5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/08/2019
ms.locfileid: "67648961"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Microsoft Intune App SDK Xamarin Bindings

> [!NOTE]
> Először célszerű elolvasnia az [Intune App SDK használatának első lépései](app-sdk-get-started.md) című cikket, amely bemutatja az integráció előkészítését a támogatott platformokon.

## <a name="overview"></a>Áttekintés
Az [Intune App SDK Xamarin Bindings](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) lehetővé teszi az [Intune alkalmazásvédelmi szabályzatok](app-protection-policy.md) használatát a Xamarinnal készített iOS- és Android-alkalmazásokban. A kötések lehetővé teszik a fejlesztők számára, hogy Intune alkalmazásvédelmi funkciókat építsenek be a Xamarin-alapú alkalmazásaikba.

A Microsoft Intune App SDK Xamarin Bindings lehetővé teszi, hogy Intune alkalmazásvédelmi szabályzatokat (vagy más néven alkalmazás- vagy MAM-szabályzatokat) építsen be a Xamarinnal fejlesztett alkalmazásokba. A MAM-kompatibilis alkalmazás az, amelyik integrálva van az Intune App SDK-val. Mindez lehetővé teszi a rendszergazdáknak, hogy alkalmazásvédelmi szabályzatokat telepítsenek a mobilalkalmazásra vonatkozóan, ha az Intune aktívan felügyeli az alkalmazást.

## <a name="whats-supported"></a>Támogatott források és műveletek

### <a name="developer-machines"></a>Fejlesztői gépek
* Windows (Visual Studio version 15.7+)
* macOS

### <a name="mobile-app-platforms"></a>Mobilalkalmazás-platformok
* Android
* iOS

### <a name="intune-mobile-application-management-scenarios"></a>Intune mobilalkalmazás-kezelési helyzetek

* Intune APP-WE (eszközregisztráció nélkül)
* Intune MDM által regisztrált eszközök
* Külső EMM által regisztrált eszközök

Az Intune App SDK Xamarin Bindingsszal létrehozott Xamarin-alkalmazásokra mostantól alkalmazhatók az Intune alkalmazásvédelmi szabályzatai az Intune mobileszköz-felügyeletében (MDM) regisztrált eszközökön és a nem regisztrált eszközökön is.

## <a name="prerequisites"></a>Előfeltételek

A [licencfeltételek](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf) áttekintése. Nyomtassa ki és őrizze meg a licencfeltételeket. Az Intune App SDK Xamarin Bindings letöltésével és használatával elfogadja licencfeltételeket. Amennyiben a feltételeket nem fogadja el, ne használja a szoftvert.

Az SDK támaszkodik [Active Directory Authentication Library (ADAL)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) számára annak [hitelesítési](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) és feltételes indítási forgatókönyvek, melyek konfigurálhatók, az alkalmazásokat szükség [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/). 

Ha az alkalmazás már adal-t vagy az MSAL használatára van konfigurálva, és rendelkezik a saját egyéni ügyfél-azonosító az Azure Active Directory-hitelesítésre használható, győződjön meg arról, a lépések a Xamarin-alkalmazás engedélyt az Intune Mobile Application Management (MAM) szolgáltatáshoz a alkalmazni. Található utasítások a "[az alkalmazás-hozzáférést biztosít az Intune app protection szolgáltatás](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional)" szakaszában a [első lépések az Intune SDK útmutatóját](app-sdk-get-started.md).

## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Az Intune alkalmazásvédelmi szabályzatainak engedélyezése az iOS-mobilalkalmazásban
1. Adja hozzá Xamarin.iOS-projektjéhez a [Microsoft.Intune.MAM.Xamarin.iOS NuGet-csomagot](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS).
2. Kövesse az Intune App SDK iOS-mobilalkalmazásokba való integrálásához szükséges általános lépéseket. Kezdhet az [iOS-hez készült Intune App SDK – fejlesztői útmutató](app-sdk-ios.md#build-the-sdk-into-your-mobile-app) című témakör integrálási útmutatásának 3. lépésével. Az IntuneMAMConfigurator futtatásáról szóló szakasz utolsó lépését átugorhatja, mivel az eszköz része a Microsoft.Intune.MAM.Xamarin.iOS csomagnak, és a build időpontjában automatikusan futtatva lesz.
    **Fontos**: Az alkalmazás a kulcsláncmegosztás módja kissé eltér a Visual Studióban xcode-ban. Nyissa meg az alkalmazás jogosultságokat tartalmazó plist-fájlját, és győződjön meg arról, hogy az „Enable Keychain” („Kulcslánc engedélyezése”) lehetőség engedélyezve van, és hogy ebben a szakaszban a megfelelő kulcslánc-megosztási csoportok szerepelnek. Ezután győződjön meg arról, hogy a projekt „iOS Bundle Signing” („iOS-kötegaláírási”) beállításai között a konfigurációk és platformok összes megfelelő kombinációjához meg van adva a jogosultságokat tartalmazó plist-fájl a „Custom Entitlements” („Egyéni jogosultságok”) mezőben.
3. Miután hozzáadta a kötéseket, és megfelelően konfigurálta az alkalmazást, az alkalmazás megkezdheti az Intune SDK API-jának használatát. Ehhez a következő névteret kell hozzáadnia:

      ```csharp
      using Microsoft.Intune.MAM;
      ```
4. Az alkalmazásvédelmi szabályzatok fogadásának megkezdéséhez az alkalmazást regisztrálni kell az Intune MAM szolgáltatásban. Ha az alkalmazás nem az [Azure Active Directory Authentication Library](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) (ADAL) vagy a [Microsoft Authentication Library](https://www.nuget.org/packages/Microsoft.Identity.Client) (MSAL) tárral hitelesíti a felhasználókat, Ön pedig ezt az Intune SDK-val szeretné kezelni, az alkalmazásnak át kell adnia a felhasználó egyszerű felhasználónevét az IntuneMAMEnrollmentManager LoginAndEnrollAccount metódusának:
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```
      Az alkalmazások üres értékűek is lehetnek, ha a felhasználó egyszerű felhasználóneve ismeretlen a hívás idején. Ebben az esetben a rendszer az e-mail-címet és a jelszót kéri a felhasználóktól.
      
      Ha az alkalmazás már az ADA vagy az MSAL segítségével hitelesíti a felhasználókat, egyszeri bejelentkezést (SSO) konfigurálhat az alkalmazás és az Intune SDK között. Elsőként konfigurálnia kell az ADAL/MSAL szolgáltatást a tokenek az iOS-es Intune Xamarin-kötések által is használt ugyanazon kulcslánc-hozzáférési csoport használatára (com.microsoft.adalcache). Az adal-t, akkor ehhez [AuthenticationContext iOSKeychainSecurityGroup tulajdonságának beállítása](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/wiki/iOS-Keychain-Access). Az MSAL, a következőket kell tennie [PublicClientApplication iOSKeychainSecurityGroup tulajdonságát állítsa](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki/Xamarin-iOS-specifics#enable-keychain-access). Ezután felül kell bírálnia az Intune SDK alapértelmezett AAD-beállításait az alkalmazáséival. Ezt az alkalmazás Info.plist fájljában található IntuneMAMSettings szótárban teheti meg az [iOS-hez készült Intune App SDK – fejlesztői útmutató](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk) című témakörben leírtaknak megfelelően, vagy használhatja az IntuneMAMPolicyManager-példány AAD-felülbírálási tulajdonságait. Az Info.plist fájlt alkalmazó módszer használata ajánlott az olyan alkalmazások esetében, melyek ADAL-beállításai statikusak, míg a felülbírálási tulajdonságok használata ajánlott olyan alkalmazások esetében, melyek futásidőben határozzák meg ezeket az értékeket. Az SSO-beállítások konfigurálása után az alkalmazásnak a sikeresen hitelesítést követően át kell adnia a felhasználó egyszerű felhasználónevét az IntuneMAMEnrollmentManager RegisterAndEnrollAccount metódusának:
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      Az alkalmazások meghatározhatják a regisztrációs kísérleteke eredményeit az EnrollmentRequestWithStatus metódus az IntuneMAMEnrollmentDelegate egyik alosztályában való alkalmazásával, valamint az IntuneMAMEnrollmentManager Delegate tulajdonságának az osztály egyik példányához való beállításával. Erről példát a [Xamarin.iOS-mintaalkalmazásban](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) találhat.

      Sikeres regisztráció esetén az alkalmazások meghatározhatják a regisztrált fiók egyszerű felhasználónevét a következő tulajdonság lekérdezésével (amennyiben azt addig nem ismerték): 
      ```csharp
       string enrolledAccount = IntuneMAMEnrollmentManager.Instance.EnrolledAccount;
      ```      
> [!NOTE] 
> iOS rendszerre nincs remapper. A Xamarin.Forms-alkalmazásokba való integrálásnak ugyanúgy kell történnie, mint általában a Xamarin.iOS-projektek esetén. 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Az Intune alkalmazásvédelmi szabályzatainak engedélyezése Androidos mobilalkalmazásban
1. Adja hozzá Xamarin.Android-projektjéhez a [Microsoft.Intune.MAM.Xamarin.Android NuGet-csomagot](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android).
    1. Xamarin.Forms-alkalmazás hozzáadása a [Microsoft.Intune.MAM.Remapper.Tasks NuGet-csomag](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) a Xamarin.Android projekthez is. 
2. Hajtsa végre a szükséges általános lépéseket [integrálása az Intune App SDK](app-sdk-android.md) az Android rendszerhez készült mobilalkalmazás további részleteket a jelen dokumentum hivatkozó közben.

### <a name="xamarinandroid-integration"></a>Xamarin.Android-integráció

Az Intune App SDK integrálásához teljes áttekintése található a [Microsoft Intune App SDK Androidon – útmutató fejlesztőknek](app-sdk-android.md). Olvassa végig az útmutató és a Xamarin-alkalmazás az Intune App SDK integrálása a következő szakaszok célja egy natív Android-alkalmazást Java nyelven fejlesztett, és a egy Xamarin-alkalmazás fejlesztett, jelölje ki a megvalósítás közötti különbségek C#. Ezekben a szakaszokban a kiegészítő kell kezelni, és nem jár el ebben az esetben a következő témakör elolvasásával helyett.

#### <a name="remapper"></a>Remapper
Verziótól kezdve a 1.4428.1 kiadásban a `Microsoft.Intune.MAM.Remapper` csomag adhatók hozzá Xamarin.Android-alkalmazásba, [hozhat létre azokat az eszközöket](app-sdk-android.md#build-tooling) a MAM osztály metódus és rendszerek szolgáltatások cseréjére végrehajtásához. Ha a Remapper részét képezi, az átnevezett metódusok és a MAM-alkalmazás szakaszok MAM egyenértékű helyettesítő részeit automatikusan történik, ha az alkalmazást a létrehozása.

Egy osztály kizárása a MAM-besorolása alapján a következő tulajdonság lehet hozzáadni a projektek a Remapper `.csproj` fájlt.
```xml
  <PropertyGroup>
    <ExcludeClasses>Semicolon separated list of relative class paths to exclude from MAM-ification</ExcludeClasses>
  </PropertyGroup>
```

#### <a name="renamed-methodsapp-sdk-androidmdrenamed-methods"></a>[Átnevezett metódusok](app-sdk-android.md#renamed-methods)
Sok esetben az androidos osztályban rendelkezésre álló metódus végsőként van megjelölve a helyettesítő MAM-osztályban. Ebben az esetben a helyettesítő MAM-osztály egy hasonlóan elnevezett metódust biztosít (a `MAM` utótaggal), amelyet felül kell írni. Így például a `MAMActivity` származtatásakor az `OnCreate()` felülírása, illetve a `base.OnCreate()` metódus hívása helyett az `Activity` tevékenységnek felül kell írnia az `OnMAMCreate()` metódust, és meg kell hívnia a `base.OnMAMCreate()` metódust.

#### <a name="mam-applicationapp-sdk-androidmdmamapplication"></a>[MAM-alkalmazás](app-sdk-android.md#mamapplication)
Az alkalmazás meg kell határoznia egy `Android.App.Application` osztály. Ha manuálisan integrálása MAM, kell örökölnie `MAMApplication`. Ügyeljen rá, hogy az alosztály megfelelően jelölve legyen a `[Application]` attribútummal, és felülbírálja a `(IntPtr, JniHandleOwnership)` konstruktort.
```csharp
    [Application]
    class TaskrApp : MAMApplication
    {
    public TaskrApp(IntPtr handle, JniHandleOwnership transfer)
        : base(handle, transfer) { }
```
> [!NOTE]
> A MAM Xamarin-kötések hibát okozhat az alkalmazás, amikor a hibakeresési módban rendszerbe állított. Áthidaló megoldásként a `Debuggable=false` attribútumot hozzá kell adni a `Application` osztály és a `android:debuggable="true"` jelzője el kell távolítani a jegyzékfájl manuálisan adta meg.

#### <a name="enable-features-that-require-app-participationapp-sdk-androidmdenable-features-that-require-app-participation"></a>[Alkalmazás részvételét igénylő szolgáltatások engedélyezése](app-sdk-android.md#enable-features-that-require-app-participation)
Példa: PIN-kód az alkalmazáshoz szükséges, hogy
```csharp
MAMPolicyManager.GetPolicy(currentActivity).IsPinRequired;
```
Példa: Az elsődleges Intune-felhasználó meghatározása
```csharp
IMAMUserInfo info = MAMComponents.Get<IMAMUserInfo>();
return info?.PrimaryUser;
```
Példa: Határozza meg, ha az eszközre való mentése vagy engedélyezve van a felhőalapú tárolás
```csharp
MAMPolicyManager.GetPolicy(currentActivity).GetIsSaveToLocationAllowed(SaveLocation service, String username);
```

#### <a name="register-for-notifications-from-the-sdkapp-sdk-androidmdregister-for-notifications-from-the-sdk"></a>[Az SDK értesítéseire regisztrálás](app-sdk-android.md#register-for-notifications-from-the-sdk)
Az alkalmazásnak regisztrálnia kell az SDK értesítéseire hozzon létre egy `MAMNotificationReceiver` és annak regisztrálásával a következővel `MAMNotificationReceiverRegistry`. Ez a fogadó és a kívánt értesítés típusának megadásával történik `App.OnMAMCreate`, ahogy az alábbi példában látható:
```csharp
public override void OnMAMCreate()
{
    // Register the notification receivers
    IMAMNotificationReceiverRegistry registry = MAMComponents.Get<IMAMNotificationReceiverRegistry>();
    foreach (MAMNotificationType notification in MAMNotificationType.Values())
    {
        registry.RegisterReceiver(new ToastNotificationReceiver(this), notification);
    }
    ...
```

#### <a name="mam-enrollment-managerapp-sdk-androidmdmamenrollmentmanager"></a>[MAM Eszközregisztráció-kezelővel](app-sdk-android.md#mamenrollmentmanager)
```csharp
IMAMEnrollmentManager mgr = MAMComponents.Get<IMAMEnrollmentManager>();
```

### <a name="xamarinforms-integration"></a>Xamarin.Forms-integráció

A `Xamarin.Forms` alkalmazások a `Microsoft.Intune.MAM.Remapper` csomag végez MAM osztály lecserélését automatikusan úgy, hogy `MAM` osztályok az osztály hierarchiává, gyakran használt `Xamarin.Forms` osztályokat. 

> [!NOTE]
> A Xamarin.Forms-integráció, hogy a Xamarin.Android-integrációval lásd fent emellett elvégezni.

Miután hozzáadta a projekthez a Remapper szüksége lesz az egyenértékű MAM-cserékhez végrehajtásához. Például `FormsAppCompatActivity` és `FormsApplicationActivity` továbbra is használható az alkalmazás megadott felülbírálások `OnCreate` és `OnResume` a MAM-megfelelője cserélése `OnMAMCreate` és `OnMAMResume` jelölik.

```csharp
    public class MainActivity : global::Xamarin.Forms.Platform.Android.FormsAppCompatActivity
    {
        protected override void OnMAMCreate(Bundle savedInstanceState)
        {
            base.OnMAMCreate(savedInstanceState);
            global::Xamarin.Forms.Forms.Init(this, savedInstanceState);
            LoadApplication(new App());
        }
```
Ha a cserét nem történik majd felmerülhet a következő fordítási hibákat a lecserélendő létrehozásáig:
* [Fordítási hiba CS0239](https://docs.microsoft.com/dotnet/csharp/misc/cs0239). Ez a hiba fordul elő, az űrlap ``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``.
Ez elvárható, hiszen a Remapper Xamarin osztályok az öröklési módosítja, amikor bizonyos funkciókat tesznek `sealed` és egy új MAM-változatot hozzáadásával felülírása helyett.
* [Fordítási hiba CS0507](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0507): Ez a hiba fordul elő, az űrlap ``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``. A Remapper néhány, a Xamarin-osztályok az öröklési megváltozik, amikor bizonyos tag funkciók változnak a `public`. Ha az felülírja ezeket a funkciókat, szüksége lesz módosítani azokat a hozzáférési módosítók azok számára, felülbírálások használatával lehet `public` is.

> [!NOTE]
> A Remapper újra ír egy függőség használ a Visual Studio IntelliSense automatikus kiegészítését. Ezért szükségessé töltse be újra, és a projekt újraépítéséhez, az IntelliSense helyesen ismeri fel a módosítások a Remapper hozzáadásakor.

### <a name="company-portal-app"></a>Vállalati portál alkalmazás
Az Intune SDK Xamarin Bindings használják jelenléte a [céges portál](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) Android-alkalmazás az alkalmazásvédelmi szabályzatok engedélyezése az eszközön. A Céges portál az Intune szolgáltatástól kéri le az alkalmazásvédelmi szabályzatokat. Az alkalmazás az inicializáláskor betölti a Céges portálról a szabályzatot és a betartatásához szükséges kódot. A felhasználónak nem kell jelentkeznie.

> [!NOTE]
> Amikor a vállalati portál alkalmazás-e kapcsolva a **Android** eszköz, az Intune által felügyelt alkalmazások ugyanúgy működik, mint a szokásos alkalmazások Intune alkalmazásvédelmi szabályzatait nem támogató.

Az eszközregisztráció nélküli alkalmazásvédelem esetében a felhasználónak _**nem**_ kell regisztrálnia az eszközt a Céges portál alkalmazással.

### <a name="sample-applications"></a>Mintaalkalmazások
Mintaalkalmazások, valamint az áttelepítésre alkalmatlan a Xamarin.Android- és Xamarin Forms-alkalmazások mobilalkalmazás-felügyeleti funkciók érhetők el a [GitHub](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps).

## <a name="support"></a>Támogatás
Ha vállalata már Intune-ügyfél, együttműködve nyisson egy támogatási jegyet, és probléma létrehozása a Microsoft támogató szolgálat képviselőjével [a GitHub hibabejelentő oldalán](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues) , mi pedig segítünk, amint tudunk. 

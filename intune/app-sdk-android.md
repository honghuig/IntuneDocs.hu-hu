---
title: A Microsoft Intune App SDK Androidon – útmutató fejlesztőknek
description: Az Androidhoz készült Microsoft Intune App SDK lehetővé teszi, hogy az Intune mobilalkalmazás-felügyeleti (MAM) funkcióját beépítse Android-alkalmazásaiba.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/26/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4530c1ec573560924b54aa8fd21d39a86cefe97e
ms.sourcegitcommit: cb4e71cd48311ea693001979ee59f621237a6e6f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/03/2019
ms.locfileid: "67558428"
---
# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>A Microsoft Intune App SDK Androidon – útmutató fejlesztőknek

> [!NOTE]
> Kezdésként érdemes lehet elolvasni [Az Intune APP SDK áttekintése](app-sdk.md) című cikket, amely ismerteti az SDK aktuálisan elérhető funkcióit, valamint az integrációval kapcsolatos előkészületeket a támogatott platformokon.

Az Androidhoz készült Microsoft Intune App SDK révén Intune-os alkalmazásvédelmi szabályzatokat (más néven **APP**- vagy MAM-szabályzatokat) építhet be natív Android-alkalmazásába. Intune által kezeltnek az Intune App SDK-val integrált alkalmazásokat nevezzük. A rendszergazdák egyszerűen telepíthetnek alkalmazásvédelmi szabályzatokat az Intune által kezelt alkalmazáshoz, ha az Intune aktívan felügyeli az alkalmazást.


## <a name="whats-in-the-sdk"></a>Az SDK tartalma

Az Intune App SDK-ban a következő fájlok találhatók:

* **Microsoft.Intune.MAM.SDK.aar**: Az SDK-összetevők a támogatási kódtár JAR-fájlok kivételével.
* **Microsoft.Intune.MAM.SDK.Supp, vagy egyt.v4.jar**: A támogatási könyvtárat az osztályokat, amelyek az Android v4-alkalmazásokban a MAM engedélyezéséhez szükségesek.
* **Microsoft.Intune.MAM.SDK.Supp, vagy egyt.v7.jar**: Az Android 7-es verzióját használó alkalmazásokban a MAM engedélyezéséhez szükségesek osztályok támogatási könyvtárat.
* **Microsoft.Intune.MAM.SDK.Support.v17.jar**: A támogatási könyvtárat az osztályok az Androidos v17 használó alkalmazásokban a MAM engedélyezéséhez szükségesek. 
* **Microsoft.Intune.MAM.SDK.Support.Text.jar**: Az osztályokat, amelyek az Android-alkalmazásokban a MAM engedélyezéséhez szükségesek támogatja az erőforrástár-osztályok a `android.support.text` csomagot.
* **Microsoft.Intune.MDM.SDK.DownlevelStubs.jar**: A JAR-fájl tartalmazza a fájl az Android rendszer osztályokat, amelyek csak újabb eszközökön található, de a MAMActivity módszerek hivatkozik. Az újabb eszközök figyelmen kívül hagyják ezeket az osztálycsonkokat. Erre a Jar-fájlra csak akkor van szükség, ha az alkalmazása a MAMActivity osztályból származtatott osztályokon reflexiót végez, és így a legtöbb alkalmazásba nem szükséges belefoglalni. A Jar-fájl használata esetén ügyeljen rá, hogy a fájlban található összes osztályt ki kell zárnia a ProGuard hatóköréből. Mindegyik az „android” gyökércsomag alatt lesz megtalálható
* **com.microsoft.intune.mam.build.jar**: A Gradle-beépülő modul amely [az SDK integrálásával segédeszközök](#build-tooling).
* **CHANGELOG.txt**: Minden SDK-verzióban végzett módosítások szolgáltat információt.
* **THIRDPARTYNOTICES.TXT**:  Attribútumértesítés, amely a külső és/vagy OSS kódnak az alkalmazásba fordítására.

## <a name="requirements"></a>Követelmények

### <a name="android-versions"></a>Android-verzió
Az SDK az Android API 19 (Android 4.4 +) Android API 28 (Android 9.0) keresztül támogatja.

### <a name="company-portal-app"></a>Vállalati portál alkalmazás
Az androidos Intune App SDK a [Céges portál](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) alkalmazással teszi lehetővé az alkalmazásvédelmi szabályzatok működését. A Céges portál az Intune szolgáltatástól kéri le az alkalmazásvédelmi szabályzatokat. Az alkalmazás az inicializáláskor betölti a Céges portálról a szabályzatot és a betartatásához szükséges kódot.

> [!NOTE]
> Ha a Céges portál alkalmazás nincs telepítve az eszközre, akkor az Intune által kezelt alkalmazás ugyanúgy működik, mint az általános, az Intune alkalmazásvédelmi szabályzatait nem támogató alkalmazások.

Az eszközregisztráció nélküli alkalmazásvédelem esetében a felhasználónak _**nem**_ kell regisztrálnia az eszközt a Céges portál alkalmazással.

## <a name="sdk-integration"></a>SDK-integráció

### <a name="sample-app"></a>Mintaalkalmazás
Példa bemutatja, hogyan integrálható az Intune App SDK-val megfelelően érhető el a [GitHub](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App). Ez a példa a [gradle-t hozhat létre a beépülő modul](#gradle-build-plugin).

### <a name="referencing-intune-app-libraries"></a>Hivatkozás Intune App-kódtárakra

Az Intune App SDK for Android egy szabványos, külső függőségek nélküli androidos függvénytár. A **Microsoft.Intune.MAM.SDK.aar**-ban megvannak mind az alkalmazásvédelmi szabályzatok használatát lehetővé tevő interfészek, mind pedig a Microsoft Intune Céges portál alkalmazással való együttműködéshez szükséges kód.

A **Microsoft.Intune.MAM.SDK.aar**-t androidos függvénytár-hivatkozásként kell megadni. Ehhez nyissa meg az alkalmazásprojektet az Android Studióban, válassza a **File > New > New module** (Fájl > Új > Új modul), majd az **Import .JAR/.AAR Package** (.JAR-/.AAR-csomag importálása) elemet. Ezután jelölje ki a Microsoft.Intune.MAM.SDK.aar nevű androidos archívumcsomagot az .AAR-modul létrehozásához. Kattintson a jobb gombbal az alkalmazáskódot tartalmazó modulra vagy modulokra, válassza a **Module Settings (Modul beállításai)**  > **Dependencies (Függőségek)**  >  **+ ikon** > **Module dependency (Modulfüggőség)** lehetőséget, adja meg a most létrehozott MAM SDK AAR-modult, és végül kattintson az **OK** gombra. Ezzel biztosíthatja, hogy a modul a MAM SDK-val forduljon le a projekt buildelésekor.

Ezenkívül a **Microsoft.Intune.MAM.SDK.Support.XXX.jar** kódtárak tartalmazzák a megfelelő `android.support.XXX` kódtárak Intune-változatait. Ezek nem kerültek bele a Microsoft.Intune.MAM.SDK.aar-ba, arra az esetre, ha egy alkalmazásnak nem kell függenie a támogatási kódtáraktól.

#### <a name="proguard"></a>ProGuard

Ha fordítási lépésként a [ProGuard](http://proguard.sourceforge.net/) (vagy bármely más zsugorítási/rejtjelezési mechanizmus) használt, az SDK olyan további konfigurációs szabályokkal rendelkezik, amelyeket fordításkor bele kell foglalni. Ha például a. A buildek AAR, a szabályok automatikus integrálva vannak a proguard lépés és őrzi meg a szükséges osztály-fájlokat.

Az Azure Active Directory Authentication Libraries (ADAL) szolgáltatásnak saját ProGuard-korlátozásai lehetnek. Ha az Ön alkalmazása az ADAL-lal van integrálva, ezen korlátozások tekintetében az ADAL dokumentációja a mérvadó.

### <a name="build-tooling"></a>Build-eszközök
Az Intune App SDK egy androidos függvénytár, amely lehetővé teszi, hogy az alkalmazás támogassa az Intune-szabályzatokat, és részt vegyen azok kikényszerítésében. Néhány szabályzat [kényszerítéséhez az alkalmazásnak ebben kifejezetten részt kell vennie](#enable-features-that-require-app-participation), azonban a legtöbbnek a kényszerítése félig automatikus. Ez az automatikus kényszerítés megköveteli, hogy az alkalmazások lecseréljenek néhány Android-alaposztálytól származó öröklést a MAM-megfelelőktől származóakkal, és ugyanígy lecseréljék néhány Android rendszerbeli szolgáltatásosztály hívását azok MAM-megfelelőinek küldött hívásokkal. A szükséges meghatározott helyettesítések részletei az [alábbiakban](#class-and-method-replacements) olvashatók.

Ezeknek a cseréknek a manuális végrehajtása fárasztó folyamat lehet. Ehelyett az SDK olyan fordítási eszközöket (a Gradle-buildekhez egy beépülő modult a nem Gradle-buildekhez pedig egy parancssori eszközt) biztosít, amelyek automatikus végrehajtják a cseréket. Ezek az eszközök átalakítják a Java-fordítással létrehozott osztályfájlokat, és nem módosítják az eredeti forráskódot.

Az eszközök végre [cseréjére közvetlen](#class-and-method-replacements) csak. Bonyolultabb SDK-integrációkat, például [Mentés másként szabályzatot](#enable-features-that-require-app-participation), [Többszörös identitást](#multi-identity-optional), [App-WE-regisztrációt](#app-protection-policy-without-device-enrollment), [AndroidManifest-módosításokat](#manifest-replacements) vagy [ADAL-konfigurációt](#configure-azure-active-directory-authentication-library-adal) nem hajtanak végre, ezért ezeket még azelőtt kell elvégezni, mielőtt az alkalmazás teljesen engedélyezve lenne az Intune-ban. Olvassa el figyelmesen a dokumentáció többi részét az alkalmazás szempontjából releváns integrációs pontok megtalálásához.

> [!NOTE]
> Az eszközöket lehet olyan projekten is futtatni, amelyen manuális cserékkel már végrehajtották a MAM SDK részleges vagy teljes forrásintegrációját. A projektnek továbbra is függőségként kell listáznia a MAM SDK-t.

### <a name="gradle-build-plugin"></a>Gradle-build beépülő modul
Ha az alkalmazás nem jön létre a Gradle-lel, ugorjon az [Integrálása a parancssori eszközzel](#command-line-build-tool) szakaszra. 

Az App SDK beépülő modul terjesztése az SDK részeként történik a **GradlePlugin/com.microsoft.intune.mam.build.jar** fájlban. A Gradle csak akkor tudja megtalálni a beépülő modult, ha az hozzá van adva a buildscript classpath sorhoz. A beépülő modul a [Javassist](https://jboss-javassist.github.io/javassist/) eszközkészlettől függ, amelyet szintén fel kell venni. Ezeknek a classpath sorhoz adásához, adja hozzá a következőt a gyökérhez: `build.gradle`

```groovy
buildscript {
    repositories {
        jcenter()
    }
    dependencies {
        classpath "org.javassist:javassist:3.22.0-GA"
        classpath files("$PATH_TO_MAM_SDK/GradlePlugin/com.microsoft.intune.mam.build.jar")
    }
}
```

Ezt követően az APK-projekt `build.gradle` fájljában egyszerűen alkalmazza a beépülő modult az alább módon:
```groovy
apply plugin: 'com.microsoft.intune.mam'
```

Alapértelmezés szerint a beépülő modul **csak** a `project` függőségein fog működni.
A tesztfordítást nem érinti. Megadhat konfigurációt az alábbiak listázásához:
* Kizárandó projektek
* [Kizárandó külső függőségek](#usage-of-includeexternallibraries) 
* Meghatározott osztályok a feldolgozásból való kizáráshoz
* Változók a feldolgozásból való kizáráshoz. Ezek vonatkozhatnak a teljes változónévre vagy egyetlen ízre. Példa:
     * Ha az alkalmazás rendelkezik `debug` és `release` buildtípussal {`savory`, `sweet`} és {`vanilla` ízekkel, `chocolate`} akkor megadhatja, hogy
     * `savory` az összes sós ízű változó kizárásához, vagy megadhatja a `savoryVanillaRelease` értéket pontosan ennek az változónak a kizárásához.

#### <a name="example-partial-buildgradle"></a>Részleges példa: build.gradle

```groovy

apply plugin: 'com.microsoft.intune.mam'

dependencies {
    implementation project(':product:FooLib')
    implementation project(':product:foo-project')
    implementation fileTree(dir: "libs", include: ["bar.jar"])
    implementation fileTree(dir: "libs", include: ["zap.jar"])
    implementation "com.contoso.foo:zap-artifact:1.0.0"
    implementation "com.microsoft.bar:baz:1.0.0"

    // Include the MAM SDK
    implementation files("$PATH_TO_MAM_SDK/Microsoft.Intune.MAM.SDK.aar")
}
intunemam {
    excludeProjects = [':product:FooLib']
    includeExternalLibraries = ['bar.jar', "com.contoso.foo:zap-artifact", "com.microsoft.*", "!com.microsoft.qux*"]
    excludeClasses = ['com.contoso.SplashActivity']
    excludeVariants=['savory']
}

```
Ennek a hatása a következő lesz:
* A `:product:FooLib` nincs újraírva, mert azt az `excludeProjects` tartalmazza.
* A `:product:foo-project` újra van írva, kivéve a `com.contoso.SplashActivity` osztályt, ami ki van hagyva, mert azt az `excludeClasses` tartalmazza.
* A `bar.jar` újra van írva, mert azt az `includeExternalLibraries` tartalmazza.
* A `zap.jar`**nics** újraírva, mert az nem projekt, és azt az `includeExternalLibraries` nem tartalmazza.
* A `com.contoso.foo:zap-artifact:1.0.0` újra van írva, mert azt az `includeExternalLibraries` tartalmazza.
* A `com.microsoft.bar:baz:1.0.0` újra van írva, mert azt az `includeExternalLibraries` tartalmazza egy helyettesítő karakteren keresztül (`com.microsoft.*`).
* `com.microsoft.qux:foo:2.0` nem áll feladatátvitelt annak ellenére, hogy a kulcs megegyezik-e az előző elemmel azonos helyettesítő karaktert, mert ez explicit módon ki van zárva, egy negálás minta használatával.

#### <a name="usage-of-includeexternallibraries"></a>Az IncludeExternalLibraries használata

Mivel a beépülő modul csak projektfüggőségeken működik (amit általában a `project()` függvény biztosít) alapértelmezés szerint a `fileTree(...)` által megadott vagy a maven vagy egyéb csomagforrásból (például „`com.contoso.bar:baz:1.2.0`”) származó minden függőséget meg kell adni az `includeExternalLibraries` tulajdonság számára, ha ezeknek a MAM általi feldolgozása az alábbiakban leírt feltételek alapján szükséges. Helyettesítő karakterek (*) használhatók. Egy elem kiadásától kezdve `!` egy negálás, és használható helyettesítő karakter ellenkező esetben tenné szereplő könyvtárak kizárása.

Ha külső függőségeket ad meg munkadarab-jelöléssel, akkor javasolt kihagyni a verzió-összetevőt az `includeExternalLibraries` értékéből. Ha belefoglalja a verziót, akkor annak pontos verziónak kell lennie. A dinamikus verziómegadások (pl. `1.+`) nem megengedettek.

Azt, hogy bele kell-e foglalnia a függvénytárakat az `includeExternalLibraries` sorba, általános szabályként két kérdés alapján döntheti el:
1. Tartalmaz a függvénytár olyan osztályokat, amelyhez rendelkezésre állnak MAM-megfelelők? Példák: `Activity`, `Fragment`, `ContentProvider`, `Service` stb.
2. Ha igen, használja az alkalmazás ezeket az osztályokat?

Ha mindkét kérdésre „igen” a válasz, akkor azt a függvénytárat bele kell foglalnia az `includeExternalLibraries` sorba. 

| Forgatókönyv | Tartalmaznia kell? |
|--|--|
| Belefoglal egy PDF-megtekintő függvénytárat az alkalmazásába, és a megtekintő `Activity` tevékenységét használja az alkalmazásban, amikor a felhasználók PDF-eket próbálnak megtekinteni | Igen |
| A továbbfejlesztett webes teljesítmény érdekében belefoglal egy HTTP-függvénytárat az alkalmazásába | Nem |
| Belefoglal egy olyan függvénytárat, mint a React Native, amely az `Activity`, az `Application` és a `Fragment` elemekből származtatott osztályokat tartalmaz, és felhasználja ezeket az osztályokat, vagy további származtatást végez belőlük az alkalmazásában | Igen |
| Belefoglal egy olyan függvénytárat, mint a React Native, amely az `Activity`, az `Application` és a `Fragment` elemekből származtatott osztályokat tartalmaz, de csak statikus segédeket vagy segédprogramosztályokat használ | Nem |
| Belefoglal egy olyan függvénytárat, amely a `TextView` osztályból származtatott megtekintési osztályokat tartalmaz, és felhasználja ezeket az osztályokat, vagy további származtatást végez belőlük az alkalmazásában | Igen |

#### <a name="reporting"></a>Jelentéskészítés
A build beépülő modul végrehajtott változtatások HTML formátumú jelentést hozhat létre. Ez a jelentés generációja kérni, adja meg a `report = true` a a `intunemam` konfigurációs letiltása. Ha jönnek létre, a jelentés lesz írva `outputs/logs` hozhat létre a címtárban.

```groovy
intunemam {
    report = true
}
```

#### <a name="dependencies"></a>Függőségek

A Gradle beépülő modul függőségben van a [Javassist](https://jboss-javassist.github.io/javassist/) eszközkészlettől, amelynek elérhetőnek kell lennie a Gradle számára a függőségfeloldáshoz (a fent leírtaknak megfelelően). A Javassist használata kizárólag a fordítás idején történik a beépülő modul futtatásakor. Az alkalmazáshoz nem lesz hozzáadva Javassist-kód.

> [!NOTE] 
> Az Android Gradle beépülő modul 3.0-s vagy újabb verzióját és a Gradle 4.1-es vagy újabb verzióját kell használnia.

### <a name="command-line-build-tool"></a>Parancssori fordítóeszköz
Ha a build a Gradle-t használja, ugorjon a [következő szakaszra](#class-and-method-replacements).

A parancssori fordítóeszköz az SDK-letöltés `BuildTool` mappájában található. Ugyanazt a feladatot látja el, mint a fent részletezett Gradle beépülő modul, de integrálható egyéni vagy nem Gradle build-rendszerekbe. Mivel ez generikusabb, nehezebb meghívni, ezért, ha lehetséges a Gradle beépülő modul használata javasolt.

#### <a name="using-the-command-line-tool"></a>A parancssori eszköz használata

A parancssori eszközt a megadott segítő parancsfájlokkal lehet meghívni, amelyek a `BuildTool\bin` könyvtárban találhatók.

Az eszköz a következő paramétereket várja.

| Paraméter | Leírás |
| -- | -- |
| `--input` | A módosításra váró osztályfájlok jar-fájljainak és könyvtárainak pontosvesszővel tagolt listája. Ennek tartalmaznia kell minden olyan jar-fájlt és könyvtárat, amelyet felül szeretne írni. |
| `--output` | A módosított osztályok tárolására szolgáló jar-fájlok és könyvtárak pontosvesszővel tagolt listája. Bemeneti bejegyzésenként egy kimeneti bejegyzésnek kell lennie, és ezeket sorrendben kell listázni. |
| `--classpath` | A build osztályútvonala. Ez tartalmazhat jar-fájlokat és osztálykönyvtárakat is. |
| `--excludeClasses`| Egy pontosvesszővel tagolt lista, amely tartalmazza azoknak az osztályoknak a nevét, amelyeket ki kell zárni az újraírásból. |

Az összes paramétert meg kell adni, kivéve az `--excludeClasses` paramétert, amely nem kötelező.

> [!NOTE] 
> Az Unix-rendszerrel pontosvesszővel elválasztva, a parancs az elválasztó. A parancsok felosztása a rendszerhéj elkerülése érdekében ügyeljen arra, hogy az egyes pontosvessző escape "\' vagy a paraméter teljes zabalit do idézőjelek közé.

#### <a name="example-command-line-tool-invocation"></a>Példa a parancssori eszköz meghívására

``` batch
> BuildTool\bin\BuildTool.bat --input build\product-foo-project;libs\bar.jar --output mam-build\product-foo-project;mam-build\libs\bar.jar --classpath build\zap.jar;libs\Microsoft.Intune.MAM.SDK\classes.jar;%ANDROID_SDK_ROOT%\platforms\android-27\android.jar --excludeClasses com.contoso.SplashActivity
```

Ennek a hatása a következő lesz:

* A `product-foo-project` könyvtár át lesz írva erre: `mam-build\product-foo-project`
* A `bar.jar` át lesz írva erre: `mam-build\libs\bar.jar`
* A `zap.jar`**nincs** átírva, mert az csak a `--classpath` listában van felsorolva
* A `com.contoso.SplashActivity` osztály **nincs** átírva, még akkor sem, ha az `--input` paraméterben van

> [!NOTE] 
> A build-eszköz jelenleg nem támogatja az aar-fájlokat. Ha a build-rendszer nem bontja ki a `classes.jar` fájlt az aar-fájlok feldolgozásakor, akkor ezt Önnek kell megtennie a build-eszköz meghívása előtt.


## <a name="class-and-method-replacements"></a>Osztályok és metódusok lecserélése

Az Intune-felügyelet engedélyezéséhez az androidos alaposztályokat a MAM-megfelelőjükkel kell helyettesíteni. Az SDK-osztályok az androidos alaposztály és az alkalmazás saját származtatott verziója között helyezkednek el. Alkalmazástevékenységek esetében ez például egy, az alábbihoz hasonló öröklési hierarchiát eredményez: `Activity` > `MAMActivity` >
`AppSpecificActivity`. A MAM-réteg szűrői rendszerműveleteket hívnak, hogy zökkenőmentesen biztosíthassák az alkalmazása számára a felügyelt nézetet.

Az alaposztályokon kívül bizonyos osztályokat az alkalmazás származtatás nélkül használhat (pl. `MediaPlayer`), ezenkívül kötelező MAM-megfelelőkkel is rendelkezik, és [bizonyos metódushívásokat szintén le kell cserélni](#wrapped-system-services). A pontos részletek az alábbiak.

Az SDK [build-eszközei](#build-tooling) az ebben a szakaszban szereplő összes cserét automatikusan végre tudják hajtani. 



| Androidos alaposztály | Intune App SDK-beli helyettesítése |
|--|--|
| android.app.Activity | MAMActivity |
| android.app.ActivityGroup | MAMActivityGroup |
| android.app.AliasActivity | MAMAliasActivity |
| android.app.Application | MAMApplication |
| android.app.Dialog | MAMDialog |
| android.app.AlertDialog.Builder | MAMAlertDialogBuilder |
| android.app.DialogFragment | MAMDialogFragment |
| android.app.ExpandableListActivity | MAMExpandableListActivity |
| android.app.Fragment | MAMFragment |
| android.app.IntentService | MAMIntentService |
| android.app.LauncherActivity | MAMLauncherActivity |
| android.app.ListActivity | MAMListActivity |
| android.app.ListFragment | MAMListFragment |
| android.app.NativeActivity | MAMNativeActivity |
| android.app.PendingIntent | MAMPendingIntent (lásd: [PendingIntent](#pendingintent)) |
| android.app.Service | MAMService |
| android.app.TabActivity | MAMTabActivity |
| android.app.TaskStackBuilder | MAMTaskStackBuilder |
| android.app.backup.BackupAgent | MAMBackupAgent |
| android.app.backup.BackupAgentHelper | MAMBackupAgentHelper |
| android.app.backup.FileBackupHelper | MAMFileBackupHelper |
| android.app.backup.SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
| android.content.BroadcastReceiver | MAMBroadcastReceiver |
| android.content.ContentProvider | MAMContentProvider |
| android.os.Binder | MAMBinder (csak akkor szükséges, ha a Binder létrehozása nem androidos interfészdefiníciós nyelvű (AIDL-) interfészből történik) |
| android.media.MediaPlayer | MAMMediaPlayer |
| android.media.MediaMetadataRetriever | MAMMediaMetadataRetriever |
| android.provider.DocumentsProvider | MAMDocumentsProvider |
| android.preference.PreferenceActivity | MAMPreferenceActivity |
| android.support.multidex.MultiDexApplication | MAMMultiDexApplication |
| android.widget.TextView | MAMTextView |
| android.widget.AutoCompleteTextView | MAMAutoCompleteTextView |
| android.widget.AutoCompleteTextView | MAMCheckedTextView |
| android.widget.EditText | MAMEditText |
| android.inputmethodservice.ExtractEditText | MAMExtractEditText |
| android.widget.MultiAutoCompleteTextView | MAMMultiAutoCompleteTextView |

> [!NOTE]
> Még ha az alkalmazásának nincs is szüksége saját, származtatott `Application` osztályra, [lásd `MAMApplication` alább](#mamapplication)

### <a name="microsoftintunemamsdksupportv4jar"></a>Microsoft.Intune.MAM.SDK.Support.v4.jar:

| Androidos osztály | Intune App SDK-beli helyettesítése |
|--|--|
| Android.support.v4.App.DialogFragment | MAMDialogFragment
| android.support.v4.app.FragmentActivity | MAMFragmentActivity
| android.support.v4.app.Fragment | MAMFragment
| android.support.v4.app.JobIntentService | MAMJobIntentService
| Android.support.v4.App.TaskStackBuilder | MAMTaskStackBuilder
| Android.support.v4.Content.FileProvider | MAMFileProvider
| android.support.v4.content.WakefulBroadcastReceiver | MAMWakefulBroadcastReceiver

### <a name="microsoftintunemamsdksupportv7jar"></a>Microsoft.Intune.MAM.SDK.Support.v7.jar:

|Androidos osztály | Intune App SDK-beli helyettesítése |
|--|--|
| android.support.v7.app.AlertDialog.Builder | MAMAlertDialogBuilder |
| android.support.v7.app.AppCompatActivity | MAMAppCompatActivity |
| android.support.v7.widget.AppCompatAutoCompleteTextView | MAMAppCompatAutoCompleteTextView |
| android.support.v7.widget.AppCompatCheckedTextView | MAMAppCompatCheckedTextView |
| android.support.v7.widget.AppCompatEditText | MAMAppCompatEditText |
| android.support.v7.widget.AppCompatMultiAutoCompleteTextView | MAMAppCompatMultiAutoCompleteTextView |
| android.support.v7.widget.AppCompatTextView | MAMAppCompatTextView |

### <a name="microsoftintunemamsdksupportv17jar"></a>Microsoft.Intune.MAM.SDK.Support.v17.jar:
|Androidos osztály | Intune App SDK-beli helyettesítése |
|--|--|
| android.support.v17.leanback.widget.SearchEditText | MAMSearchEditText |

### <a name="microsoftintunemamsdksupporttextjar"></a>Microsoft.Intune.MAM.SDK.Support.Text.jar:
|Androidos osztály | Intune App SDK-beli helyettesítése |
|--|--|
| android.support.text.emoji.widget.EmojiAppCompatEditText | MAMEmojiAppCompatEditText |
| android.support.text.emoji.widget.EmojiAppCompatTextView | MAMEmojiAppCompatTextView |
| android.support.text.emoji.widget.EmojiEditText | MAMEmojiEditText |
| android.support.text.emoji.widget.EmojiTextView | MAMEmojiTextView |

### <a name="renamed-methods"></a>Átnevezett metódusok
Sok esetben az androidos osztályban rendelkezésre álló metódus végsőként van megjelölve a helyettesítő MAM-osztályban. Ebben az esetben a helyettesítő MAM-osztály egy hasonlóan elnevezett metódust biztosít (általában a `MAM` utótaggal), amelyet felül kell írni. Így például a `MAMActivity` származtatásakor az `onCreate()` felülírása, illetve a `super.onCreate()` metódus hívása helyett az `Activity` tevékenységnek felül kell írnia az `onMAMCreate()` metódust, és meg kell hívnia a `super.onMAMCreate()` metódust. A Java-fordítónak érvényesítenie kell a végső korlátozásokat az eredeti metódus véletlen felülbírálásának elkerülése érdekében az egyenértékű MAM-metódus helyett.

### <a name="mamapplication"></a>MAMApplication
Ha az alkalmazása létrehozza az `android.app.Application` osztály egy alosztályát, akkor ehelyett **mindenképp** a `com.microsoft.intune.mam.client.app.MAMApplication` osztályból kell alosztályt létrehoznia. Ha az alkalmazása nem hoz létre alosztályt az `android.app.Application` osztályból, akkor **mindenképp** be kell állítania a `"com.microsoft.intune.mam.client.app.MAMApplication"` osztályt az `"android:name"` attribútumként az AndroidManifest.xml fájl `<application>` címkéjénél.

### <a name="pendingintent"></a>PendingIntent
A `PendingIntent.get*` helyett például a `MAMPendingIntent.get*` metódust kell használni. Az így létrejövő `PendingIntent` már szintén a megszokott módon használható.

### <a name="wrapped-system-services"></a>Burkolt rendszerszolgáltatások
Néhány rendszerszolgáltatási osztály esetében statikus metódushívás szükséges a MAM-burkolóosztályon a kívánt metódusnak közvetlenül a szolgáltatáspéldányon történő hívása helyett. A `getSystemService(ClipboardManager.class).getPrimaryClip()` hívásának például a `MAMClipboardManager.getPrimaryClip(getSystemService(ClipboardManager.class)` hívásává kell alakulnia. Ezeknek a cseréknek a manuális végrehajtása nem javasolt. Ehelyett hagyja, hogy ezeket a BuildPlugin hajtsa végre.

| Androidos osztály | Intune App SDK-beli helyettesítése |
|--|--|
| android.content.ClipboardManager | MAMClipboard |
| android.content.ContentProviderClient | MAMContentProviderClientManagement |
| android.content.ContentResolver | MAMContentResolverManagement |
| android.content.pm.PackageManager | MAMPackageManagement |
| android.app.DownloadManager | MAMDownloadManagement |
| android.print.PrintManager | MAMPrintManagement |
| android.support.v4.print.PrintHelper | MAMPrintHelperManagement |
| android.view.View | MAMViewManagement |
| android.view.DragEvent | MAMDragEventManagement |

Egyes osztályaival rendelkezik a legtöbb burkolt be, például a módszereket `ClipboardManager`, `ContentProviderClient`, `ContentResolver`, és `PackageManager` míg más osztályok burkolt be, például csak egy vagy két módszert `DownloadManager`, `PrintManager`, `PrintHelper`, `View`, és `DragEvent`. Tekintse meg a MAM egyenértékű osztályokra a pontos metódus által elérhetővé tett, ha nem használja a BuildPlugin API-k. 

### <a name="manifest-replacements"></a>Cserék a jegyzékben
Lehetséges, hogy a fenti osztálycserék egy részét a jegyzékfájlban és a Java-kódban is el kell végezni. Különösen fontos:
* a jegyzékfájlban szereplő `android.support.v4.content.FileProvider`-hivatkozásokat le kell cserélni erre: `com.microsoft.intune.mam.client.support.v4.content.MAMFileProvider`.

## <a name="androidx-libraries"></a>AndroidX függvénytárak
A Google az Android P-vel egy új (átnevezett) támogatási függvénytárhalmazt jelentett be, amelynek a neve AndroidX, és a 28-as verzió a meglévő android.support függvénytárak legújabb fő kiadása.

Az androidos támogatási függvénytáraktól eltérően az AndroidX függvénytárakhoz nem biztosítunk MAM-változókat. Ehelyett az AndroidX függvénytárat ugyanúgy kell kezelni, mint bármely más függvénytárat, és úgy kell konfigurálni, hogy átírja a build beépülő modulja/eszköze. A Gradle buildjeinek esetében ezt meg lehet tenni az `androidx.*` változónak a beépülő modul konfigurációjának `includeExternalLibraries` mezőjébe történő belefoglalásával. A parancssori eszköz indításainak kifejezetten listázniuk kell az összes jar-fájlt.
## <a name="sdk-permissions"></a>Az SDK engedélyei

Az Intune App SDK három [androidos rendszerengedélyt](https://developer.android.com/guide/topics/security/permissions.html) igényel azokhoz az alkalmazásokhoz, amelyekbe beépül:

* `android.permission.GET_ACCOUNTS` (kérése futásidőben történik, ha szükség van rá)

* `android.permission.MANAGE_ACCOUNTS`

* `android.permission.USE_CREDENTIALS`

Az Azure Active Directory Authentication Library ([ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/)) a közvetített hitelesítés végrehajtásához igényli ezeket az engedélyeket. Ha az alkalmazás nem kapja meg ezeket az engedélyeket, vagy ha a felhasználó visszavonja ezeket az engedélyeket, akkor a közvetítőt igénylő hitelesítési folyamatok (a Munkahelyi portál alkalmazás) le lesznek tiltva.

## <a name="logging"></a>Naplózás

A naplózott adatok maximális hasznossága érdekében a naplózást célszerű korán inicializálni. Erre az `Application.onMAMCreate()` a legalkalmasabb hely.

Ha az alkalmazásban MSM-naplókat szeretne fogadni, hozzon létre [Java-kezelőt](https://docs.oracle.com/javase/7/docs/api/java/util/logging/Handler.html), és vegye fel a `MAMLogHandlerWrapper`-be. Ez minden naplóüzenetre meghívja a `publish()` metódust az alkalmazás kezelőjén.

```java
/**
 * Global log handler that enables fine grained PII filtering within MAM logs.  
 *
 * To start using this you should build your own log handler and add it via
 * MAMComponents.get(MAMLogHandlerWrapper.class).addHandler(myHandler, false);  
 *
 * You may also remove the handler entirely via
 * MAMComponents.get(MAMLogHandlerWrapper.class).removeHandler(myHandler);
 */
public interface MAMLogHandlerWrapper {
    /**
     * Add a handler, PII can be toggled.
     *
     * @param handler handler to add.
     * @param wantsPII if PII is desired in the logs.    
     */
    void addHandler(final Handler handler, final boolean wantsPII);

    /**
     * Remove a handler.
     *
     * @param handler handler to remove.
     */
    void removeHandler(final Handler handler);
}
```



## <a name="enable-features-that-require-app-participation"></a>Alkalmazás részvételét igénylő szolgáltatások engedélyezése

Az SDK számos alkalmazásvédelmi szabályzatot nem tud önállóan implementálni. Az alkalmazás a saját működésének szabályozásával képes e funkciókat biztosítani. Ehhez több API-t használ, amelyek az alábbi `AppPolicy` felületen találhatók. Egy `AppPolicy`-példány beolvasásához használja a `MAMPolicyManager.getPolicy`-t.

```java
/**
 * External facing application policies.
 */
public interface AppPolicy {

/**
 * Restrict where an app can save personal data.
 * This function is now deprecated. Please use getIsSaveToLocationAllowed(SaveLocation, String) instead
 * @return True if the app is allowed to save to personal data stores; false otherwise.
 */
@Deprecated
boolean getIsSaveToPersonalAllowed();

/**
 * Check if policy prohibits saving to a content provider location.
 *
 * @param location
 *            a content URI to check
 * @return True if location is not a content URI or if policy does not prohibit saving to the content location.
 */
boolean getIsSaveToLocationAllowed(Uri location);

/**
 * Determines if the SaveLocation passed in can be saved to by the username associated with the cloud service.
 *
 * @param service
 *           see {@link SaveLocation}.
 * @param username
 *           the username/email associated with the cloud service being saved to. Use null if a mapping between
 *           the AAD username and the cloud service username does not exist or the username is not known.
 * @return true if the location can be saved to by the identity, false if otherwise.
 */
boolean getIsSaveToLocationAllowed(SaveLocation service, String username);

/**
 * Checks whether any activities which could handle the given intent are allowed by policy. Returns false only if all
 * activities which could otherwise handle the intent are blocked. If there are no activities which could handle the intent
 * regardless of policy, returns true. If some activities are allowed and others blocked, returns true. Note that it is not
 * necessary to use this method for policy enforcement. If your app attempts to launch an intent for which there are no
 * allowed activities, MAM will display a dialog explaining the situation to the user.
 *
 * @param intent
 *         intent to check
 *
 * @return whether any activities which could handle this intent are allowed.
*/
boolean areIntentActivitiesAllowed(Intent intent);

/**
 * Whether the SDK PIN prompt is enabled for the app.
 *
 * @return True if the PIN is enabled. False otherwise.
 */
boolean getIsPinRequired();

/**
 * Whether the Intune Managed Browser is required to open web links.
 * @return True if the Managed Browser is required, false otherwise
 */
boolean getIsManagedBrowserRequired();

/**
 * Check if policy allows Contact sync to local contact list.
 *
 * @return True if Contact sync is allowed to save to local contact list; false otherwise.
 */
boolean getIsContactSyncAllowed();

/**
 * This method is intended for diagnostic/telemetry purposes only. It can be used to discover whether
 * file encryption is in use. File encryption is transparent to the app, and the app should not need
 * to make any business logic decisions based on this.
 * 
 * @return True if file encryption is in use.
 */
boolean diagnosticIsFileEncryptionInUse();

/**
 * Return the policy in string format to the app.
 *  
 * @return The string representing the policy.
 */
String toString();

}
```

> [!NOTE]
> A `MAMPolicyManager.getPolicy` mindig nem null értékű alkalmazásszabályzatot ad vissza – akkor is, ha az eszközre vagy az alkalmazásra nem vonatkozik Intune-beli felügyeleti szabályzat.

### <a name="example-determine-if-pin-is-required-for-the-app"></a>Példa: PIN-kód az alkalmazáshoz szükséges, hogy

Ha az alkalmazásnak saját felhasználói PIN-kódkezelő funkciója van, akkor azt célszerű letiltani, ha a rendszergazda úgy állította be az SDK-t, hogy az kérjen alkalmazás-PIN-kódot. Az alábbi metódust meghívva állapíthatja meg, hogy a rendszergazda telepített-e alkalmazás-PIN-szabályzatot az alkalmazáshoz az aktuális végfelhasználónál:

```java

MAMPolicyManager.getPolicy(currentActivity).getIsPinRequired();
```

### <a name="example-determine-the-primary-intune-user"></a>Példa: Az elsődleges Intune-felhasználó meghatározása

Az egyszerű felhasználónevet (**UPN**) az AppPolicy-ban elérhető API-kon felül a `MAMUserInfo` interfészben definiált `getPrimaryUser()` API is elérhetővé teszi. Az UPN-t az alábbi kódot meghívva kérheti le:

```java
MAMUserInfo info = MAMComponents.get(MAMUserInfo.class);
if (info != null) return info.getPrimaryUser();
```

Alább a MAMUserInfo interfész teljes definiálása olvasható:

```java
/**
 * External facing user informations.
 *
 */
public interface MAMUserInfo {
       /**
        * Get the primary user name.
        *
        * @return the primary user name or null if the device is not enrolled.
        */
       String getPrimaryUser();
}
```

### <a name="example-determine-if-saving-to-device-or-cloud-storage-is-permitted"></a>Példa: Határozza meg, ha az eszközre való mentése vagy engedélyezve van a felhőalapú tárolás

Számos alkalmazás valósít meg olyan funkciókat, amelyek lehetővé teszik a végfelhasználó számára fájlok mentését helyi háttértárra vagy felhőbeli tárolószolgáltatásba. Az Intune App SDK lehetővé teszi a rendszergazdáknak az adatszivárgás ellen a szervezet igényei szerinti szabályzatkorlátozások alkalmazásával történő védekezést.  A rendszergazda által beállítható szabályzatok egyike arra vonatkozik, hogy a felhasználók menthetnek-e fájlokat nem felügyelt személyes adattárba. Ide tartoznak a helyi mentési helyek, az SD-kártyák és a harmadik felek biztonsági mentési szolgáltatásai.

**A funkció engedélyezéséhez az alkalmazás részvételére van szükség.** Ha az alkalmazás lehetővé teszi a személyes vagy a felhőbeli helyekre való mentést közvetlenül az alkalmazásból, ezt a funkciót meg kell valósítani annak biztosításához, hogy a rendszergazda szabályozhassa, engedélyezve van-e a mentés az adott helyre. Az alábbi API lehetővé teszi, hogy az alkalmazás megállapítsa, hogy a személyes tárolóba való mentés engedélyezve van-e az aktuális Intune-rendszergazda szabályzata szerint. Az alkalmazás ekkor érvényesítheti a házirendet, mivel meg tudja állapítani, hogy elérhető-e személyes adattár a felhasználó számára az alkalmazáson keresztül.  

Az alábbi hívással állapíthatja meg, hogy a szabályzat be van-e tartatva:

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(
SaveLocation service, String username);
```

A `service` paramétert a következők egyikének kell lennie `SaveLocation` értékeket:


- `SaveLocation.ONEDRIVE_FOR_BUSINESS`
- `SaveLocation.SHAREPOINT`
- `SaveLocation.LOCAL`
- `SaveLocation.OTHER`

A `username` az egyszerű felhasználónév/felhasználónév vagy e-mail társítani kell a felhőszolgáltatáshoz való mentésének (*nem* feltétlenül ugyanaz, mint a felhasználó a tulajdonos a dokumentum mentése folyamatban). Használja a NULL értékű, ha az AAD UPN-jét, és a cloud service felhasználónév közötti leképezést nem létezik, vagy a felhasználónév nem ismert.

Korábban ugyanezen **AppPolicy** osztály `getIsSaveToPersonalAllowed()` függvényével lehetett megállapítani, hogy az adott felhasználó szabályzata engedélyezi-e a mentést különféle helyekre. Ez a függvény mostanra **elavult**, és nem szabad használni. Az alábbi kód egyenértékű a `getIsSaveToPersonalAllowed()` függvénnyel:

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(SaveLocation.LOCAL, userNameInQuestion);
```

>[!NOTE]
> A `SaveLocation.OTHER` akkor használatos, ha a szóban forgó hely nem szerepel a **SaveLocations** enumerációban.


## <a name="register-for-notifications-from-the-sdk"></a>Regisztráció az SDK értesítéseire

### <a name="overview"></a>Áttekintés
Az Intune App SDK lehetővé teszi, hogy az alkalmazás szabályozza bizonyos szabályzatok, például a szelektív törlési szabályzat működését, ha a rendszergazda telepítette őket. Amikor a rendszergazda alkalmaz egy ilyen szabályzatot, az Intune szolgáltatás értesítést küld az SDK-nak.

Ehhez regisztrálnia kell az SDK által küldött értesítésekre: hozzon létre egy `MAMNotificationReceiver` osztályt, és regisztrálja a következővel: `MAMNotificationReceiverRegistry`. Ez a fogadó és az `App.onCreate` metódusban fogadni kívánt értesítés típusának megadásával történik, az alábbi példában látható módon:

```java
@Override
public void onCreate() {
  super.onCreate();
  MAMComponents.get(MAMNotificationReceiverRegistry.class)
    .registerReceiver(
      new ToastNotificationReceiver(),
      MAMNotificationType.WIPE_USER_DATA);
  }
```

### <a name="mamnotificationreceiver"></a>MAMNotificationReceiver

A `MAMNotificationReceiver` fogadja az értesítéseket az Intune szolgáltatástól. Egyes értesítéseket közvetlenül az SDK kezel, míg mások az alkalmazás részvételét igénylik. Az alkalmazásnak igaz vagy hamis értéket **kell** visszaadnia az értesítésekből. Hacsak valamely, általa az értesítés eredményeként megkísérelt művelet sikertelen nem volt, mindig igaz értéket kell visszaadjon.

* Ez a hiba megjelenhet az Intune szolgáltatásnak küldött jelentésben. Jelentendő helyzet lehet például az olyan eset, amikor az alkalmazás nem törli a felhasználói adatokat, miután a rendszergazda kezdeményezte a törlést.

>[!NOTE]
> A `MAMNotificationReceiver.onReceive` metódusban biztonságosan blokkolható, mivel a visszahívása nem a felhasználói felület szálán fut.

Alább látható az SDK-ban ily módon definiált `MAMNotificationReceiver` interfész:

```java
/**
 * The SDK is signaling that a MAM event has occurred.
 *
 */
public interface MAMNotificationReceiver {

    /**
     * A notification was received.
     *
     * @param notification
     *            The notification that was received.
     * @return The receiver should return true if it handled the
     *   notification without error (or if it decided to ignore the
     *   notification). If the receiver tried to take some action in
     *   response to the notification but failed to complete that
     *   action it should return false.
     */
    boolean onReceive(MAMNotification notification);
}
```

### <a name="types-of-notifications"></a>Az értesítések típusai

A következő értesítéseket küldi a program az alkalmazásnak, és némelyikük igényelheti az alkalmazás részvételét:

* **WIPE_USER_DATA**: Ezt az értesítést a `MAMUserNotification` osztály. Az értesítés beérkezésekor az alkalmazásnak a `MAMUserNotification` osztály által átadott „vállalati” identitáshoz társított összes adatot törölnie kell. Az értesítést jelenleg az APP-WE szolgáltatásba való beléptetés megszüntetésekor küldi a program. A regisztrációs folyamat során általában sor kerül a felhasználó elsődleges nevének megadására. Ha regisztrál erre az értesítésre, az alkalmazásnak kell gondoskodnia az összes felhasználói adat törléséről. Ha nem regisztrál, az alapértelmezett szelektív törlési viselkedés érvényesül.

* **WIPE_USER_AUXILIARY_DATA**: Alkalmazások akkor regisztrálhatnak erre az értesítésre, ha szeretnék, hogy az Intune App SDK végrehajtsa az alapértelmezett szelektív törlést, de továbbra is szeretné eltávolítani a bizonyos kiegészítő adatokat is törölni kívánnak. Ezt az értesítést, egyetlen identitás-alkalmazások – nem érhető el, csak el lesz küldve a többszörös identitást használó alkalmazások.

* **REFRESH_POLICY**: Ezt az értesítést a `MAMUserNotification`. Az értesítés fogadásakor a gyorsítótárba az alkalmazás által az Intune szabályzat döntések kell érvénytelenítve és frissíteni. Ha az alkalmazás nem tárolja a házirend jósolható, azt nem kell ezt az értesítést regisztráljon.

* **REFRESH_APP_CONFIG**: Ezt az értesítést a `MAMUserNotification`. Az értesítés fogadásakor minden gyorsítótárazott alkalmazás konfigurációs adatokat kell érvénytelenítve és frissíteni.

* **REFRESH_POLICY**: Ezt az értesítést a `MAMUserNotification` és tájékoztatja az alkalmazást, hogy legyen-e készül. Felügyelet nélkül az alkalmazás nem fogja tudni olvasni a titkosított fájlokat, a MAMDataProtectionManagerrel titkosított adatokat, kezelni a titkosított vágólapot, vagy bármilyen más módon részt venni a felügyelt alkalmazások ökoszisztémájában. További részleteket alább találja.

* **MAM_ENROLLMENT_RESULT**: Ezt az értesítést egy `MAMEnrollmentNotification` az alkalmazásnak, hogy egy alkalmazás-azt beléptetési kísérlet befejezése és a kísérlet állapota.

* **COMPLIANCE_STATUS**: Ezt az értesítést a `MAMComplianceNotification` az alkalmazásnak a megfelelőség szervizelési kísérletek eredményéről.

> [!NOTE]
> Az alkalmazások nem regisztrálhatnak egyszerre a `WIPE_USER_DATA` és a `WIPE_USER_AUXILIARY_DATA` értesítésre.

### <a name="managementremoved"></a>REFRESH_POLICY

A `MANAGEMENT_REMOVED` értesítés jelzi, hogy a korábban a házirend által felügyelt felhasználó már nem kell felügyeli az Intune MAM-szabályzatot. Nem igényel felhasználói adatok törlése, és kijelentkezés a felhasználói (a törlési volt szükség, ha egy `WIPE_USER_DATA` értesítés lenne). Számos alkalmazás előfordulhat, hogy nem kell kezelni ezt az értesítést, azonban használó alkalmazásoknak `MAMDataProtectionManager` kell [speciális jegyezze fel ezt az értesítést,](#data-protection).

Ha a MAM meghívja az alkalmazás `MANAGEMENT_REMOVED` fogadó, a következő igaz lesz:
* MAM már rendelkezik visszafejteni a korábban titkosított fájlok (de nem védett pufferek) az alkalmazáshoz tartozó. A sdcard nyilvános helye, amely nem tartozik az alkalmazás közvetlenül a fájlok (például a dokumentumok vagy a letöltési mappák) visszafejtése nem történik meg.
* Új fájlok vagy a fogadó metódus (vagy bármely más, a fogadó megkezdése után futó kódot) által létrehozott védett pufferek nem lesznek titkosítva.
* Az alkalmazás továbbra is hozzáfér, titkosítási kulcs, így műveletek, például a visszafejtési adatok pufferek sikeres lesz.

Az alkalmazás fogadó adja vissza, ha többé nem lesz, hogy hozzáférhessen a titkosítási kulcsokhoz.

## <a name="configure-azure-active-directory-authentication-library-adal"></a>Az Azure Active Directory Authentication Library (ADAL) konfigurálása (nem kötelező)

Először olvassa el a [GitHub ADAL-kódtárában](https://github.com/AzureAD/azure-activedirectory-library-for-android) található ADAL-integrációs irányelveket.

Az SDK a hitelesítési és feltételes indítási forgatókönyvekhez az [ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/)-ra támaszkodik, amely a [hitelesítéshez](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) megköveteli, hogy az alkalmazásokat az [Azure Active Directoryval](https://azure.microsoft.com/documentation/articles/active-directory-whatis/) konfigurálják. A konfigurációs értékeket az SDK az AndroidManifest metaadatain keresztül közli.

Az alkalmazás konfigurálásához és a megfelelő hitelesítés engedélyezéséhez vegye fel a következőket az AndroidManifest.xml-be. Ezen konfigurációk némelyike csak akkor szükséges, ha az alkalmazás általánosan az ADAL-t használja hitelesítéshez. Ebben az esetben azokra a konkrét értékekre is szüksége lesz, amelyekkel az alkalmazás az AAD-ben regisztrálja magát. Így lehet biztosítani, hogy a rendszer ne kérje kétszer a felhasználó hitelesítését. Az AAD ugyanis két különböző regisztrációs értéket ismer fel: egyet az alkalmazásból, egyet pedig az SDK-ból.

```xml
<meta-data
    android:name="com.microsoft.intune.mam.aad.Authority"
    android:value="https://AAD authority/" />
<meta-data
    android:name="com.microsoft.intune.mam.aad.ClientID"
    android:value="your-client-ID-GUID" />
<meta-data
    android:name="com.microsoft.intune.mam.aad.NonBrokerRedirectURI"
    android:value="your-redirect-URI" />
<meta-data
    android:name="com.microsoft.intune.mam.aad.SkipBroker"
    android:value="[true | false]" />
```

### <a name="adal-metadata"></a>ADAL-metaadatok

* **Authority:** a használatban lévő AAD-szolgáltató. Ennek az értéknek a hiánya esetén a nyilvános AAD-környezet lesz használva.
    > [!NOTE]
    > Ne adjon meg értéket a mezőnek, ha az alkalmazása szuverén felhőt használ.

* **ClientID** van az AAD ClientID azonosító (más néven alkalmazás-azonosító) használható. Ha regisztrálva van az Azure AD-ben, akkor az alkalmazás saját ClientID-jét kell használni. Ha ez az érték hiányzik, a rendszer egy Intune-beli alapértelmezett értéket használ.

* **NonBrokerRedirectURI:** a közvetítő nélküli esetekben használandó AAD átirányítási URI. Ha nincs megadva, a rendszer az alapértelmezett `urn:ietf:wg:oauth:2.0:oob` értéket használja. Ez a legtöbb alkalmazáshoz megfelelő.

    * A NonBrokerRedirectURI csak akkor használható, ha a SkipBroker értéke "true".

* **SkipBroker** segítségével felülírhatja az alapértelmezett ADAL SSO részvételi viselkedést. SkipBroker csak akkor szabad megadni az alkalmazásokhoz, melyek adja meg a ClientID **és** nem támogatja a közvetített hitelesítést/eszközszintű SSO. Ebben az esetben kell állítani "true". A legtöbb alkalmazás nem kell beállítani a SkipBroker paramétert.

    * A ClientID **kell** SkipBroker értéket a jegyzékfájlba adható meg.

    * Ha a ClientID meg van adva, az alapértelmezett értéke "false".

    * Ha a SkipBroker értéke "true", a NonBrokerRedirectURI lesz. Integrálja az adal-t (és így kell nincs ClientID) alkalmazásokat is alapértelmezés szerint "true".

### <a name="common-adal-configurations"></a>Általános ADAL-konfigurációk

A következőkben az alkalmazások ADAL-konfigurációjának gyakori eseteit mutatjuk be. Keresse meg az alkalmazásához illő esetet, és állítsa be az ADAL (fent ismertetett) metaadat-paramétereit a megfelelő értékekre. Minden esetben előfordulhat, hogy adható meg a szolgáltató nem alapértelmezett környezetek jelölését. Ha nincs megadva, az AAD-szolgáltató nyilvános üzemi használható.

#### <a name="1-app-does-not-integrate-adal"></a>1. Az alkalmazás nem integrálja az ADAL-t
ADAL-metaadatok **nem kell** szerepel a jegyzékfájlban.

#### <a name="2-app-integrates-adal"></a>2. Az alkalmazás integrálja az ADAL-t

|Szükséges ADAL-paraméter| Value |
|--|--|
| ClientID | Az alkalmazás ClientID azonosítója (az Azure AD állítja elő az alkalmazás regisztrálásakor) |

Előfordulhat, hogy adható meg a szolgáltató szükség esetén.

Kell regisztrálnia az alkalmazást az Azure ad-vel és az alkalmazás hozzáférést biztosít a app protection szolgáltatás:
* Az alkalmazások Azure AD-ban való regisztrálásáról [itt](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) találhat információt.
* Győződjön meg arról, az Android-alkalmazás engedélyt az alkalmazásvédelmi szabályzat (alkalmazás) app Service a lépéseket követi. Útmutatásait a [első lépések az Intune SDK útmutatóját](https://docs.microsoft.com/intune/app-sdk-get-started#next-steps-after-integration) alatt "az alkalmazás hozzáférést biztosít az Intune app protection szolgáltatás (nem kötelező)". 

Lásd emellett alább a [Feltételes hozzáférés](#conditional-access) követelményeit.


#### <a name="3-app-integrates-adal-but-does-not-support-brokered-authenticationdevice-wide-sso"></a>3. Az alkalmazás integrálja az adal-t, de nem támogatja a közvetített hitelesítést/eszközszintű SSO

|Szükséges ADAL-paraméter| Value |
|--|--|
| ClientID | Az alkalmazás ClientID azonosítója (az Azure AD állítja elő az alkalmazás regisztrálásakor) |
| SkipBroker | **True** |

Az Authority és a NonBrokerRedirectURI megadható szükséges esetén.

### <a name="conditional-access"></a>Feltételes hozzáférés

A feltételes hozzáférés egy Azure Active Directorybeli [szolgáltatás](https://docs.microsoft.com/azure/active-directory/develop/active-directory-conditional-access-developer), mellyel vezérelheti az AAD-erőforrások elérését. [Az Intune-rendszergazdák definiálhatnak feltételes hozzáférési szabályokat](https://docs.microsoft.com/intune/conditional-access), melyekkel az erőforrások elérését az Intune által felügyelt eszközökre és alkalmazásokra korlátozhatják. Kövesse az alábbi lépéseket annak biztosításához, hogy az alkalmazása el tudja érni a szükséges erőforrásokat. Ha az alkalmazása nem szerez be egyetlen AAD-hozzáférési tokent sem, vagy ha csak feltételes hozzáféréssel nem védhető erőforrásokhoz fér hozzá, akkor kihagyhatja ezeket a lépéseket.

1. Kövesse az [ADAL-integráció irányelveit](https://github.com/AzureAD/azure-activedirectory-library-for-android#how-to-use-this-library). 
   Fordítson különös figyelmet a 11. lépésben ismertetett közvetítőhasználatra.
2. [Regisztrálja az alkalmazását az Azure Active Directoryban] (https://docs.microsoft.com/azure/active-directory/active-directory-app-registration). 
   Az átirányítási URI-t megtalálhatja a fentebb hivatkozott ADAL-integrációs irányelvekben.
3. Állítsa be a jegyzékfájl metaadat-paramétereit az [Általános ADAL-konfigurációk](#common-adal-configurations) szerint (2. elem, fentebb).
4. Tesztelje a konfiguráció helyességét. Ehhez engedélyezze az [eszközalapú feltételes hozzáférést](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use) az [Azure Portalon](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExchangeConnectorMenu/aad/connectorType/2), és bizonyosodjon meg a következőkről:
    - Hogy az alkalmazásába való bejelentkezéskor a rendszer kéri a Céges portál telepítését és regisztrálását.
    - Hogy a regisztrálás után sikeresen befejeződik az alkalmazásába való bejelentkezés.
5. Forduljon az alkalmazás az Intune APP SDK-integráció leszállítását követően msintuneappsdk@microsoft.com jóváhagyott alkalmazások listájára hozzáadandó [alkalmazásalapú feltételes hozzáférés](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use#app-based-conditional-access)
6. Miután az alkalmazását hozzáadtuk a jóváhagyott alkalmazások listájához, ellenőrizze a rendszer működését. Ehhez [konfigurálja az alkalmazásalapú feltételes hozzáférést](https://docs.microsoft.com/intune/app-based-conditional-access-intune-create), és győződjön meg róla, hogy az alkalmazásába való bejelentkezés sikeresen befejeződik.

## <a name="app-protection-policy-without-device-enrollment"></a>Eszközregisztráció nélküli alkalmazásvédelmi szabályzat

### <a name="overview"></a>Áttekintés
Az Intune APP-WE vagy MAM-WE néven is ismert eszközbeléptetés nélküli alkalmazásvédelmi szabályzata lehetővé teszi, hogy az Intune anélkül is felügyelhesse az alkalmazásokat, hogy az eszközök az Intune MDM-re regisztrálva lennének. Az APP-WE működik eszközbeléptetéssel és anélkül is. A Céges portál alkalmazást továbbra is telepíteni kell az eszközre, de a felhasználónak nem kell bejelentkeznie a Céges portálba és beléptetnie az eszközt.

> [!NOTE]
> Az összes alkalmazásnak támogatnia kell az alkalmazásvédelmi szabályzatok eszközbeléptetés nélküli használatát.

### <a name="workflow"></a>Munkafolyamat

Ha egy alkalmazás új felhasználói fiókot hoz létre, azt regisztrálnia kell felügyeletre az Intune App SDK-val. Az SDK kezeli az alkalmazás APP-WE szolgáltatásba való beléptetésének részleteit; szükség esetén a megfelelő időközönként újból megpróbálkozik a beléptetéssel, ha az sikertelen.

Az alkalmazás az Intune App SDK-tól kérdezheti le a regisztrált felhasználók állapotát is, amikor azt próbálja megállapítani, hogy az illetőt el kell-e tiltani a vállalati tartalom elérésétől. Több fiókot is lehet felügyeletre regisztrálni, de jelenleg egyszerre csak egy lehet aktívan beléptetve az APP-WE szolgáltatásba, és így az alkalmazásban is egyszerre csak egy fiók kaphat alkalmazásvédelmi szabályzatot.

Az alkalmazásnak visszahívás útján kell megszereznie a megfelelő hozzáférési jogkivonatot az Azure Active Directory Authentication Librarytől (ADAL) az SDK nevében. Az alapfeltevés az, hogy az alkalmazás már az ADAL-lal hitelesíti a felhasználókat és szerzi be a saját hozzáférési jogkivonatát.

Amikor az alkalmazás teljesen eltávolít egy fiókot, meg kell szüntetnie annak regisztrációját, így jelezve, hogy a továbbiakban az adott felhasználóra nem kell szabályzatot alkalmazni. Ha a felhasználó be volt léptetve a MAM-szolgáltatásba, akkor a beléptetés megszűnik, az alkalmazás pedig törlődik.


### <a name="overview-of-app-requirements"></a>Az alkalmazások követelményeinek áttekintése

Az APP-WE-integráció implementálásához az alkalmazásnak a felhasználói fiókot regisztrálnia kell a MAM SDK-val:

1. Az alkalmazásnak _kötelező_ a `MAMServiceAuthenticationCallback` interfész egy példányát implementálni és regisztrálni. A visszahívási példányt az alkalmazás életciklusának lehető legkorábbi pontján kell regisztrálni (jellemzően az alkalmazás osztályának `onMAMCreate()` metódusában).

2. Felhasználói fiók létrejötte és a felhasználó sikeres ADAL-bejelentkezése után alkalmazásnak _kötelező_ meghívni a `registerAccountForMAM()` metódust.

3. Felhasználói fiók eltávolítása után az alkalmazásnak az `unregisterAccountForMAM()` metódussal kell eltávolítania a fiókot az Intune-felügyeletből.

    > [!NOTE]
    > Ha egy felhasználó átmenetileg kijelentkezik az alkalmazásból, akkor nincs szükség az `unregisterAccountForMAM()` meghívására, mert előfordulhat, hogy ez törlést kezdeményez, és eltávolítja a felhasználó céges adatait.


### <a name="mamenrollmentmanager"></a>MAMEnrollmentManager

Az összes szükséges hitelesítési és regisztrációs API a `MAMEnrollmentManager` interfészben található. `MAMEnrollmentManager`-hivatkozást az alábbi módon lehet szerezni:

```java
MAMEnrollmentManager mgr = MAMComponents.get(MAMEnrollmentManager.class);

// make use of mgr
```

A visszaadott `MAMEnrollmentManager`-példány garantáltan nem null értékű. Az API-metódusok között vannak **hitelesítésre** és **fiókregisztrációra** használatosak.

```java
package com.microsoft.intune.mam.policy;

public interface MAMEnrollmentManager {
    public enum Result {
        AUTHORIZATION_NEEDED,
        NOT_LICENSED,
        ENROLLMENT_SUCCEEDED,
        ENROLLMENT_FAILED,
        WRONG_USER,
        MDM_ENROLLED,
        UNENROLLMENT_SUCCEEDED,
        UNENROLLMENT_FAILED,
        PENDING,
        COMPANY_PORTAL_REQUIRED;
    }

    //Authentication methods
    interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
    }
    void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
    void updateToken(String upn, String aadId, String resourceId, String token);

    //Registration methods
    void registerAccountForMAM(String upn, String aadId, String tenantId);
    void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
    void unregisterAccountForMAM(String upn);
    Result getRegisteredAccountStatus(String upn);
}
```

### <a name="account-authentication"></a>Fiókhitelesítés

Ez a szakasz a `MAMEnrollmentManager` hitelesítési API-metódusait és azok használatát ismerteti.

```java
interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
}
void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
void updateToken(String upn, String aadId, String resourceId, String token);
```

1. Az alkalmazásnak a `MAMServiceAuthenticationCallback` interfész implementálásával kell biztosítania, hogy az SDK kérhessen ADAL-jogkivonatot az adott felhasználóhoz és erőforrás-azonosítóhoz. A `MAMEnrollmentManager` számára annak `registerAuthenticationCallback()` metódusát meghívva kell biztosítani a visszahívási példányt. Az alkalmazás életciklusának már korai szakaszában is szükség lehet jogkivonatra a beléptetési újrapróbálkozásokhoz vagy az alkalmazásvédelmi szabályzat frissítésének kereséséhez, így a visszahívást ideálisan az alkalmazás `MAMApplication` alosztályának `onMAMCreate()` metódusában érdemes regisztrálni.

2. A kért erőforrás-azonosítóra szóló hozzáférési jogkivonatot az `acquireToken()` metódusnak kell beszereznie az adott felhasználó számára. Ha ez nem sikerül, a metódusnak null értéket kell visszaadnia.

    > [!NOTE]
    > Győződjön meg arról, hogy az alkalmazás már használja a `resourceId` és `aadId` átadott paraméterek `acquireToken()` úgy, hogy a helyes-e jogkivonat beszerzése van.

    ```java
    class MAMAuthCallback implements MAMServiceAuthenticationCallback {
        public String acquireToken(String upn, String aadId, String resourceId) {
            return mAuthContext.acquireTokenSilentSync(resourceId, ClientID, aadId).getAccessToken();
        }
    }
    ```

3. Ha az alkalmazás nem tud jogkivonatot biztosítani, amikor az SDK meghívja az `acquireToken()` metódust – például mert a csendes hitelesítés sikertelen és éppen nem lehet felhasználói felületet megjeleníteni –, később az `updateToken()` metódust meghívva teheti ezt meg. Az `updateToken()` metódusnak az `acquireToken()` korábbi meghívásakor használt UPN-t, AAD-azonosítót és erőforrás-ID kell átadni a végül beszerzett jogkivonattal együtt. Az alkalmazásnak a lehető leghamarabb meg kell hívnia ezt a metódust, miután a megadott visszahívás a null értéket adta.

    > [!NOTE]
    > Az SDK rendszeres időközönként megpróbálja az `acquireToken()` meghívásával megszerezni a jogkivonatot, így az `updateToken()` meghívása szigorúan véve nem szükséges, Azonban erősen ajánlott elősegítheti a beléptetések és időben befejezéséhez alkalmazás alkalmazásvédelmi szabályzat-ellenőrzéshez.


### <a name="account-registration"></a>Fiókregisztráció

Ez a szakasz a `MAMEnrollmentManager` fiókregisztrációs API-metódusait és azok használatát ismerteti.

```java
void registerAccountForMAM(String upn, String aadId, String tenantId);
void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
void unregisterAccountForMAM(String upn);
Result getRegisteredAccountStatus(String upn);
```

1. A fiókokat az alkalmazásnak a `registerAccountForMAM()` metódust meghívva kell regisztrálnia a felügyelet alá. A felhasználói fiókot egyszerű felhasználóneve (UPN) és AAD-s felhasználói azonosítója is azonosítja. A beléptetési adatoknak a felhasználó AAD-bérlőjéhez társításához a bérlőazonosító is szükséges. A felhasználó jogosultságának előfordulhat, hogy is meg kell adni a regisztráció engedélyezéséhez szuverén felhők; ellen További információ: [szuverén felhő regisztrációs](#sovereign-cloud-registration).  Az SDK megpróbálhatja az adott felhasználó számára beléptetni az alkalmazást a MAM-szolgáltatásba. Ha a beléptetés sikertelen, akkor rendszeres időközönként újra fog próbálkozni vele, amíg a fiók regisztrációja meg nem szűnik. Az újrapróbálkozások időköze általában 12–24 óra. Az SDK aszinkron módon, értesítések útján közli a beléptetési kísérletek állapotát.

2. AAD-hitelesítés szükség, mert a legjobb akkor regisztrálni, amikor a felhasználói fiók van, miután a felhasználó van bejelentkezve az alkalmazásba, és az ADAL használatával sikeres hitelesítése. A felhasználó AAD-Azonosítóját és Bérlőazonosítóját a rendszer adja vissza az ADAL-hitelesítési hívás során a [ `AuthenticationResult` ](https://github.com/AzureAD/azure-activedirectory-library-for-android) objektum.
    * A bérlőazonosító az `AuthenticationResult.getTenantID()` metódusból származik.
    * A felhasználóval kapcsolatos adatok egy, az `AuthenticationResult.getUserInfo()` metódusból származó, `UserInfo` típusú alobjektumban találhatók meg, az AAD-beli felhasználót pedig ebből az objektumból lehet lekérni a `UserInfo.getUserId()` metódussal.

3. A fiókok Intune-felügyeleti regisztrációját az alkalmazásnak az `unregisterAccountForMAM()` metódust meghívva kell megszüntetnie. Ha a fiók sikeresen be lett léptetve, és felügyelt fiók lett, az SDK fogja megszüntetni a beléptetését és törölni az adatait. A rendszeres időközönkénti beléptetési próbálkozások abbamaradnak. Az SDK aszinkron módon, értesítések útján beléptetés-megszüntetési kérések állapotát biztosít.

### <a name="sovereign-cloud-registration"></a>Regisztrálás szuverén felhőbe

A [szuverén felhőt használó](https://www.microsoft.com/trustcenter/cloudservices/nationalcloud) alkalmazásoknak **mindenképp** meg kell adniuk az `authority` beállítást a `registerAccountForMAM()` metódushoz.  Ezt úgy szerezheti be, hogy megadja az `instance_aware=true` értéket az ADAL [1.14.0+](https://github.com/AzureAD/azure-activedirectory-library-for-android/releases/tag/v1.14.0) acquireToken metódusának extraQueryParameters paraméterében, majd meghívja a `getAuthority()` metódust az AuthenticationCallback AuthenticationResult példányon.

```java
mAuthContext.acquireToken(this, RESOURCE_ID, CLIENT_ID, REDIRECT_URI, PromptBehavior.FORCE_PROMPT, "instance_aware=true",
        new AuthenticationCallback<AuthenticationResult>() {
            @Override
            public void onError(final Exception exc) {
                // authentication failed
            }

            @Override
            public void onSuccess(final AuthenticationResult result) {
                mAuthority = result.getAuthority();
                // handle other parts of the result
            }
        });
```

> [!NOTE]
> Nincs beállítva a `com.microsoft.intune.mam.aad.Authority` metaadatok konfigurációelem-AndroidManifest.xml fájlban.

> [!NOTE]
> Győződjön meg róla, hogy a szolgáltató (authority) megfelelően van beállítva a `MAMServiceAuthenticationCallback::acquireToken()` metódusban.

#### <a name="currently-supported-sovereign-clouds"></a>Jelenleg támogatott szuverén felhők

1. Arlington

### <a name="important-implementation-notes"></a>Fontos megjegyzések az implementálással kapcsolatban

#### <a name="authentication"></a>Authentication

* Amikor az alkalmazás meghívja a `registerAccountForMAM()` metódust, kis idővel utána visszahívást kaphat egy másik szálon a `MAMServiceAuthenticationCallback` interfészén. Ideális esetben az alkalmazás meggyorsítva a kért jogkivonatot a fiók regisztrálása előtt beszerezte saját jogkivonatát az adal-t. Az alkalmazás a visszahívásból érvényes jogkivonatot ad vissza, ha a beléptetés folytatódik, és az alkalmazás megkapja az értesítést a végeredményt.

* Ha az alkalmazás nem ad vissza érvényes AAD-jogkivonatot, a beléptetés végeredménye `AUTHENTICATION_NEEDED` lesz. Az alkalmazás ezt az eredményt értesítést kap, ha a beléptetési folyamat meggyorsítása a felhasználói token beszerzése által, erősen ajánlott, és korábban már kért erőforrás `acquireToken()` és hív-e a `updateToken()` metódus kezdeményezése a regisztrációs folyamatot újra.

* Az alkalmazás regisztrált `MAMServiceAuthenticationCallback` interfésze is meg lesz hívva az alkalmazásvédelmi szabályzatok frissítéseinek rendszeres kereséséhez szükséges jogkivonat beszerzése céljából. Ha az alkalmazás kérésre nem tudja biztosítani a kért jogkivonatot, akkor nem fog értesítést kapni, de meg kell próbálnia jogkivonatot beszerezni, és a legközelebbi alkalmas időpontban meghívni az `updateToken()` metódust a beléptetési folyamat meggyorsítása érdekében. A visszahívás akkor is meg lesz hívva a következő beléptetési kísérletnél, ha nincs jogkivonat.

* A szuverén felhők támogatásához meg kell adnia a szolgáltatót (authority).

#### <a name="registration"></a>Regisztráció

* Az egyszerűség kedvéért a regisztrációs metódusok idempotensek. A `registerAccountForMAM()` például csak akkor regisztrálja a fiókot és próbálja meg beléptetni az alkalmazást, ha a fiók még nincs regisztrálva, az `unregisterAccountForMAM()` pedig csak akkor törli a fiók regisztrációját, ha az az adott időpontban regisztrálva van. Az ismételt hívások hatástalanok lesznek, így ezeket a metódusokat következmény nélkül meg lehet hívni többször is. Ezenkívül levelezést metódusok és értesítéseket az eredmények között nem garantált: Vagyis ha `registerAccountForMAM` nevezzük az identitást, amely már regisztrálva van, az értesítés nem lehet elküldeni újra az identitásukat. Lehetnek olyan értesítések is, amelyek nem kapcsolódnak ezen metódusok meghívásához, mivel az SDK rendszeres időközönként próbálkozik beléptetésekkel a háttérben, az Intune szolgáltatástól érkező törlési kérések pedig kiválthatnak beléptetés-visszavonásokat.

* A regisztrációs metódusokat tetszőleges számú különböző identitáshoz meg lehet hívni, de jelenleg egyszerre csak egy felhasználói fiókot lehet sikeresen beléptetni. Ha több, az Intune-hoz licencelt és alkalmazásvédelmi szabályzattal célzott felhasználói fiókot regisztrálnak egyszerre vagy csaknem egy időben, akkor nem lehet előre tudni, hogy melyik nyeri a versenyt.

* Végül a `MAMEnrollmentManager` interfésztől lehet lekérdezni, hogy egy bizonyos fiók regisztrálva van-e, és a `getRegisteredAccountStatus` metódussal lehet lekérni az aktuális állapotát. Ha a megadott fiók nincs regisztrálva, a metódus a **null** értéket adja vissza. Ha a fiók regisztrálva van, a metódus a `MAMEnrollmentManager.Result` enumeráció valamely elemével jelzi a fiók állapotát.

### <a name="result-and-status-codes"></a>Eredmény- és állapotkódok

A fiók az első regisztráció során `PENDING` állapotban kerül be a rendszerbe, jelezvén, hogy a MAM-szolgáltatásba való kezdeti beléptetési kísérlet még nem fejeződött be. A beléptetési kísérlet befejezése után egy értesítés jön létre az alábbi táblázatban felsorolt eredménykódok valamelyikével. Ezenkívül a `getRegisteredAccountStatus()` metódus visszaadja a fiók állapotát, hogy az alkalmazás bármikor el tudja dönteni, hogy letiltsa-e az adott felhasználó hozzáférését a vállalati tartalomhoz. Ha a beléptetési kísérlet sikertelen, a fiók állapota idővel változhat, amint az SDK a háttérben tovább próbálkozik a beléptetéssel.

|Eredménykód | Magyarázat |
| -- | -- |
|AUTHORIZATION_NEEDED | Ez az eredmény azt jelzi, hogy az alkalmazás regisztrált `MAMServiceAuthenticationCallback`-példánya nem szolgáltatott jogkivonatot, vagy az érvénytelen volt.  Az alkalmazásnak be kell szereznie egy jogkivonatot, és lehetőség szerint meg kell hívnia az `updateToken()` metódust. |
| NOT_LICENSED | A felhasználónak nincs Intune-licence, vagy sikertelen volt az Intune MAM-szolgáltatáshoz való kapcsolódás.  Az alkalmazásnak nem felügyelt (normál) állapotban kell tovább futnia, a felhasználót pedig nem kell blokkolni.  Amennyiben később a felhasználónak lesz licence, az SDK rendszeresen próbálkozik a beléptetéssel. |
| ENROLLMENT_SUCCEEDED | A beléptetési kísérlet sikeres volt, vagy a felhasználó már korábban be lett léptetve.  Sikeres beléptetés esetén ezt az értesítést megelőzően egy szabályzatfrissítési értesítést is küld a rendszer.  A vállalati adatokhoz való hozzáférést engedélyezni kell. |
| ENROLLMENT_FAILED | A beléptetési kísérlet sikertelen volt.  A további részletek az eszköznaplókban találhatók.  Az alkalmazás ebben az állapotban nem engedélyezheti a vállalati tartalomhoz való hozzáférést, hiszen korábban megállapította, hogy a felhasználónak van Intune-licence.|
| WRONG_USER | Egy eszközön minden alkalmazást csak egy felhasználó léptethet be a MAM-szolgáltatásba.  Másik felhasználó csak akkor hajthat végre sikeres beléptetést, ha előbb az összes beléptetett alkalmazás beléptetését megszüntetik.  Ellenkező esetben ezt az alkalmazást is csak az elsődleges felhasználó léptetheti be.  Ez az ellenőrzés a licencellenőrzés után zajlik le, tehát a felhasználó céges adatokhoz való hozzáférését az alkalmazás sikeres beléptetéséig tiltani kell.|
| UNENROLLMENT_SUCCEEDED | A beléptetés megszüntetése sikeres volt.|
| UNENROLLMENT_FAILED | A beléptetés-megszüntetési kérés sikeres volt.  A további részletek az eszköznaplókban találhatók. |
| PENDING | A felhasználó első beléptetési kísérlete folyamatban van.  Az alkalmazás a beléptetés eredményének ismertté válásáig letilthatja a vállalati adatokhoz való hozzáférést, de nem köteles így tenni. |
| COMPANY_PORTAL_REQUIRED | A felhasználónak van Intune-licence, de az alkalmazást nem lehet beléptetni, amíg a Céges portál alkalmazás nincs telepítve az eszközre. Az Intune App SDK megpróbálja megtagadni az alkalmazáshoz való hozzáférést az adott felhasználótól, és felszólítani a Céges portál alkalmazás telepítésére (részletek alább). |


### <a name="company-portal-requirement-prompt-override-optional"></a>A Céges portál követelményére való figyelmeztetés felülbírálása (nem kötelező)

`COMPANY_PORTAL_REQUIRED` eredmény esetén az SDK letiltja az ahhoz az identitáshoz kapcsolódó tevékenységeket, amelynek a beléptetése a kérés tárgya volt. Az SDK ezen tevékenységekre válaszul egy, a Céges portál alkalmazás letöltését kérő üzenetet jelenít meg. Ha ezt a saját alkalmazásában szeretné elkerülni, a tevékenységek implementálhatják a `MAMActivity.onMAMCompanyPortalRequired` metódust.

Ennek meghívása még az előtt történik, hogy az SDK megjelenítené az alapértelmezett letiltó felhasználói felületet. Ha az alkalmazás módosítja a tevékenység identitását, vagy törli a beléptetést megkísérlő felhasználó regisztrációját, az SDK nem fogja letiltani a tevékenységet. Ebben az esetben az alkalmazás feladata a vállalati adatszivárgás megakadályozása. Az aktív identitás megváltoztatására csak a többidentitású alkalmazások (lásd alább) képesek.

Ha explicit módon nem örököl `MAMActivity` osztályt (mivel a build-eszköz hajtja végre ezt a módosítást), de továbbra is kezelnie kell ezt az értesítést, akkor ehelyett implementálhatja a `MAMActivityBlockingListener` osztályt.

### <a name="notifications"></a>Értesítések

Ha az alkalmazás regisztrál típusú értesítések **MAM_ENROLLMENT_RESULT**, amely egy `MAMEnrollmentNotification` szeretné küldeni az alkalmazást, amelyet a beléptetési kérés befejezéséről tájékoztatja. A `MAMEnrollmentNotification` értesítés fogadása a `MAMNotificationReceiver` interfészen keresztül történik, a [Regisztráció az SDK értesítéseire](#register-for-notifications-from-the-sdk) című szakaszban leírtak szerint.

```java
public interface MAMEnrollmentNotification extends MAMUserNotification {
    MAMEnrollmentManager.Result getEnrollmentResult();
}
```

A `getEnrollmentResult()` metódus a beléptetési kérés eredményét adja vissza.  Mivel a `MAMEnrollmentNotification` a `MAMUserNotification` kiterjesztése, a beléptetési kérés által érintett felhasználó identitása is elérhető. Az alkalmazásnak ezen értesítések fogadásához a [Regisztráció az SDK értesítéseire](#register-for-notifications-from-the-sdk) című szakaszban leírtaknak megfelelően implementálnia kell a `MAMNotificationReceiver` interfészt.

A regisztrált felhasználói fiók állapota beléptetési értesítés érkezik, de nem minden esetben változik, előfordulhat, hogy módosítani. (például, ha `AUTHORIZATION_NEEDED` értesítés érkezik egy konkrétabb eredménykód után például `WRONG_USER`, annál több informatív eredmény lesz továbbra is a fiók állapotát).  Ha a fiók sikeresen regisztrálta, az állapot marad, `ENROLLMENT_SUCCEEDED` mindaddig, amíg a fiók regisztrációját megszüntetik vagy tartalmának végleges törléséig.

A regisztrált felhasználói fiók állapota beléptetési értesítés érkezik, de nem minden esetben változik, előfordulhat, hogy módosítani. (például, ha `AUTHORIZATION_NEEDED` értesítés érkezik egy konkrétabb eredménykód után például `WRONG_USER`, annál több informatív eredmény lesz továbbra is a fiók állapotát).  Ha a fiók sikeresen regisztrálta, az állapot marad, `ENROLLMENT_SUCCEEDED` mindaddig, amíg a fiók regisztrációját megszüntetik vagy tartalmának végleges törléséig.

## <a name="app-ca-with-policy-assurance"></a>A házirend-frissítési garanciát biztosító alkalmazás hitelesítésszolgáltató

### <a name="overview"></a>Áttekintés
Alkalmazás CA (feltételes hozzáférés) házirend garanciával működő, az erőforrásokhoz való hozzáférés az Intune alkalmazásvédelmi szabályzatokat az alkalmazásra van conditionalized.  Aad-ben ez érvényesíti, azzal, hogy az alkalmazásnak, hogy a rendszer által regisztrált és felügyelt alkalmazás eléréséhez egy alkalmazás Hitelesítésszolgáltatót házirend garanciával működő védett erőforrás-jogkivonat megadása előtt.  Az alkalmazás a token beszerzéséhez az ADAL broker használatához szükséges, és a beállítás megegyezik a fentieknek megfelelően [feltételes hozzáférés](#conditional-access)

### <a name="adal-changes"></a>ADAL módosítások
Az ADAL-könyvtár tartalmaz egy új hibakód arról értesíti az alkalmazást, amelyet egy token beszerzéséhez a hibát okozta alkalmazásfelügyelet meg nem felelés.  Ha az alkalmazás megkapja az erről a hibakódról, próbálja meg elhárítani a megfelelőségi házirend, és regisztrálja az alkalmazást az SDK-t hívja kell. Kivételt fogja fogadni a `onError()` metódus az adal `AuthenticationCallback`, és a hiba kódja `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED`.  Ebben az esetben a kivétel is konvertálható egy `IntuneAppProtectionPolicyRequiredException`, a további paramétereket az kinyerhetők a használatra a megfelelőség javítása (lásd az alábbi mintakód). Ha a szervizelés sikeresen megtörtént, az alkalmazás újból megkísérelheti a token beszerzéséhez az ADAL használatával.

> [!NOTE]
> Az új hibakód és egyéb támogatási házirend tudatban alkalmazás hitelesítésszolgáltató 1.15.0 verziójának megkövetelése (vagy nagyobb) az ADAL-könyvtár.

### <a name="mamcompliancemanager"></a>MAMComplianceManager

A `MAMComplianceManager` fogadásakor. a szabályzat által megkövetelt hiba az ADAL illesztője.  Tartalmazza a `remediateCompliance()` metódushoz, amely megpróbálja az alkalmazás megfelelő állapotba kell meghívni. `MAMComplianceManager`-hivatkozást az alábbi módon lehet szerezni:

```java
MAMComplianceManager mgr = MAMComponents.get(MAMComplianceManager.class);

// make use of mgr
```

A visszaadott `MAMComplianceManager`-példány garantáltan nem null értékű.

```java
package com.microsoft.intune.mam.policy;

public interface MAMComplianceManager {
    void remediateCompliance(String upn, String aadId, String tenantId, String authority, boolean showUX);
}
```

A `remediateCompliance()` módszert hívja meg próbál meg az alkalmazást, hogy megfelel a feltételeknek, adja meg a kért jogkivonatot az aad-beli felügyelete alá helyezi.  Az első négy paraméterek a kivételt az ADAL által fogadott kinyerésének `AuthenticationCallback.onError()` metódus (lásd az alábbi mintakód).  A végső paraméter olyan logikai érték, amely azt vezérli, hogy látható-e a felhasználói felület a megfelelőségi kísérlet során.  Ez az egyszerű blokkoló folyamatban stílus felületet alapértelmezés szerint előírt alkalmazások, amelyek nem rendelkeznek a szükséges testre szabott felhasználói felület megjelenítése során ezt a műveletet.  Csak letiltja a megfelelőség szervizelési folyamatban van, és nem jelennek meg a végső eredményt.  Az alkalmazás kell regisztrálni egy értesítést fogadó kezelni a sikeres vagy sikertelen a megfelelőség szervizelési kísérlet (lásd alább).

A `remediateCompliance()` módszerrel teheti meg, a MAM-regisztrációját, a megfelelőségi létrehozó részeként.  Az alkalmazás beléptetési értesítés kaphat, ha regisztrálva van az értesítést fogadó regisztrációs értesítéseket.  Az alkalmazás regisztrált `MAMServiceAuthenticationCallback` fog rendelkezni annak `acquireToken()` metodu volat jogkivonat beszerzéséhez a MAM-regisztrációját. `acquireToken()` neve az alkalmazás már beszerezte saját jogkivonatát, így minden nyilvántartási vagy a fiók létrehozási feladatot, amely az alkalmazás egy sikeres token beszerzése után előfordulhat, hogy rendelkezik még nem tette előtt.  A visszahívás egy token beszerzéséhez ebben az esetben képesnek kell lennie.  Ha nem téríthetők vissza származó jogkivonat `acquireToken()`, a megfelelőség szervizelési kísérlet sikertelen lesz.  Ha felhívja `updateToken()` később a kért erőforrás érvényes token az a megfelelőség szervizelési megpróbálja közvetlenül az adott tokennel.

> [!NOTE]
> Beavatkozás nélküli token beszerzéséhez továbbra is lehetséges a `acquireToken()` , mert a felhasználó fog rendelkezik már lett interaktív az ügynök telepítése, és regisztrálja az eszközt, mielőtt `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED` hibaüzenet érkezik.  Ennek eredményeképpen a közvetítő kellene egy érvényes frissítési jogkivonat a gyorsítótárban, lehetővé téve a kért jogkivonat sikeres csendes acqisition.

Íme egy példa a szabályzat által megkövetelt hiba azért a `AuthenticationCallback.onError()` módját, valamint hívása a `MAMComplianceManager` kezelni a hibát.

```java
public void onError(@Nullable Exception exc) {
    if (exc instanceof AuthenticationException && 
        ((AuthenticationException) exc).getCode() == ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED) {

        final IntuneAppProtectionPolicyRequiredException policyRequiredException = 
            (IntuneAppProtectionPolicyRequiredException) ex;

        final String upn = policyRequiredException.getAccountUpn();
        final String aadId = policyRequiredException.getAccountUserId();
        final String tenantId = policyRequiredException.getTenantId();
        final String authority = policyRequiredException.getAuthorityURL();

        MAMComplianceManager complianceManager = MAMComponents.get(MAMComplianceManager.class);
        complianceManager.remediateCompliance(upn, aadId, tenantId, authority, showUX);
    }
}
```

### <a name="status-notifications"></a>Állapotra vonatkozó értesítések

Ha az alkalmazás regisztrál típusú értesítések **COMPLIANCE_STATUS**, amely egy `MAMComplianceNotification` tájékoztatja az alkalmazást a megfelelőség szervizelési kísérlet a végső állapotának küld. A `MAMComplianceNotification` értesítés fogadása a `MAMNotificationReceiver` interfészen keresztül történik, a [Regisztráció az SDK értesítéseire](#register-for-notifications-from-the-sdk) című szakaszban leírtak szerint.

```java
public interface MAMComplianceNotification extends MAMUserNotification {
    MAMCAComplianceStatus getComplianceStatus();
    String getComplianceErrorTitle();
    String getComplianceErrorMessage();
}
```

A `getComplianceStatus()` metódus a megfelelőség szervizelési kísérlet eredményét adja vissza az értéket a `MAMCAComplianceStatus` enum.

|Állapotkód | Magyarázat |
| -- | -- |
| ISMERETLEN | A állapota ismeretlen. Ennek oka lehet egy nem várt hiba oka. További információk a céges portál naplói is található. |
| MEGFELELŐ | Megfelelőség szervizelési sikeres volt, és az alkalmazás most már nem felelnek meg a házirend. Az ADAL token beszerzéséhez újra meg kell próbálni. |
| NOT_COMPLIANT | Megfelelőség javítása nem sikerült.  Az alkalmazás nem megfelelő, és ADAL token beszerzéséhez kell nem kísérli meg újra a hibajelzést kiváltó körülmény kijavításáig.  További információ a hibáról a MAMComplianceNotification e küldi el. |
| SERVICE_FAILURE | Hiba történt az Intune szolgáltatástól megfelelőségi adatok beolvasására tett kísérlet során. További információk a céges portál naplói is található. |
| NETWORK_FAILURE | Az Intune szolgáltatáshoz való kapcsolódás során fellépő hiba történt. Az alkalmazás érdemes megpróbálni a token beszerzéséhez újra, ha a hálózati kapcsolat helyreáll. |
| CLIENT_ERROR | Megfelelőség javítása nem sikerült az ügyfél kapcsolatos valamilyen okból.  Ha például nem token vagy nem megfelelő felhasználó. További információ a hibáról a MAMComplianceNotification e küldi el. |
| PENDING | Megfelelőség javítása nem sikerült, mert a állapotválasz kellett még nem érkezett a szolgáltatástól, ha az időkorlát túl lett lépve. Az alkalmazás próbálkozzon újra később a token beszerzéséhez. |
| COMPANY_PORTAL_REQUIRED | Ahhoz, hogy a megfelelőség szervizelési sikeres végrehajtásához az eszközön a céges portál kell telepíteni.  Ha a céges portál már telepítve van az eszközön, az alkalmazásnak újra kell indítani.  Ebben az esetben egy párbeszédpanel jelenik meg a felhasználót arra kéri, indítsa újra az alkalmazást. |

Ha a megfelelőségi állapot `MAMCAComplianceStatus.COMPLIANT`, az alkalmazás kell indítsa el újra az eredeti token beszerzéséhez (a saját erőforrás). Ha a megfelelőség szervizelési kísérlet sikertelen volt a `getComplianceErrorTitle()` és `getComplianceErrorMessage()` módszerek honosított karakterlánc, amelyet az alkalmazás tudja megjeleníteni a végfelhasználók számára, ha úgy dönt, akkor adja vissza.  A következő többi hibaeseteket többsége nem az alkalmazás által remediable, így az általános esetben lehet érdemes választani, fiók létrehozása vagy a bejelentkezés sikertelen, és engedélyezi a felhasználó számára. Próbálkozzon újra később.  Állandó hiba esetén a MAM-naplók segíthetnek a hiba okának megállapításához.  A végfelhasználó is elküldhetik a naplókban található utasításokat használatával [Itt](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android "e-mailt a cég informatikai támogatási naplók").

Mivel `MAMComplianceNotification` kibővíti `MAMUserNotification`, a felhasználó, akinek a szervizelés végrehajtására történt kísérlet akkor is elérhető.

Íme egy példa egy névtelen osztállyal a MAMNotificationReceiver felület megvalósítása fogadó regisztrálása:

```java
final MAMNotificationReceiverRegistry notificationRegistry = MAMComponents.get(MAMNotificationReceiverRegistry.class);
// create a receiver
final MAMNotificationReceiver receiver = new MAMNotificationReceiver() {
    public boolean onReceive(MAMNotification notification) {
        if (notification.getType() == MAMNotificationType.COMPLIANCE_STATUS) {
            MAMComplianceNotification complianceNotification = (MAMComplianceNotification) notification;
            
            // take appropriate action based on complianceNotification.getComplianceStatus()
            
            // unregister this receiver if no longer needed
            notificationRegistry.unregisterReceiver(this, MAMNotificationType.COMPLIANCE_STATUS);
        }
        return true;
    }
};
// register the receiver
notificationRegistry.registerReceiver(receiver, MAMNotificationType.COMPLIANCE_STATUS);
```

> [!NOTE]
> Hívása előtt regisztrálni kell az értesítést fogadó `remediateCompliance()` eredményeként az értesítés kihagyott folyamatban van a versenyhelyzet elkerülése érdekében.

### <a name="implementation-notes"></a>Megvalósításhoz fűzött megjegyzések

> [!NOTE]
> Az alkalmazás `MAMServiceAuthenticationCallback.acquireToken()` metódus át kell adnia *igaz* az új `forceRefresh` jelzőt `acquireTokenSilentSync()` frissítésének kényszerítése a közvetítőtől.  Ez a tokeneket, amelyek hatással lehetnek a MAM-szolgáltatás jogkivonatok ADAL gyorsítótárazási problémája megkerüléséhez. Általában ez hasonlóan néz ki:
```java
AuthenticationResult result = acquireTokenSilentSync(resourceId, clientId, userId, /* forceRefresh */ true);
```

> [!NOTE]
> Ha szeretne egy egyéni blokkoló felhasználói felület megjelenítése a javítási kísérlet során, akkor kell átadnia *hamis* showUX paraméter `remediateCompliance()`. Győződjön meg arról, hogy a felhasználói felület megjelenítése, és az értesítési figyelő hívása előtt először regisztráljon `remediateCompliance()`.  Ez megakadályozza, hogy ha az értesítés sikerült nem észlelnének. Ha versenyhelyzet `remediateCompliance()` nagyon gyorsan meghiúsul.  Ha például a `onCreate()` vagy `onMAMCreate()` egy tevékenység alosztályát módszer az értesítési figyelő regisztrálja, és ezután hívja meg az ideális hely `remediateCompliance()`.  A paraméterek `remediateCompliance()` , szándék kiegészítő funkciók a UX adható át.  A megfelelőségi állapot értesítés fogadásakor az eredmény megjelenítéséhez, vagy egyszerűen csak az a tevékenység befejezése.

> [!NOTE]
> `remediateCompliance()` regisztrálja a fiókot és próbálja meg a regisztrációt.  A fő token igényelve, miután hívása `registerAccountForMAM()` már nem szükséges, azonban nem árt, ennek során. Másrészről, ha az alkalmazás nem tudja beszerezni a jogkivonatot és távolítsa el a felhasználói fiókot kívánja, akkor kell meghívnia `unregisterAccountForMAM()` távolítsa el a fiókot, és megakadályozza a háttérben futó beléptetési újrapróbálkozásokhoz.

## <a name="protecting-backup-data"></a>Biztonságimásolat-adatok védelme

Az Android Marshmallow (API 23) esetében az Android két módszert kínál az alkalmazásoknak az adataik biztonsági mentéséhez. Mindegyik lehetőség elérhető az alkalmazás számára, de különböző lépések végrehajtását igényli az Intune-adatvédelem megfelelő megvalósításához. Az alábbi táblázatban áttekintheti a megfelelő adatvédelmi működéshez szükséges műveleteket.  A biztonsági mentési módszerek részletes ismertetését az [Android API útmutatójában](https://developer.android.com/guide/topics/data/backup.html) olvashatja el.

### <a name="auto-backup-for-apps"></a>Alkalmazások automatikus biztonsági mentése

Az Android az Android Marshmallow rendszerű eszközökre telepített alkalmazásokhoz kezdte el kínálni a Google Drive-ra történő [automatikus teljes biztonsági mentést](https://developer.android.com/guide/topics/data/autobackup.html), függetlenül az alkalmazások cél API-jától. Ha az AndroidManifest.xml fájlban explicit módon **false** értékűre állítja az `android:allowBackup` attribútumot, akkor az alkalmazás soha nem kerül az Android által végrehajtott biztonsági mentések várólistájára, és a „vállalati” adatok megmaradnak az alkalmazásban. Ebben az esetben nincs további teendő.

Alapértelmezés szerint azonban az `android:allowBackup` attribútum true értékű még akkor is, ha az `android:allowBackup` nincs megadva a jegyzékfájlban. Ez azt jelenti, hogy az alkalmazások összes adatáról automatikus biztonsági másolat készül a felhasználó Google Drive-fiókjába, és ez olyan alapértelmezett működés, amely **adatszivárgási kockázatot** vet fel. Ezért az SDK az alább leírt módosításokat követeli meg az adatvédelem alkalmazásának biztosításához.  Fontos követnie az alábbi az irányelveket az ügyféladatok megfelelő védelme érdekében, ha az alkalmazást Android Marshmallow rendszerű eszközökön szeretné futtatni.  

Az Intune lehetővé teszi az Android összes elérhető [automatikus biztonsági mentési funkciójának](https://developer.android.com/guide/topics/data/autobackup.html) használatát, beleértve az egyéni szabályok definiálását XML-ben, de az adatok védelme érdekében követnie kell az alábbi lépéseket:

1. Ha az alkalmazás **nem** saját BackupAgentet használ, az alapértelmezett MAMBackupAgent használatával engedélyezheti az Intune szabályzatainak megfelelő automatikus teljes biztonsági mentéseket. Helyezze el az alábbi kódrészletet az alkalmazás jegyzékfájljában:

    ```xml
    android:fullBackupOnly="true"
    android:backupAgent="com.microsoft.intune.mam.client.app.backup.MAMDefaultBackupAgent"
    ```


2. **[nem kötelező]** Amennyiben saját BackupAgent implementálása mellett döntött, mindenképpen a MAMBackupAgent vagy a MAMBackupAgentHelper osztályt kell használnia. Lásd a következő szakaszokat. Fontolja meg az áttérést az Intune (az 1. lépésben ismertetett) **MAMDefaultFullBackupAgent** osztályának használatára, amely egyszerű biztonsági mentést tesz lehetővé Android M-en és újabb rendszereken.

3. Amikor eldönti, hogy az alkalmazásról milyen típusú teljes biztonsági mentés készüljön (szűretlen, szűrt, semmilyen), az `android:fullBackupContent` attribútumot be kell állítania igaz vagy hamis értékűre vagy egy XML-erőforrásra az alkalmazásban.

4. Minden, az `android:fullBackupContent` attribútumban elhelyezett adatot _**kötelező**_ egy `com.microsoft.intune.mam.FullBackupContent` nevű metaadatcímkébe másolni.

    **1. példa**: Ha azt szeretné, hogy az alkalmazás teljes biztonsági másolatok kizárások nélkül, állítsa mind a `android:fullBackupContent` attribútum és `com.microsoft.intune.mam.FullBackupContent` metaadatcímkét **igaz**:

    ```xml
    android:fullBackupContent="true"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />  
    ```

    **2. példa**: Ha azt szeretné, hogy az alkalmazás saját egyéni Backupagentjét használja, és lemond az teljes, az Intune szabályzat megfelelő, automatikus biztonsági mentés, először be kell állítania az attribútumot és a metaadatcímkét címke **hamis**:

    ```xml
    android:fullBackupContent="false"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="false" />  
    ```

    **3. példa**: Ha azt szeretné, hogy az alkalmazás XML-fájlban definiált egyéni szabályoknak megfelelően teljes biztonsági másolatok, ugyanarra az XML-erőforrásra állítsa be az attribútumot és a metaadatcímkét címkét:

    ```xml
    android:fullBackupContent="@xml/my_scheme"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />  
    ```


### <a name="keyvalue-backup"></a>Kulcs/érték biztonsági mentés

A [Key/Value Backup](https://developer.android.com/guide/topics/data/keyvaluebackup.html) (Kulcs/érték biztonsági mentés) lehetőség minden 8-as vagy újabb verziójú API számára elérhető, és az [Android Backup Service](https://developer.android.com/google/backup/index.html) szolgáltatásba tölti fel az adatokat, felhasználónként legfeljebb 5 MB-nyit. A Key/Value Backup használata esetén **BackupAgentHelper** vagy **BackupAgent** osztályt kell használni.

### <a name="backupagenthelper"></a>BackupAgentHelper

A BackupAgentHelper osztályt mind a natív androidos funkciókat, mind az Intune MAM-integrációt tekintve jóval egyszerűbb implementálni, mint a BackupAgentet. A BackupAgentHelper lehetővé teszi, hogy a fejlesztő teljes fájlokat és közös beállításokat regisztráljon rendre egy **FileBackupHelper** és egy **SharedPreferencesBackupHelper** osztályban, amelyek ezután létrehozáskor hozzáadódnak a BackupAgentHelper osztályhoz. Az alábbi lépéseket követve használhat BackupAgentHelper osztályt az Intune MAM-szolgáltatással:

1. Ha többidentitásos biztonsági mentést szeretne használni a BackupAgentHelper osztállyal, kövesse az [Extending BackupAgentHelper](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgentHelper) (A BackupAgentHelper kiterjesztése) című angol nyelvű Android-útmutatót.

2. Osztályával terjessze ki a BackupAgentHelper, a FileBackupHelper és a SharedPreferencesBackupHelper osztályok MAM-os megfelelőjét.

|Androidos osztály | MAM-os megfelelő |
|--|--|
|BackupAgentHelper |MAMBackupAgentHelper |
|FileBackupHelper | MAMFileBackupHelper
|SharedPreferencesBackupHelper| MAMSharedPreferencesBackupHelper|

Ezen irányelvek betartása elősegíti a sikeres, többidentitásos biztonsági mentést és visszaállítást.

### <a name="backupagent"></a>BackupAgent

A BackupAgent segítségével sokkal egyértelműbben adható meg, hogy mely adatokról készüljön biztonsági mentés. Mivel az implementálás nagyrészt a fejlesztő felelőssége, több lépésre van szükség az Intune megfelelő adatvédelmének biztosításához. Azáltal, hogy a munka nagyobb része a fejlesztőre hárul, az Intune-integráció itt valamivel több jelentőséggel bír.

**MAM-integráció:**

1. Gondosan tanulmányozza át a [Key/Value Backup](https://developer.android.com/guide/topics/data/keyvaluebackup.html) (Kulcs/érték biztonsági mentés) és főleg az [Extending BackupAgent](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent) (A BackupAgent kiterjesztése) című Android-útmutatókat annak érdekében, hogy a BackupAgent-implementáció biztosan megfeleljen az androidos irányelveknek.

2. Osztályával terjessze ki a `MAMBackupAgent` osztályt.

**Többidentitásos biztonsági mentés:**

1. A biztonsági mentés megkezdése előtt ellenőrizze, hogy **a rendszergazda valóban engedélyezte-e** a szóban forgó fájlok vagy adatpufferek biztonsági mentését többidentitásos környezetben. Erre a célra szolgál a `MAMFileProtectionManager` és `MAMDataProtectionManager` osztályokban szereplő `isBackupAllowed` függvény. Ha valamely fájl vagy adatpuffer biztonsági mentése nem engedélyezett, azt ne vonja be a biztonsági mentésbe.

2. Ha a biztonsági mentés egy pontján biztonsági másolatot szeretne készíteni az 1. lépésben ellenőrzött fájlokhoz tartozó identitásokról, a `backupMAMFileIdentity(BackupDataOutput data, File … files)` függvényt kell meghívnia azokkal a fájlokkal, amelyekből adatokat szeretne kinyerni. Ez a művelet automatikusan új biztonsági mentési entitásokat hoz létre, és a `BackupDataOutput` kimenetre írja azokat. Ezeket az entitásokat automatikusan felhasználja a program a visszaállítás során.

**Többidentitásos visszaállítás:**

Az adatok biztonsági mentésével kapcsolatos Android-útmutatóban meg van adva egy általános algoritmus az alkalmazásadatok visszaállításához, az [Extending BackupAgent](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent) (A BackupAgent kiterjesztése) című szakaszban pedig kódminta is található. A sikeres, többidentitásos visszaállítás érdekében kötelező a kódmintában megadott általános struktúrát követni, különös tekintettel az alábbiakra:

1. A biztonsági mentési entitásokon egy `while(data.readNextHeader())`* ciklussal kell végighaladni.

2. Ha a `data.getKey()`* nem egyezik meg az `onBackup`-ba írt kulccsal, akkor meg kell hívni a `data.skipEntityData()`* függvényt. Enélkül előfordulhat, hogy a visszaállítások nem járnak sikerrel.

3. Kerülje a visszatérést a biztonsági mentési entitások `while(data.readNextHeader())`* szerkezetben való feldolgozása során, mert elveszhetnek az automatikusan kiírt entitások.

* A `data` helyére az alkalmazásnak a visszaállításkor átadott **MAMBackupDataInput** helyi változónevét kell behelyettesíteni.

## <a name="multi-identity-optional"></a>Több identitás használata (nem kötelező)

### <a name="overview"></a>Áttekintés
Az Intune App SDK alapértelmezés szerint az alkalmazás egészére alkalmazza a szabályzatot. A többszörös identitás az Intune-alkalmazásvédelem választható funkciója, amelynek engedélyezése esetén a szabályzatok identitásonként alkalmazhatók. Ez a többi alkalmazásvédelmi funkciónál jelentősen nagyobb mértékű közreműködést igényel az alkalmazástól.

> [!NOTE]
> Az alkalmazás megfelelő közreműködésének elmulasztása adatszivárgásokat és egyéb biztonsági problémákat okozhat.

Ha a felhasználó már beléptette az eszközt vagy az alkalmazást, az SDK regisztrálja ezt az identitást, és ezt tekinti az Intune-ban felügyelt elsődleges identitásnak. Az alkalmazás többi felhasználójával nem felügyeltként bánik, szabályzatbeállításaik korlátlanok.

> [!NOTE]
> Jelenleg eszközönként csak egy Intune által felügyelt identitás támogatott.

Az identitás sztringként van definiálva. Az identitásokban **nem számítanak különbözőnek a kis- és a nagybetűk**, és az SDK nem feltétlen olyan kis- és nagybetűkkel adja vissza a tőle kért identitásokat, mint ahogyan az az identitás beállításakor eredetileg meg volt adva.

Az alkalmazásnak tájékoztatnia *kell* az SDK-t, ha módosítani kívánja az aktív identitást. Egyes esetekben az SDK is értesíti az alkalmazást, ha identitásváltás szükséges. A legtöbb esetben azonban MAM nem ismeri a felhasználói felületen éppen megjelenített, vagy egy adott időben egy szálon használt adatokat, és az alkalmazásra hagyatkozik a helyes identitás beállításához az adatvesztés elkerülése érdekében. A következő szakaszokban néhány, az alkalmazás műveletét igénylő helyzetet tüntetünk fel.

### <a name="enabling-multi-identity"></a>Több identitás használatának engedélyezése

Alapértelmezés szerint az összes alkalmazás egyszeres identitással rendelkező alkalmazásnak minősül. Az AndroidManifest.xml-ben elhelyezett alábbi metaadatokkal lehet jelezni, hogy egy alkalmazás képes több identitás kezelésére.

```xml
  <meta-data
    android:name="com.microsoft.intune.mam.MAMMultiIdentity"
    android:value="true" />
```

### <a name="setting-the-identity"></a>Az identitás beállítása

A fejlesztők (csökkenő prioritási sorrendben) a következő szinteken állíthatják be az alkalmazás identitását:

  1. Szál szintje
  2. `Context` (általában `Activity`) szint
  3. Folyamat szintje

A szál szintjén beállított identitás felülírja a Context szintjén beállított identitást, és a `Context` szinten beállított identitás felülírja a folyamat szintjén beállított identitást. Szintjén beállított identitást egy `Context` csak a megfelelő társított esetekben használatos. A fájlok I/O műveleteihez például nem tartozik `Context`. Leggyakrabban az alkalmazások állítják a `Context` az identitás- `Activity`. Egy alkalmazás *kell* nem jelennek meg adatok egy felügyelt identitás, kivéve, ha a `Activity` ugyanazon identitásra van beállítva. A folyamatszintű identitás általában csak akkor hasznos, ha az alkalmazás egyszerre csak egy-egy felhasználóval működik az összes szálon. Számos alkalmazásnak nem feltétlenül kell igénybe vennie.

Ha az alkalmazás használja a `Application` rendszerszolgáltatások beszerezni, győződjön meg arról, hogy a szálak és a folyamat identitása van beállítva, illetve, hogy a felhasználói felület identitása állította be az alkalmazás helyi `Application` környezetben.

Az esetek kezelése, amikor frissíti a felhasználói felület identitását a `setUIPolicyIdentity` vagy `switchMAMIdentity`, mindkét módszert is át lehet adni egy `IdentitySwitchOption` értékeket.

* `IGNORE_INTENT`: Akkor használja, ha Identitásváltás figyelmen kívül hagyja a célt, az aktuális tevékenység társított kér.
  Példa:

  1. Az alkalmazás megjelölésű fogad egy felügyelt identitás tartalmazó felügyelt dokumentum, és az alkalmazás megjelenik a dokumentumot.
  2. A felhasználó a személyes identitásával vált, így az alkalmazás kéri a felhasználói felület identitásváltást. A személyes identitásával a az alkalmazás már nem jeleníti meg a dokumentumot, így `IGNORE_INTENT` az Identitásváltás kérésekor.

  Ha nincs beállítva, az SDK feltételezi, hogy a legújabb leképezés továbbra is használatban van az alkalmazás. Ennek következtében az identitás a leképezés gyökérkönyvtárral beérkező adatokat, és az identitása házirendet kap.

>[!NOTE]
> Mivel a `CLIPBOARD_SERVICE` használható felhasználói felületi műveletekre, az SDK-t használja a felhasználói felület identitását az előtérben futó tevékenység a `ClipboardManager` műveleteket.
> A `MAMPolicyManager` következő metódusaival lehet beállítani az identitást, illetve beolvasni a korábban beállított identitásértékeket.

```java
  public static void setUIPolicyIdentity(final Context context, final String identity, final MAMSetUIIdentityCallback mamSetUIIdentityCallback);

  public static String getUIPolicyIdentity(final Context context);

  public static MAMIdentitySwitchResult setProcessIdentity(final String identity);

  public static String getProcessIdentity();

  public static MAMIdentitySwitchResult setCurrentThreadIdentity(final String identity);

  public static String getCurrentThreadIdentity();

/**
   * Get the current app policy. This does NOT take the UI (Context) identity into account.
   * If the current operation has any context (e.g. an Activity) associated with it, use the overload below.
   */
  public static AppPolicy getPolicy();

  /**
  * Get the current app policy. This DOES take the UI (Context) identity into account.
   * If the current operation has any context (e.g. an Activity) associated with it, use this function.
   */
  public static AppPolicy getPolicy(final Context context);


  public static AppPolicy getPolicyForIdentity(final String identity);

  public static boolean getIsIdentityManaged(final String identity);
  ```

>[!NOTE]
> Az alkalmazás identitását null értékre állítva törölheti.
>
> Az üres sztring használható olyan identitásként, amelyre biztosan nem vonatkozik alkalmazásvédelmi szabályzat.

#### <a name="results"></a>Eredmény
Az identitást beállító összes metódus a `MAMIdentitySwitchResult` objektummal adja vissza az eredményértékeket. Négy visszaadható érték van:

| Visszatérési érték | Forgatókönyv |
|--|--|
| SUCCEEDED | Az identitásváltás sikeres volt. |
| NOT_ALLOWED  | Az identitásváltás nem engedélyezett. Ez akkor fordul elő, ha valaki a Felhasználói felület (Környezet) identitást próbálja beállítani, amikor egy másik identitás van beállítva az aktuális szálhoz. |
| CANCELLED | A felhasználó megszakította az identitásváltást. Ez általában úgy történik, hogy megnyomja a Vissza gombot egy PIN-kódot kérő vagy hitelesítési üzenetnél. |
| FAILED | Az identitásváltás ismeretlen okból nem sikerült.|

Az alkalmazás biztosítania kell, hogy az Identitásváltás sikeres megjelenítése vagy a céges adatok használata előtt. Jelenleg a folyamat- és a szálidentitás-váltások mindig sikeresek lesznek a több identitást támogató alkalmazások esetén, azonban fenntartjuk a jogot hibafeltételek hozzáadására. A felhasználói felület identitásváltása sikertelen lehet érvénytelen argumentumok esetén, ha az ütközne a szálidentitással, vagy ha a felhasználó a feltételes indítási követelményeit megszakítja (pl. a Vissza gombra kattint a PIN-kód képernyőn).


Környezet identitás beállítása esetén az eredmény aszinkron módon jelenik meg. Ha a Környezet egy tevékenység, akkor az SDK mindaddig nem tudja, hogy sikeres volt-e az identitásváltás, amíg feltételes indítás történik – itt ugyanis a felhasználónak meg kell adnia a PIN-kódját vagy vállalati hitelesítő adatait. Az alkalmazásnak az elvárások szerint egy `MAMSetUIIdentityCallback` interfészt implementálva kell fogadnia ezt az eredményt, bár ennél a paraméternél a null érték átadása is megengedett.

```java
    public interface MAMSetUIIdentityCallback {
        void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult);
  }
```

A tevékenységek identitását közvetlenül a `MAMActivity` egy metódusával, a `MAMPolicyManager.setUIPolicyIdentity` meghívása nélkül is beállíthatja. A metódus az alábbi:

```java
     public final void switchMAMIdentity(final String newIdentity, final EnumSet<IdentitySwitchOption> options);
```

Az `MAMActivity` osztály metódusát felül is lehet bírálni, ha azt szeretné, hogy az alkalmazás értesítést kapjon a tevékenység identitásának módosítására tett kísérletek eredményéről.

``` java
    public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);
```

Ha nem bírálja felül `onSwitchMAMIdentityComplete` (hívja fel a `super` metódus), a sikertelen Identitásváltás tevékenységet a folyamatban, befejezett tevékenység eredményez. Ha a metódus bírálja felül, akkor ügyelnie kell arra, hogy a céges adatok nem jelenik meg a sikertelen Identitásváltás után.

>[!NOTE]
> Előfordulhat, hogy az identitásváltás után újból létre kell hozni a tevékenységet. Ebben az esetben a `onSwitchMAMIdentityComplete` visszahívása lesz elküldve a tevékenység új példányának.


### <a name="implicit-identity-changes"></a>Az identitás implicit megváltoztatása

Az alkalmazás identitásbeállítási képessége mellett a szálak és a környezetek identitása megváltoztatható a más, alkalmazásvédelmi szabályzattal ellátott Intune által kezelt alkalmazásból beérkező adatok alapján is.

#### <a name="examples"></a>Példák

  1. Ha például egy tevékenység egy másik MAM-alkalmazás által küldött `Intent` alapján indul el, akkor a tevékenység identitása a másik alkalmazásban az `Intent` elküldésekor érvényes identitás alapján lesz beállítva.

  2. A szolgáltatások esetében a szál identitása hasonlóan lesz beállítva az `onStart`- vagy az `onBind`-hívások időtartamára. Átmenetileg a `Binder`-be érkező, az `onBind` által visszaadott hívások is beállítják a szál identitását.

  3. A beérkező hívások a `ContentProvider` esetében is hasonlóképpen beállítják a szál identitását az időtartamukra vonatkozóan.


  Ezenkívül a tevékenységekkel kapcsolatos felhasználói beavatkozások is előidézhetnek implicit identitásváltást.

  **Példa:** A felhasználó megszakítja az engedélyezési kérést során `Resume` üres identitásra való implicit váltást eredményez.

  Lehetőség van arra, hogy az alkalmazás értesüljön ezekről a váltásokról, és szükség esetén megtiltsa őket. A `MAMService` és a `MAMContentProvider` a következő, az alosztályok által felülbírálható metódust teszi elérhetővé:

  ```java
  public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchResultCallback callback);
  ```

  A `MAMActivity` osztályban a metódusnak még egy paramétere van:

  ```java
  public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchReason reason,
    final AppIdentitySwitchResultCallback callback);
  ```

  * Az `AppIdentitySwitchReason` rögzíti az implicit váltás forrását, és a következő értékeket tudja fogadni: `CREATE`, `RESUME_CANCELLED` és `NEW_INTENT`.  A `RESUME_CANCELLED` ok akkor használható, amikor a tevékenység folytatása PIN-kódot kérő, hitelesítési vagy egyéb megfelelőségi felhasználói felület megjelenítését idézi elő, és a felhasználó megpróbál kilépni erről a felhasználói felületről, általában a Vissza gomb használatával.


  * Az `AppIdentitySwitchResultCallback` a következőképpen történik:

    ```java
    public interface AppIdentitySwitchResultCallback {
        /**
         * @param result
         *            whether the identity switch can proceed.
         */
        void reportIdentitySwitchResult(AppIdentitySwitchResult result);
    }
    ```

    Az ```AppIdentitySwitchResult``` értéke `SUCCESS` vagy `FAILURE`.

Az `onMAMIdentitySwitchRequired` metódus hívandó az összes implicit identitásváltás esetében, kivéve azokat, amelyek a `MAMService.onMAMBind` által visszaadott Binderen keresztül történtek. Az `onMAMIdentitySwitchRequired` alapértelmezett implementációi a következő metódusokat hívják meg azonnal:

* `reportIdentitySwitchResult(FAILURE)` Ha a hiba oka `RESUME_CANCELLED`.

* `reportIdentitySwitchResult(SUCCESS)` – minden más esetben.

  Nem valószínű, hogy az alkalmazások többségének másképpen kell blokkolnia vagy késleltetnie az identitásváltást, de ha mégis erre van szükség, akkor a következő szempontokat kell figyelembe venni:

  * Az identitásváltás blokkolásakor az eredmény ugyanaz lesz, mint amikor a `Receive` megosztási beállítások tiltják le az adatok beérkezését.

  * Ha egy szolgáltatás a főszálon fut, a `reportIdentitySwitchResult` hívását **kötelező** szinkron módon végrehajtani, ellenkező esetben a felhasználói felület szála leáll.

  * A **`Activity`** létrehozását, `onMAMIdentitySwitchRequired` hívása előtt `onMAMCreate`. Ha az alkalmazásnak felhasználói felületet kell megjelenítenie annak megállapításához, hogy engedélyezhető-e az identitásváltás, akkor az adott felhasználói felületet *egy másik* tevékenységgel kell megjeleníteni.

  * Az egy **`Activity`** , ha az üres identitásra való váltás kérése történik a, `RESUME_CANCELLED`, az alkalmazásnak módosítania kell a folytatott tevékenységet, hogy az adatmegjelenítés az adott identitásváltásnak.  Ha ez nem lehetséges, az alkalmazásnak el kell utasítania a váltást, és újból kérnie kell a felhasználót a folytatáshoz használt identitás szabályzatának teljesítésére (például a PIN-kód megadását kérő képernyőt megjelenítve).

    > [!NOTE]
    > A többszörös identitást támogató alkalmazások mindig fogadják a felügyelt és a nem felügyelt alkalmazásoktól érkező adatokat. Az alkalmazás feladata, hogy felügyelt módon kezelje a felügyelt identitásokból érkező adatokat.

  Ha a kért identitás felügyelt (ezt a `MAMPolicyManager.getIsIdentityManaged` metódussal lehet ellenőrizni), de az alkalmazás nem tudja használni a fiókot (például mert a fiókokat, így az e-mail-fiókokat először be kell állítani az alkalmazásban), akkor el kell utasítania az identitásváltást.

#### <a name="build-plugin--tool-considerations"></a>A build beépülő modullal/-eszközzel kapcsolatos szempontok
Ha Ön nem explicit módon öröklik `MAMActivity`, `MAMService`, vagy `MAMContentProvider` (mivel engedélyezi a build azokat az eszközöket, győződjön meg arról, hogy a módosítás), azonban továbbra is szeretné feldolgozni váltások, előfordulhat, hogy inkább megvalósítása `MAMActivityIdentityRequirementListener` (az egy `Activity`) vagy `MAMIdentityRequirementListener` (az egy `Service` vagy `ContentProviders`).
A `MAMActivity.onMAMIdentitySwitchRequired` alapértelmezett viselkedése a `MAMActivity.defaultOnMAMIdentitySwitchRequired(activity, identity,
reason, callback)` statikus metódus meghívásával érhető el.

Ehhez hasonlóan, ha felül kell bírálnia a `MAMActivity.onSwitchMAMIdentityComplete` osztályt, akkor implementálhatja a `MAMActivityIdentitySwitchListener` osztályt anélkül, hogy explicit módon örökölné a `MAMActivity` osztálytól.

### <a name="preserving-identity-in-async-operations"></a>Identitás megőrzése aszinkron műveleteknél
Gyakran előfordul a felhasználói felület szálán végrehajtott műveleteknél, hogy más szálaknak adnak át háttérfeladatokat. A többszörös identitást támogató alkalmazásoknak biztosítaniuk kell, hogy ezek a háttérfeladatok a megfelelő identitással fussanak, mely gyakran megegyezik az átadást végző tevékenység identitásával. A MAM SDK a `MAMAsyncTask` és a `MAMIdentityExecutors` osztály biztosításával nyújt segítséget az identitás megőrzéséhez.
Ezek kell használni, ha az aszinkron művelet sikerült írni a vállalati adatokat egy fájlba, vagy más alkalmazások kommunikál.

#### <a name="mamasynctask"></a>MAMAsyncTask

Használandó `MAMAsyncTask`, egyszerűen ebből az helyett `AsyncTask` cserélje le a beállítás felülbírálja a `doInBackground` és `onPreExecute` a `doInBackgroundMAM` és `onPreExecuteMAM` jelölik. A `MAMAsyncTask` konstruktorának paramétereként meg kell adnia a tevékenység kontextusát. Példa:

```java
  AsyncTask<Object, Object, Object> task = new MAMAsyncTask<Object, Object, Object>(thisActivity) {

    @Override
    protected Object doInBackgroundMAM(final Object[] params) {
        // Do operations.
    }

    @Override
    protected void onPreExecuteMAM() {
        // Do setup.
    };
```

### <a name="mamidentityexecutors"></a>MAMIdentityExecutors
A `MAMIdentityExecutors` osztály segítségével az `Executor`- és `ExecutorService`-példányokat identitást megőrző `Executor`/`ExecutorService` osztályba burkolhatja a `wrapExecutor` és a `wrapExecutorService` metódus használatával. Példa:

```java
  Executor wrappedExecutor = MAMIdentityExecutors.wrapExecutor(originalExecutor, activity);
  ExecutorService wrappedService = MAMIdentityExecutors.wrapExecutorService(originalExecutorService, activity);
```
### <a name="file-protection"></a>Fájlvédelem

Amikor létrehozza a fájlokat, a rendszer identitást társít hozzájuk a szál és a folyamat identitása alapján. Ez az identitás lesz használva a fájltitkosításhoz és a szelektív törléshez is. Csak azok a fájlok lesznek titkosítva, amelyek identitása felügyelt, és szabályzata előírja a titkosítást. Az SDK alapértelmezett szelektív törlése csak azokat a felügyelt identitáshoz tartozó fájlokat fogja törölni, amelyekre törlést kértek. Az alkalmazás a `MAMFileProtectionManager` osztállyal kérdezheti le vagy módosíthatja a fájlok identitását.

```java
public final class MAMFileProtectionManager {

   /**
    * Protect a file or directory. This will synchronously trigger whatever protection is required for the file, and will tag the
    * file for future protection changes. If an identity is set on a directory, it is set recursively on all files and
    * subdirectories. New files or directories will inherit their parent directory's identity. If MAM is operating in offline mode,
    * this method will silently do nothing.
    *
    * @param identity
    *        Identity to set.
    * @param file
    *        File to protect.
    *
    * @throws IOException
    *         If the file cannot be protected.
    */
   public static void protect(final File file, final String identity) throws IOException;

   /**
     * Protect a file obtained from a content provider. This is intended to be used for
     * sdcard (whether internal or removable) files accessed through the Storage Access Framework.
     * It may also be used with descriptors referring to private files owned by this app.
     * It is not intended to be used for files owned by other apps and such usage will fail. If
     * creating a new file via a content provider exposed by another MAM-integrated app, the new
     * file identity will automatically be set correctly if the ContentResolver in use was
     * obtained via a Context with an identity or if the thread identity is set.
     *
     * This will synchronously trigger whatever protection is required for the file, and will tag
     * the file for future protection changes. If an identity is set on a directory, it is set
     * recursively on all files and subdirectories. If MAM is operating in offline mode, this
     * method will silently do nothing.
     *
     * @param identity
     *            Identity to set.
     * @param file
     *            File to protect.
     *
     * @throws IOException
     *             If the file cannot be protected.
     */
    public static void protect(final ParcelFileDescriptor file, final String identity) throws IOException;

   /**
    * Get the protection info on a file.
    *
    * @param file
    *            File or directory to get information on.
    * @return File protection info, or null if there is no protection info.
    * @throws IOException
    *             If the file cannot be read or opened.
    */
    public static MAMFileProtectionInfo getProtectionInfo(final File file) throws IOException;

   /**
    * Get the protection info on a file.
    *
    * @param file
    *            File or directory to get information on.
    * @return File protection info, or null if there is no protection info.
    * @throws IOException
    *             If the file cannot be read or opened.
    */
    public static MAMFileProtectionInfo getProtectionInfo(final ParcelFileDescriptor file) throws IOException;

}

public interface MAMFileProtectionInfo {
    String getIdentity();
}
 ```

#### <a name="app-responsibility"></a>Alkalmazás feladatköre
A MAM nem következtethet automatikusan kapcsolatra a beolvasott fájlok és egy `Activity` által megjelenített adatok között. Az alkalmazásoknak a vállalati adatok megjelenítése előtt be *kell* állítaniuk a megfelelő felhasználóifelület-identitást. Ez érvényes a fájlokból beolvasott adatokra is. Az alkalmazáson kívüli forrásból (ami lehet egy `ContentProvider` vagy egy nyilvánosan írható hely) származó fájlok esetén az alkalmazásnak meg *kell* kísérelnie a fájl identitásának megállapítását (a `MAMFileProtectionManager.getProtectionInfo` használatával), mielőtt megjelenítené a fájlból beolvasott információt. Ha a `getProtectionInfo` nem null, nem üres identitást jelez, a felhasználói felület identitását azzal egyezőre *kell* beállítani (a `MAMActivity.switchMAMIdentity` vagy a `MAMPolicyManager.setUIPolicyIdentity` használatával). Ha az identitásváltás nem sikerül, a fájl adatait *nem szabad* megjeleníteni.

A folyamat lehet például a következőhöz hasonló:
  * Felhasználó kiválasztja az alkalmazásban megnyitandó dokumentumot.
  * A megnyitási folyamat során az adatok a lemezről való beolvasása előtt az alkalmazás ellenőrzi a tartalom megjelenítésére használandó identitást.
    * MAMFileProtectionInfo info = MAMFileProtectionManager.getProtectionInfo(docPath)
    * if(info)   MAMPolicyManager.setUIPolicyIdentity(activity, info.getIdentity(), callback)
    * Az alkalmazás megvárja, amíg a visszahívás egy eredményt jelez.
    * Ha a jelentett eredmény hiba, az alkalmazás nem jeleníti meg a dokumentumot.
  * Az alkalmazás megnyílik, és rendereli a fájlt.
  
#### <a name="single-identity-to-multi-identity-transition"></a>A többszörös identitás váltania egyszeres identitással
Ha egy alkalmazást, amely korábban kiadott integrált egyszeres identitást Intune-nal később integrálható a többszörös identitás, a korábban telepített alkalmazások tapasztalható átmenet (a felhasználó számára nem látható, ott nem nincs társított UX). Az alkalmazás nincs *szükséges* explicit módon kezelje az átállás semmit. Az átállás továbbra is visszatérhetnek előtt létrehozott összes fájl Írországból induló szolgáltatásnak kezelt (tehát ezek titkosított marad, a titkosítási házirend esetén). Ha szükséges, a frissítés észleléséhez és használata `MAMFileProtectionManager.protect` címkézése meghatározott fájlokat és könyvtárakat az üres identitáshoz (ezzel a művelettel eltávolítja a titkosítást, ha azok titkosítva).

#### <a name="offline-scenarios"></a>Kapcsolat nélküli forgatókönyvek

A fájl identitásának címkézésénél az offline mód különbségnek számít. A következő szempontokat kell figyelembe venni:

  * Ha a Céges portál nincs telepítve, akkor a fájlok nem láthatók el identitáscímkével.

  * Ha a Céges portál telepítve van, de az alkalmazásra nem vonatkozik Intune MAM-szabályzat, akkor a fájlokat nem lehet megbízhatóan ellátni identitáscímkével.

  * Amikor elérhetővé válik a fájlok identitáscímkézése, akkor az összes korábban létrehozott fájl személyesként/nem felügyeltként (az üres karakterláncú identitáshoz tartozó fájlként) lesz kezelve, kivéve, ha az alkalmazás korábban egyidentitásos felügyelt alkalmazásként lett telepítve: ebben az esetben a fájlok a beléptetett felhasználóhoz tartozó fájlokként lesznek kezelve.

### <a name="directory-protection"></a>Könyvtárvédelem

A könyvtárakat is a fájlok védelmére szolgáló `protect` metódussal lehet védeni. A könyvtárvédelem rekurzívan érvényes a könyvtárban lévő összes fájlra és alkönyvtárra, illetve a benne létrehozott új fájlokra. Emiatt a nagy méretű könyvtárak esetében a `protect` hívás hosszabb ideig tarthat. Éppen ezért a sok fájlt tartalmazó könyvtárakra védelmet alkalmazó alkalmazásoknak érdemes a `protect` hívást aszinkron módon, háttérszálon futtatni.

### <a name="data-protection"></a>Adatvédelem

A fájlok nem címkézhetők meg több identitáshoz tartozó fájlként. Azok az alkalmazások, amelyeknek egy fájlban kell tárolniuk különböző felhasználók adatait, manuálisan tehetik meg ezt a `MAMDataProtectionManager` által biztosított szolgáltatásokkal. Ez lehetővé teszi az alkalmazás számára az adatok titkosítását és hozzákötését egy adott felhasználóhoz. A titkosított adatok lemezen, fájlban tárolhatók. Az identitáshoz tartozó adatokat lekérdezheti, és az adatokat visszafejtheti.

A `MAMDataProtectionManager` osztályt hasznosító alkalmazásoknak fogadót kell implementálniuk a `MANAGEMENT_REMOVED` értesítéshez. Az értesítés lefutása után az ezen osztállyal védett pufferek nem lesznek olvashatóak, ha a fájltitkosítást a pufferek védett állapotában kapcsolták be. Egy alkalmazás meghívásával javítani tudja ezt a helyzetet `MAMDataProtectionManager.unprotect` az összes pufferen az értesítés időtartama alatt. Az értesítés időtartama alatt a protect metódust is biztonságosan meg lehet hívni, ha az identitásadatokat meg szeretnék őrizni – a titkosítás ez idő alatt garantáltan le van tiltva.


```java

public final class MAMDataProtectionManager {
    /**
     * Protect a stream. This will return a stream containing the protected
     * input.
     *
     * @param identity
     *            Identity to set.
     * @param input
     *            Input data to protect, read sequentially. This function
     *            will change the position of the stream but may not have
     *            read the entire stream by the time it returns. The
     *            returned stream will wrap this one. Calls to read on the
     *            returned stream may cause further reads on the original
     *            input stream. Callers should not expect to read directly
     *            from the input stream after passing it to this method.
     *            Calling close on the returned stream will close this one.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be protected
     */
    public static InputStream protect(final InputStream input, final String identity);

    /**
     * Protect a byte array. This will return protected bytes.
     *
     * @param identity
     *            Identity to set.
     * @param input
     *            Input data to protect.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be protected
     */
    public static byte[] protect(final byte[] input, final String identity) throws IOException;

    /**
     * Unprotect a stream. This will return a stream containing the
     * unprotected input.
     *
     * @param input
     *            Input data to protect, read sequentially.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be unprotected
     */
    public static InputStream unprotect(final InputStream input) throws IOException;

    /**
     * Unprotect a byte array. This will return unprotected bytes.
     *
     * @param input
     *            Input data to protect.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be unprotected
     */
    public static byte[] unprotect(final byte[] input) throws IOException;

    /**
     * Get the protection info on a stream.
     *
     * @param input
     *            Input stream to get information on. Either this input
     *            stream must have been returned by a previous call to
     *            protect OR input.markSupported() must return true.
     *            Otherwise it will be impossible to get protection info
     *            without advancing the stream position. The stream must be
     *            positioned at the beginning of the protected data.
     * @return Data protection info, or null if there is no protection
     *            info.
     * @throws IOException
     *             If the input cannot be read.
     */
    public static MAMDataProtectionInfo getProtectionInfo(final InputStream input) throws IOException;

    /**
     * Get the protection info on a stream.
     *
     * @param input
     *            Input bytes to get information on. These must be bytes
     *            returned by a previous call to protect() or a copy of
     *            such bytes.
     * @return Data protection info, or null if there is no protection
     *            info.
     * @throws IOException
     *             If the input cannot be read.
     */
    public static MAMDataProtectionInfo getProtectionInfo(final byte[] input) throws IOException;
}
```

### <a name="content-providers"></a>Tartalomszolgáltatók

Ha az alkalmazás nem biztosít a vállalati adatokat egy `ParcelFileDescriptor` keresztül egy `ContentProvider`, az alkalmazás metódusát meghívva kell `isProvideContentAllowed(String)` a `MAMContentProvider`, átmenő identitás UPN (egyszerű felhasználónév), a tartalom. Ha ez a függvény hamis értéket ad vissza, akkor a tartalmat *nem szabad* visszaadnia a hívónak. A tartalomszolgáltatón keresztül visszaadott fájlleírók kezelése automatikusan a fájl identitása alapján történik.

Ha Ön nem öröklődnek `MAMContentProvider` explicit módon, és ehelyett lehetővé teszi a build azokat az eszközöket, győződjön meg arról, hogy a módosítás, előfordulhat, hogy egy statikus verziója ugyanezt a módszert hívja: `MAMContentProvider.isProvideContentAllowed(provider, contentIdentity)`.

### <a name="selective-wipe"></a>Szelektív törlés

Ha egy többidentitású alkalmazás regisztrál a `WIPE_USER_DATA` értesítésekre, akkor az alkalmazás felelőssége, hogy eltávolítsa a törölt felhasználóhoz tartozó összes adatot, ideértve az összes olyan fájlt is, amely meg lett jelölve az adott felhasználói identitáshoz tartozóként. Ha az alkalmazás eltávolítja a felhasználói adatokat egy fájlból, de a fájl többi adatát meg kívánja őrizni, akkor *mindenképp* meg kell változtatnia a fájl identitását (egy személyes felhasználóra vagy egy üres identitásra, a `MAMFileProtectionManager.protect` segítségével). Ha használ titkosítási szabályzatot, akkor a felhasználóhoz tartozó törlendő fájlokat a rendszer nem fejti vissza, és így ezek tartalma elérhetetlen lesz az alkalmazás számára a törlés után.

A `WIPE_USER_DATA` értesítésekre regisztráló alkalmazások nem részesülnek az SDK alapértelmezett szelektív törlési funkciójának előnyeiben. A többidentitásos alkalmazások esetében ez nagyobb jelentőségű tényező lehet, mivel a MAM alapértelmezett szelektív törlése csak a törlendő identitáshoz tartozó fájlokat fogja törölni. Ha a többidentitásos alkalmazás szeretné végrehajtatni a MAM alapértelmezett szelektív törlését, _**és**_ ezenfelül saját törlési műveleteit is végre szeretné hajtani, akkor célszerű feliratkoznia a `WIPE_USER_AUXILIARY_DATA` értesítésekre. Ezt az értesítést az SDK közvetlenül azelőtt küldi el, hogy végrehajtaná a MAM alapértelmezett szelektív törlési műveletét. Az alkalmazások nem regisztrálhatnak mindkét `WIPE_USER_DATA` és `WIPE_USER_AUXILIARY_DATA`.

Az alapértelmezett szelektív törlésének fog zárja be az alkalmazás szabályosan, tevékenységek befejezése és alkalmazás folyamatának leállítása. Ha az alkalmazás felülírja az alapértelmezett szelektív törlést, érdemes zárja be az alkalmazást, hogy manuálisan megakadályozza, hogy a felhasználó memórián belüli adathozzáférés után a törlést.


## <a name="enabling-mam-targeted-configuration-for-your-android-applications-optional"></a>Célzott MAM-konfiguráció engedélyezése Android-alkalmazásokhoz (nem kötelező)
Alkalmazásspecifikus kulcs-érték párokat az Intune-konzolon konfigurálhatók [MAM-TUDJUK](https://docs.microsoft.com/intune/app-configuration-policies-managed-app) és [Androidos munkahelyi profil alkalmazások](https://docs.microsoft.com/intune/app-configuration-policies-use-android).
A kulcs-érték párokat az Intune nem értelmezi, hanem továbbadja az alkalmazásnak. Azon alkalmazások, amelyek ilyen konfigurációt kívánnak kapni, a `MAMAppConfigManager` és `MAMAppConfig` osztályokat használhatják ehhez. Ha több szabályzat ugyanazon alkalmazást célozza, valószínűleg több ütköző érték érhető el ugyanazon kulcshoz.

> [!NOTE] 
> Konfigurációk a MAM-n keresztül történő továbbítását beállítása – nem lehet, hogy a delievered `offline`.  Csak az Android Enterprise AppRestrictions kézbesítése egy `MAMUserNotification` az ebben az esetben egy üres identitásra.

### <a name="example"></a>Példa
```java
MAMAppConfigManager configManager = MAMComponents.get(MAMAppConfigManager.class);
String identity = "user@contoso.com"
MAMAppConfig appConfig = configManager.getAppConfig(identity);
LOGGER.info("App Config Data = " + appConfig.getFullData());
String valueToUse = null;
if (appConfig.hasConflict("foo")) {
    List<String> values = appConfig.getAllStringsForKey("foo");
    for (String value : values) {
        if (isCorrectValue(value)) {
            valueToUse = value;
        }
    }
} else {
    valueToUse = appConfig.getStringForKey("foo", MAMAppConfig.StringQueryType.Any);
}
LOGGER.info("Found value " + valueToUse);
```

### <a name="notification"></a>Értesítés
Az alkalmazás konfigurációja egy új értesítéstípust ad hozzá:
* **REFRESH_APP_CONFIG**: Ezt az értesítést a `MAMUserNotification` és tájékoztatja az alkalmazást, hogy új alkalmazáskonfigurációs adatok érhető el.

### <a name="further-reading"></a>További információk
További információ a Graph API funkcióiról: [Graph API-segédlet](https://developer.microsoft.com/graph/docs/concepts/overview). <br>

A célzott MAM-alkalmazáskonfigurációs szabályzat Android rendszerben való létrehozásáról lásd [A Microsoft Intune alkalmazáskonfigurációs szabályzatainak használata Android rendszerben](https://docs.microsoft.com/intune/app-configuration-policies-use-android) célzott MAM-alkalmazáskonfigurációról szóló szakaszát.

## <a name="style-customization-optional"></a>Stílus testreszabása (nem kötelező)

A MAM SDK-ban létrehozott nézetek megjelenését testre lehet szabni, hogy jobban illeszkedjenek az SDK-t integráló alkalmazáshoz. Meg lehet szabni az elsődleges, a másodlagos és a háttérszínt, valamint az alkalmazás emblémájának méretét. Ez a testreszabás nem kötelező. Ha nincs konfigurálva egyéni stílus, a rendszer az alapértelmezéseket használja.


### <a name="how-to-customize"></a>A testreszabás menete
Ha módosítani szeretné az Intune MAM-nézeteinek stílusát, először készítsen stílus-felülíró XML-fájlt. Ezt helyezze el az alkalmazás „/res/xml” könyvtárában, és adjon neki tetszőleges nevet. Az alábbi példa bemutatja a fájl szükséges formátumát.
```xml
<?xml version="1.0" encoding="utf-8"?>
<styleOverrides>
    <item
        name="foreground_color"
        resource="@color/red"/>
    <item
        name="accent_color"
        resource="@color/blue"/>
    <item
        name="background_color"
        resource="@color/green"/>
    <item
        name="logo_image"
        resource="@drawable/app_logo"/>
</styleOverrides>
```

Az alkalmazásban már meglévő erőforrásokat kell újrahasználnia, tehát például a zöld színt a colors.xml fájlban kell definiálni, és itt hivatkozni, de a „#0000ff” hexa színkódot itt nem használhatja. Az alkalmazásembléma legfeljebb 110 dip (dp) méretű lehet. Kisebb emblémát is megadhat, de az optimális megjelenés érdekében érdemes kihasználni a maximális méretet. Ha túllépi a 110 dipes határt, a képet a rendszer lekicsinyíti, amitől valószínűleg homályos lesz.

Alább felsoroljuk az összes megengedett stílusattribútumot, az általuk szabályozott felületi elemeket, XML-attribútumnevüket és a hozzájuk várt erőforrástípusokat.

|Stílusattribútum | Érintett felületi elem | Attribútumelem neve | Várt erőforrástípus |
| -- | -- | -- | -- |
| Háttérszín | A PIN-kódot bekérő képernyő háttérszíne <Br>A PIN-kód mezőjének kitöltőszíne | background_color | Szín |
| Előtérszín | Előtérbeli szöveg színe <br> A PIN-kód mezőjének szegélyszíne alapértelmezett állapotban <br> A PIN-kód mezőjébe beírt (akár rejtjelezett) karakterek színe| foreground_color | Szín|
| Kiemelőszín | A PIN-kód mezőjének szegélyszíne kiemelt állapotban <br> Hivatkozások |accent_color | Szín |
| Alkalmazás emblémája | Az Intune PIN-kódot bekérő képernyőjén megjelenő nagy ikon | logo_image | Rajzolható |

## <a name="default-enrollment-optional"></a>Alapértelmezés szerinti regisztráció (választható)

Az alábbiakban útmutatást találhat egy APP-WE szolgáltatás automatikus regisztrációjához szükséges, az alkalmazásindításkor megjelenő felhasználói kérés beállításához (ebben a szakaszban erre **alapértelmezett regisztráció** néven hivatkoztunk), valamint ahhoz, hogy hogyan kényszerítheti az Intune alkalmazásvédelmi szabályzatait, hogy csak az Intune által védett felhasználók használhassák a SDK-val integrált Android LOB-alkalmazást. A cikk emellett ismerteti, hogyan engedélyezhető az SSO az SDK-val integrált Android LOB-alkalmazáshoz. Ezt **nem** támogatják azok az áruházbeli alkalmazások, amelyeket nem Intune-felhasználók is használhatnak.

> [!NOTE] 
> Az **alapértelmezett regisztráció** előnyei közé tartozik egy egyszerűsített módszer az eszközön található alkalmazás az APP-WE szolgáltatástól lekért szabályzatához.

> [!NOTE] 
> **Alapértelmezett regisztrációs** szuverén felhő tudatában van.

Az alábbi lépéseket követve az alapértelmezett regisztráció engedélyezéséhez:

1. Ha az alkalmazás integrálja az adal-t vagy az egyszeri Bejelentkezéssel, engedélyeznie kell a [konfigurálása adal-t](#configure-azure-active-directory-authentication-library-adal) következő [common ADAL konfigurációs](#common-adal-configurations) #2. Ha nem, előfordulhat, hogy kihagyja ezt a lépést.
   
2. Az alapértelmezett regisztráció engedélyezéséhez írja az alábbi értéket a jegyzékfájlba:
   ```xml 
   <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />
   ```
   > [!NOTE] 
   > Ez lehet az alkalmazás egyetlen MAM-WE-integrációja. Ha bármilyen más próbálkozás történik MAMEnrollmentManager API-k hívására, problémák merülnek fel.

3. A szükséges MAM-szabályzat engedélyezéséhez írja az alábbi értéket a jegyzékfájlba:
   ```xml 
   <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />
   ```
   > [!NOTE] 
   > Ez kényszeríti a felhasználót, hogy letöltse a Céges portált az eszközre, és a használat előtt elvégezze az alapértelmezett regisztrációt.


## <a name="limitations"></a>Korlátozások

### <a name="file-size-limitations"></a>Fájlméretre vonatkozó korlátozások

A [ProGuard](http://proguard.sourceforge.net/) nélkül futó nagyméretű kódbázis esetén a Dalvik végrehajtható fájlformátum korlátozásai problémát jelenthetnek. Konkrétan a következő korlátozások fordulhatnak elő:

1. A mezőkre vonatkozó 65 KB-os korlát.
2. A metódusokra vonatkozó 65 KB-os korlát.

### <a name="policy-enforcement-limitations"></a>Szabályzatbetartatási korlátozások

* **Tartalomfeloldók használata**: Az "átvitel vagy fogadás" Intune-szabályzatot előfordulhat, hogy részben vagy teljesen blokkolhatja eléréséhez a tartalomfeloldóknak a más alkalmazások tartalomszolgáltatójának használatát. Ennek következtében `ContentResolver` metódusok null vagy hibaértéket értéket (például `openOutputStream` kivételt fogja kijelezni `FileNotFoundException` Ha blokkolva van). Az alkalmazás a következő hívással állapíthatja meg, hogy a tartalomfeloldón keresztüli adatírás sikertelenségét házirend okozta (vagy hogy egy házirend ilyen hibát okozna):
    ```java
    MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(contentURI);
    ```
    vagy ha nincs hozzárendelt tevékenység

    ```java
    MAMPolicyManager.getPolicy().getIsSaveToLocationAllowed(contentURI);
    ```

    A második esetben a több identitást használó alkalmazásoknak ügyelniük kell a szálidentitás megfelelő beállítására (vagy explicit identitásértéket kell átadniuk a `getPolicy` metódushívásban).

### <a name="exported-services"></a>Exportált szolgáltatások

 Az Intune App SDK-ban szereplő AndroidManifest.xml fájlban szerepel a **MAMNotificationReceiverService** szolgáltatás, amelynek exportált szolgáltatásnak kell lennie ahhoz, hogy a Céges portál értesítéseket küldhessen a kezelt alkalmazásoknak. A szolgáltatás ellenőrzi a hívót annak ellenőrzéséhez, hogy csak a vállalati portál számára engedélyezett-e az értesítések küldése.

### <a name="reflection-limitations"></a>A reflexió korlátozásai
Egyes MAM-alaposztályok (például MAMActivity és MAMDocumentsProvider) olyan metódusokat tartalmaznak (az eredeti Android-alaposztályok alapján), amelyek paraméter- és visszatérési típusai csak bizonyos API-szintek felett érhetők el. Ezen okból kifolyólag nem mindig enumerálható reflexióval az alkalmazás-összetevők összes metódusa. Ez a korlátozás nemcsak a MAM-ra érvényes, hanem akkor is jelentkezne, ha az alkalmazás saját maga implementálná az adott metódusokat az Android-alaposztályokból.

### <a name="robolectric"></a>Robolectric
A MAM SDK-funkcionalitás Robolectric keretrendszerrel való tesztelése nem támogatott. A MAM SDK Robelectric futtatásakor viselkedések Robolectric alatti, nézve, amelyek nem felel meg pontosan a valódi eszközön vagy emulátory systému miatt problémákat is ismertek.

Ha a Roboelectric keretrendszerrel kell tesztelnie az alkalmazását, a javasolt kerülő megoldás az, hogy az alkalmazása logikai kódját áthelyezi egy segédosztályba, és az egységtesztelési apk-t egy olyan alkalmazásosztállyal hozza létre, amely nem öröklődik a MAMApplication osztályból.
## <a name="expectations-of-the-sdk-consumer"></a>Az SDK-használók elvárásai

Az Intune SDK fenntartja az Android API által biztosított szerződést, bár a szabályzatok betartatása miatt gyakrabban léphetnek fel hibaállapotok. Az alábbi androidos gyakorlati tanácsok csökkentik a hibák valószínűségét:

* Azon androidos SDK-függvények, amelyek null értékkel is visszatérhetnek, nagyobb valószínűséggel lesznek null értékűek.  A problémák minimalizálása érdekében biztosítsa, hogy a megfelelő helyeken legyenek null-ellenőrzések.

* A lekérdezhető funkciókat a MAM-os helyettesítő API-kkal kell lekérdezni.

* Minden származtatott függvénynek meg kell hívnia a szülőosztálybeli verzióját.

* Kerülje az API-k nem egyértelmű módon való használatát. Így például az `Activity.startActivityForResult` requestCode ellenőrzése nélküli használata működésbeli furcsaságokat idézhet elő.

## <a name="telemetry"></a>Telemetria

Az Androidhoz készült Intune App SDK nem szabályozza az alkalmazásából való adatgyűjtést. A vállalati portál alkalmazás alapértelmezés szerint naplózza a rendszer által létrehozott adatokat. Az adatokat az SDK a Microsoft Intune-nak küldi el. A Microsoft Policy megfelelően nem gyűjtünk a személyes adatokról.

> [!NOTE]
> Ha a végfelhasználók nem szeretnének ilyen adatokat küldeni, ki kell kapcsolniuk a telemetriát a Céges portál alkalmazás Beállítások menüpontjában. További információt [A használatra vonatkozó adatok Microsoft általi gyűjtésének kikapcsolása](https://docs.microsoft.com/intune-user-help/turn-off-microsoft-usage-data-collection-android) című témakörben találhat. 

## <a name="recommended-android-best-practices"></a>Ajánlott gyakorlati tanácsok Androidon

* Lehetőség szerint minden kódtárprojektnek azonos android:package csomagot kell használnia. Ez nem fog szórványos hibákat jelenteni futásidőben, mivel ez a probléma pusztán a buildelés során áll fenn. Az Intune App SDK újabb verziói ki fognak küszöbölni bizonyos párhuzamosságokat.

* Mindig az elérhető legújabb Android SDK buildelőeszközeit használja.

* Távolítsa el a felesleges és használaton kívüli kódtárakat (például android.support.v4)

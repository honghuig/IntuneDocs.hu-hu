---
title: Konfigurálja a Microsoft által kezelt kezdőképernyő alkalmazás
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan konfigurálhatja a Microsoft által felügyelt kezdőlap képernyős alkalmazást.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 865c7f03-f525-4dfa-b3a8-d088a9106502
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 50ac3ff27c22bf63b73f2ae10e6909112564180f
ms.sourcegitcommit: 1b7ee2164ac9490df4efa83c5479344622c181b5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/08/2019
ms.locfileid: "67648730"
---
# <a name="configure-the-microsoft-managed-home-screen-app-for-android-enterprise"></a>Konfigurálja a Microsoft által felügyelt Android Enterprise kezdőképernyő-alkalmazás

A felügyelt kezdőlap képernyő a használt vállalati tulajdonú Android Enterprise dedikált eszközök Intune-nal regisztrált, és a többalkalmazásos kioszk módban futó alkalmazás, amely. Ezekhez az eszközökhöz a felügyelt kezdőlap képernyő-ra épülve azt más jóváhagyott alkalmazások a gyorsindítóból funkcionál. A felügyelt kezdőlap képernyő rendszergazdák lehetővé teszi a szabhatja testre az eszközeiket, és korlátozhatja, hogy a felhasználó hozzáférhet. 

## <a name="when-to-configure-the-microsoft-managed-home-screen-app"></a>Ha a Microsoft által felügyelt kezdőlap képernyő alkalmazás konfigurálása

Eszközkonfiguráció keresztül elérhető beállítások esetén általában nincs beállításainak konfigurálása. Ezzel időt takarít meg, a hibák minimalizálása és kapja meg az Intune-támogatási jobb felhasználói élményt. Azonban néhány kezdőlap képernyő felügyelt beállítás jelenleg csak keresztül elérhető a **alkalmazáskonfigurációs szabályzatok** panel az Intune-konzolon. Megtudhatja, hogyan konfigurálhatja a különböző beállításokat a dokumentum használata vagy a configuration designerrel vagy JSON-parancsfájl használatával. 

> [!NOTE]
> Jelenleg lehetőség, de célszerű, lehetővé teszi felsorolt alkalmazások, és a webes hivatkozások keresztül rögzített **ügyfélalkalmazás** és **eszközkonfiguráció**. Az elérhető beállítások teljes listáját **eszközkonfiguráció** , amely hatással van a kezdőlap képernyő felügyelt, lásd: [eszközbeállítások dedikált](device-restrictions-android-for-work.md#dedicated-device-settings).  

Először keresse meg az Intune-konzolon, az Azure Portalon, és nyissa meg **ügyfélalkalmazás** > **alkalmazáskonfigurációs szabályzatok**. A konfigurációs szabályzat hozzáadása **felügyelt eszközök** futó **Android** , és válassza a **kezdőlap képernyő felügyelt** a társított alkalmazással. Kattintson a **konfigurációs beállítások** a különböző elérhető kezdőlap képernyő felügyelt beállításainak konfigurálása. 

## <a name="choosing-a-configuration-settings-format"></a>A konfigurációs beállítások formátuma kiválasztása

Két módszerrel, amellyel kezdőlap képernyő felügyelt konfigurációs beállításainak megadásához:

- **Konfigurációtervező** beállításokat konfigurálhatja egy könnyen kezelhető felhasználói felületen keresztül, amely lehetővé teszi a különböző szolgáltatások, és ki, és állítsa be az értékeket. Ezen módszer esetében nincsenek néhány letiltott konfigurációs kulcsok typu `BundleArray`. A konfigurációs kulcsokat csak JSON-adatok megadásával konfigurálható. 
- **JSON-adatok** lehetővé teszi, hogy a JSON-parancsfájl használatával az összes lehetséges konfigurációs kulcsok definiálása. 

Tulajdonságok a Configuration Designer hozzáadásakor automatikusan alakíthatók ezek a Tulajdonságok JSON kiválasztásával **adja meg a JSON-adatok** származó a **konfigurációs beállítások formátuma** legördülő listából.

![Képernyőkép a konfigurációs beállítások formátuma](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_01.png)

## <a name="using-configuration-designer"></a>Konfigurációtervező használata

Konfigurációtervező lehetővé teszi, hogy válassza ki az előre megadott beállításait és a hozzájuk tartozó értékek. 

![Képernyőkép a hozzáadott konfigurációs beállításai](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_02.png)

A következő táblázat felsorolja a kezdőlap képernyő felügyelt rendelkezésre álló konfigurációs kulcsok, értéktípusok, alapértékeket és leírásokat. A leírás a kiválasztott értékek alapján várt eszköz viselkedésének nyújt. A táblázatban nem szereplő Configuration Designer a letiltott konfigurációs kulcsokat.

| Konfigurációs kulcs | Érték típusa | Alapértelmezett érték | Leírás |
|---------------------------------------------------------------------------------------------------------------------------|-------------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Rács méretének beállítása | Karakterlánc | Automatikus | Lehetővé teszi az alkalmazások kell elhelyezni a felügyelt kezdőképernyőn rács méretét. Beállíthatja, hogy az alkalmazás sorok és oszlopok meghatározhatja a rács méretét a következő formátumban száma `columns;rows`. A rács méretét határozza meg, ha maximális számát, amely egy sort a kezdőképernyőn megjelenő alkalmazások lenne a beállított sorok számát és egy oszlopot a kezdőképernyőn megjelenő alkalmazások maximális számát beállított oszlopok számát. |
| Képernyő fejléc engedélyezése | bool | IGAZ | Lehetővé teszi a különböző nézeteket, amelyek a felügyelt kezdőképernyő kínál, például a hírcsatorna vagy hírcsatorna kártyák felső fejlécében. Ha engedélyezi ezt a beállítást, az eszközök felhasználóinak jelenik meg a fejléc. |
| Állapotsor eszköz engedélyezése | bool | IGAZ | Lehetővé teszi a kezdőképernyőn (felső sáv, amely megjeleníti az aktuális kapcsolatot, például Wi-Fi és stb.) lévő állapotsávon található. Ha engedélyezi ezt a konfigurációs kulcsot, a felhasználó felel meg a kapcsolatok és aktív alkalmazások állapotsorok megjelenített ikonokat megtekinthető lesz. |
| A jelvény értesítések engedélyezése | bool | HAMIS | Lehetővé teszi, hogy az értesítési jelvény az ikonok, amely az alkalmazás az új értesítések száma alapján mutatja. Ha engedélyezi ezt a beállítást, a végfelhasználók számára jelennek-e a értesítési jelvények alkalmazásokat, az olvasatlan értesítések. Ha ez a konfiguráció fő le van tiltva, a végfelhasználó számára nem jelenik meg, előfordulhat, hogy alkalmazásokba jelzéssel értesítést olvasatlan értesítések. |
| Zárolási kezdőképernyőjén | bool | IGAZ | Eltávolítja a kezdőképernyőn ikonok Navigálás a végfelhasználó képességét. Ha engedélyezi ezt a konfigurációs kulcsot, az ikonok a kezdőképernyőn lesz zárolva, és a végfelhasználó nem tudná, és a kezdőképernyő különböző rács elfoglalt húzza. Ha engedélyezve van `false`, a végfelhasználók tudják alkalmazás és a Webhivatkozás ikonok Navigálás a felügyelt kezdőlap képernyőn.  |
| Eszköz asztaltulajdonság beállítása | Karakterlánc | Alapértelmezett | Lehetővé teszi egy tetszőleges háttérkép beállítása, amely egy háttérképeként beállítja a kép URL-Címének megadásával. |
| Állítsa be az alkalmazás az ikon mérete | integer | 2 | Lehetővé teszi a kezdőképernyőn látható alkalmazások ikon méretének beállítása. Ebben a konfigurációban a különböző méretű - (legkisebb) 0, 1 (kicsi), 2 (rendszeres), kiválaszthatja a következő értékeket (nagy) 3 és 4 (legnagyobb). |
| Set alkalmazás mappa ikonra | integer | 0 | Lehetővé teszi, hogy meghatározza az alkalmazás mappa megjelenése a kezdőképernyőn. A Megjelenés a következő értékek közül választhat: Sötét Square(0);   Sötét Circle(1); Világos Square(2); Világos Circle(3). |
| Hitelesítési módok engedélyezése | bool | HAMIS | A felhasználó lehetőség műveletek, például pöccintsen felfelé és lefelé pöccintsen különböző hitelesítési módok engedélyezése. Ha letiltja ezt a konfigurációs kulcsot, a végfelhasználók csak akkor tudnak pöccintsen jobbra, ha van egy második oldalára, és térjen vissza a kezdőlapon. |
| Függőleges görgethető engedélyezése | bool | HAMIS | Lehetővé teszi, hogy a felügyelt kezdőképernyő függőleges görgetést. Ha engedélyezi ezt a konfigurációs kulcsot, a végfelhasználó csak lesz függőleges helyett vízszintesen érintőképernyőn navigálhat különböző oldalakat. |
| Set-kezdőképernyő téma | sztring | Theme.Light.Blue | Válassza ki a téma a kezdőképernyőn a témákat különböző színű előre meghatározott teszi lehetővé. A következő formátumban írja be a karakterlánc a következő témák választhat.   Theme.Light.Green. Ahol világos lecserélhető sötét for a sötét téma- és zöld kicserélhető kék, sárga, Rózsaszínre, piros, narancssárga és a lila. |
| Tároló engedélyezése | bool | HAMIS | Lehetővé teszi az alkalmazás dock szakaszában a kezdőképernyőn alján megjelenített állandó alkalmazások és a belépési pont összes telepített alkalmazáshoz. Ha engedélyezi ezt a konfigurációs kulcsot, a végfelhasználó a dockban alkalmazások hozzáférhetnek, és a minden alkalmazás szakaszban felsorolt engedélyezése megtörtént-e az eszközön telepített összes alkalmazás listájára go is elérhető lesz. |
| Képernyő tájolásának beállítása | integer | 1 | Fekvő tájolással, a kezdőképernyőn tájolásának beállítása, vagy Automatikus elforgatás lehetővé teszi lehetővé. A tájolás (a tájolású módban), 1 érték megadásával állíthatja (a fekvő tájolásban) 2, 3 (a Autorotate). |
| Kezdőképernyő hírcsatorna engedélyezése | bool | HAMIS | Lehetővé teszi a kezdőképernyőn, amelynek bal oldalán a kezdőképernyőn érintőképernyőn láthatja a hírcsatornában. Ezzel a hírcsatornával jeleníti meg a különböző típusú tartalom például hírek, naptár, gyakori felhasználói alkalmazásokban és a Cortana beszédfelismerési asszisztens kártya stb. Ha engedélyezi ezt a beállítást, a végfelhasználó a hírcsatornán navigálhat a bal oldalon, a kezdőképernyőn érintőképernyőn lesz. |
| Áttekintés mód engedélyezése | bool | HAMIS | Lehetővé teszi a végfelhasználók hozzáadása vagy eltávolítása a kezdőképernyőn, közvetlenül az alapértelmezett képernyőnek a érintőképernyőn elérhető különböző oldalakat. Ha engedélyezi ezt a beállítást, a végfelhasználó fogja tudni hozzáadni az alapértelmezett oldal, a kezdőképernyő jobb lapozható is tudják módosítani az alapértelmezett oldalt és is elérhetik a beállítások a felügyelt kezdőképernyőn eléréséhez. |
| Eszköz telemetria engedélyezése | bool | HAMIS | Lehetővé teszi a számára a felügyelt kezdőképernyő rögzített telemetria. Ha engedélyezi ezt a beállítást, a Microsoft képes rögzíteni az eszköz használatának telemetriai adatait, például egy adott alkalmazás elindítása az eszköz hányszor lesz. |
| Alkalmazások engedélyezése felsorolt beállítása | bundleArray | HAMIS | Lehetővé teszi, hogy az alkalmazás az eszközön telepített között a kezdőképernyőn látható alkalmazások megadásához. Az alkalmazásokat, amelyeket szeretné láthatóvá tenni az alkalmazást csomag nevének megadásával meghatározhatja a az alkalmazások, például com.microsoft.emmx biztosítja, beállítások elérhető-e a kezdőképernyőn. Az alkalmazásokat, hogy engedélyezi-listán ebben a szakaszban már telepítve kell lennie az eszközön annak érdekében, hogy a kezdőképernyőn látható. |
| Rögzített beállítása webes hivatkozások | bundleArray | HAMIS | Lehetővé teszi webhelyek rögzítése a kezdőképernyőn Gyorsindítás ikonjai. Ezzel a konfigurációval határozza meg az URL-címet, és adja hozzá a kezdőképernyőn, indítsa el a böngészőben, hogy egyetlen koppintással a végfelhasználó számára. |
| Keresősáv engedélyezése | bool | HAMIS | Lehetővé teszi a kezdőképernyőn a keresősávba. Ha engedélyezi ezt a beállítást, akkor az eszköz számára a kezdőképernyőn, ahol azok tudná adja meg, függetlenül azok szeretne keresni a weben a keresősávba jelennek meg. |
| Gépház alkalmazás letiltása | bool | HAMIS | A beállítások lapon letiltja a felügyelt kezdőlap képernyő. Ha letiltja ezt a beállítást, a végfelhasználó számára az eszköz nem lesz képes a beállítások a felügyelt kezdőlap képernyő. |
| Képernyőkímélő engedélyezése | bool | HAMIS | A képernyő takarékos üzemmódban engedélyezéséhez, vagy sem. Ha a beállítása igaz, konfigurálhat **screen_saver_image**, **screen_saver_show_time**, **inactive_time_to_show_screen_saver**, és **media_detect_ screen_saver**. |
| Képernyőn a képernyőkímélő kép | Karakterlánc |   | Állítsa be a képernyőn a képernyőkímélő kép URL-CÍMÉT. Ha nincs URL-cím van beállítva, eszközöket jeleníti meg az alapértelmezett képernyőn a képernyőkímélő lemezkép képernyőkímélő aktiválása. Alapértelmezett kép a kezdőlap képernyő felügyelt alkalmazás ikonját.  |
| Képernyőn a képernyőkímélő idő megjelenítése | integer | 0 | Lehetővé teszi a beállítással az eszköz beállítása idő másodpercben a képernyőkímélő képernyő takarékos üzemmódban jelenik meg. Ha 0 értékre állítja, a képernyőkímélő jeleníti meg a képernyő takarékos üzemmódban határozatlan ideig, amíg az eszköz aktívvá válik.  |
| Ahhoz, hogy a képernyőkímélő tétlenség ideje | integer | 30 | Az eszköz nem aktív a képernyőkímélő aktiválása előtt másodpercek számát. Ha az értéke 0, az eszköz képernyő takarékos üzemmódban soha nem váltanak. |
| Media észleli a képernyőkímélő megjelenítése előtt | bool | IGAZ | Válassza ki, hogy az eszköz képernyőjén meg kell jelennie a képernyőkímélő ha hang és videó lejátszása az eszközön. Ha igaz értékű, az eszköz nem játszható le a hang/kép, függetlenül az érték a **inactive_time_to_show_scree_saver**. Ha értéke HAMIS, eszköz képernyőjén jeleníti meg megfelelően állítsa be értéket a képernyőkímélő **inactive_time_to_show_screen_saver**.   |
| Engedélyezze a virtuális kezdőlapjának gombja | bool | HAMIS | Kapcsolja be ezt a beállítást `True` , hogy a végfelhasználó, aki rendelkezik hozzáféréssel, amely visszaadja az aktuális feladathoz vannak a felügyelt kezdőlapjára a felhasználó otthoni felügyelt kezdőképernyő gombra.  |
| Virtuális otthoni gomb típusa | Karakterlánc | swipe_up | Használat **swipe_up** a kezdőlap gombja hozzáférés és a egy pöccintsen felfelé kézmozdulat. Használat **lebegőpontos** fix kiszolgálású, állandó otthoni gombra, a végfelhasználók által a képernyőn áthelyezhető eléréséhez. |
| Akkumulátor és jel erőssége mutató sáv | bool | True  | Ez a beállítás bekapcsolásával `True` az akkumulátor és jel erőssége jelző sáv mutatja. |
| Kilépés zárolási feladat módjának jelszava | Karakterlánc |   | Adjon meg egy 4 – 6 számjegyű kód használatával ideiglenesen dobja el a hibaelhárítási zárolása-tevékenységhez módból. |
| Wi-Fi-beállítás megjelenítése | bool | HAMIS | Ez a beállítás bekapcsolásával `True` lehetővé teszi, hogy a végfelhasználó kapcsolhatja be és ki a Wi-Fi, vagy másik Wi-Fi hálózathoz való csatlakozáshoz.  |
| Bluetooth-beállítás megjelenítése | bool | HAMIS | Ez a beállítás bekapcsolásával `True` felhasználó-vagy bekapcsolása a Bluetooth és csatlakozni más Bluetooth-kompatibilis eszközök segítségével.   |
| Alkalmazások mappa neve szerint vannak rendezve: | bool | IGAZ | Ez a beállítás bekapcsolásával `False` lehetővé teszi, hogy egy olyan mappa, amelyben megadott sorrendben jelennek meg az elemeket. Ellenkező esetben megjelennek a mappa alphbetically.   |
| Engedélyezett alkalmazás sorrend | bool | HAMIS | Ez a beállítás bekapcsolásával `True` lehetővé teszi, hogy lehetővé teszik a sorrendet, az alkalmazások, weblinks és mappákat a felügyelt kezdőlap képernyőn. Az engedélyezés után a beállítása, a Rendezés **app_order**mobileszközeiket végfelhasználói kapcsolhatja be és ki a Bluetooth és csatlakozni más Bluetooth-kompatibilis eszközökhöz.   |
| Alkalmazás sorrend | bundleArray | HAMIS | A felügyelt kezdőlap képernyőn alkalmazásokat, weblinks és mappák sorrendjének megadását teszi lehetővé. Ezzel a beállítással a **kezdőlap zárolási képernyő** engedélyezni kell, **rács méretének beállítása** meg kell határozni és **engedélyezett alkalmazás rendelés** értékre kell állítani `True`.   |

## <a name="enter-json-data"></a>Enter JSON Data

Adja meg a JSON-adatok kezdőlap képernyő felügyelt összes elérhető beállításait, valamint az le van tiltva, a beállítások konfigurálásához **Configuration Designer**.

![Képernyőkép a hozzáadott JSON-adatok](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_03.png)

A felsorolt konfigurálható beállítások listáját mellett a **Configuration Designer** tábla (fent), a következő táblázat tartalmazza a konfigurációs kulcsokat csak JSON-adatok keresztül lehet konfigurálni.

|    Konfigurációs kulcs    |    Érték típusa    |    Alapértelmezett érték    |    Leírás    |
|-------------------------------------------------|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Alkalmazások engedélyezése felsorolt beállítása    |    bundleArray    | <img alt="JSON - Example 1" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson01.png" width="300"> |    Lehetővé teszi, hogy az alkalmazás az eszközön telepített között a kezdőképernyőn látható alkalmazások megadásához. Az alkalmazások meghatározhatja, hogy láthatóvá szeretné az alkalmazások app csomag nevének megadásával, például com.android.settings biztosítja, beállítások elérhető-e a kezdőképernyőn. Az alkalmazásokat, hogy engedélyezi-listán ebben a szakaszban már telepítve kell lennie az eszközön annak érdekében, hogy a kezdőképernyőn látható.    |
|    Rögzített beállítása webes hivatkozások    |    bundleArray    | <img alt="JSON - Example 2" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson02.png" width="300"> |    Lehetővé teszi webhelyek rögzítése a kezdőképernyőn Gyorsindítás ikonjai. Ezzel a konfigurációval határozza meg az URL-címet, és adja hozzá a kezdőképernyőn, indítsa el a böngészőben, hogy egyetlen koppintással a végfelhasználó számára.    |
|    Hozzon létre felügyelt mappát alkalmazások csoportosításához    |    bundleArray    | <img alt="JSON - Example 3" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson03.png" width="300"> |    Lehetővé teszi, hogy hozhat létre és mappák, valamint a csoport alkalmazások belül ezeket a mappákat. A végfelhasználók nem tudja áthelyezni a mappákat, nevezze át a mappákat vagy az alkalmazások áthelyezése a mappákban található.   Mappák létrehozása a sorrendben fog megjelenni, és betűrend szerint jelenik meg a mappákban található alkalmazások.         Megjegyzés: mappákba csoportosításához használni kívánt összes alkalmazást kell hozzárendelni, az eszközhöz szükséges és kell hozzáadni a felügyelt kezdőlap képernyőre.     |

Az alábbi példa tartalmazza az összes elérhető konfigurációs kulccsal rendelkező JSON-parancsfájl:

```json
{
    "kind": "androidenterprise#managedConfiguration",
    "productId": "com.microsoft.launcher.enterprise",
    "managedProperty": [
        {
            "key": "keep_page_header",
            "valueBool": true
        },
        {
            "key": "keep_status_bar",
            "valueBool": true
        },
        {
            "key": "show_notification_badge",
            "valueBool": false
        },
        {
            "key": "lock_home_screen",
            "valueBool": true
        },
        {
            "key": "wallpaper",
            "valueString": "default"
        },
        {
            "key": "icon_size",
            "valueInteger": 2
        },
        {
            "key": "app_folder_icon",
            "valueInteger": 0
        },
        {
            "key": "gesture_on",
            "valueBool": false
        },
        {
            "key": "vertical_scrolling",
            "valueBool": false
        },
        {
            "key": "theme",
            "valueString": "Theme.Light.Blue"
        },
        {
            "key": "dock_enable",
            "valueBool": false
        },
        {
            "key": "screen_orientation",
            "valueInteger": 1
        },
        {
            "key": "feed_enable",
            "valueBool": false
        },
        {
            "key": "allow_overview_mode",
            "valueBool": false
        },
        {
            "key": "enable_telemetry",
            "valueBool": false
        },
        {
            "key": "applications",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": “app package name here”
                        }
                    ]
                }
            ]
        },
        {
            "key": "weblinks",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "link",
                            "valueString": “link here”
                        },
                        {
                            "key": "label",
                            "valueString": “weblink label here”
                        }
                    ]
                }
            ]
        },
        {
            "key": "search_bar",
            "valueBool": false
        },
        {
            "key": "hide_settings",
            "valueBool": false
        },
        {
            "key": "show_virtual_home",
            "valueBool": false
        },
        {
            "key": "virtual_home_type",
            "valueString": "swipe_up"
        },
        {
            "key": "show_virtual_status_bar",
            "valueBool": true
        },
        {
            "key": "exit_lock_task_mode_code",
            "valueString": ""
        },
        {
            "key": "show_wifi_setting",
            "valueBool": false
        },
        {
            "key": "show_bluetooth_setting",
            "valueBool": false
        },
        {
            "key": "grid_size",
            "valueString": "4;5"
        },
        {
            "key": "app_order_enabled",
            "valueBool": true
        },
        {
            "key": "apps_in_folder_ordered_by_name",
            "valueBool": true
        },
        {
            "key": "app_orders",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": "com.Microsoft.emmx"
                        },
                        {
                            "key": "type",
                            "valueString": "application"
                        },
                        {
                            "key": "container",
                            "valueInteger": 1
                        },
                        {
                            "key": "position",
                            "valueInteger": 1
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Work"
                        },
                        {
                            "key": "type",
                            "valueString": "managed_folder"
                        },
                        {
                            "key": "container",
                            "valueInteger": 1
                        },
                        {
                            "key": "position",
                            "valueInteger": 2
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": "com.microsoft.launcher.enterprise"
                        },
                        {
                            "key": "type",
                            "valueString": "application"
                        },
                        {
                            "key": "class",
                            "valueString": "com.microsoft.launcher.launcher"
                        },
                        {
                            "key": "container",
                            "valueInteger": 1
                        },
                        {
                            "key": "position",
                            "valueInteger": 3
                        }
                    ]
                }
            ]
        },
        {
            "key": "managed_folders",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Folder name here"
                        },
                        {
                            "key": "applications",
                            "valueBundleArray": [
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.emmx"
                                        }
                                    ]
                                },
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.bing"
                                        }
                                    ]
                                },
                                {
                                    "managedProperty": [
                                        {
                                            "key": "link",
                                            "valueString": "https://microsoft.com/"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Example folder name 2"
                        },
                        {
                            "key": "applications",
                            "valueBundleArray": [
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.office.word"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    ]
}

```
## <a name="next-steps"></a>További lépések

- Dedikált Android Enterprise-eszközökkel kapcsolatos további információkért lásd: [dedikált vállalati Android-eszköz regisztrálása az Intune beállítása](android-kiosk-enroll.md).

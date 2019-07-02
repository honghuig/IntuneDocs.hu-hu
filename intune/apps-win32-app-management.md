---
title: Adjon hozzá és Win32-alkalmazások hozzárendelése a Microsoft Intune
titleSuffix: ''
description: Ismerje meg, hogyan adhat hozzá, hozzárendelése és Win32-alkalmazások Microsoft Intune-nal kezelheti. E témakör áttekintést nyújt a Win32-alkalmazások telepítési és kezelési lehetőségeiről az Intune-ban, valamint a Win32-alkalmazásokkal kapcsolatos hibák elhárításával kapcsolatban.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: efdc196b-38f3-4678-ae16-cdec4303f8d2
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e458558d488c9bbca2c2ed78255be103a5ac79f0
ms.sourcegitcommit: 116ef72b9da4d114782d4b8dd9f57556c9b01511
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/01/2019
ms.locfileid: "67494385"
---
# <a name="intune-standalone---win32-app-management"></a>Önálló Intune - Win32-Alkalmazáskezelés

[Az Intune önálló verziója](mdm-authority-set.md) mostantól lehetővé teszi, hogy nagyobb Win32-alkalmazás felügyeleti képességeket. Bár a felhőhöz csatlakozó ügyfelek használhatják a Konfigurációkezelőt a Win32-alkalmazások kezeléséhez, a kizárólag Intune-nal rendelkező ügyfelek számára több lehetőség érhető el az üzletági (LOB) Win32-alkalmazások kezeléséhez. E témakör áttekintést nyújt a Win32-alkalmazások Intune-ban elérhető kezelési funkcióiról, valamint a hibaelhárítással kapcsolatos lehetőségekről.

> [!NOTE]
> Az alkalmazás felügyeleti funkció mindkét 32 bites és 64 bites operációs rendszer-architektúra támogatja a Windows-alkalmazások.

## <a name="prerequisites"></a>Előfeltételek

Win32-Alkalmazáskezelés használatához győződjön meg a következő feltételeknek:

- A Windows 10 1607-es verzió vagy újabb (vállalati, Pro és Education verziók)
- A Windows 10-ügyfélnek: 
    - Eszközök az Azure AD-csatlakoztatott legyen, és automatikusan regisztrálva. Az Intune felügyeleti bővítmény támogatja az Azure AD-hez, a hibrid tartományhoz, a csoport házirend beléptetett eszközök támogatottak. 
    > [!NOTE]
    > A csoportházirend regisztrált forgatókönyv – a végfelhasználók használnak a helyi felhasználói fiók AAD-be való csatlakozás a Windows 10-es eszköz. A felhasználó jelentkezzen be az eszközt, az AAD felhasználói fiók használatával kell, és regisztrálása az Intune-ban. Az Intune telepíti az Intune felügyeleti bővítmény az eszközön, ha egy PowerShell-parancsprogram, vagy egy Win32-alkalmazás a felhasználó vagy eszköz számára vonatkozik.
- Windows-alkalmazások mérete az egyes alkalmazások maximumon 8 GB.

## <a name="prepare-the-win32-app-content-for-upload"></a>A Win32-alkalmazás tartalmának előkészítése a feltöltéshez

Használja a [Microsoft Win32 tartalom előkészítő eszközt](https://go.microsoft.com/fwlink/?linkid=2065730) előre a Windows klasszikus (Win32) alkalmazások feldolgozásához. Az eszköz konvertálja az alkalmazástelepítési fájlok a *.intunewin* formátumban. Az eszköz az Intune által az alkalmazás telepítési állapotának meghatározásához szükséges attribútumok némelyike is észleli. Miután ezt az eszközt használja az alkalmazást telepítő mappához, lesz egy Win32-alkalmazás létrehozása az Intune-konzolon.

> [!IMPORTANT]
> A [Microsoft Win32 tartalom előkészítő eszközt](https://go.microsoft.com/fwlink/?linkid=2065730) zips alkalmazást az összes fájlt és almappát, amikor létrehozza a *.intunewin* fájlt. Ügyeljen arra, a Microsoft Win32 tartalom előkészítő eszköz külön installer-fájlok és mappák, így nem adja meg az eszközt vagy más szükségtelen fájlok és mappák a *.intunewin* fájlt.

Letöltheti a [Microsoft Win32 tartalom előkészítő eszközt](https://go.microsoft.com/fwlink/?linkid=2065730) a Githubról zip-fájlként. A tömörített fájl tartalmaz egy nevű mappát **Microsoft-Win32-Content-Prep-Tool-master**. A mappa tartalmazza az előkészítő eszköze, a licenc, egy információs fájl és a kibocsátási megjegyzéseket. 

### <a name="process-flow-to-create-intunewin-file"></a>Folyamat .intunewin fájl létrehozása

   ![Folyamat .intunewin fájl létrehozása](./media/prepare-win32-app.svg)

### <a name="run-the-microsoft-win32-content-prep-tool"></a>A Microsoft Win32 tartalom előkészítő eszköz futtatása

Ha `IntuneWinAppUtil.exe` paraméterek nélkül a parancsablakból, az eszköz végigvezeti Önt a beviteli a szükséges paramétereket lépésről lépésre. Vagy a paramétereket adhat hozzá a parancs a következő rendelkezésre álló parancssori paraméterek alapján.

### <a name="available-command-line-parameters"></a>Elérhető parancssori paraméterek 

|    **Parancssori paraméter**    |    **Leírás**    |
|:------------------------------:|:----------------------------------------------------------:|
|    `-h`     |    Súgó    |
|    `-c <setup_folder>`     |    A mappa összes telepítési fájljai számára. Ebben a mappában lévő összes fájl tömörítése be *.intunewin* fájlt.    |
|    `-s <setup_file>`     |    Telepítőfájl (például *setup.exe* vagy *setup.msi*).    |
|    `-o <output_folder>`     |    Kimeneti mappa a létrehozott *.intunewin* fájl számára.    |
|    `-q`       |    Csendes mód    |

### <a name="example-commands"></a>Példaparancsok

|    **Példaparancs**    |    **Leírás**    |
|:-----------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    `IntuneWinAppUtil -h`    |    Ez a parancs megjeleníti az eszköz használatára vonatkozó információkat.    |
|    `IntuneWinAppUtil -c c:\testapp\v1.0 -s c:\testapp\v1.0\setup.exe -o c:\testappoutput\v1.0 -q`    |    Ez a parancs létrehozza az `.intunewin` fájlt a megadott forrásmappa és telepítőfájl alapján. Az MSI-telepítőfájlhoz az eszköz lekéri az Intune-hoz szükséges adatokat. Ha a `-q` van megadva, a parancs csendes módban fog futni, és ha a kimeneti fájl már létezik, felül fogja írni. Ha a kimeneti mappa még nem létezik, akkor automatikusan létrejön.    |

Létrehozásakor egy *.intunewin* fájlt minden olyan fájlok, a telepítési mappa egy almappájába hivatkoznia kell. Ezután használja a relatív elérési út egy konkrét fájlt kell hivatkoznia. Példa:

**Telepítő forrásmappája:** *c:\testapp\v1.0*<br>
**Licencfájl:** *c:\testapp\v1.0\licenses\license.txt*

Tekintse meg a *license.txt* fájl relatív elérési út használatával *licenses\license.txt*.

## <a name="create-assign-and-monitor-a-win32-app"></a>Win32-alkalmazás létrehozása, hozzárendelése és monitorozása

Az üzletági (LOB) alkalmazásokhoz hasonlóan Win32-alkalmazást is hozzáadhat a Microsoft Intune-hoz. Az ilyen alkalmazásokat általában házon belül írják, vagy egy külső féltől származnak. 

### <a name="process-flow-to-add-a-win32-app-to-intune"></a>A folyamat egy Win32-alkalmazás hozzáadása az Intune-hoz

   ![A folyamat egy Win32-alkalmazás hozzáadása az Intune-hoz](./media/add-win32-app.svg)

### <a name="add-a-win32-app-to-intune"></a>A Win32-alkalmazás hozzáadása az Intune-hoz

Az alábbi lépések útmutatást nyújtanak a Windows-alkalmazások Intune-hoz való hozzáadásához.

### <a name="step-1-specify-the-software-setup-file"></a>1\. lépés: A szoftvertelepítő fájl megadása

1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3.  Az **Intune** panelen válassza az **Ügyfélalkalmazások** > **Alkalmazások** > **Hozzáadás** elemet.
4.  Az a **Hozzáadás** alkalmazás panelen válassza **Windows-alkalmazás (Win32)** a megadott legördülő listából.

    ![Az hozzáadása panelen – Hozzáadás típusa legördülő menü képernyőképe](./media/apps-win32-app-01.png)

### <a name="step-2-upload-the-app-package-file"></a>2\. lépés: Az alkalmazáscsomag-fájl feltöltése

1.  Az **Alkalmazás felvétele** panelen válassza az **Alkalmazáscsomag-fájl** lehetőséget egy fájl kiválasztásához. Megjelenik az Alkalmazáscsomag-fájl panel.

    ![Az alkalmazás csomag fájl panelen – képernyőfelvétel](./media/apps-win32-app-02.png)

2.  Az **Alkalmazáscsomag-fájl** panelen válassza a tallózás gombot. Ezt követően jelölje ki az *.intunewin* kiterjesztésű Windows-telepítőfájlt.

    > [!IMPORTANT]
    > Győződjön meg arról, a Microsoft Win32 tartalom előkészítő eszköz legújabb verzióját használja. Ha nem a legújabb verziót használja, megjelenik egy figyelmeztetés, amely jelzi, hogy az alkalmazás csomagolása a Microsoft Win32 tartalom előkészítő eszköz egy régebbi verzióját használja. 

3.  Amikor végzett, válassza az **OK** gombot.

### <a name="step-3-configure-app-information"></a>3\. lépés: Az alkalmazásadatok konfigurálása

1.  Az alkalmazás konfigurálásához az **Alkalmazás hozzáadása** panelen válassza az **Alkalmazás adatai** elemet.
2.  Az **Alkalmazás adatai** panelen konfigurálja az alábbi információkat. Lehetséges, hogy ezen a panelen néhány érték automatikusan ki lesz töltve.
    - **Név**: Adja meg az alkalmazás nevét, a vállalati portálon megjelenő. Ha ugyanazt az alkalmazásnevet kétszer adja meg, mindkét alkalmazás meg fog jelenni a céges portálon.
    - **Description** (Leírás): Adja meg az alkalmazás leírását. A leírás megjelenik a Céges portálon.
    - **Közzété**r: Itt adhatja meg az alkalmazás kiadójának nevét.
    - **Kategória**: Válasszon ki egyet vagy többet a beépített Alkalmazáskategóriák közül, vagy válasszon egy kategóriát, amelyet Ön hozott létre. A kategóriákkal megkönnyítheti a felhasználók számára az alkalmazás megkeresését a Céges portálon való böngészés során.
    - **Megjelenítés kiemelt alkalmazásként a céges portálon**: Az alkalmazás jól észrevehető módon való megjelenítése a vállalati portál fő lapján, amikor a felhasználók tallózással alkalmazásokat keresnek.
    - **Információs URL-cím**: Igény esetén megadhatja az alkalmazással kapcsolatos információkat tartalmazó webhely URL-CÍMÉT. Az URL-cím megjelenik a Céges portálon.
    - **Adatvédelmi URL-címe**: Igény esetén megadhatja az alkalmazás adatvédelmi nyilatkozatát tartalmazó webhely URL-CÍMÉT. Az URL-cím megjelenik a Céges portálon.
    - **Fejlesztői**: Megadhatja az alkalmazás fejlesztőjének nevét.
    - **Tulajdonos**: Szükség esetén adja meg az alkalmazás tulajdonosának nevét. Például **HR részleg**.
    - **Megjegyzések**: Adja meg az alkalmazáshoz társítani kívánt megjegyzéseket.
    - **Embléma**: Töltse fel az alkalmazáshoz társított ikont. Ez az ikon jelenik meg az alkalmazásnál a Céges portálon böngésző felhasználók számára.
3.  Amikor végzett, válassza az **OK** gombot.

### <a name="step-4-configure-app-installation-details"></a>4\. lépés: Konfigurálja az alkalmazás telepítésének részletei
1.  Az alkalmazás telepítési és eltávolítási parancsának konfigurálásához az **Alkalmazás felvétele** panelen válassza a **Program** elemet.
2.  Adja meg az alkalmazás telepítéséhez szükséges teljes telepítési parancssort. 

    Például, ha az alkalmazás Fájlnév **MyApp123**, adja hozzá a következő:<br>
    `msiexec /p “MyApp123.msp”`<p>
    És, ha az alkalmazás `ApplicationName.exe`, a következő paranccsal lehetséges az alkalmazás nevét, majd a csomag által támogatott parancssori argumentumok (kapcsolók). <br>Példa:<br>
    `ApplicationName.exe /quiet`<br>
    A fenti parancsban a `ApplicationName.exe` csomag támogatja a `/quiet` parancssori argumentum.<p> A megadott argumentumok az alkalmazáscsomag által támogatott az alkalmazás gyártójától.

3.  Adja meg az alkalmazás eltávolításához szükséges teljes eltávolítási parancssort az alkalmazás GUID-értékei alapján. 

    Például:`msiexec /x “{12345A67-89B0-1234-5678-000001000000}”`

    > [!NOTE]
    > Az adott Win32-alkalmazás telepítését a **Felhasználó** vagy a **Rendszer** környezetben konfigurálhatja. A **Felhasználó** környezet csak az adott felhasználóra vonatkozik. A **Rendszer** környezet az adott, Windows 10-es rendszerű eszköz összes felhasználójára vonatkozik.
    >
    > A végfelhasználóknak nem kell bejelentkezniük az eszközön a Win32-alkalmazások telepítéséhez.
    > 
    > A Win32 alkalmazás telepítésének és eltávolításának fog hajtható végre rendszergazdai jogosultság (alapértelmezés szerint) Ha az alkalmazás felhasználói környezetben telepítésre van beállítva, és a végfelhasználó számára az eszköz rendszergazdai jogosultságokkal rendelkezik.

4.  Amikor végzett, válassza az **OK** gombot.

### <a name="step-5-configure-app-requirements"></a>5\. lépés: Alkalmazáskövetelmények konfigurálása

1.  Az alkalmazás telepítéséhez szükséges rendszerkövetelmények beállításához az **Alkalmazás felvétele** panelen válassza a **Követelmények** elemet.
2.  Az a **adjon hozzá egy olyan követelményszabályt** panelen konfigurálja az alábbi adatokat. Lehetséges, hogy ezen a panelen néhány érték automatikusan ki lesz töltve.
    - **Operációs rendszer-architektúra**: Válassza ki a architektúrák telepítenie kell az alkalmazást.
    - **Az operációs rendszer minimális**: Válassza ki az operációs rendszer minimálisan szükséges az alkalmazás telepítéséhez.
    - **Szükséges lemezterület (MB)** : Opcionálisan adja hozzá a szabad lemezterület a rendszermeghajtón az alkalmazás telepítéséhez szükséges.
    - **Memória (MB)** : Opcionálisan adja hozzá a fizikai memória (RAM), az alkalmazás telepítéséhez szükséges.
    - **Logikai processzorok szükséges minimális száma**: Opcionálisan adja hozzá az alkalmazás telepítéséhez szükséges logikai processzorok minimális száma.
    - **Minimális CPU-sebesség szükséges (MHz)** : Opcionálisan adja hozzá az alkalmazás telepítéséhez szükséges minimális CPU-sebesség.

3. Kattintson a **hozzáadása** megjelenítéséhez a **adjon hozzá egy olyan követelményszabályt** panelen, és további követelményszabályokat. Válassza ki a **követelmény típusa** , válassza ki a szabályt, amely segítségével határozza meg, hogyan érvényesítési követelmény. Követelmény szabályai fájl rendszer-információkat, a beállításjegyzék-értékek vagy a PowerShell-parancsfájlok alapulhat. 
    - **Fájl**: Ha úgy dönt **fájl** , a **követelmény típusa**, a követelményszabály észlelnie kell egy fájlhoz vagy mappához, dátuma, verziója vagy mérete. 
        - **Elérési út** – Az észlelendő fájlt vagy mappát tartalmazó mappa teljes elérési útja.
        - **Fájl vagy mappa** – Az észlelendő fájl vagy mappa.
        - **Vlastnost** – válassza ki a szabály az alkalmazás meglétének ellenőrzése.
        - **32 bites alkalmazással társítva 64 bites ügyfeleken** – Ha 64 bites ügyfeleken a „path” környezeti változókat 32 bites környezetben szeretné kibontani, válassza az **Igen** lehetőséget. A **Nem** (ez az alapértelmezett beállítás) kiválasztásakor a rendszer minden „path” változót 64 bites környezetben bontja ki a 64 bites ügyfeleken. A 32 bites ügyfelek mindig a 32 bites környezetet használják.
    - **Beállításjegyzék**: Ha úgy dönt **beállításjegyzék** , a **követelmény típusa**, a követelményszabály észlelnie kell egy beállításjegyzékbeli beállítás értékét, karakterlánc, egész szám vagy verzió alapján.
        - **Kulcs elérési útja** – Az észlelendő értéket tartalmazó beállításjegyzék-bejegyzés teljes elérési útja.
        - **Érték neve** – Az észlelendő beállításazonosító neve. Ha ez az érték üres, akkor az észlelés a kulcs alapján történik. A rendszer egy kulcs (alapértelmezett) értékét használja észlelési értékként, ha az észlelési módszer nem a fájl vagy a mappa meglétén alapul.
        - **Beállításjegyzék kulcsfontosságú követelmény az** – válassza ki a beállításjegyzékbeli kulcs összehasonlító határozza meg, hogyan történjen a szabály érvényesítése.
        - **32 bites alkalmazással társítva 64 bites ügyfeleken** – Ha a 32 bites beállításjegyzékben szeretne keresni a 64 bites ügyfeleken, válassza az **Igen** lehetőséget. A **Nem** (ez az alapértelmezett beállítás) kiválasztásakor a rendszer a 64 bites ügyfeleken a 64 bites beállításjegyzékben fog keresni. A 32 bites ügyfeleknél a keresés mindig a 32 bites beállításjegyzéket érinti.
    - **parancsfájl**: Válasszon **parancsfájl** , a **követelmény típusa**, amikor egy olyan követelményszabályt, a fájl, a beállításjegyzék vagy az Intune-konzolon elérhető más módon nem hozható létre.
        - **Parancsfájl** – a PowerShell-parancsprogram-alapú követelményi szabálynak, ha létezik kódja: 0, hogy észlelni fogja az STDOUT részletesebben. Ha például észlelni tudjuk STDOUT egész szám, amelynek értéke 1.
        - **32 bites folyamatként futtassa parancsprogramot 64 bites ügyfeleken** – ki **Igen** egy 32 bites folyamatban a parancsfájl futtatásához 64 bites ügyfeleken. Válassza ki **nem** (alapértelmezett), a parancsfájl futtatásához 64 bites folyamatként 64 bites ügyfeleken. 32 bites ügyfelek 32 bites folyamatként futtassa a szkriptet.
        - **Futtassa ezt a szkriptet a hitelesítő adatok használatával a bejelentkezett**: Válassza ki **Igen** a parancsfájl futtatásához az eszköz hitelesítő adatainak ** az aláírt használatával.
        - **Szkriptaláírás ellenőrzésének kényszerítése** – Az **Igen** lehetőség kiválasztásával ellenőrizheti, hogy a szkriptet egy megbízható gyártó írta-e alá, így a szkript figyelmeztetések és felszólítások megjelenítése nélkül fog futni. A szkript letiltás nélkül fog futni. A **Nem** (ez az alapértelmezett beállítás) kiválasztásakor a szkript végfelhasználói megerősítéssel, az aláírás ellenőrzése nélkül fut.
        - **Válassza ki a kimeneti adatok típusát**: Válassza ki az követelmény szabály egyezést meghatározása során használt.
4.  Amikor végzett, válassza az **OK** gombot.

### <a name="step-6-configure-app-detection-rules"></a>6\. lépés: Alkalmazás észlelési szabályok konfigurálása

1.  Az alkalmazás meglétének észleléséhez szükséges szabályok konfigurálásához az **Alkalmazás felvétele** panelen válassza az **Észlelési szabályok** elemet.
2.  A **Szabályok formátuma** mezőben adja meg, hogyan fogja észlelni a rendszer az alkalmazás meglétét. Választhatja az észlelési szabályok manuális konfigurálását, illetve egyéni szkriptet is használhat az alkalmazás meglétének észleléséhez. Legalább egy észlelési szabályt ki kell választani. 

    > [!NOTE]
    > Az **Észlelési szabályok** panelen, ha szeretne, több szabályt is hozzáadhat. Az alkalmazás észleléséhez az **összes** szabály feltételeinek teljesülnie kell.

    - **Észlelési szabályok manuális konfigurálása** – A következő szabálytípusok egyikét választhatja ki:
        1.  **MSI** – Jóváhagyás MSI-verzióellenőrzés alapján. Ezt a lehetőséget csak egyszer lehet hozzáadni. Ha ezt a szabálytípust választja, kétféle beállítás áll a rendelkezésére:
            - **MSI-termékkód** – Adjon meg egy érvényes MSI-termékkódot az alkalmazáshoz.
            - **MSI-termékverzió ellenőrzése** – Az **Igen** lehetőség kiválasztásával a rendszer az MSI-termékkód mellett az MSI-termékverziót is ellenőrzi.
        2.  **Fájl** – Ellenőrzés a fájl vagy mappa észlelése, dátuma, verziója vagy mérete alapján.
            - **Elérési út** – Az észlelendő fájlt vagy mappát tartalmazó mappa teljes elérési útja.
            - **Fájl vagy mappa** – Az észlelendő fájl vagy mappa.
            - **Észlelési módszer** – Válassza ki az alkalmazás meglétének ellenőrzéséhez használt észlelési módszer típusát.
            - **32 bites alkalmazással társítva 64 bites ügyfeleken** – Ha 64 bites ügyfeleken a „path” környezeti változókat 32 bites környezetben szeretné kibontani, válassza az **Igen** lehetőséget. A **Nem** (ez az alapértelmezett beállítás) kiválasztásakor a rendszer minden „path” változót 64 bites környezetben bontja ki a 64 bites ügyfeleken. A 32 bites ügyfelek mindig a 32 bites környezetet használják.
            
            **Példák a fájlalapú észlelésre**
            1.  Fájl meglétének ellenőrzése.
         
                ![Képernyőkép az észlelési szabály paneljéről – a fájl megléte](./media/apps-win32-app-03.png)
        
            2.  Mappa meglétének ellenőrzése.
         
                ![Képernyőkép az észlelési szabály paneljéről – a mappa megléte](./media/apps-win32-app-04.png)
        
        3. **Beállításjegyzék** – Ellenőrzés érték, sztring, egész szám vagy verzió alapján.
            - **Kulcs elérési útja** – Az észlelendő értéket tartalmazó beállításjegyzék-bejegyzés teljes elérési útja.
            - **Érték neve** – Az észlelendő beállításazonosító neve. Ha ez az érték üres, akkor az észlelés a kulcs alapján történik. A rendszer egy kulcs (alapértelmezett) értékét használja észlelési értékként, ha az észlelési módszer nem a fájl vagy a mappa meglétén alapul.
            - **Észlelési módszer** – Válassza ki az alkalmazás meglétének ellenőrzéséhez használt észlelési módszer típusát.
            - **32 bites alkalmazással társítva 64 bites ügyfeleken** – Ha a 32 bites beállításjegyzékben szeretne keresni a 64 bites ügyfeleken, válassza az **Igen** lehetőséget. A **Nem** (ez az alapértelmezett beállítás) kiválasztásakor a rendszer a 64 bites ügyfeleken a 64 bites beállításjegyzékben fog keresni. A 32 bites ügyfeleknél a keresés mindig a 32 bites beállításjegyzéket érinti.
            
            **Példák a beállításjegyzéken alapuló észlelésre**
            1.  A beállításkulcs meglétének ellenőrzése.
            
                ![Képernyőkép az észlelési szabály paneljéről – van beállításkulcs](./media/apps-win32-app-05.png)    
            
            2.  Ellenőrizze, hogy létezik-e beállításazonosítót.
        
                ![Képernyőkép az észlelési szabály paneljéről – van beállításazonosító](./media/apps-win32-app-06.png)    
        
            3.  A beállításazonosító sztring egyenlőségének ellenőrzése.
        
                ![Képernyőkép az észlelési szabály paneljéről – a beállításazonosító sztring egyenlő](./media/apps-win32-app-07.png)    
     
    - **Egyéni észlelési szkript alkalmazása** – Adja meg az alkalmazás észleléséhez használandó PowerShell-szkriptet. 
    
        1.  **Szkriptfájl** – Válasszon egy PowerShell-szkriptet, amely észleli majd az alkalmazás jelenlétét az ügyfélen. Az alkalmazást a rendszer akkor észleli, ha a szkript egy 0 értékű kilépési kódot ad vissza, és sztringértéket ír az STDOUT elembe.

        2.  **32 bites folyamatként futtassa parancsprogramot 64 bites ügyfeleken** – ki **Igen** egy 32 bites folyamatban a parancsfájl futtatásához 64 bites ügyfeleken. Válassza ki **nem** (alapértelmezett), a parancsfájl futtatásához 64 bites folyamatként 64 bites ügyfeleken. 32 bites ügyfelek 32 bites folyamatként futtassa a szkriptet.

        3.  **Szkriptaláírás ellenőrzésének kényszerítése** – Az **Igen** lehetőség kiválasztásával ellenőrizheti, hogy a szkriptet egy megbízható gyártó írta-e alá, így a szkript figyelmeztetések és felszólítások megjelenítése nélkül fog futni. A szkript letiltás nélkül fog futni. A **Nem** (ez az alapértelmezett beállítás) kiválasztásakor a szkript végfelhasználói megerősítéssel, az aláírás ellenőrzése nélkül fut.
    
            Intune-ügynök ellenőrzi az eredményeket a parancsfájlból. Beolvassa a szkript által a standard kimeneti (STDOUT) streambe írt értékeket, a standard hibastreamet (STDERR) és a kilépési kódot. Ha a szkript egyik értéke nem nulla, akkor a szkript futtatása meghiúsul, és az alkalmazásészlelési állapot nem települ. Ha a kilépési kód nulla, és az STDOUT elemben vannak adatok, akkor az alkalmazásészlelési állapot Telepítve lesz. 

            > [!NOTE]
            > A Microsoft javasolja, hogy a parancsfájl UTF-8 kódolást. Ha a szkript értéke 0, a végrehajtása sikeres volt. A második kimeneti csatorna alkalmazás észlelését jelzi – az STDOUT-adatok azt jelzik, hogy az alkalmazás megtalálható az ügyfélen. Most nem egy adott sztringet keresünk az STDOUT-ból.

        4.  Miután hozzáadta a szabály(ok)at, válassza ki a **Hozzáadás** > **OK** lehetőséget.

### <a name="step-7-configure-app-return-codes"></a>7\. lépés: Visszatérési kódok alkalmazás konfigurálása

1.  Az **Alkalmazás felvétele** panelen válassza a **Visszatérési kódok** lehetőséget az alkalmazástelepítés újrapróbálkozási viselkedését vagy a telepítés utáni viselkedést meghatározó visszatérési kódok hozzáadásához. A visszatérési kód bejegyzéseit a rendszer alapértelmezés szerint hozzáadja az alkalmazás létrehozása során. További visszatérési kódokat is megadhat, és a meglévőket is módosíthatja. 
2.  A **Visszatérési kódok** panelen adjon hozzá további visszatérési kódokat, vagy módosítsa a meglévőket.
    - **Nem sikerült** – a visszaadott érték, amely azt jelzi, hogy az alkalmazás telepítése nem sikerült.
    - **Hardveres újraindítás** – A hardveres újraindítás visszatérési kódja nem engedi meg, hogy a további Win32-alkalmazások újraindítás nélkül legyenek telepíthetők az ügyfélen. 
    - **Szoftveres újraindítás** – A szoftveres újraindítás visszatérési kódja lehetővé teszi, hogy a következő Win32-alkalmazás az ügyfél újraindítása nélkül telepíthető legyen. Az aktuális alkalmazás telepítésének befejezéséhez újraindításra van szükség.
    - **Újrapróbálkozás** – Az újrapróbálkozás visszatérési kód háromszor kísérli meg az alkalmazás telepítését. Az egyes kísérletek közötti 5 percet vár. 
    - **Sikeres** – Ez a visszaadott érték azt jelzi, hogy az alkalmazás telepítése sikeresen megtörtént.
3.  Válassza ki az **OK** lehetőséget, miután bővítette vagy módosította a visszatérési kódok listáját.

### <a name="step-8-add-the-app"></a>8\. lépés: Az alkalmazás hozzáadása

1.  Az **Alkalmazás hozzáadása** panelen ellenőrizze, hogy helyesen konfigurálta-e az alkalmazásadatokat.
2.  Az alkalmazást a **Hozzáadás** elem kiválasztásával töltheti fel az Intune-ba.

### <a name="step-9-assign-the-app"></a>9\. lépés: Az alkalmazás a hozzárendelése

1.  Az alkalmazás panelen válassza a **Hozzárendelések** elemet.
2.  Válassza a **Csoport hozzáadása** lehetőséget az alkalmazáshoz kapcsolódó **Csoport hozzáadása** ablaktábla megnyitásához.
3.  Az adott alkalmazáshoz válasszon egy **hozzárendelés-típust**:
    - **Regisztrált eszközök esetében elérhető**: Felhasználók telepítik az alkalmazást a céges portál alkalmazás vagy a céges portál webhelyen.
    - **Szükséges**: Az alkalmazás telepítve van a kiválasztott csoportok eszközeire.
    - **Távolítsa el**: Az alkalmazás eltávolítása a kiválasztott csoportokban található eszközökre.
4.  Válassza ki a **Tartalmazott csoportok** elemet, és rendelje hozzá a csoportokat, amelyek az alkalmazást fogják használni.
5.  Kattintson a **Hozzárendelés** ablaktáblán az **OK** gombra a belefoglalt csoportok kiválasztásának befejezéséhez.
6.  Ha ki szeretne zárni felhasználói csoportokat az alkalmazás-hozzárendelésből, válassza a **Csoportok kizárása** lehetőséget.
7.  A **Csoport hozzáadása** panelen kattintson az **OK** gombra.
8.  Az alkalmazás **Hozzárendelések** ablaktábláján kattintson a **Mentés** gombra.

Ezen a ponton végrehajtotta egy Win32-alkalmazás hozzáadása az Intune-hoz. Az alkalmazás-hozzárendeléssel és monitorozással kapcsolatos további információ: [Alkalmazások hozzárendelése csoportokhoz a Microsoft Intune-nal](https://docs.microsoft.com/intune/apps-deploy) és [Alkalmazásadatok és -hozzárendelések figyelése a Microsoft Intune-ban](https://docs.microsoft.com/intune/apps-monitor).

## <a name="app-dependencies"></a>Alkalmazás függőségei

Alkalmazás függőségei olyan alkalmazások, amelyek a Win32-alkalmazás telepítése előtt telepíteni kell. Megkövetelheti, hogy más alkalmazások telepíti a függőségeket. Pontosabban, az eszközön telepíteni kell a függő alkalmazás(ok) a Win32-alkalmazás telepítése előtt. Legfeljebb 100 függőségeket, beleértve a függőségeket bármely része van függőségeit, valamint az alkalmazás programkódját. A Win32-alkalmazás függőségei is hozzáadhat, csak a Win32-alkalmazás hozzáadása és az Intune-bA feltöltött után. A Win32-alkalmazás hozzáadása után látni fogja a **függőségek** lehetőséget a panelen, a Win32-alkalmazás. 

Ha egy alkalmazás függőség hozzáadása, kereshet az alkalmazás nevének és közzétevő alapján. Ezenkívül a hozzáadott függőségek az alkalmazás nevének és közzétevő alapján rendezheti. Korábban hozzáadott alkalmazás függőségei nem lehet kiválasztani a hozzáadva függőségi listáját. 

Lehetősége van-e minden függő alkalmazás automatikus telepítése. Alapértelmezés szerint a **automatikusan telepíteni** beállítás **Igen** az egyes függőségek. Automatikusan telepít egy függő alkalmazást, akkor is, ha a felhasználó vagy eszköz, nem vonatkozik a függő alkalmazást az Intune telepíti az alkalmazást az eszköz megfelel a függőséget a Win32-alkalmazás telepítése előtt. Fontos megjegyezni, hogy egy függőségi lehet rekurzív alárendelt függőségeket, és minden egyes alárendelt függőségi lesz telepítve, a fő függőség telepítése előtt. Emellett a függőségek telepítése hajtsa végre egy telepítési sorrendben egy adott függőségi szintjén.

Az alkalmazás függ, a Win32-alkalmazás hozzáadásához használja az alábbi lépéseket:

1. Válassza ki az Intune-ban **ügyfélalkalmazás** > **alkalmazások** hozzá ügyfélalkalmazások listájának megtekintése. 
2. Válasszon egy hozzáadott **Windows-alkalmazás (Win32)** alkalmazást. 
3. Válassza ki **függőségek** hozzáadása a függő alkalmazás(ok), a Win32-alkalmazás telepítése előtt telepíteni kell. 
4. Kattintson a **Hozzáadás** hozzáadása az alkalmazás függ.
5. Miután hozzáadta a függő alkalmazás(ok), kattintson a **kiválasztása**.
6. Döntse el, hogy automatikusan telepítse a függő alkalmazást kiválasztásával **Igen** vagy **nem** alatt **automatikusan telepíteni**.
7. Kattintson a **Save** (Mentés) gombra.

A felhasználó jelzi, hogy folyamatban van-e a függő alkalmazások Windows bejelentési értesítések jelennek meg letöltötte és telepítette a Win32-alkalmazás telepítési folyamat részeként. Emellett ha egy függő alkalmazás nincs telepítve, a végfelhasználó gyakran egyikét fogja találni a következő értesítéseket:
- 1 vagy több függő alkalmazások nem sikerült telepíteni
- nem teljesített alkalmazáskövetelmények 1 vagy több függő
- 1 vagy több függő alkalmazást egy eszköz-újraindítás függőben van

Ha nem **automatikusan telepíteni** függőség, a Win32-alkalmazás telepítése nem kísérelte meg. Ezenkívül alkalmazásjelentések jelennek meg, hogy a függőséget megjelölt volt `failed` is adja meg a hiba okát. A függőség telepítése sikertelen kattintva megtekintheti a Win 32 alkalmazásban megadott hiba (vagy figyelmeztetés) [telepítés részletei](troubleshoot-app-install.md#win32-app-installation-troubleshooting). 

Minden egyes függőségi felelnie a Intune Win32 alkalmazás újrapróbálkozási algoritmussal (3-szor telepítése 5 perc várakozás után próbálja meg) és a globális újraértékelésének ütemezését. Is függőségei alkalmazandók, csak a Win32-alkalmazás telepítése az eszközön időpontjában. Függőségek, amelyek nem alkalmazhatók a Win32-alkalmazás eltávolítása. Függőség törléséhez meg kell kattintson a három pontra (három ponttal jelölt) a bal oldalon, a függő alkalmazás a függőségi lista a sor végén található. 

## <a name="delivery-optimization"></a>Kézbesítésoptimalizálás

A Windows 10 1709-es és újabb ügyfelek letöltik egy kézbesítési optimalizálás összetevő használatával a Windows 10-es ügyfél Intune Win32 alkalmazás tartalma. Kézbesítésoptimalizálás társ-társ funkciókat biztosít, amelyek alapértelmezés szerint van kapcsolva. Kézbesítésoptimalizálás konfigurálható a csoportházirend és az Intune-eszközkonfiguráció keresztül. További információkért lásd: [kézbesítés optimalizálása Windows 10-es](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

## <a name="install-required-and-available-apps-on-devices"></a>Kötelező és elérhető alkalmazások telepítése az eszközökön

A felhasználó kötelező és elérhető alkalmazástelepítésekhez Windows bejelentési értesítések jelennek meg. Az alábbi képen a bejelentési értesítések egy példája látható, amely szerint az alkalmazás telepítésének befejezéséhez újra kell indítani az eszközt. 

![Képernyőfelvétel a Windows bejelentési értesítések egy alkalmazás telepítése](./media/apps-win32-app-08.png)    

Az alábbi képen tájékoztatja a végfelhasználót, hogy az eszköz alkalmazás változások történnek.

![Képernyőkép, amely az alkalmazás változásokra kerül sor a felhasználó értesítése](./media/apps-win32-app-09.png)    

## <a name="toast-notifications-for-win32-apps"></a>Bejelentési értesítések Win32-alkalmazások 
Ha szükséges, bemutató végfelhasználói bejelentési értesítések egy alkalmazás-hozzárendelés tilthatja le. Az Intune-ból, válassza ki a **ügyfélalkalmazás** > **alkalmazások** > Válassza ki az alkalmazást > **hozzárendelések** > **csoportokhozközétartozik**. 

> [!NOTE]
> Az Intune felügyeleti bővítmény Win32-alkalmazások nem lesz eltávolítva a nem regisztrált eszközökön telepítve van. A rendszergazdák kihasználhatják a hozzárendelés-kizárás nem ajánlja fel a BYOD-eszközök Win32-alkalmazások.

## <a name="troubleshoot-win32-app-issues"></a>A Win32-alkalmazások hibáinak elhárítása
Az ügynöknaplók általában a következő helyen érhetők el az ügyfélgépen: `C:\ProgramData\Microsoft\IntuneManagementExtension\Logs`. A `CMTrace.exe` segítségével megtekintheti ezeket a naplófájlokat. *CMTrace.exe* letölthető [Configuration Manager Client Tools](https://docs.microsoft.com/sccm/core/support/tools). 

![Képernyőkép az ügynököt a naplók az ügyfélszámítógépen](./media/apps-win32-app-10.png)    

> [!IMPORTANT]
> Ahhoz, hogy a megfelelő telepítéséhez és futtatásához a LOB-Win32-alkalmazások, a kártevőirtó-beállítások a következő könyvtárait kizárása kell éppen beolvasott:<p>
> **A X64 ügyfélgépek**:<br>
> *C:\Program Files (x86)\Microsoft Intune Management Extension\Content*<br>
> *C:\windows\IMECache*
>  
> **A X86 ügyfélgépek**:<br>
> *C:\Program Files\Microsoft Intune Management Extension\Content*<br>
> *C:\windows\IMECache*

### <a name="detecting-the-win32-app-file-version-using-powershell"></a>Annak ellenőrzése, PowerShell-lel Win32-alkalmazás fájl verziója

Ha nehézséget jelent a Win32-alkalmazás fájlverziót észlelése, vegye figyelembe a használatával, vagy módosítsa a következő PowerShell-parancsot:

``` PowerShell

$FileVersion = [System.Diagnostics.FileVersionInfo]::GetVersionInfo("<path to binary file>").FileVersion
#The below line trims the spaces before and after the version name
$FileVersion = $FileVersion.Trim();
if ("<file version of successfully detected file>" -eq $FileVersion)
{
#Write the version to STDOUT by default
$FileVersion
exit 0
}
else
{
#Exit with non-zero failure code
exit 1
}

```
A PowerShell a fenti parancsban cserélje le a `<path to binary file>` a Win32-alkalmazás fájl elérési útját karakterlánc. Egy példa az elérési útra a következőhöz hasonló lesz:<br>
`C:\Program Files (x86)\Microsoft SQL Server Management Studio 18\Common7\IDE\ssms.exe`

Továbbá cserélje le a `<file version of successfully detected file>` karakterlánc, amely észlelni kell a fájl verziója. Egy példa fájlt verzió-karakterláncnak a következő lesz a következőhöz hasonló:<br>
`2019.0150.18118.00 ((SSMS_Rel).190420-0019)`

Ha szeretné megszerezni a, a Win32-alkalmazás, használhatja a következő PowerShell-parancsot:

``` PowerShell

[System.Diagnostics.FileVersionInfo]::GetVersionInfo("<path to binary file>").FileVersion

```

Cserélje le a fenti PowerShell-parancs `<path to binary file>` a fájl elérési útjára.

### <a name="additional-troubleshooting-areas-to-consider"></a>További hibaelhárítási területeket megfontolandó szempontok
- Ellenőrizze a célcsoportkezelést, és győződjön meg arról, hogy az ügynök telepítve van az eszközön – egy olyan Win32-alkalmazás vagy PowerShell-szkript, amelynek csoport a célzottja, ügynöktelepítési szabályzatot hoz létre a biztonsági csoporthoz.
- Ellenőrizze az operációs rendszer verzióját – 1607-es vagy annál újabb Windows 10-re van szükség.  
- Ellenőrizze a Windows 10 termékváltozatát – a Windows 10 S és az S módban futó Windows-verziók nem támogatják az MSI-telepítést.

Win32-alkalmazások hibaelhárításával kapcsolatos további információkért lásd: [Win32 alkalmazás telepítési hibák elhárítása](troubleshoot-app-install.md#win32-app-installation-troubleshooting).

## <a name="next-steps"></a>További lépések

- További információk az alkalmazások Intune-hoz való hozzáadásáról: [Alkalmazások hozzáadása a Microsoft Intune-hoz](apps-add.md).

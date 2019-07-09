---
title: Office 365-alkalmazások hozzárendelése Windows 10-eszközök Microsoft Intune-nal
titleSuffix: ''
description: Ismerje meg, hogyan használhatja a Microsoft Intune Windows 10 rendszerű eszközökön Office 365-alkalmazások telepítéséhez.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 00712b891790fbf437e9fed024f7610f37fee129
ms.sourcegitcommit: 1b7ee2164ac9490df4efa83c5479344622c181b5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/08/2019
ms.locfileid: "67648701"
---
# <a name="assign-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>Office 365-alkalmazások hozzárendelése Windows 10-es eszközökhöz a Microsoft Intune-nal

Az alkalmazások hozzárendelése, figyelése, konfigurálása és védelme előtt hozzá kell adnia őket az Intune-hoz. Az elérhető egyik [alkalmazástípusok](apps-add.md#app-types-in-microsoft-intune) van Office 365-alkalmazások Windows 10 rendszerű eszközökhöz. Ha ez az alkalmazástípus az Intune-ban, rendelje hozzá, és az Office 365-alkalmazások telepítése Windows 10 rendszerű kezelt eszközökhöz. Rendelje hozzá is, és telepítse a Microsoft Project Online asztali ügyfele és a Microsoft Visio Online 2. csomagját, alkalmazásai, ha a hozzájuk való saját licencekkel. Elérhető Office 365-alkalmazások listájában, az Intune-konzol Azure-ban egyetlen bejegyzésként jelennek meg.

> [!NOTE]
> Office 365 ProPlus-licencekkel kell aktiválnia a Microsoft Intune-on keresztül üzembe helyezett Office 365 ProPlus-alkalmazásokat. Jelenleg az Intune nem támogatja az Office 365 Business Edition kiadását.

## <a name="before-you-start"></a>Előkészületek

> [!IMPORTANT]
> Ha a végfelhasználói eszközön .msi Office-alkalmazások találhatók, azokat az **MSI eltávolítása** szolgáltatással biztonságosan el kell távolítani. Ellenkező esetben az Intune által biztosított Office 365-alkalmazások telepítése sikertelen lesz.

- Azokon az eszközökön, melyekre telepíti az alkalmazásokat, a Windows 10 alkotói frissítésének vagy újabb verziójának kell futnia.
- Az Intune csak az Office 365 csomagból származó Office-alkalmazások hozzáadását támogatja.
- Ha bármely Office-alkalmazás meg van nyitva, amikor az Intune telepíti az alkalmazáscsomagot, előfordulhat, hogy a telepítés sikertelen lesz, és elvesznek a végfelhasználók adatai a nem mentett fájlokból.
- Ez a telepítési mód nincs támogatva Windows 10 S, Windows Home, Windows Team, Windows Holographic és Windows Holographic for Business rendszert futtató eszközökön.
- Az Intune nem támogatja az asztali Office 365-programok (más néven az Office Centennial-alkalmazások) Microsoft Áruházból történő telepítését olyan eszközök esetében, amelyekre korábban már telepítettek valamilyen Office 365-alkalmazást az Intune segítségével. Ha ezt a konfigurációt telepíti, az adatvesztést vagy adatsérülést okozhat.
- Több kötelező vagy elérhető alkalmazás-hozzárendelés nem adódik össze. A későbbi alkalmazás-hozzárendelés felülírja a már meglévő alkalmazás-hozzárendeléseket. Ha például az első Office-alkalmazáscsomag tartalmazta a Wordöt, de az újabb már nem, akkor a Word el lesz távolítva. Ez a feltétel a Visio- és Project-alkalmazásokra nem vonatkozik.
- A Mutiple Office 365-telepítések jelenleg nem támogatottak. Az eszköz csak egy üzemelő példánynak lesz elküldve
- **Office-verzió**: - Itt választhatja ki, hogy az Office 32 bites vagy 64 bites verzióját szeretné hozzárendelni. A 32 bites verziót 32 bites és 64 bites eszközökön is, a 64 bites verziót viszont csak 64 bites eszközökön telepítheti.
- **MSI eltávolítása a végfelhasználói eszközökről** – Itt választhatja ki, hogy eltávolítja-e a már meglévő Office .MSI-alkalmazásokat a végfelhasználói eszközökről. A telepítés nem lesz sikeres, ha a végfelhasználói eszközökön már meglévő .MSI-alkalmazások vannak. Az eltávolítás nem korlátozódik az **Alkalmazáscsomag konfigurálásánál** telepítésre kiválasztott alkalmazásokra, mert minden Office (MSI) alkalmazást eltávolít a végfelhasználói eszközről. További információkért lásd: [Az Office már meglévő MSI-verzióinak eltávolítása az Office 365 ProPlusra való frissítés esetén](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). Amikor az Intune újratelepíti a végfelhasználói gépekre az Office-t, a végfelhasználók automatikusan ugyanazokat a nyelvi csomagokat kapják meg, mint az előző .MSI-alapú Office-telepítésnél.

## <a name="get-started"></a>Bevezetés

1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Az **Intune** ablaktáblán válassza az **Ügyfélalkalmazások** lehetőséget.
4. Az **Ügyfélalkalmazások** tevékenységprofil panelén a **Kezelés** szakaszban válassza az **Alkalmazások** lehetőséget.
5. Válassza a **Hozzáadás** lehetőséget.
6. Az **Alkalmazások hozzáadása** ablaktáblán, az **Alkalmazástípus** listában, az **Office 365 csomag** alatt válassza a **Windows 10** lehetőséget.

## <a name="select-settings-format"></a>Válassza ki a beállítások formátuma

Alkalmazás-beállítás konfigurálásával kiválasztásával módszert választhat egy **beállítások formátuma**. A beállítás formátum lehetőségek a következők:
- Konfigurációtervező
- XML-adatok megadása

Ha úgy dönt **Configuration designer** a **alkalmazás hozzáadása** panelen két további beállítás lehetőséget kínálnak változik:
- Alkalmazáscsomag konfigurálása
- Alkalmazáscsomag beállításai

<img alt="Add Office 365 - Configuration designer" src="./media/apps-add-office365/apps-add-office365-02.png" width="700">

Ha úgy dönt **XML adatok megadása** a **alkalmazás hozzáadása** megjelenített panelről a **XML adatok megadása** lehetőséget. Válassza ezt a megjelenítendő a **konfigurációs fájl** panelen. 

![Adja hozzá az Office 365 konfigurációtervező](./media/apps-add-office365/apps-add-office365-01.png)
    
További információ a **XML adatok megadása** talál [XML adatok megadása](apps-add-office365.md#enter-xml-format) alatt.

## <a name="configure-app-suite-information"></a>Alkalmazáscsomag adatai konfigurálása

Ebben a lépésben adhatja meg az alkalmazáscsomag adatait. Ezek alapján azonosíthatja az alkalmazáscsomagot az Intune-ban, és a felhasználók is ezek alapján találhatják meg azt a céges portálon.

1. Az **Alkalmazás hozzáadása** ablaktáblán válassza az **Alkalmazáscsomag adatai** lehetőséget.
2. Az **Alkalmazáscsomag adatai** ablaktáblán tegye a következőket:
    - **Csomag neve**: Adja meg az alkalmazáscsomag nevét, a vállalati portálon megjelenített formában. Ügyeljen arra, hogy minden megadott csomagnév egyedi legyen. Ha ugyanazt a csomagnevet kétszer adja meg, csak az egyik alkalmazás fog megjelenni a felhasználók számára a céges portálon.
    - **Csomag leírása**: Adja meg az alkalmazáscsomag leírását. Felsorolhatja például a kiválasztott belefoglalt alkalmazásokat.
    - **Közzétevő**: A Microsoft a közzétevő jelenik meg.
    - **Kategória**: Kiválaszthat egy vagy több, a beépített Alkalmazáskategóriák vagy egy létrehozott kategóriát is. Ez a beállítás megkönnyíti a Céges portálon kereső felhasználóknak az alkalmazás megtalálását.
    - **Megjelenítés kiemelt alkalmazásként a céges portálon**: Válassza ki ezt a beállítást, az alkalmazáscsomag hangsúlyosan jelenítheti fő lapján, a céges portál főoldalán alkalmazásokat kereső felhasználók számára.
    - **Információs URL-cím**: Nem kötelező: megadhatja az alkalmazással kapcsolatos információkat tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Adatvédelmi URL-címe**: Nem kötelező: megadhatja az alkalmazás adatvédelmi nyilatkozatát tartalmazó webhely URL-címét. Ez az URL-cím jelenik meg a felhasználók számára a céges portálon.
    - **Fejlesztői**: Fejlesztőként a Microsoft jelenik meg.
    - **Tulajdonos**: Tulajdonosként a Microsoft jelenik meg.
    - **Megjegyzések**: Adja meg az alkalmazáshoz társítani kívánt megjegyzéseket.
    - **Embléma**: Az Office 365-embléma akkor jelenik meg az alkalmazás a céges portálon böngésző felhasználók számára.
3. Kattintson az **OK** gombra.

## <a name="configure-app-suite"></a>Alkalmazáscsomag konfigurálása

Ha bejelölte a **Configuration designer** lehetőség a **szabályzatbeállítás** legördülő listából, látni fogja a **alkalmazáscsomag konfigurálása** beállítást a **hozzáadása alkalmazás** panelen. Válassza ki azokat az Office-alkalmazásokat, melyeket szeretne eszközökhöz hozzárendelni.

1. Az **Alkalmazás felvétele** ablaktáblán válassza az **Alkalmazáscsomag konfigurálása** lehetőséget.
2. Az **Alkalmazáscsomag konfigurálása** ablaktáblán válassza ki a szokásos Office-alkalmazásokat, melyeket szeretne eszközökhöz hozzárendelni.  
    Emellett telepíthet alkalmazásokat a Microsoft Project Online asztali ügyfele és a Microsoft Visio Online 2. csomagját, ha hozzájuk való saját licencekkel.
3. Kattintson az **OK** gombra.

## <a name="configure-app-suite-settings"></a>Suite beállításainak konfigurálása

Ha bejelölte a **Configuration designer** lehetőség a **szabályzatbeállítás** legördülő listából, látni fogja a **Alkalmazásbeállítások Suite** beállítást a **alkalmazás hozzáadása**  panelen. Ebben a lépésben az alkalmazáscsomag telepítési beállításait konfigurálhatja. A beállítások minden, a csomaghoz hozzáadott alkalmazásra vonatkoznak.

1. Az **Alkalmazás hozzáadása** ablaktáblán válassza az **Alkalmazáscsomag beállításai** lehetőséget.
2. Az **Alkalmazáscsomag beállításai** ablaktáblán tegye a következőket:
    - **Office-verzió**: Válassza ki, hogy szeretné-e hozzárendelése az Office 32 bites vagy 64 bites verzióját. A 32 bites verziót 32 bites és 64 bites eszközökön is, a 64 bites verziót viszont csak 64 bites eszközökön telepítheti.
    - **Frissítési csatorna**: Válassza ki, hogyan Office frissítése az eszközökön. A különböző frissítési csatornákkal kapcsolatban az [Office 365 ProPlus frissítési csatornáinak áttekintése](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus) című témakörben találhat további információt. A következő lehetőségek közül választhat:
        - **Havonta**
        - **Havonta (megcélzott)**
        - **Semi-Annual**
        - **Féléves (megcélzott)**

        A csatorna kiválasztása után igény szerint kattinthat az **Adott** elemre az Office adott verziójának telepítéséhez a végfelhasználói eszközök kiválasztott csatornáján. Ekkor kiválaszthatja az Office **adott verzióját** a használathoz.
        
        Az elérhető verziók idővel változni fognak. Ezért egy új központi telepítés létrehozásakor újabb verziók válhatnak elérhetővé, és előfordulhat, hogy egyes régebbi verziók már nem érhetők el. A jelenleg üzemelő példányok továbbra is a régebbi verziót telepítik, de a verziólista csatornánként folyamatosan frissül.
        
        A rögzített verziót (vagy bármely tulajdonságot) frissítő és lehetőség szerint üzembe helyezett eszközök esetén, ha azokon az előző verziót telepítették, az állapotjelentés az eszköz bejelentkezéséig a Telepítve állapotot mutatja. Amikor az eszköz bejelentkezik, az állapot ideiglenesen Ismeretlenre vált, de ez a felhasználó számára nem látható. Amikor a felhasználó kezdeményezi az újabb elérhető verzió telepítését, látni fogja, hogy az állapot Telepítettre változott.
        
        További információkért lásd: [Az Office 365 ProPlus frissítési csatornáinak áttekintése](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

    - **MSI eltávolítása a végfelhasználói eszközökről** – Itt választhatja ki, hogy eltávolítja-e a már meglévő Office .MSI-alkalmazásokat a végfelhasználói eszközökről. A telepítés nem lesz sikeres, ha a végfelhasználói eszközökön már meglévő .MSI-alkalmazások vannak. Az eltávolítás nem korlátozódik az **Alkalmazáscsomag konfigurálásánál** telepítésre kiválasztott alkalmazásokra, mert minden Office (MSI) alkalmazást eltávolít a végfelhasználói eszközről. További információkért lásd: [Az Office már meglévő MSI-verzióinak eltávolítása az Office 365 ProPlusra való frissítés esetén](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). Amikor az Intune újratelepíti a végfelhasználói gépekre az Office-t, a végfelhasználók automatikusan ugyanazokat a nyelvi csomagokat kapják meg, mint az előző .MSI-alapú Office-telepítésnél. 
    - **Automatikusan fogadja el az alkalmazás végfelhasználói licencszerződés**: Válassza ezt a lehetőséget, ha nincs szüksége a végfelhasználók számára, hogy fogadja el a licencszerződést. Ebben az esetben az Intune automatikusan elfogadja a szerződést.
    - **Megosztott aktiválás használata**: Akkor válassza ezt a beállítást, ha több felhasználó ugyanazt a számítógépet. További információ: [Az Office 365 megosztott aktiválásának áttekintése](https://docs.microsoft.com/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus).
    - **Nyelvek**: Az Office automatikusan települ, a támogatott nyelveket, Windows, a végfelhasználói eszközön telepített egyikében. Ezt a beállítást akkor jelölje be, ha az alkalmazáscsomaghoz további nyelveket szeretne telepíteni. <p></p>
    További nyelveket helyezhet üzembe az Intune által felügyelt Office 365 Pro Plus-alkalmazások számára. Az elérhető nyelvek listája tartalmazza a nyelvi csomag **Típusát** (alap, részleges vagy nyelvi ellenőrzési) is. Az Azure Portalon válassza a **Microsoft Intune** > **Ügyfélalkalmazások** > **Alkalmazások** > **Hozzáadás** lehetőséget. Az **Alkalmazás hozzáadása** panelen, az **Alkalmazástípusok** listáján, válassza az **Office 365 csomag** alatti **Windows 10** lehetőséget. Az **Alkalmazáscsomag beállításai** panelen válassza a **Nyelvek** lehetőséget. További információkért lásd [a nyelvek az Office 365 ProPlusban történő üzembe helyezésének áttekintését](https://docs.microsoft.com/deployoffice/overview-of-deploying-languages-in-office-365-proplus).

## <a name="select-scope-tags-optional"></a>Válassza ki a hatókörcímkék (nem kötelező)
Hatókörcímkék segítségével határozza meg, ki láthatja az alkalmazás ügyféladatokat az Intune-ban. Hatókörcímkék teljes kapcsolatban lásd: [szerepköralapú hozzáférés-vezérléshez és a hatókör címkék használata elosztott informatikai](scope-tags.md).

1. Válassza ki **hatókör (címkék)**  > **hozzáadása**.
2. Használja a **kiválasztása** mező használatával keresheti meg hatókörcímkék.
3. Válassza ki az ehhez az alkalmazáshoz hozzárendelni kívánt hatókörcímkék melletti jelölőnégyzetet.
4. Válassza a **Kiválasztás** > **OK** lehetőséget.

## <a name="enter-xml-format"></a>Adja meg az XML-formátuma

Ha bejelölte a **XML adatok megadása** lehetőség a **szabályzatbeállítás** legördülő listából, látni fogja a **adja meg az XML-formátuma** beállítást a **alkalmazáshozzáadása**panelen. További információkért lásd: [beállítási lehetőségei az Office-telepítő eszköz](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

## <a name="finish-up"></a>Befejezés

Amikor elkészült, válassza az **Alkalmazás hozzáadása** ablaktáblán a **Hozzáadás** lehetőséget. A létrehozott alkalmazás megjelenik az alkalmazáslistában.

## <a name="troubleshooting"></a>Hibaelhárítás
Az Intune használja a [Office-telepítő eszköz](https://docs.microsoft.com/DeployOffice/overview-of-the-office-2016-deployment-tool) letöltéséhez és az ügyfél számítógépekre, az Office 365 ProPlus üzembe helyezése a [Office 365 CDN](https://docs.microsoft.com/office365/enterprise/content-delivery-networks). Hivatkozási leírt ajánlott eljárások [végpontok kezelése az Office 365](https://docs.microsoft.com/office365/enterprise/managing-office-365-endpoints) győződjön meg arról, hogy a hálózati konfiguráció lehetővé teszi a ügyfelek hozzáférhetnek a CDN-t közvetlenül ahelyett, hogy a CDN útválasztási adatforgalom keresztül központi proxyk elkerülése érdekében Bemutatkozik a szükségtelen késés.

Futtassa a [Support és az Office 365-höz Segéd helyreállítási](https://diagnostics.office.com) a céleszközön, ha telepítés vagy a futásidejű hibák.

## <a name="errors-during-installation-of-the-app-suite"></a>Hiba történt az alkalmazáscsomag telepítésekor

Lásd: [Office 365 ProPlus ULS-naplózás engedélyezése](https://blogs.technet.microsoft.com/odsupport/2018/06/18/how-to-enable-office-365-proplus-uls-logging) információ részletes telepítési naplók megtekintése.

Az alábbi táblázatban az esetlegesen megjelenő gyakori hibakódok és azok jelentése található.

### <a name="status-for-office-csp"></a>Az Office felhőszolgáltatójának állapota

| Állapot | Fázis | Leírás |
|--------------------------------------------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1460 (ERROR_TIMEOUT) | Letöltés | Nem sikerült letölteni az Office-telepítő eszközt |
| 13 (ERROR_INVALID_DATA) | - | Nem sikerült ellenőrizni a letöltött Office-telepítő eszköz aláírását |
| A CertVerifyCertificateChainPolicy függvény által visszaadott hibakód | - | Nem sikerült a letöltött Office-telepítő eszköz hitelesítési ellenőrzése |
| 997 | WIP | Telepítés |
| 0 | Telepítés után | A telepítés sikeres volt |
| 1603 (ERROR_INSTALL_FAILURE) | - | Nem sikerült egy előfeltétel ellenőrzése, például: SxS (kísérlet telepítésekor 2016 MSI telepítése) verzió mismatchOthers |
| 0x8000ffff (E_UNEXPECTED) | - | Kísérlet történt az eltávolításra, miközben a számítógépen nem található meg az Office Kattintásra szolgáltatás |
| 17002 | - | Nem sikerült befejezni a forgatókönyv végrehajtását (telepítés). Lehetséges okok: a telepítés során installationUnknown nyelvi azonosító egy másik installationOut lemezterület megszakította userInstallation megszakítva |
| 17004 | - | Ismeretlen termékváltozatok |


### <a name="office-deployment-tool-error-codes"></a>Az Office-telepítő eszköz hibakódjai

| Forgatókönyv | Visszatérési kód | Felhasználói felület | Megjegyzés |
|------------------------------------------------------------------------------------------------------------------|---------------------------------------|----------------------------------------------------|------------------------------------|
| Kísérlet történt az eltávolításra, miközben nincs aktív Kattintásra-telepítés | -2147418113, 0x8000ffff vagy 2147549183 | Hibakód: 30088-1008Error kódja: 30125-1011 (404) | Office-telepítő eszköz |
| Telepítés, miközben telepítve van az MSI-verzió | 1603 | - | Office-telepítő eszköz |
| A felhasználó vagy egy másik telepítés megszakította a telepítést | 17002 | - | Kattintásra |
| Kísérlet a 64 bites verzió telepítésére egy olyan eszközön, amelyen telepítve van a 32 bites verzió. | 1603 | - | Az Office-telepítő eszköz visszatérési kódja |
| Kísérlet egy ismeretlen termékváltozat telepítésére (az Office-felhőszolgáltató esetében ez nem valós használati eset, mivel csak érvényes termékváltozatokat lehet beküldeni) | 17004 | - | Kattintásra |
| Nincs elegendő szabad terület | 17002 | - | Kattintásra |
| Nem sikerült elindítani a Kattintásra-ügyfelet (váratlan) | 17000 | - | Kattintásra |
| A Kattintásra-ügyfélnek nem sikerült várólistára helyeznie a forgatókönyvet (váratlan) | 17001 | - | Kattintásra |

## <a name="next-steps"></a>További lépések

- Az alkalmazásoknak a választott csoportokhoz való hozzárendeléséhez tekintse meg az [Alkalmazások hozzárendelése csoportokhoz](/intune-azure/manage-apps/deploy-apps) című cikket.

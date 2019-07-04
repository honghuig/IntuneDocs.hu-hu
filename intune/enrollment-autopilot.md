---
title: Eszközök regisztrálása a Windows AutoPilot használatával
titleSuffix: Microsoft Intune
description: Útmutató a Windows 10-eszközök Windows AutoPilot használatával történő regisztrálásához.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/5/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8144acb25c1ef13f7f2ed5c7deac5eb679639111
ms.sourcegitcommit: 95f32e381d14f0a75465b6103af2665fccb2de16
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539041"
---
# <a name="enroll-windows-devices-in-intune-by-using-the-windows-autopilot"></a>Windows-eszközök regisztrálása az Intune-ban a Windows Autopilot használatával  
A Windows Autopilot egyszerűbbé teszi az eszközök regisztrálását az Intune-ban. A testre szabott operációsrendszer-lemezképek létrehozása és karbantartása sok időt vesz igénybe. Gyakran ezeknek az egyéni operációsrendszer-lemezképeknek az új eszközökre való alkalmazásával is időt kell töltenie, hogy felkészítse az eszközöket a használatra, mielőtt a végfelhasználóknak adná azokat. A Microsoft Intune és az AutoPilot révén új eszközöket adhat hozzá a végfelhasználók számára anélkül, hogy egyéni operációsrendszer-lemezképek létrehozására, kezelésére és az eszközökre való alkalmazására lenne szükség. Az AutoPilot-eszközök Intune-nal való felügyelete során a regisztráció után szabályzatokat, profilokat, alkalmazásokat és sok mást is kezelni tud. A megoldás előnyeinek, használati eseteinek és előfeltételeinek áttekintéséről lásd [a Windows AutoPilot áttekintését](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).


## <a name="prerequisites"></a>Előfeltételek
- [Intune-előfizetés](licenses.md)
- [Engedélyezni kell a Windowsos eszközök automatikus regisztrációját](windows-enroll.md#enable-windows-10-automatic-enrollment)
- [Az Azure Active Directory Premium előfizetéssel](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="how-to-get-the-csv-for-import-in-intune"></a>A fürt megosztott kötetei szolgáltatás beszerzése az importáláshoz az Intune-ban

További témakörben találhat további információt tekintse meg a powershell-parancsmag ismertetése.

- [Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo/1.3/Content/Get-WindowsAutoPilotInfo.ps1)

## <a name="add-devices"></a>Eszközök felvétele

A Windows AutoPilot-eszközök felvételéhez importálhat egy CSV-fájlt az adataikkal.

1. Az [Azure Portalbeli Intune-ban](https://aka.ms/intuneportal) válassza az **Eszközök regisztrálása** > **Windows-regisztráció** > **Eszközök** > **Importálás** elemet.

    ![A Windows AutoPilot-eszközök képernyőképe](media/enrollment-autopilot/autopilot-import-device.png)

2. A **Windows AutoPilot-eszközök hozzáadása** alatt keresse meg a hozzáadni kívánt eszközöket felsoroló CSV-fájlt. A CSV-fájl szerepelnie kell a sorozatszámokat, Windows Termékazonosítói, hardver-kivonatok és opcionális csoport címkék. Legfeljebb 500 sor lehet a listában. Használja a fejlécet és a sor formátuma alább látható:

    `Device Serial Number,Windows Product ID,Hardware Hash,Group Tag`</br>
    `<serialNumber>,<ProductID>,<hardwareHash>,<optionalGroupTag>`

    ![A Windows AutoPilot-eszközök hozzáadásának képernyőképe](media/enrollment-autopilot/autopilot-import-device2.png)

3. Válassza az **Importálás** lehetőséget az eszközadatok importálásának elindításához. Az importálás több percig is eltarthat.

4. Az importálás befejezése után válassza az **Eszközök regisztrálása** > **Windows-regisztráció** > **Windows AutoPilot** > **Eszközök** > **Szinkronizálás** lehetőséget. Egy üzenet jelenik meg, hogy a szinkronizálás folyamatban van. Nagyszámú eszköz szinkronizálása esetén előfordulhat, hogy várnia kell pár percet, amíg a folyamat befejeződik.

5. Frissítse a nézetet az új eszközök megjelenítéséhez.

## <a name="create-an-autopilot-device-group"></a>AutoPilot-eszközcsoport létrehozása

1. Az [Azure Portalbeli Intune-ban](https://aka.ms/intuneportal) válassza a **Csoportok** > **Új csoport** elemet.
2. A **Csoport** panelen:
    1. A **Csoport típusa** beállításnál válassza a **Biztonsági** lehetőséget.
    2. Gépelje be a **Csoport nevét** és a **Csoport leírását**.
    3. A **Tagság típusa** beállításnál válassza a **Hozzárendelt** vagy a **Dinamikus eszköz** lehetőséget.
3. Ha a **Tagság típusa** beállításnál az előző lépésben a **Hozzárendelt** értéket választotta, akkor válassza a **Csoport** panel **Tagok** elemét, és adjon hozzá AutoPilot-eszközöket a csoporthoz.
    A még nem regisztrált AutoPilot-eszközök olyan eszközök, amelyek neve megegyezik az eszköz sorozatszámával.
4. Ha a **Tagság típusa** alatt a **Dinamikus eszköz** lehetőséget választotta, akkor válassza a **Csoport** panel **Dinamikus eszköz tagok** lehetőségét, és gépelje be az alábbi kódok bármelyikét a **Speciális szabály** mezőbe.
    - Ha azt szeretné, hozzon létre egy csoportot, amely tartalmazza az Autopilot-eszközök összes, írja be: `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - Az OrderID attribútumot az Azure AD-eszközök az Intune csoporthoz címke mezőbe képezi le. Ha azt szeretné, hozzon létre egy csoportot, amely tartalmazza az Autopilot-eszközök egy adott csoport tag(OrderID) az összes, a következő szempontokat kell megadnia: `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`
    - Ha létre kíván hozni egy csoportot, amely az egy adott beszerzési rendelési azonosítóval rendelkező összes Autopilot-eszközét tartalmazza, írja be a következőt: `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    A **Speciális szabály** kódjának megadása után válassza a **Mentés** lehetőséget.
5. Válassza a **Létrehozás** lehetőséget.  

## <a name="create-an-autopilot-deployment-profile"></a>AutoPilot üzembehelyezési profil létrehozása
Az Autopilot-üzembehelyezési profilokkal Autopilot-eszközeit konfigurálhatja.
1. Az [Azure Portalbeli Intune-ban](https://aka.ms/intuneportal) válassza az **Eszközök regisztrálása** > **Windows-regisztráció** > **Telepítési profilok** > **Profil létrehozása** elemet.
2. Az a **alapjai** írja be a **neve** és választható **leírása**.

    ![Képernyőkép az alapvető beállítások lap](media/enrollment-autopilot/create-profile-basics.png)

3. Ha azt szeretné, hogy a hozzárendelt csoportokban lévő minden eszköz automatikusan átálljon az AutoPilotra, állítsa a **Minden megcélzott eszköz AutoPilot-eszközzé alakítása** beállítást **Igen** értékre. A hozzárendelt csoportokban lévő nem AutoPilot-eszközök az AutoPilot üzembehelyezési szolgáltatással regisztrálnak. A regisztráció feldolgozása 48 órát is igénybe vehet. Az eszköz regisztrációjának törlése és alaphelyzetbe állítása után az Autopilot regisztrálja az eszközt. Miután ilyen módon regisztrál egy eszközt, a beállítás letiltása vagy a profil-hozzárendelés eltávolítása nem távolítja el az eszközt az Autopilot üzembehelyezési szolgáltatásból. Ehhez [közvetlenül kell törölnie az eszközt](enrollment-autopilot.md#delete-autopilot-devices).
4. Kattintson a **Tovább** gombra.
5. Az a **Out-of-box élmény (OOBE)** lapon a **üzembe helyezési mód**, válasszon egyet az alábbi két lehetőség közül választhat:
    - **Felhasználó-központú**: Az ilyen profillal rendelkező eszközök az őket regisztráló felhasználóhoz vannak társítva. Az eszköz regisztrálásához felhasználói hitelesítő adatokra van szükség.
    - **Helyi üzembe helyezése (előzetes verzió)** : (a Windows 10-es, 1809 vagy újabb verzió szükséges) a profilt használó eszközök nem kapcsolódnak a felhasználó regisztrálja az eszközt. Az eszköz telepítéséhez nincs szükség felhasználói hitelesítő adatokra.

    ![Képernyőkép a Kezdőélmény lap](media/enrollment-autopilot/create-profile-outofbox.png)

6. A **Csatlakozás az Azure AD-hez mint** mezőben válassza az **Azure AD-hez csatlakoztatott** lehetőséget.
7. Adja meg az alábbi lehetőségeket:
    - **Végfelhasználói licencszerződés (EULA)** : (Windows 10 1709-es vagy újabb verzió) Válassza ki, hogy szeretné-e a végfelhasználói licencszerződés megjelenjen a felhasználók számára.
    - **Adatvédelmi beállítások**: Válassza ki, hogy szeretné-e az adatvédelmi beállítások megjelenjenek a felhasználók számára.
    >[!IMPORTANT]
    >Az Autopilot központi telepítése a Windows 10-es verziójú 1903 eszközök és újabb verziók esetén a diagnosztikai adatok alapértelmezett értéke automatikusan teljes. További információkért lásd: [Windows diagnosztikai adatok](https://docs.microsoft.com/windows/privacy/windows-diagnostic-data) <br>
    
    - **Fiókbeállítások módosítása elrejtése (Windows 10-es, 1809 vagy újabb verzió szükséges)** : Válasszon **elrejtése** fiók beállításainak módosítása nem fognak megjelenni a vállalati bejelentkezési és a tartomány hiba lapokon elkerülése érdekében. Ez a beállítás megköveteli, hogy [az Azure Active Directoryban konfigurálva legyen a Vállalati védjegyezés](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding).
    - **Felhasználói fiók típusa**: Válassza ki a felhasználói fiók típusa (**rendszergazda** vagy **Standard** felhasználó).
    - **Lehetővé teszi a fehér kesztyűtartó OOBE** (Windows 10-es, 1903 vagy újabb; verzió szükséges [további fizikai követelmények](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove#prerequisites)): Válasszon **Igen** körültekintő támogatás engedélyezéséhez.
    - **Eszköz neve sablon alkalmazása** (Windows 10-es, 1809 vagy újabb verzió szükséges): Válasszon **Igen** hozhat létre egy sablont szeretné használni a regisztráció során egy eszköz elnevezésekor. A nevek legfeljebb 15 karakterből állhatnak, és betűket, számokat és kötőjelet tartalmazhatnak. A nevek nem állhatnak csak számokból. Hardverspecifikus sorozatszám hozzáadásához használja a [%SERIAL% makrót](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp). Egy másik lehetőség a [%RAND:x% makró](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) használata, amellyel véletlenszerű számsort adhat hozzá. Az x a hozzáadni kívánt számjegyek számát jelenti. 
    - **Nyelv (régió)** \*: Válassza ki az eszközhöz használt nyelv. Ez a lehetőség csak akkor érhető el, ha a **Telepítési mód** beállításnál az **Öntelepítő** lehetőséget választotta.
    - **Billentyűzet automatikus konfigurálása**\*: Ha egy **nyelv (régió)** van kiválasztva, válassza a **Igen** kihagyja a billentyűzet-kiválasztási lapot. Ez a lehetőség csak akkor érhető el, ha a **Telepítési mód** beállításnál az **Öntelepítő** lehetőséget választotta.
8. Kattintson a **Tovább** gombra.
9. Az a **címkék hatókör** lap, igény szerint adja hozzá a hatókörcímkék ezt a profilt a alkalmazni szeretné. Hatókörcímkék kapcsolatos további információkért lásd: [szerepköralapú hozzáférés-vezérléshez és a hatókör címkék használata elosztott informatikai](scope-tags.md).
10. Kattintson a **Tovább** gombra.
11. Az a **hozzárendelések** lapon a **kijelölt csoportok** a **hozzárendelése**.

    ![Képernyőkép a hozzárendelések lapon](media/enrollment-autopilot/create-profile-assignments.png)

12. Válasszon **válassza ki a befoglalandó csoportokat**, jelölje ki a csoportokat fel szeretne venni ebben a profilban.
13. Ha szeretne kizárni azokat a csoportokat, válassza a **válassza ki a kizárandó csoportokat**, jelölje ki a kizárni kívánt csoportokat.
14. Kattintson a **Tovább** gombra.
15. Az a **felülvizsgálat + létrehozás** lapon a **létrehozás** a profil létrehozásához.

    ![Képernyőkép az Áttekintés lap](media/enrollment-autopilot/create-profile-review.png)

> [!NOTE]
> Az Intune időközönként ellenőrzi, hogy a hozzárendelt csoportokat az új eszközöket, és majd kezdje meg a profilok hozzárendelése az eszközökhöz. Ez a folyamat befejezése több percet is igénybe vehet. Eszköz üzembe helyezése előtt győződjön meg arról, hogy ez a folyamat befejeződött.  Ellenőrizheti a **eszközregisztráció** > **Windows regisztrációs** > **eszközök** ahol megjelenik a módosításához a profil állapota " Hozzá nem rendelt","Hozzárendelése"és végül a"Hozzárendelt."

## <a name="edit-an-autopilot-deployment-profile"></a>AutoPilot üzembehelyezési profil szerkesztése
Az AutoPilot üzembehelyezési profil létrehozása után módosíthatja az üzembehelyezési profil egyes részeit.   

1. Az [Azure Portalbeli Intune-on](https://aka.ms/intuneportal) válassza az **Eszközök regisztrálása** elemet.
2. A **Windows-regisztráció** terület **Windows AutoPilot** szakaszában válassza az **Üzembehelyezési profilok** lehetőséget.
3. Válassza ki a szerkeszteni kívánt profilt.
4. A telepítési profil nevének vagy leírásának módosításához kattintson a bal oldali **Tulajdonságok** elemre. A módosítások elvégzését követően kattintson a **Mentés** gombra.
5. A Kezdőélmény beállításainak módosításához kattintson a **Beállítások** elemre. A módosítások elvégzését követően kattintson a **Mentés** gombra.

> [!NOTE]
> A profil módosításai alkalmazva lesznek a profilhoz társított eszközökön. Azonban a frissített profilt az Intune-ban korábban már regisztrált eszközökre csak azok alaphelyzetbe állítása és megújítása után alkalmazza a rendszer.

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Riasztások a Windows Autopilot-hozzárendelés nélküli eszközökre  <!-- 163236 -->  

A riasztások jelzik, hogy az AutoPilot programban hány eszközhöz nincs hozzárendelve AutoPilot üzembehelyezési profil. A riasztás adatai alapján a profilok létrehozhatók és a hozzárendelés nélküli eszközökhöz rendelhetők. A riasztásra kattintva megjelenik a Windows AutoPilot-eszközök részletes adatokat is tartalmazó, teljes listája.


A nem társított eszközökre vonatkozó riasztások megtekintéséhez az [Azure Portalbeli Intune-ban](https://aka.ms/intuneportal) válassza az **Eszközök regisztrálása** > **Áttekintés** > **Nem társított eszközök** lehetőséget.  


## <a name="assign-a-user-to-a-specific-autopilot-device"></a>Felhasználó hozzárendelése egy adott Autopilot-eszközhöz

Felhasználót rendelhet hozzá egy adott Autopilot-eszközhöz. Ez a hozzárendelés előre kitölti a [vállalati védjeggyel ellátott](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding) bejelentkezési oldal felhasználói űrlapját az Azure Active Directoryból származó adatokkal a Windows beállítása során. Egyéni üdvözlési megnevezés beállítását is lehetővé teszi. A windowsos bejelentkezési adatokat nem tölti ki előre és nem is módosítja. Ilyen módon csak licenccel rendelkező Intune-felhasználók rendelhetők hozzá.

Előfeltételek: Az Azure Active Directory vállalati portál lett konfigurálva, és a Windows 10-es, 1809 vagy újabb verziója.

1. Az [Azure Portalbeli Intune-ban](https://aka.ms/intuneportal) válassza az **Eszközregisztráció** > **Windows-regisztráció** > **Eszközök** > eszköz kijelölése > **Felhasználó hozzárendelése** lehetőséget.

    ![Képernyőkép a felhasználó hozzárendeléséről](media/enrollment-autopilot/assign-user.png)

2. Jelöljön ki egy Intune-licenccel rendelkező Azure-felhasználót, és válassza a **Kiválasztás** lehetőséget.

    ![Képernyőkép a felhasználó kiválasztásáról](media/enrollment-autopilot/select-user.png)

3. A **Rövid felhasználónév** mezőbe gépeljen be egy rövid nevet, vagy fogadja el az alapértelmezettet. Ez a rövid név jelenik meg, amikor a felhasználó bejelentkezik a Windows telepítése során.

    ![A rövid felhasználónév képernyőképe](media/enrollment-autopilot/friendly-name.png)

4. Válassza az **OK** gombot.


## <a name="delete-autopilot-devices"></a>AutoPilot-eszközök törlése

Windows Autopilot-eszközök Intune-ban nem regisztrált törölheti:

- Törölje az eszközök a Windows Autopilot **eszközregisztráció** > **Windows regisztrációs** > **eszközök**. Válassza ki a törölni, majd kattintson a kívánt eszközöket **törlése**. Windows Autopilot-eszköz törlése eltarthat néhány percig.

Teljesen eltávolításának bérlőjéből megköveteli, hogy az Intune-eszközök, az Azure Active Directory eszköz és a Windows Autopilot-eszköz rekordjai törléséhez. Ezt mind megteheti az Intune-ból:

1. Ha az eszközök Intune-ban regisztrált, előbb futtatnia kell [törölheti őket az Intune-ban minden Eszközök panelen](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. Az eszközök törlése az Azure Active Directory okoseszközökért **eszközök** > **az Azure AD-eszközök**.

3. Törölje az eszközök a Windows Autopilot **eszközregisztráció** > **Windows regisztrációs** > **eszközök**. Válassza ki a törölni, majd kattintson a kívánt eszközöket **törlése**. Windows Autopilot-eszköz törlése eltarthat néhány percig.

## <a name="using-autopilot-in-other-portals"></a>Az AutoPilot használata más portálokon
Ha nem kíván a mobileszközök felügyeletével foglalkozni, más portálokon is használhatja az AutoPilotot. Más portálok is használhatók, de javasoljuk, hogy az Intune-t csak AutoPilottal végzett üzembe helyezések felügyeletéhez használja. Az Intune más portálokkal való használatakor az Intune nem tudja végrehajtani a következőket:  

- Megjeleníteni az Intune-ban létrehozott, de egy másik portálon szerkesztett profilok módosításait
- Szinkronizálni egy másik portálon létrehozott profilokat
- Megjeleníteni a profil-hozzárendelések más portálon végzett módosításait
- Szinkronizálni a más portálon végzett profil-hozzárendeléseket
- Megjeleníteni az eszközlista más portálon végzett módosításait

## <a name="windows-autopilot-for-existing-devices"></a>Windows Autopilot meglévő eszközökhöz

Ha a Configuration Manager [meglévő eszközökhöz használható AutoPilot szolgáltatásával](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) regisztrál, egy korrelátorazonosítóval csoportosíthatja a Windows-eszközöket. A korrelátorazonosító az AutoPilot konfigurációs fájljának egyik paramétere. Az [enrollmentProfileName Azure AD-beli eszközattribútum](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) beállítása automatikusan az ezzel megegyező „OfflineAutopilotprofile-\<korrelátorazonosítóra\>” módosul. Így tetszőleges dinamikus Azure AD-csoportok hozhatók létre korrelátorazonosító alapján az enrollmentprofileName attribútum használatával.

>[!WARNING] 
> Mivel a korrelátorazonosító nincs előzetesen megadva az Intune-on, az eszköz tetszés szerint jelenthet be bármilyen korrelátorazonosítót. Ha a felhasználó által létrehozott korrelátorazonosító egyezik egy AutoPilot- vagy Apple DEP-profil nevével, az eszköz hozzá lesz adva az enrollmentProfileName attribútumon alapuló összes dinamikus Azure AD-eszközcsoporthoz. Az ütközés elkerüléséhez:
> - A dinamikus csoportokra vonatkozó szabályokat mindig a *teljes* enrollmentProfileName érték használatával hozza létre.
> - Az Autopilot- és Apple DEP-profilok nevét soha ne kezdje az OfflineAutopilotprofile- előtaggal.

## <a name="next-steps"></a>További lépések
Miután konfigurálta a Windows AutoPilotot a regisztrált Windows 10-eszközökhöz, sajátítsa el, hogyan felügyelheti az eszközöket. További információt [A Microsoft Intune-eszközfelügyelet ismertetése](https://docs.microsoft.com/intune/device-management) című témakörben talál.

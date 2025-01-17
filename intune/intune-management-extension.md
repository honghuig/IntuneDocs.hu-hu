---
title: PowerShell-parancsfájlok hozzáadása a Windows 10-es eszközökhöz a Microsoft Intune-Azure-ban | Microsoft Docs
description: Hozzon létre és futtasson PowerShell-parancsfájlokat, rendelje hozzá a Azure Active Directory csoportokhoz a parancsfájl-szabályzatot, a jelentések segítségével figyelje a parancsfájlokat, és tekintse meg a Windows 10-es eszközökön a Microsoft Intuneban hozzáadott parancsfájlok törlésének lépéseit. Tekintse meg a gyakori problémákat és a megoldásokat is.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 230f226cba70a7fc61efd236cc0fde0ca6b7fa68
ms.sourcegitcommit: c3a4fefbac8ff7badc42b1711b7ed2da81d1ad67
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/22/2019
ms.locfileid: "68374932"
---
# <a name="use-powershell-scripts-on-windows-10-devices-in-intune"></a>PowerShell-parancsfájlok használata Windows 10-es eszközökön az Intune-ban

A Microsoft Intune felügyeleti bővítmény használatával tölthet fel PowerShell-parancsfájlokat az Intune-ban Windows 10-es eszközökön való futtatáshoz. A felügyeleti bővítmény fokozza a Windows 10 mobileszköz-felügyeletet (MDM), és megkönnyíti a modern felügyeletre való áttérést.

Ez a funkció az alábbiakra vonatkozik:

- Windows 10 és újabb

## <a name="move-to-modern-management"></a>Áthelyezés a modern felügyeletbe

A végfelhasználói számítástechnika a digitális átalakulás korszakát éli. Klasszikus, hagyományos, egyetlen eszköz platformra, üzleti tulajdonú eszközökre, az irodából dolgozó felhasználókra és különböző manuális, reaktív informatikai folyamatokra koncentrál. A modern munkahely számos olyan platformot használ, amely felhasználói és üzleti tulajdonban van, lehetővé teszi a felhasználók számára, hogy bárhonnan működjenek, és automatizált és proaktív informatikai folyamatokat biztosítanak.

A MDM-szolgáltatások, például a Microsoft Intune, kezelhetik a Windows 10 rendszerű mobil-és asztali eszközöket. A beépített Windows 10-es felügyeleti ügyfél az Intune-nal kommunikálva vállalati felügyeleti feladatokat futtat. Szükség lehet néhány feladatra, például a speciális eszközök konfigurálására és a hibaelhárításra. A Win32-alkalmazások felügyeletéhez a [win32 app Management](apps-win32-app-management.md) szolgáltatást használhatja a Windows 10-es eszközökön.

Az Intune felügyeleti bővítmény kiegészíti a Windows 10-es MDM funkcióit. Létrehozhat PowerShell-parancsfájlokat Windows 10-es eszközökön való futtatáshoz. Hozzon létre például egy speciális eszköz-konfigurációval rendelkező PowerShell-parancsfájlt. Ezután töltse fel a parancsfájlt az Intune-ba, rendelje hozzá a parancsfájlt egy Azure Active Directory (AD) csoporthoz, és futtassa a parancsfájlt. Ezután megfigyelheti a parancsfájl futtatási állapotát az elejétől a végéig.

## <a name="prerequisites"></a>Előfeltételek

Az Intune felügyeleti bővítmény a következő előfeltételekkel rendelkezik. Ha az előfeltételek teljesülnek, az Intune felügyeleti bővítmény automatikusan települ, amikor egy PowerShell-parancsfájl vagy Win32-alkalmazás hozzá van rendelve a felhasználóhoz vagy az eszközhöz.

- A Windows 10 1607-es vagy újabb verzióját futtató eszközök. Ha az eszköz [tömeges automatikus regisztrációval](windows-bulk-enroll.md)van regisztrálva, akkor az eszközöknek a Windows 10 1703-es vagy újabb verzióját kell futtatniuk. Az Intune felügyeleti bővítmény nem támogatott Windows 10 rendszerű módban, mert az S mód nem engedélyezi a nem áruházbeli alkalmazások futtatását. 
  
- Azure Active Directoryhoz (AD) csatlakoztatott eszközök, beleértve a következőket:  
  
  - Hibrid Azure AD-csatlakozás: Azure Active Directoryhoz (AD) csatlakoztatott eszközök, valamint a helyszíni Active Directoryhoz (AD) is csatlakoztatva vannak. Útmutatásért lásd [a hibrid Azure Active Directory csatlakoztatásának](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan) megtervezése című témakört.

- Az Intune-ban regisztrált eszközök, beleértve a következőket:

  - Csoportházirendben (GPO) regisztrált eszközök. Útmutatásért lásd: [Windows 10-es eszközök automatikus regisztrálása csoportházirend használatával](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy) .
  
  - Az Intune-ban manuálisan regisztrált eszközök, amely a következőket nyújtja:
  
    - Az [Intune-ba való automatikus regisztrálás](quickstart-setup-auto-enrollment.md) engedélyezve van az Azure ad-ben. A végfelhasználó egy helyi felhasználói fiókkal jelentkezik be az eszközre, manuálisan csatlakoztatja az eszközt az Azure AD-hoz, majd bejelentkezik az eszközre az Azure AD-fiók használatával.
    
    VAGY  
    
    - A felhasználó az Azure AD-fiókjával bejelentkezik az eszközre, majd regisztrálja magát az Intune-ban.

  - Configuration Manager és Intune-t használó közösen felügyelt eszközök. Győződjön meg arról, hogy az **ügyfélalkalmazások** számítási feladatait az **Intune** vagy az **Intune**teszteli. A következő cikkekben talál útmutatást: 
  
    - [A közös felügyelet ismertetése](https://docs.microsoft.com/sccm/comanage/overview) 
    - [Ügyfélalkalmazások munkaterhelése](https://docs.microsoft.com/sccm/comanage/workloads#client-apps)
    - [Configuration Manager számítási feladatok átváltása az Intune-ba](https://docs.microsoft.com/sccm/comanage/how-to-switch-workloads)
  
> [!TIP]
> Győződjön meg arról, hogy az eszközök csatlakoznak az Azure AD- [hez](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network) . Azok az eszközök, [](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network) amelyek csak az Azure ad-ben vannak regisztrálva, nem kapják meg a parancsfájlokat.

## <a name="create-a-script-policy-and-assign-it"></a>Hozzon létre egy parancsfájl-szabályzatot, és rendelje hozzá

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközkonfiguráció** > **PowerShell-parancsfájlok** > **Hozzáadás** lehetőséget.

    ![PowerShell-parancsfájlok hozzáadása és használata Microsoft Intune](./media/mgmt-extension-add-script.png)

3. Az **alapvető beállítások**területen adja meg a következő tulajdonságokat, majd válassza a **Next (tovább**) gombot:
    - **Név**: Adja meg a PowerShell-parancsfájl nevét. 
    - **Description** (Leírás): Adja meg a PowerShell-parancsfájl leírását. A beállítás használata nem kötelező, de ajánlott.
4. A **parancsfájl beállításainál**adja meg a következő tulajdonságokat, majd válassza a **Next (tovább**) gombot:
    - **Parancsfájl helye**: Keresse meg a PowerShell-parancsfájlt. A parancsfájlnak 200 KB-nál (ASCII) kisebbnek kell lennie.
    - **Futtassa ezt a parancsfájlt a bejelentkezett hitelesítő adatok használatával**: Válassza az **Igen** lehetőséget a parancsfájlnak a felhasználó hitelesítő adataival való futtatásához az eszközön. Ha a parancsfájlt a rendszerkörnyezetben szeretné futtatni, válassza a **nem** (alapértelmezett) lehetőséget. Számos rendszergazda választja az **Igen**lehetőséget. Ha a parancsfájlnak a rendszerkörnyezetben kell futnia, válassza a **nem**lehetőséget.
    - **Parancsfájl aláírásának érvényesítése**: Válassza az **Igen** lehetőséget, ha a parancsfájlt megbízható közzétevőnek kell aláírnia. Válassza a **nem** (alapértelmezett) lehetőséget, ha nincs szükség a parancsfájl aláírására. 
    - **Parancsfájl futtatása a 64 bites PowerShell-gazdagépen**: Az **Igen** gombra kattintva futtathatja a szkriptet egy 64 bites PowerShell-(PS-) gazdagépen egy 64 bites ügyféloldali architektúrán. Válassza a **nem** (alapértelmezett) lehetőséget a parancsfájl 32 bites PowerShell-gazdagépen való futtatásához.

      Ha az **Igen** vagy a **nem**értékre állítja a beállítást, használja az alábbi táblázatot az új és a meglévő házirend-viselkedéshez:

      | Parancsfájl futtatása a 64 bites PS-gazdagépen | Ügyfél-architektúra | Új PS-parancsfájl | Meglévő házirend – PS-parancsfájl |
      | --- | --- | --- | --- | 
      | Nem | 32 bites  | 32 bites PS-gazdagép támogatott | Csak a 32 bites PS-gazdagépen fut, amely 32 bites és 64 bites architektúrán működik. |
      | Igen | 64 bites | Parancsfájlt futtat a 64 bites PS-gazdagépen a 64 bites architektúrák esetében. A 32 bites futtatásakor a szkript egy 32 bites PS-gazdagépen fut. | Parancsfájlt futtat a 32 bites PS-gazdagépen. Ha a beállítás 64 bitesre változik, a parancsfájl megnyílik (nem fut) egy 64 bites PS-gazdagépen, és jelentést készít az eredményekről. A 32 bites futtatásakor a szkript a 32 bites PS-gazdagépen fut. |

5. Válassza ki a **hatókör címkéit**. A hatókör címkéi nem kötelezőek. [A szerepköralapú hozzáférés-vezérlés (RBAC) és a hatókör-címkék használata](scope-tags.md) további információkat tartalmaz.

    Hatókör címke hozzáadása:

    1. Válassza a **hatókör címkék kiválasztása** lehetőséget > válasszon ki egy meglévő hatókör-címkét a listából > **válassza ki**.

    2. Ha elkészült, kattintson a **Tovább gombra**.

6. Válassza  > a hozzárendelések lehetőséget **, majd válassza a csoportok elemet**. Megjelenik az Azure AD-csoportok meglévő listája.

    1. Válasszon ki egy vagy több olyan csoportot, amely tartalmazza azokat a felhasználókat, akiknek az eszközei megkapják a parancsfájlt. Válassza a **Kiválasztás** lehetőséget A kiválasztott csoportok megjelennek a listában, és megkapják a szabályzatot.

        > [!NOTE]
        > Az Intune-ban található PowerShell-parancsfájlok az Azure AD-eszközök biztonsági csoportjaira vagy az Azure AD felhasználói biztonsági csoportjaira is kiállíthatók.

    2. Kattintson a **Tovább** gombra.

        ![PowerShell-szkriptek kiosztása vagy üzembe helyezése Microsoft Intuneban lévő eszközökön](./media/mgmt-extension-assignments.png)

7. A **felülvizsgálat + Hozzáadás**elemnél megjelenik a konfigurált beállítások összegzése. A parancsfájl mentéséhez válassza a **Hozzáadás** lehetőséget. A **Hozzáadás**gombra kattintva a rendszer telepíti a szabályzatot a kiválasztott csoportokra.

## <a name="important-considerations"></a>Fontos szempontok

- Ha a parancsfájlok felhasználói környezetre vannak beállítva, és a végfelhasználó rendszergazdai jogosultságokkal rendelkezik, alapértelmezés szerint a PowerShell-parancsfájl a rendszergazdai jogosultság alatt fut.

- A végfelhasználóknak nem kell bejelentkezniük az eszközre a PowerShell-parancsfájlok végrehajtásához.

- Az Intune felügyeleti bővítmény-ügyfél óránként egyszer ellenőrzi az Intune-t, és minden egyes új parancsfájl vagy változás után újraindul. Miután hozzárendelte a szabályzatot az Azure AD-csoportokhoz, elindul a PowerShell-parancsfájl, és elkészül a futtatási eredmények jelentése. A parancsfájl végrehajtása után a rendszer nem hajtja végre újra, hacsak nem változik a parancsfájl vagy a házirend.

## <a name="monitor-run-status"></a>Futtatási állapot figyelése

Megfigyelheti a felhasználók és eszközök PowerShell-parancsfájljainak futtatási állapotát az Azure Portalon.

A **PowerShell-parancsfájlok** panelen válassza ki a megfigyelendő parancsfájlt, válassza a **Figyelés** lehetőséget, majd válassza az alábbi jelentések egyikét:

- **Eszközállapot**
- **Felhasználó állapota**

## <a name="intune-management-extension-logs"></a>Intune felügyeleti bővítmény naplófájljai

Az ügyfélgépen lévő ügynökök naplói jellemzően a `\ProgramData\Microsoft\IntuneManagementExtension\Logs`-ben találhatók. A naplófájlok megtekintéséhez használhatja a [CMTrace. exe](https://docs.microsoft.com/sccm/core/support/tools) fájlt. 

![Képernyőkép vagy minta cmtrace-ügynök naplói Microsoft Intune](./media/apps-win32-app-10.png)  

## <a name="delete-a-script"></a>Parancsfájl törlése

A **PowerShell-parancsfájlok** panelen kattintson a jobb gombbal a parancsfájlra, és válassza a **Törlés** lehetőséget.

## <a name="common-issues-and-resolutions"></a>Gyakori problémák és megoldások

### <a name="issue-intune-management-extension-doesnt-download"></a>A probléma leírása: Az Intune felügyeleti bővítmény nem tölthető le

**Lehetséges megoldások**:

- Az eszköz nincs csatlakoztatva az Azure AD-hez. Győződjön meg arról, hogy az [](#prerequisites) eszközök megfelelnek az előfeltételeknek (ebben a cikkben). 
- Nincsenek olyan PowerShell-parancsfájlok vagy Win32-alkalmazások rendelve a csoportokhoz, amelyekhez a felhasználó vagy az eszköz tartozik.
- Az eszköz nem tud bejelentkezni az Intune szolgáltatásba, mert nincs internet-hozzáférés, nincs hozzáférése a Windows leküldéses Notification Serviceshoz (WNS) és így tovább.
- Az eszköz S üzemmódban van. Az Intune felügyeleti bővítmény nem támogatott az S módban futó eszközökön. 

Ha szeretné megtudni, hogy az eszköz automatikusan regisztrálva van-e, a következőket teheti:

  1. Lépjen a **Beállítások** > **fiókok** > **hozzáférés munkahelyi vagy iskolai**rendszerhez elemre.
  2. Válassza ki az összekapcsolt fiók > **adatokat**.
  3. A **speciális diagnosztikai jelentés**területen válassza a **jelentés létrehozása**lehetőséget.
  4. Nyissa `MDMDiagReport` meg a webböngészőben.
  5. Keresse meg a **MDMDeviceWithAAD** tulajdonságot. Ha a tulajdonság létezik, a rendszer automatikusan regisztrálja az eszközt. Ha ez a tulajdonság nem létezik, akkor az eszköz nincs automatikusan regisztrálva.

A [Windows 10 automatikus regisztrációjának engedélyezése](windows-enroll.md#enable-windows-10-automatic-enrollment) az automatikus regisztráció konfigurálásának lépéseit tartalmazza az Intune-ban.

### <a name="issue-powershell-scripts-do-not-run"></a>A probléma leírása: A PowerShell-parancsfájlok nem futnak

**Lehetséges megoldások**:

- A PowerShell-parancsfájlok nem futnak minden bejelentkezéskor. Ezek a következőket futtatják:

  - Ha a parancsfájl hozzá van rendelve egy eszközhöz
  - Ha megváltoztatja a parancsfájlt, feltölti, és hozzárendeli a parancsfájlt egy felhasználóhoz vagy eszközhöz
  
    > [!TIP]
    > A **Microsoft Intune felügyeleti bővítmény** egy olyan szolgáltatás, amely az eszközön fut, ugyanúgy, mint a Services alkalmazásban (Services. msc) felsorolt egyéb szolgáltatások. Az eszköz újraindítása után a szolgáltatás újraindulhat, és megkeresheti az Intune szolgáltatással társított PowerShell-parancsfájlokat is. Ha a **Microsoft Intune felügyeleti bővítmény** szolgáltatás manuális értékre van állítva, akkor előfordulhat, hogy a szolgáltatás nem indul újra az eszköz újraindítása után.

- Győződjön [meg arról, hogy az eszközök csatlakoznak az Azure ad-hez](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network). Azok az eszközök, amelyek csak a munkahelyhez vagy[](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network) szervezethez csatlakoznak (az Azure ad-ben regisztrálva vannak), nem kapják meg a parancsfájlokat.
- Az Intune felügyeleti bővítmény ügyfél óránként egyszer ellenőrzi a parancsfájl vagy a szabályzat Intune-ban történt változásait.
- Erősítse meg, hogy `%ProgramFiles(x86)%\Microsoft Intune Management Extension`a rendszer letölti az Intune felügyeleti bővítményét.
- A parancsfájlok nem futnak a Surface hubokon vagy a Windows 10-es módban.
- Tekintse át a hibákat a naplókban. Lásd: az [Intune felügyeleti bővítmény naplófájljai](#intune-management-extension-logs) (ebben a cikkben).
- A lehetséges engedélyekkel kapcsolatos problémák esetén győződjön meg arról, hogy a PowerShell- `Run this script using the logged on credentials`parancsfájl tulajdonságai a következőre vannak beállítva:. Győződjön meg arról is, hogy a bejelentkezett felhasználó rendelkezik a megfelelő engedélyekkel a parancsfájl futtatásához.

- A parancsfájlokkal kapcsolatos problémák elkülönítéséhez hajtsa végre a következő lépéseket:

  - Tekintse át a PowerShell-végrehajtási konfigurációt az eszközökön. Útmutatásért tekintse meg a [PowerShell végrehajtási szabályzatát](https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-6) .
  - Futtasson egy minta parancsfájlt az Intune felügyeleti bővítmény használatával. Hozza létre például a könyvtárat `C:\Scripts` , és adja meg mindenki számára a teljes hozzáférést. Futtassa a következő parancsfájlt:

    ```powershell
    write-output "Script worked" | out-file c:\Scripts\output.txt
    ```

    Ha ez sikeres, a kimenet. txt fájlt létre kell hoznia, és tartalmaznia kell a "parancsfájlból kidolgozott" szöveget.

  - Az Intune nélküli parancsfájlok végrehajtásának teszteléséhez futtassa a rendszerfiókban lévő parancsfájlokat a [PsExec eszköz](https://docs.microsoft.com/sysinternals/downloads/psexec) helyi használatával:

    `psexec -i -s`

## <a name="next-steps"></a>További lépések

[](device-profile-monitor.md) A profilok figyelése és [megoldása](device-profile-troubleshoot.md) .

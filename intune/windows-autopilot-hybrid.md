---
title: Regisztráció a hibrid Azure AD-hez csatlakoztatott eszközök – a Windows Autopilot
titleSuffix: ''
description: Windows Autopilot használatával regisztrálása hibrid Azure AD-hez csatlakoztatott eszközök Microsoft Intune-ban.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3fb85cc2847c235f7f8079715dee6a2d924f0ac8
ms.sourcegitcommit: ede86a3cb094c12e3e218b956abb9935bec76902
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/05/2019
ms.locfileid: "67572585"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-by-using-intune-and-windows-autopilot"></a>Üzembe helyezése hibrid Azure AD-hez csatlakoztatott eszközök Intune-nal és a Windows Autopilot használatával
Hibrid Azure Active Directory (Azure AD) beállításához használhatja az Intune és a Windows Autopilot-hez csatlakoztatott eszközök. Ehhez kövesse a cikkben.

## <a name="prerequisites"></a>Előfeltételek

Sikerült beállítani a [hibrid Azure AD-hez csatlakoztatott eszközök](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan). Ügyeljen arra, hogy [az eszköz regisztrációjának ellenőrzése]( https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration) a Get-MsolDevice parancsmag használatával.

A regisztrálni kívánt eszközöknek a következő feltételeknek kell megfelelniük:
- Windows 10-es v1809 fut, vagy nagyobb.
- Rendelkezniük kell internet-hozzáféréssel.
- Hozzáférhet az Active Directory (VPN-kapcsolat jelenleg nem támogatott).
- A beépített élmény (OOBE) mennek keresztül.
- Tudni pingelni a tartományvezérlő a tartomány, amelyhez csatlakozni kíván.

## <a name="set-up-windows-10-automatic-enrollment"></a>Windows 10-es eszközök automatikus regisztrációjának beállítása

1. Jelentkezzen be a [az Azure portal](https://portal.azure.com) , és válassza a bal oldali panelen **Azure Active Directory**.

   ![Az Azure Portalon](./media/auto-enroll-azure-main.png)

1. Válassza a **Mobilitás (MDM és MAM)** elemet.

   ![Az Azure Active Directory panel](./media/auto-enroll-mdm.png)

1. Válassza a **Microsoft Intune** elemet.

   ![A mobilitás (MDM és MAM) panelen](./media/auto-enroll-intune.png)

1. Ügyeljen arra, hogy a felhasználók, akik üzembe helyezése az Azure AD-hez csatlakoztatott eszközök és a Windows Intune használatával, amely megtalálható a csoport tagjai a **MDM felhasználói hatókör**.

   ![A konfigurálás mobilitás (MDM és MAM) panelen](./media/auto-enroll-scope.png)

1. Az alapértelmezett értéket használja a **MDM használati feltételeinek URL-cím használata**, **MDM-felderítési URL-cím**, és **MDM megfelelőségi URL-címe** mezőbe, és válassza ki **mentése**.

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>A számítógépfiókok maximális számának növelése a Szervezeti egység területen

Az Intune-összekötő az Active Directory a helyszíni Active Directory-tartományban lévő hoz létre az autopilot-ban regisztrált számítógépeket. Az Intune-összekötőt üzemeltető számítógépen a tartományon belül, a számítógép-objektumok létrehozásához jogosultsággal kell rendelkeznie. 

Egyes tartományokban található számítógépek nem jogokat kapnak a a számítógépek létrehozásához. Ezenkívül tartományokban egy beépített korlátja (alapértelmezés szerint 10), amelyre vonatkozik az összes felhasználók és számítógépek, amelyek nem a számítógép-objektumok létrehozása delegált jogosultságokkal. Ezért a jogosultságokat kell delegálható a számítógépeken, amelyek az Intune-összekötő a szervezeti egység, hibrid Azure AD-hez csatlakoztatott eszközök jönnek létre.

A szervezeti egység, amely az adott jogosultságot számítógépek létrehozásához meg kell egyeznie:
- A szervezeti egység, a tartományhoz való csatlakozás-profilban megadott.
- Ha nincs profil van kijelölve, a számítógép tartományához a tartomány nevét.

1. Nyissa meg **az Active Directory – felhasználók és számítógépek (DSA.msc)** .

1. Kattintson a jobb gombbal a szervezeti egység, amely segítségével hozzon létre hibrid Azure AD-hez csatlakoztatott számítógépek, és válassza ki **Vezérlés delegálása**.

    ![A Vezérlés delegálása parancs](media/windows-autopilot-hybrid/delegate-control.png)

1. Az a **Vezérlés delegálása** varázslóban válassza **tovább** > **Hozzáadás** > **objektumtípusok**.

1. Az a **objektumtípusok** panelen válassza a **számítógépek** jelölőnégyzetet, majd válassza ki **OK**.

    ![Az objektumtípusok panel](media/windows-autopilot-hybrid/object-types-computers.png)

1. Az a **válassza ki a felhasználók, számítógépek vagy csoportok** ablaktáblán, a a **írja be a kijelölendő objektumok nevét** mezőbe írja be annak a számítógépnek a nevét, ahol az összekötő telepítve van.

    ![A felhasználók, számítógépek vagy csoportok panel](media/windows-autopilot-hybrid/enter-object-names.png)

1. Válassza ki **Névellenőrzés** a bejegyzés érvényesítéséhez kattintson **OK**, majd válassza ki **tovább**.

1. Válassza ki **hozzon létre egy egyéni feladat** > **tovább**.

1. Válassza ki a **csak a mappában a következő objektumok** jelölőnégyzetet, majd válassza ki a **számítógép-objektumok**, **ebben a mappában hozzon létre a kijelölt objektumok**, és  **Ez a mappa a kijelölt objektumok törlése** jelölőnégyzeteket.

    ![Az Active Directory-objektum típusa panel](media/windows-autopilot-hybrid/only-following-objects.png)
    
1. Kattintson a **Tovább** gombra.

1. A **engedélyek**, jelölje be a **teljes hozzáférés** jelölőnégyzetet.  
    Ez a művelet a többi beállítást választja ki.

    ![Az engedélyek panel](media/windows-autopilot-hybrid/full-control.png)

1. Válassza ki **tovább**, majd válassza ki **Befejezés**.

## <a name="install-the-intune-connector"></a>Az Intune-összekötő telepítése

Az Intune-összekötő az Active Directory telepítve olyan számítógépre, amelyen fut a Windows Server 2016 vagy újabb verzióját kell lennie. A számítógép is az internetes és az Active Directory hozzáféréssel kell rendelkeznie. A méret és a rendelkezésre állás növelése érdekében, valamint egyszerre több Active Directory-tartomány támogatásához egyszerre több összekötőt is telepíthet környezetében. Azt javasoljuk, hogy az összekötőt telepíti, amelyek más Intune-összekötő nem fut a kiszolgálón.

1. Győződjön meg arról, hogy rendelkezik-e telepítve és konfigurálva, a nyelvi csomag [az Intune-összekötő (előzetes verzió) nyelvi követelmények](https://docs.microsoft.com/windows/deployment/windows-autopilot/intune-connector).
2. A [Intune](https://aka.ms/intuneportal)válassza **eszközregisztráció** > **Windows regisztrációs** > **Active Directory (az Intune-összekötő Előzetes verzió)**  > **összekötő hozzáadása**. 
3. Kövesse az utasításokat az összekötő letöltéséhez.
4. Nyissa meg a letöltött összekötő telepítőfájl *ODJConnectorBootstrapper.exe*, az összekötő telepítéséhez.
5. Válassza ki a telepítés végén **konfigurálása**.
6. Válassza ki **jelentkezzen be a**.
7. Adja meg a felhasználó globális rendszergazdai vagy Intune-rendszergazda szerepkör hitelesítő adatait.  
   A felhasználói fiókot az Intune-licenccel kell rendelkeznie.
8. Lépjen a **eszközregisztráció** > **Windows regisztrációs** > **az Intune-összekötő (előzetes verzió) az Active Directory**, és ellenőrizze, hogy a kapcsolat állapota a következő **aktív**.

> [!NOTE]
> Az összekötő való bejelentkezés után is igénybe vehet pár perc alatt megjelennek az [Intune](https://aka.ms/intuneportal). Csak akkor, ha az Intune szolgáltatásba való sikeres kommunikációjának jelenik meg.

### <a name="turn-off-ie-enhanced-security-configuration"></a>Kapcsolja ki az Internet Explorer fokozott biztonsági beállításai
Alapértelmezés szerint a Windows Server rendelkezik-e kapcsolva az Internet Explorer fokozott biztonsági beállításai. Ha nem tud bejelentkezni az Intune-összekötő az Active Directory majd kikapcsolása Internet Explorer – fokozott biztonsági beállítások a rendszergazda számára. [Hogyan kapcsolhatja ki az Internet Explorer fokozott biztonsági beállításai](https://blogs.technet.microsoft.com/chenley/2011/03/10/how-to-turn-off-internet-explorer-enhanced-security-configuration)

### <a name="configure-web-proxy-settings"></a>Webproxy-beállítások konfigurálása

Ha a webalkalmazás-proxy a hálózati környezetben, győződjön meg arról, hogy az Intune-összekötő az Active Directory megfelelően működik lépésként tekintse át [együttműködnek a meglévő helyszíni proxykiszolgálók](autopilot-hybrid-connector-proxy.md).


## <a name="create-a-device-group"></a>Eszközcsoport létrehozása
1. A [Intune](https://aka.ms/intuneportal)válassza **csoportok** > **új csoport**.

1. Az a **csoport** ablaktáblán tegye a következőket:

    a. A **csoporttípust**válassza **biztonsági**.

    b. Adjon meg egy **csoportnév** és **csoport leírása**.

    c. Válassza ki a **tagságtípusának**.

1. Ha a kiválasztott **dinamikus eszközök** a tagsági típus a a **csoport** ablaktáblán válassza **dinamikus eszköztagság** , majd a **speciális szabály** tegye a következők egyikét:
    - Hozzon létre egy csoportot, amely az Autopilot minden eszközt magában foglal, írja be a következőt `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`.
    - Az OrderID attribútumot az Azure AD-eszközök az Intune-csoporthoz címke mezőbe képezi le. Ha azt szeretné, hozzon létre egy csoportot, amely tartalmazza az Autopilot-eszközök egy adott csoport Tag(OrderID) kell írnia az összes: `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`
    - Adja meg, amely tartalmazza az összes az Autopilot-eszközök egy adott beszerzési rendelés Azonosítóval rendelkező csoport létrehozásához, `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`.
    
1. Kattintson a **Mentés** gombra.

1. Kattintson a **Létrehozás** gombra.  

## <a name="register-your-autopilot-devices"></a>Az Autopilot-eszközök regisztrálása

Válassza ki az Autopilot-eszközök regisztrálásához a következő módszerek valamelyikével.

### <a name="register-autopilot-devices-that-are-already-enrolled"></a>A már beléptetett Autopilot-eszközök regisztrálása

1. Autopilot-üzembehelyezési profil létrehozása a **Minden megcélzott eszköz AutoPilot-eszközzé alakítása** beállítás **Igen** értékre állításával. 
2. Rendelje hozzá a profilt egy csoportot, amely az Autopilot automatikusan regisztrálni kívánt tagot tartalmaz.

További információért lásd: [AutoPilot-üzembehelyezési profil létrehozása](enrollment-autopilot.md#create-an-autopilot-deployment-profile).

### <a name="register-autopilot-devices-that-arent-enrolled"></a>A nem beléptetett Autopilot-eszközök regisztrálása

Ha az eszközök még nincsenek beléptetve, regisztrációjukat saját kezűleg elvégezheti. További információkért lásd: [Eszközök hozzáadása](enrollment-autopilot.md#add-devices)

### <a name="register-devices-from-an-oem"></a>OEM-eszközök regisztrálása

Új eszközök vásárlásakor egyes számítógépgyártók (OEM) regisztrálhatják az eszközöket az Ön számára. További információkat a [Windows Autopilot oldala](https://aka.ms/WindowsAutopilot) tartalmaz.

Ha az Autopilot-eszközök vannak *regisztrált*, mielőtt az Intune-ban regisztrált, jelennek meg három helyen (állítsa be a sorozatszámokhoz nevű):
- A **Autopilot-eszközök** panel az Azure Portalon az Intune-ban. Válassza ki **eszközregisztráció** > **Windows regisztrációs** > **eszközök**.
- A **az Azure AD-eszközök** panel az Azure Portalon az Intune-ban. Válassza ki **eszközök** > **az Azure AD-eszközök**.
- A **Azure AD minden eszköz** kiválasztásával az Azure Portalon az Azure Active Directory panel **eszközök** > **minden eszköz**.

Után az Autopilot-eszközök vannak *regisztrált*, négy helyen jelennek meg:
- A **Autopilot-eszközök** panel az Azure Portalon az Intune-ban. Válassza ki **eszközregisztráció** > **Windows regisztrációs** > **eszközök**.
- A **az Azure AD-eszközök** panel az Azure Portalon az Intune-ban. Válassza ki **eszközök** > **az Azure AD-eszközök**.
- A **Azure AD minden eszköz** panel az Azure Active Directoryban az Azure Portalon. Válassza ki **eszközök** > **minden eszköz**.
- A **minden eszköz** panel az Azure Portalon az Intune-ban. Válassza ki **eszközök** > **minden eszköz**.

Az Autopilot-eszközök regisztrálását követően a nevük válnak az eszköz állomásnevét. Alapértelmezés szerint a hostname kezdődik *asztali -* .


## <a name="create-and-assign-an-autopilot-deployment-profile"></a>Autopilot-üzembehelyezési profil létrehozása és hozzárendelése
Az Autopilot-üzembehelyezési profilokkal Autopilot-eszközeit konfigurálhatja.

1. A [Intune](https://aka.ms/intuneportal)válassza **eszközregisztráció** > **Windows regisztrációs** > **Deployment-profilok**  >  **Profil létrehozása**.
1. Adjon meg egy **neve** és opcionálisan egy **leírás**.
1. A **üzembe helyezési mód**válassza **felhasználó-központú**.
1. Az a **csatlakozzon az Azure AD szolgáltatásba** jelölje ki **hibrid Azure AD-csatlakoztatott (előzetes verzió)** .
1. Válassza ki **Out-of-box élmény (OOBE)** , szükség szerint adja meg a beállításokat, és válassza **mentése**.
1. Válassza a **Létrehozás** lehetőséget a profil létrehozásához. 
1. A profil panelen válassza ki **hozzárendelések**.
1. Válassza ki **válassza ki a csoportokat**.
1. Az a **válassza ki a csoportokat** ablaktáblán válassza ki az eszközcsoport, és kattintson **kiválasztása**.

Módosítsa az eszköz profilt állapot körülbelül 15 percet vesz igénybe *nincs hozzárendelve* való *hozzárendelése* , és végül a *hozzárendelt*.

## <a name="optional-turn-on-the-enrollment-status-page"></a>(Nem kötelező) A regisztrálási állapot oldal bekapcsolása

1. A [Intune](https://aka.ms/intuneportal)válassza **eszközregisztráció** > **Windows regisztrációs** > **regisztrálási állapot oldal**.
1. Az a **regisztrálási állapot oldal** ablaktáblán válassza előbb **alapértelmezett** > **beállítások**.
1. Az a **alkalmazás és a profil telepítés állapotának megjelenítése** jelölje ki **Igen**.
1. Igény szerint konfigurálja a többi beállítást.
1. Kattintson a **Mentés** gombra.

## <a name="create-and-assign-a-domain-join-profile"></a>Tartomány-csatlakoztatási profil létrehozása és hozzárendelése

1. A [Intune](https://aka.ms/intuneportal)válassza **eszközkonfiguráció** > **profilok** > **profil létrehozása**.
1. Adja meg a következő tulajdonságokat:
   - **Név**: Adja meg az új profil leíró nevét.
   - **Description** (Leírás): Adja meg a profil leírását.
   - **Platform**: Válassza ki **Windows 10 és újabb**.
   - **Profil típusa**: Válassza ki **tartományhoz való csatlakozás (előzetes verzió)** .
1. Válassza ki **beállítások**, és adja meg egy **számítógépnév előtagja**, **tartománynév**, (nem kötelező), és **szervezeti egység** a[DN formátum](https://docs.microsoft.com/windows/desktop/ad/object-names-and-identities#distinguished-name). 
1. Válassza ki **OK** > **létrehozása**.  
    A profil létrehozásáról és megjelennek a listában.
1. A profil hozzárendelése esetén kövesse a [eszközprofil hozzárendelése](device-profile-assign.md#assign-a-device-profile) , és rendelje hozzá a profilt ugyanabba a csoportba ebben a lépésben használt [eszközcsoport létrehozása](windows-autopilot-hybrid.md#create-a-device-group)
   - Több tartományhoz való csatlakozás profilok központi telepítése
   
     a. Hozzon létre egy dinamikus csoportot, amely tartalmazza az összes az Autopilot-eszközök az egy adott Autopilot deployment-profilt, adja meg (device.enrollmentProfileName - eq "Autopilot-profil neve"). 
     
     b. "Az Autopilot-profil neve" cserélje le a megjelenítendő név alatt létrejön a profil [létrehozása és hozzárendelése az Autopilot deployment-profil](windows-autopilot-hybrid.md#create-and-assign-an-autopilot-deployment-profile). 
     
     c. Több Autopilot deployment-profil létrehozása, és rendelje hozzá a profil a dinamikus csoportban megadott eszközön.

> [!NOTE]
> Az elnevezési funkciókat a hibrid Azure AD JOIN a Windows Autopilot támogatja a soros % például változókat, és csak az előtagok támogatják a számítógép nevét.

## <a name="next-steps"></a>További lépések

Miután konfigurálta a Windows Autopilotot, ideje elsajátítani, hogyan felügyelheti az eszközöket. További információkért lásd: [a Microsoft Intune-Eszközfelügyelet?](device-management.md).

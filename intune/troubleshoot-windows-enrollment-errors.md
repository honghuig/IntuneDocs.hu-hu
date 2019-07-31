---
title: A Windows-eszközök regisztrálásával kapcsolatos problémák elhárítása Microsoft Intune
titleSuffix: Microsoft Intune
description: Javaslatok a Windows-eszközök Intune-beli regisztrálásával kapcsolatos leggyakoribb problémák elhárításához.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d76b9581cac6e9d74e83ce50400e14468a13d3e6
ms.sourcegitcommit: c715c93bb242f4fe44bbdf2fd585909854ed72b6
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/30/2019
ms.locfileid: "68664178"
---
# <a name="troubleshoot-windows-device-enrollment-problems-in-microsoft-intune"></a>A Windows-eszközök regisztrálásával kapcsolatos problémák elhárítása Microsoft Intune

Ez a cikk az Intune-rendszergazdáknak segít megérteni és elhárítani a Windows-eszközök Intune-beli regisztrálásakor felmerülő problémákat.

## <a name="prerequisites"></a>Előfeltételek
Mielőtt elkezdené a hibaelhárítást, fontos, hogy gyűjtsön néhány alapvető információt. Ezek az információk segítenek jobban megérteni a problémát, és csökkenthetik a megoldási időt.

Gyűjtse össze a következő információkat a problémával kapcsolatban:
- Érvényes Intune-licenc van hozzárendelve a felhasználóhoz? Ahhoz, hogy a felhasználók regisztrálni tudják eszközeiket, hozzá kell rendelni a szükséges licencet.
- A legújabb frissítés telepítve van a Windows-eszközön? Az Intune egyes funkciói csak a Windows legújabb verziójával működnek. A Windows Updateon keresztül elérhető ismert problémák számos javítást biztosítanak. A legújabb frissítések alkalmazása gyakran javít egy Windows-eszköz regisztrálásával kapcsolatos problémát. 
- Pontosan milyen hibaüzenet jelenik meg?
- Hol látja a hibaüzenetet?
- Mikor indult el a probléma? Valaha is működött a regisztráció? 
- Milyen platformon (Android, iOS, Windows) van probléma?
- Hány felhasználót érint a rendszer? Az összes érintett felhasználó vagy csak néhány?
- Hány eszközt érint a rendszer? Minden eszköz érintett vagy csak néhány?
- Mi a MDM-szolgáltató? Ha System Center Configuration Manager, a Configuration Manager milyen verzióját használja?
- Hogyan történik a beléptetés? A "saját eszközök használata" (BYOD) vagy Apple Készülékregisztrációs program (DEP) beléptetési profilokkal?

## <a name="error-messages"></a>Hibaüzenetek

### <a name="this-user-is-not-authorized-to-enroll"></a>Ez a felhasználó nem rendelkezik jogosultsággal a regisztráláshoz.

0x801c003 hiba: "Ez a felhasználó nem rendelkezik jogosultsággal a regisztráláshoz. Próbálkozzon újra, vagy forduljon a rendszergazdához a hibakód (0x801c0003) használatával. "
80180003-es hiba: "Hiba történt. Ez a felhasználó nem rendelkezik jogosultsággal a regisztráláshoz. Próbálkozzon újra, vagy forduljon a rendszergazdához a 80180003-as hibakódgal. "

**Okozhat** Az alábbi feltételek bármelyike: 

- A felhasználó már regisztrálta az Intune-ban engedélyezett eszközök maximális számát.    
- Az eszköz típusa korlátozásai le vannak tiltva.    
- A számítógép Windows 10 Home rendszert futtat. Azonban az Intune-ban való regisztrálás vagy az Azure AD-hez való csatlakozás csak a Windows 10 Pro és újabb kiadásokban támogatott.

#### <a name="resolution"></a>Megoldás:
A probléma több lehetséges megoldást is kínál:

##### <a name="remove-devices-that-were-enrolled"></a>A regisztrált eszközök eltávolítása
1. Jelentkezzen be az [Azure Portalra](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview).    
2. Ugrás a **felhasználók** > **minden felhasználója**számára.    
3. Válassza ki az érintett felhasználói fiókot, majd kattintson az **eszközök**elemre.    
4. Válassza ki a fel nem használt vagy nemkívánatos eszközöket, majd kattintson a **Törlés**gombra. 

##### <a name="increase-thedevice-enrollment-limit"></a>Az eszközök regisztrálási korlátjának emelése

> [!NOTE]
> Ez a módszer növeli az eszközök regisztrálási korlátját az összes felhasználó számára, nem csak az érintett felhasználót.

1. Jelentkezzen be az [Azure Portalra](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview).
2. Lépjen az **eszközök** >regisztrálása **regisztrációs korlátozások**elemre, majd válassza az **eszköz korlátozási korlátozásait**.    
3. Növelje az **eszköz korlátjának**értékét. 

##### <a name="checkdevice-type-restrictions"></a>Az eszközök típusára vonatkozó korlátozások keresése
1. Jelentkezzen be az [Intune](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview) -portálra egy globális rendszergazdai fiókkal.
2. Lépjen az **eszközök** > regisztrálása beléptetési**korlátozásokhoz**, majd válassza ki az **alapértelmezett** korlátozást az **eszköz típusa korlátozásai**alatt.    
3. Válassza a **platformok**lehetőséget, majd válassza a Windows **engedélyezése**  **(Mdm)** lehetőséget.

    > [!IMPORTANT]
    > Ha az aktuális beállítás már **engedélyezve**van, módosítsa a **blokkolás**értékre, mentse a beállítást, majd állítsa vissza, hogy **engedélyezze** , majd mentse újra a beállítást. Ezzel alaphelyzetbe állítja a beléptetési beállítást.

4. Várjon körülbelül 15 percet, majd regisztrálja újra az érintett eszközt.    

##### <a name="upgrade-windows-10-home"></a>A Windows 10 Home frissítése
[Frissítse a Windows 10 Home rendszert a Windows 10 Pro](https://support.microsoft.com/help/12384/windows-10-upgrading-home-to-pro) vagy újabb verzióra. 



### <a name="this-user-is-not-allowed-to-enroll"></a>Ez a felhasználó regisztrációja nem engedélyezett.

0x801c0003 hiba: "A felhasználó regisztrációja nem engedélyezett. Próbálkozzon újra, vagy forduljon a rendszergazdához a hibakód 801c0003. "

**Okozhat** Előfordulhat, hogy a **felhasználók az Azure ad-** be való csatlakozáshoz a **none**értékre vannak beállítva. Ez megakadályozza, hogy az új felhasználók az eszközeiket az Azure AD-be csatlakozzanak. Ezért az Intune-regisztráció meghiúsul.

#### <a name="resolution"></a>Megoldás:
1. Jelentkezzen be rendszergazdaként a [Azure Portalba](https://portal.azure.com/) .    
2. Lépjen **Azure Active Directory** eszközök>**eszközbeállítások menüpontra**. ****  >     
3. A felhasználók beállíthatja, hogy az eszközök az **Azure ad** -hez csatlakozzanak.    
4. Regisztrálja újra az eszközt.   

### <a name="the-device-is-already-enrolled"></a>Az eszköz már regisztrálva van.

8018000a hiba: "Hiba történt. Az eszköz már regisztrálva van.  Forduljon a rendszergazdához a hibakód 8018000a. "

**Okozhat** A következő feltételek egyike igaz:
- Egy másik felhasználó már regisztrálta az eszközt az Intune-ban, vagy csatlakoztatta az eszközt az Azure AD-hez. Annak megállapításához, hogy ez a helyzet-e, lépjen a **Beállítások** > **fiókok** > **munkahelyi hozzáférés elemre**. Keresse meg az alábbihoz hasonló üzenetet: "Egy másik felhasználó a rendszeren már csatlakoztatva van egy munkahelyi vagy iskolai hálózathoz. Távolítsa el a munkahelyi vagy iskolai kapcsolatokat, és próbálkozzon újra. "    
- A Configuration Manager ügyfél ügynöke telepítve van a számítógépen.    

#### <a name="resolution"></a>Megoldás:

A probléma megoldásához használja az alábbi módszerek egyikét:

##### <a name="remove-the-other-work-or-school-account"></a>A másik munkahelyi vagy iskolai fiók eltávolítása
1. Jelentkezzen ki a Windowsból, majd jelentkezzen be a másik fiókkal, amely regisztrált vagy csatlakozott az eszközhöz.    
2. Lépjen a **Beállítások** > **fiókok** > **munkahelyi hozzáférés**elemre, majd távolítsa el a munkahelyi vagy iskolai fiókot.
3. Jelentkezzen ki a Windowsból, majd jelentkezzen be a fiókjával.    
4. Regisztrálja az eszközt az Intune-ban, vagy csatlakoztassa az eszközt az Azure AD-hez. 

##### <a name="remove-the-configuration-manager-client"></a>Az Configuration Manager-ügyfél eltávolítása
Távolítsa el a Configuration Manager ügyfelet, majd regisztrálja újra az eszközt.



### <a name="this-account-is-not-allowed-on-this-phone"></a>Ez a fiók nem engedélyezett ezen a telefonon.

Hiba: "Ez a fiók nem engedélyezett ezen a telefonon. Győződjön meg arról, hogy a megadott adatok helyesek, majd próbálkozzon újra, vagy kérjen támogatást a vállalattól. "

**Okozhat** Az eszközt regisztrálni próbáló felhasználónak nincs érvényes Intune-licence.

#### <a name="resolution"></a>Megoldás:
Rendeljen érvényes Intune-licencet a felhasználóhoz, majd regisztrálja az eszközt.


### <a name="looks-like-the-mdm-terms-of-use-endpoint-is-not-correctly-configured"></a>Úgy tűnik, hogy a MDM használati feltételeinek végpontja helytelenül van konfigurálva.

**Okozhat** A következő feltételek egyike igaz: 
 - Az Office 365-hez és az Intune-hoz készült mobileszköz-kezelést (MDM) is használhatja a bérlőn, és az eszköz regisztrálását végző felhasználó nem rendelkezik érvényes Intune-licenccel vagy Office 365-licenccel.     
- Az Azure AD MDM használati feltételei üresek, vagy nem tartalmazzák a megfelelő URL-címet.    

#### <a name="resolution"></a>Megoldás:

A probléma megoldásához használja az alábbi módszerek egyikét: 
 
##### <a name="assign-a-valid-license-to-the-user"></a>Érvényes licencet rendeljen a felhasználóhoz
Lépjen a [Microsoft 365 felügyeleti](https://portal.office.com/adminportal/home)központba, majd rendeljen hozzá egy Intune-t vagy egy Office 365-licencet a felhasználóhoz.

##### <a name="correct-themdm-terms-of-use-url"></a>Javítsa ki a MDM használati feltételeinek URL-címét
  1. Jelentkezzen be a [Azure Portalba](https://portal.azure.com/), majd válassza a **Azure Active Directory**lehetőséget.    
  2. Válassza a **mobilitás (Mdm és MAM)** lehetőséget, majd kattintson a **Microsoft Intune**elemre.    
  3. Válassza az **alapértelmezett Mdm-URL-címek visszaállítása**lehetőséget, és ellenőrizze, hogy a **Mdm URL-címe** beállítás értéke **https://portal.manage.microsoft.com/TermsofUse.aspx** .    
  4. Válassza a **Mentés** elemet.    


### <a name="something-went-wrong"></a>Hiba történt.

80180026-es hiba: "Hiba történt. Ellenőrizze, hogy a megfelelő bejelentkezési adatokat használja-e, és hogy a szervezet használja-e ezt a funkciót. Próbálkozzon újra, vagy forduljon a rendszergazdához a 80180026-es hibakód használatával. "

**Okozhat** Ez a hiba akkor fordulhat elő, ha Windows 10 rendszerű számítógépet próbál csatlakoztatni az Azure AD-hez, és az alábbi feltételek mindegyike teljesül: 
- A MDM automatikus regisztrációja engedélyezve van az Azure-ban.    
- Az Intune PC-ügyfél (Intune PC Agent) vagy a Configuration Manager ügyfél ügynöke telepítve van a Windows 10 rendszerű számítógépre.

#### <a name="resolution"></a>Megoldás:
A probléma megoldásához használja az alábbi módszerek egyikét:

##### <a name="disablemdm-automatic-enrollment-in-azure"></a>Tiltsa le a MDM automatikus regisztrációját az Azure-ban.
1. Jelentkezzen be a [Azure Portalba](https://portal.azure.com/).    
2. Lépjen a **Azure Active Directory** > **mobilitás (Mdm és MAM)**  > **Microsoft Intune**.    
3. Állítsa a **Mdm felhasználói hatókörét** **none**értékre, majd kattintson a **Mentés**gombra.    
     
##### <a name="uninstall"></a>Eltávolítás
Távolítsa el az Intune PC-ügyfelet vagy Configuration Manager-ügynököt a számítógépről.    

### <a name="the-software-cannot-be-installed"></a>A szoftver nem telepíthető.

Hiba: "A szoftver nem telepíthető, 0x80cf4017."

**Okozhat** Az ügyfélszoftver elavult.

#### <a name="resolution"></a>Megoldás:
1. Jelentkezzen be [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com)a szolgáltatásba.    
2. Nyissa meg a **felügyeleti** > **ügyfélszoftver letöltése**lehetőséget, majd kattintson az **ügyfélszoftver letöltése**elemre.    
3. Mentse a telepítőcsomagot, majd telepítse az ügyfélszoftvert. 


### <a name="the-account-certificate-is-not-valid-and-may-be-expired"></a>A fiók tanúsítványa nem érvényes, és lehet, hogy lejárt.

Hiba: "A fiók tanúsítványa nem érvényes, és lehet, hogy lejárt, 0x80cf4017."

**Okozhat** Az ügyfélszoftver elavult.

#### <a name="resolution"></a>Megoldás:
1. Jelentkezzen be [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com)a szolgáltatásba.    
2. Nyissa meg a **felügyeleti** > **ügyfélszoftver letöltése**lehetőséget, majd kattintson az **ügyfélszoftver letöltése**elemre.    
3. Mentse a telepítőcsomagot, majd telepítse az ügyfélszoftvert.    

### <a name="your-organization-does-not-support-this-version-of-windows"></a>A szervezet nem támogatja a Windows ezen verzióját. 

Hiba: "Hiba történt. A szervezet nem támogatja a Windows ezen verzióját.  (0x80180014) "

**Okozhat** A Windows MDM regisztrációja le van tiltva az Intune-bérlőben.

#### <a name="resolution"></a>Megoldás:
A probléma önálló Intune-környezetben való kijavításához kövesse az alábbi lépéseket: 
 
1. Jelentkezzen be rendszergazdaként a [Azure Portalba](https://portal.azure.com/) .    
2. Válassza az **Intune** lehetőséget a bal oldalon, majd lépjen az ****  > eszközök regisztrálása beléptetési**korlátozásokhoz**.    
3. Az **eszközök típusának korlátozásai**területen kattintson a **platformok**elemre, majd válassza a Windows **engedélyezése**  **(Mdm)** lehetőséget.    
4. Kattintson a **Save** (Mentés) gombra.    
 
A probléma megoldásához az Intune-nal és a Configuration Managertel rendelkező hibrid MDM hajtsa végre az alábbi lépéseket: 
1. Nyissa meg a Configuration Manager-konzolt.    
2. Válassza az **Adminisztráció**, majd a **Cloud Services**lehetőséget.    
3. Kattintson a jobb gombbal **Microsoft Intune**előfizetésre, majd válassza a **platformok konfigurálása > Windows**lehetőséget.    
4.  > Jelölje be a **Windows-regisztráció** > engedélyezése**OK**elemet.  


### <a name="a-setup-failure-has-occurred-during-bulk-enrollment"></a>Telepítési hiba történt a csoportos regisztráció során.

**Okozhat** A megfelelő kiépítési csomaghoz tartozó Account Package (Package_GUID) Azure AD felhasználói fiókjai nem jogosultak eszközök csatlakoztatására az Azure AD-hez. Ezek az Azure AD-fiókok automatikusan létrejönnek a Windows Configuration Designerrel (WCD) rendelkező kiépítési csomag vagy az iskolai PC-alkalmazás beállítása során, és ezeket a fiókokat az eszközök Azure AD-hez való csatlakoztatására használják.

#### <a name="resolution"></a>Megoldás:
1. Jelentkezzen be rendszergazdaként a [Azure Portalba](https://portal.azure.com/) .    
2. Lépjen **Azure Active Directory > eszközök > eszközbeállítások menüpontra**.    
3. Beállíthatja, hogy a **felhasználók az Azure ad** -be vagy az **összes**  **kiválasztott**eszközhöz csatlakozzanak.

   Ha a **kijelölt**lehetőséget választja, kattintson a **kijelölt**elemre, majd kattintson a **Tagok hozzáadása** lehetőségre az összes olyan felhasználó hozzáadásához, akik csatlakozhatnak az eszközéhez az Azure ad-ben. Győződjön meg arról, hogy a kiépítési csomaghoz tartozó összes Azure AD-fiók hozzá van adva.
 
További információ a kiépítési csomag létrehozásáról a Windows Configuration Designerben: létesítési [csomag létrehozása a Windows 10](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-create-package)rendszerhez.

További információ az iskolai számítógépek alkalmazásának beállításáról: [az iskolai számítógépek alkalmazásának beállítása](https://docs.microsoft.com/education/windows/use-set-up-school-pcs-app).


### <a name="auto-mdm-enroll-failed"></a>Automatikus MDM-regisztráció: Meghiúsult 

Ha Csoportházirend használatával próbál automatikusan regisztrálni egy Windows 10-es eszközt, a következő problémákat tapasztalhatja: 
- A Feladatütemezőben, a **Microsoft** > **Windows** > **EnterpriseMgmt**alatt a beléptetési **ügyfél által a Mdm-re való automatikus regisztráláshoz létrehozott ütemezés** utolsó futtatási eredménye a következő: **Az 76-es esemény automatikus MDM regisztrálása: Sikertelen művelet (ismeretlen Win32-hibakód: 0x8018002b)**       
- Eseménynapló a következő eseményt naplózza az Applications **and Services logs/Microsoft/Windows/DeviceManagement-Enterprise-Diagnostics-Provider/admin**területen:   
    ```asciidoc
    Log Name: Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
    Source: DeviceManagement-Enterprise-Diagnostics-Provider
    Event ID: 76
    Level: Error
    Description: Auto MDM Enroll: Failed (Unknown Win32 Error code: 0x80180002b)
    ```
**Okozhat** A következő feltételek egyike igaz: 
- Az UPN nem ellenőrzött vagy nem irányítható tartományt tartalmaz, például:. local ( joe@contoso.localpéldául).    
- **A Mdm felhasználói hatóköre**  **none**értékre van állítva. 

#### <a name="resolution"></a>Megoldás:
Ha az UPN nem ellenőrzött vagy nem irányítható tartományt tartalmaz, kövesse az alábbi lépéseket: 

1. Azon a kiszolgálón, amelyen a Active Directory tartományi szolgáltatások (AD DS) fut, nyissa meg **Active Directory felhasználókat és számítógépeket** . Ehhez írja be a **DSA. msc** parancsot a **Futtatás** párbeszédpanelen, majd kattintson **az OK**gombra.    
2. Kattintson a tartomány alatt lévő **felhasználók** elemre, majd tegye a következőket:  
    - Ha csak egy érintett felhasználó van, kattintson a jobb gombbal a felhasználóra, majd kattintson a **Tulajdonságok**elemre. A **fiók** lap UPN-utótag legördülő listájában a **felhasználói bejelentkezési név**területen válasszon egy érvényes UPN-utótagot, például contoso.com, majd kattintson **az OK**gombra.    
    - Ha több érintett felhasználó van, válassza ki a felhasználókat, a **művelet** menüben kattintson a **Tulajdonságok**elemre. A **fiók** lapon jelölje be az **UPN-utótag** jelölőnégyzetet, válasszon ki egy érvényes UPN-utótagot, például contoso.com a legördülő listából, majd kattintson **az OK**gombra.
3. Várjon a következő szinkronizálásra, vagy kényszerítse a különbözeti szinkronizálást a szinkronizációs kiszolgálóról a következő parancsok futtatásával egy rendszergazda jogú PowerShell-parancssorban:
    ```powershell
    Import-Module ADSync
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

Ha a **Mdm felhasználói hatóköre**  **none**értékre van állítva, kövesse az alábbi lépéseket: 
 
1. Jelentkezzen be a [Azure Portalba](https://portal.azure.com/), majd válassza a **Azure Active Directory**lehetőséget.
2. Válassza a **mobilitás (Mdm és MAM)** lehetőséget, majd válassza a **Microsoft Intune**lehetőséget.    
3. A **Mdm felhasználói hatókörének** beállítása az **összes**értékre. Vagy állítsa be a **Mdm felhasználói hatókörét** **néhány**értékre, és válassza ki azokat a csoportokat, amelyek automatikusan regisztrálhatják Windows 10-es eszközeiket.    
4. A **MAM felhasználói hatókör** beállítása **none**értékre.


## <a name="next-steps"></a>További lépések

- [Eszközök regisztrálásával kapcsolatos problémák elhárítása az Intune-ban](troubleshoot-device-enrollment-in-intune.md)
- [Kérdés feltevése az Intune-fórumon](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [A Microsoft Intune támogatási csapatának blogja](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [A Microsoft nagyvállalati mobilitási és biztonsági blogjának beolvasása](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
- [Támogatás kérése Microsoft Intune](https://docs.microsoft.com/intune/get-support) 
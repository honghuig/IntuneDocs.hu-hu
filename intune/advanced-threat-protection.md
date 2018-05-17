---
title: A Windows Defender ATP használata a Microsoft Intune-ban – Azure | Microsoft Docs
description: Ismerkedjen meg a Windows Defender Komplex kártevők elleni védelem (ATP) engedélyezésének módjával egy teljes forgatókönyvön keresztül, amely érinti az ATP bekapcsolását az Intune-ban és a Windows Defender biztonsági központban (ATP portál), eszközök ATP-konfigurációs profilokkal történő bevonását, Intune eszközmegfelelőségi szabályzat létrehozását, Azure AD feltételes hozzáférési szabályzat létrehozását és az eszközmegfelelőség figyelését.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2e99ed0bd1eb5bae90913aedba5973e5e1282f70
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/02/2018
---
# <a name="enable-windows-defender-atp-with-conditional-access-in-intune"></a>A Windows Defender ATP engedélyezése feltételes hozzáféréssel az Intune-ban

A Windows Defender Komplex veszélyforrások elleni védelem (ATP) és a Microsoft Intune együttesen segít megelőzni a biztonsági incidenseket és mérsékelni a vállalaton belüli incidensek következményeit.

Az a funkció a Windows 10 rendszerű eszközökre vonatkozik

Tegyük fel, hogy valaki beágyazott rosszindulatú kódot tartalmazó Word-mellékletet küld az egyik vállalaton belüli felhasználónak. A felhasználó megnyitja a mellékletet, és engedélyezi annak tartalmát. Megemelt jogosultsági szintű támadás kezdődik, és a támadó egy távoli számítógépről rendszergazdai jogosultságot szerez az áldozat eszközén. A támadó ezután távolról hozzáfér a felhasználó többi eszközéhez is.

A biztonsági incidens a teljes vállalatot is érintheti.

A Windows Defender ATP képes megoldani a leírthoz hasonló biztonsági eseményeket. A Windows Defender biztonsági központ (ATP konzol) „magas kockázatúként” jelenti az eszközöket, és részletes jelentést tartalmaz a gyanús tevékenységről. Példánkban a Windows Defender ATP észleli, hogy az eszköz szokatlan kódot hajtott végre, egy folyamat jogosultsági szintje megemelkedett, rosszindulatú kódot szúrt be, és gyanús távoli rendszerhéjat adott ki. A Windows Defender ATP ez után lehetőségeket kínál fel a fenyegetés mérséklésére.

Az Intune használatával a kockázat elfogadható szintjét meghatározó megfelelőségi szabályzatok hozhatók létre. Ha egy eszköz túllépi ezt a kockázati szintet, akkor nem megfelelővé válik. Ezt az Azure Active Directory (AD) feltételes hozzáférésével használva a felhasználó vállalati erőforrásokhoz való hozzáférése blokkolva lesz.

Ez a cikk a következőkhöz nyújt útmutatást:

- Az Intune engedélyezése az ATP-ben és az ATP engedélyezése az Intune-ban. Ezek a feladatok szolgáltatások közötti kapcsolatot hoznak létre az Intune és a Windows Defender ATP között. Ez a kapcsolat teszi lehetővé, hogy a Windows Defender ATP kiírhassa az Intune-eszközökre vonatkozó kockázatokat.
- A megfelelőségi szabályzat létrehozása az Intune-ban.
- Feltételes hozzáférés engedélyezése az Azure Active Directory-ban (AD) az eszközökön azok fenyegetési szintje alapján.

## <a name="prerequisites"></a>Előfeltételek

Az ATP Intune-nal való használatához a következőknek konfigurálva és használatra készen kell állniuk:

- Licenccel rendelkező bérlő az Enterprise Mobility + Security E5 és Windows E5 (vagy Microsoft 365 Enterprise E5) csomaghoz
- Microsoft Intune környezet az [Intune-nal felügyelt](windows-enroll.md) Windows 10-es eszközökhöz, amelyek az Azure AD-ba is be vannak léptetve
- [Windows Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) és hozzáférés a Windows Defender biztonsági központhoz (ATP portál)

## <a name="enable-windows-defender-atp-in-intune"></a>A Windows Defender ATP engedélyezése az Intune-ban

1. Jelentkezzen be az [Azure portálra](https://portal.azure.com).
2. Kattintson az **Összes szolgáltatás** lehetőségre, szűrjön az **Intune-ra**, és válassza ki a **Microsoft Intune** elemet.
3. Válassza az **Eszközmegfelelőség** > **Windows Defender ATP** > **Windows Defender Komplex veszélyforrások elleni védelem rendszergazdai konzol megnyitása** lehetőséget.

    ![Helyettesítő szöveg](./media/atp-device-compliance-open-windows-defender.png)

4. A **Windows Defender biztonsági központban**:
    1. Válassza a **Beállítások** > **Speciális funkciók** lehetőséget.
    2. A **Microsoft Intune kapcsolathoz** válassza a **Be** lehetőséget:

        ![Helyettesítő szöveg](./media/atp-security-center-intune-toggle.png)

    3. Válassza a **Beállítások mentése** lehetőséget.

5. Az Intune-ba visszatérve válassza az **Eszközmegfelelőség** > **Windows Defender ATP** lehetőséget. A **Windows 10.0.15063+ rendszerű eszközök csatlakoztatása a Windows Defender Komplex veszélyforrások elleni védelemhez** melletti kapcsolót állítsa **Be** helyzetbe.
6. Válassza a **Mentés** lehetőséget.

Ezt a feladatot általában egyszer kell elvégezni. Ha tehát az ATP már engedélyezve van az Intune-erőforrásában, akkor nem szükséges megismételnie.

## <a name="onboard-devices-using-a-configuration-profile"></a>Eszközök bevonása konfigurációs profil használatával

A Windows Defender része egy, az eszközökre telepítendő konfigurációs csomag. A telepített csomag a [Windows Defender ATP szolgáltatásokkal](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) kommunikál a fájlok vizsgálatáról, a fenyegetések észleléséről, és jelenti a kockázatokat a Windows Defender ATP-nek. Az Intune használatával létrehozható egy ezt a konfigurációs csomagot használó konfigurációs profil. Ez után ezt a profilt kell az első alkalommal bevonni kívánt eszközökhöz rendelni.

Miután egyszer védelem alá vont egy eszközt egy konfigurációs csomaggal, nem kell ismét megtennie. Ez általában egyszeri feladat.

Eszközöket [csoportszabályzat vagy a System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-windows-defender-advanced-threat-protection) használatával is bevonhat.

A következő lépések az Intune használatával végzett védelembe vételt ismertetik.

#### <a name="download-configuration-package"></a>Konfigurációs csomag letöltése

1. A [Windows Defender biztonsági központban](https://securitycenter.windows.com) válassza a **Beállítások** > **Bevonás** lehetőséget.
2. Adja meg a következő beállításokat:
  - **Operációs rendszer**: Windows 10
  - **Gép bevonása** > **üzembe helyezés módja**: Mobileszköz-felügyelet / Microsoft Intune
3. Válassza a **Csomag letöltése** lehetőséget és mentse a **WindowsDefenderATPOnboardingPackage.zip** fájlt. Bontsa ki a fájlt.

Ez a tömörített fájl tartalmazza a **WindowsDefenderATP.onboarding** fájlt, amelyre a következő lépéseknél lesz szükség.

#### <a name="create-the-atp-configuration-profile"></a>Az ATP konfigurációs profil létrehozása

Ez a profil a korábbi lépésekben letöltött bevonási csomagot használja.

1. Az [Azure Portalon](https://portal.azure.com) kattintson az **Összes szolgáltatás** lehetőségre, szűrjön az **Intune-ra**, és válassza ki a **Microsoft Intune** elemet.
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adjon meg **Nevet** és **Leírást**.
4. A **Platform** beállításnál válassza a **Windows 10 és újabb** lehetőséget.
5. A **Profiltípus** beállításnál válassza a **Windows Defender Komplex veszélyforrások elleni védelem (Windows 10 asztali verzió)** lehetőséget.
6. A beállítások konfigurálása:

  - **Regisztrációs konfigurációs csomag feltöltése**: Tallózással keresse meg és jelölje ki a letöltött **WindowsDefenderATP.onboarding** fájlt. Ez a fájl teszi lehetővé azt a beállítást, hogy az eszközök jelenthessenek a Windows Defender ATP szolgáltatásnak.
  - **Minták megosztása minden fájlhoz**: Engedélyezi minták gyűjtését és megosztását a Windows Defender ATP-vel. Ha például gyanús fájlt talál, elküldheti a Windows Defender ATP-nek alapos elemzésre.
  - **Telemetriai jelentések gyakoriságának növelése**: Magas kockázatnak kitett eszközök ennek a beállításnak az engedélyezésével gyakrabban jelentik a telemetriai adatokat a Windows Defender ATP szolgáltatásnak.
  - **Regisztráció megszüntetésére szolgáló konfigurációs csomag feltöltése**: Ha meg kívánja szüntetni a Windows Defender ATP általi figyelést, akkor letölthet és hozzáadhat egy kizáró csomagot a [Windows Defender biztonsági központból](https://securitycenter.windows.com). Egyébként ez a tulajdonság figyelmen kívül hagyható.

    A [Windows 10 rendszerű gépek bevonása a System Center Configuration Manager használatával](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-sccm-windows-defender-advanced-threat-protection) részletesebben ismerteti ezeket a Windows Defender ATP-beállításokat.

7. Válassza az **OK**, majd a **Létrehozás** lehetőséget a változások mentéséhez. Ezzel létrejön a profil.

## <a name="create-the-compliance-policy"></a>A megfelelőségi szabályzat létrehozása
A megfelelőségi szabályzat határozza meg egy eszközön a kockázat elfogadható szintjét.

1. Az [Azure Portalon](https://portal.azure.com) kattintson az **Összes szolgáltatás** lehetőségre, szűrjön az **Intune-ra**, és válassza ki a **Microsoft Intune** elemet.
2. Válassza az **Eszközmegfelelőség** > **Szabályzatok** > **Szabályzat létrehozása** lehetőséget.
3. Adjon meg **Nevet** és **Leírást**.
4. A **Platform** beállításnál válassza a **Windows 10 és újabb** lehetőséget.
5. Az **Eszközállapot** beállításainál adja meg az **Eszköz fenyegetettségi szintjének legmagasabb megengedett szintje** Ön által választott értékét:

  - **Védett**: Ez a szint a legbiztonságosabb. Az eszköz csak akkor fér hozzá a céges erőforrásokhoz, ha semmilyen veszélyforrás nincs rajta. Ha bármilyen veszélyforrás észlelhető, az eszköz nem megfelelőnek minősül.
  - **Alacsony**: Az eszköz csak abban az esetben minősül megfelelőnek, ha kizárólag alacsony szintű veszélyforrások állnak fenn. A közepes vagy magas fenyegetettségi szintű eszközök nem megfelelők.
  - **Közepes**: Az eszköz abban az esetben minősül megfelelőnek, ha az eszközön észlelt veszélyforrások alacsony vagy közepes szintűek. Magas szintű fenyegetések észlelése esetén az eszköz nem megfelelőnek minősül.
  - **Magas**: Ez a legkevésbé biztonságos, minden fenyegetettségi szintet megengedő beállítás. Az ilyen eszközök magas, közepes és alacsony szintű fenyegetettség esetén is megfelelőnek minősülnek.

6. Válassza az **OK**, majd a **Létrehozás** lehetőséget a változások mentéséhez (ezzel létrejön a szabályzat).

## <a name="assign-the-policy"></a>A szabályzat hozzárendelése

1. Az [Azure Portalon](https://portal.azure.com) kattintson az **Összes szolgáltatás** lehetőségre, szűrjön az **Intune-ra**, és válassza ki a **Microsoft Intune** elemet.
2. Válassza az **Eszközmegfelelőség** > **Szabályzatok** lehetőséget, majd válassza ki Windows Defender ATP-megfelelőségi szabályzatát.
3. Válassza a **Hozzárendelések** lehetőséget.
4. Belefoglalással vagy kizárással adja meg a szabályzathoz rendelni kívánt Azure AD-csoportokat.
5. A szabályzatnak a kijelölt csoportokhoz rendeléséhez válassza a **Mentés** lehetőséget. A rendszer ekkor kiértékeli a szabályzat hatókörébe tartozó felhasználói eszközök megfelelőségét.

## <a name="create-an-azure-ad-conditional-access-policy"></a>Azure AD feltételes hozzáférési szabályzat létrehozása
A feltételes hozzáférési szabályzat akkor tiltja az erőforrásokhoz való hozzáférést, *ha* az eszköz nem megfelelő. Így érhető el, hogy a fenyegetettségi szintet túllépő eszközök ne férjenek hozzá olyan vállalati erőforrásokhoz, mint a SharePoint vagy az Exchange Online.

1. Az [Azure Portalon](https://portal.azure.com) nyissa meg az **Azure Active Directory** > **Feltételes hozzáférés** > **Új szabályzat** panelt.
2. Adjon meg **Nevet** a szabályzathoz és válassza a **Felhasználók és csoportok** lehetőséget. A befoglalási vagy kizárási lehetőségek használatával jelölje ki a szabályzathoz rendelendő csoportokat majd válassza a **Kész** lehetőséget.
3. Válassza a **Felhőalkalmazások** lehetőséget, és válassza ki a védeni kívánt alkalmazásokat. Az **Alkalmazások kijelölése** alatt választhatja például az **Office 365 SharePoint Online** és az **Office 365 Exchange Online** elemeket.

    A módosítások mentéséhez válassza a **Kész** gombot.

4. A **Feltételek** > **Ügyfélalkalmazások** választásával a szabályzat alkalmazásokra és böngészőkre is érvényesíthető. Választhatja például az **Igen**, majd a **Böngésző** és a **Mobilalkalmazások és asztali ügyfelek** lehetőségeket.

    A módosítások mentéséhez válassza a **Kész** gombot.

5. Az eszközmegfelelőségen alapuló feltételes hozzáférés az **Engedélyezés** választásával érvényesíthető. Választhatja például a **Hozzáférés engedélyezése** > **Eszköz megfelelőként való megjelölésének megkövetelése** lehetőséget.

    A módosítások mentéséhez válassza az **Választ** gombot.

6. A módosítások mentéséhez válassza a **Szabályzat engedélyezése** majd a **Létrehozás** lehetőséget.

Hasznos forrás a [Mi az a feltételes hozzáférés?](conditional-access.md) című cikk.

## <a name="monitor-device-compliance"></a>Az eszközmegfelelőség figyelése
Most a Windows Defender ATP megfelelőségi szabályzattal rendelkező eszközök állapotának figyelése következik.

1. Az [Azure Portalon](https://portal.azure.com) kattintson az **Összes szolgáltatás** lehetőségre, szűrjön az **Intune-ra**, és válassza ki a **Microsoft Intune** elemet.
2. Válassza az **Eszközmegfelelőség** > **Megfelelés a szabályzatoknak** lehetőséget.
3. Keresse meg a listában a Windows Defender ATP-szabályzatot, és tekintse meg a megfelelő és nem megfelelő eszközöket.

## <a name="more-good-stuff"></a>További hasznos források
[Windows Defender ATP – feltételes hozzáférés](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/conditional-access-windows-defender-advanced-threat-protection)  
[Windows Defender ATP – Kockázati irányítópult](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection)  
[Eszközmegfelelőségi szabályzatok – első lépések](device-compliance-get-started.md)  
[Feltételes hozzáférés az Azure AD-ben](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
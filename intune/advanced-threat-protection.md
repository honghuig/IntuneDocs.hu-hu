---
title: A Microsoft Defender ATP használata a Microsoft Intune-Azure-ban | Microsoft Docs
description: Megtudhatja, hogyan engedélyezheti a Microsoft Defender komplex veszélyforrások elleni védelmet (Microsoft Defender ATP) egy teljes körű forgatókönyvben, beleértve a Microsoft Defender ATP bekapcsolását az Intune-ban és a Microsoft Defender Security Center, a Microsoft Defender ATP-t használó eszközöket. konfigurációs profil, Intune-eszköz megfelelőségi szabályzat létrehozása, Azure AD feltételes hozzáférési szabályzat létrehozása és az eszközök megfelelőségének figyelése.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: af27a9b07434346a5425d0539759cb90ebf1ee6f
ms.sourcegitcommit: 614c4c36cfe544569db998e17e29feeaefbb7a2e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68427087"
---
# <a name="enforce-compliance-for-microsoft-defender-atp-with-conditional-access-in-intune"></a>A Microsoft Defender ATP megfelelőségének betartatása feltételes hozzáféréssel az Intune-ban  

A Microsoft Defender komplex veszélyforrások elleni védelem (Microsoft Defender ATP) és a Microsoft Intune együttműködve segít megelőzni a biztonsági réseket, és korlátozza a szervezeten belüli szabálysértések hatását.

Ez a funkció az alábbiakra vonatkozik: Windows 10-es eszközök

Tegyük fel, hogy valaki beágyazott rosszindulatú kódot tartalmazó Word-mellékletet küld az egyik vállalaton belüli felhasználónak. A felhasználó megnyitja a mellékletet, és engedélyezi annak tartalmát. Megemelt jogosultsági szintű támadás kezdődik, és a támadó egy távoli számítógépről rendszergazdai jogosultságot szerez az áldozat eszközén. A támadó ezután távolról hozzáfér a felhasználó többi eszközéhez is.

A biztonsági incidens a teljes vállalatot is érintheti.

A Microsoft Defender ATP a forgatókönyvhöz hasonló biztonsági eseményeket tud elhárítani. A Microsoft Defender Security Center "magas kockázatnak" tekinti az eszközöket, és részletes jelentést készít a gyanús tevékenységekről. A példánkban a Microsoft Defender ATP azt észleli, hogy az eszköz rendellenes kódot hajtott végre, a folyamat jogosultság-eszkalációját, a rosszindulatú kód beadását és a gyanús távoli rendszerhéj kiosztását. A Microsoft Defender ATP ezt követően lehetőséget biztosít a fenyegetés enyhítésére.

Az Intune használatával a kockázat elfogadható szintjét meghatározó megfelelőségi szabályzatok hozhatók létre. Ha egy eszköz túllépi ezt a kockázati szintet, akkor nem megfelelővé válik. Ezt az Azure Active Directory (AD) feltételes hozzáférésével használva a felhasználó vállalati erőforrásokhoz való hozzáférése blokkolva lesz.

Ez a cikk a következőkhöz nyújt útmutatást:

- Engedélyezze az Intune-t a Microsoft Defender Security Centerban, és engedélyezze a Microsoft Defender ATP-t az Intune-ban. Ezek a feladatok szolgáltatások közötti kapcsolatot hoznak létre az Intune és a Microsoft Defender ATP között. Ez a kapcsolódás lehetővé teszi, hogy a Microsoft Defender ATP megírja a számítógép kockázatát az Intune-eszközök számára.
- A megfelelőségi szabályzat létrehozása az Intune-ban.
- Engedélyezze a feltételes hozzáférést a Azure Active Directory (AD) eszközön az eszközökön a fenyegetések szintje alapján.

## <a name="prerequisites"></a>Előfeltételek

Ha a Microsoft Defender ATP-t az Intune-nal szeretné használni, győződjön meg róla, hogy a következő konfigurálva van, és készen áll a használatra:

- Licenccel rendelkező bérlő az Enterprise Mobility + Security E3 és Windows E5 (vagy Microsoft 365 Enterprise E5) csomaghoz
- Microsoft Intune környezet az [Intune-nal felügyelt](windows-enroll.md) Windows 10-es eszközökhöz, amelyek az Azure AD-ba is be vannak léptetve
- [Microsoft DEFENDER ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) és hozzáférés a microsoft Defender Security Centerhoz (ATP-portál)

## <a name="enable-microsoft-defender-atp-in-intune"></a>A Microsoft Defender ATP engedélyezése az Intune-ban

Amikor új alkalmazást integrál az Intune Mobile Threat Defense-be, és engedélyezi a kapcsolatot, az Intune egy klasszikus feltételes hozzáférési szabályzatot hoz létre Azure Active Directoryban. Minden MTD-alkalmazás, mint például a [DEFENDER ATP](advanced-threat-protection.md) vagy bármely további [MTD-partner](mobile-threat-defense.md#mobile-threat-defense-partners), új klasszikus feltételes hozzáférési szabályzatot hoz létre.  Ezek a szabályzatok figyelmen kívül hagyhatók, de nem szerkeszthetők, nem törölhetők és nem tilthatók le.

Klasszikus feltételes hozzáférési szabályzatok a MTD-alkalmazásokhoz: 

- Az Intune-MTD arra használják, hogy az eszközök regisztrálva legyenek az Azure AD-ben, hogy rendelkezzenek az eszköz azonosítójával. Az azonosító megadása kötelező, hogy az eszközök és az állapotuk sikeresen jelentse az Intune-nak.  
- Nem különböznek a MTD kezeléséhez esetlegesen létrehozott feltételes hozzáférési házirendektől.
- Alapértelmezés szerint a kiértékeléshez használt egyéb feltételes hozzáférési szabályzatok nem működnek együtt.  

A klasszikus feltételes hozzáférési szabályzatok megjelenítéséhez [Az Azure](https://portal.azure.com/#home)-ban lépjen **Azure Active Directory** > a**feltételes hozzáférés** > **klasszikus házirendjei**elemre.

### <a name="to-enable-defender-atp"></a>A Defender ATP engedélyezése
1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **eszköz megfelelősége** > **Microsoft Defender ATP**lehetőséget, majd az *összekötő beállításai*alatt válassza **a Microsoft Defender Security Center megnyitása**lehetőséget.

    ![Válassza ki a Microsoft Defender Security Center megnyitásához](./media/advanced-threat-protection/atp-device-compliance-open-microsoft-defender.png)

4. A **Microsoft Defender Security Centerban**:
    1. Válassza a **Beállítások** > **Speciális funkciók** lehetőséget.
    2. A **Microsoft Intune kapcsolathoz** válassza a **Be** lehetőséget:

        ![Az Intune-hoz való kapcsolódás engedélyezése](./media/advanced-threat-protection/atp-security-center-intune-toggle.png)

    3. Válassza a **Beállítások mentése** lehetőséget.

4. Lépjen vissza az Intune-ba, a**Microsoft Defender ATP** **eszköz megfelelősége** > . Állítsa be a **Windows-eszközök csatlakoztatása 10.0.15063 és újabb verzióját a Microsoft DEFENDER ATP** -be **a**következőre:.
5. Kattintson a **Mentés** gombra.

Ezt a feladatot általában egyszer kell elvégezni. Így ha a Microsoft Defender ATP már engedélyezve van az Intune-erőforrásban, akkor nem kell újra végrehajtania.

## <a name="onboard-devices-using-a-configuration-profile"></a>Eszközök bevonása konfigurációs profil használatával

Amikor egy végfelhasználó regisztrál az Intune-ba, különböző beállításokat küldhet az eszközre egy konfigurációs profil használatával. Ez a Microsoft Defender ATP-re is vonatkozik.

A Microsoft Defender ATP olyan bevezetési konfigurációs csomagot tartalmaz, amely a [Microsoft DEFENDER ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) -szolgáltatásokkal kommunikál a fájlok vizsgálatához, a fenyegetések észleléséhez és a Microsoft Defender ATP kockázatának jelentéséhez.

A bevezetéskor az Intune egy automatikusan létrehozott konfigurációs csomagot kap a Microsoft Defender ATP-ből. Az Intune leküldi a konfigurációs csomagot az eszközre, amikor elküldi a konfigurációs profilt az eszközre, amely lehetővé teszi a Microsoft Defender ATP számára az eszköz figyelését a fenyegetések ellen.

Miután egyszer védelem alá vont egy eszközt egy konfigurációs csomaggal, nem kell ismét megtennie. Eszközöket [csoportszabályzat vagy a System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints) használatával is bevonhat.

### <a name="create-the-configuration-profile"></a>A konfigurációs profil létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adjon meg **Nevet** és **Leírást**.
4. A **Platform** beállításnál válassza a **Windows 10 és újabb** lehetőséget.
5. A **Profil típusa**beállításnál válassza a **Microsoft Defender ATP (Windows 10 asztali verzió)** lehetőséget.
6. A beállítások konfigurálása:

    - **Microsoft DEFENDER ATP-ügyfél konfigurációs csomagjának típusa**: Válassza  a bevezetést, hogy hozzáadja a konfigurációs csomagot a profilhoz. A **Regisztráció megszüntetése** lehetőséget választva eltávolíthatja profilból a konfigurációs csomagot.
  
    > [!NOTE]  
    > Ha megfelelően létesített egy, a Microsoft Defender ATP-sel létesített kapcsolatokat, az  Intune automatikusan előkészíti a konfigurációs profilt, és a **Microsoft Defender ATP-ügyfél konfigurációs csomagjának típusa** beállítás nem lesz elérhető.
  
    - **Minta megosztása az összes fájlhoz**:  A lehetővé teszi a minták gyűjtését és a Microsoft Defender ATP-vel való megosztását. Ha például egy gyanús fájlt lát, beküldheti azt a Microsoft Defender ATP-be a Deep Analysis használatával. **Nincs konfigurálva, nem** oszt meg egyetlen mintát sem a Microsoft Defender ATP-ben.
    - A **telemetria-jelentéskészítés gyakoriságának gyorsítása**: A magas kockázatú eszközök esetében **engedélyezze** ezt a beállítást, hogy az a Microsoft Defender ATP szolgáltatásnak gyakrabban telemetria jelentést.

    A [Windows 10-es gépek System Center Configuration Manager használatával történő](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-sccm) előkészítése további részleteket tartalmaz ezekről a Microsoft Defender ATP-beállításokról.

7. Válassza az **OK**, majd a **Létrehozás** lehetőséget a változások mentéséhez. Ezzel létrejön a profil.

## <a name="create-the-compliance-policy"></a>A megfelelőségi szabályzat létrehozása
A megfelelőségi szabályzat határozza meg egy eszközön a kockázat elfogadható szintjét.

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközmegfelelőség** > **Szabályzatok** > **Szabályzat létrehozása** lehetőséget.
3. Adjon meg **Nevet** és **Leírást**.
4. A **Platform** beállításnál válassza a **Windows 10 és újabb** lehetőséget.
5. A **Microsoft DEFENDER ATP** -beállítások részen állítsa be, hogy **az eszköz a gép kockázati pontszáma alatt vagy alatt legyen** az előnyben részesített szint. A fenyegetések szintjének besorolását a [Microsoft DEFENDER ATP határozza meg](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue).

   - **Törlés**: Ez a szint a legbiztonságosabb. Az eszközön nem lehetnek meglévő fenyegetések, és továbbra is hozzáférhetnek a vállalati erőforrásokhoz. Ha bármilyen veszélyforrás észlelhető, az eszköz nem megfelelőnek minősül. (A Microsoft Defender ATP-felhasználók a *biztonságos értéket biztosítják*.)
   - **Alacsony**: Az eszköz csak abban az esetben minősül megfelelőnek, ha kizárólag alacsony szintű fenyegetések állnak fenn. A közepes vagy magas veszélyforrású eszközök nem megfelelőek.
   - **Közepes**: Az eszköz abban az esetben minősül megfelelőnek, ha az eszközön észlelt fenyegetések alacsony vagy közepes méretűek. Magas szintű fenyegetések észlelése esetén az eszköz nem megfelelőnek minősül.
   - **Magas**: Ez a szint a legkevésbé biztonságos, és lehetővé teszi az összes veszélyforrás szintjét. A magas, közepes vagy alacsony veszélyforrású eszközök megfelelőnek minősülnek.

6. Válassza az **OK**, majd a **Létrehozás** lehetőséget a változások mentéséhez (ezzel létrejön a szabályzat).

## <a name="assign-the-policy"></a>A szabályzat hozzárendelése

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza ki az **eszköz megfelelőségi** > **szabályzatait**> Válassza ki a Microsoft Defender ATP-megfelelőségi szabályzatát.
3. Válassza a **Hozzárendelések** lehetőséget.
4. Belefoglalással vagy kizárással adja meg a szabályzathoz rendelni kívánt Azure AD-csoportokat.
5. A szabályzatnak a kijelölt csoportokhoz rendeléséhez válassza a **Mentés** lehetőséget. A rendszer ekkor kiértékeli a szabályzat hatókörébe tartozó felhasználói eszközök megfelelőségét.

## <a name="create-a-conditional-access-policy"></a>Feltételes hozzáférési szabályzat létrehozása
A feltételes hozzáférési szabályzat blokkolja az erőforrásokhoz való hozzáférést, *Ha* az eszköz nem megfelelő. Így érhető el, hogy a fenyegetettségi szintet túllépő eszközök ne férjenek hozzá olyan vállalati erőforrásokhoz, mint a SharePoint vagy az Exchange Online.  

> [!TIP]  
> A feltételes hozzáférés az Azure Active Directory (Azure AD) technológiája. Az *Intune-ból* elérhető feltételes hozzáférési csomópont ugyanaz a csomópont, amelyet az *Azure AD-ből* is el lehet érni.  

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba, és válassza a **feltételes hozzáférés** > **új szabályzat**lehetőséget.
2. Adjon meg **Nevet** a szabályzathoz és válassza a **Felhasználók és csoportok** lehetőséget. A befoglalási vagy kizárási lehetőségek használatával jelölje ki a szabályzathoz rendelendő csoportokat majd válassza a **Kész** lehetőséget.
3. Válassza a **Felhőalkalmazások** lehetőséget, és válassza ki a védeni kívánt alkalmazásokat. Az **Alkalmazások kijelölése** alatt választhatja például az **Office 365 SharePoint Online** és az **Office 365 Exchange Online** elemeket.

    A módosítások mentéséhez válassza a **Kész** gombot.

4. A **Feltételek** > **Ügyfélalkalmazások** választásával a szabályzat alkalmazásokra és böngészőkre is érvényesíthető. Választhatja például az **Igen**, majd a **Böngésző** és a **Mobilalkalmazások és asztali ügyfelek** lehetőségeket.

    A módosítások mentéséhez válassza a **Kész** gombot.

5. Válassza az **Engedélyezés** lehetőséget, ha feltételes hozzáférést szeretne alkalmazni az eszköz megfelelősége alapján. Választhatja például a **Hozzáférés engedélyezése** > **Eszköz megfelelőként való megjelölésének megkövetelése** lehetőséget.

    A módosítások mentéséhez válassza az **Választ** gombot.

6. A módosítások mentéséhez válassza a **Szabályzat engedélyezése** majd a **Létrehozás** lehetőséget.

[Mi a feltételes hozzáférés?](conditional-access.md) jó erőforrás.

## <a name="monitor-device-compliance"></a>Az eszközmegfelelőség figyelése
Ezután figyelje a Microsoft Defender ATP-megfelelőségi szabályzattal rendelkező eszközök állapotát.

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközmegfelelőség** > **Megfelelés a szabályzatoknak** lehetőséget.
3. Keresse meg a Microsoft Defender ATP-szabályzatot a listában, és tekintse meg, hogy mely eszközök megfelelőek vagy nem megfelelőek.

## <a name="more-good-stuff"></a>További hasznos források
[Microsoft Defender ATP feltételes hozzáférés](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/conditional-access)  
[A Microsoft Defender ATP kockázati irányítópultja](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)  

[Eszközmegfelelőségi szabályzatok – első lépések](device-compliance-get-started.md)  
[Feltételes hozzáférés az Azure AD-ben](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
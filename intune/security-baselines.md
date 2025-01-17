---
title: Biztonsági alapkonfigurációk használata a Microsoft Intuneban – Azure | Microsoft Docs
description: Ajánlott Windows biztonsági beállítások hozzáadása vagy konfigurálása a felhasználók és az eszközök adatainak a mobileszköz-felügyelethez Microsoft Intune való védelméhez. A BitLocker engedélyezése, a Microsoft Defender komplex veszélyforrások elleni védelem konfigurálása, az Internet Explorer vezérlése, intelligens képernyő használata, helyi biztonsági házirendek beállítása, jelszó megkövetelése, internetes letöltések letiltása stb.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bbab505d668f0e348b3b4d34fb2c39ac683f340b
ms.sourcegitcommit: bd09decb754a832574d7f7375bad0186a22a15ab
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68353587"
---
# <a name="use-security-baselines-to-configure-windows-10-devices-in-intune"></a>Biztonsági alapkonfigurációk használata a Windows 10-es eszközök Intune-ban való konfigurálásához

Az Intune biztonsági alapkonfigurációi segítségével biztonságossá teheti és megvédheti a felhasználókat és az eszközöket. A biztonsági alapkonfigurációk a Windows beállításai előre konfigurált csoportjai, amelyek segítségével a megfelelő biztonsági csapatok által javasolt, ismert beállításokat és alapértelmezett értékeket alkalmazhat. Amikor létrehoz egy biztonsági alapkonfiguráció-profilt az Intune-ban, az *eszköz konfigurációs* profilját hozza létre.

Ez a funkció az alábbiakra vonatkozik:

- Windows 10 1809-es és újabb verziók

A biztonsági alapkonfigurációkat az Intune-ban lévő felhasználók vagy eszközök csoportjaira telepíti, és a beállítások a Windows 10 vagy újabb rendszerű eszközökre vonatkoznak. Ha például a *Mdm biztonsági* alapkonfiguráció automatikusan engedélyezi a BitLockert a cserélhető meghajtókon, a automatikusan jelszót kér az eszköz zárolásának feloldásához, automatikusan letiltja az alapszintű hitelesítést, és így tovább. Ha egy alapértelmezett érték nem működik a környezetében, a szükséges beállítások alkalmazásához szabja testre az alaptervet.  

A különálló alaptípusok tartalmazhatják ugyanazokat a beállításokat, de a beállításokhoz eltérő alapértelmezett értékeket is használhatnak. Fontos megérteni a használni kívánt alapkonfigurációk alapértelmezett értékeit, majd módosítani az egyes alapterveket, hogy azok megfeleljenek a szervezeti igényeknek.  

> [!NOTE]
> A Microsoft nem javasolja, hogy éles környezetben a biztonsági alapkonfigurációk előzetes verzióit használják. Az előzetes verziójú alapkonfiguráció beállításai az előzetes verzió során változhatnak. 

A biztonsági alapkonfigurációk használatának célja, hogy a Microsoft 365 használatakor teljes körű biztonságos munkafolyamattal rendelkezzen. Az előnyök többek között a következők:

- A biztonsági alapkonfiguráció a biztonságot befolyásoló beállításokkal kapcsolatos ajánlott eljárásokat és javaslatokat tartalmazza. Az Intune-partnerek ugyanazzal a Windows biztonsági csoporttal rendelkeznek, amely csoportházirend biztonsági alapterveket hoz létre. Ezek az ajánlások az útmutató és a széleskörű tapasztalatok alapján érhetők el.
- Ha még nem ismeri az Intune-t, és nem tudja, hol kezdjen hozzá, akkor a biztonsági alaptervek előnyt biztosítanak. Gyorsan létrehozhat és üzembe helyezhet egy biztonságos profilt, tudván, hogy segít megvédeni a szervezet erőforrásait és adatait.
- Ha jelenleg a csoportházirendet használja, az Intune-ba való Migrálás sokkal egyszerűbb, mint az alaptervek. Ezek az alapkonfigurációk natív módon vannak beépítve az Intune-ba, és modern felügyeleti felülettel rendelkeznek.



A [Windows biztonsági](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines) alapkonfigurációk egy nagyszerű erőforrás, amellyel többet tudhat meg a szolgáltatásról. [Mobileszköz-kezelés](https://docs.microsoft.com/windows/client-management/mdm/) A (MDM) egy nagyszerű erőforrás a MDM, és a Windows-eszközökön is.

## <a name="security-baseline-versions-and-instances"></a>A biztonsági alapterv verziói és példányai
Időről időre az alapterv új frissítései elérhetővé válnak. Az alapkonfiguráció minden új verziójának példánya hozzáadhat vagy eltávolíthat beállításokat, vagy egyéb módosításokat is bevezethet. Például, mivel az új Windows 10 beállítások elérhetővé válnak a Windows 10 új verzióival, a MDM biztonsági alapterve egy új verzió-példányt kaphat, amely tartalmazza a legújabb beállításokat.  

Az Intune-konzolon megtekintheti, hogy mely biztonsági alaptervek érhetők el és milyen információkat. Az elérhető információk közé tartozik az alapkonfiguráció típusát használó profilok száma, az alapkonfiguráció különböző példányainak rendelkezésre állása, valamint a legutóbbi legutóbbi példány elérhetővé tételének vagy közzétételének időpontja.  Az alábbi példa egy jól használt MDM biztonsági alapterv csempéjét mutatja be:  

![Alapkonfiguráció csempe](./media/security-baselines/baseline-tile.png)

A használt alapverziókkal kapcsolatos információk megtekintéséhez válasszon ki egy alapkonfigurációt, majd válassza a **verziók**lehetőséget. Az Intune a profilok által használt verziók részleteit jeleníti meg. A verziók panelen egyetlen verzió kiválasztásával megtekintheti az adott verziót használó profilok mélyebb részleteit. Kiválaszthat két különböző verziót is, majd az alapkonfigurációk **összehasonlítása** lehetőségre kattintva letöltheti azokat a CSV-fájlokat, amelyek részletezik ezeket a különbségeket.  

![Alaptervek összehasonlítása](./media/security-baselines/compare-baselines.png)

Amikor létrehoz egy biztonsági alapkonfiguráció- *profilt*, a profil automatikusan a legutóbb kiadott biztonsági alapkonfiguráció-példányt használja.  Továbbra is használhatja és szerkesztheti azokat a profilokat, amelyeket korábban az alapkonfiguráció korábbi verziójának használatával hozott létre, beleértve az előzetes verzió használatával létrehozott alapterveket is. 

A biztonsági alapprofilok [](#change-the-baseline-instance-for-a-profile) támogatják a használatban lévő alapterv verziójának módosítását. Ez azt jelenti, hogy amikor egy új verzió jön létre, nem kell létrehoznia új alapkonfigurációt, hogy kihasználhassa. Ehelyett, ha elkészült, kiválaszthat egy alapkonfigurációt, majd a beépített lehetőség használatával módosíthatja a profil példányának verzióját.  

## <a name="available-security-baselines"></a>Elérhető biztonsági alaptervek 

Az Intune-nal az alábbi biztonsági alapkonfigurációk használhatók. A hivatkozások használatával megtekintheti az egyes alaptervek legutóbbi példányának beállításait. 

- **MDM biztonsági alapterv**
  - [A MDM biztonsági alapterve a Spring 2019 (19H1) számára](security-baseline-settings-mdm.md)
  - [Előnézet MDM biztonsági alapterv október 2018](security-baseline-settings-mdm-archive.md)

- **A Microsoft Defender ATP alapterve**  
  (Ennek az alapkonfigurációnak a *használatához a környezetnek meg kell felelnie a [Microsoft Defender komplex veszélyforrások elleni védelem](advanced-threat-protection.md#prerequisites)használatának*előfeltételeinek.
  - [Előnézet A Microsoft Defender ATP alapterve](security-baseline-settings-defender-atp.md)  

  > [!NOTE]
  > A Microsoft Defender ATP biztonsági alapterve fizikai eszközökre van optimalizálva, és jelenleg nem ajánlott virtuális gépeken (VM) vagy VDI-végpontokon használni. Bizonyos alapbeállítások befolyásolhatják a távoli interaktív munkameneteket a virtualizált környezetekben.  További információ: a [Microsoft DEFENDER ATP biztonsági](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline) alapkonfigurációjának nagyobb megfelelősége a Windows dokumentációjában.

Továbbra is használhatja és szerkesztheti a korábban létrehozott profilokat egy előnézeti sablon alapján, még akkor is, ha az előnézeti sablon már nem érhető el új profilok létrehozásához. 

## <a name="prerequisites"></a>Előfeltételek
- Az alapkonfigurációk az Intune-ban való kezeléséhez a fióknak beépített szerepkörrel kell rendelkeznie a [házirend és a profil kezelőjében](role-based-access-control.md#built-in-roles) .

- Egyes alapkonfigurációk használata esetén előfordulhat, hogy aktív előfizetéssel kell rendelkeznie a további szolgáltatásokhoz, például a Microsoft Defender ATP-hez.  

## <a name="co-managed-devices"></a>Közösen felügyelt eszközök

Az Intune által felügyelt eszközökön a biztonsági alapkonfigurációk hasonlók a közösen felügyelt eszközökhöz Configuration Manager. A közösen felügyelt eszközök a System Center Configuration Manager és a Microsoft Intune használatával kezelik a Windows 10 rendszerű eszközöket egyszerre. Lehetővé teszi, hogy a meglévő Configuration Manager befektetéseit az Intune előnyeihez csatlakoztassa. A [közös felügyelet áttekintése](https://docs.microsoft.com/sccm/comanage/overview) nagyszerű erőforrás, ha Configuration Managert használ, és a felhő előnyeit is szeretné használni.

A közösen felügyelt eszközök használatakor az **eszköz konfigurációs** munkaterhelését (a beállításait) az Intune-ra kell váltania. Az [eszköz konfigurációs](https://docs.microsoft.com/sccm/comanage/workloads#device-configuration) munkaterhelései további információkat biztosítanak.

## <a name="create-the-profile"></a>A profil létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba, majd az elérhető alaptervek listájának megtekintéséhez válassza az **eszköz biztonsági** > alapkonfigurációi elemet.


    ![Válassza ki a konfigurálni kívánt biztonsági alaptervet](./media/security-baselines/available-baselines.png)

2. Válassza ki a használni kívánt alaptervet, majd válassza a **profil létrehozása**lehetőséget.  

3. Az **alapok** lapon a következő tulajdonságokat kell megadnia:

    - **Név**: Adja meg a biztonsági alaptervek profiljának nevét. Adja meg például *a DEFENDER ATP standard profilját*.

    - **Description** (Leírás): Adjon meg egy szöveget, amely leírja, hogy mi ez az alapkonfiguráció. A leírás a kívánt szöveg megadására szolgál. Nem kötelező, de ajánlott.  

   Kattintson a **tovább** gombra a következő lapra való ugráshoz. Miután új lapot adott meg, kiválaszthatja a lap nevét, hogy visszatérjen egy korábban megtekintett laphoz.  

4. A konfigurációs beállítások lapon tekintse meg a kiválasztott alaptervben elérhető **Beállítások** csoportjait. Egy csoport kibontásával megtekintheti a csoport beállításait, valamint az alapkonfigurációban lévő beállítások alapértelmezett értékeit is. Megadott beállítások keresése:
   - Válassza ki a kibontani kívánt csoportot, és tekintse át a rendelkezésre álló beállításokat.  
   - A keresősáv  használatával olyan kulcsszavakat határozhat meg, amelyek szűrik a nézetet úgy, hogy csak azok a csoportok jelenjenek meg, amelyek tartalmazzák a keresési feltételeket.  
 
   Az alapkonfiguráció mindegyik beállításának alapértelmezett konfigurációja az adott alapverzióhoz tartozik. Konfigurálja újra az alapértelmezett beállításokat az üzleti igények kielégítése érdekében. A különböző alapkonfigurációk ugyanazt a beállítást tartalmazhatják, és a beállítástól függően különböző alapértelmezett értékeket is használhatnak az alaptervnek megfelelően. 

    ![Csoport kibontása a csoport beállításainak megtekintéséhez](./media/security-baselines/sample-list-of-settings.png)

5. A hatókör  Címkék lapon válassza a **hatókör címkék kiválasztása** lehetőséget a *címkék kiválasztása* panel megnyitásához a hatókör címkék a profilhoz való hozzárendeléséhez. 

6. A **hozzárendelések** lapon válassza a **csoportok kiválasztása** lehetőséget, majd rendelje hozzá az alaptervet egy vagy több csoporthoz. **Válassza ki** a kizárni kívánt csoportokat a hozzárendelés finomhangolásához.  

   ![Profil hozzárendelése](./media/security-baselines/assignments.png)
  
7. Amikor készen áll az alapkonfiguráció üzembe helyezésére, folytassa a **felülvizsgálat + létrehozás** lapra, és tekintse át az alapterv részleteit. A profil mentéséhez és telepítéséhez válassza a **Létrehozás** lehetőséget.  

   Amint létrehozza a profilt, a rendszer leküldi a hozzárendelt csoportba, és azonnal alkalmazhatja.

   > [!TIP]  
   > Ha a profilt a csoportokhoz való első hozzárendelés nélkül menti, később is szerkesztheti a profilt.  

   ![Az alapterv áttekintése](./media/security-baselines/review.png) 

  
8. Miután létrehozta a profilt, szerkessze az **eszköz biztonsági** > **biztonsági**alapkonfigurációi területen, válassza ki a konfigurált alapkonfigurációt, majd válassza a **profilok**lehetőséget.  Válassza ki a profilt az elérhető profilok listájából, majd válassza a **Tulajdonságok**lehetőséget. Az összes elérhető konfigurációs lapon módosíthatja a beállításokat, majd a módosítások elvégzéséhez válassza a **felülvizsgálat + mentés** lehetőséget.  

## <a name="change-the-baseline-instance-for-a-profile"></a>Profil alapkonfiguráció-példányának módosítása
Az alapprofilok támogatják a profil által használt alapkonfiguráció-példány változását. Kiválaszthat egy régebbi példányt, vagy több tipikusan egy újabb példányát ugyanazon alaptervből.  Két különböző alapterv között nem módosítható, például úgy, hogy a MDM biztonsági alaptervének használatával a Defender ATP alapkonfigurációját használja. 

Az alapkonfiguráció módosításának konfigurálásakor lehetősége lesz letölteni egy CSV-fájlt, amely felsorolja a két érintett alapverzió közötti változásokat. Azt is megteheti, hogy megtartja az összes testreszabást az eredeti alapverzióban, és alkalmazza azokat az új verzióra, vagy implementálja a kiválasztott új alapverzióban található összes alapértelmezett értéket. 

A mentés után a rendszer azonnal újratelepíti az alaptervet a hozzárendelt csoportokba.  

**Átalakítás során**:
- Új, a használt eredeti verzióban nem szereplő beállítások lettek hozzáadva, és az alapértelmezett értékek használatára vannak beállítva.  

- A rendszer eltávolítja az új alapverzióban nem szereplő beállításokat, és ezt a biztonsági alapkonfigurációt már nem kényszeríti ki.  

  Ha egy beállítást már nem felügyel egy alapkonfiguráció-profil, akkor ez a beállítás nem áll alaphelyzetbe az eszközön. Ehelyett az eszközön beállított beállítás az utolsó konfigurációra lesz állítva, amíg egy másik folyamat nem kezeli a beállítást a módosításra. Példák olyan folyamatokra, amelyek megváltoztathatják a beállításokat a kezelés leállítása után, egy másik alapkonfigurációt, egy csoportházirend-beállítást vagy az eszközön végzett manuális konfigurálást is tartalmazhatnak. 

### <a name="to-change-the-instance-for-a-baseline"></a>Egy alapterv példányának módosítása  

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) -ba, majd válassza az **eszköz biztonsági** > alapkonfigurációk lehetőséget, majd válassza ki a módosítani kívánt profilt tartalmazó alapkonfiguráció csempéjét.  

2. Ezután válassza a **profilok**lehetőséget, majd jelölje be a szerkeszteni kívánt profilhoz tartozó jelölőnégyzetet, majd válassza a **verzió módosítása**lehetőséget.  

   ![alapterv kiválasztása](./media/security-baselines/select-baseline.png)  

3. A **verzió módosítása** panelen a **válassza ki** a legördülő menüben frissíteni kívánt biztonsági alapkonfigurációt, majd válassza ki a használni kívánt verziót.  

   ![Válasszon verziót](./media/security-baselines/select-instance.png)  
   
4. Válassza a **frissítés áttekintése** lehetőséget egy olyan CSV-fájl letöltéséhez, amely az aktuális példány verziójának és a kiválasztott új verziónak a különbségét jeleníti meg. Tekintse át ezt a fájlt, és Ismerje meg, hogy mely beállítások legyenek hozzáadva, melyeket eltávolított, illetve hogy a beállítások alapértelmezett értékei a frissített profilban legyenek.  

   Ha elkészült, folytassa a következő lépéssel.  

5. A profil frissítéséhez válasszon ki egy **módszert**a két lehetőség közül: 
   - **Alapkonfiguráció-módosítások elfogadása, de a meglévő beállítások** megtartása – ez a beállítás megőrzi a testreszabásokat az alapprofilban, és alkalmazza azokat a használni kívánt új verzióra.
   - **Alapkonfiguráció-módosítások elfogadása és a meglévő beállítások** elvetése – ez a lehetőség teljesen felülírja az eredeti profilt. A frissített profil az alapértelmezett értékeket fogja használni az összes beállításhoz.  

6. Válassza ki **elküldése**. A profil frissítése a kiválasztott alapkonfigurációhoz, és az átalakítás befejezése után az alapkonfiguráció azonnal újratelepül a hozzárendelt csoportokba.

## <a name="remove-a-security-baseline-assignment"></a>Biztonsági alapterv-hozzárendelés eltávolítása
Ha egy biztonsági alapkonfiguráció már nem érvényes egy eszközre, vagy az alapkonfiguráció beállításai nincsenek *konfigurálva*, az eszközön lévő beállítások nem állíthatók be előre felügyelt konfigurációra. Ehelyett az eszköz korábban felügyelt beállításai megtartják az alapkonfigurációtól kapott utolsó beállításokat, amíg egy másik folyamat nem frissíti ezeket a beállításokat az eszközön.  

Más folyamatok, amelyek később módosíthatják az eszköz beállításait, tartalmazhatnak egy másik vagy új biztonsági alapkonfigurációt, az eszköz konfigurációs profilját, Csoportházirend konfigurációját vagy a beállítás manuális szerkesztését az eszközön.  





## <a name="q--a"></a>Kérdések és válaszok

### <a name="why-these-settings"></a>Miért ezek a beállítások?

A Microsoft biztonsági csapata több éves tapasztalattal rendelkezik a Windows-fejlesztőknek és a biztonsági Közösségnek a javaslatok létrehozásához. Az ebben az alapkonfigurációban található beállítások a legfontosabb biztonsággal kapcsolatos konfigurációs beállításoknak tekintendők. Az új Windows-buildekben a csapat az újonnan kiadott funkciók alapján módosítja a javaslatait.

### <a name="is-there-a-difference-in-the-recommendations-for-windows-security-baselines-for-group-policy-vs-intune"></a>Van különbség a csoportházirend és a Windows biztonsági alaptervek esetében. Intune?

Ugyanaz a Microsoft biztonsági csapat választotta ki és szervezte meg az egyes alapkonfigurációk beállításait. Az Intune az Intune biztonsági alapkonfigurációjának összes vonatkozó beállítását tartalmazza. A csoportházirend alapkonfigurációjának néhány beállítása a helyszíni tartományvezérlőre vonatkozik. Ezek a beállítások nem tartoznak az Intune javaslataihoz. Az összes többi beállítás azonos.

### <a name="are-the-intune-security-baselines-cis-or-nsit-compliant"></a>Megfelelőek-e az Intune biztonsági alapkonfigurációi a CIS vagy a NSIT?

Szigorúan szólva, nem. A Microsoft biztonsági csapata a vállalatokat, például a CIS-t a javaslatok fordítására kéri. A "CIS-kompatibilis" és a Microsoft alapkonfigurációk között azonban nincs egy az egyhez típusú hozzárendelés.

### <a name="what-certifications-does-microsofts-security-baselines-have"></a>Milyen minősítésekkel rendelkezik a Microsoft biztonsági alapkonfigurációi? 

- A Microsoft továbbra is közzéteszi a csoportházirend-objektumok (GPO-k) és a [biztonsági megfelelőségi eszközkészlet](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10)biztonsági alapkonfigurációit, mivel azok sok évig tartanak. Ezeket az alapterveket számos szervezet használja. Az alapkonfigurációk javaslatai a Microsoft Security csapatának a nagyvállalati ügyfelekkel és külső ügynökségekkel való összevonása, beleértve a védelmi minisztériumot (DoD), a National Institute of Standards and Technology (NIST) és egyebeket. Ezekkel a szervezetekkel megoszthatjuk javaslatait és alapterveit. Ezeknek a szervezeteknek saját javaslatai is vannak, amelyek szorosan tükrözik a Microsoft javaslatait. Ahogy a mobileszköz-felügyelet (MDM) továbbra is a felhőbe növekszik, a Microsoft ezzel egyenértékű MDM-ajánlásokat hozott létre ezekről a csoportházirend-alaptervekről. Ezek a további alapkonfigurációk a Microsoft Intunera épülnek, és megfelelőségi jelentéseket tartalmaznak a felhasználók, csoportok és eszközök számára, amelyek követik az alaptervet (vagy nem követik).

- Számos ügyfél kiindulási pontként használja az Intune alapkonfigurációjának javaslatait, majd testreszabja azt az informatikai és biztonsági igények kielégítése érdekében. A Microsoft Windows 10-es RS5 **Mdm biztonsági** alapkonfigurációja a kiadás első alapterve. Ez az alapkonfiguráció általános infrastruktúraként készült, amely lehetővé teszi, hogy az ügyfelek később más biztonsági alapterveket is importálnak a CIS, a NIST és más szabványok alapján. Jelenleg a Windowshoz érhető el, és végül az iOS és az Android rendszerre is kiterjed.

- Áttelepítés a helyszíni Active Directory csoportházirendből egy tiszta felhőalapú megoldásba Azure Active Directory (AD) használatával, Microsoft Intune egy utazás. A [biztonsági megfelelőségi eszközkészlet](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10) olyan csoportházirend-sablonokat is tartalmaz, amelyek segíthetnek a hibrid ad és az Azure ad-hez csatlakoztatott eszközök kezelésében. Ezek az eszközök igény szerint lekérhetik a felhő (Intune) és a csoportházirend-beállítások MDM beállításait a helyszíni tartományvezérlőkön.

## <a name="next-steps"></a>További lépések
- Tekintse meg a beállításokat az elérhető alaptervek legújabb verzióiban:  
  - [MDM biztonsági alapterv](security-baseline-settings-mdm.md)  
  - [A Microsoft Defender ATP alapterve](security-baseline-settings-defender-atp.md)  

- Ellenőrizze az állapotot, és figyelje meg az alaptervet [és a profilt](security-baselines-monitor.md)


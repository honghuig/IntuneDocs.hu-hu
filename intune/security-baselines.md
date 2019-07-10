---
title: Biztonsági alapterveket használja a Microsoft Intune – Azure |} A Microsoft Docs
description: Adja hozzá, vagy a felhasználó és az eszközökön a Microsoft Intune mobileszköz-felügyeleti adatok védelme érdekében ajánlott a windows biztonsági beállítások konfigurálása. Engedélyezheti a Bitlockert, Microsoft Defender komplex veszélyforrások elleni védelem konfigurálása, szabályozhatja az Internet Explorer, SmartScreen használata, a helyi biztonsági házirendek beállítása, jelszó kérése, internetes tölt le, és további letiltása.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3e4e1040913daef5418f0b4fa1e56f6ef827dd67
ms.sourcegitcommit: 63b55e81122e5c15893302b109ae137c30855b55
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67713278"
---
# <a name="use-security-baselines-to-configure-windows-10-devices-in-intune"></a>Biztonsági alapterveket segítségével a konfigurálása a Windows 10-eszközök Intune-ban

Használja az Intune biztonsági előírások, biztonságos és a felhasználók és eszközök védelme érdekében. Biztonsági alapterveket csoportjai előre konfigurált Windows-beállítások, amelyek segítenek a alkalmazni egy ismert csoport, beállítások és a megfelelő biztonsági csapatok által ajánlott alapértelmezett értékeket. A biztonsági alapkonfiguráció profilok az Intune-ban való létrehozásakor próbál létrehozni egy *eszközkonfiguráció* profilt.

Ez a funkció az alábbiakra vonatkozik:

- A Windows 10-es 1809 és újabb verziók

Biztonsági alapterveket telepít a felhasználók vagy eszközök Intune-ban, és a beállítások a Windows 10 vagy újabb rendszerű eszközökre vonatkoznak. Például a *MDM biztonsági alapterv* automatikusan engedélyezi a BitLocker cserélhető meghajtók, automatikusan az eszköz zárolásának feloldásához jelszó szükséges, automatikusan letiltja, és alapszintű hitelesítést. Alapértelmezett érték a környezet nem működik, ha testre szabhatja a beállításokat kell alkalmazni az alaptervhez.  

Külön alapkonfiguráció típusok tartalmazhatnak ugyanazokat a beállításokat, de más alapértelmezett értékeit használja ezeket a beállításokat. Fontos tudni, hogy az alapterv az alapértelmezett beállításokat kíván használni, és, majd módosítsa a minden egyes referenciakonfigurációnál, hogy illeszkedjen a szervezeti igényeinek.  

> [!NOTE]
> A Microsoft nem javasolja biztonsági alapterveket előzetes verzióját használja éles környezetben. Egy előzetes alapkonfigurációját a beállításokat az előzetes verzió folyamán megváltozhatnak. 

A biztonsági alapterv használatával célja, hogy rendelkezik egy végpontok közötti biztonságos munkafolyamatot a Microsoft 365 használatakor. Az előnyök közé:

- Egy biztonsági alaptervet az ajánlott eljárásokat és javaslatokat, amely hatással van a biztonsági beállításait tartalmazza. Az azonos Windows biztonsági csapat, amely csoport házirend biztonsági előírások hoz létre az Intune-partnerek. Ezekkel az ajánlásokkal útmutatást és széles körű ismeretekkel alapulnak.
- Ha Ön új Intune-ba, és nem tudja, hogy hol kell elkezdeni, majd biztonsági előírások lehetővé teszi egy nagy előnnyel jár. Gyors létrehozása és üzembe helyezése egy biztonságos profilt, tudván, hogy Ön segítséget a munkahelyi erőforrások és adatok védelme.
- Ha jelenleg használja a csoportházirendet, felügyelethez az Intune-ba való migrálás sokkal egyszerűbb, mivel ezek alapterveket. Ezek az alapkonfigurációkat az Intune-hoz natív módon épülnek, és többek között a modern felügyeleti környezetet biztosít.



[Windows biztonsági előírások](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines) egy nagyszerű forrás, amely további információk a funkcióról. [Mobileszköz-kezelés](https://docs.microsoft.com/windows/client-management/mdm/) (MDM) egy nagyszerű forrás MDM és a Windows-eszközökön elvégezhető.

## <a name="security-baseline-versions-and-instances"></a>Biztonsági alapverziók és példányok
Időről időre új alapterv frissítései elérhetővé válnak. Egyes alapterv új verzió példányát adhatók hozzá vagy távolítsa el a beállításokat vagy más változásokat is. Például amint új Windows 10-beállítások Windows 10 új verzióval elérhetővé válnak, a mobileszköz-kezelési biztonsági alapterv kaphat egy új verzió-példányt, amely tartalmazza a legújabb beállításokat.  

Az Intune-konzolon megtekintheti, mely biztonsági előírások érhetők el, és a rájuk vonatkozó információkat. Rendelkezésre álló információt tartalmaz a rendelkezik alapterv használó hány profilok írja be, a referenciakonfiguráció típusú hány külön példányt érhetők el, és amikor utolsó legfrissebb példánya elvégezték-e rendelkezésre, vagy a közzétett.  Az alábbi példa bemutatja a csempét egy jól használt mobileszköz-kezelési biztonsági alapterv esetében:  

![Alapkonfiguráció csempe](./media/security-baselines/baseline-tile.png)

Használni, válassza ki az alapkonfigurációt, és válassza a alapverziók kapcsolatos információk megtekintéséhez **verziók**. Intune-ban a verziók adatainak megjelenítése használatban a profilok alapján. A verziók panelen válassza ki a profilokat, amelyek azt a verziót részletesebb információhoz egyetlen verziót. Is válassza ki a két különböző verziókat, és válassza a **alaptervek összehasonlítása** letöltése CSV-fájl, amely azokat a különbségeket.  

![Alapkonfigurációk összehasonlítása](./media/security-baselines/compare-baselines.png)

Amikor létrehoz egy biztonsági alaptervet *profil*, a profil automatikusan használja a legutóbb kiadott biztonsági alapkonfiguráció-példány.  Továbbra is használhatja, és szerkesztheti a korábban létrehozott használó profilok korábbi alapkonfiguráció verziójának egy példányára, beleértve az előzetes verzióval létrehozott alapkonfigurációkat. 

Alapvető biztonsági profilok támogatása egy [a verzió megváltoztatása](#change-the-baseline-instance-for-a-profile) , azon használatban van. Ez azt jelenti, amikor új verzióra, nem kell létrehozni egy új alapkonfigurációjának profilját, hogy igénybe vehesse azt. Ehelyett, amikor készen áll, is válassza ki a alapkonfigurációjának profilját, és a beépített lehetőség használatával módosítsa a példány verzióját a profilhoz.  

## <a name="available-security-baselines"></a>Biztonsági alapterveket 

A következő biztonsági alapterv példányok érhetők el az Intune-nal való használatra. A hivatkozások használatával megtekintheti a beállításokat minden egyes referenciakonfigurációnál legfrissebb példánya esetében. 

- **Mobileszköz-kezelési biztonsági alapterv**
  - [Mobileszköz-kezelési biztonsági alaptervet Spring 2019 (19 órával 1)](security-baseline-settings-mdm.md)
  - [Előzetes verzió: Mobileszköz-kezelési biztonsági alaptervet a 2018. október](security-baseline-settings-mdm-archive.md)

- **A Windows Defender ATP-alapkonfiguráció**  
  *(Ez a alapvető használatához a környezetnek használatára vonatkozó Előfeltételek kell megfelelnie [Microsoft Defender komplex veszélyforrások elleni védelem](advanced-threat-protection.md#prerequisites))* .
  - [Előzetes verzió: A Windows Defender ATP-alapkonfiguráció](security-baseline-settings-defender-atp.md)  

Továbbra is használhatja, és a egy előzetes sablon alapján, akkor is, ha az előzetes verzió sablon már nem érhető el új profil létrehozásához, amelyet korábban hozott létre profilokat. 

## <a name="prerequisites"></a>Előfeltételek
- Az Intune-ban alapkonfigurációk kezelésére, a fióknak rendelkeznie kell a [házirend- és Profilkezelő](role-based-access-control.md#built-in-roles) beépített szerepkör.

- Egyes alapkonfigurációknak használatát szükség lehet, hogy aktív a további szolgáltatásokat, például a Microsoft Defender ATP-előfizetéssel rendelkezik.  

## <a name="co-managed-devices"></a>Közösen kezelt eszközök

Az Intune által felügyelt eszközökön a biztonsági előírások hasonlóak közösen kezelt eszközök Configuration Managerrel. Közösen kezelt eszközök a System Center Configuration Manager és a Microsoft Intune használatával egyszerre kezelheti a Windows 10 rendszerű eszközökre. Lehetővé teszi a meglévő Configuration Manager befektetési és az Intune felhőalapú csatolása. [Megosztott kezelés – áttekintés](https://docs.microsoft.com/sccm/comanage/overview) van egy nagyszerű forrás, ha használja a Configuration Managert, és a felhő nyújtotta előnyök is érdemes.

Közösen kezelt eszközök használata esetén kell váltania a **eszközkonfiguráció** munkaterhelés (beállítások) az Intune-hoz. [Eszköz konfigurációs számítási feladatok](https://docs.microsoft.com/sccm/comanage/workloads#device-configuration) további információkat biztosít.

## <a name="create-the-profile"></a>A profil létrehozása

1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) majd **eszközbiztonsági** > **biztonsági előírások** elérhető alapkonfigurációk listáját.


    ![Válassza ki egy biztonsági alaptervet konfigurálása](./media/security-baselines/available-baselines.png)

2. Válassza ki szeretné használni, és válassza ki az alapkonfigurációt **profil létrehozása**.  

3. Az a **alapjai** lapra, adja meg a következő tulajdonságokat:

    - **Név**: Adja meg a biztonsági alapterveket profil nevét. Adja meg például *Defender ATP-ben a szokásos profilt*.

    - **Description** (Leírás): Adja meg, amely azt ismerteti, Mire jó ez a alapvető szöveget. A leírás megadása nem adhatja meg a kívánt szöveget. Opcionális de javasolt.  

   Válassza ki **tovább** , nyissa meg a következő lapot. Egy új lapot, speciális, kiválaszthatja a lap neve korábban megtekintett lapra való visszatéréshez.  

4. A konfigurációs beállítások lapon megtekintheti a csoportok **beállítások** , amelyek elérhetők a kiválasztott alapkonfiguráció. Kibővítheti a beállítások megtekintéséhez a csoporthoz, és ezeket a beállításokat az alaptervet az alapértelmezett értékeit. Beállítások keresése:
   - Válasszon ki egy csoportot, bontsa ki, és tekintse át a rendelkezésre álló beállításokat.  
   - Használja a *keresési* sávot, és adja meg a kulcsszavak, szűrje a nézetet megjeleníteni csak ezeket a csoportokat, amelyek tartalmazzák a keresési feltételeknek.  
 
   Egyes alapterv beállításhoz alapértelmezett konfigurációját, hogy az alapszintű verzióra. Konfigurálja újra az alapértelmezett beállításokat, az üzleti igényeinek. Különböző alaptervek előfordulhat, hogy ugyanazt a beállítást tartalmaz, és a beállítása, a baseline függően eltérő alapértelmezett értékeit használja. 

    ![Bontsa ki az adott csoport beállításainak megtekintéséhez](./media/security-baselines/sample-list-of-settings.png)

5. Az a **címkék hatókör** lapon jelölje be **válassza ki a hatókörcímkék** megnyitásához a *címkék kiválasztása* hatókörcímkék hozzárendelése a profil panelen. 

6. Az a **hozzárendelések** lapon jelölje be **válassza ki a befoglalandó csoportokat** , és hozzárendelheti az alapkonfiguráció egy vagy több csoportjára. Használat **válassza ki a kizárandó csoportokat** finomhangolása a hozzárendelést.  

   ![Profil hozzárendelése](./media/security-baselines/assignments.png)
  
7. Ha készen áll az alapkonfiguráció telepítése, lépjen a **tekintse át + létrehozása** lapra, és ellenőrizze a részleteket az alapterv esetében. Válassza ki **létrehozás** mentse és telepítse a profilt.  

   Amint a profilt hoz létre, a rendszer továbbítja a hozzárendelt csoportba, és azonnal is vonatkozhatnak.

   > [!TIP]  
   > Ha egy profil első hozzárendelése csoportok nélkül menti, ehhez a profilhoz később módosíthatja.  

   ![Tekintse át az alaptervhez](./media/security-baselines/review.png) 

  
8. Miután létrehozott egy profilt, szerkesztheti a **eszközbiztonsági** > **biztonsági előírások**, válassza ki a referenciakonfiguráció típusát, amelyet konfigurált, és válassza ki **profilok**.  Válassza ki a profilt az elérhető profilok listájából, és válassza **tulajdonságok**. Szerkesztheti az összes elérhető konfigurációs lapok beállításait, és válassza ki **felülvizsgálat + mentése** a módosítások véglegesítéséhez.  

## <a name="change-the-baseline-instance-for-a-profile"></a>Az alapkonfiguráció-példány egy profil módosítása
Alapkonfiguráció profilok támogatja a referenciakonfiguráció-példányt, amely a profilt használja. Kiválaszthatja, hogy egy régebbi példányt, vagy több általában egy azonos alapvonaltól újabb példányát.  Két különböző alapkonfigurációkat, például a profil módosításával az alapterv Defender ATP-ben a mobileszköz-kezelési biztonsági alapterv használata között nem módosítható. 

Az Alapverzió módosítását konfigurálásánál lesz sorolja fel a módosítások között részt vevő két alapverziók CSV-fájl letöltése lehetőséget. Ön is érhető el a kiválasztott azokat alkalmazni az új verzió és minden testreszabás maradjon az eredeti alapszintű verzióra, vagy minden, az alapértelmezett érték található a kiválasztott új verziójú alapkonfigurációként megvalósításához. 

Mentéskor az átalakítás befejeződése után az eredeti van azonnal áttelepült a hozzárendelt csoportok.  

**Az átalakítás során**:
- Nem használja az eredeti verzió az új beállítások vannak hozzáadva, és állítsa az alapértelmezett értékeket használja.  

- Beállítások, amelyek nem a kiválasztott új verziójú alapkonfigurációként eltávolítva, és már nem kényszeríti ki a biztonsági alapkonfigurációjának profilját.  

  Ha egy beállítás már nem kezeli a alapkonfigurációjának profilját, ez a beállítás nem beállításokat az eszközön. Ehelyett a beállítás esetén az eszköz marad, amíg egy másik folyamat az utolsó konfigurációban kezeli a beállítás módosításához. Olyan folyamatokat, amelyek egy beállítást módosíthatja, miután leállította az azt felügyelő például egy másik alapkonfigurációjának profilját, egy csoportházirend-beállítás vagy az eszközön végrehajtott manuális konfiguráció. 

### <a name="to-change-the-instance-for-a-baseline"></a>Az alapterv-példány módosítása  

1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) majd **eszközbiztonsági** > **biztonsági előírások**, majd válassza a csempe a referenciakonfiguráció-típus, amely rendelkezik a kívánt profilt módosíthatja.  

2. Majd **profilok**, majd válassza ki a kívánt profilt, szerkesztheti, és válassza ki a jelölőnégyzetet **verzió módosítása**.  

   ![Válassza ki az alapkonfigurációt](./media/security-baselines/select-baseline.png)  

3. A a **verzió módosítása** ablaktáblán, használja a **válassza ki a frissíteni egy biztonsági alaptervet** legördülő menüből, és válassza ki a használni kívánt verzió példányt.  

   ![verzió kiválasztása](./media/security-baselines/select-instance.png)  
   
4. Válassza ki **felülvizsgálati frissítés** profilok jelenlegi példány és az új verzió kiválasztott különbségének tartalmazó CSV-fájl letöltéséhez. Tekintse át ezt a fájlt, hogy megismerte, hogy mely beállítások lettek hozzáadva, eltávolítva, és ezeknek a beállításoknak az alapértelmezett értékeket a frissített profil.  

   Ha elkészült, folytassa a következő lépéssel.  

5. Válassza ki a két lehetőség egyikét **módszer a profil frissítése**: 
   - **Alapterv-módosítások elfogadásához, de ne a testreszabások beállítás meglévő** – Ez a beállítás megőrzi a alapkonfigurációjának profilját a testreszabott, és alkalmazza őket az új verziót használja választotta.
   - **Alapterv-módosítások elfogadásához, és elveti a testreszabások beállítás meglévő** – Ez a beállítás felülírja az eredeti profil teljesen. A frissített profil összes beállítás az alapértelmezett értékeket fogja használni.  

6. Válassza ki **elküldése**. A kiválasztott alapszintű verzióra, és az átalakítás befejeződése után a profilt frissítések, az alapkonfiguráció azonnal ismét üzembe helyezi a hozzárendelt csoportok.

## <a name="remove-a-security-baseline-assignment"></a>Egy biztonsági alapterv-hozzárendelés eltávolítása
Ha egy eszköz már nem vonatkozik a biztonsági alapkonfiguráció beállítás, illetve az alapterv-beállításaiban *nincs konfigurálva*, ezeket a beállításokat az eszközön nem térhet előre felügyelt konfigurációra. Ehelyett a korábban felügyelt beállításokat az eszközön tartsa a legutóbbi konfigurációját, mivel az alapkonfiguráció kapott, amíg egy másik folyamat frissíti ezeket a beállításokat az eszközön.  

Egyéb folyamatokat, amelyek előfordulhat, hogy később megváltoztatja az eszközön található beállítások közé tartozik a különböző vagy új biztonsági alapterv, eszközkonfigurációs profil, a csoportházirend-konfigurációk vagy az eszközön beállítás manuális szerkesztése.  





## <a name="q--a"></a>Kérdések és válaszok

#### <a name="why-these-settings"></a>Miért ezek a beállítások?

A Microsoft biztonsági csoportja van tapasztalata közvetlenül, a Windows-fejlesztőknek és a biztonsági Közösséggel ezek a javaslatok létrehozása. Ez a alapvető beállításait a leginkább releváns biztonsági konfigurációs beállítások minősülnek. Az egyes Windows új verzióját a csapat megjeleníti a javaslatokat, újonnan kiadott funkciókat alapján állítja be.

#### <a name="is-there-a-difference-in-the-recommendations-for-windows-security-baselines-for-group-policy-vs-intune"></a>Van különbség a Windows biztonsági alapterveket a csoport házirend vs kapcsolatos ajánlások. Intune-ban?

A azonos biztonsági csoportja úgy döntött, és a beállítások minden egyes referenciakonfigurációnál rendezve. Az Intune a vonatkozó beállítások az Intune-ban biztonsági alapkonfiguráció tartalmaz. Van még néhány a csoport házirend alapkonfiguráció egy helyi tartományvezérlő jellemző. Ezek a beállítások az Intune javaslatok nem tartoznak. A többi beállítás megegyeznek.

#### <a name="are-the-intune-security-baselines-cis-or-nsit-compliant"></a>Az Intune-ban biztonsági előírások CI-k vagy a megfelelő NSIT?

Szigorúan véve, nem. A Microsoft biztonsági csapat olvas, szervezetek, például a CI-k, a fordítási javaslatait. De "CIS-kompatibilis" és a Microsoft alaptervek között egy-az-egyhez leképezés nem létezik.

#### <a name="what-certifications-does-microsofts-security-baselines-have"></a>Milyen minősítések rendelkezik a Microsoft biztonsági előírások? 

- A Microsoft továbbra is a biztonsági előírások a csoportházirendek (GPO-k) közzététele és a [biztonsági megfelelőségi eszközkészlet](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10), mert már sok éve van. Ezek alaptervek számos vállalat használja. A javaslatokat ezen alaptervek a vállalati ügyfelekkel és a külső ügynökségek, beleértve a védelmi Minisztérium (DoD), nemzeti szabványügyi és Technology (NIST) a Microsoft biztonsági csapat engagement származnak. Osztjuk meg a javaslatok és alaptervek ezek szervezetekkel. Ezek a szervezetek saját javaslatok, amelyek szorosan tükrözik a Microsoft javaslatokat is. Mobileszköz-felügyelet (MDM) fejlesztéseiről a felhőbe, a Microsoft ezen csoport házirend alapkonfigurációkat egyenértékű MDM javaslatok hozta létre. Ezek további alaptervek beépített Microsoft Intune-ba, és a felhasználók, csoportok és hajtsa végre a (vagy nem) az alapkonfiguráció megfelelőségi jelentéseket tartalmazza.

- Számos ügyfél használja az Intune általános javaslatok kiindulási pontként, és majd szabja testre a felel meg az informatikai és biztonsági igényeinek. A Microsoft Windows 10-es RS5 **MDM biztonsági alapterv** az első alapkonfiguráció felszabadítása érdekében. Ez a alapvető általános infrastruktúra, amely lehetővé teszi az ügyfelek számára, végül importálja a többi CI-k, NIST és más szabványok alapján biztonsági előírások épül. Jelenleg Windows érhető el, és végül fogja tartalmazni, iOS és Android rendszerhez.

- Áttérés a helyszíni Active Directory csoportházirendjei-ről az Azure Active Directory (AD) használatával a Microsoft Intune-nal tiszta felhőalapú megoldásokhoz. Annak érdekében, vannak a csoportházirend-sablon szerepel a [biztonsági megfelelőségi eszközkészlet](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10) , amelyek segítségével kezelheti az Azure AD-hez csatlakoztatott eszközök és a hibrid AD. Ezek az eszközök beszerezheti a mobileszköz-kezelési beállításokat a felhőből (Intune) és a csoportházirend-beállítások helyi tartományvezérlőkön, szükség szerint.

## <a name="next-steps"></a>További lépések
- A beállítások megtekintéséhez a legújabb verziói az elérhető alapkonfigurációk:  
  - [Mobileszköz-kezelési biztonsági alapterv](security-baseline-settings-mdm.md)  
  - [A Windows Defender ATP-alapkonfiguráció](security-baseline-settings-defender-atp.md)  

- Ellenőrizze az állapotát és a figyelő a [alapkonfiguráció és a profil](security-baselines-monitor.md).

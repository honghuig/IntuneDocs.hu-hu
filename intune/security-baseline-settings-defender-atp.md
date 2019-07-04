---
title: Az Intune biztonsági alapterveket beállításai a Microsoft Defender komplex veszélyforrások elleni védelem
titleSuffix: Microsoft Intune
description: Biztonsági alapkonfiguráció beállítások az Intune által támogatott Microsoft Defender komplex veszélyforrások elleni védelem kezelése
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/29/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: karthib
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5bdd2171853a8db944c910ef4d912f7681d17077
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/03/2019
ms.locfileid: "67549130"
---
# <a name="microsoft-defender-advanced-threat-protection-baseline-settings-for-intune"></a>Intune-hoz készült Microsoft Defender komplex veszélyforrások elleni védelem alapbeállítások

Tekintse meg a Microsoft Intune által támogatott Microsoft Defender komplex veszélyforrások elleni védelem (korábbi nevén a Windows Defender komplex veszélyforrások elleni védelem) alapértelmezett beállításait. A komplex veszélyforrások elleni védelem (ATP) alapterv alapértelmezett értékeket jelölik az ATP ajánlott konfigurációját, és nem egyeznek meg a referenciakonfiguráció más biztonsági előírások alapértelmezett értéket.  

  Ha a környezet megfelel-e használatára vonatkozó Előfeltételek érhető el a Microsoft Defender komplex veszélyforrások elleni védelem alapkonfiguráció [Microsoft Defender komplex veszélyforrások elleni védelem](advanced-threat-protection.md#prerequisites)).




> [!NOTE]  
> Az ATP alapkonfiguráció beállítás **előzetes**. Az előzetes verzió, a listában a rendelkezésre álló beállítások, valamint a sorrendet, amelyben ez a tartalom megadja ezeket a beállításokat, előfordulhat, hogy egyeznek meg a portálon.  
>
> Az alapbeállítások előzetes esnek, ez a tartalom frissülni fognak, hogy a biztonsági alapkonfiguráció beállítások az Intune által támogatott aktuális listáját.

## <a name="application-guard"></a>Alkalmazásőr  
További információkért lásd: [WindowsDefenderApplicationGuard CSP](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp) a Windows dokumentációjában.  

A Microsoft Edge használatakor a Microsoft Defender Application Guard megvédi környezetét a szervezet számára nem megbízható helyekről. Amikor a felhasználók a webhelyeket, amely nem szerepel a elkülönített hálózat határát, a helyek nyissa meg a Hyper-V virtuális böngészési munkamenetben. Megbízható helyek határozzák meg egy hálózathatárt.  

- **Application Guard** - *Settings/AllowWindowsDefenderApplicationGuard*  
  Válassza ki *Igen* , kapcsolja be ezt a szolgáltatást, amely nem megbízható webhelyek egy Hyper-V virtualizált böngészési tárolóban nyitja meg. Ha a beállítása *nincs konfigurálva*, egyetlen helyhez sem (megbízható és nem megbízható) megnyitja az eszközön, és nem virtualizált tárolóban.  

  **Alapértelmezett**: Igen
 
  - **Vállalati webhelyeken lévő külső tartalom** - *beállítások/BlockNonEnterpriseContent*  
    Válassza ki *Igen* való betöltését nem jóváhagyott webhelyekről származó tartalom blokkolása. Ha a beállítása *nincs konfigurálva*, nem vállalati helyek megnyithatja az eszközön. 
 
    **Alapértelmezett**: Igen

  - **A vágólap viselkedése** - *beállítások/ClipboardSettings*  
    Válassza ki a helyi számítógép és az Alkalmazásőr virtuális böngészőjében között milyen másolási és beillesztési műveletek engedélyezettek.  A lehetőségek a következők:
    - *Nincs konfigurálva*  
    - *Mindkét letiltása* -adatokat nem tudja áthelyezni a számítógép és a virtuális böngésző között.  
    - *Tároló letiltása gazdagép* -adatok a számítógépről nem tudja áthelyezni a virtuális böngészőben.
    - *Blokk-tárolóból a gazdagépre* -adatokat nem tudja áthelyezni a virtuális böngészőből a gazdagép PC.
    - *Nincs letiltása* – nincs tartalom létezik letiltása.  

    **Alapértelmezett**: Mindkét letiltása  

- **Windows hálózati elkülönítési szabályzat – a vállalati hálózati tartománynevek**  
  További információkért lásd: [házirend CSP - NetworkIsolation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-networkisolation) a Windows dokumentációjában.
  
  Tartományok, IP-címtartományok és hálózati határok, amely az Application Guard vállalati helyként kezeli a felhőben üzemeltetett vállalati erőforrás listáját adja meg.  

  **Alapértelmezett**: securitycenter.windows.com

## <a name="application-reputation"></a>Alkalmazás-megbízhatósági besorolása  

További információkért lásd: [házirend CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) a Windows dokumentációjában.

- **Nem ellenőrzött fájlok futtatásának letiltása**  
    A felhasználó nem futtathat ellenőrizetlen fájlokat. Ha a beállítása *nincs konfigurálva*, alkalmazottak figyelmen kívül hagyja a SmartScreen-figyelmeztetéseket, és a kártevő fájlokat futtathat. Állítsa be *Igen* , hogy az alkalmazottak nem SmartScreen vonatkozó figyelmeztetések mellőzése és a kártevő fájlokat futtathat.  
  
    **Alapértelmezett**: Igen

- **SmartScreen-üzenetek szükséges alkalmazások és fájlok**  
  Állítsa be *Igen* a Windows SmartScreen engedélyezése.  

  **Alapértelmezett**: Igen

## <a name="attack-surface-reduction"></a>Támadási felület csökkentése  

- **Office-alkalmazások indítsa el a gyermek-folyamat típusa**  
  [Támadási felület csökkentésére szolgáló szabály](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – Ha beállítása *blokk*, Office-alkalmazások szükséges gyermekelemek létrehozásához a folyamatok nem engedélyezett. Office alkalmazások közé tartoznak a Word, Excel, PowerPoint, a OneNote és a hozzáférés. Egy alárendelt folyamat létrehozása egy tipikus kártevő működés, különösen a makró-alapú támadásokkal szemben, amelyek az Office-alkalmazások elindításához, vagy letöltheti a rosszindulatú végrehajtható fájlok.  

  **Alapértelmezett**: Letiltás

- **Parancsfájl letöltött tartalom végrehajtási típusa**  
  [Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection) – adja meg, hogy töltse le, vagy próbálja meg telepíteni a vélhetően nemkívánatos alkalmazások észlelése egy szintjét.  

  **Alapértelmezett**: Letiltás 

- **Hitelesítő adatok lopásának megjelölése típus megakadályozása**  
  Állítsa be *engedélyezése* való [védelem származtatott tartományi hitelesítő adatok a Credential Guard](https://docs.microsoft.com/windows/security/identity-protection/credential-guard/credential-guard). Windows Defender Credential Guard virtualizálás-alapú biztonsági használatával elkülöníteni a titkos kódok, hogy csak a kiemelt jogosultságú rendszerszoftverek férhessenek hozzá őket. A titkos kódokhoz való illetéktelen hozzáférés a hitelesítési adatok ellopását okozó (például pass-the-hash vagy pass-the-ticket típusú) támadásokhoz vezethetnek. Windows Defender Credential Guard megakadályozza, hogy ezeket a támadásokat NTLM-jelszókivonatok, a Kerberos jegymegadási jegyek és a tartományi hitelesítő adatok, alkalmazások által tárolt hitelesítő adatok ellenőrzését.  

  **Alapértelmezett**: Engedélyezés

- **E-mailek tartalmának végrehajtási típus**  
  [Támadási felület csökkentésére szolgáló szabály](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – Ha beállítása *blokk*, a szabály blokkolja a következő fájl futtatása vagy a Microsoft Outlook vagy a webes levelezésben (például Gmail.com vagy Outlook.com) látható e-mailt indított típusok:  

  - Végrehajtható fájlok (például .exe, .dll vagy .scr)  
  - Parancsfájlok (például egy PowerShell .ps, Basic .vbs vagy .js JavaScript-fájl)  
  - Archív fájlok parancsfájl  

  **Alapértelmezett**: Letiltás

- **Az Adobe Reader indítása egy gyermek folyamatban**  
  [Támadási felület csökkentésére szolgáló szabály](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – *engedélyezése* Ez a szabály blokkolja az Adobe Reader hozzon létre egy alárendelt folyamat. Pszichológiai manipuláció vagy az azokat kihasználó támadások ellen kártevő szoftverek letöltheti, és indítsa el a további is észleltünk adattartalmakat. és az Adobe Reader kívül break.  

  **Alapértelmezett**: Engedélyezés

- **Parancsfájl rejtjelezett makró kód típusa**  
  [Támadási felület csökkentésére szolgáló szabály](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – kártevők és más fenyegetések ellen is megkísérelheti rejtse, és a rosszindulatú kódot az egyes parancsfájl fájlok elrejtése. Ez a szabály megakadályozza a parancsfájlok, amelyek futtatását úgy tűnik, hogy rejtjelezett lehet.  
    
  **Alapértelmezett**: Letiltás

- **Nem megbízható USB-folyamat típusa**  
  [Támadási felület csökkentésére szolgáló szabály](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – Ha beállítása *blokk*, aláíratlan vagy nem megbízható végrehajtható fájlok cserélhető USB-meghajtók, és nem futtatható, SD-kártyán.

  Végrehajtható fájlok a következők:
  - Végrehajtható fájlok (például .exe, .dll vagy .scr)
  - Parancsfájlok (például egy PowerShell .ps, Basic .vbs vagy .js JavaScript-fájl)  

  **Alapértelmezett**: Letiltás

- **Egyéb Office-alkalmazások feldolgozásához injektálási típusa**  
  [Támadási felület csökkentésére szolgáló szabály](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) -érték beállítása *blokk*, többek között a Word, Excel, PowerPoint és OneNote-ot, Office-alkalmazások más folyamatokba való nem injektovat kód. Kódinjektálás általában kártevő futtatására szolgál rosszindulatú kódot próbál a víruskereső vizsgálati motorokból tevékenység elrejtéséhez.  

  **Alapértelmezett**: Letiltás

- **Office-makrók letiltására szolgáló kód engedélyezése Win32 importálás típusa**  
  [Támadási felület csökkentésére szolgáló szabály](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) -érték beállítása *blokk*, ez a szabály próbál letiltása az Office-fájlokat importálhatja a Win32 dll-EK, amelyik tartalmaz. Office-fájlok közé tartoznak a Word, Excel, PowerPoint és OneNote-ban. Kártevő szoftverek importálása és betölteni a Win32 dll-EK, majd API-hívásokat, hogy további fertőzéstől a rendszerben használt használhatják Office-fájlok makrók letiltására szolgáló kódot.  

  **Alapértelmezett**: Letiltás

- **Az Office kommunikációs alkalmazások indítása egy gyermek folyamatban**  
  [Támadási felület csökkentésére szolgáló szabály](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – Ha beállítása *engedélyezése*, ez a szabály megakadályozza, hogy az Outlook alárendelt folyamatok létrehozásával. Blokkolja egy alárendelt folyamat létrehozása, ez a szabály pszichológiai manipuláció támadások ellen védi, és megakadályozza, hogy a biztonsági rés kiaknázása elleni kód visszaél az Outlookban biztonsági rést.  

  **Alapértelmezett**: Engedélyezés

- **Office alkalmazások végrehajtható tartalom létrehozása vagy az indítási típusa**  
  [Támadási felület csökkentésére szolgáló szabály](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – Ha beállítása *blokk*, Office-alkalmazások nem hozható létre végrehajtható tartalmat. Office alkalmazások közé tartoznak a Word, Excel, PowerPoint, a OneNote és a hozzáférés.  

  Ez a szabály a gyanús és kártékony bővítményeket és parancsfájlokat (bővítmények), hogy hozzon létre, vagy indítsa el a végrehajtható fájlok által használt jellemző viselkedés célozza. Ez a jellemző kártevő technika. Bővítmények az Office-alkalmazások által használt le lesznek tiltva. Általában ezek használja a Windows Scripting Host (.wsh fájlok), amely bizonyos feladatok automatizálására, vagy adja meg a felhasználó által létrehozott bővítmény szolgáltatásai parancsfájlok futtatása.

  **Alapértelmezett**: Letiltás

## <a name="bitlocker"></a>BitLocker  

További információ [a BitLocker csoportházirend-beállítások](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings) a Windows dokumentációjában.  

- **Eszközök titkosítása**  
  Válassza ki *Igen* ahhoz, hogy a BitLocker eszköz titkosítását. Eszköz hardver- és Windows-verziót, attól függően eszközök felhasználói számára, győződjön meg arról, hogy nincs-e az eszközön nem külső titkosítási kérheti. Windows-titkosítás bekapcsolását, amíg aktív külső titkosítási jelenik meg az eszköz instabillá válhat.  

   **Alapértelmezett**: Igen

- **Bit széfjét a cserélhető meghajtót házirend**  
  A szabályzat határozza meg, hogy a titkosítás a BitLocker által a cserélhető meghajtók titkosítását erősségét. Vállalatok szabályozhatja a titkosítás szintjét, a biztonság fokozása érdekében (AES-256-ot az AES-128-nál nagyobb). Ha *Igen* ahhoz, hogy ez a beállítás, megadható egy titkosítási algoritmus és a fő erőssége rögzített adatmeghajtókon, operációsrendszer-meghajtók és eltávolítható adatmeghajtókon külön-külön. A rögzített és operációs rendszert tartalmazó meghajtókon azt javasoljuk az XTS-AES algoritmus használata. A cserélhető meghajtók használjon AES-CBC 128 bites vagy AES-CBC 256 bites Ha a meghajtó eszközöktől, amelyek nem futnak Windows 10-es, 1511-es vagy újabb verzióját használja. A titkosítási mód módosítása nem befolyásolja, ha a meghajtó már titkosítva van, vagy ha a titkosítás folyamatban van. Ebben az esetben figyelmen kívül ezt a beállítást. 

  Bit széfjét a cserélhető meghajtót házirend esetén adja meg a következő beállításokat:

    - **Titkosítás megkövetelése az írási hozzáférés**  
      **Alapértelmezett**: Igen

    - **Titkosítási módszer**  
      **Alapértelmezett**: AES 128bit CBC

- **Rögzített meghajtó házirend bit széfjének**  
  A házirend határozza meg, hogy a titkosítás a BitLocker által rögzített meghajtók titkosítását erősségét. Vállalatok szabályozhatja a titkosítás szintjét, a biztonság fokozása érdekében (AES-256-ot az AES-128-nál nagyobb). Ha engedélyezi ezt a beállítást, konfigurálhatja egy titkosítási algoritmus és a fő erőssége a rögzített adatmeghajtók, operációsrendszer-meghajtók és a cserélhető adatmeghajtók külön-külön. A rögzített és operációs rendszert tartalmazó meghajtókon azt javasoljuk az XTS-AES algoritmus használata. A cserélhető meghajtók használjon AES-CBC 128 bites vagy AES-CBC 256 bites Ha a meghajtó eszközöktől, amelyek nem futnak Windows 10-es, 1511-es vagy újabb verzióját használja. A titkosítási mód módosítása nem befolyásolja, ha a meghajtó már titkosítva van, vagy ha a titkosítás folyamatban van. Ebben az esetben figyelmen kívül ezt a beállítást.

  A Bit széfjének rögzített meghajtó házirend a következő beállításokat:

    - **Titkosítás megkövetelése az írási hozzáférés**  
      **Alapértelmezett**: Igen

    - **Titkosítási módszer**  
      **Alapértelmezett**: AES 128bit XTS

- **Bit széfjének Rendszerházirend meghajtó**  
  A házirend határozza meg, hogy a titkosítás a BitLocker által a rendszermeghajtó titkosítását erősségét. Vállalatok előfordulhat, hogy kívánják vezérelni a titkosítás szintjét, a biztonság fokozása érdekében (AES-256-ot az AES-128-nál nagyobb). Ha engedélyezi ezt a beállítást, konfigurálhatja egy titkosítási algoritmus és a fő erőssége a rögzített adatmeghajtók, operációsrendszer-meghajtók és a cserélhető adatmeghajtók külön-külön. A rögzített és operációs rendszert tartalmazó meghajtókon azt javasoljuk az XTS-AES algoritmus használata. A cserélhető meghajtók használjon AES-CBC 128 bites vagy AES-CBC 256 bites Ha a meghajtó eszközöktől, amelyek nem futnak Windows 10-es, 1511-es vagy újabb verzióját használja. A titkosítási mód módosítása nem befolyásolja, ha a meghajtó már titkosítva van, vagy ha a titkosítás folyamatban van. Ebben az esetben figyelmen kívül ezt a beállítást.  

  Bit széfjének rendszer meghajtó házirend esetén adja meg a következő beállításokat:  

  - **Titkosítási módszer**  
    **Alapértelmezett**: AES 128bit XTS

## <a name="device-control"></a>Eszköz-vezérlő  

- **Cserélhető adathordozók vizsgálata teljes vizsgálat során**  
  [Defender/AllowFullScanRemovableDriveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) -érték beállítása *Igen*, Defender megvizsgálja a cserélhető meghajtók, például a pendrive, a rosszindulatú vagy nemkívánatos szoftver teljes vizsgálat során. Defender víruskereső USB-eszközök az összes fájlt megvizsgálja-fájlokat az USB-eszköz futtatása előtt.

  A listában szereplő kapcsolódó beállításai: *Defender/AllowFullScanOnMappedNetworkDrives*  

  **Alapértelmezett**: Igen

- **A külső eszközök nem kompatibilisek a Kernel DMA védelmet enumerálási**  
   Lásd: *DmaGuard/DeviceEnumerationPolicy* a [CSP - DmaGuard házirend](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy)

  Ez a szabályzat külső DMA-kompatibilis eszközök ellen további biztonságot nyújt. Az enumerálás a DMA eszköz memória elkülönítése és az elszigetelés kompatibilis külső képes a DMA-eszközök feletti ellenőrzés lehetővé teszi.

  Ez a szabályzat csak akkor lép érvénybe, ha Kernel DMA védelem támogatott, és a rendszer belső vezérlőprogramja által engedélyezett. Kernel DMA védelmi funkciója platform, amely nem vezérelhető, házirend, vagy a felhasználó-eszköz. Támogatnia kell ezt a rendszer a gyártási idején. 

  Ellenőrizze, hogy ha a rendszer támogatja-e a Kernel DMA védelem, futtassa az MSINFO32.exe a rendszeren, és tekintse át a *Kernel DMA védelem* mezőt az összefoglalás lapon.  

  A lehetőségek a következők: 
  - *Eszköz alapértelmezése* – után jelentkezzen be, vagy a képernyő zárolásának feloldásához DMA újramegfeleltetése kompatibilis illesztőprogramok bármikor számbavétele engedélyezett eszközök. A DMA nem kompatibilis illesztőprogramok újramegfeleltetése eszközök csak lehet enumerálni, miután a felhasználó feloldja a képernyő
  - *Lehetővé teszi az összes* – minden külső DMA-kompatibilis PCIe eszközök felsorolandó bármikor
  - *Minden* -kompatibilis illesztőprogramok újramegfeleltetése DMA-eszközök engedélyezett bármikor számbavétele. A DMA nem kompatibilis illesztőprogramok újramegfeleltetése eszköz elindításához, és végezze el a DMA bármikor soha nem lesz engedélyezett.

  **Alapértelmezett**: Eszköz alapértelmezése

- **A készülékazonosítók hardver eszköz telepítése**  
  [DeviceInstallation/PreventInstallationOfMatchingDeviceIDs](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdeviceids) – ezt a házirendet, a Plug and Play hardverazonosítók és, hogy Windows rendszer akadályozza eszközökhöz kompatibilis azonosítók listájának megadását. A házirend-beállítás élvez bármely más házirend-beállítás lehetővé teszi, hogy a Windows eszköz telepítése. Ha ez a szabályzatbeállítás engedélyezi (állítsa *hardveres eszköz telepítést*), Windows rendszer akadályozza egy eszközt, amelynek hardveres vagy kompatibilis azonosítója megjelenik a listában hoz létre. Ha engedélyezi ezt a beállítást, a távoli asztali kiszolgálón, a szabályzat irányíthassa át a megadott eszközök, a távoli asztali ügyfélhez a távoli asztali kiszolgálónak van hatással. Ha letiltja vagy nem konfigurálja ezt a beállítást (állítsa *hardveres eszköz telepítésének engedélyezése*), eszközök telepíthesse és frissíthesse az engedélyezett vagy egyéb házirend-beállítás megakadályozta abban.  

  **Alapértelmezett**: Blokk hardveres eszköz telepítése  

  Amikor *hardveres eszköz telepítést* van kijelölve, a következő beállítások érhetők el.
  - **Megfelelő hardveres eszközök eltávolítása**  
    Ez a beállítás nem érhető el, csak ha *hardveres eszköz telepítése által készülékazonosítók* értékre van állítva *hardveres eszköz telepítést*.  

    **Alapértelmezett**: *Alapértelmezett konfiguráció nélkül*

  - **Hardver eszközök azonosítói nem futtatható**  
    Ez a beállítás nem érhető el, csak ha *hardveres eszköz telepítése által készülékazonosítók* értékre van állítva *hardveres eszköz telepítést*. Konfigurálja a beállítást, bontsa ki a lehetőséget, válassza a **+ Hozzáadás**, majd adja meg a letiltani kívánt hardver eszközazonosító.  

    **Alapértelmezett**: *Nincsenek eszközök le vannak tiltva.*  

- **Közvetlen memória-hozzáférés letiltása**  
  [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess) -közvetlen memória-hozzáférés (DMA) letiltása az összes gyakran használt adatok moduláris PCI alsóbb rétegbeli portok az eszközön, mindaddig, amíg a felhasználó bejelentkezik a Windows e Szabályzatbeállítással. Miután egy felhasználó bejelentkezik, a Windows enumerálnia a PCI-eszköz csatlakozik a gazdagép beépülő PCI portokat. Minden alkalommal, amikor a felhasználó a gép zárolja, DMA le van tiltva a gyakori elérésű beépülő PCI portokon gyermekek eszközökkel nem rendelkező mindaddig, amíg a felhasználó újra bejelentkezik. Már enumerálták, amikor a számítógép zárolása fel lett oldva eszközök továbbra is működni, amíg nem választható le. 

  A házirend-beállítás csak akkor lép érvénybe, ha a BitLocker vagy az eszköztitkosítás engedélyezve van.  

  **Alapértelmezett**: Igen


- **A telepítő osztályok hardveres eszköz telepítése**  
  [DeviceInstallation/AllowInstallationOfMatchingDeviceSetupClasses](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdevicesetupclasses) – az ezzel a szabályzattal megadhatja, hogy a telepítő osztály globálisan egyedi azonosítóra (GUID), hogy Windows rendszer akadályozza az eszközillesztők eszköz listáját. A házirend-beállítás élvez bármely más házirend-beállítás lehetővé teszi, hogy a Windows eszköz telepítése. Ha engedélyezi ezt a házirend-beállítást (állítsa *hardveres eszköz telepítést*), a Windows rendszer akadályozza, vagy frissítési eszköz-illesztőprogramokat, akinek az eszközét a telepítő osztály GUID szerepelnek a listán, hoz létre. Ha engedélyezi ezt a beállítást, a távoli asztali kiszolgálón, a házirend-beállítást befolyásolja irányíthassa át a megadott eszközök, a távoli asztali ügyfélhez a távoli asztali kiszolgálónak. Ha letiltja vagy nem konfigurálja ezt a beállítást (állítsa *hardveres eszköz telepítésének engedélyezése*), a Windows telepítheti, és frissítési eszközök engedélyezett, vagy egyéb házirend-beállítás megakadályozza.  

  **Alapértelmezett**: Blokk hardveres eszköz telepítése

  Amikor *hardveres eszköz telepítést* van kijelölve, a következő beállítások érhetők el.  

  - **Megfelelő hardveres eszközök eltávolítása**  
    Ez a beállítás nem érhető el, csak ha *hardveres eszköz telepítése a telepítő osztályok* értékre van állítva *hardveres eszköz telepítést*.  
 
    **Alapértelmezett**: *Alapértelmezett konfiguráció nélkül*  

  - **Hardver eszközök azonosítói nem futtatható**  
    Ez a beállítás csak akkor, ha a hardveres eszköz telepítése a telepítő osztályok hardveres eszköz telepítése blokkolására van beállítva érhető el. Konfigurálja a beállítást, bontsa ki a lehetőséget, válassza a **+ Hozzáadás**, majd adja meg a letiltani kívánt hardver eszközazonosító.  
 
    **Alapértelmezett**: *Nincsenek eszközök le vannak tiltva.*

## <a name="endpoint-detection-and-response"></a>Végpont észlelés és válasz  
További információkért lásd: [WindowsAdvancedThreatProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/windowsadvancedthreatprotection-csp) a Windows dokumentációjában.  

- **Telemetriai jelentések gyakoriságának növelése** - *konfigurációs/TelemetryReportingFrequency*  

  A Microsoft Defender komplex veszélyforrások elleni védelem telemetriai jelentések gyakoriságának növelése.  

  **Alapértelmezett**: Igen

- **Minták megosztása minden fájlhoz** - *konfigurációs/SampleSharing*  

  Visszaad vagy beállít a Microsoft Defender komplex veszélyforrások elleni védelem Mintamegosztás konfigurációs paraméter.  

  **Alapértelmezett**: Igen

## <a name="exploit-protection"></a>Biztonsági rés kiaknázása elleni védelem  

- **Biztonsági rés kiaknázása elleni védelem XML**  
  További információkért lásd: [importálása, exportálása és telepítése a biztonsági rés kiaknázása elleni védelem konfigurációk ](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/import-export-exploit-protection-emet-xml) a Windows dokumentációjában.  

  Lehetővé teszi a rendszergazda leküldenie egy kívánt rendszer és alkalmazás kockázatcsökkentési beállításokat a szervezet összes eszközre jelölő konfigurációt. A konfigurációs XML képviseli. 

  Biztonsági rés kiaknázása elleni védelem segít vonatkozik eszközök védelme a kártevők, amelyek a biztonsági rések használatával elosztani és fertőznek. A Windows biztonsági alkalmazás vagy a PowerShell használatával létrehozhat egy csoportot (más néven a konfigurációs) megoldások. Ez a konfiguráció exportálása XML-fájlba, majd ossza meg több gépet a hálózaton úgy, hogy az összes ugyanazokat a kockázatcsökkentési beállításokat.
 
  Képes konvertálni, és egy meglévő EMET konfigurációs XML-fájl importálása egy biztonsági rés kiaknázása elleni védelem konfigurációs XML-jét.

- **Block biztonsági rés kiaknázása elleni védelem felülbírálása**  
  [WindowsDefenderSecurityCenter/DisallowExploitProtectionOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disallowexploitprotectionoverride) – állítsa *Igen* meg, hogy a felhasználók ne módosíthassák a biztonsági rés kiaknázása elleni védelem beállításainak az a Windows Defender biztonsági központ. Ha letiltja vagy nem konfigurálja ezt a beállítást, akkor a helyi felhasználók módosíthatja a biztonsági rés kiaknázása elleni védelem beállítások területen.  
  **Alapértelmezett**: Igen  

- **Az ellenőrzött mappahozzáférés révén**  
  Lásd: [Defender/ControlledFolderAccessAllowedApplications](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-controlledfolderaccessallowedapplications) és [Defender/ControlledFolderAccessProtectedFolders](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-controlledfolderaccessprotectedfolders) 
  
   Fájlok és mappák védelme a nemkívánatos alkalmazások által végrehajtott, jogosulatlan módosítások ellen.

  **Alapértelmezett**: Vizsgálati üzemmód

## <a name="web-network-protection"></a>Webes hálózatvédelem  

- **Hálózati védelem típusa**  
  [Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection) – Ez a szabályzat lehetővé teszi, hogy kapcsolja be a Windows Defender Exploit Guard hálózatvédelem be- vagy kikapcsolása. Hálózatvédelem funkciója a Windows Defender Exploit Guard, amely védelmet biztosít az alkalmazottak az Internet elérésére folytathatnak, a biztonsági rés kiaknázása elleni futtató helyek és a rosszindulatú bármilyen alkalmazást használja. Ez magában foglalja, megakadályozza, hogy a külső böngészők veszélyes helyekre csatlakozzanak.  

  Ha a termékeken beállítása *engedélyezése* vagy *rendszervizsgálati módban*, felhasználókat nem lehet kikapcsolni a hálózatvédelem, és a Windows Defender biztonsági központ segítségével kapcsolódási kísérletek kapcsolatos információk megtekintéséhez.  
 
  - *Engedélyezése* blokkolja a felhasználók és alkalmazások veszélyes tartományokhoz csatlakozzon.  
  - *Vizsgálati üzemmód* nem tiltja a felhasználók és alkalmazások veszélyes tartományokhoz csatlakozzon.  

  Ha a beállítása *felhasználó által definiált*, felhasználók vagy alkalmazások nincsenek letiltva a veszélyes tartományokhoz való kapcsolódást és a kapcsolatokról információt nem érhető el a Windows Defender biztonsági központban.  

  **Alapértelmezett**: Vizsgálati üzemmód

- **A Microsoft Edge SmartScreen megkövetelése**  
  [Böngésző/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen) – Microsoft Edge a Windows Defender SmartScreen (bekapcsolva) használ a felhasználók megvédeni a potenciális adathalászattal és a kártevő szoftverek alapértelmezés szerint. Alapértelmezés szerint ez a szabályzat engedélyezve van (állítsa *Igen*), ha engedélyezve van, és meggátolja a felhasználókat a Windows Defender SmartScreen kikapcsolásával.  Ha egy eszközhöz hatékony házirend egyenlő nincs konfigurálva, bármikor kikapcsolhatják a Windows Defender SmartScreen, így az eszköz nem védett.  

  **Alapértelmezett**: Igen
  
- **Rosszindulatú webhelyelérés letiltása**  
  [Böngésző/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride) – alapértelmezés szerint a Microsoft Edge lehetővé teszi a felhasználók kihagyhatják (figyelmen kívül hagyása) a Windows Defender SmartScreen-figyelmeztetések potenciálisan rosszindulatú webhelyekről, így a felhasználók továbbra is a hely. A szabályzat engedélyezve van (állítsa *Igen*), a Microsoft Edge meggátolja a felhasználókat a figyelmeztetések mellőzése és a letiltja őket a webhelyen való folyamatos.  

  **Alapértelmezett**: Igen

- **Ellenőrizetlen fájlletöltés letiltása**  
  [Böngésző/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles) – alapértelmezés szerint a Microsoft Edge lehetővé teszi a felhasználók kihagyhatják (figyelmen kívül hagyása) a Windows Defender SmartScreen potenciálisan kártékony fájlokkal kapcsolatos figyelmeztetések, lehetővé téve számukra letöltésének folytatása nem ellenőrzött fájlok. A szabályzat engedélyezve van (állítsa *Igen*), felhasználók ebben az esetben a rendszer megkerüli a figyelmeztetéseket, és nem ellenőrzött fájlok nem tölthető le.  

  **Alapértelmezett**: Igen

## <a name="windows-defender-anti-virus----settings-review-pending-for-this-section"></a>A Windows Defender víruskereső [beállítások függőben lévő vonatkozó felülvizsgálat ebben a szakaszban]

További információkért lásd: [házirend CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) a Windows dokumentációjában.

- **Microsoft-webböngészőkben betöltött szkriptek vizsgálata**  
  [Defender/AllowScriptScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning) – állítsa *Igen* , hogy a funkció a Windows Defender a parancsfájlok vizsgálatát.  

  **Alapértelmezett**: Igen

- **A bejövő e-mailek vizsgálata**  
  [Defender/AllowEmailScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) – állítsa *Igen* , hogy a Windows Defender megvizsgálja az e-mailt.  

  **Alapértelmezett**: Igen

- **Defender minta küldésének jóváhagyás típusa**  
  [Defender/SubmitSamplesConsent](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) – a felhasználó hozzájárulási szintjét a Windows Defender adatküldéshez. Ha már rendelkezik a szükséges feltételeket, a Windows Defender küldi el őket. Ha nincs (és ha a felhasználó soha nem szeretne feltenni által megadott), a felhasználói felület elindítása felhasználói jóváhagyás kérése (Ha *felhőalapú védelem* értékre van állítva *Igen*) adatok küldése előtt.  

  **Alapértelmezett**: Biztonságos minták automatikus küldése

- **Network Inspection System (NIS)**  
  [Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection) -aláírást a hálózati Hálózatvizsgáló rendszer (NIS) által észlelt rosszindulatú adatforgalmat.  
 
  **Alapértelmezett**: Igen

- **Aláírás-frissítési időköz (óra)**  
  [Defender/SignatureUpdateInterval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) – adjon meg (óra), az eszköz milyen gyakran ellenőrzi Defender-aláírás új frissítéseket.  
 
  **Alapértelmezett**: 4

- **Az ütemezett vizsgálatok alacsony processzorprioritás konfigurálása**  
  [Defender/EnableLowCPUPriority](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority) – Ha beállítása *Igen*, processzorprioritás ellenőrzés beállítása alacsony értékre. Amikor *nincs konfigurálva*, nem változnak az ütemezett vizsgálatok processzorprioritás.  

    **Alapértelmezett**: Igen

- **Defender blokkolása a hozzáférés-védelem**  
  [Defender/AllowOnAccessProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowonaccessprotection) – Ha beállítása *Igen*, a Windows Defender a hozzáférés-védelem engedélyezve van.  

  **Alapértelmezett**: Igen

- **Rendszervizsgálat típusa**  
  [Defender/ScanParameter](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter) -Defender vizsgálat típusa.  

  **Alapértelmezett**: Gyorsvizsgálat

- **Minden letöltés ellenőrzése**  
  [Defender/AllowIOAVProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection) -érték beállítása *Igen*, hogy a Defender megvizsgálja az összes letöltött fájlokat és mellékleteket.  

  **Alapértelmezett**: Igen

- **A karanténba zárt kártevők ennyi nap után törlődjenek**  
  [Defender/DaysToRetainCleanedMalware](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) – adja meg, hány napig karanténba helyezett elemeket a rendszer már automatikusan törlése előtt. Amikor nastavena nA hodnotu nula, karanténba helyezett elemek soha nem automatikusan törlődnek.  

  **Alapértelmezett**: 0

- **Ütemezett vizsgálat kezdete**  
  [Defender/ScheduleScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime) – a Defender számára eszközök időszak ütemezését. 
  
  Kapcsolódó lehetőség ebben a listában: *Defender/ScheduleScanDay*   

  **Alapértelmezett**: 2 AM

- **Felhőalapú védelem**  
  [Defender/AllowCloudProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection) – Ha beállítása *Igen*, Windows Defender információkat küld a Microsoftnak kapcsolatos esetleges problémákról talál. A Microsoft elemzi ezt az információt, többet megtudhat, illetve más ügyfelek számára, és továbbfejlesztett megoldásokat kínálnak.

  Ha ez a szabályzat beállítása *Igen*, használhat *Defender minta küldésének jóváhagyás típusa* adatokat küld az eszköz felett biztosít a felhasználóknak.  

  **Alapértelmezett**: Igen

- **Defender potenciálisan nemkívánatos alkalmazás**  
  [Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection) – a Windows Defender víruskereső képes felismerni és blokkolni a *vélhetően nemkívánatos alkalmazások* (végpontjaira) való letöltését és telepítését a hálózaton. 
 
  - Ha a beállítása *blokk*, a Windows Defender blokkolja a végpontjaira, és felsorolja azokat az előzményekben és más fenyegetések ellen.
  - Ha a beállítása *naplózási*, Windows defender észleli végpontjaira, de nem tiltja őket. Információ a Windows Defender ellen vett volna az alkalmazások által létrehozott Windows Defender az megjelenítő eseményeket keresve találhatók.  
  - Ha a beállítása *eszköz alapértelmezett*, elleni védelem ki van kapcsolva.  
 
  **Alapértelmezett**: Letiltás

- **Defender felhőalapú kiterjesztett időkorlátja**  
  [Defender/CloudExtendedTimeout](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout) – adja meg a maximális további időt, amely a Windows Defender víruskereső letilthat egy fájlt a felhőből érkező eredményre várva. Alap mennyi ideig vár, a Windows Defender érték 10 másodperc. Itt további időt (akár 50 másodperc) hozzáadódik a 10 másodperchez. A legtöbb esetben a vizsgálat kevesebb, mint a maximális időt vesz igénybe. Az idő növelésével azonban elegendő időt biztosíthat ahhoz, hogy a felhő alaposan megvizsgálja a gyanús fájlokat.  

  Alapértelmezés szerint a kibontott idő értéke 0 (letiltva). Az Intune azt javasolja, hogy engedélyezi ezt a beállítást, és legalább 20 másodpercet adjon meg.  
 
  **Alapértelmezett**: 0

- **Archív fájlok ellenőrzése**  
  [Defender/AllowArchiveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning) – állítsa *Igen* szeretné, hogy a Windows Defender archív fájlok ellenőrzése.  

  **Alapértelmezett**: Igen

- **Defender rendszer ütemezett vizsgálat**  
  [Defender/ScheduleScanDay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday) -ütemezést, mely napján Defender megvizsgálja-eszközök. 
 
  Kapcsolódó lehetőség ebben a listában: *Defender/ScheduleScanTime*

  **Alapértelmezett**: felhasználó által definiált

- **Viselkedésfigyelés engedélyezése**  
  [Defender/AllowBehaviorMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring) – állítsa *Igen* funkció a Windows Defender Viselkedésfigyelés engedélyezése. Beágyazott Windows 10, Windows Defender Viselkedésfigyelés érzékelők gyűjtése és az operációs rendszer viselkedési jelek feldolgozni és az érzékelő adatokat küldeni a Microsoft Defender ATP, elkülönített, privát felhő példányát.  

  **Alapértelmezett**: Igen

- **Hálózati mappákból megnyitott fájlok vizsgálata**  
  [Defender/AllowScanningNetworkFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) – állítsa *Igen* szeretné, hogy a Windows Defender megvizsgálja a fájlokat a hálózatban. A felhasználó nem fog tudni észlelt kártevők eltávolítása csak olvasható fájlokat.  

  **Alapértelmezett**: Igen

- **Defender felhőalapú blokkblob szintje**  
  [Defender/CloudBlockLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel) – használja a blokkolás és a gyanús fájlok vizsgálatát, ez a szabályzat határozza meg, hogyan agresszív Windows Defender víruskereső. A lehetőségek a következők:

  - Magas – agresszív ismeretlen fájlok letiltása közben (vakriasztásokkal teli nagyobb eséllyel sikerül) ügyfél teljesítményének optimalizálása
  - Magas plusz - fájlok agresszív ismeretlen letiltása, és további védelmi intézkedések (ügyfélteljesítményre) alkalmazása
  - Zéró tolerancia – minden ismeretlen végrehajtható fájlok letiltása

  **Alapértelmezett**: Nincs konfigurálva

- **Valós idejű figyelés**  
  [Defender/AllowRealtimeMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring) – állítsa *Igen* a Windows Defender valós idejű figyelés engedélyezése.  

  **Alapértelmezett**: Igen

- **CPU-használati korlát ellenőrzés közben**  
  [Defender/AvgCPULoadFactor](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor) – adja meg a maximális átlagos CPU kihasználtsága (%), amellyel a Windows Defender-ellenőrzés során.  

  **Alapértelmezett**: 50

- **Csatlakoztatott hálózati meghajtók vizsgálata teljes vizsgálat során**  
  [Defender/AllowFullScanOnMappedNetworkDrives](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanonmappednetworkdrives) -beállítása *Igen* szeretné, hogy a Windows Defender megvizsgálja a fájlokat a hálózatban. A felhasználó nem észlelt kártevők eltávolítása csak olvasható fájlokat,

  A listában szereplő kapcsolódó beállításai: *Defender/AllowScanningNetworkFiles*

  **Alapértelmezett**: Igen

- **Blokk végfelhasználói hozzáférés a Defenderhez**  
  [Defender/AllowUserUIAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowuseruiaccess) – állítsa *Igen* a végfelhasználók elérésének letiltása az eszközön a Windows Defender felhasználói felületén.  

  **Alapértelmezett**: Igen

- **Gyors ellenőrzés kezdetének időpontja**  
  [Defender/ScheduleQuickScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) – a Defender számára a Gyorsvizsgálat futtatása az időszak ütemezését.  

  **Alapértelmezett**: 2 AM

## <a name="windows-defender-firewall"></a>Windows Defender-tűzfal
További információkért lásd: [tűzfal CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp) a Windows dokumentációjában.

- **Biztonsági társítás üresjárati ideje törlés előtt** - *MdmStore/globális/SaIdleTime*   
  Hálózati forgalom nem látható a másodpercek száma a biztonsági társítások törölve lesznek.  
  **Alapértelmezett**: 300

- **File Transfer Protocol** - *MdmStore/globális/DisableStatefulFtp*   
  Letiltja az állapotalapú File Transfer Protocol (FTP).  
  **Alapértelmezett**: Igen

- **Packet queuing** - *MdmStore/Global/EnablePacketQueue*    
  Adja meg, hogy a fogadó oldali szoftver skálázása miként legyen engedélyezve a titkosított fogadás és az egyszerű szöveges továbbítás számára az IPsec alagutas átjáró használata esetén. Ez biztosítja, hogy a csomagsorrend megőrzése.  
  **Alapértelmezett**: Eszköz alapértelmezése

- **Tűzfal profil tartomány** - *FirewallRules/FirewallRuleName/profilok*  
  Megadja a profilok, amelyhez a szabály tartozik: Magánjellegű és nyilvános tartományokban. Ezt az értéket a profil-tartományokhoz csatlakozó hálózatok jelöli.  

  Rendelkezésre álló beállítások:  
  - **Egyedi küldésű válaszok a csoportos küldésű szórásokra szükséges**  
    **Alapértelmezett**: Igen

  - **Egyesített csoportházirend-engedélyezett alkalmazás szabályai**  
    **Alapértelmezett**: Igen

  - **Bejövő értesítések letiltva**  
    **Alapértelmezett**: Igen

  - **A csoportházirend globális port szabályokat egyesíteni**  
    **Alapértelmezett**: Igen

  - **Rejtett üzemmód letiltva**  
    **Alapértelmezett**: Igen

  - **Tűzfal engedélyezve van**  
    **Alapértelmezett**: Engedélyezett

  - **A csoportházirend nem egyesített kapcsolatbiztonsági szabályok**  
    **Alapértelmezett**: Igen

  - **A csoportházirend nem egyesített házirend szabályai**  
    **Alapértelmezett**: Igen

- **A tűzfalszabályok profilban nyilvános** - *FirewallRules/FirewallRuleName/profilok*  
  Megadja a profilok, amelyhez a szabály tartozik: Magánjellegű és nyilvános tartományokban. Ez az érték a profilt a nyilvános hálózatok jelöli. Ezek a hálózatok besorolt nyilvános által a rendszergazdák a fogadó kiszolgálón. A besorolás akkor történik meg az első alkalommal a gazdagép csatlakozik a hálózathoz. Ezek a hálózatok általában, kávézóban – üzemelő hálózathoz, és más nyilvános helyeken, ahol a társaknak a hálózaton vagy a rendszergazda nem megbízható.  

  Rendelkezésre álló beállítások:

  - **Blokkolja a bejövő kapcsolatok**  
    **Alapértelmezett**: Igen 

  - **Egyedi küldésű válaszok a csoportos küldésű szórásokra szükséges**  
    **Alapértelmezett**: Igen  

  - **Rejtett üzemmód megadása kötelező**  
    **Alapértelmezett**: Igen 
 
  - **Szükséges kimenő kapcsolatok**  
    **Alapértelmezett**: Igen  

  - **Egyesített csoportházirend-engedélyezett alkalmazás szabályai**  
    **Alapértelmezett**: Igen  

  - **Bejövő értesítések letiltva**  
    **Alapértelmezett**: Igen  

  - **A csoportházirend globális port szabályokat egyesíteni**  
    **Alapértelmezett**: Igen

  - **Rejtett üzemmód letiltva**  
    **Alapértelmezett**: Igen

  - **Tűzfal engedélyezve van**  
    **Alapértelmezett**: Engedélyezett  

  - **A csoportházirend nem egyesített kapcsolatbiztonsági szabályok**  
    **Alapértelmezett**: Igen  

  - **Bejövő forgalom szükséges**  
    **Alapértelmezett**: Igen

  - **A csoportházirend nem egyesített házirend szabályai**  
    **Alapértelmezett**: Igen  

- **Tűzfal profil privát** - *FirewallRules/FirewallRuleName/profilok*  
  Megadja a profilok, amelyhez a szabály tartozik: Magánjellegű és nyilvános tartományokban. Ezt az értéket a profil magánhálózatok jelöli.  

  Rendelkezésre álló beállítások: 

  - **Blokkolja a bejövő kapcsolatok**  
    **Alapértelmezett**: Igen

  - **Egyedi küldésű válaszok a csoportos küldésű szórásokra szükséges**  
    **Alapértelmezett**: Igen

  - **Rejtett üzemmód megadása kötelező**  
    **Alapértelmezett**: Igen

  - **Szükséges kimenő kapcsolatok**  
    **Alapértelmezett**: Igen

  - **Bejövő értesítések letiltva**  
    **Alapértelmezett**: Igen

  - **A csoportházirend globális port szabályokat egyesíteni**  
    **Alapértelmezett**: Igen

  - **Rejtett üzemmód letiltva**  
    **Alapértelmezett**: Igen  

  - **Tűzfal engedélyezve van**  
    **Alapértelmezett**: Engedélyezett

  - **Engedélyezett alkalmazás nem egyesített csoportházirend-szabályai**  
    **Alapértelmezett**: Igen

  - **A csoportházirend nem egyesített kapcsolatbiztonsági szabályok**  
    **Alapértelmezett**: Igen

  - **Bejövő forgalom szükséges**  
    **Alapértelmezett**: Igen

  - **A csoportházirend nem egyesített házirend szabályai**  
    **Alapértelmezett**: Igen  

- **Tűzfal előre megosztott kulcs kódolási módszert**  
  **Alapértelmezett**: UTF8

- **Tanúsítvány visszavont tanúsítványok listájának ellenőrzése**  
  **Alapértelmezett**: Eszköz alapértelmezése

## <a name="windows-hello-for-business"></a>Vállalati Windows Hello  

További információkért lásd: [PassportForWork CSP](https://docs.microsoft.com/windows/client-management/mdm/passportforwork-csp) a Windows dokumentációjában.

- **A vállalati Windows Hello konfigurálása** - *TenantId/házirendek/UsePassportForWork*    
  Windows Hello for Business egy alternatív módszer a azáltal, hogy a jelszavak, intelligens kártyák és a virtuális intelligens kártyák a Windows-ba történő bejelentkezéskor.  

  Ha engedélyezi, vagy nem konfigurálja ezt a beállítást, az eszköz kiépítése Windows Hello for Business. Ha letiltja ezt a beállítást, az eszköz nem építhet ki Windows Hello for Business bármely felhasználó számára.

  Az Intune nem támogatja a Windows Hello letiltása. Ehelyett konfigurálhatja a szabályzat engedélyezése Windows Hello for Business (Igen), vagy nem konfigurálja Windows Hello közvetlenül (nincs konfigurálva). Nincs konfigurálva, amikor egy eszköz kapnak konfigurációja keresztül más a szabályzatot, amely előfordulhat, hogy engedélyezi vagy letiltja ezt a szolgáltatást.  

  **Alapértelmezett**: Igen  

- **Kisbetűk használatának megkövetelése a PIN-kód** - *LowercaseLetters TenantId/házirendek/PINComplexity*  
  **Alapértelmezett**: Engedélyezett  

- **Speciális karakterek megkövetelése a PIN-kód** - *SpecialCharacters TenantId/házirendek/PINComplexity*  
  **Alapértelmezett**: Engedélyezett  

- **Nagybetűk használatának megkövetelése a PIN-kód** - *UppercaseLetters TenantId/házirendek/PINComplexity*   
  **Alapértelmezett**: Engedélyezett  


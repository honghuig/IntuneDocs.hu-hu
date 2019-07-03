---
title: Alkalmazások telepítésével kapcsolatos problémák elhárítása
titleSuffix: Microsoft Intune
description: A Microsoft Intune hibaelhárítási paneljével elháríthatja az alkalmazások telepítésével kapcsolatos problémákat.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/19/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f4180c6d803edc8cd9d9f3948466a5ceed22ae36
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67530790"
---
# <a name="troubleshoot-app-installation-issues"></a>Alkalmazások telepítésével kapcsolatos problémák elhárítása

A Microsoft Intune MDM által felügyelt eszközökön néha sikertelenek lehetnek az alkalmazástelepítések. Ilyen esetekben nem könnyű megérteni a hiba okát, illetve elhárítani azt. A Microsoft Intune olyan adatokat szolgáltat az alkalmazástelepítésbeli hibákról, amelyekkel az ügyfélszolgálati operátorok és az Intune-rendszergazdák megtekinthetik az alkalmazásadatokat, és reagálhatnak az ügyfelek kérelmeire. Az Intune hibaelhárítási panelje megjeleníti a hibák adatait, így a felhasználói eszközökön kezelt alkalmazások információit is. Az alkalmazások végpontok közötti életciklusához tartozó adatok a **Felügyelt alkalmazások** panelen, az egyes eszközök alatt tekinthetők meg. Itt megtekintheti a telepítési problémákat, például az alkalmazás létrehozási, módosítási és célzási dátumát, valamint az eszközökre való továbbításának dátumát. 

## <a name="app-troubleshooting-details"></a>Alkalmazás hibaelhárítási részletei

Az Intune az adott felhasználók eszközein telepített alkalmazások alapján szolgáltat hibaelhárítási információkat.

1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Az **Intune** panelen válassza a **Hibaelhárítás** lehetőséget.
4. A felhasználó kiválasztásához kattintson a **Felhasználó kijelölése** lehetőségre. Ekkor megjelenik a **Felhasználók kijelölése** panel.
5. Jelöljön ki egy felhasználót a megfelelő név vagy e-mail cím beírásával. Kattintson a **Kijelölés** gombra a lap alján. A felhasználóval kapcsolatos hibaelhárítási információ a **Hibaelhárítás** panelen jelenik meg. 
6. Az **Eszközök** listában jelölje ki azt az eszközt, amelyen hibaelhárítást szeretne végezni.
    ![Az Intune Hibaelhárítás panelje.](media/troubleshoot-app-install-01.png)
7. A kijelölt eszköz paneljén válassza a **Felügyelt alkalmazások** lehetőséget. Megjelenik a felügyelt alkalmazások listája.
    ![Az Intune által kezelt eszköz adatai.](media/troubleshoot-app-install-02.png)
8. Válassza ki azt az alkalmazást, amelynél hibát jelez a **Telepítés állapota**.
    ![A kiválasztott alkalmazás, amelynél megjelennek a telepítési hiba adatai.](media/troubleshoot-app-install-03.png)

    > [!Note]  
    > Ugyanazt az alkalmazást eltérő alkalmazásműveleti szándékkal rendelhetik hozzá különböző csoportokhoz. Egy alkalmazás feloldott szándéka például **Kizárva** értéket jelez, ha az alkalmazás ki van zárva egy felhasználó számára az alkalmazás-hozzárendelés során. További információ: [Alkalmazások hozzárendelési ütközéseinek feloldása](apps-deploy.md#how-conflicts-between-app-intents-are-resolved).<br><br>
    > Ha egy szükséges alkalmazás telepítése sikertelen, akkor Ön vagy a segélyszolgálat szinkronizálhatja az eszközt, és újra megkísérelheti az alkalmazás telepítését.

Az alkalmazástelepítési hiba információi ismertetik a problémát. Ezen adatok segítségével meghatározhatja a probléma feloldásához szükséges műveletet. További információ az alkalmazás telepítési problémák elhárítása: [alkalmazástelepítési hibák](troubleshoot-app-install.md#app-installation-errors).

> [!Note]  
> A **Hibaelhárítás** panel a böngészőben a [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting) címen is elérhető.

## <a name="win32-app-installation-troubleshooting"></a>A Win32 alkalmazás telepítési hibák elhárítása

Válassza ki a Win32-alkalmazás, amely az Intune felügyeleti bővítmény segítségével telepítve lett. Kiválaszthatja a **naplók összegyűjtése** lehetőséget, ha a Win32-alkalmazás telepítése nem sikerült. 

> [!IMPORTANT]
> A **naplók összegyűjtése** beállítás nem lesz engedélyezve, ha a Win32-alkalmazás telepítése sikeresen megtörtént az eszközön.<p>Win32-alkalmazás naplóadatokat gyűjthet, mielőtt az Intune felügyeleti bővítmény telepítve kell lennie a Windows-ügyfél. Az Intune felügyeleti bővítmény telepítve van, amikor egy PowerShell-parancsprogram, vagy egy Win32-alkalmazás egy felhasználó vagy eszköz biztonsági csoport üzemel. További információkért lásd: [az Intune felügyeleti bővítmény – Előfeltételek](intune-management-extension.md#prerequisites).

### <a name="collect-log-file"></a>Naplófájl összegyűjtése

A Win32-alkalmazás telepítési naplók összegyűjtésére, először hajtsa végre a szakaszban található lépéseket [hibaelhárítási adatok alkalmazás](troubleshoot-app-install.md#app-troubleshooting-details). Ezt követően folytassa a következő lépéseket:

1. Kattintson a **naplók összegyűjtése** beállítást a **telepítés részletei** panelen.

    <image alt="Win32 app installation details - Collect log option" src="media/troubleshoot-app-install-04.png" width="500" />

2. Fájlelérési utak a napló adja meg a nevet, hogy a fájl naplógyűjtési folyamat megkezdéséhez, és kattintson a **OK**.
    
    > [!NOTE]
    > Naplók összegyűjtése a kevesebb mint két órát fog igénybe venni. Támogatott fájltípusok: *.log, .txt, .dmp, .cab, .zip, .xml, .evtx és .evtl*. Legfeljebb 25 Fájlelérési utak használata engedélyezett.

3. Miután a naplófájlok összegyűjtése, kiválaszthatja a **naplók** hivatkozásra a letöltéséhez a rendszernapló fájljaiban.

    <image alt="Win32 app log details - Download logs" src="media/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > Értesítés a sikeres, az alkalmazáskatalógus log művelet jelenik meg.

#### <a name="win32-log-collection-requirements"></a>A Win32 log adatgyűjtési követelmények

Vonatkoznak konkrét követelmények, amelyek naplófájlokat gyűjthet kell követnie:

- Meg kell adnia a naplófájl teljes elérési útja. 
- Naplók gyűjtése, például a következő környezeti változókat adhat meg:<br>
  *%PROGRAMFILES%, %PROGRAMDATA% %PUBLIC%, %WINDIR%, %TEMP%, %TMP%*
- Csak a pontos fájlkiterjesztések engedélyezettek, mint például:<br>
  *.log, .txt, .dmp, .cab, .zip, .xml*
- Töltse fel a maximális naplófájl, 60 MB vagy 25 fájlokra, amelyik hamarabb következik be. 
- Win32-alkalmazás telepítése naplógyűjtés engedélyezve van, amelyek megfelelnek a szükséges alkalmazások esetében érhető el, és távolítsa el az alkalmazás hozzárendelési szándék.
- A tárolt naplókat a naplók található PII adatok védelme érdekében vannak titkosítva.
- Nyitó támogatási jegyek Win32 alkalmazás hibáit, miközben csatolása a kapcsolódó hiba naplókat, a fenti lépésekkel.

## <a name="app-installation-errors"></a>Alkalmazástelepítési hibák

Az alábbi hibaüzenetek és leírások az Androidos és iOS-es telepítési hibák részleteit mutatják be. 

### <a name="android-errors"></a>Android hibák

|    Hibaüzenet/hibakód    |    Leírás    |
|----------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Nem sikerült telepíteni az alkalmazást. (0xC7D14FB5)    |    Ez a hibaüzenet akkor jelenik meg, ha az Intune nem tudja megállapítani az Android-alkalmazás telepítési hibájának kiváltó okát. A hiba során az Android nem adott semmilyen információt.       Ez a hiba akkor lép fel, ha az APK letöltése sikeres volt, az alkalmazás telepítése azonban sikertelen. A hibát gyakran egy hibás APK-fájl okozza, amelyet nem lehet telepíteni az eszközre. Egy lehetséges ok, ha a Google Play Protect biztonsági okokból letiltja az alkalmazás telepítését. Egy másik lehetséges ok, ha az eszköz nem támogatja az alkalmazást. Például ha az alkalmazás az API 21-es vagy újabb verzióját igényli, az eszközön pedig az API 19-es verziója van telepítve.         Az Intune ezt a hibát adja vissza a DA és a KNOX eszközökhöz is, és bár előfordulhat, hogy megjelenik egy értesítés, amelyre kattintva a felhasználó újrapróbálkozhat, ha a problémát az APK okozza, akkor a telepítés mindig sikertelen lesz. Ha az alkalmazás egy opcionálisan elérhető alkalmazás, az értesítés elvethető. Azonban ha az alkalmazás szükséges, az értesítés nem vethető el.        |
|    Az alkalmazás telepítése meg lett szakítva, mert a telepítő-(APK) fájlt a letöltés után, de a telepítés előtt törölve lett. (0xC7D14FBA)    |    Az APK letöltése sikeres volt, de a fájl el lett távolítva az eszközről, még mielőtt a felhasználó telepítette volna az alkalmazást. Ez akkor fordulhat elő, ha sok idő telt el a letöltés és a telepítés között. Például a felhasználó az eredeti telepítés megszakadt, adatbázis, és rákattintva az értesítést, és próbálkozzon újra.         Ez a hibaüzenet csak a DA-forgatókönyveknél jelenik meg. A KNOX-forgatókönyvek csendben elvégezhetők. Megjelenítünk egy újrapróbálkozási értesítést, amelyet a felhasználó elfogadhat a megszakítás helyett. Ha az alkalmazás egy opcionálisan elérhető alkalmazás, az értesítés elvethető. Azonban ha az alkalmazás szükséges, az értesítés nem vethető el.    |
|    Az alkalmazás telepítése meg lett szakítva, mert a folyamat újra lett indítva a telepítés során. (0xC7D14FBB)    |    Az eszköz újra lett indítva a megszakítva telepítést eredményez az Alkalmazáscsomag telepítési folyamat során.        Ez a hibaüzenet a DA- és KNOX-eszközök esetén is megjelenik. Az Intune megjelenít egy értesítést, amelyre rákattintva a felhasználó újrapróbálkozhat. Ha az alkalmazás egy opcionálisan elérhető alkalmazás, az értesítés elvethető. Azonban ha az alkalmazás szükséges, az értesítés nem vethető el.    |
|    Az alkalmazás nem észlelhető a sikeres telepítést követően. (0x87D1041C)    |    A felhasználó explicit módon eltávolította az alkalmazást. Ezt a hibát nem az ügyfél adja vissza. A hibát az okozza, hogy az alkalmazás valamikor telepítve lett, de aztán a felhasználó eltávolította. Ez a hiba csak a szükséges alkalmazások esetén jelenhet meg. A nem szükséges alkalmazásokat a felhasználó eltávolíthatja. Ez a hiba csak a DA esetén következik be. A KNOX nem engedélyezi a felügyelt alkalmazások eltávolítását.       A következő szinkronizáláskor az eszközön újra megjelenik az értesítés arról, hogy a felhasználó végezze el a telepítést.   A felhasználó figyelmen kívül hagyhatja az értesítést. Az eszköz azonban egészen addig jelenteni fogja a hibát, amíg a felhasználó nem telepíti az alkalmazást.    |
|    A letöltés egy ismeretlen hiba miatt nem sikerült. (0xC7D14FB2)    |    Ez a hiba akkor fordul elő, ha a letöltés sikertelenül végződik. A hibát gyakran a Wi-Fi problémái vagy a lassú kapcsolat okozza.       Ez a hiba csak DA-forgatókönyveknél jelenik meg. A KNOX-forgatókönyveknél a felhasználó nem kap értesítést a telepítésről, mert az csendben elvégezhető. Az Intune megjelenít egy értesítést, amelyre rákattintva a felhasználó újrapróbálkozhat. Ha az alkalmazás egy opcionálisan elérhető alkalmazás, az értesítés elvethető. Azonban ha az alkalmazás szükséges, az értesítés nem vethető el.    |
|    A letöltés egy ismeretlen hiba miatt nem sikerült. Az eszköz a következő szinkronizáláskor újra megpróbálkozik a szabályzattal. (0xC7D15078)    |    Ez a hiba akkor fordul elő, ha a letöltés sikertelenül végződik. A hibát gyakran a Wi-Fi problémái vagy a lassú kapcsolat okozza.       Ez a hiba csak DA-forgatókönyveknél jelenik meg. A KNOX-forgatókönyveknél a felhasználó nem kap értesítést a telepítésről, mert az csendben elvégezhető.    |
|    A végfelhasználó számára az alkalmazás telepítése megszakadt. (0xC7D14FB1)    |    A felhasználó explicit módon eltávolította az alkalmazást. Ez a hiba jelentkezik az Android operációs rendszer telepítésekor tevékenység a felhasználó megszakította. Amikor az operációs rendszer telepítésről szóló prompt megjelent, a felhasználó a Mégse gombra vagy a prompton kívülre kattintott.        Ez a hiba csak DA-forgatókönyveknél jelenik meg. A KNOX-forgatókönyveknél a felhasználó nem kap értesítést a telepítésről, mert az csendben elvégezhető. Az Intune megjelenít egy értesítést, amelyre rákattintva a felhasználó újrapróbálkozhat. Ha az alkalmazás egy opcionálisan elérhető alkalmazás, az értesítés elvethető. Azonban ha az alkalmazás szükséges, az értesítés nem vethető el.    |
|    A fájl letöltésének folyamata váratlanul leállt. (0xC7D15015)    |    Az operációs rendszer leállította a letöltési folyamatot, mielőtt az befejeződött volna. Ez a hiba akkor fordulhat elő, ha az eszköz töltöttségi szintje túl alacsony, vagy a letöltés túl sokáig tart.       Ez a hiba csak DA-forgatókönyveknél jelenik meg. A KNOX-forgatókönyveknél a felhasználó nem kap értesítést a telepítésről, mert az csendben elvégezhető. Az Intune megjelenít egy értesítést, amelyre rákattintva a felhasználó újrapróbálkozhat. Ha az alkalmazás egy opcionálisan elérhető alkalmazás, az értesítés elvethető. Azonban ha az alkalmazás szükséges, az értesítés nem vethető el.    |
|    A fájlletöltési szolgáltatás váratlanul leállt. Az eszköz a következő szinkronizáláskor újra megpróbálkozik a szabályzattal. (0xC7D1507C)    |    Az operációs rendszer leállította a letöltési folyamatot, mielőtt az befejeződött volna. Ez a hiba akkor fordulhat elő, ha az eszköz töltöttségi szintje túl alacsony, vagy a letöltés túl sokáig tart.       Ez a hiba csak DA-forgatókönyveknél jelenik meg. A KNOX-forgatókönyveknél a felhasználó nem kap értesítést a telepítésről, mert az csendben elvégezhető.    |

### <a name="ios-errors"></a>iOS hibák

| Hibaüzenet/hibakód | Leírás és hibaelhárítási tippek |
|------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| (0x87D12906) | Apple MDM-ügynököt, az adott vissza, hogy a telepítési parancs sikertelen volt. |
| (0x87D1313C) | A hálózati kapcsolat megszakadt, miközben az eszköz küldte el a frissített letöltési URL-címe. Pontosabban a megadott gazdagépnév kiszolgáló nem található. |
| iOS-eszköz jelenleg elfoglalt. (0x87D11388) | Az iOS-eszköz foglalt volt, amely hibát eredményezett. |
| Az alkalmazás telepítése nem sikerült. (0x87D13B64) | Egy alkalmazás telepítési hiba történt. A hiba okának felderítéséhez szükség van az XCODE-naplókra. |
| Az alkalmazás felügyelt, de lejárt, vagy a felhasználó el lett távolítva. (0x87D13B66) | A felhasználónak explicit módon eltávolítja az alkalmazást. Vagy az alkalmazás lejárt, de nem sikerült letölteni, vagy az alkalmazás észlelésének eredménye nem egyezik meg az eszköz által küldött válasszal.   Emellett a hibát az iOS 9.2.2 platform egyik hibája is okozhatja. |
| Az alkalmazás telepítésre van ütemezve, de a beváltási kódra van szüksége a tranzakció végrehajtásához. (0x87D13B60) | Ez a hiba általában akkor fordul elő, az alkalmazások befizetett iOS Store-alkalmazások. |
| Az alkalmazás nem észlelt a telepítés sikeres befejezése után.   (0x87D1041C) | Az észlelési folyamat nem felel meg a választ az eszközről. |
| A felhasználó elutasította az alkalmazás telepítésére vonatkozó ajánlatot. (0x87D13B62) | Kezdeti alkalmazás telepítésekor a felhasználó rákattintott szakítható meg. |
| A felhasználó elutasította az alkalmazás frissítésére vonatkozó ajánlatot. (0x87D13B63) | A végfelhasználó számára való kattintás megszakítja a frissítési folyamat alatt. |
| Ismeretlen hiba (0x87D103E8) | Ismeretlen alkalmazás telepítési hiba történt. Az eredményül kapott hiba Ez akkor, ha a többi hiba nem történt. |
| Megosztott iPad (-2016330861) csak telepíthető VPP-alkalmazásokat. | Az alkalmazások telepítéséhez egy megosztott iPad Apple Volume Purchase Program használatával lehet lekérdezni. |
| Nem telepíthet alkalmazásokat, ha az App Store le van tiltva (-2016330860).  | A felhasználó számára telepítik az alkalmazást az App Store engedélyezni kell. |
| Nem található a VPP-licenc (-2016330859) alkalmazáshoz.  | Próbálja meg visszavonni, és az alkalmazás licencének újrakiosztás. |
| Az MDM-szolgáltató (-2016330858) a rendszer alkalmazások nem lehet telepíteni. | Az iOS operációs rendszer által előre telepített alkalmazások telepítése nem támogatott. |
| Nem telepíthet alkalmazásokat, ha az eszköz van, elveszett módot (-2016330857). | Az eszköz összes használatát az elveszett üzemmód le van tiltva.   Alkalmazások telepítéséhez elveszett mód letiltása. |
| Nem telepíthet alkalmazásokat, ha az eszköz teljes képernyős módban (-2016330856) van. | Próbálja meg hozzáadni az eszközt telepíteni alkalmazásokat a kioszk mód konfigurációs szabályzat kizárási csoporthoz. |
| Az eszköz (-2016330852) nem telepíthető 32 bites alkalmazásokat. | Az eszköz nem támogatja a 32 bites alkalmazások telepítéséhez. Próbálja meg a 64 bites verziója, az alkalmazás üzembe helyezése. |
| Az App Store (-2016330855) felhasználói be kell jelentkeznie. | A felhasználónak kell bejelentkezni az App Store az alkalmazás telepítése előtt. |
| Ismeretlen hiba. Kérjük, próbálkozzon újra (-2016330854). | Az alkalmazás telepítése ismeretlen okból nem sikerült.   Próbálkozzon újra később. |
| Az alkalmazás telepítése nem sikerült. Az Intune megpróbálja újra a következő alkalommal az eszköz szinkronizálások (-2016330853). | Az alkalmazás telepítése egy eszközön hibába ütközött. Az eszköz szinkronizálása érdekében próbálja meg újból telepíteni az alkalmazást. |

### <a name="other-installation-errors"></a>Egyéb telepítési hibák

|    Üzenet/hibakód    |    Leírás    |
|-----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    0x80073CFF, 0x80CF201C (ügyfélhiba)    |    Az alkalmazás telepítéséhez közvetlen telepítést lehetővé tevő rendszerrel kell rendelkeznie. Győződjön meg arról, hogy az alkalmazáscsomag megbízható aláírással és telepítve van egy tartományhoz csatlakoztatott eszköz, amely rendelkezik a **AllowAllTrustedApps** házirend engedélyezve van, vagy a Windows közvetlen telepítési licenccel rendelkező eszközök esetén a  **AllowAllTrustedApps** házirend engedélyezve van. További információkért lásd: [csomagolási, telepítési és lekérdezési Windows Store Apps hibaelhárítási](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).     |
|    0x80073CF0    |    A csomag nem nyitható meg. Lehetséges okok:<ul><li> A csomag nincs aláírva.</li><li> A közzétevő neve nem egyezik meg az aláíró tanúsítvány tulajdonosával.</li></ul> Ellenőrizze a **AppxPackagingOM** eseménynaplóban talál. További információkért lásd: [csomagolási, telepítési és lekérdezési Windows Store Apps hibaelhárítási](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).    |
|    0x80073CF3    |    A csomag nem sikerült a frissítés, függőségeinek vagy ütközéseinek érvényességét. Lehetséges okok:<ul><li> A bejövő csomag ütközik egy telepített csomaggal.</li><li> Nem található a megadott csomagfüggőség.</li><li> A csomag nem támogatja a megfelelő processzorarchitektúrát.</li></ul> Ellenőrizze a **AppXDeployment-Server** eseménynaplóban talál. További információkért lásd: [csomagolási, telepítési és lekérdezési Windows Store Apps hibaelhárítási](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).    |
|    0x80073CFB    |    A megadott csomag már telepítve van, és a csomag újratelepítése le van tiltva. Ezt a hibaüzenetet kapja, amely nem azonos a csomagot, amely már telepítve van a csomag telepítésekor sikerült. Ellenőrizze, hogy a csomag tartalmaz-e digitális aláírást. Ha újraépít vagy újra aláír egy csomagot, a csomag nem lesz bitenként azonos az előzőleg telepített csomaggal. Ez a hiba kétféleképpen javítható ki:<ul><li> Növelje a verziószámot, az alkalmazás, majd építse és írja alá újra a csomagot.</li><li> Távolítsa el a régi csomagot a rendszer minden felhasználója esetében, az új csomag telepítése előtt.</li></ul> További információkért lásd: [csomagolási, telepítési és lekérdezési Windows Store Apps hibaelhárítási](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).    |
|    0x87D1041C    |    Az alkalmazás telepítése sikeres volt, de a rendszer nem ismeri fel az alkalmazást. Az alkalmazás volt Intune sikeresen telepítette, majd később eltávolítja. Az alkalmazás okai a következők:<ul><li> A végfelhasználó eltávolítja az alkalmazást.</li><li> Az azonosító adatokat a csomagban nem egyezik, milyen hibás alkalmazások jelentett.</li><li>Az önfrissítési MSIs a verzió-kezelő nem egyezik az adatokat az alkalmazás, az Intune-on kívül frissítést követően.</li></ul> Kérje meg a felhasználót, hogy telepítse újra az alkalmazást a vállalati portálról. Vegye figyelembe, hogy kötelező alkalmazások újratelepítése automatikusan, amikor az eszköz következő bejelentkezésekor.    |

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>A Microsoft Áruházból származó alkalmazások hibáinak elhárítása

A [Troubleshooting packaging, deployment, and query of Microsoft Store apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) (A Microsoft Áruházbeli alkalmazások csomagolási, telepítési és lekérdezési hibáinak elhárítása) című cikkben foglaltak segítenek elhárítani az alkalmazásoknak a Microsoft Áruházból akár Intune-nal, akár más módon történő telepítésekor tapasztalt gyakori problémákat.

## <a name="next-steps"></a>További lépések

- További információt az Intune hibaelhárításáról a [Segítségnyújtás a céges felhasználóknak a hibaelhárítási portál használatával](help-desk-operators.md) című témakörben talál. 
- Ismertető a Microsoft Intune esetleges ismert problémáiról. További információt [Az Intune ismert problémái](known-issues.md) című témakörben talál.
- További segítségre van szüksége? Ismerje meg, [hogyan kérhet támogatást az Intune-hoz](get-support.md).

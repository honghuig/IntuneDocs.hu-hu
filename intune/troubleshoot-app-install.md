---
title: Alkalmazások telepítésével kapcsolatos problémák elhárítása
titleSuffix: Microsoft Intune
description: A Microsoft Intune hibaelhárítási paneljével elháríthatja az alkalmazások telepítésével kapcsolatos problémákat.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/25/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b93fc8bc1bddbae8b1b0bde4f8b8815e8052fb51
ms.sourcegitcommit: 2fa20338bd0236884e1f3fde624cf70da89fd254
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/26/2019
ms.locfileid: "68507696"
---
# <a name="troubleshoot-app-installation-issues"></a>Alkalmazások telepítésével kapcsolatos problémák elhárítása

A Microsoft Intune MDM által felügyelt eszközökön néha sikertelenek lehetnek az alkalmazástelepítések. Ilyen esetekben nem könnyű megérteni a hiba okát, illetve elhárítani azt. A Microsoft Intune olyan adatokat szolgáltat az alkalmazástelepítésbeli hibákról, amelyekkel az ügyfélszolgálati operátorok és az Intune-rendszergazdák megtekinthetik az alkalmazásadatokat, és reagálhatnak az ügyfelek kérelmeire. Az Intune hibaelhárítási panelje megjeleníti a hibák adatait, így a felhasználói eszközökön kezelt alkalmazások információit is. Az alkalmazások végpontok közötti életciklusához tartozó adatok a **Felügyelt alkalmazások** panelen, az egyes eszközök alatt tekinthetők meg. Itt megtekintheti a telepítési problémákat, például az alkalmazás létrehozási, módosítási és célzási dátumát, valamint az eszközökre való továbbításának dátumát. 

## <a name="app-troubleshooting-details"></a>Alkalmazás-hibaelhárítás részletei

Az Intune az adott felhasználók eszközein telepített alkalmazások alapján szolgáltat hibaelhárítási információkat.

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
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

Az alkalmazástelepítési hiba információi ismertetik a problémát. Ezen adatok segítségével meghatározhatja a probléma feloldásához szükséges műveletet. Az alkalmazások telepítési problémáinak elhárításával kapcsolatos további információkért lásd az [alkalmazások telepítési hibáit](troubleshoot-app-install.md#app-installation-errors)ismertető témakört.

> [!Note]  
> A **Hibaelhárítás** panel a böngészőben a [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting) címen is elérhető.

## <a name="user-group-targeted-app-installation-does-not-reach-device"></a>A felhasználói csoport megcélzó alkalmazásának telepítése nem érhető el az eszközön
Az alkalmazások telepítésekor a következő műveleteket kell figyelembe venni:
- Ha az alkalmazás nem jelenik meg a Céges portálban, győződjön meg arról, hogy az alkalmazás **elérhető** szándékkal van telepítve, és hogy a felhasználó a céges portálhoz fér hozzá az alkalmazás által támogatott típusú eszközhöz.
- A Windows BYOD eszközökhöz a felhasználónak munkahelyi fiókot kell hozzáadnia az eszközhöz.
- Ellenőrizze, hogy a felhasználó meghaladja-e a HRE-eszköz korlátját:
  1. Navigáljon [Azure Active Directory eszköz beállításaihoz](https://portal.azure.com/#blade/Microsoft_AAD_IAM/DevicesMenuBlade/DeviceSettings/menuId).
  2. Jegyezze fel a **maximális eszközök felhasználónként**való beállításának értékét.
  3. Navigáljon [Azure Active Directory felhasználóhoz](https://portal.azure.com/#blade/Microsoft_AAD_IAM/UsersManagementMenuBlade/AllUsers).
  4. Válassza ki az érintett felhasználót, és kattintson az **eszközök**elemre.
  5. Ha a felhasználó túllépi a beállított korlátot, törölje azokat az elavult rekordokat, amelyekre már nincs szükség.
- IOS DEP-eszközök esetén győződjön meg arról, hogy a felhasználó regisztrálva van a **felhasználó által** az Intune-eszköz áttekintés paneljén. Ha a NA-t jeleníti meg, akkor telepítsen egy konfigurációs házirendet a Intune Céges portálhoz. További információ: [a céges portál alkalmazás konfigurálása](https://docs.microsoft.com/intune/app-configuration-policies-use-ios#configure-the-company-portal-app-to-support-ios-dep-devices).

## <a name="win32-app-installation-troubleshooting"></a>Win32-alkalmazás telepítésének hibaelhárítása

Válassza ki az Intune felügyeleti bővítmény használatával üzembe helyezett Win32-alkalmazást. Ha a Win32-alkalmazás telepítése sikertelen, a **naplók összegyűjtése** lehetőség kiválasztásával végezhető el. 

> [!IMPORTANT]
> A **naplók összegyűjtése** beállítás nem lesz engedélyezve, ha a Win32-alkalmazás sikeresen telepítve van az eszközön.<p>A Win32-alkalmazások naplózási adatainak összegyűjtéséhez az Intune felügyeleti bővítményét telepíteni kell a Windows-ügyfélre. Az Intune felügyeleti bővítmény akkor települ, ha PowerShell-parancsfájlt vagy Win32-alkalmazást telepít egy felhasználói vagy eszköz biztonsági csoportba. További információ: [Intune felügyeleti bővítmény – előfeltételek](intune-management-extension.md#prerequisites).

### <a name="collect-log-file"></a>Naplófájl gyűjtése

A Win32-alkalmazás telepítési naplóinak összegyűjtéséhez kövesse az [alkalmazás hibaelhárítási részletei](troubleshoot-app-install.md#app-troubleshooting-details)című szakasz lépéseit. Ezután folytassa a következő lépésekkel:

1. Kattintson a **naplók összegyűjtése** lehetőségre a **telepítés részletei** panelen.

    <image alt="Win32 app installation details - Collect log option" src="media/troubleshoot-app-install-04.png" width="500" />

2. A naplófájlok gyűjtési folyamatának megkezdéséhez adja meg a fájl elérési útját, és kattintson **az OK**gombra.
    
    > [!NOTE]
    > A naplózási gyűjtemény kevesebb mint két órát vesz igénybe. Támogatott fájltípusok: *. log,. txt,. dmp,. cab,. zip,. XML,. evtx és. evtl*. Legfeljebb 25 fájlelérési út engedélyezett.

3. A naplófájlok gyűjtése után kiválaszthatja a **naplók** hivatkozást a naplófájlok letöltéséhez.

    <image alt="Win32 app log details - Download logs" src="media/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > Ekkor megjelenik egy értesítés, amely az alkalmazás naplójának sikeres sikerességét jelzi.

#### <a name="win32-log-collection-requirements"></a>A Win32-naplók gyűjtésének követelményei

A naplófájlok összegyűjtéséhez konkrét követelményekre van szükség:

- Meg kell adnia a naplófájl teljes elérési útját. 
- Megadhatja a naplózási gyűjtemény környezeti változóit, például a következőket:<br>
  *% PROGRAMFILES%,% PROGRAMDATA%% NYILVÁNOS%,% WINDIR%,% TEMP%,% TMP%*
- Csak a pontos fájlkiterjesztések engedélyezettek, például:<br>
  *.log, .txt, .dmp, .cab, .zip, .xml*
- A feltölteni kívánt maximális naplófájl 60 MB vagy 25 fájl, amelyik előbb megtörténik. 
- A Win32-alkalmazás telepítési naplójának gyűjteménye engedélyezve van azon alkalmazások esetében, amelyek megfelelnek a szükséges, elérhető és eltávolított alkalmazás-hozzárendelési szándéknak.
- A tárolt naplók titkosítva vannak a naplókban található személyes adatok biztonsága érdekében.
- A Win32-alkalmazások támogatási jegyének megnyitása közben csatolja a kapcsolódó hibák naplóit a fenti lépésekkel.

## <a name="app-installation-errors"></a>Alkalmazástelepítési hibák

Az alábbi hibaüzenetek és leírások az Androidos és iOS-es telepítési hibák részleteit mutatják be. 

### <a name="android-errors"></a>Android hibák

|    Hibaüzenet/hibakód    |    Leírás    |
|----------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Nem sikerült telepíteni az alkalmazást. (0xC7D14FB5)    |    Ez a hibaüzenet akkor jelenik meg, ha az Intune nem tudja megállapítani az Android-alkalmazás telepítési hibájának kiváltó okát. A hiba során az Android nem adott semmilyen információt.       Ez a hiba akkor lép fel, ha az APK letöltése sikeres volt, az alkalmazás telepítése azonban sikertelen. A hibát gyakran egy hibás APK-fájl okozza, amelyet nem lehet telepíteni az eszközre. Egy lehetséges ok, ha a Google Play Protect biztonsági okokból letiltja az alkalmazás telepítését. Egy másik lehetséges ok, ha az eszköz nem támogatja az alkalmazást. Például ha az alkalmazás az API 21-es vagy újabb verzióját igényli, az eszközön pedig az API 19-es verziója van telepítve.         Az Intune ezt a hibát adja vissza a DA és a KNOX eszközökhöz is, és bár előfordulhat, hogy megjelenik egy értesítés, amelyre kattintva a felhasználó újrapróbálkozhat, ha a problémát az APK okozza, akkor a telepítés mindig sikertelen lesz. Ha az alkalmazás egy opcionálisan elérhető alkalmazás, az értesítés elvethető. Azonban ha az alkalmazás szükséges, az értesítés nem vethető el.        |
|    Az alkalmazás telepítése megszakadt, mert a telepítési (APK) fájl törlődött a letöltés után, de még a telepítés előtt. (0xC7D14FBA)    |    Az APK letöltése sikeres volt, de a fájl el lett távolítva az eszközről, még mielőtt a felhasználó telepítette volna az alkalmazást. Ez akkor fordulhat elő, ha sok idő telt el a letöltés és a telepítés között. A felhasználó például megszakította az eredeti telepítést, megvárta, majd rákattintott az értesítésre az újbóli próbálkozáshoz.         Ez a hibaüzenet csak a DA-forgatókönyveknél jelenik meg. A KNOX-forgatókönyvek csendben elvégezhetők. Megjelenítünk egy újrapróbálkozási értesítést, amelyet a felhasználó elfogadhat a megszakítás helyett. Ha az alkalmazás egy opcionálisan elérhető alkalmazás, az értesítés elvethető. Azonban ha az alkalmazás szükséges, az értesítés nem vethető el.    |
|    Az alkalmazás telepítése megszakadt, mert a folyamat újra lett indítva a telepítés során. (0xC7D14FBB)    |    Az eszköz újraindult az APK telepítési folyamata során, ami egy megszakított telepítést eredményezett.        Ez a hibaüzenet a DA- és KNOX-eszközök esetén is megjelenik. Az Intune megjelenít egy értesítést, amelyre rákattintva a felhasználó újrapróbálkozhat. Ha az alkalmazás egy opcionálisan elérhető alkalmazás, az értesítés elvethető. Azonban ha az alkalmazás szükséges, az értesítés nem vethető el.    |
|    Az alkalmazás nem észlelhető a sikeres telepítést követően. (0x87D1041C)    |    A felhasználó explicit módon eltávolította az alkalmazást. Ezt a hibát nem az ügyfél adja vissza. A hibát az okozza, hogy az alkalmazás valamikor telepítve lett, de aztán a felhasználó eltávolította. Ez a hiba csak a szükséges alkalmazások esetén jelenhet meg. A nem szükséges alkalmazásokat a felhasználó eltávolíthatja. Ez a hiba csak a DA esetén következik be. A KNOX nem engedélyezi a felügyelt alkalmazások eltávolítását.       A következő szinkronizáláskor az eszközön újra megjelenik az értesítés arról, hogy a felhasználó végezze el a telepítést.   A felhasználó figyelmen kívül hagyhatja az értesítést. Az eszköz azonban egészen addig jelenteni fogja a hibát, amíg a felhasználó nem telepíti az alkalmazást.    |
|    A letöltés egy ismeretlen hiba miatt nem sikerült. (0xC7D14FB2)    |    Ez a hiba akkor fordul elő, ha a letöltés sikertelenül végződik. A hibát gyakran a Wi-Fi problémái vagy a lassú kapcsolat okozza.       Ez a hiba csak DA-forgatókönyveknél jelenik meg. A KNOX-forgatókönyveknél a felhasználó nem kap értesítést a telepítésről, mert az csendben elvégezhető. Az Intune megjelenít egy értesítést, amelyre rákattintva a felhasználó újrapróbálkozhat. Ha az alkalmazás egy opcionálisan elérhető alkalmazás, az értesítés elvethető. Azonban ha az alkalmazás szükséges, az értesítés nem vethető el.    |
|    A letöltés egy ismeretlen hiba miatt nem sikerült. Az eszköz a következő szinkronizáláskor újra megpróbálkozik a szabályzattal. (0xC7D15078)    |    Ez a hiba akkor fordul elő, ha a letöltés sikertelenül végződik. A hibát gyakran a Wi-Fi problémái vagy a lassú kapcsolat okozza.       Ez a hiba csak DA-forgatókönyveknél jelenik meg. A KNOX-forgatókönyveknél a felhasználó nem kap értesítést a telepítésről, mert az csendben elvégezhető.    |
|    A végfelhasználó megszakította az alkalmazás telepítését. (0xC7D14FB1)    |    A felhasználó explicit módon eltávolította az alkalmazást. Ezt a hibát akkor adja vissza a rendszer, amikor a felhasználó megszakította az Android operációsrendszer-telepítési tevékenységet. Amikor az operációs rendszer telepítésről szóló prompt megjelent, a felhasználó a Mégse gombra vagy a prompton kívülre kattintott.        Ez a hiba csak DA-forgatókönyveknél jelenik meg. A KNOX-forgatókönyveknél a felhasználó nem kap értesítést a telepítésről, mert az csendben elvégezhető. Az Intune megjelenít egy értesítést, amelyre rákattintva a felhasználó újrapróbálkozhat. Ha az alkalmazás egy opcionálisan elérhető alkalmazás, az értesítés elvethető. Azonban ha az alkalmazás szükséges, az értesítés nem vethető el.    |
|    A fájl letöltésének folyamata váratlanul leállt. (0xC7D15015)    |    Az operációs rendszer leállította a letöltési folyamatot, mielőtt az befejeződött volna. Ez a hiba akkor fordulhat elő, ha az eszköz töltöttségi szintje túl alacsony, vagy a letöltés túl sokáig tart.       Ez a hiba csak DA-forgatókönyveknél jelenik meg. A KNOX-forgatókönyveknél a felhasználó nem kap értesítést a telepítésről, mert az csendben elvégezhető. Az Intune megjelenít egy értesítést, amelyre rákattintva a felhasználó újrapróbálkozhat. Ha az alkalmazás egy opcionálisan elérhető alkalmazás, az értesítés elvethető. Azonban ha az alkalmazás szükséges, az értesítés nem vethető el.    |
|    A fájlletöltési szolgáltatás váratlanul leállt. Az eszköz a következő szinkronizáláskor újra megpróbálkozik a szabályzattal. (0xC7D1507C)    |    Az operációs rendszer leállította a letöltési folyamatot, mielőtt az befejeződött volna. Ez a hiba akkor fordulhat elő, ha az eszköz töltöttségi szintje túl alacsony, vagy a letöltés túl sokáig tart.       Ez a hiba csak DA-forgatókönyveknél jelenik meg. A KNOX-forgatókönyveknél a felhasználó nem kap értesítést a telepítésről, mert az csendben elvégezhető.    |

### <a name="ios-errors"></a>iOS hibák

| Hibaüzenet/hibakód | Leírás/hibaelhárítási tippek |
|------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| (0x87D12906) | Az Apple MDM-ügynök visszaadotta, hogy a telepítési parancs sikertelen volt. |
| (0x87D1313C) | A hálózati kapcsolat megszakadt a frissített letöltési szolgáltatás URL-címének az eszközre való küldése során. Pontosabban nem található a megadott állomásnévvel rendelkező kiszolgáló. |
| az iOS-eszköz jelenleg foglalt. (0x87D11388) | Az iOS-eszköz foglalt, ami hibát eredményezett. |
| Az alkalmazás telepítése nem sikerült. (0x87D13B64) | Alkalmazás-telepítési hiba történt. A hiba okának felderítéséhez szükség van az XCODE-naplókra. |
| Az alkalmazás felügyelt, de a felhasználó lejárt vagy el lett távolítva. (0x87D13B66) | A felhasználó explicit módon eltávolította az alkalmazást. Vagy az alkalmazás lejárt, de nem sikerült letölteni, vagy az alkalmazás észlelésének eredménye nem egyezik meg az eszköz által küldött válasszal.   Emellett a hibát az iOS 9.2.2 platform egyik hibája is okozhatja. |
| Az alkalmazás telepítésre van ütemezve, de a tranzakció elvégzéséhez szükség van egy beváltási kódra. (0x87D13B60) | Ez a hiba általában olyan iOS-es áruházbeli alkalmazásokban fordul elő, amelyek fizetős alkalmazások. |
| A telepítés sikeres befejezése után az alkalmazás nem észlelhető.   (0x87D1041C) | Az alkalmazás észlelési folyamata nem felelt meg az eszköz válaszának. |
| A felhasználó elutasította az alkalmazás telepítésére vonatkozó ajánlatot. (0x87D13B62) | Az alkalmazás kezdeti telepítésekor a felhasználó a Mégse gombra kattintott. |
| A felhasználó elutasította az alkalmazás frissítésére vonatkozó ajánlatot. (0x87D13B63) | A végfelhasználó rákattint a Mégse gombra a frissítési folyamat során. |
| Ismeretlen hiba (0x87D103E8) | Ismeretlen alkalmazás-telepítési hiba történt. Ez a hiba akkor következik be, ha más hibák nem történtek meg. |
| A VPP-alkalmazásokat csak megosztott iPadre lehet telepíteni (-2016330861). | Az alkalmazásokat a Apple Volume Purchase Program használatával kell beszerezni egy megosztott iPaden való telepítéshez. |
| Nem lehet alkalmazásokat telepíteni, ha az App Store le van tiltva (-2016330860).  | Az App Store-nak engedélyezve kell lennie ahhoz, hogy a felhasználó telepítse az alkalmazást. |
| Nem található a VPP-licenc az alkalmazáshoz (-2016330859).  | Próbálja meg visszavonni és újból hozzárendelni az alkalmazás licencét. |
| A rendszeralkalmazások nem telepíthetők a MDM-szolgáltatóval (-2016330858). | Az iOS operációs rendszer által előre telepített alkalmazások telepítése nem támogatott. |
| Nem lehet alkalmazásokat telepíteni, ha az eszköz elveszett módban van (-2016330857). | Az eszköz minden használata elveszett módban van letiltva.   Az elveszett üzemmód letiltása az alkalmazások telepítéséhez. |
| Az alkalmazások nem telepíthetők, ha az eszköz kioszk módban van (-2016330856). | Próbálja meg hozzáadni az eszközt egy kizárási csoporthoz a kioszk mód konfigurációs házirendjéhez az alkalmazások telepítéséhez. |
| Az 32-bites alkalmazások nem telepíthetők erre az eszközre (-2016330852). | Az eszköz nem támogatja a 32 bites alkalmazások telepítését. Próbálja meg telepíteni az alkalmazás 64 bites verzióját. |
| A felhasználónak be kell jelentkeznie az App Store-ba (-2016330855). | Az alkalmazás telepítésének megkezdése előtt a felhasználónak be kell jelentkeznie az alkalmazás-áruházba. |
| Ismeretlen probléma. Próbálkozzon újra (-2016330854). | Az alkalmazás telepítése ismeretlen ok miatt meghiúsult.   Próbálkozzon újra később. |
| Az alkalmazás telepítése nem sikerült. Az Intune újra próbálkozik az eszköz következő szinkronizálásakor (-2016330853). | Az alkalmazás telepítése eszköz hibába ütközött. Az eszköz szinkronizálásával próbálja megismételni az alkalmazás telepítését. |

### <a name="other-installation-errors"></a>Egyéb telepítési hibák

|    Hibaüzenet/kód    |    Leírás    |
|-----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    0x80073CFF, 0x80CF201C (ügyfél-hiba)    |    Az alkalmazás telepítéséhez közvetlen telepítést lehetővé tevő rendszerrel kell rendelkeznie. Győződjön meg arról, hogy az alkalmazáscsomag megbízható aláírással van aláírva, és telepítve van egy tartományhoz csatlakoztatott eszközön, amelyen engedélyezve van a **AllowAllTrustedApps** szabályzat, vagy olyan eszköz, amely rendelkezik a **AllowAllTrustedApps** házirenddel rendelkező Windows közvetlen telepítési-licenccel. engedélyezve. További információ: [a Windows áruházbeli alkalmazások csomagolásának hibaelhárítása, üzembe helyezése és lekérdezése](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).     |
|    0x80073CF0    |    A csomag nem nyitható meg. Lehetséges okok:<ul><li> A csomag nincs aláírva.</li><li> A közzétevő neve nem egyezik meg az aláíró tanúsítvány tulajdonosával.</li></ul> További információért olvassa el az **appxpackagingom eseménynaplóban talál** -eseménynaplót. További információ: [a Windows áruházbeli alkalmazások csomagolásának hibaelhárítása, üzembe helyezése és lekérdezése](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).    |
|    0x80073CF3    |    A csomag nem tudta frissíteni, függőséget vagy ütközést érvényesíteni. Lehetséges okok:<ul><li> A bejövő csomag ütközik egy telepített csomaggal.</li><li> A megadott csomag-függőség nem található.</li><li> A csomag nem támogatja a megfelelő processzor-architektúrát.</li></ul> További információért olvassa el a **AppXDeployment-Server** eseménynaplóját. További információ: [a Windows áruházbeli alkalmazások csomagolásának hibaelhárítása, üzembe helyezése és lekérdezése](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).    |
|    0x80073CFB    |    A megadott csomag már telepítve van, és a csomag újratelepítése le van tiltva. Ez a hiba akkor jelenhet meg, ha olyan csomagot telepít, amely nem azonos a már telepített csomaggal. Ellenőrizze, hogy a csomag tartalmaz-e digitális aláírást. Ha újraépít vagy újra aláír egy csomagot, a csomag nem lesz bitenként azonos az előzőleg telepített csomaggal. Ez a hiba kétféleképpen javítható ki:<ul><li> Növelje az alkalmazás verziószámát, majd építse újra, majd írja alá újra a csomagot.</li><li> Az új csomag telepítése előtt távolítsa el a régi csomagot a rendszer minden felhasználója számára.</li></ul> További információ: [a Windows áruházbeli alkalmazások csomagolásának hibaelhárítása, üzembe helyezése és lekérdezése](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).    |
|    0x87D1041C    |    Az alkalmazás telepítése sikeres volt, de a rendszer nem ismeri fel az alkalmazást. Az alkalmazást az Intune sikeresen telepítette, majd ezt követően eltávolította. Az alkalmazás eltávolításának okai a következők:<ul><li> A végfelhasználó eltávolította az alkalmazást.</li><li> A csomagban lévő azonosító adatok nem egyeznek meg a hibás alkalmazásokhoz tartozó eszközök jelentéseivel.</li><li>Az önfrissítő rendszercsomagok a termék verziója nem felel meg az alkalmazásnak az Intune-on kívüli frissítés utáni információjának.</li></ul> Kérje meg a felhasználót, hogy telepítse újra az alkalmazást a vállalati portálról. Vegye figyelembe, hogy a szükséges alkalmazások újratelepítése automatikusan megtörténik, amikor az eszköz következő bejelentkezik.    |
|    0x8000FFFF    |    Váratlan hiba történt a telepítés során. További információért olvassa el a telepítési naplókat.    |

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>A Microsoft Áruházból származó alkalmazások hibáinak elhárítása

A [Troubleshooting packaging, deployment, and query of Microsoft Store apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) (A Microsoft Áruházbeli alkalmazások csomagolási, telepítési és lekérdezési hibáinak elhárítása) című cikkben foglaltak segítenek elhárítani az alkalmazásoknak a Microsoft Áruházból akár Intune-nal, akár más módon történő telepítésekor tapasztalt gyakori problémákat.

## <a name="app-troubleshoooting-resources"></a>Alkalmazás-troubleshoooting erőforrásai
- [A Visio és a Project üzembe helyezése az Office Pro Plus üzembe helyezésének részeként](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Deploying-Visio-and-Project-as-part-of-your-Office/ba-p/701795)
- [Végezze el az Intune-telepítéssel telepített MSfB alkalmazások Windows 10 1903 rendszeren való telepítését.](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Take-Action-to-Ensure-MSfB-Apps-deployed-through/ba-p/658864)
- [MSI-alkalmazások központi telepítésének hibaelhárítása Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-MSI-App-deployments-in-Microsoft/ba-p/359125)
- [Ajánlott eljárások a szoftverek terjesztéséhez a klasszikus Intune-ban Windows PC-ügynök](https://support.microsoft.com/en-us/help/2583929/best-practices-for-intune-software-distribution-to-windows-pc)

## <a name="next-steps"></a>További lépések

- További információt az Intune hibaelhárításáról a [Segítségnyújtás a céges felhasználóknak a hibaelhárítási portál használatával](help-desk-operators.md) című témakörben talál. 
- Ismertető a Microsoft Intune esetleges ismert problémáiról. További információ: az [Intune-ügyfél sikeressége](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess).
- További segítségre van szüksége? Ismerje meg, [hogyan kérhet támogatást az Intune-hoz](get-support.md).

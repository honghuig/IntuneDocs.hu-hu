---
title: Mobilalkalmazás-kezelési hibaelhárítás
titleSuffix: Microsoft Intune
description: Ez a témakör ismerteti a feltételes hozzáférést néhány hibaelhárítási tipp.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/03/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1cf8f7753a92ad45a68f976359560ef6da2d1cec
ms.sourcegitcommit: 1b7ee2164ac9490df4efa83c5479344622c181b5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/08/2019
ms.locfileid: "67648723"
---
# <a name="troubleshoot-mobile-application-management"></a>Mobilalkalmazás-kezelési hibaelhárítás

Ez a témakör az Intune App Protection (más néven MAM vagy mobileszköz-kezelésben) használatakor előforduló gyakori problémák megoldása.

Ha ezekkel az információkkal nem tudja megoldani a problémát, a [Hogyan kérhet támogatást az Intune-hoz](get-support.md) című témakörben talál további részleteket a segítségkéréshez.

## <a name="common-it-administrator-issues"></a>A rendszergazdáknál gyakran előforduló problémák

Ezek a gyakori problémák az Intune alkalmazásvédelmi szabályzatai segítségével a rendszergazdák tapasztalhatnak.

| Probléma | Leírás | Megoldás: |
| -- | -- | -- |
| A Skype Vállalati verzióra nem vonatkozó szabályzat | Az Azure Portalon beállított, eszközregisztráció nélküli alkalmazásvédelmi szabályzat nem lép életbe az iOS- és Android-eszközökön futó Skype Vállalati verzió alkalmazásra vonatkozóan. | A Skype Vállalati verziót a modern hitelesítésre kell beállítani.  Kövesse a [Bérlő engedélyezése modern hitelesítéshez](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) című részben található utasításokat a modern hitelesítés beállításához Skype-hoz. |
| Nem alkalmazott Office-alkalmazás-szabályzat | Az alkalmazásvédelmi szabályzatok egyetlen felhasználónál sem lépnek életbe a [támogatott Office-alkalmazásokra](https://www.microsoft.com/cloud-platform/microsoft-intune-partners) vonatkozóan. | Ellenőrizze, hogy a felhasználók rendelkeznek-e Intune-licenccel, illetve, hogy a használt alkalmazásvédelmi szabályzat megcélozza-e az Office-alkalmazásokat. Az újonnan beállított alkalmazásvédelmi szabályzatok életbe lépéséhez esetenként 8 órának is el kell telnie. |
| A rendszergazda nem tudja beállítani az alkalmazásvédelmi szabályzatot az Azure Portalon | Informatikai rendszergazda nem tudja az alkalmazásvédelmi szabályzatok konfigurálása az Azure Portalon. | Az alábbi felhasználói szerepkörök rendelkeznek hozzáféréssel az Azure Portalra: <ul><li>Globális rendszergazda; Ez a beállíthat a [Microsoft 365 felügyeleti központban](https://admin.microsoft.com/)</li><li>Tulajdonos; Ez a beállíthat a [az Azure portal](https://portal.azure.com/).</li><li>Közreműködő; Ez a beállíthat a [az Azure portal](https://portal.azure.com/).</li></ul> Tekintse meg [szerepköralapú vezérlés (RBAC) a Microsoft Intune-nal](role-based-access-control.md) a szerepkörök beállításával, segítségért.|
|Az alkalmazásvédelmi szabályzat jelentéseiből hiányzó felhasználói fiókok | A felügyeleti konzol jelentéseiben nem szerepelnek azok a felhasználói fiókok, amelyekre a közelmúltban alkalmazták az alkalmazásvédelmi szabályzatot. | Az alkalmazásvédelmi szabályzattal újonnan megcélzott felhasználók esetében előfordul, hogy 24 órának is el kell telnie, hogy a felhasználó megjelenjen a jelentésekben. |
| Nem működő szabályzatváltozások | Az alkalmazásvédelmi szabályzatokat érintő változások és frissítések életbe lépéséhez akár 8 órára is szükség lehet. | Ha alkalmazandó, a végfelhasználó jelentkezzen ki az alkalmazásból, majd jelentkezzen be újra, ezzel kényszerítve a szinkronizálást a szolgáltatással. |
| Az alkalmazásvédelmi szabályzat nem működik a DEP-pel | Az alkalmazásvédelmi szabályzat nem lép érvénybe az Apple DEP-eszközökön. | Győződjön meg róla, hogy használja-e a Felhasználói affinitás funkciót az Apple Eszközregisztrációs programmal (DEP). Felhasználói affinitásra minden olyan alkalmazás esetében szükség van, amely felhasználói hitelesítést igényel DEP alatt. <br><br>Tekintse meg [automatikusan iOS-eszközök regisztrálása az Apple Device Enrollment Program](device-enrollment-program-enroll-ios.md) iOS DEP-regisztrációról bővebben.|
| Az adatátviteli szabályzat nem működik iOS-szel | A **Más alkalmazásokból való adatátvitel engedélyezése az alkalmazásnak** és a **Más alkalmazásokból való adatfogadás engedélyezése az alkalmazásnak** szabályzatok nem tudják kezelni az adatátvitelt az iOS-ben. | Lásd: [kezelése a Microsoft Intune-ban iOS-alkalmazások közti adatátvitel](data-transfer-between-apps-manage-ios.md). |

## <a name="common-end-user-issues"></a>A végfelhasználóknál előforduló gyakori problémák

A végfelhasználóknál előforduló gyakori problémák a következő kategóriákba sorolhatók:

* **Normál használati forgatókönyvek**: A végfelhasználó ezen forgatókönyvek szerinti, amely az Intune alkalmazásvédelmi szabályzattal rendelkeznek az alkalmazások tapasztalhat. Ezek nem tényleges problémákat, de problémának vagy hibáknak tűnhetnek.

* **Normál használati párbeszédpanelek**: Ezek a használati párbeszédpanelek egy olyan Intune alkalmazásvédelmi szabályzattal rendelkeznek az alkalmazások láthatják. Ezeket az üzeneteket és párbeszédpanelek **nem** hibát jeleznek.

* **Hibaüzenetek és párbeszédpanelek**: Ezek a hibaüzenetek és párbeszédpanelek láthatják az alkalmazásokkal, az Intune alkalmazásvédelmi szabályzattal rendelkeznek. Ezek gyakran a rendszergazda által elkövetett hibát jeleznek, vagy az Intune-alkalmazásvédelem hibáját.

### <a name="normal-usage-scenarios"></a>Normál használati forgatókönyvek

Platform | Forgatókönyv | Magyarázat |
---| --- | --- |
iOS | A végfelhasználó az iOS megosztási bővítménnyel megnyithatja a munkahelyi vagy az iskolai adatokat a nem felügyelt alkalmazásokban, még akkor is, ha az adatátviteli szabályzat beállítása **Csak felügyelt alkalmazások** vagy **Nincs alkalmazás**. Nem jár ez adatszivárgással? | Az Intune alkalmazásvédelmi szabályzata nem tudja kezelni az iOS megosztási bővítményt az eszköz felügyelete nélkül. Ezért az **Intune titkosítja a „céges” adatokat, mielőtt az alkalmazáson kívül megosztaná**. Ezt úgy ellenőrizheti, hogy megpróbálja megnyitni a „céges” fájlt a felügyelt alkalmazáson kívüli más alkalmazással. A fájlnak titkosítottnak kell lennie, így a felügyelt alkalmazáson kívül mással nem nyitható meg.
iOS | Miért nem a végfelhasználó **a Microsoft Authenticator alkalmazás telepítésére kéri** | Erre azért van szükség, amikor az alkalmazás alapú feltételes hozzáférés alkalmazása, lásd: [jóváhagyott ügyfélalkalmazás megkövetelése](https://docs.microsoft.com/azure/active-directory/conditional-access/app-based-conditional-access).
Android | Miért kell a végfelhasználónak akkor is **telepítenie a Céges portál alkalmazást**, ha MAM-alkalmazásvédelmet használok eszközregisztráció nélkül?  | Androidon a legtöbb alkalmazásvédelmi funkció be van építve a Céges portál alkalmazásba. **Annak ellenére, hogy a Céges portál alkalmazás mindig szükséges, eszközregisztrációra nincs szükség**. A regisztráció nélküli alkalmazásvédelemhez a végfelhasználónak telepítenie kell a Céges portál alkalmazást az eszközre.
iOS/Android | Alkalmazásvédelmi szabályzat nem vázlat e-mailt az Outlook alkalmazás a alkalmazni | Mivel az Outlook támogatja a vállalati és személyes környezet, azt nem kényszeríti ki a MAM a draft e-mailt.
iOS/Android | Alkalmazásvédelmi szabályzat nem alkalmazza az új dokumentumok WXP (Word, Excel, PowerPoint) | Vállalati és személyes környezet támogatja a WXP, mivel azt nem kényszeríti ki MAM az új dokumentumok például a OneDrive vállalati azonosított helyen mentéséig.
iOS/Android | Az alkalmazások nem teszi lehetővé a Mentés másként helyi tárba, ha a szabályzat engedélyezve van | Az alkalmazás fejlesztőjének ehhez a beállításhoz az alkalmazás viselkedését vezérli.
Android | Android rendelkezik, mint az iOS-es milyen "natív" alkalmazások hozzáférhetnek a MAM által védett tartalom további korlátozások | Az Android a nyílt platformnak és a "natív" alkalmazás társítása a végfelhasználók által módosítható potenciálisan nem biztonságos alkalmazásokat. Alkalmazása [az adatátviteli szabályzat kivételei](app-protection-policies-exception.md) adott alkalmazásokra érvényes.
Android | Az Azure Information Protection (AIP) PDF-fájlként mentheti, ha a Mentés másként gátolja meg a rendszer | Az AIP figyelembe veszi a "Disable nyomtatáshoz" a MAM-szabályzat használatakor Mentés PDF-fájlként.
iOS | Az Outlook alkalmazás a PDF-mellékletek megnyitására meghiúsul, és "művelet nem engedélyezett | Ez akkor fordulhat elő, ha a felhasználó még nem végzett hitelesítést a Acrobat olvasó az Intune-ban, vagy rendelkezik ujjlenyomat hitelesítéséhez használt saját szervezet számára. Nyissa meg előre Acrobat olvasó, és a hitelesítés UPN hitelesítő adatok használatával.


### <a name="normal-usage-dialogs"></a>Normál használati párbeszédpanelek

Platform | Üzenet vagy párbeszédpanel | Magyarázat |
--- | --- | --- |
iOS, Android | **Jelentkezzen be**: Az adatok védelme a munkahelyének felügyelnie kell ezt az alkalmazást. A művelet befejezéséhez jelentkezzen be a munkahelyi vagy az iskolai fiókjába. | A végfelhasználónak egy alkalmazásvédelmi szabályzatot igénylő alkalmazás használatához munkahelyi vagy iskolai fiókjával kell bejelentkeznie. Ahhoz, hogy a szabályzat vonatkozik a felhasználói hitelesítést kell végeznie az Azure Active Directoryban.
iOS, Android |**Újraindítás szükséges**: A szervezet már védi az adatokat az alkalmazásban. A folytatáshoz újra kell indítania az alkalmazást. | Az alkalmazás épp megkapta az Intune alkalmazásvédelmi szabályzatot, és ahhoz, hogy a szabályzat érvénybe léptetéséhez újra kell indítani.
iOS, Android |**A művelet nem engedélyezett**: A szervezet csak lehetővé teszi, hogy ezt az alkalmazást munkahelyi vagy iskolai adatok megnyitását. | A rendszergazda a **Más alkalmazásokból való adatfogadás engedélyezése az alkalmazásnak** beállításaként a **Csak felügyelt alkalmazások** lehetőséget adta meg. Ezért a végfelhasználó csak viheti át az adatokat ebbe az alkalmazásba egy alkalmazásvédelmi szabályzattal rendelkező más alkalmazásokból.
iOS, Android |**A művelet nem engedélyezett**: A szervezet csak lehetővé teszi az adatok átviteléhez más kezelt alkalmazásokba. | A rendszergazda **Az alkalmazás átadhat adatokat más alkalmazásoknak** beállításaként a **Csak felügyelt alkalmazások** lehetőséget adta meg. Ezért a végfelhasználó csak küldhetnek adatokat ebből az alkalmazásból egy alkalmazásvédelmi szabályzattal rendelkező más alkalmazásokba.
iOS, Android |**Törlési riasztás**: Munkahelye eltávolította az ehhez az alkalmazáshoz hozzárendelt adatokat. A folytatáshoz indítsa újra az alkalmazást. | A rendszergazda az Intune alkalmazásvédelmi funkciójával kezdeményezte az alkalmazástörlés.
Android | **Céges portál szükséges**: Munkahelyi vagy iskolai fiókját használja az alkalmazással, telepítenie kell az Intune vállalati portál alkalmazást. Kattintson a "Ugrás az áruházba" gombra a folytatáshoz. | Androidon a legtöbb alkalmazásvédelmi funkció be van építve a Céges portál alkalmazásba. **Annak ellenére, hogy a Céges portál alkalmazás mindig szükséges, eszközregisztrációra nincs szükség**. A regisztráció nélküli alkalmazásvédelemhez a végfelhasználónak telepítenie kell a Céges portál alkalmazást az eszközre.

### <a name="error-messages-and-dialogs-on-ios"></a>Hibaüzenetek és párbeszédpanelek az iOS-ben

Hibaüzenet vagy párbeszédpanel | Ok | Szervizelés |
-- | --- | --- |
**Alkalmazás nem állította be**: Ez az alkalmazás nincs beállítva a használatra. Segítségért forduljon a rendszergazdához. | Hiba történt egy alkalmazásvédelmi szabályzatot az alkalmazás észleléséhez. |Léptessen életbe egy iOS-es alkalmazásvédelmi szabályzatot a felhasználó biztonsági csoportjában, és célozza meg benne ezt az alkalmazást.
**Üdvözli az Intune Managed Browser**: Ez az alkalmazás akkor működik a legjobban, ha a Microsoft Intune által kezelt. Bármikor böngészheti vele az internetet. Ha az alkalmazást a Microsoft Intune felügyeli, további adatbiztonsági funkciókat is elérhet. | Hiba történt észleléséhez egy alkalmazásvédelmi szabályzatot az Intune Managed Browser alkalmazás. <br><br>A felhasználó ebben az esetben is internetezhet, de az alkalmazást nem az Intune fogja felügyelni. | Léptessen életbe egy iOS-es alkalmazásvédelmi szabályzatot a felhasználó biztonsági csoportjában, és célozza meg benne ezt az Intune Managed Browser alkalmazást.
**Sikertelen bejelentkezés**: Nem tudjuk beléptetni most. Próbálkozzon újra később. | Nem sikerült regisztrálni a felhasználót a MAM-szolgáltatásban, miután a felhasználó megpróbált munkahelyi vagy iskolai fiókjával bejelentkezni. | Léptessen életbe egy iOS-es alkalmazásvédelmi szabályzatot a felhasználó biztonsági csoportjában, és célozza meg benne ezt az alkalmazást.
**A fiók nincs beállítva**: A szervezete nem állította be a fiókját a munkahelyi vagy iskolai adatok elérésére. Kérjen segítséget a rendszergazdától. | A felhasználói fiókhoz nem tartozik Intune A Direct-licenc. | Győződjön meg arról, hogy a felhasználói fiók van hozzárendelve az Intune-licencet a [Microsoft 365 felügyeleti központban](https://admin.microsoft.com).
**Nem felel meg az eszköz**: Ez az alkalmazás nem használható, mert Ön egy feltört eszközt használ. Segítségért forduljon a rendszergazdához. | Az Intune észlelte, hogy a felhasználó feltört eszközt használ. | Állítsa vissza az eszköz gyári alapbeállításait. Kövesse az Apple támogatói webhelyén található [utasításokat](https://support.apple.com/HT201274).
**Internetkapcsolat szükséges**: Akkor kapcsolódnia kell az internethez, ellenőrizze, hogy az alkalmazás használhatja. | Az eszközön nincs internetkapcsolat. | Csatlakoztassa az eszközt egy Wi-Fi- vagy adathálózathoz.
**Ismeretlen hiba történt**: Próbálja meg újraindítani az alkalmazást. Ha nem szűnik meg a probléma, kérjen segítséget a rendszergazdától. | Ismeretlen hiba történt. | Próbálkozzon újra egy kis idő elteltével. Ha a hiba továbbra is fennáll, hozzon létre egy [támogatási jegyet](get-support.md#create-an-online-support-ticket) az Intune-nal.
**Hozzáférés a szervezet adataihoz**: A megadott munkahelyi vagy iskolai fiók nem rendelkezik hozzáféréssel ehhez az alkalmazáshoz. Lehetséges, hogy másik fiókkal kell bejelentkeznie. Segítségért forduljon a rendszergazdához. | Az Intune észlelte, hogy a felhasználó egy második, az eszközön a MAM-mal regisztrált fióktól eltérő munkahelyi vagy iskolai fiókkal próbál bejelentkezni. A MAM egyszerre csak egy munkahelyi vagy iskolai fiókot képes kezelni egy eszközön. | A felhasználó jelentkezzen be azzal a fiókkal, amelynek felhasználóneve megjelenik a bejelentkezési képernyőn. Szükség lehet [az Intune-hoz a felhasználói UPN-beállítás konfigurálása](https://docs.microsoft.com/intune/data-transfer-between-apps-manage-ios#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm). <br> <br> Vagy jelentkezzen be az új munkahelyi vagy iskolai fiókkal, és távolítsa el a MAM-mal jelenleg regisztrált fiókot.
**Csatlakozási probléma**: Váratlan csatlakozási probléma lépett fel. Ellenőrizze a kapcsolatot, majd próbálkozzon újra.  |  Váratlan hiba. | Próbálkozzon újra egy kis idő elteltével. Ha a hiba továbbra is fennáll, hozzon létre egy [támogatási jegyet](get-support.md#create-an-online-support-ticket) az Intune-nal.
**Riasztási**: Ez az alkalmazás már nem használható. További információért forduljon a rendszergazdához. | Nem sikerült ellenőrizni az alkalmazás tanúsítványának érvényességét. | Ellenőrizze, hogy az alkalmazás naprakész verzióját használja-e. <br><br> Telepítse újra az alkalmazást.
**Hiba**: Az alkalmazás problémát észlelt, és be kell zárni. Ha nem szűnik meg a probléma, forduljon a rendszergazdához. | Nem sikerült beolvasni a MAM-alkalmazás PIN kódját az Apple iOS kulcsláncából. | Indítsa újra az eszközt. Ellenőrizze, hogy az alkalmazás naprakész verzióját használja-e. <br><br> Telepítse újra az alkalmazást.

### <a name="error-messages-and-dialogs-on-android"></a>Hibaüzenetek és párbeszédpanelek az Androidban

Párbeszédpanel/hibaüzenet | Ok | Szervizelés |
-- | --- | --- |
**Alkalmazás nem állította be**: Ez az alkalmazás nincs beállítva a használatra. Segítségért forduljon a rendszergazdához. | Hiba történt egy alkalmazásvédelmi szabályzatot az alkalmazás észleléséhez. |Léptessen életbe egy Andoridos alkalmazásvédelmi szabályzatot a felhasználó biztonsági csoportjában, és célozza meg benne ezt az alkalmazást.
**Sikertelen alkalmazások indítása**: Hiba történt az alkalmazás indításakor. Próbálja meg frissíteni az alkalmazást vagy az Intune Munkahelyi portál alkalmazást. Ha segítségre van szüksége, lépjen kapcsolatba a rendszergazdával. | Az Intune észleli az alkalmazásra vonatkozó érvényes alkalmazásvédelmi szabályzatot, de az alkalmazás összeomlik a MAM inicializálása során. | Ellenőrizze, hogy az alkalmazás naprakész verzióját használja-e. <br><br> Ellenőrizze, hogy telepítve van-e az eszközön az Intune Munkahelyi portál alkalmazás, és hogy naprakész-e. <br><br> Ha a hiba továbbra is fennáll, használja a vállalati portál alkalmazás naplók küldése az Intune-ba, vagy hozzon létre egy [támogatási jegyet](get-support.md#create-an-online-support-ticket).
**Nem találhatók alkalmazások**: Nincsenek alkalmazások az eszköz, amellyel munkahelye engedélyezné a tartalom megnyitását. Segítségért forduljon a rendszergazdához. | A felhasználó munkahelyi vagy iskolai adatokat próbált meg megnyitni egy másik alkalmazásban, de az Intune nem talált olyan más felügyelt alkalmazást, amely jogosult az adatok megnyitására. | Állítson be egy androidos alkalmazásvédelmi szabályzatot a felhasználó biztonsági csoportjában, és célozzon meg vele legalább egy másik MAM-kompatibilis alkalmazást, amely alkalmas a kérdéses adatok megnyitására.
**Sikertelen bejelentkezés**: Próbálja meg újra bejelentkezni. Ha nem szűnik meg a probléma, kérje a rendszergazda segítségét. | Nem sikerült hitelesíteni a fiókot, amellyel a felhasználó megpróbál bejelentkezni. | A felhasználó azzal a munkahelyi vagy iskolai fiókkal jelentkezzen be, amely már regisztrálva van az Intune MAM-szolgáltatásában (ez az első munkahelyi vagy iskolai fiók, amellyel sikeresen bejelentkezett ebbe az alkalmazásba). <br><br> Törölje az alkalmazásadatokat. <br><br> Ellenőrizze, hogy az alkalmazás naprakész verzióját használja-e. <br><br> Ellenőrizze, hogy a Munkahelyi portál alkalmazás naprakész verzióját használja-e.
**Internetkapcsolat szükséges**: Akkor kapcsolódnia kell az internethez, ellenőrizze, hogy az alkalmazás használhatja. | Az eszközön nincs internetkapcsolat. | Csatlakoztassa az eszközt egy Wi-Fi- vagy adathálózathoz.
**Nem megfelelő eszköz**: Ez az alkalmazás nem használható, mert Ön egy rootolt eszközt használ. Segítségért forduljon a rendszergazdához. | Az Intune észlelte, hogy a felhasználó feltört eszközt használ. | Állítsa vissza az eszköz gyári alapbeállításait.
**A fiók nincs beállítva**: A Microsoft Intune-nal felügyelni ezt az alkalmazást, de a fiók nincs beállítva. Segítségért forduljon a rendszergazdához. | A felhasználói fiókhoz nem tartozik Intune A Direct-licenc. | Győződjön meg arról, hogy a felhasználói fiók van hozzárendelve az Intune-licencet a [Microsoft 365 felügyeleti központban](https://admin.microsoft.com).
**Nem sikerült regisztrálni az alkalmazást**: A Microsoft Intune-nal felügyelni ezt az alkalmazást, de nem sikerült regisztrálni az alkalmazást jelenleg. Segítségért forduljon a rendszergazdához. | Nem sikerült automatikusan regisztrálni az alkalmazást a MAM-szolgáltatásban, pedig alkalmazásvédelmi szabályzatra van szükség. | Törölje az alkalmazásadatokat. <br><br> Naplók küldése az Intune a céges portál alkalmazáson keresztül, vagy küldjön egy támogatási jegyet. További információkért lásd: [hogyan kérhet támogatást a Microsoft Intune](get-support.md).

## <a name="next-steps"></a>További lépések

- [A mobilalkalmazás-kezelés beállításának ellenőrzése](app-protection-policies-validate.md)
- Megtudhatja, hogyan használja a naplófájlok hibáinak elhárítása az Intune alkalmazásvédelmi szabályzatának, lásd: [https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Intune-app-protection-policy-using/ba-p/330372](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Intune-app-protection-policy-using/ba-p/330372)
- További információt az Intune hibaelhárításáról a [Segítségnyújtás a céges felhasználóknak a hibaelhárítási portál használatával](help-desk-operators.md) című témakörben talál. 
- Ismertető a Microsoft Intune esetleges ismert problémáiról. További információt [Az Intune ismert problémái](known-issues.md) című témakörben talál.
- További segítségre van szüksége? Ismerje meg, [hogyan kérhet támogatást az Intune-hoz](get-support.md).

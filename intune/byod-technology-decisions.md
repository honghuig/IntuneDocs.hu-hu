---
title: Technológiai döntések a hozott eszközök EMS általi felügyeletéhez
description: Fő technológiai döntések a hozott eszközök engedélyezésével, illetve a céges adatok Microsoft Enterprise Mobility + Security szolgáltatással való védelmével kapcsolatban.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 12/8/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: c2e8c475cd52e199519db7a3d7ea83e6dbfef1a3
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67530653"
---
# <a name="technology-decisions-for-enabling-byod-with-microsoft-enterprise-mobility--security-ems"></a>Technológiai döntések a hozott eszközök Microsoft Enterprise Mobility + Security (EMS) általi felügyeletével kapcsolatban.

A dolgozók távoli, saját eszközön való munkavégzését lehetővé tevő stratégia kidolgozása során fontos döntéseket kell meghoznia a hozott eszközök engedélyezésével és a céges adatok védelmével kapcsolatban. Az EMS szerencsére egy olyan teljes körű megoldás, amely minden szükséges képességgel rendelkezik.  

A jelen témakörben a hozott eszközök céges levelezés elérésére való bevezetésének egyszerű esetét vizsgáljuk meg. Arra a kérdésre fogunk összpontosítani, hogy szükséges-e a teljes eszköz felügyelete, vagy pedig elég csak az alkalmazásokat felügyelni. Mindkettő érvényes választás.

## <a name="assumptions"></a>Előfeltételek
* Az Azure Active Directory és a Microsoft Intune alapvető ismerete
* Exchange Online-ban tárolt e-mail-fiókok

## <a name="common-reasons-to-manage-the-device-mdm"></a>Gyakori érvek a teljes eszköz felügyelete mellett (MDM)
Könnyedén hozzásegítheti a felhasználókat eszközeik regisztrálásához eszköz felügyeletre való üzembe helyezésével egy [feltételes hozzáférési](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) szabályzat Exchange Online-on. Az alábbi okokból lehet szükség a személyes eszközök felügyeletére:

**WiFi/VPN** – Ha a felhasználóknak a produktív munkához céges csatlakozási profilra van szükségük, könnyedén konfigurálhatja ezt.

**Alkalmazások** – Ha a felhasználók eszközére alkalmazásokat kell leküldeni, zökkenőmentesen kézbesítheti ezeket. Ide tartozhatnak például a biztonsági okokból szükséges alkalmazások, ideértve a Mobile Threat Defense alkalmazást is.

**Megfelelőség** – Egyes cégeknek meg kell felelniük bizonyos jogszabályoknak vagy más előírásoknak, melyek specifikus MDM-vezérlést igényelnek. Előfordulhat például, hogy az MDM segítségével titkosítania kell a teljes eszközt, vagy jelentést kell készítenie az eszközön megtalálható összes alkalmazásról.

## <a name="common-reasons-to-only-manage-the-apps-mam"></a>Gyakori érvek csak az alkalmazások felügyelete mellett (MAM)
Az MDM nélküli MAM rendkívül népszerű a hozott eszközt támogató cégek körében. A feltételes hozzáférési szabályzat Exchange Online-on üzembe helyezésével ösztönözheti a felhasználókat, e-mailek elérését az Outlook Mobile alkalmazással (mely támogatja a MAM-védelem). Az alábbi okokból lehet szükség arra, hogy csak az alkalmazásokat felügyelje a személyes eszközökön:

**Felhasználói élmény** – Az MDM-regisztráció számos (platform által kényszerített) figyelmeztető üzenet megjelenésével jár, melyek hatására a felhasználók gyakran úgy döntenek, hogy inkább nem szeretnének hozzáférni a levelezésükhöz a személyes eszközükön. A MAM sokkal kevésbé ijesztő a felhasználóknak, hiszen csak egy előugró üzenet jelenik meg egyszer, mely tudatja velük, hogy a MAM-védelem aktív.

**Megfelelőség** – Egyes cégeknél előfordulhat, hogy olyan szabályzatoknak kell megfelelni, amelyek alacsonyabb fokú felügyeleti képességeket írnak elő a személyes eszközökhöz. A MAM például csak céges adatokat képes eltávolítani az alkalmazásokból, ellentétben az MDM-mel, mely képes eltávolítani az eszközön tárolt összes adatot.

![Kép, mely összehasonlítja a mobileszköz felügyeletét az alkalmazások felügyeletével](./media/byod-app-device-mgmt.png)

Tudjon meg többet az [eszközfelügyelet és az alkalmazásfelügyelet életciklusairól](introduction-device-app-lifecycles.md).

## <a name="mdm-vs-mam-capability-comparison"></a>Az MDM és a MAM képességeinek összehasonlítása
Mint már említettük, feltételes hozzáféréssel ösztönözheti a a felhasználót, hogy regisztrálják eszközüket, vagy egy felügyelt alkalmazást, például az Outlook Mobile használja. Számos más feltételt is alkalmazhat mindkét esetben, például:

* Melyik felhasználó kísérli meg a hozzáférést
* Megbízható-e a tartózkodási hely vagy sem
* Bejelentkezés kockázati szintje
* Eszközplatform

Sok cégnek megvannak azonban a saját, specifikus kockázataik.  Az alábbi táblázatban áttekintheti a gyakori problémákat, és hogy az MDM, illetve a MAM milyen választ ad az adott problémára.

| Probléma   |   MDM  |   MAM  |
|------------|--------|--------|
|Jogosulatlan adathozzáférés | Csoporttagság megkövetelése | Csoporttagság megkövetelése |
|Jogosulatlan adathozzáférés | Eszközbeléptetés megkövetelése | Védett alkalmazás megkövetelése |
|Jogosulatlan adathozzáférés | Meghatározott tartózkodási hely megkövetelése | Meghatározott tartózkodási hely megkövetelése |
| | | |
|Feltört felhasználói fiók| MFA megkövetelése | MFA megkövetelése|
|Feltört felhasználói fiók | Magas kockázatú felhasználók blokkolása | Magas kockázatú felhasználók blokkolása |
|Feltört felhasználói fiók | PIN-kód az eszközhöz | PIN-kód az alkalmazáshoz |
| | | |
| Feltört eszköz vagy alkalmazás | Szabályzatnak megfelelő eszköz megkövetelése | Jailbreak ellenőrzése alkalmazásindításkor |
| Feltört eszköz vagy alkalmazás | Eszközadatok titkosítása | Alkalmazásadatok titkosítása |
| | | |
|Elveszett vagy ellopott eszköz | Összes eszközadat eltávolítása | Összes alkalmazásadat eltávolítása|
| | | |
| Véletlen adatmegosztás vagy mentés nem biztonságos helyre | Eszközadatok biztonsági mentésének korlátozása | Kivágás/másolás/beillesztés korlátozása|
| Véletlen adatmegosztás vagy mentés nem biztonságos helyre | Mentés másként funkció korlátozása | Mentés másként funkció korlátozása |
|Véletlen adatmegosztás vagy mentés nem biztonságos helyre | Nyomtatás letiltása | n/a|

## <a name="next-steps"></a>További lépések
A fentiek alapján eldöntheti, hogy az eszközfelügyeletre, az alkalmazásfelügyeletre, vagy pedig a kettő kombinációjára összpontosítva engedélyezi a hozott eszközöket a cégében. A kívánt implementációt önállóan meghatározhatja, és biztos lehet abban, hogy bárhogyan is dönt, az Azure AD-ban elérhetők lesznek a megfelelő identitás- és biztonsági szolgáltatások.  

A tervezés következő fázisához használja az Intune [Tervezési útmutatóját](planning-guide.md).

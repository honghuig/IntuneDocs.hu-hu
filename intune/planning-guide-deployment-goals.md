---
title: Telepítési célok, célkitűzések és kihívások meghatározása
titleSuffix: Microsoft Intune
description: Ez a cikk segítséget nyújt a Microsoft Intune csak felhőalapú megvalósításához kapcsolódó telepítési célok, célkitűzések és kihívások meghatározásában.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 24cf9d97-db39-4b95-a664-4aa2e33edb87
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9d1cbfb7062dd897442d842a0b50b03a95a57a24
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/03/2019
ms.locfileid: "67549328"
---
# <a name="determine-deployment-goals-objectives-and-challenges"></a>Üzembe helyezési célok, célkitűzések és kihívások meghatározása

A jó telepítési tervhez legelőször is meg kell határozni munkahelye telepítési céljait, célkitűzéseit, valamint a lehetséges kihívásokat. Az alábbiakban mindegyik kérdést részletesen is megtárgyaljuk.

## <a name="deployment-goals"></a>Üzembe helyezés céljai

Az üzembe helyezési célok azok a hosszútávú eredmények, amelyeket az Intune vállalatnál történő üzembe helyezésével el szeretne érni. Az alábbi felsorolásban ezekre a célokra találhatók példák a leírásukkal és az üzleti értékükkel együtt.

- **Integráció az Office 365-tel és az Office-mobilalkalmazások támogatása**

    - **Leírás:** Szoros integráció biztosítása az Office 365 és az Office-mobilalkalmazások alkalmazásvédelemmel használatát.

    - **Üzleti érték:** Biztonságos és jobb felhasználói élmény azáltal, hogy felhasználók számára, ismerik és kedvelt alkalmazások használatát.

- **Belső céges szolgáltatásokhoz való hozzáférés engedélyezése mobileszközökön**

    - **Leírás:** Engedélyezze az alkalmazottak hatékonyan dolgozzanak, bárhol is szükségük van, és az eszközökön a számukra leginkább megfelelő működéséhez. Ez magába foglalja a mobileszközökről végzett hatékony munkát, valamint a céges adatokhoz való biztonságos hozzáférést.

    - **Üzleti érték:** Az üzleti agilisak lehetnek és a egy versenyképesebbé munkakörnyezet munkavállalók bárhonnan tudnak dolgozni lehetővé teszi.

- **Adatvédelem biztosítása a mobileszközökön**

    - **Leírás:** Ha az adatokat mobileszközökön tárolják, ott meg kell védeni azokat a rosszindulatú vagy véletlenszerű elvesztésektől vagy megosztásoktól.

    - **Üzleti érték:** Adatok védelme létfontosságú győződjön meg arról, hogy versenyképesek maradjunk, és, hogy azt az a saját és ügyfeleink adatait a lehető legkörültekintőbben kezeljük.

- **Költségcsökkentés**

    - **Leírás:** Ha lehetséges, csökkenti a projektet, telepítési és működtetési költségeket.

    - **Üzleti érték:** Az erőforrások hatékony használatát lehetővé teszi, hogy a vállalkozás más területeken fektet, hatékonyabban versenyezhet, és jobb szolgáltatásokat nyújthat az ügyfeleknek.

## <a name="deployment-objectives"></a>Üzembe helyezés feladatai

Az üzembe helyezés feladatai olyan műveletek, amelyekkel az adott munkahely elérheti az Intune üzembe helyezési céljait. Az alábbiakban néhány példa következik az üzembe helyezési feladatokra, valamint azok megvalósítására.

- **Az eszközkezelési megoldások számának csökkentése**

    - **Végrehajtás:** Összevonása egyetlen mobileszköz-felügyeleti megoldásra: A Microsoft Intune a céges adatok védelme az alkalmazások és eszközök számára.

- **Biztosítson az Exchange-hez és a SharePoint Online-hoz biztonságos hozzáférést**

    - **Végrehajtás:** Alkalmazza a feltételes hozzáférés az Exchange és SharePoint Online.

- **Ne engedje, hogy a céges adatok a mobileszköz nem céges szolgáltatásain kerüljenek tárolásra vagy továbbításra**

    - **Végrehajtás:** A Microsoft Office és az üzletági alkalmazások az Intune alkalmazásvédelmi szabályzatok alkalmazhatók.

- **Biztosítsa a céges adatok törlésének képességét az eszközről**

    - **Végrehajtás:** Eszközök regisztrálása az Intune-ban. Ez lehetővé teszi a vállalati adatok és erőforrások törlését a távolból, ha szükséges.

## <a name="deployment-challenges"></a>Üzembe helyezés kihívásai

Az üzembe helyezés kihívásai kiemelt fontossággal bírnak a cégek életében, és előfordulhat, hogy negatív hatást gyakorolhatnak magára a telepítésre. Olykor ezek régi projekteknél fellépő múltbéli problémákkal kapcsolatosak, amelyeket szeretne elkerülni, vagy pedig a jelenlegi üzembe helyezéskor felmerülő újakkal. Az alábbi listában néhány példa található az Intune üzembe helyezési kihívásaira és lehetséges kezelésükre.

- A kezdeti projekt nem terjed ki a támogatásra és a végfelhasználói élményre. Ez gyenge végfelhasználói adaptációhoz és a támogatás szervezésében jelentkező kihívásokhoz vezet.

    - **Megoldás:** A támogatási képzéseket foglalják magukban. A végfelhasználói tapasztalat érvényesítése az üzembe helyezési terv sikerességi metrikáival.

- A világosan meghatározott célok és sikerkritériumok metrikáinak hiánya miatt nincsenek kézzelfogható eredmények. Emiatt problémák jelentkezésekor a cég reaktív üzemmódba válthat.

    - **Megoldás:** A célok és sikerkritériumok metrikáinak korai szakaszában definiálja a projekt hatókörének, és ki a bevezetési fázisai hús ezeket az adatpontokat használatával. Győződjön meg róla, hogy SMART céljai vannak (Specific, Measurable, Attainable, Realistic, and Timely – meghatározottak, mérhetőek, elérhetőek, reálisok és időbeliek). Tervezze meg céljai mérését minden fázisban, hogy bevezetési projektjei biztosan a megfelelő irányba haladjanak.

- Elmulasztotta a cég értékeivel összhangban álló, világos értékjavaslat létrehozását, érvényesítését és agresszív megosztását. Ez gyakran korlátozott adaptációhoz és befektetésmegtérüléshez (ROI) vezet.

    - **Megoldás:** Bár bizonyára Izgatottan várja, hogy belevágjon a projektbe, győződjön meg arról, hogy egyértelműen meghatározott a céljait és törekvéseit. Ezeket foglalja bele valamennyi tájékoztatási és képzési tevékenységbe, hogy a felhasználók tisztában legyenek azzal, miért választotta a szervezet az Intune-t.

## <a name="next-steps"></a>További lépések

Most, hogy azonosította a telepítési célok, célkitűzések és a lehetséges kihívásokat, áttérhet a következő szakaszban: [Használati esetek azonosítása](planning-guide-scenarios.md).

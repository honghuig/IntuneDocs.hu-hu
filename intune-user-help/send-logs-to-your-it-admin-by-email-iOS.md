---
title: "iOS-es naplók küldése a Microsoft fejlesztőinek | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 733a590e-836f-4941-bfd9-6ae53ba25e06
searchScope:
- User help
ROBOTS: 
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: 1ba0dab35e0da6cfe744314a4935221a206fcea7
ms.openlocfilehash: 4abb070d6cf4f8200bdf1b9380ade7db81535622
ms.lasthandoff: 03/13/2017


---

# <a name="send-logs-to-the-company-portal-developers-for-ios-devices"></a>Naplók küldése a Céges portál fejlesztőinek iOS-es eszközök esetén

Egyes esetekben a Céges portál alkalmazás váratlanul kiléphet. Ez egy olyan probléma, amelyről az alkalmazás fejlesztői mindenképpen tudni szeretnének, mivel a visszajelzés segít az alkalmazás továbbfejlesztésében és a jövőbeni hasonló problémák megelőzésében. Az információk egy speciális dokumentumban, egy úgynevezett _diagnosztikai naplófájlban_ találhatók az eszközön.

Ha a hibát Ön is tapasztalja, a Céges portál fejlesztőinek további információra van szükségük a hiba reprodukálásához és a probléma okának felderítéséhez. A szükséges lépések az alábbiak:

1.    Kísérelje meg a hiba reprodukálását. Nem baj, ha nem sikerül, de ha igen, a következő lépés egyszerűbb lehet.
2.    Válassza a __Beállítások__ > __Adatvédelem__ > __Diagnosztika és használat__ > __Diagnosztika és használati adatok__ menüpontot. Ez a lista tartalmazza az alkalmazáshoz tartozó lezajlott tevékenységeket az összeomlásoktól kezdve az általános használati mintákig. Az adatok nem tartalmaznak személyes információkat. A rendszer a listát a legutóbbi tevékenységektől a legrégebbi tevékenységekig rendezi. Ha sikerült reprodukálnia a hibát, az az alkalmazáshoz tartozó tevékenységlista első elemeként jelenik meg a lapon. Ha nem sikerült reprodukálnia a hibát, görgessen le addig, amíg nem talál egy olyan elemet, amely a „Company Portal” („céges portál”) kifejezéssel kezdődik. Koppintson erre az elemre a megnyitáshoz.
3.    Tartsa lenyomva és húzza lefelé vagy felfelé a kis kék pontokat a jelentés teljes szövegének kijelöléséhez. Koppintson a __Másolás__ elemre az előugró menüben.
4.    Indítsa el a levelezőprogramot, majd másolja be a tartalmat az e-mail törzsébe. Küldje el az e-mailt az <a href="mailto:IntuneCPiOSfeedback@microsoft.com?subject=My Company Portal App Closed Unexpectedly&body=Press and hold, then paste your copied Company Portal app logs here.">IntuneCPiOSfeedback@microsoft.com</a> címre.

További segítségre van szüksége? Forduljon a rendszergazdához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](http://portal.manage.microsoft.com).

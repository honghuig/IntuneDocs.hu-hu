---
title: "Az eszközmegfelelőség figyelése"
titleSuffix: Intune Azure preview
description: "Azure-beli Intune – előzetes: Útmutató az eszközök megfelelőségének figyeléséhez."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: e073ca318d7db23239fc68b79718198dbee54b6e
ms.contentlocale: hu-hu
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-monitor-device-compliance-in-intune-azure-preview"></a>Eszközmegfelelőség figyelése az Azure-beli Intune előzetes verziójában

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

A **megfelelőségi profilok** állapotának összegzését az **Áttekintés** panelen tekintheti meg.
A diagramokon keresztüli interaktív átkattintással feltárhatja a részleteket. Ha több megfelelőségi profil is van konfigurálva, megtekintheti az egyes szabályzatok állapotát, ha a szabályzat panelen a **Jelentések** elemet választja a **Felügyelet** szakaszban.  Az előzetes verzióban elérhető jelentések részletei az alábbiakban láthatók.

##  <a name="device-compliance"></a>Eszközmegfelelőség

Az eszközmegfelelőségi jelentés összesített nézete az alábbi állapotok valamelyikét jelentő eszközök számára vonatkozó összesített adatok megjelenítésével kezdődik:

- **Megfelelő**: Az eszköz megfelelőségének kiértékelésére nemrég került sor, és a megadott megfelelőségiprofil-beállításoknak megfelelőként került meghatározásra.
- **Nem megfelelő**: Az eszköz kiértékelése megtörtént, és nem megfelelőként került meghatározásra.  Ha a profilban meg volt adva türelmi időszak, az lejárt, és az eszköz nem megfelelő állapotba került.
- **Türelmi időszak**: Az eszköz kiértékelése megtörtént, és nem megfelelőként került meghatározásra. A türelmi időszak azonban továbbra is érvényben marad, amíg az eszköz ténylegesen nem megfelelőként lesz megjelölve.

Az egyes eszközök és a felhasználók további adatainak megtekintéséhez megjelenítheti az egyes szakaszok részleteit.

## <a name="setting-compliance"></a>Beállítás-megfelelőség

A beállítás-megfelelőségi jelentés részletesen megjeleníti az egyes megfelelőségi beállítások adatait, például:

- A beállításnak nem megfelelő eszközök számát.
- A platformot, amelyre a beállítás vonatkozik.

Az egyes beállítások részletezésével további információkat jeleníthet meg azokról a profilokról, amelyeken engedélyezve vannak ezek a beállítások, illetve megtekintheti a beállítás értékét.

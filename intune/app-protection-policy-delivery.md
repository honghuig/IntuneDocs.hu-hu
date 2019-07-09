---
title: Undertastand alkalmazáselérés védelmi házirend és időzítése
titleSuffix: Microsoft Intune
description: Ismerje meg, hogy a különböző telepítési windows értenie, amikor a módosítások meg kell jelennie a végfelhasználói eszközökön az alkalmazásvédelmi szabályzatok.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ec111319-7e02-434f-946b-88647726bf1a
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 14b4af7145e09e1af3d2a6d3a2fd3ef17319be35
ms.sourcegitcommit: 1b7ee2164ac9490df4efa83c5479344622c181b5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/08/2019
ms.locfileid: "67649002"
---
# <a name="understand-app-protection-policy-delivery-timing"></a>Alkalmazásvédelmi szabályzat kézbesítési ütemezését ismertetése

Ismerje meg, hogy a különböző telepítési windows értenie, amikor a módosításokat a végfelhasználók eszközein található meg kell jelennie az alkalmazásvédelmi szabályzatok.

## <a name="delivery-timing-summary"></a>Kézbesítési ütemezését összegzése

Alkalmazásvédelmi szabályzat alkalmazásszolgáltatást attól függ, a licenc állapota és az Intune szolgáltatás regisztrálását a felhasználók számára.  

|    Felhasználói állapot    |    Alkalmazásvédelmi     |    Újrapróbálkozási időköz (lásd a megjegyzést)    |    Miért jelentkezik?    |
|-----------------------------------------------------|-------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
|    A bérlői nincs előkészítve    |    Várja meg a következő újrapróbálkozási időszak.  Alkalmazásvédelem nem lesz aktív, a felhasználó számára.    |    24 óra    |    Akkor következik be, ha nincs beállítva az Intune-bérlő.    |
|    A felhasználó nem rendelkezik licenccel     |    Várja meg a következő újrapróbálkozási időszak.  Alkalmazásvédelem nem lesz aktív, a felhasználó számára.     |    12 óra – azonban Androidos eszközökön ez az időtartam alatt igényel az Intune APP SDK-val 5.6.0-s vagy újabb. Egyéb támogatni eszközök, az időköz 24 óra.   |    Akkor következik be, amikor a felhasználó rendelkezik nem jogosult, az Intune-ban.    |
|    Az alkalmazásvédelmi szabályzatok nem hozzárendelt felhasználó    |    Várja meg a következő újrapróbálkozási időszak.  Alkalmazásvédelem nem lesz aktív, a felhasználó számára.    |    12 óra        |    Akkor következik be, amikor a felhasználó nem hozzárendelt alkalmazás beállításait.    |
|    A felhasználó sikeresen regisztrált az Intune MAM    |    Alkalmazásvédelmi szabályzat-beállítások szerint alkalmazza.    Frissítések alapján történik az újrapróbálkozási időköz    |    Az Intune szolgáltatás definiált felhasználói terhelés alapján.    Általában 30 perc.     |    Akkor következik be, amikor a felhasználó sikeresen regisztrálta az Intune szolgáltatással a MAM-konfiguráció.    |

> [!NOTE]
> Újrapróbálkozási időközök előfordulhat, hogy megkövetelése alkalmazás aktív használatával történik, ami azt jelenti, az alkalmazást elindítja, és használja.  Ha az újrapróbálkozási időköznek 24 órában, és a felhasználó vár, 48 óra múlva indítsa el az alkalmazást, az alkalmazás-Protection-ügyfél újra megpróbálja 48 óra.

## <a name="handling-network-connectivity-issues"></a>Hálózati kapcsolati hibák kezelése

Ha a felhasználói regisztráció hálózati kapcsolódási problémák miatt nem sikerül egy gyorsított újrapróbálkozási időköz szolgál.  Az alkalmazás-Protection-ügyfél egyre hosszabb időközönként próbálkozik, amíg az időköz eléri 60 perc, vagy a sikeres csatlakozást követően.  Az ügyfél ezután mindaddig, amíg a sikeres csatlakozást követően 60 perces időközönként újra fog próbálkozni. Az ügyfél ezután visszatér a szokásos újrapróbálkozási időköz a felhasználói állapot alapján.

## <a name="next-steps"></a>További lépések

[Licencek hozzárendelése a felhasználókhoz, hogy regisztrálhassák az eszközöket az Intune-ban](licenses-assign.md)


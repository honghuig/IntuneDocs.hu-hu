---
title: "Az alkalmazásvédelmi szabályzatok ellenőrzése"
titleSuffix: Intune Azure preview
description: "Intune az Azure-on – előzetes: Ez a témakör azt ismerteti, hogyan tesztelheti és ellenőrizheti, hogy az alkalmazásvédelmi szabályzat konfigurációja és működése megfelelő-e."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angerobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 26e191965eff482cf97b920e028cdf60d1881d32
ms.contentlocale: hu-hu
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-validate-your-app-protection-policy-setup"></a>Az alkalmazásvédelmi szabályzatok konfigurációjának ellenőrzése

[!INCLUDE[azure_preview](./includes/azure_preview.md)]


Ez a témakör azon problémák ellenőrzésével kapcsolatban nyújt tájékoztatást, amelyek az alkalmazásvédelmi szabályzatok konfigurációját követően merülhetnek fel. Az útmutató az Azure-portál **előzetes verziójában** található alkalmazásvédelmi szabályzatokra vonatkozik.

### <a name="checking-for-symptoms"></a>Hibajelenségek keresése
Mivel az alkalmazásvédelem egy adatvédelmi eszköz, nem valószínű, hogy a felhasználók jeleznek problémákat. Alkalmazásvédelmi konfigurációs problémák esetén a felhasználó ugyanolyan korlátlan hozzáféréssel rendelkezik, mint az alkalmazásvédelem nélkül, így nem veszi észre a problémát. Éppen ezért azt javasoljuk, hogy alkalmazásvédelmi konfigurációját úgy ellenőrizze, hogy az alkalmazásvédelmi szabályzatokat olyan felhasználók kis csoportján teszteli, akik képesek szándékosan tesztelni az alkalmazásvédelmi korlátozásokat.


### <a name="what-to-check"></a>Mit kell ellenőrizni?

Ha a tesztelés azt mutatja, hogy az alkalmazásvédelmi szabályzat nem az elvárt módon működik, akkor javasoljuk, hogy ellenőrizze az alábbiakat:

- A felhasználók rendelkeznek alkalmazásvédelmi licenccel?
- A felhasználók rendelkeznek O365-licenccel?
- Az egyes felhasználók alkalmazásvédelmi alkalmazásainak állapota. Az alkalmazások lehetséges állapotai: **Bejelentkezett** és **Nem bejelentkezett**.

#### <a name="user-app-protection-status"></a>A felhasználók alkalmazásvédelmi állapota
1. Az Azure-portálon válassza az **Alkalmazások kezelése** > **Figyelés** >  **App protection user status** (Alkalmazásvédelmi felhasználói állapot) > **felhasználók** lehetőséget.

2. A listából válasszon ki egy felhasználót, vagy keressen rá valamelyik felhasználóra, majd válassza a **Felhasználó kiválasztása** lehetőséget. Az **Alkalmazásjelentések** oszlop tetején fog megjelenni, hogy a felhasználó rendelkezik-e alkalmazásvédelmi licenccel. Ez alatt látható, hogy a felhasználó rendelkezik-e O365-licenccel, és itt jelenik meg az alkalmazás állapota a felhasználó összes eszközére vonatkozóan.



### <a name="what-to-do"></a>Mi a teendő
A felhasználói állapotnak megfelelően az alábbi műveleteket hajthatja végre:

- Ha a felhasználó nem rendelkezik alkalmazásvédelmi licenccel, rendeljen Intune-licencet a felhasználóhoz.
- Ha a felhasználó nem rendelkezik O365-licenccel, szerezzen be számára egy licencet.
- Ha a felhasználó alkalmazása **Nincs bejelentkezve** állapottal jelenik meg a listában, ellenőrizze, hogy megfelelően állította-e be az adatvédelmi szabályzatot az adott alkalmazáshoz.
- Győződjön meg róla, hogy ezek a feltételek érvényesek minden olyan felhasználóra, akit be kíván vonni az adatvédelmi szabályzatok hatálya alá.

### <a name="see-also"></a>További információ

[Mi az Intune alkalmazásvédelmi szabályzata?](app-protection-policies.md)

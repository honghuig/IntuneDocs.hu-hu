---
title: Az iOS-szoftverfrissítési szabályzatok konfigurálása az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Konfigurációs szabályzat létrehozása vagy felvétele a Microsoft Intune-ban, amellyel korlátozhatja, mikor kerüljenek automatikusan telepítésre az Intune által felügyelt, vagy ellenőrzött iOS-eszközök szoftverfrissítései. Megadhatja azokat a dátumokat és időpontokat, amelyeknél nem szeretné, hogy települjenek a frissítések. Ezt a szabályzatot csoportokhoz, felhasználókhoz és eszközökhöz is hozzárendelheti, és ellenőrizheti az esetleges telepítési hibákat is vele.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5a5c9dea847ace51c7d6f06cfa43c44beead18f8
ms.sourcegitcommit: 78ae22b1a7cb221648fc7346db751269d9c898b1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66373419"
---
# <a name="add-ios-software-update-policies-in-intune"></a>IOS-szoftverfrissítési szabályzatok hozzáadása az Intune-ban

A-frissítési szabályzatokkal kikényszerítheti a legújabb elérhető rendszerfrissítések automatikus telepítését a felügyelt iOS-eszközökön. A szabályzat beállításakor megadhatja azokat a napokat és időpontokat, amikor nem szeretné, hogy az eszközök frissítéseket telepítsenek. 

Ez a funkció az alábbiakra vonatkozik:

- iOS 10.3 vagy újabb (csak felügyelt eszköz)

Az eszköz körülbelül 8 óránként jelentkezik be az Intune-ba. Ha az eszköz elérhető frissítést talál a megadott korlátozott időszakokon kívül, akkor letölti és telepíti a legújabb rendszerfrissítéseket. Az eszköz frissítéséhez nincs szükség felhasználói beavatkozásra. A szabályzat nem akadályozza meg, hogy a felhasználó manuálisan frissítse az operációs rendszert.

## <a name="configure-the-policy"></a>A szabályzat konfigurálása

1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Válassza a **Szoftverfrissítések** > **iOS-frissítési szabályzatok** > **Létrehozás** lehetőséget.
3. Adja meg a következő beállításokat:

    - **Név**: Adja meg a szoftver frissítések házirend nevét. Például írja be a következőt: `iOS restricted update times`.
    - **Description** (Leírás): Adja meg a házirend leírását. A beállítás használata nem kötelező, de ajánlott.

4. Válassza ki **beállítások > konfigurálása**. Adja meg a következő beállításokat:

    - **Válassza ki a frissítések telepítésének elkerüléséhez alkalommal**: Adjon meg egy korlátozott időkeret, amikor nem kényszerített telepíti a frissítéseket. 
      - Egynapos blokkok nem támogatottak, és nem fognak működni. Például ne konfigurálja a szabályzat egy *kezdési idő* du. 8- és a egy *befejezési idő* , reggel 6 óra.
      - Egy szabályzatot, amely 12 AM-nél kezdődik és ér véget, Éjfélkor lesz kiértékelve, mint 0 óra és a nem a 24 órát, aminek eredményeképpen nincs korlátozás.

      A korlátozott időtartamon beállításakor adja meg a következő adatokat:

      - **Nap**: Válassza ki a nap, hét, ha nincsenek telepítve a frissítések. Ellenőrizze például, hétfőn, szerdán és pénteken ahhoz, hogy ezek a napok való telepítése is.
      - **Időzóna**: Válasszon időzónát.
      - **Kezdési idő**: Válassza ki a korlátozott időkeret kezdési idejét. Adja meg például 05-kor, így a frissítések nincsenek telepítve, 05-kor kezdődik.
      - **Befejezési idő**: Válassza ki a korlátozott időkeret befejezési időpontja. Adja meg például 1 AM, így a frissítések telepíthetők, hogy 1 Órakor indítása.

    - **Látható-e a szoftverfrissítések a végfelhasználók számára nem változik az ütemezett frissítések késleltetése (nap)** : 

      **Ez a beállítás át [Eszközkorlátozások](device-restrictions-ios.md#general). Ezen a helyen, a portálon eltávolítjuk**. Egy rövid ideig a meglévő szabályzatok itt módosítható. Miután körülbelül egy hónap, ezzel a beállítással a meglévő szabályzatok törlődik.

      Szeretné korlátozni a hatás, a következőket javasoljuk:
        - Távolítsa el a meglévő szabályzat ezen a helyen, a portálon.
        - Hozzon létre egy új [eszközkorlátozási szabályzatot](device-restrictions-ios.md#general).
        - A céloznia ugyanazokat a felhasználókat, mint az eredeti házirenddel.

      Ütközés esetén ez a beállítás nem módosítja *, kivéve, ha* a két érték azonosak. Ütközés elkerülése érdekében ügyeljen arra, módosítsa vagy távolítsa el a meglévő szabályzatot erről a helyről a portálon.
      > [! [Fontos]  
      > Egy szabályzatot, amely rendelkezik egy *kezdési idő* és *befejezési idő* éjféltől set ki lesz értékelve, mint 0 óra, és nem 24 óra. Ennek eredményeképpen nincs korlátozás.  

5. Válassza ki **OK** > **létrehozás** a módosítások mentéséhez és a szabályzat létrehozásához.

A szabályzat létrejön, és megjelenik a szabályzatok listájában.

Az Intune támogatási csapat útmutatásért lásd: [látható-e a felügyelt eszközökön az Intune-ban szoftverfrissítéseket késleltetés](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753).

> [!NOTE]
> Az Apple mobileszköz-kezelése nem teszi lehetővé, hogy a készülékek számára kikényszerítse a frissítések adott időpontban történő telepítését.

## <a name="change-the-restricted-times-for-the-policy"></a>A korlátozott időtartamok módosítása a szabályzatban

1. A **Szoftverfrissítések** területen válassza **iOS-frissítési szabályzatok** lehetőséget.
2. Válasszon ki egy meglévő szabályzatot > **Tulajdonságok**.
3. Frissítse a korlátozás időpontjait:

    1. Válassza ki a hét napjait
    2. Válassza ki, hogy melyik időzóna szerint kívánja alkalmazni a szabályzatot
    3. Adja meg a feketelistás órák kezdő és záró idejét

    > [!NOTE]
    > Ha a **kezdési idő** és **befejezési idő** mindkét beállítás 12 óra, akkor az Intune nem ellenőrzi a korlátozások mikor telepítse a frissítéseket. Ez azt jelenti, hogy rendelkezik a konfigurációk, mint **válassza ki a frissítések telepítésének elkerüléséhez alkalommal** figyelmen kívül hagy, és a frissítések bármikor telepíthetik.  

## <a name="assign-the-policy-to-users"></a>A szabályzat hozzárendelése a felhasználókhoz

A meglévő szabályzatokat csoportokhoz, felhasználókhoz vagy eszközökhöz rendelheti. Hozzárendelés után a szabályzatok alkalmazásra fognak kerülni.

1. A **Szoftverfrissítések** területen válassza **iOS-frissítési szabályzatok** lehetőséget.
2. Válasszon ki egy meglévő szabályzatot > **Hozzárendelések**. 
3. Válassza ki azokat az Azure Active Directory csoportokat, felhasználókat vagy eszközöket, amelyeknél alkalmazni vagy kizárni szeretné a szabályzatot.
4. Válassza a **Mentés** lehetőséget a szabályzat csoportok felé történő telepítéséhez.

A rendszer ekkor kiértékeli a szabályzat hatókörébe tartozó felhasználók által használt eszközök frissítési megfelelőségét. Ez a szabályzat a felhasználó nélküli eszközöket is támogatja.

## <a name="monitor-device-installation-failures"></a>Eszközök telepítési hibáinak figyelése
<!-- 1352223 -->
**Szoftverfrissítések** > **iOS-eszközök telepítési hibái** felügyelt IOS-eszközök egy frissítési szabályzattal, frissítéssel próbálkoztak, és nem sikerült frissíteni a listáját jeleníti meg. Minden eszköz mellett látható egy állapotleírás, amelyből kiderül, hogy az adott eszköz miért nem frissült automatikusan. A kifogástalan, naprakész eszközök nem jelennek meg a listában. A naprakész eszközökön telepítve van az a legújabb frissítés, amelyet az eszköz támogatni képes.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).

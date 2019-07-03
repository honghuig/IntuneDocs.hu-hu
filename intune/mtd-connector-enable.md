---
title: A Mobile Threat Defense-összekötő engedélyezése a Microsoft Intune-ban
titleSuffix: Microsoft Intune
description: A Mobile Threat Defense (MTD) partner és a Microsoft Intune közötti összekötő engedélyezése.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 45bcafad3dc6c2a407e1b7b88e07f4021e8b5a36
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67528291"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>A Mobile Threat Defense-összekötő engedélyezése az Intune-ban

> [!NOTE] 
> Ez a témakör minden Mobile Threat Defense-partnerre vonatkozik.

A Mobile Threat Defense (MTD) beállítása során konfigurált egy, az MTD-partnerkonzolra vonatkozó fenyegetésosztályozási szabályzatot, és létrehozta az eszközmegfelelőségi szabályzatot az Intune-ban. Ha már konfigurálta az Intune-összekötőt az MTD-partnerkonzolon, engedélyezheti az MTD-kapcsolatot az Intune-ban.

## <a name="to-enable-the-mtd-connector"></a>Az MTD-összekötő engedélyezése

1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

4. Az **Intune-irányítópulton** válassza az **Eszközmegfelelőség**, majd a **Beállítás** szakaszban a **Mobile Threat Defense** elemet.

5. A **Mobile Threat Defense** panelen válassza a **Hozzáadás** elemet.

6. A legördülő listában jelölje ki a saját MTD-megoldását mint **Beállítani kívánt Mobile Threat Defense-összekötőt**.

    ![Az MTD beállítása az Azure-beli Intune-portálon](./media/enable-mtd-connector-1.png)

7. A szervezet igényeinek megfelelően adja meg a kapcsolós beállításokat. Az elérhető kapcsolós megoldások az MTD-partnertől függenek.

## <a name="mtd-toggle-options"></a>Az MTD kapcsolós megoldásai

A cég igényei alapján eldöntheti, hogy az MTD mely kapcsolós beállításait kell engedélyeznie. További részletek:

- **Csatlakozás Android 4.1 + eszközök az [MTD partner name] for Work MTD-hez**: Ha engedélyezi ezt a beállítást, az akkor Android 4.1 + rendszerű eszközök bejelenthetik a biztonsági kockázatokat az Intune-bA biztonsági másolatot.
    - **Nem megfelelőnek minősítés, ha nem érkezik adat**: Ha az Intune nem kap adatokat egy ilyen platformos eszközről az MTD-partnertől, fontolja meg az eszköz nem megfelelő.
<br></br>
- **Csatlakozás iOS 8.0 és újabb eszközökre az [MTD partner name] for Work MTD-hez**: Ha engedélyezi ezt a beállítást, akkor is iOS 8.0 + eszközök bejelenthetik a biztonsági kockázatokat vissza az Intune-hoz.
    - **Nem megfelelőnek minősítés, ha nem érkezik adat**: Ha az Intune nem kap adatokat egy ilyen platformos eszközről az MTD-partnertől, fontolja meg az eszköz nem megfelelő.
<br></br>
- **IOS eszközök Alkalmazásszinkronizálásának engedélyezése**: Lehetővé teszi, hogy a Mobile Threat Defense-partner threat elemzési célokra használja az Intune az iOS-alkalmazások metaadatait kérhet.

- **Nem támogatott operációsrendszer-verziók letiltása**: Annak letiltása, ha az eszköz operációs rendszer fut, kevesebb, mint a minimális támogatott verziója.

- **Ennyi nap múlva partner nem válaszol**: Ennyi nap inaktivitás után tekinti úgy a partner a kapcsolat megszakadása miatt nem válaszol az Intune. Az Intune nem veszi figyelembe a nem válaszoló MTD-partnerek megfelelőségi állapotát.

> [!IMPORTANT] 
> Ha lehetséges, javasoljuk, hogy adja hozzá, és az MTD-alkalmazások hozzárendelése az eszközmegfelelőségi és feltételes hozzáférési szabályzat szabályok létrehozása előtt. Ez segít biztosítja, hogy az MTD alkalmazást kész és elérhető legyen a végfelhasználók számára, mielőtt hozzáférhetnének a levelezéshez és más vállalati erőforrásokhoz való telepítéséhez.

> [!TIP]
> A Mobile Threat Defense panelen látható a **Kapcsolat állapota** és a **Legutóbb szinkronizálva**, mely utóbbi az Intune és az MTD-partner közötti szinkronizálásra vonatkozik.

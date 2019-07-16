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
ms.openlocfilehash: a2084ad1ec0deefd24c0d61f69d99ee11149af96
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882739"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>A Mobile Threat Defense-összekötő engedélyezése az Intune-ban

> [!NOTE] 
> Ez a témakör minden Mobile Threat Defense-partnerre vonatkozik.

A Mobile Threat Defense (MTD) beállítása során konfigurált egy, az MTD-partnerkonzolra vonatkozó fenyegetésosztályozási szabályzatot, és létrehozta az eszközmegfelelőségi szabályzatot az Intune-ban. Ha már konfigurálta az Intune-összekötőt az MTD-partnerkonzolon, engedélyezheti az MTD-kapcsolatot az Intune-ban.

## <a name="to-enable-the-mtd-connector"></a>Az MTD-összekötő engedélyezése

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.

4. Az **Intune-irányítópulton** válassza az **Eszközmegfelelőség**, majd a **Beállítás** szakaszban a **Mobile Threat Defense** elemet.

5. A **Mobile Threat Defense** panelen válassza a **Hozzáadás** elemet.

6. A legördülő listában jelölje ki a saját MTD-megoldását mint **Beállítani kívánt Mobile Threat Defense-összekötőt**.

    ![Az MTD beállítása az Azure-beli Intune-portálon](./media/enable-mtd-connector-1.png)

7. A szervezet igényeinek megfelelően adja meg a kapcsolós beállításokat. Az elérhető kapcsolós megoldások az MTD-partnertől függenek.

## <a name="mtd-toggle-options"></a>Az MTD kapcsolós megoldásai

A cég igényei alapján eldöntheti, hogy az MTD mely kapcsolós beállításait kell engedélyeznie. További részletek:

- **Android 4.1 + rendszerű eszközök csatlakoztatása a (z) [MTD-partner neve] for Work MTD**: Ha engedélyezi ezt a beállítást, az Android 4.1 + rendszerű eszközök bejelenthetik a biztonsági kockázatokat az Intune-nak.
  - **Nem megfelelőként való megjelölés, ha nem érkezik ilyen érték**: Ha az Intune nem kap információt a platformon található eszközről az MTD-partnertől, vegye figyelembe, hogy az eszköz nem megfelelő.
<br></br>
- **IOS 8.0 + rendszerű eszközök csatlakoztatása a (z) [MTD partner neve] for Work MTD**: Ha engedélyezi ezt a beállítást, az iOS 8.0 + rendszerű eszközök bejelenthetik a biztonsági kockázatokat az Intune-nak.
  - **Nem megfelelőként való megjelölés, ha nem érkezik ilyen érték**: Ha az Intune nem kap információt a platformon található eszközről az MTD-partnertől, vegye figyelembe, hogy az eszköz nem megfelelő.
<br></br>
- **Alkalmazások szinkronizálásának engedélyezése iOS**-eszközökhöz: Lehetővé teszi a Mobile Threat Defense-partner számára, hogy az Intune-ból származó iOS-alkalmazások metaadatait a veszélyforrások elemzése céljából használja.

- Nem **támogatott operációsrendszer-verziók letiltása**: Letiltja, ha az eszköz a minimális támogatott verziónál kisebb operációs rendszert futtat.

- **A partnernek nem válaszoló napok száma**: Ennyi nap inaktivitás után veszi figyelembe, hogy az Intune nem válaszol a partnernek, mert a kapcsolat megszakad. Az Intune nem veszi figyelembe a nem válaszoló MTD-partnerek megfelelőségi állapotát.

> [!IMPORTANT] 
> Ha lehetséges, javasoljuk, hogy az eszköz megfelelőségének és a feltételes hozzáférési szabályzat szabályainak létrehozása előtt vegye fel és rendelje hozzá a MTD-alkalmazásokat. Ez segít biztosítani, hogy a MTD alkalmazás készen álljon, és elérhető legyen a végfelhasználók számára az e-mailekhez vagy más vállalati erőforrásokhoz való hozzáféréshez.

> [!TIP]
> A Mobile Threat Defense panelen látható a **Kapcsolat állapota** és a **Legutóbb szinkronizálva**, mely utóbbi az Intune és az MTD-partner közötti szinkronizálásra vonatkozik.

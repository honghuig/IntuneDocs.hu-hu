---
title: Felhasználók és eszközök összekapcsolásának felügyelete Windows rendszerű számítógépekhez
titleSuffix: Microsoft Intune
description: Hogyan kapcsoljon össze egy felhasználót egy Intune felügyelte Windows rendszerű számítógéppel.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 53c99d63-c312-442a-8a71-de1b10fcd39b
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0eca9dfddbf9ea2c68cf58b1da64d9b046df7e77
ms.sourcegitcommit: bd09decb754a832574d7f7375bad0186a22a15ab
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68353637"
---
# <a name="manage-user-device-linking-for-windows-pcs"></a>Felhasználók és eszközök összekapcsolásának felügyelete Windows rendszerű számítógépekhez

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Az ebben a témakörben ismertetett információk csak az Intune-szoftverügyféllel PC-ként felügyelt Windows-számítógépekre vonatkoznak. 

Mielőtt szoftvereket telepítene egy felhasználónak, a felhasználót egy számítógéphez kell kapcsolni. Egy felhasználót több számítógéphez is kapcsolhat, de minden gép csak egyetlen felhasználóhoz kapcsolható. A felhasználókat a rendszer automatikusan összekapcsolja azokkal a számítógépekkel, amelyeket a céges portálon keresztül regisztráltak az Intune-ban.

További információ az eszköz elsődleges felhasználóról: [elsődleges felhasználó keresése](find-primary-user.md).

Felhasználók kapcsolása számítógépekhez:

1. A [Microsoft Intune felügyeleti konzolján](https://manage.microsoft.com/) válassza a **Csoportok** &gt; **Minden eszköz** elemet (vagy egy másik csoportot, amely tartalmazza azt a számítógépet, amelyet az adott felhasználóhoz szeretne kapcsolni).

2. Jelölje ki a felhasználóval összekapcsolni kívánt számítógépet, majd válassza a **Felhasználó csatolása** elemet.

   A **Felhasználó csatolása** párbeszédpanel megjeleníti az elérhető felhasználók listáját a megjelenített nevükkel, a felhasználói azonosítójukkal és azon számítógépek számával, amelyekhez az egyes felhasználók jelenleg kapcsolva vannak. Ha a kijelölt számítógéphez már van felhasználó kapcsolva, akkor annak a felhasználónak a neve és felhasználói azonosítója megjelenik az **Aktuális felhasználó** területen. Ha a számítógép nincs felhasználóhoz kapcsolva, akkor az **Aktuális felhasználó** területen a **Nincs felhasználó** felirat jelenik meg.

3. Tegye a következők valamelyikét:

   - Ha azt szeretné, hogy a számítógép továbbra is az aktuális felhasználóhoz legyen kapcsolva (ha van ilyen), válassza a **Mégse** lehetőséget.

   - Ha el szeretné távolítani az aktuális felhasználóra mutató hivatkozást, ha van ilyen, válassza a <strong> **&gt;** kapcsolat eltávolítása ok</strong>lehetőséget.

   - Ha a számítógépet egy új felhasználóhoz szeretné kapcsolni, válasszon ki egy felhasználót a **Minden felhasználó** listában. Erősítse meg, hogy a felhasználói adatok helyesek, majd kattintson az **OK** gombra.

> [!TIP]
> Ha korlátozni szeretné végfelhasználókat abban, hogy önmagukat számítógépekkel kapcsolják össze, engedélyezze **A felhasználók korlátozása abban, hogy önmagukat számítógépekhez csatolhassák** beállítást a **Microsoft Intune-ügynök beállításai** szabályzatban.

## <a name="see-also"></a>Lásd még:

[A Windows rendszerű számítógépek Intune-szoftverügyféllel való felügyeletének általános feladatai](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)

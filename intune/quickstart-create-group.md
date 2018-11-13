---
title: Rövid útmutató – Csoport létrehozása felhasználók kezeléséhez
titlesuffix: Microsoft Intune
description: Ebben a rövid útmutatóban a Microsoft Intune használatával fog csoportot létrehozni meglévő felhasználók alapján.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/21/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2b52265bb9b3df800c0e13450a2154e46098a933
ms.sourcegitcommit: 9d08545727543b434dd270371fa50233470f2bce
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50410820"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>Rövid útmutató: Csoport létrehozása felhasználók kezeléséhez

Ebben a rövid útmutatóban az Intune használatával fog csoportot létrehozni egy meglévő felhasználó alapján. Csoportokkal kezelheti a felhasználókat, és ellenőrzés alatt tarthatja, hogy a felhasználók milyen céges erőforrásokat érhetnek el. Ezek lehetnek a vállalati intranet részei, vagy olyan külső erőforrások, mint a SharePoint-webhelyek, SaaS-alkalmazások vagy webalkalmazások.

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon egy ingyenes próbafiókkal](free-trial-sign-up.md).

>[!NOTE]
>Az Intune biztosítja az előre létrehozott **Minden felhasználó** és **Minden eszköz** csoportok beépített optimalizálását a felhasználók kényelme érdekében a konzolon.

## <a name="prerequisites"></a>Előfeltételek

- Ennek a rövid útmutatónak a követéséhez [létre kell hoznia egy felhasználót](quickstart-create-user.md).

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba

Jelentkezzen be az [Intune-ba](https://aka.ms/intuneportal) [globális rendszergazdaként vagy Intune-szolgáltatásadminisztrátorként](users-add.md#types-of-administrators). Ha létrehozott egy Intune próba-előfizetést, az a fiók lesz a globális rendszergazda, amelyikkel létrehozta azt.

## <a name="create-a-group"></a>Csoport létrehozása

Létre fog hozni egy csoportot, amelyet a későbbiekben fog használni ebben a rövid útmutatóban.

1. Miután megnyitotta a **Microsoft Intune** panelt, válassza a **Csoportok** > **Új csoport** lehetőséget.
2. A **Csoporttípus** legördülő listában válassza a **Biztonság** elemet.
3. A **Név** tulajdonságot állítsa be „Contoso tesztelők” értékre, és adjon meg **Leírást** a csoporthoz.
4. Adja meg a **Tagság típusa** elemhez a **Hozzárendelt** beállítást. 
5. Kattintson a **Tagok** lehetőségre, majd válasszon egy vagy több tagot a csoporthoz a meglévő listából.

    ![Képernyőkép egy csoport létrehozásáról a Microsoft Intune-ban](./media/quickstart-use-groups-01.png)

6. Kattintson a **Kiválasztás** > **Létrehozás** elemre.

Miután sikeresen létrehozta a csoportot, az megjelenik az **Összes csoport** listájában. 

## <a name="next-steps"></a>További lépések

Ebben a rövid útmutatóban az Intune használatával hozott létre csoportot egy meglévő felhasználó alapján.

> [!div class="nextstepaction"]
> [Eszközmegfelelőségi szabályzat létrehozása](quickstart-create-policy.md)
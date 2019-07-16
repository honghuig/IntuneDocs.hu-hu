---
title: Windows 10-es oktatási beállítások a Microsoft Intune-ban – Azure | Microsoft Docs
description: Tekintse meg a Windows 10-es eszközökre vonatkozó oktatási beállítások listáját. Ezeket a beállításokat egy eszköz konfigurációs profiljában használhatja a teszt alkalmazással, kiválaszthatja, hogy a felhasználók vagy tanulók hogyan jelentkeznek be, figyelheti a képernyőt a teszt során, és többet az Intune-ban.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d5c78f72e7ffc580cce6cfec7237a3efe3ceb3e5
ms.sourcegitcommit: fd2499df5123758ecb093b4cdd486e35f713b040
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68230101"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>A tesztelési alkalmazás konfigurálása Windows 10-es eszközökön az Intune használatával

Ebből a cikkből megtudhatja, hogy a Microsoft Intune Education hogyan végezheti el a Windows 10 és újabb rendszerű eszközökön konfigurálható tesztelési alkalmazások beállításait. Az alkalmazás használatával a tanulók bejelentkezhetnek egy eszközre, és tesztet végezhetnek.

Ezeket a beállításokat egy eszköz konfigurációs profiljához adja hozzá, majd Microsoft Intune használatával rendeli hozzá vagy helyezi üzembe az eszközökön.

A szolgáltatással kapcsolatos további információkért tekintse meg a [tesztelési alkalmazást az Intune-ban](education-settings-configure.md) .

## <a name="before-you-begin"></a>Előkészületek

[Eszközkonfigurációs profil létrehozása](education-settings-configure.md#create-a-device-profile).

## <a name="take-a-test-settings"></a>Tesztelési beállítások  

- **Fiók típusa**: Válassza ki, hogy a felhasználók hogyan jelentkezzenek be a tesztbe. A választható lehetőségek:
  - Azure AD-fiók
  - Tartományi fiók
  - Helyi fiók
- **Fiók felhasználóneve**: Adja meg annak a fióknak a felhasználónevét, amelyet a Take a test alkalmazással használ. A fiókokat a következő formátumban adhatja meg:
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **Assessment URL-címe**: Adja meg annak a tesztnek az URL-címét, amelyet el szeretne végezni a felhasználók számára. Az URL-cím beszerzésével kapcsolatos további információkért tekintse meg a [teszt dokumentációját](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).
- **Képernyő figyelése**: Válassza az **Engedélyezés lehetőséget** a képernyő tevékenység monitorozásához, miközben a felhasználók tesztet vesznek. A **nincs konfigurálva beállítás** megakadályozza a képernyő figyelését a teszt során.
- **Szöveges javaslat**: Válassza az **Engedélyezés lehetőséget** , hogy a teszt elfogadók megjelenjenek a szöveges javaslatok. **Nincs konfigurálva** a szöveges javaslatok blokkolása a felhasználók számára.

## <a name="next-steps"></a>További lépések

A profil létrehozása megtörtént, de előfordulhat, hogy még nem csinál semmit. Ügyeljen arra, hogy [hozzárendelje a profilt](device-profile-assign.md), és [Figyelje annak állapotát](device-profile-monitor.md).

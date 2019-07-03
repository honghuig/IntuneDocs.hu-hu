---
title: Egyéni beállítások hozzáadása macOS-eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
titleSuffix: ''
description: Exportálhat macOS-beállításokat az Apple Configuratorből vagy az Apple Profile Managerből, majd a Microsoft Intune-ba importálhatja őket. Ezek a beállítások létrehozását, használatát és egyéni beállításainak és funkcióinak macOS-eszközökön. Ez az egyéni profil ezután hozzárendelhető vagy kiosztható a cég vagy szervezet macOS-eszközei számára egy kiindulási alap vagy szabvány létrehozása érdekében.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04671df820fee96d4090b13f6fa8f6c4f983a1ac
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67530229"
---
# <a name="use-custom-settings-for-macos-devices-in-microsoft-intune"></a>macOS-eszközökre vonatkozó egyéni beállítások használata a Microsoft Intune-ban

A Microsoft Intune-nal egyéni beállításokat adhat hozzá vagy hozhat létre a macOS-eszközökhöz „egyéni profilok” használatával. Az egyéni profilok az Intune részét képezik. Akkor hasznosak, ha olyan eszközbeállításokat és funkciókat szeretne használni, amelyek nem érhetők el beépítetten az Intune-ban.

macOS-eszközök használatakor az alábbi két megoldással lehet egyéni beállításokat juttatni az Intune-ba:

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Apple Profile Manager](https://support.apple.com/profile-manager)

Ezekkel az eszközökkel exportálhatja a beállításokat egy konfigurációs profilba. Az Intune-ban importálja ezt a fájlt, majd hozzárendeli a profilt a macOS-felhasználókhoz és -eszközökhöz. A hozzárendelés után a beállítások ki lesznek osztva, és létrehoznak egy macOS-eszközökre vonatkozó kiindulási alapot vagy szabványt a cégen vagy szervezeten belül.

Ebből a cikkből megtudhatja, hogyan hozhat létre egyéni profilt macOS-eszközök számára, és az Apple Configurator és az Apple Profil Manager használatához is útmutatást kap.

## <a name="before-you-begin"></a>Előkészületek

- Ha a konfigurációs profilokat az **Apple Configuratorral** hozza létre, győződjön meg arról, hogy az exportált beállítások kompatibilisek az Ön által használt eszközökön futó macOS verziójával. A nem kompatibilis beállításokból fakadó problémák megoldásával kapcsolatos információkat az [Apple Developer](https://developer.apple.com/) webhelyről letölthető **Configuration Profile Reference** és **Mobile Device Management Protocol Reference** című (angol nyelvű) útmutatókban talál.

- Az **Apple Profile Manager** használatakor:

  - Engedélyezze a [mobileszköz-felügyeletet](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C) a Profile Managerben.
  - Adja hozzá a [macOS-eszközöket](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984) a Profile Managerben.
  - Miután hozzáadott egy eszközt a Profile Managerben, lépjen a **Könyvtár** > **Eszközök** részhez > válassza ki az eszközt > válassza a **Beállítások** lehetőséget. Adja meg az eszköz általános, biztonsági, adatvédelmi, címtár- és tanúsítványbeállításait.

    Töltse le és mentse ezt a fájlt. A fájlt az Intune-profilban adja majd meg. 

  - Ellenőrizze, hogy az Apple Profile Managerből exportált beállítások kompatibilisek-e az Ön által használt eszközökön futó macOS-verzióval. A nem kompatibilis beállításokból fakadó problémák megoldásával kapcsolatos információkat az [Apple Developer](https://developer.apple.com/) webhelyről letölthető **Configuration Profile Reference** és **Mobile Device Management Protocol Reference** című (angol nyelvű) útmutatókban talál.

## <a name="create-the-profile"></a>A profil létrehozása

1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg a következő beállításokat:

    - **Név**: Adja meg egy nevet a profilnak, például `macos custom profile`.
    - **Description** (Leírás): Adja meg a profil leírását.
    - **Platform**: Válasszon **macOS**.
    - **Profil típusa**: Válasszon **egyéni**.

4. Az **Egyéni konfiguráció** részben adja meg a következő beállításokat:

    - **Egyéni konfigurációs profil neve**: Adja meg a szabályzat nevét. Ez a név megjelenik az eszközön, valamint az Intune állapotában.
    - **Konfigurációs profil fájlja**: Keresse meg az Apple Configuratort vagy az Apple-profil Manager használatával létrehozott konfigurációs profilt. Az importált fájl megjelenik a **Fájl tartalma** területen.

5. Az Intune-profil létrehozásához válassza az **OK** > **Létrehozás** lehetőséget. Ha a profil elkészült, megjelenik az **Eszközkonfiguráció – Profilok** listában.

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Következő lépésként [végezze el a profil hozzárendelését](device-profile-assign.md).

Tekintse meg, hogyan [hozhat létre profilokat iOS-eszközökön](custom-settings-ios.md).

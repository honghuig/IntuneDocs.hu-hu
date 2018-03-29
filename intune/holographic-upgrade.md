---
title: "A Windows Holographic frissítése a Windows Holographic for Business verzióra"
titleSuffix: Microsoft Intune
description: "Tudja meg, hogyan frissítheti a Windows Holographic operációs rendszert futtató eszközöket a Windows Holographic for Business verzióra"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e7c750b372c297637abcdb9e941dae17714d081b
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/08/2018
---
# <a name="upgrade-devices-running-windows-holographic-to-windows-holographic-for-business"></a>A Windows Holographic operációs rendszert futtató eszközök frissítése a Windows Holographic for Business verzióra


A Windows Holographic operációs rendszert futtató eszközök Microsoft Intune-nal való kezeléséhez frissítenie kell az eszközöket a Windows Holographicról a Windows Holographic for Businessre. A frissítéshez létrehozhat egy kiadásfrissítési profilt. A Microsoft HoloLens esetében a frissítéshez szükséges licenc beszerzéséhez megvásárolhatja a Commercial Suite-ot is. További információkért lásd: [Unlock Windows Holographic for Business features](https://docs.microsoft.com/en-us/hololens/hololens-upgrade-enterprise) (A Windows Holographic for Business új funkcióinak elérése).

## <a name="to-set-up-an-edition-upgrade-device-configuration-profile"></a>Kiadásfrissítési eszközkonfigurációs profil beállítása

1. Jelentkezzen be rendszergazdai fiókjával az [Azure Portalra](https://portal.azure.com).


2.  Nyissa meg az **Eszközkonfiguráció**, **Profilok** lapot, majd kattintson a **Profil létrehozása** gombra.

    ![A profil létrehozása](media/Holographic-create-profile.png)

3.  A **Profil létrehozása** panelen írja be a profil nevét, és válassza a **Windows 10 és újabb rendszerek** platformot, majd a **Kiadásfrissítés** profiltípust. Kattintson a **Beállítások > Konfigurálás** lehetőségre.

5. A **Kiadásfrissítés** panelen a **Frissítés erre a kiadásra** listában válassza a **Windows 10 Holographic for Business** lehetőséget. A **Licencfájl** részen keresse meg és jelölje ki a kapott XML formátumú licencfájlt.

    ![Az XML-fájl nevének megadása](media/Holographic-edition-upgrade.png)
 
5.  Kattintson az **OK** gombra, majd a **Létrehozás** elemre a profil létrehozásához.


## <a name="deploy-the-edition-upgrade-policy"></a>A kiadásfrissítési szabályzat érvénybe léptetése

A következő lépés során rendelje hozzá a kiadásfrissítési profilt a kijelölt csoportokhoz vagy eszközökhöz.

1. Kattintson a **Hozzárendelések** elemre az előző lépésekben létrehozott profilban.

2. A **Hozzárendelések** panelen válassza ki a szabályzattal felvenni vagy kizárni kívánt felhasználói csoportokat és eszközöket.

![Csoportok belefoglalása vagy kizárása](media/Holographic-groups.PNG)

Ha ezek a felhasználók vagy eszközök regisztrálva vannak az Intune-ban, a kiadásfrissítési profil lesz alkalmazva. 

## <a name="next-steps"></a>További lépések

A csoportokkal kapcsolatos további tudnivalókért lásd: [Csoportok – első lépések](get-started-groups.md).


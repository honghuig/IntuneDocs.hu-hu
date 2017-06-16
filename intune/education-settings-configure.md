---
title: "Az Intune oktatási beállításainak konfigurálása Windows 10 esetén"
titleSuffix: Intune Azure preview
description: "Intune az Azure-on – előzetes: További információ arról, hogyan használható az Intune az oktatási beállítások felügyelt eszközökön való konfigurálásához Windows 10 esetén."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 3acb45ccc9e67fb410a9511f138d1558a49fadf9
ms.contentlocale: hu-hu
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-configure-windows-10-education-settings-in-microsoft-intune"></a>Az oktatási beállítások konfigurálása a Microsoft Intune-ban Windows 10 esetén

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Az oktatási profilokkal lehet megadni a Windows Vizsga alkalmazást konfiguráló részleteket, például a fiókadatokat és a vizsga URL-címét. Ennek konfigurálásakor megnyílik a Vizsga alkalmazás a megadott vizsgával, és annak befejezéséig az eszközön nem lehet másik alkalmazást futtatni.

A témakörben található információk alapján megismerheti az eszközkorlátozási profilok konfigurálásának alapjait, és az egyes platformokra vonatkozó további témakörökben bővebben is olvashat az eszközök tulajdonságairól.

## <a name="create-a-device-profile-containing-education-profile-settings"></a>Oktatási profilbeállításokat tartalmazó eszközprofil létrehozása

1. Jelentkezzen be az Azure Portalra.
2. Válassza a **További szolgáltatások** > **Egyéb** > **Intune** lehetőséget.
3. Az **Intune** panelen válassza az **Eszközkonfiguráció** lehetőséget.
2. Az **Eszközkonfiguráció** panelen válassza a **Felügyelet** > **Profilok** lehetőséget.
3. A profilok paneljén válassza a **Profil létrehozása** lehetőséget.
4. A **Profil létrehozása** panelen adja meg az eszközkorlátozási profil **Nevét** és **Leírását**.
5. A **Platform** legördülő listából válassza a **Windows 10 és újabb** lehetőséget.
6. A **Profil típusa** legördülő listában válassza az **Oktatási profil** lehetőséget. 
7. Kattintson a Beállítások > Konfigurálás elemre, majd a **Vizsga** panelen konfigurálja a következőket:
    - **Fiók felhasználóneve** – Írja be a Vizsga alkalmazáshoz használni kívánt fiók felhasználónevét. Ez lehet tartományi fiók, Azure Active Directory- (AAD-) fiók vagy helyi számítógépfiók is.
    - **Felmérési URL-cím** – Adja meg annak a vizsgának az URL-jét, amelyet a felhasználóknak el kell végezniük. További információt a Vizsga dokumentációjában talál.
    - **Képernyőfigyelés** – Itt adhatja meg, hogy szeretné-e figyelni a felhasználók képernyőjét a vizsga során.
    - **Szövegjavaslat** – Engedélyezheti vagy letilthatja a szövegjavaslatokat a vizsga során.
8. Ha elkészült, lépjen vissza a **Profil létrehozása** panelre, és válassza a **Létrehozás** elemet.

Ekkor létrejön a profil, és megjelenik a profilok listáját tartalmazó panelen.
Ha szeretné a profil csoportokhoz való hozzárendelésével folytatni, erről a [How to assign device profiles](device-profile-assign.md) (Eszközprofilok hozzárendelése) című témakörben olvashat.




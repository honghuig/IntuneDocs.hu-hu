---
title: "E-mail-beállítások az Intune-ban Windows 10-es eszközök esetén"
titleSuffix: Intune Azure preview
description: "Intune az Azure-on – előzetes: A cikk a e-mail-kapcsolatoknak a Windows 10 rendszerű eszközökön való konfigurálására használható Intune-beállításokat ismerteti."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ffafbd0-4b5d-4c86-a46b-611f9b7a58e5
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 9a052f26d87fbfdc5794cf97033b409846db6a73
ms.lasthandoff: 02/18/2017


---

# <a name="email-profile-settings-for-windows-10-devices-in-microsoft-intune"></a>Windows 10-es eszközökre vonatkozó e-mail-profilbeállítások a Microsoft Intune-ban

[!INCLUDE[azure_preview](../includes/azure_preview.md)]



- **E-mail-kiszolgáló** – Itt adja meg az Exchange-kiszolgáló állomásnevét.
- **Fióknév** – Adja meg az e-mail-fiók megjelenítendő nevét (ez lesz látható a felhasználók eszközén).
- **Felhasználónév attribútum az AAD-ből** – Ez az Active Directory (AD) vagy az Azure AD egy attribútuma, ennek alapján fogja generálni a rendszer ennek az e-mail-profilnak a felhasználónevét. Válassza az **Elsődleges SMTP-cím** (például **user1@contoso.com**) lehetőséget, vagy az **Egyszerű felhasználónév** (például **user1** vagy **user1@contoso.com**) lehetőséget.
- **E-mail-cím attribútuma az AAD-ből** – Válassza ki, hogyan jöjjön létre a felhasználói e-mail-cím az egyes eszközökön. Ha az elsődleges SMTP-cím használatával kíván bejelentkezni az Exchange-be, válassza az **Elsődleges SMTP-cím** lehetőséget; ha e-mail-címként a teljes egyszerű felhasználónevet kívánja használni, válassza az **Egyszerű felhasználónév** lehetőséget.


## <a name="security-settings"></a>Biztonsági beállítások

- **SSL** – SSL-kommunikáció használata az e-mailek küldésekor és fogadásakor, valamint az Exchange-kiszolgálóval való kommunikációhoz.



## <a name="synchronization-settings"></a>Szinkronizálási beállítások

- **Szinkronizálandó e-mailek mennyisége** – Válassza ki, hogy hány napra visszamenőleg szeretné szinkronizálni az e-maileket, vagy az összes e-mail szinkronizálásához válassza a **Korlátlan** lehetőséget.
- **Szinkronizálás ütemezése** – Válassza ki azt az ütemezést, amely szerint az eszközök szinkronizálni fogják az adatokat az Exchange Serverrel. **Az üzenetek érkezésekor** lehetőség kiválasztásával a rendszer azonnal szinkronizálja az adatokat, amint megérkeznek, a **Manuális** beállítás esetén pedig a felhasználónak kell kezdeményeznie a szinkronizálást.

## <a name="content-sync-settings"></a>Tartalomszinkronizálási beállítások

- **Szinkronizálandó tartalomtípus** – Válassza ki az eszközökre szinkronizálni kívánt tartalomtípusokat:
    - **Névjegyek**
    - **Naptár**
    - **Feladatok**

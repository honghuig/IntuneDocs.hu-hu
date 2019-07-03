---
title: A Sophos Mobile Intune szolgáltatással való integráció beállítása
titleSuffix: Intune on Azure
description: Hogyan állítható be a Microsoft Intune-nal a Sophos Mobile megoldás annak érdekében, hogy a vállalati erőforrások mobil elérése.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: ec60a618280caf6a5b7ef242c192cc64b5d839de
ms.sourcegitcommit: 84c79ceea27f7411528defc5ee8ba35ae2bf473c
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67511906"
---
# <a name="integrate-sophos-mobile-with-intune"></a>A Sophos Mobile integrálása az Intune-nal  

A következő lépéseket a Sophos Mobilfenyegetések elleni megoldás integrálása az Intune-nal.  

## <a name="before-you-begin"></a>Előkészületek  

Mielőtt elkezdené a Sophos Mobile integrálása az Intune-nal, ellenőrizze, hogy rendelkezik az alábbiakkal:  
- Microsoft Intune-előfizetés  
- Azure Active Directory rendszergazdai hitelesítő adatok a következő engedélyek megadására:  
  - Bejelentkezés és felhasználói profil olvasása  
  - A címtár elérése a bejelentkezett felhasználó nevében  
  - Címtáradatok olvasása  
  - Eszközadatok küldése az Intune-ba  
- Rendszergazdai hitelesítő adatok a Sophos mobileszköz-felügyeleti konzol eléréséhez.  


### <a name="sophos-mobile-app-authorization"></a>A Sophos Mobile alkalmazás engedélyezése  
  
A Sophos Mobile alkalmazás engedélyezési folyamata a következő:  
- A Sophos mobilszolgáltatás adatok az Eszközállapot vissza az Intune-hoz való engedélyezése.  
- A Sophos Mobile szinkronizálja az Azure AD regisztrációs az eszköz adatbázisának feltöltéséhez.  
- A Sophos Mobile felügyeleti konzol használatához Azure AD egyszeri bejelentkezési (SSO) engedélyezése.  
- A Sophos mobilalkalmazás bejelentkezni az Azure AD SSO engedélyezése.  


## <a name="to-set-up-sophos-mobile-integration"></a>A Sophos Mobile-integráció beállítása  

1. Jelentkezzen be a [az Azure portal]( https://portal.azure.com/)lépjen **Intune** > **eszközmegfelelőség** > **Mobile Threat Defense** > Válassza ki **Hozzáadás**.  
2. Az a **hozzáadása összekötő** lapon használja a legördülő menüt, és válassza **Sophos**. Majd **létrehozás**.  
3. Válassza ki a hivatkozást *nyissa meg a Sophos felügyeleti konzol*.  
4. Jelentkezzen be a [Sophos felügyeleti konzol](https://central.sophos.com/) a Sophos hitelesítő adataival.  
5. Lépjen a **Mobile** > **beállítások** > **telepítő** > **Sophos telepítő**.  
6. Az a **Sophos telepítő** lapon válassza ki a **MTD Intune-ban** fülre.  
   ![A Sophos beállítása](./media/sophos-mtd-connector-integration/sophos-setup.png) 
 
7. Válassza ki **kötési**, majd válassza ki **Igen**. A Sophos az Intune-hoz csatlakozik, és jelentkezzen be az Intune-előfizetés szükséges. 
8. A Microsoft Intune hitelesítési ablakában adja meg a hitelesítő adatait az Intune és a **elfogadás** engedélyeket kérhetnek *Sophos Mobile hozzászóláslánc Defense*.  
   ![Az Intune-hitelesítés](./media/sophos-mtd-connector-integration/intune-authentication.png)

9. Az a **Sophos telepítő** lapon jelölje be **mentése** elvégezni a konfigurálást az Intune-ban:  
   ![A Sophos beállítások mentése](./media/sophos-mtd-connector-integration/save-sophos-configuration.png)  

1. A **sikeres integrációt** jelző ablak megjelenésekor az integráció befejeződött.  
1. Az Intune-konzolon a Sophos már elérhető.  


## <a name="next-steps"></a>További lépések  
[A Sophos ügyfélalkalmazások konfigurálása](mtd-apps-ios-app-configuration-policy-add-assign.md)

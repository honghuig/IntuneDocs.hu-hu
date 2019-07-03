---
title: Az Intune-nal Wandera Mobile Threat Protection-integráció beállítása
titleSuffix: Intune on Azure
description: Hogyan állítható be a Microsoft Intune-nal Wandera mobil veszélyforrások elleni Eszközvédelem megoldás annak érdekében, hogy a vállalati erőforrások mobil elérése.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: e4f2969c6bb7f15022990aa99bbf20e94588406e
ms.sourcegitcommit: 84c79ceea27f7411528defc5ee8ba35ae2bf473c
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67512294"
---
# <a name="integrate-wandera-mobile-threat-protection-with-intune"></a>Wandera mobil veszélyforrások elleni védelem integrálása az Intune-nal  

A következő lépéseket a Wandera Mobilfenyegetések elleni megoldás integrálása az Intune-nal.  

## <a name="before-you-begin"></a>Előkészületek  

Wandera integrálása az Intune-nal, a folyamat megkezdése előtt győződjön meg arról, hogy már működik a következő előfeltételek vonatkoznak a:
- Microsoft Intune-előfizetés  
- Azure Active Directory rendszergazdai hitelesítő adatok a következő engedélyek megadására:  
  - Bejelentkezés és felhasználói profil olvasása  
  - A címtár elérése a bejelentkezett felhasználó nevében  
  - Címtáradatok olvasása  
  - Eszközadatok küldése az Intune-ba  

- Előfizetés Wandera:
  - Egy vagy több Wandera fiókok, amelyek licencét for EMM-csatlakozás  
  - Wandera a felügyelői rendszergazdai jogosultságokkal rendelkező fiók  
 
### <a name="wandera-mobile-threat-defense-app-authorization"></a>Wandera Mobile Threat Defense alkalmazás engedélyezése  

A Wandera Mobile Threat Defense alkalmazás engedélyezési folyamata:  
- Lehetővé teszi a Wandera Mobile Threat Defense szolgáltatást, az adatok az Eszközállapot vissza az Intune-hoz.  
- Wandera szinkronizálja az Azure AD regisztrációs az eszköz adatbázisának feltöltéséhez.  
- Lehetővé teszi a Wandera a MÉRLEGELI felügyeleti portálon az Azure AD egyszeri bejelentkezés (SSO) használatára.  
- A Wandera Mobile Threat Defense alkalmazás bejelentkezni az Azure AD SSO engedélyezése.  


## <a name="set-up-wandera-mobile-threat-defense-integration"></a>Wandera Mobile Threat Defense-integráció beállítása  
A telepítő *EMM-csatlakozás* Wandera megköveteli, hogy egyszeri feldolgozását, hogy elvégezte-e az Intune-ban és a Wandera konzolokban. A konfigurációs folyamat nagyjából 15 percet vesz igénybe. Konfigurációjához koordinálása nélkül Wandera műszaki fiókjával, vagy támogatási képviselőhöz.  

### <a name="enable-support-for-wandera-in-intune"></a>Az Intune-ban Wandera támogatásának engedélyezése
1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) , majd **eszközmegfelelőség** > **Mobile Threat Defense** > és válassza ki **Hozzáadás**.

2. Az a **hozzáadása összekötő** lapon használja a legördülő menüt, és válassza **Wandera**. Majd **létrehozás**.  

3. A Mobile Threat Defense panelen válassza ki a **Wandera** MTD-összekötő az összekötők, nyissa meg a listából a *-összekötő szerkesztése* ablaktáblán. Válassza ki **nyissa meg a rendszergazdai konzolt Wandera** megnyitásához [SUGÁRDIAGRAM](https://radar.wandera.com/login), Wandera felügyeleti konzolt, és jelentkezzen be. 

4. A Wandera-konzolon lépjen a **beállítások** > **EMM Integration**, és válassza ki a **EMM-csatlakozás** fülre. Használja a *EMM szállítói* listából, és válassza ki *a Microsoft Intune*.

   ![Válassza ki az Intune-ban](media/wandera-mtd-connector-integration/set-up-intune-in-radar.png)

5. Válassza ki **engedélyeket** való kapcsolatot létesíteni az Intune-portálon. Jelentkezzen be az Intune rendszergazdai hitelesítő adataival, jelölje be a jelölőnégyzetet, majd **elfogadás** az engedélyek kérése.  

   ![Fogadja el az engedélyek](media/wandera-mtd-connector-integration/permissions.png) 

6. Wandera a kapcsolat befejeződik, és visszatér a MÉRLEGELI felügyeleti konzolon. Ismételje meg a folyamat **Grant** igény szerint további konfigurációk esetén eléréséhez.  

   ![Engedélyek és integrációk](media/wandera-mtd-connector-integration/integrations-and-permissions.png) 

7. A MÉRLEGELI konzolon nevének másolása a **SyncOnly** alatt megjelenő csoport **EMM címke**. Csoportok beállítása az Intune-ban való Wandera szinkronizálásra ezt a nevet fogja használni.

   ![Engedélyek és integrációk](media/wandera-mtd-connector-integration/sync-group-name.png) 

8. Lépjen vissza a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) konzolról, és a Wandera MTD-összekötő szerkesztése. Állítsa be a rendelkezésre álló be-vagy kikapcsolja **a**, és a **mentése** a konfigurációt.  

   ![Enable Wandera](media/wandera-mtd-connector-integration/enable-wandera.png) 

Az Intune és a Wandera ezzel csatlakozott.  

## <a name="configure-the-wandera-applications-and-synchronization-group"></a>A Wandera alkalmazások és a szinkronizálási csoport konfigurálása  
Wandera üzembe helyezéséhez fel fog venni a Wandera mobilalkalmazásokban a platformok (iOS és Android) használata az Intune-hoz, és hozzárendelheti azokat a szinkronizáláshoz; adott csoportban a *SyncOnly* csoport. 

A következő szakaszok és eljárások végigvezeti Önt a folyamatot.

További információ erről a folyamatról a Wandera, jelentkezzen be Wandera [SUGÁRDIAGRAM](https://radar.wandera.com/login). Lépjen a **beállítások** > **EMM Integration**, jelölje be a **App-leküldés** lapra, és válassza ki **a Microsoft Intune**. App-leküldés lapon frissítések az Intune-ra vonatkozó utasításokat.  

### <a name="add-the-wandera-apps"></a>A Wandera alkalmazások hozzáadása  
Alkalmazások az ügyfél létrehozása az Intune-ban a Wandera alkalmazás telepítése Android és IOS rendszerű eszközökre. Lásd: [hozzáadása MTD-alkalmazások](mtd-apps-ios-app-configuration-policy-add-assign.md) eljárások és a Wandera alkalmazások egyéni adatait.  

Miután létrehozta az alkalmazásokat, visszatérhet ide, a szinkronizálási csoport létrehozása és hozzárendelése az alkalmazásokat.  


### <a name="create-the-synchronization-group-and-assign-the-apps"></a>A szinkronizálási csoport létrehozása és az alkalmazások hozzárendelése

1. Nevét a **SyncOnly** alatt megjelenő csoport **EMM címke** a Wandera a MÉRLEGELI-konzolról. Előfordulhat, hogy mentette-e ez a név alatt 7. lépés során [engedélyezése az Intune-ban Wandera támogatása](#enable-support-for-wandera-in-intune). Ez a név használata az Intune-ban a csoport neveként Wandera szinkronizálásához.  

2. Az Intune-konzolon lépjen a **csoportok** válassza **új csoport**. Adja meg az alábbi parancsot a szinkronizálási csoport Wandera általi használatra konfigurálásához:
   - **Csoport típusa**: **Biztonsági**
   - **Csoport neve**: Adja meg a **SyncOnly** a MÉRLEGELI Wandera felügyeleti konzol lekért nevet.

   ![a szinkronizálási csoport konfigurálása](media/wandera-mtd-connector-integration/configure-sync-group.png)

3. Válassza ki **tagok** és az Android és IOS rendszerű eszközök Wandera a használni kívánt csoportok hozzárendelése.

4. Válassza ki **létrehozás** menteni a csoportot.

További információkért lásd: [alkalmazások üzembe helyezése](apps-deploy.md)

### <a name="assign-the-wandera-apps-to-the-synchronization-group"></a>A Wandera alkalmazások hozzárendelése a szinkronizálási csoport  
Ismételje meg a következő eljárás a Wandera alkalmazást iOS-hez és Androidhoz készült hozott létre.

1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) , majd **ügyfélalkalmazás** > **alkalmazások** válassza ki a Wandera alkalmazást.  

2. Válassza ki **hozzárendelések** , majd **csoport hozzáadása**.  

3. Az a *csoport hozzáadása* panelen a *hozzárendelés-típus* kiválasztása **szükséges**.

4. Válassza ki **tartalmazott csoportok**, majd **válassza ki a befoglalandó csoportokat**. Adja meg a létrehozott Wandera szinkronizálási csoportot, és kattintson **kiválasztása** > **OK** > **OK**. Válassza ki **mentése** a csoport-hozzárendelés végrehajtásához.  
 

## <a name="next-steps"></a>További lépések  
Most, hogy konfigurálta az integrációt, indítsa el a házirendek konfigurálása, speciális feltételes hozzáférés beállítása és jelentések megtekintése az Wandera felügyeleti konzolon. További információk kezeléséről és konfigurációjáról Wandera kapcsolatban lásd: a [támogatási központ Getting Started Guide](https://radar.wandera.com/?return_to=https://wandera.force.com/Customer/s/getting-started) Wandera dokumentációjában.  
 
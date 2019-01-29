---
title: A Microsoft Intune bérlői állapota lap
titleSuffix: Microsoft Intune
description: Az Intune-bérlő állapotát lap segítségével fontos bérlői adatainak megtekintése az Intune-portál elhagyása nélkül
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 98b3180bc90c7b54213781ddf8b6668918b22dd3
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203795"
---
# <a name="intune-tenant-status-page"></a>Az Intune bérlői állapota lap
Egy információs központ, a bérlő állapotának lap segítségével naprakész a fontos a bérlő, licenc rendelkezésre állásáról és használata, összekötő állapotát, és az Intune szolgáltatással kapcsolatos fontos kommunikáció.  

Az irányítópult megtekintése az Azure Portalon, lépjen az **Intune > Bérlőállapot**.  Bérlői állapota megjelenik a **Súgó és támogatási csoport**.  

A lap négy területet oszlik:

## <a name="tenant-details"></a>Bérlő részletei
Bérlő részletei a bérlő egy pillantással adatainak megadása. Részletek megtekintése, például a bérlő nevét és helyét, az MDM-szolgáltató és a bérlők szolgáltatási kiadás száma. A kiadási száma egy hivatkozás, amely megnyitja a *Újdonságok az Intune-ban* a cikk a Microsoft docs webhelyén, ahol olvashat a legújabb funkciókat és frissítéseket az Intune szolgáltatáshoz.  

Ez a szakasz is a rendelkezésre álló licencek és hány rendelkező felhasználókhoz rendelt alapvető információkat biztosít. Licencek eszközök nem jelennek meg.

## <a name="connector-status"></a>Összekötő állapota
Összekötő állapota egyablakos helyét az összes elérhető összekötő állapotának áttekintése az Intune-hoz.  

Az összekötők a következők:
- **Külső szolgáltatások úgy konfigurálhatók kapcsolatok**. Ha például a *Apple Volume Purchase Program* szolgáltatás vagy a *Windows Autopilot* szolgáltatás.  Az ilyen típusú összekötő állapota a legutóbbi sikeres szinkronizálásának időpontját alapul.
- **Tanúsítványok vagy egy külső nem felügyelt szolgáltatáshoz való csatlakozáshoz szükséges hitelesítő adatokat**, pl. *Apple leküldéses értesítési szolgáltatások* (APNS) tanúsítványokat. Az ilyen típusú összekötő állapota a lejárat időbélyeg a tanúsítvány vagy hitelesítő adatok alapján történik.  

Alapértelmezés szerint csak öt összekötő jelennek meg. Választhat **tekintse meg az összes összekötő** bontsa ki a lista az összes elérhető összekötők, többek között még nem konfigurálta használható összekötők megtekintéséhez.  

Ha több mint egy típustól egy összekötőt, az állapota az összes azonos összekötőket összegzését. A csoport egyetlen összekötőket legalább kifogástalan állapotát az egészségügyi lesz.  

Nem megfelelő állapotú összekötők mindig a lista tetején jelennek meg. Ezután olyan összekötőket figyelmeztetéseket, majd a megfelelő összekötők listája. Még nem konfigurálta összekötőket utolsó.

**Összekötő állapota:**
- **Nem megfelelő állapotú:**
    - A tanúsítvány vagy hitelesítő adatok érvényessége lejárt
    - A legutóbbi szinkronizálás legalább három nappal ezelőtt volt
- **Figyelmeztetés:**
    - A tanúsítvány vagy hitelesítő adatok hét napon belül lejár
    - A legutóbbi szinkronizálás több mint egy nappal ezelőtt volt
- **Kifogástalan állapotú:**
    - A tanúsítvány vagy hitelesítő adatok nem jár le a hét napon belül
    - A legutóbbi szinkronizálás kevesebb, mint egy nappal ezelőtt volt  

Amikor kiválaszt egy összekötőt a listából, a portál megjelenít a portálon, amely fontos létrehozásáról és konfigurálásáról az összekötőt.  Például, ha kiválasztja a **VPP lejárati dátuma** összekötőt, a **Program-tokenek mennyiségi licencszerződés keretében vásárolt iOS** lap megnyitásakor, ahol megtekintheti, hogy az összekötő további információt. Ezután hozzon létre egy új konfigurációt vagy szerkesztheti és problémáinak elhárítása egy már meglévőt.  

## <a name="intune-service-health"></a>Az Intune szolgáltatás állapota  
Keresse meg a Microsoft 365 üzemállapot-jelző pult vagy az üzenetközpont nélkül megtekintheti az aktív incidensek által érintett, és a tanácsadók adatait, mind a Microsoft 365 felügyeleti központban, található https://portal.office.com. Csak a ahol hatás lett tudomásul vette a bérlő érintő incidensek jelennek meg.  

Amikor kiválaszt egy incidenst, a támogatási kérelem részletek közvetlenül a bérlő állapotának oldalán jelennek meg. Tanácsok és incidensek korábbi megtekintéséhez jelölje ki **korábbi incidensek/tanácsadók**. A Microsoft 365 felügyeleti központ megnyílik, és ezután megtekintheti tanácsok és incidensek az elmúlt 30 nap-bérlője számára.  

Információk megtekintéséhez *az Intune szolgáltatás állapota*, a fióknak rendelkeznie kell a **globális rendszergazdai** vagy **szolgáltatás-rendszergazda** szerepkört az Azure Active Directoryban vagy a Office felügyeleti portálján. Szeretné hozzárendelni ezeket az engedélyeket, jelentkezzen be a [Microsoft 365 felügyeleti központban](https://portal.officeppe.com/AdminPortal/Home#/homepage) globális rendszergazdai jogosultságokkal rendelkező. Válassza ki **felhasználók > aktív felhasználók**, és válassza ki azt a fiókot, amelyhez hozzáférés szükséges. Válassza ki **szerkesztése** szerepkörhöz, válassza ki a *szolgáltatás-rendszergazda* vagy *globális rendszergazdai*, majd **mentése** hozzárendelése a módosításokat a engedélyek.  

A kommunikációs beállítások az Intune szolgáltatás állapotát a Microsoft 365 felügyeleti központban csak beállítása.

## <a name="intune-news"></a>Az Intune-hírek  
Tájékoztató kommunikáció az Intune szolgáltatás csapat megtekintéséhez nyissa meg az Office Üzenetközpontjában nélkül. Kommunikációs üzeneteket, amelyek nemrég történt az Intune szolgáltatásba, vagy az a bérlőhöz tartozó von a változásokat tartalmazza.  

Alapértelmezés szerint a legutóbbi 10 aktív üzenetek jelennek meg. Régebbi üzeneteket megtekintéséhez jelölje ki **lásd a régebbi üzeneteket** megnyitásához a *üzenetközpont* a Microsoft 365 felügyeleti központ portálján.  

Intune hírek vonatkozó információk megtekintéséhez, a fióknak rendelkeznie kell a **globális rendszergazdai** vagy **szolgáltatás-rendszergazda** szerepkörhöz az Azure Active Directoryban, vagy lehet hozzárendelni a **üzenetközpont olvasó**  szerepkör az Office felügyeleti portálon.  Rendelje hozzá ezt az engedélyt, jelentkezzen be a [Microsoft 365 felügyeleti központban](https://portal.officeppe.com/AdminPortal/Home#/homepage) rendszergazdai jogosultságokkal. Válassza ki **felhasználók > aktív felhasználók**, és válassza ki azt a fiókot, amelyhez hozzáférés szükséges. Válassza ki **szerkesztése** a *szerepkörök*, jelölje be *csapatok kommunikáció rendszergazda*, majd **mentése** az engedélyek hozzárendelése a szerkesztése.  

A kommunikációs beállítások az Intune hírek a Microsoft 365 felügyeleti központban csak beállítása.
---
title: Microsoft Intune bérlő állapota lap
titleSuffix: Microsoft Intune
description: Az Intune-bérlő állapota lapon megtekintheti a bérlő fontos adatait az Intune-portál elhagyása nélkül
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 946d46baf17a5ffdd4b567adca32b651cacb72bb
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882223"
---
# <a name="intune-tenant-status-page"></a>Intune-bérlő állapota lap
A bérlő állapota lap egy központi központ, ahol megtekintheti a bérlő aktuális és fontos adatait. A részletek tartalmazzák a licencek rendelkezésre állását és használatát, az összekötő állapotát, valamint az Intune szolgáltatással kapcsolatos fontos kommunikációt.  

Az irányítópult megtekintéséhez a Azure Portal lépjen az **Intune > a bérlő állapota**elemre.  A bérlő állapota a **Súgó és támogatás csoportban**jelenik meg.  

A lap négy területre oszlik:

## <a name="tenant-details"></a>Bérlő részletei
A bérlői adatok áttekintést nyújtanak a bérlőről. Megtekintheti a bérlő nevét és helyét, a MDM-szolgáltatót és a bérlői szolgáltatás kiadási számát. A szolgáltatás kiadásának száma egy hivatkozás, amely megnyitja az *Újdonságok az Intune-ban* című cikket a Microsoft docs webhelyen. Az *Újdonságok*az Intune szolgáltatás legújabb szolgáltatásairól és frissítéseiről olvashatók.  

Ez a szakasz a rendelkezésre álló licencekkel kapcsolatos alapvető információkat és a felhasználókhoz rendelt mennyiségeket is tartalmazza. Az eszközökhöz tartozó licencek nem jelennek meg.

## <a name="connector-status"></a>Összekötő állapota
Az összekötő állapota egy egyablakos hely az Intune összes elérhető összekötője állapotának áttekintéséhez.  

Az összekötők a következők:
- **Külső szolgáltatásokhoz konfigurált kapcsolatok**. Például a *Apple Volume Purchase program* szolgáltatás vagy a *Windows Autopilot* szolgáltatás.  Az ilyen típusú összekötő állapota a legutóbbi sikeres szinkronizálási időponton alapul.
- A külső, nem felügyelt szolgáltatásokhoz, például az *Apple Push Notification Services* (APNS) tanúsítványokhoz való **kapcsolódáshoz szükséges tanúsítványok vagy hitelesítő adatok**. Az ilyen típusú összekötő állapota a tanúsítvány vagy a hitelesítő adat lejárati időbélyegzője alapján történik.  

Alapértelmezés szerint a kijelző legfeljebb öt összekötőt jelenít meg. A lista kibontásához válassza az **összes összekötő** megjelenítése lehetőséget, hogy megtekintse az összes elérhető összekötőt, beleértve a használatra nem konfigurált összekötőket is.  

A nem megfelelő állapotú összekötők mindig a lista tetején jelennek meg. A következő a figyelmeztetéseket tartalmazó összekötők, majd az egészséges összekötők listája. A még nem konfigurált összekötők utoljára jelennek meg.

Ha több, mint egyetlen összekötő egyetlen típusból áll, az állapot az összes azonos összekötő összefoglalása. Az egyes összekötők legalább kifogástalan állapota a csoport állapotának megfelelően van használatban.  

**Összekötő állapota:**
- **Sérült**
  - A tanúsítvány vagy a hitelesítő adat Lejárt
  - A legutóbbi szinkronizálás három nappal ezelőtt történt
- **Figyelmeztetés**
  - A tanúsítvány vagy a hitelesítő adat érvényessége hét napon belül lejár
  - A legutóbbi szinkronizálás több mint egy nappal ezelőtt történt
- **Kifogástalan**
  - A tanúsítvány vagy a hitelesítő adat nem jár le a következő hét napon belül
  - A legutóbbi szinkronizálás kevesebb mint egy nappal ezelőtt történt  

Amikor kijelöl egy összekötőt a listából, a portál az összekötő létrehozásához vagy konfigurálásához szükséges portált jeleníti meg.  Ha például kiválasztja a **VPP lejárati dátum** összekötőt, megnyílik az **iOS Volume-purchased program-** jogkivonatok lap, ahol megtekintheti az összekötő további részleteit. Ezután létrehozhat egy új konfigurációt, vagy szerkesztheti és kijavíthatja a meglévő problémákat.  

## <a name="intune-service-health"></a>Az Intune szolgáltatás állapota  
Az aktív incidensek és a tanácsadók adatait úgy tekintheti meg, hogy nem kell megnyitnia a Microsoft 365 Service Health irányítópultot vagy az üzenetközpont-t, amely a [Microsoft 365 felügyeleti központban](https://admin.microsoft.com)található. Csak azok az incidensek jelennek meg, amelyeken a bérlőt érintő hatás látható.  

Ha kijelöl egy eseményt, az incidens részletei közvetlenül a bérlő állapota lapon jelennek meg. A korábbi tanácsadók és incidensek megtekintéséhez válassza a **korábbi incidensek/tanácsadók**megtekintése lehetőséget. Megnyílik a Microsoft 365 felügyeleti központ, és megtekintheti a bérlőnek az elmúlt 30 napban megadott tanácsadókat és incidenseket.  

Az *Intune-Service Health*adatainak megtekintéséhez a fióknak a Azure Active Directory vagy a Microsoft 365 felügyeleti központban kell lennie a **globális rendszergazdai** vagy **szolgáltatás-rendszergazdai** szerepkörrel. Az engedélyek hozzárendeléséhez jelentkezzen be a [Microsoft 365 felügyeleti](https://admin.microsoft.com) központba globális rendszergazdai engedélyekkel. Válassza a **felhasználók > az aktív felhasználók**lehetőséget, majd válassza ki azt a fiókot, amelyhez hozzáférés szükséges. Válassza a szerepkörök **szerkesztése** lehetőséget, válassza a *szolgáltatás-rendszergazda* vagy a *globális rendszergazda*lehetőséget, majd **mentse** a szerkesztést az engedélyek hozzárendeléséhez.  

A Microsoft 365 felügyeleti központban csak az Intune-Service Health kommunikációs beállításait állíthatja be.

## <a name="intune-news"></a>Intune-Hírek  
Tekintse meg az Intune szolgáltatás csapatának tájékoztató jellegű kommunikációját anélkül, hogy az Office Message Centerre kellene navigálnia. A kommunikáció olyan módosításokat tartalmaz, amelyek nemrég történtek az Intune szolgáltatásban, vagy amelyek a bérlői úton történnek.  

Alapértelmezés szerint az utolsó 10 aktív üzenet látható. A régebbi üzenetek megtekintéséhez kattintson a **korábbi üzenetek** megjelenítése elemre az *üzenetközpont* megnyitásához a Microsoft 365 felügyeleti központban.  

Az Intune-Hírek információinak megtekintéséhez a fióknak a Azure Active Directory  vagy az üzenetsor  - **olvasó** szerepkörrel kell rendelkeznie a Microsoft 365 felügyeleti központban.  Az engedély hozzárendeléséhez jelentkezzen be a [Microsoft 365 felügyeleti](https://admin.microsoft.com) központba rendszergazdai engedélyekkel. Válassza a **felhasználók > az aktív felhasználók**lehetőséget, majd válassza ki azt a fiókot, amelyhez hozzáférés szükséges. Válassza a *szerepkörök* **szerkesztése** lehetőséget, válassza a *csapatok kommunikációs rendszergazdája*lehetőséget, majd **mentse** a szerkesztést az engedélyek hozzárendeléséhez.  

A Microsoft 365 felügyeleti központban csak az Intune-Hírek kommunikációs beállításait állíthatja be.

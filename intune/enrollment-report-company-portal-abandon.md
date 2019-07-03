---
title: Hiányos felhasználói regisztrációk jelentése az Intune-ban
titleSuffix: Microsoft Intune
description: Ismerje meg a teljes felhasználói regisztrációk jelentése.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 2/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: c15bd301b60481f4d8b15617512851e2cc29034a
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67529759"
---
# <a name="incomplete-user-enrollments-report"></a>Hiányos felhasználói regisztrációk jelentése

Ez a jelentés elmagyarázza, ahol a vállalati portálon regisztrációs folyamatot felhasználók vannak nem befejezik a regisztrációs folyamatot.

A jelentés megtekintéséhez válassza ki **Intune** > **eszközregisztráció** > **hiányos felhasználói regisztrációk**.

Ezen információk alapján frissítheti a bevezetési dokumentumok, amely a felhasználókat a regisztráció befejezéséhez. Ha például sok felhasználó szakítja meg a folyamatot a Felhasználási feltételeknél, akkor megvizsgálhatja ezt a területet, és intuitívebbé teheti a felhasználók számára.

## <a name="what-is-an-incomplete-enrollment"></a>Mit jelent a hiányos regisztrációs?

Hiányos regisztrációnak az, amikor a felhasználó végrehajtja a következőket:

- Explicit módon a regisztrációt leállító műveletet választ
- Bezárja a Céges portált a regisztráció során
- Több mint 30 percet tölt el egy regisztrációs szakasszal, mielőtt a következővel folytatná

Ha egy felhasználó úgy dönt, hogy a regisztráció és az újraindítások többször, az megjelenik tett kísérletet, és több befejezetlen regisztrációk. Ha egy felhasználó különböző regisztrációs képernyők között, 30 percig várakozik, több befejezetlen regisztrációk tekintendő.

## <a name="what-does-the-report-show"></a>Mi mutat meg a jelentés?

A jelentések iOS és Android-eszközökre vonatkozó adatokat magukba foglalják.

A jelentés az elmúlt két hétre vonatkozó adatokat jelenít meg, de szűrheti a jelentést az elmúlt 30 napban bármely időszak megjelenítésére.

Szűrhet a dátumtartomány, az operációs rendszer és a regisztrációs szakasz alapján a **Szűrő** kiválasztásával.

### <a name="number-and-percentage-tiles"></a>Szám és százalékos arány csempék

A jelentés tetején látható száma és az összes regisztrációk viszonyítva hiányos regisztrációk aránya.

- Kezdeményezett regisztrációk: A megkísérelt regisztrációk száma.
- Hiányos regisztrációk: A megkísérelt regisztrációk, amelyek nem egy teljes körűen regisztrált és megfelelő eszközök száma.
- Hiányos sebesség: A beléptetési kísérletek, amely lettek hagyva (regisztrációk elhagyott / kezdeményezett regisztrációk) százaléka.

### <a name="line-graph"></a>Vonaldiagram

Vonaldiagramon jelenít meg a napi hiányos regisztrációk az egyes négy alapvető regisztrációs szakaszait:

- Beállítási ellenőrzőlista
- Platformképernyők
- Használati feltételek
- Megfelelőség/aktiválás

### <a name="user-abandonment-actions"></a>Felhasználói megszakítási műveletek

Az alábbi táblázatokban a műveleteknek a listája, felhasználói minősül az hiányos regisztrációs kérő üzenet. Regisztrációs képernyők példáinak megtekintéséhez megnézheti az [iOS](https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment) és az [Android](https://channel9.msdn.com/Series/IntuneEnrollment/Android-Enrollment) rendszerben történő regisztrációról készült videókat. 


#### <a name="setup-checklist-section"></a>Beállítási ellenőrzőlista szakasz

| Művelet neve | Képernyő vagy folyamat | Platform | Műveletek |
| ---- |---- |---- |---- |
| EnrollmentWrapUp | A rendszer arra kéri, hogy nyisson meg egy oldalt a Céges portálon. | iOS/Android | **Mégse** |
| EnrollmentWrapUp | Eszközregisztrációs képernyő, ami addig látható, amíg be nem fejeződik a **vállalati erőforrások betöltése** | iOS/Android | Időtartam > 30 perc |
| DeviceCategory | Eszközkategória kiválasztása (ha a rendszergazda beállította), addig látható, amíg rá nem kattint a **Kész** gombra | iOS/Android | Időtartam > 30 perc |
| PreEnrollmentWizard | Hozzáférés-beállítási képernyő, ha megkezdte a regisztrációt, de visszatért a hozzáférés-beállításhoz | iOS/Android| **Postpone** |
| PreEnrollmentWizard | Hozzáférés-beállítási képernyő, amely addig látható, amíg rá nem kattint a **Tovább** gombra a **Következő lépések** képernyőn | iOS/Android | Időtartam > 30 perc |

#### <a name="platform-screens-section"></a>Platformképernyők szakasz

| Művelet neve | Képernyő vagy folyamat | Platform | Műveletek |
| ---- |---- |---- |---- |
| iOSProfileLaunch | Rákérdezés a konfigurációs profil megjelenítésére | iOS | **Figyelmen kívül hagyás** |
| iOSProfileLaunch | Profilképernyő telepítése | iOS | **Mégse** |
| iOSProfileLaunch | Rákérdezés, hogy megbízik-e a profil forrásában az eszköz regisztrációjához | iOS | **Mégse** |
| iOSProfileLaunch | Profiltelepítési képernyő, amely a profil telepítésének befejeződéséig látható | iOS | Időtartam > 30 perc |
| AndroidPermissions | Eszközadminisztrátor aktiválása képernyő | Android | **Mégse** |
| AndroidPermissions | A hívások kezdeményezésének és kezelésének jóváhagyáskérésétől addig, amíg az eszközrendszergazda végre nem hajtja az **aktiválást** | Android | Időtartam > 30 perc |
| KnoxActivation | KLMS-ügynök aktiválása (csak Samsung) | Android| **Mégse** |
| KnoxActivation | KLMS-ügynök aktiválása a **megerősítésig** | Android | Időtartam > 30 perc|

#### <a name="terms-of-use-section"></a>Használati feltételek szakasz

| Művelet neve | Képernyő vagy folyamat | Platform | Műveletek |
| ---- |---- |---- |---- |
| TermsofUse | Használati feltételek (ha a rendszergazda konfigurálta) | iOS/Android | **Összes elutasítása** |
| TermsofUse | Használati feltételek megjelenítése az **Összes elfogadása** kiválasztásáig | iOS/Android | Időtartam > 30 perc |

#### <a name="complianceactivation-section"></a>Megfelelőség/aktiválás képernyő

| Művelet neve | Képernyő vagy folyamat | Platform | Műveletek |
| ---- |---- |---- |---- |
| Megfelelőség | Eszközmegfelelőség (ha a rendszergazda beállította) nem zöldként jelenik meg a regisztráció utáni hozzáférés-beállítás esetén| iOS/Android | **Postpone** |
| Megfelelőség | Az eszközmegfelelőség nem zöldként jelenik meg, amíg nem frissíti zöldként való megjelenítésre | iOS/Android | Időtartam > 30 perc |
| Aktiválás | Regisztrációaktiválás (ha a rendszergazda beállította) nem zöldként jelenik meg a hozzáférés beállításakor | iOS/Android | **Postpone** |
| Megfelelőség | Az eszközaktiválás nem zöldként jelenik meg, amíg nem frissíti zöldként való megjelenítésre | iOS/Android | Időtartam > 30 perc |

## <a name="next-steps"></a>További lépések

A nem teljes regisztráció díjait az ellenőrzés után áttekintheti a [regisztrálási lehetőségeket](enrollment-options.md) megtekintheti, ha bármely javítására beléptetési módosításokat végezheti el.

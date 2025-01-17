---
title: A JAMF Pro által küldött adatokat az Intune-nak küldi
titleSuffix: Microsoft Intune
description: Tekintse át azokat az adatokat, amelyeket a JAMF Pro küld Microsoft Intunenek, amikor a JAMF Pro-t integrálja a Mac-et az Intune-nal.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86f2f47322e668815d1ff37ce6c2de1e4d6cdc16
ms.sourcegitcommit: 99b74d7849fbfc8f5cf99cba33e858eeb9f537aa
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/31/2019
ms.locfileid: "68670896"
---
# <a name="data-jamf-pro-sends-to-intune"></a>A Jamf Pro által az Intune-ba küldött adatok

Ha a [JAMF Pro](https://www.jamf.com) használatával felügyeli a végfelhasználók Mac számítógépét az Intune-nal, a JAMF Pro rögzíti a felügyelt MacOS-eszközök leltározási adatait. A Jamf Pro a következő információkat továbbítja az Intune-nak:

* Azure AD-eszközazonosító
* JAMF eszközkészlet-állapot (a Jamf Pro szolgáltatásba az elmúlt 24 órán belül bejelentkezett számítógép eszközkészlet-állapota)
* Operációs rendszer verziója
* Azure AD-felhasználói azonosító
* Titkosított (FileVault 2)
* Forgalomirányító állapota
* Jelszó: Karakterkészletek minimális száma
* Jelszó lejárata (nap)
* Jelszó típusa – egyszerű, alfanumerikus, vagy ismeretlen
* Automatikus bejelentkezés tiltása
* PIN-kód minimális hossza
* Jelszó: az újrafelhasználásból kizárt korábbi jelszavak száma
* Rendszer sértetlenségének védelme
* Legutóbbi bejelentkezés
* Architektúra típusa
* Rendelkezésre álló RAM-tárhelyek
* Akkumulátor kapacitása
* Rendszerindító ROM
* Busz sebessége
* Gyorsítótár mérete
* Eszköz neve
* Csatlakozás tartományhoz
* Jamf-azonosító
* MAC-cím
* Fordítás
* Modell
* Modellazonosító
* Hálózati adapter sebessége
* Magok száma
* Processzorok száma
* OS
* Platform
* Processzor sebessége
* Processzor típusa
* Másodlagos MAC-cím
* Sorozatszám
* SMC verziója
* RAM összesen
* UDID
* Felhasználó e-mail-címe


A Jamf által felügyelt eszközöknek az Intune-konzolról történő eltávolításához a **Minden eszköz** nézetben kattintson a **Törlés** elemre. Az eszközök csoportos törlésére is van lehetőség: jelöljön ki több eszközt, és kattintson a **Törlés** elemre.

[A Jamf által felügyelt eszköz eltávolításáról a Jamf Pro dokumentációjában](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information) olvashat részletesebben. Ha további segítségre van szüksége, támogatási jegyet is küldhet a [Jamf támogatási szolgálatának](https://www.jamf.com/support/). 


---
title: "A regisztrált eszközök áttekintése a leltárfunkcióval | Microsoft Docs"
description: "Az Intune segítségével megtekintheti a felügyelt eszközök hardverinformációit."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 312911fe-b963-4949-9911-ae425e0590b2
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 3ae5809f8506e2255d9443d3587f2564bc863066
ms.lasthandoff: 12/10/2016


---

# <a name="understand-your-devices-with-inventory-in-microsoft-intune"></a>A regisztrált eszközök áttekintése a Microsoft Intune leltárfunkciójával

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

A Microsoft Intune leltárfunkcióját használva leltár készíthető a regisztrált eszközökről, illetve az Intune ügyfélszoftvert futtató Windows-számítógépekről.
Az Intune általában 7 naponta készít leltárt a felügyelt eszközökről. Emiatt előfordulhat, hogy a jelentésekben késve jelenik meg az eszközök nemrégiben történt módosítása, pl. egy eszköz átnevezése vagy a szabad tárhelye mennyiségének változása.

## <a name="whats-collected-from-enrolled-devices"></a>Milyen adatok gyűjthetők be a regisztrált eszközökről?
A mobileszközök által összegyűjtött leltáradatok megtekintéséhez futtassa a [Mobileszközkészlet-jelentések](understand-microsoft-intune-operations-by-using-reports.md) funkciót. Az Intune az alábbi táblázatban szereplő leltáradatokat gyűjti össze a regisztrált eszközökről:

|Tulajdonság|Gyűjtő eszköz|
|------------|-----------------------|
|**Név**|Az összes eszköz|
|**Operációs rendszer**|Az összes eszköz|
|**Gyártó**|Az összes eszköz|
|**Modell**|Az összes eszköz|
|**Felügyeleti csatorna**|Az összes eszköz|
|**Az AAD-ben regisztrált**|Mac OS X kivételével minden eszköz|
|**Megfelelő:**|Az összes eszköz|
|**EAS engedélyezve**|Mac OS X kivételével minden eszköz|
|**EAS-aktiválási azonosító**|Mac OS X kivételével minden eszköz|
|**EAS-aktiválás ideje**|Mac OS X kivételével minden eszköz|
|**Kezelés állapota**|Az összes eszköz|
|**E-mail-cím**|Az összes eszköz|
|**Exchange ActiveSync-azonosító**|Az összes eszköz|
|**Jailbreakelt vagy rootolt**|Csak iOS- és Android-eszközök|
|**Egyedi eszközazonosító**|Az Exchange ActiveSync kivételével minden eszköz|
|**Sorozatszám**|iOS-, Mac OS X-, Android-, Windows 8.1- és asztali Windows 10-eszközök|
|**Teljes tárterület**|iOS-, Mac OS X-, Windows 8.1-, asztali és mobil Windows 10-eszközök|
|**Szabad tárterület**|iOS-, Mac OS X-, Windows 8.1- és asztali Windows 10-eszközök|
|**Telefonszám**<br>A vállalati eszközként besorolt telefonokat a teljes telefonszámuk jelöli (például egy mobileszközkészlet-jelentés futtatásakor). A BYOD-eszközök telefonszámai &#42; karakterekkel maszkolva, csak az utolsó négy számjegyükkel jelennek meg.|iOS, Android és Windows Phone rendszerű eszközök|
|**IMEI**|Exchange ActiveSync-, iOS-, Android- és Windows Phone-eszközök|
|**MEID**<br>Mobilkészülék-azonosító szám|Csak iOS-eszközök|
|**Wi-Fi MAC-cím**|Az Exchange ActiveSync kivételével minden eszköz|
|**Előfizető szolgáltatója**|Csak iOS- és Android-eszközök|
|**Mobiltechnológia**|Csak iOS- és Android-eszközök|
|**Felügyelt**|Csak iOS-eszközök|
|**Aktiválási zár állapota**|Csak iOS-eszközök|
|**Beléptetés dátuma**|Az összes eszköz|
|**Legutóbbi frissítés**|Az összes eszköz|
|**Ethernet MAC-cím**|Csak Mac OS X-eszközök|
|**Aktiválási zár engedélyezve**|Csak iOS-eszközök|
|**Titkosítás engedélyezve**|Az összes eszköz|

## <a name="whats-collected-from-windows-pcs"></a>A Windows rendszerű számítógépekről gyűjtött adatok
> [!IMPORTANT]
> Ez a szakasz csak az Intune Windows PC-ügyfélszoftvert futtató Windows rendszerű számítógépekre vonatkozik.

A windowsos számítógépek által összegyűjtött leltáradatok megtekintéséhez futtassa a [Számítógépleltár-jelentések](understand-microsoft-intune-operations-by-using-reports.md) funkciót. Az Intune az alábbi táblázatban szereplő leltáradatokat gyűjti össze a Windows rendszerű számítógépekről:

-   **Név**

-   **Ház típusa**

-   **Gyártó**

-   **Modell**

-   **Operációs rendszer**

-   **TPM-verzió**

-   **Teljes lemezterület**

-   **Felhasznált lemezterület**

-   **Szabad lemezterület**

-   **Az operációs rendszer lemezének neve**

-   **Hely az operációs rendszer lemezén**

-   **Szabad hely az operációs rendszer lemezén**

-   **Fizikai memória**

-   **A processzor neve**

-   **Processzorarchitektúra**

-   **Processzor sebessége**

-   **IP-cím**

-   **Sorozatszám**

-   **Utolsó bejelentkező felhasználó**

-   **Hozzárendelt felhasználó**

-   **Legutóbbi frissítés**

<!-- this section below belongs in the planning journey
### See Also
[Monitoring and reports with Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)
-->

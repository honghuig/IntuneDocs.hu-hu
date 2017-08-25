---
title: "Mobilalkalmazás-felügyelet (MAM) | Microsoft Docs"
description: "Az Intune-adattárház API-ban található entitásgyűjtemények mobilalkalmazásfelügyelet-kategóriájára vonatkozó referencia-témakör."
keywords: "Intune-adattárház"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 44358d68a653760804f11668ab64d30ebf7ae9eb
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/04/2017
---
# <a name="reference-for-mobile-app-management-mam-entities"></a>Mobilalkalmazás-felügyelet (MAM) típusú entitások referenciája

A **Mobilalkalmazás-felügyelet** kategória a következő mobilalkalmazásokkal kapcsolatos entitásokat tartalmazza:

  -  Alkalmazások
  -  példányszám
  -  Bejelentkezési állapot
  -  Állapotadatok
  -  Szabályzat állapota
  -  Beléptetés állapota
  -  Platformtípusok

## <a name="mamapplication"></a>MAMApplication

A **MamApplication** entitás azokat az üzletági alkalmazásokat sorolja fel, amelyek felügyelete a Mobilalkalmazás-felügyelet használatával történik és nincsenek beléptetve a vállalat rendszerébe.

| Tulajdonság | Leírás | Példa |
|---------|------------|--------|
| ApplicationKey |A MAM-alkalmazás egyedi azonosítója az adattárházban |123 |
| ApplicationName |A MAM-alkalmazás neve |"Word" |
| ApplicationId |A MAM-alkalmazás azonosítója |b66bc706-ffff-7437-0340-032819502773 |
| IsDeleted |Jelzi, hogy frissítve lett-e ez a MAM-alkalmazásrekord. Igaz – a MAM-alkalmazáshoz új, frissített mezőkből álló rekord tartozik a táblában. Hamis – a MAM-alkalmazás legfrissebb rekordja. |Igaz/hamis |
| StartDateInclusiveUTC |A MAM-alkalmazás adattárházban történt létrehozásának dátuma és időpontja (UTC) |2016.11.23. 12:00:00 |
| DeletedDateUTC |Az IsDeleted paraméter igaz értékre történt módosulásának dátuma és időpontja (UTC) |2016.11.23. 12:00:00 |
| RowLastModifiedDateTimeUTC |A MAM-alkalmazás adattárházban történt utolsó módosításának dátuma és időpontja (UTC) |2016.11.23. 12:00:00 |

## <a name="mamapplicationinstance"></a>MamApplicationInstance

A **MamApplicationInstance** entitás a felügyelt Mobilalkalmazás-felügyeleti (MAM) alkalmazásokat sorolja fel felhasználóként és eszközönként egy példányban. Az entitásban felsorolt összes felhasználó és eszköz védelem alatt áll, vagyis legalább egy MAM-szabályzat hozzájuk van rendelve.

| Tulajdonság | Leírás | Példa |
|---------|------------|--------|
| ApplicationInstanceKey |A MAM-alkalmazáspéldány egyedi azonosítója az adattárházban – helyettes kulcs |123 |
| UserId |A felhasználó azonosítója aki ezt a MAM-alkalmazást telepítette |b66bc706-ffff-7437-0340-032819502773 |
| ApplicationInstanceId |A MAM-alkalmazáspéldány egyedi azonosítója – hasonló az ApplicationInstanceKey-hez, de az azonosító természetes kulcs |b66bc706-ffff-7437-0340-032819502773 |
| ApplicationId |A MAM-alkalmazás azonosítója |com.microsoft.groupies-daily.<IOS> |
| ApplicationVersion |A MAM-alkalmazás verziószáma |2 |
| CreatedDate |A MAM-alkalmazáspéldány rekordjának létrehozási dátuma. Az érték lehet null is. |2016.11.23. 12:00:00 |
| Platform |Az eszköz platformja, amelyen ez a MAM-alkalmazás telepítve van |2 |
| PlatformVersion |Az eszköz platformjának verziója, amelyen ez a MAM-alkalmazás telepítve van |2.2 |
| SdkVersion |A MAM-SDK verziója, amellyel az adott MAM-alkalmazást becsomagolták |3.2 |
| DeviceId |Az eszköz azonosítója, amelyen ez a MAM-alkalmazás telepítve van |b66bc706-ffff-7437-0340-032819502773 |
| DeviceName |Az eszköz neve, amelyen ez a MAM-alkalmazás telepítve van |"MyDevice" |
| IsDeleted |Jelzi, hogy frissítve lett-e ez a MAM-alkalmazásrekord. Igaz – a MAM-alkalmazáspéldányhoz új, frissített mezőkből álló rekord tartozik a táblában. Hamis – a MAM-alkalmazás legfrissebb rekordja. |Igaz/hamis |
| StartDateInclusiveUTC |A MAM-alkalmazáspéldány adattárházban történt létrehozásának dátuma és időpontja (UTC) |2016.11.23. 12:00:00 |
| DeletedDateUTC |Az IsDeleted paraméter igaz értékre történt módosulásának dátuma és időpontja (UTC) |2016.11.23. 12:00:00 |
| RowLastModifiedDateTimeUTC |A MAM-alkalmazáspéldány adattárházban történt utolsó módosításának dátuma és időpontja (UTC) |2016.11.23. 12:00:00 |

## <a name="mamcheckin"></a>MamCheckin

A **MamCheckin** entitás a MAM-alkalmazáspéldány Intune szolgáltatásba történő legutóbbi bejelentkezése során begyűjtött adatokat jelöli. 

> [!Note]  
> Ha az alkalmazáspéldány naponta többször is bejelentkezik, azokat az adattárház egyetlen bejelentkezésként tárolja.

| Tulajdonság | Leírás | Példa |
|---------|------------|--------|
| DateKey |A dátumkulcs azt jelzi, hogy az adattárházban mikor lett rögzítve a MAM-alkalmazás bejelentkezése | 20160703 |
| ApplicationInstanceKey |A MAM-alkalmazás bejelentkezéséhez társított alkalmazáspéldány kulcsa |1900.2.5. 12:00:00 |
| UserKey |A MAM-alkalmazás bejelentkezéséhez társított felhasználó kulcsa |1900.12.1. 12:00:00 |
| ApplicationKey |A bejelentkező MAM-alkalmazás kulcsa |1900.10.1. 12:00:00 |
| DeviceHealthKey |A MAM-alkalmazás bejelentkezéséhez társított DeviceHealth kulcsa |1900.2.1. 12:00:00 |
| PlatformKey |A MAM-alkalmazás bejelentkezéséhez társított eszköz platformját jelöli |1900.1.1. 12:00:00 |
| EffectiveAppliedPolicyKey |A bejelentkező MAM-alkalmazáshoz társított érvényben levő hozzárendelt szabályzatot jelöli. Az érvényben levő hozzárendelt szabályzat az adott alkalmazásra és felhasználóra vonatkozó szabályzatok összevonásának eredménye. |1900.2.5. 12:00:00 |
| LastCheckInDate |A MAM-alkalmazás utolsó bejelentkezésének dátuma és időpontja. Az érték lehet null is. |2016.11.23. 12:00:00 |

## <a name="mamdevicehealth"></a>MamDeviceHealth

A **MamDeviceHealth** entitás azokat az eszközöket jelöli, amelyekhez mobilalkalmazás-felügyeleti szabályzatok vannak rendelve, beleértve a jailbreakelt eszközöket is.

| Tulajdonság | Leírás | Példa |
|---------|------------|--------|
| DeviceHealthKey |Az eszköz és a hozzá tartozó eszközállapot egyedi azonosítója az adattárházban – helyettes kulcs |1900.1.1. 12:00:00 |
| DeviceHealth |Az eszköz és a hozzá tartozó eszközállapot egyedi azonosítója – hasonló a DeviceHealthKey-hez, de az azonosító természetes kulcs |1900.1.1. 12:00:00 |
| DeviceHealthName |Az eszköz állapotát jelöli. Not available – nincs információ az eszközről. Healthy – az eszköz nem jailbreakelt. Unhealthy – az eszköz jailbreakelt. |Not Available Healthy Unhealthy |
| RowLastModifiedDateTimeUTC |Az adott MAM-eszközállapot adattárházban történt utolsó módosításának dátuma és időpontja (UTC) |2016.11.23. 12:00:00 |

## <a name="mameffectivepolicy"></a>MamEffectivePolicy

A **MamEffectivePolicy** entitás a vállalatnál alkalmazott összes érvényben levő mobilalkalmazás-felügyeleti szabályzatot sorolja fel. Az érvényben levő hozzárendelt szabályzat az adott alkalmazásra és felhasználóra vonatkozó szabályzatok összevonásának eredménye.

| Tulajdonság | Leírás | Példa |
|---------|------------|--------|
| EffectivePolicyKey |Az érvényben levő MAM-szabályzat egyedi azonosítója az adattárházban |2 |
| RealPolicyKey |A MAM-szabályzat informatikai szakember által létrehozott egyedi azonosítója. |1 |
| RowCreatedDateTimeUtc |Az érvényben levő MAM-szabályzat adattárházban történt létrehozásának dátuma és időpontja (UTC). |2016.11.23. 12:00:00 |

## <a name="mamglobalapplication"></a>MamGlobalApplication

A **MamGlobalApplication** entitás azokat az áruházbeli alkalmazásokat sorolja fel, amelyek felügyelete a Mobilalkalmazás-felügyelet használatával történik és nincsenek beléptetve a vállalat rendszerébe.

| Tulajdonság | Leírás | Példa |
|---------|------------|--------|
| ApplicationKey |Az áruházbeli alkalmazás egyedi azonosítója az adattárházban, más néven a helyettes kulcs. |123 |
| ApplicationId |Az áruházbeli alkalmazás egyedi azonosítója. Az azonosító hasonló az ApplicationKey-hez, de természetes kulcs. |com.microsoft.skydrive.<ios> |
| ApplicationName |A MAM-beli globális alkalmazásnév. |SkyDrive |
| RowLastModifiedDateTimeUTC |Az adott MAM globális alkalmazás adattárházban történt utolsó módosításának dátuma és időpontja (UTC). |2016.11.23. 12:00:00 |

## <a name="mamplatform"></a>MamPlatform

A **MamPlatform** entitás azoknak a platformoknak a nevét és típusát sorolja fel, amelyeken telepítettek MAM-alkalmazást.

| Tulajdonság | Leírás | Példa |
|---------|------------|--------|
| PlatformKey |A platform egyedi azonosítója az adattárházban – helyettes kulcs |123 |
| Platform |A platform egyedi azonosítója – a PlatformKey-hez hasonló, de természetes kulcs |123 |
| PlatformName |A platform neve |Not Available None Windows IOS Android |
| RowLastModifiedDateTimeUTC |A platform adattárházban történt utolsó módosításának dátuma és időpontja (UTC) |2016.11.23. 12:00:00 |
---
title: Szabályzat típusú entitások referenciája
titleSuffix: Microsoft Intune
description: Az Intune-adattárház API-ban található entitásgyűjtemények szabályzatkategóriájára vonatkozó referencia-témakör.
keywords: Intune-adattárház
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9f834057e95058634020fc955ced013d32b68a9
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882558"
---
# <a name="reference-for-policy-entities"></a>Szabályzat típusú entitások referenciája

A **Szabályzat**kategória mobileszközökhöz tartozó entitásokat tartalmaz, amelyek információt gyűjtenek, például:

- Az eszköz- és alkalmazáskonfigurációs profilok, valamint a megfelelőségi szabályzatok készlete  
- A sikeres, függő, sikertelen vagy hibás állapotú eszközök száma naponta  
- A sikeres, függő, sikertelen vagy hibás állapotú felhasználók száma naponta  
- A sikeres, függő, sikertelen vagy hibás állapotú eszközök száma összesen  

## <a name="policy"></a>Házirend

A **Szabályzat** entitás eszköz- és alkalmazáskonfigurációs profilokat, valamint megfelelőségi szabályzatokat tartalmaz. A szabályzatokat a Mobileszköz-kezelési (MDM) megoldás segítségével rendelheti hozzá a vállalat valamely csoportjához.

| Tulajdonság  | Leírás | Példa |
|---------|------------|--------|
| PolicyKey |A szabályzat adattárházban való jelölésére szolgáló egyedi kulcs. |123 |
| PolicyId |A szabályzat egyedi azonosítója az adattárházban. |b66bc706-ffff-7437-0340-032819502773 |
| PolicyName |A szabályzat neve. |„Windows 10 Baseline” |
| PolicyVersion |A szabályzat verziója. A szabályzat szerkesztésekor vagy módosításakor új verzió jön létre. |1, 2, 3 |
| IsDeleted |Jelzi, hogy frissítve lett-e a szabályzatrekord.  <br>Igaz – a szabályzat új, frissített mezőkkel ellátott rekorddal rendelkezik. <br>Hamis – a szabályzat legújabb rekordja. |Igaz/hamis |
| StartDateInclusiveUTC |A szabályzat adattárházban történt létrehozásának dátuma és időpontja (UTC). |2016.11.23. 12:00:00 |
| DeletedDateUTC |Az IsDeleted paraméter True (Igaz) értékre módosulásának dátuma és időpontja (UTC). |2016.11.23. 12:00:00 |
| RowLastModifiedDateTimeUTC |A szabályzat adattárházban történt utolsó módosításának dátuma és időpontja (UTC). |2016.11.23. 12:00:00 |

## <a name="policytype"></a>PolicyType

A **PolicyType** entitás az eszköz- és alkalmazáskonfigurációs profilok, valamint a megfelelőségi szabályzatok típusait tartalmazza. A szabályzatokat a Mobileszköz-kezelési (MDM) megoldás segítségével rendelheti hozzá a vállalat valamely csoportjához.

| Tulajdonság  | Leírás | Példa |
|---------|------------|--------|
| PolicyTypeId |A szabályzat egyedi azonosítója a forrásrendszerben. |123 |
| PolicyTypeKey |A szabályzat egyedi azonosítója az adattárházban. |1 |
| PolicyTypeName |A szabályzattípus neve. |A Windows 10-re vonatkozó megfelelőségi szabályzat. |

## <a name="deviceconfiguration"></a>DeviceConfiguration

A **DeviceConfigurationProfileDeviceActivity** entitás naponta listázza a sikeres, függő, sikertelen vagy hibás állapotú **eszközök** számát. A szám az entitáshoz rendelt eszközkonfigurációs profilokat jelöli. Ha például egy **eszköz** sikeres állapotban van az összes hozzárendelt házirend esetében, az adott napra a sikeres számlálót eggyel növeli. Ha az adott eszköz két hozzárendelt profillal rendelkezik, amelyek közül az egyik sikeres, míg a másik hibás állapotú, akkor az entitás növeli az értéket a sikeres állapotot jelző számlálón, és hibás állapotba helyezi az eszközt. Az entitás azt sorolja fel, hogy hány eszköz van az egyes állapotokban az elmúlt 30 napon belüli adott napon.

| Tulajdonság  | Leírás | Példa |
|---------|------------|--------|
| DateKey |A dátumkulcs azt jelzi, hogy az adattárházban mikor lett rögzítve az eszközkonfigurációs profil bejelentkezése. |20160703 |
| Függőben lévő |A függő állapotú egyedi eszközök száma. |123 |
| Sikerült |A sikeres állapotú egyedi eszközök száma. |12 |
| Hiba |A hibás állapotú egyedi eszközök száma. |10 |
| Sikertelen |A sikertelen állapotú egyedi eszközök száma. |2 |

A **DeviceConfigurationProfileUserActivity** entitás naponta listázza a sikeres, függő, sikertelen vagy hibás állapotú **felhasználók** számát. A szám az entitáshoz rendelt eszközkonfigurációs profilokat jelöli. Ha például egy **felhasználó** az összes hozzárendelt szabályzat esetében sikeres állapotú, akkor az adott napra a sikeres számlálót eggyel feljebb helyezi. Ha az adott felhasználó két hozzárendelt profillal rendelkezik, amelyek közül az egyik sikeres, míg a másik hibás állapotú, akkor a felhasználót hibás állapotúnak számítjuk.  A **DeviceConfigurationProfileUserActivity** entitás azt sorolja fel, hogy hány felhasználó van az egyes állapotokban az elmúlt 30 napon belüli adott napon.

| Tulajdonság  | Leírás | Példa |
|---------|------------|--------|
| DateKey |A dátumkulcs azt jelzi, hogy az adattárházban mikor lett rögzítve az eszközkonfigurációs profil bejelentkezése. |20160703 |
| Függőben lévő |A függő állapotú egyedi felhasználók száma. |123 |
| Sikerült |A sikeres állapotú egyedi felhasználók száma. |12 |
| Hiba |A hibás állapotú egyedi felhasználók száma. |10 |
| Sikertelen |A sikertelen állapotú egyedi felhasználók száma. |2 |

## <a name="policytypeactivity"></a>PolicyTypeActivity

A **PolicyTypeActivity** entitás a sikeres, függő, sikertelen vagy hibás állapotú eszközök számát sorolja fel összesítve. Ezeket az állapotokat az adott eszköz-, illetve alkalmazáskonfigurációs profilra, valamint megfelelőségi szabályzatra vonatkozóan ismerteti.

| Tulajdonság  | Leírás | Példa |
|---------|------------|--------|
| DateKey |A dátumkulcs azt jelzi, hogy az adattárházban mikor lett rögzítve az eszközkonfigurációs profil bejelentkezése. |20160703 |
| PolicyKey |Szabályzatkulcs, amely összekapcsolható a szabályzattal a policyName paraméter lekérése érdekében. |Windows 10 baseline |
| PolicyTypeKey |Szabályzatkulcs típusa, amely összekapcsolható a szabályzattípussal a szabályzattípus nevének lekérése érdekében. |Windows 10-es megfelelőségi szabályzat |
| Függőben lévő |A függő állapotú egyedi eszközök száma. |123 |
| Sikerült |A sikeres állapotú egyedi eszközök száma. |12 |
| Hiba |A hibás állapotú egyedi eszközök száma. |10 |
| Sikertelen |A sikertelen állapotú egyedi eszközök száma. |2 |

## <a name="compliance-policy"></a>Megfelelőségi szabályzat

A Megfelelőségi szabályzat API-referencia olyan entitásokat tartalmaz, amelyek információval szolgálnak az eszközökhöz rendelt megfelelőségi szabályzatok állapotáról.

### <a name="compliancepolicystatusdeviceactivities"></a>CompliancePolicyStatusDeviceActivities

Az alábbi táblázatban foglaltuk össze az eszközökhöz rendelt megfelelőségi szabályzatok hozzárendelési állapotát. A lista felsorolja az egyes megfelelőségi állapotokban található eszközök számát is.


|Tulajdonság     |Leírás  |Példa  |
|---------|---------|---------|
|DateKey  |A megfelelőségi szabályzat összefoglalójának létrehozási dátumkulcsa.|20161204 |
|Ismeretlen  |Azoknak az eszközöknek a száma, amelyek offline állapotban vannak, vagy valamilyen más okból nem sikerült kapcsolatba lépniük az Intune-nal vagy az Azure AD-vel. |5|
|Nem alkalmazható      |Azoknak az eszközöknek a száma, amelyeknél a rendszergazda által meghatározott eszközmegfelelőségi szabályzatok nem alkalmazhatók.|201 |
|Compliant (Megfelelő)      |Azoknak az eszközöknek a száma, amelyek megfelelnek a rendszergazda által meghatározott egy vagy több eszközmegfelelőségi szabályzatnak. |4083 |
|InGracePeriod      |Azoknak az eszközöknek a száma, amelyek nem megfelelőek, de a rendszergazda által meghatározott türelmi időszakban vannak. |57|
|Nem megfelelő      |Azoknak az eszköznek a száma, amelyek nem felelnek meg a rendszergazda által meghatározott egy vagy több eszközmegfelelőségi szabályzatnak, vagy a felhasználó nem a rendszergazda által meghatározott szabályzatoknak megfelelően járt el.|43 |
|Hiba      |Azoknak az eszközöknek a száma, amelyeknek nem sikerült kapcsolatba lépniük az Intune-nal vagy az Azure AD-vel, és hibaüzenetet küldtek. |3|

### <a name="compliancepolicystatusdeviceperpolicyactivities"></a>CompliancePolicyStatusDevicePerPolicyActivities 

Az alábbi táblázatban foglaltuk össze az eszközökhöz rendelt megfelelőségi szabályzatok hozzárendelési állapotát szabályzatonként és szabályzattípusonként. A lista szabályzatonként felsorolja az egyes megfelelőségi állapotokban található eszközök számát.



|Tulajdonság  |Leírás  |Példa  |
|---------|---------|---------|
|DateKey  |A megfelelőségi szabályzat összefoglalójának létrehozási dátumkulcsa.|20161219|
|PolicyKey     |Annak a megfelelőségi szabályzatnak a kulcsa, amelyhez az összefoglalás készült. |10178 |
|PolicyPlatformKey      |Annak a megfelelőségi szabályzathoz tartozó platformnak a kulcsa, amelyhez az összefoglalás készült.|5|
|Ismeretlen     |Azoknak az eszközöknek a száma, amelyek offline állapotban vannak, vagy valamilyen más okból nem sikerült kapcsolatba lépniük az Intune-nal vagy az Azure AD-vel.|13|
|Nem alkalmazható     |Azoknak az eszközöknek a száma, amelyeknél a rendszergazda által meghatározott eszközmegfelelőségi szabályzatok nem alkalmazhatók.|3|
|Compliant (Megfelelő)      |Azoknak az eszközöknek a száma, amelyek megfelelnek a rendszergazda által meghatározott egy vagy több eszközmegfelelőségi szabályzatnak. |45|
|Türelmi időszakban      |Azoknak az eszközöknek a száma, amelyek nem megfelelőek, de a rendszergazda által meghatározott türelmi időszakban vannak. |3|
|Nem megfelelő      |Azoknak az eszköznek a száma, amelyek nem felelnek meg a rendszergazda által meghatározott egy vagy több eszközmegfelelőségi szabályzatnak, vagy a felhasználó nem a rendszergazda által meghatározott szabályzatoknak megfelelően járt el.|7|
|Hiba      |Azoknak az eszközöknek a száma, amelyeknek nem sikerült kapcsolatba lépniük az Intune-nal vagy az Azure AD-vel, és hibaüzenetet küldtek. |3|

### <a name="policyplatformtypes"></a>PolicyPlatformTypes

Az alábbi táblázat felsorolja minden hozzárendelt szabályzat platformtípusát. A táblázat nem sorolja fel azokat a szabályzatplatform-típusokat, amelyeket még soha nem rendeltek hozzá eszközökhöz.


|Tulajdonság  |Leírás  |Példa  |
|---------|---------|---------|
|PolicyPlatformTypeKey      |A szabályzatplatform típusának egyedi kulcsa. |20170519 |
|PolicyPlatformTypeId      |A szabályzatplatform típusának egyedi azonosítója.|1|
|PolicyPlatformTypeName      |A szabályzatplatform típusának neve.|AndroidForWork |

### <a name="policydeviceactivity"></a>PolicyDeviceActivity

Az alábbi táblázat a sikeres, függő, sikertelen vagy hibás állapotú eszközök napi számát tartalmazza. A szám a szabályzattípus-profilok szerinti adatot jelöli. Ha például az adott eszköz valamennyi hozzárendelt szabályzata tekintetében sikeres állapotú, akkor az entitás azon a napon eggyel növeli az értéket a sikeres állapotot jelző számlálón. Ha az adott eszköz két hozzárendelt profillal rendelkezik, amelyek közül az egyik sikeres, míg a másik hibás állapotú, akkor az entitás növeli az értéket a sikeres állapotot jelző számlálón, és hibás állapotba helyezi az eszközt. A PolicyDeviceActivity entitás azt sorolja fel, hogy hány eszköz van az egyes állapotokban az elmúlt 30 napon belüli adott napon.

|Tulajdonság  |Leírás  |Példa  |
|---------|---------|---------|
|DateKey|A dátumkulcs azt jelzi, hogy az adattárházban mikor lett rögzítve az eszközkonfigurációs profil bejelentkezése.|20160703|
|Függőben lévő|A függő állapotú egyedi eszközök száma.|123|
|Sikerült|A sikeres állapotú egyedi eszközök száma.|12|
PolicyKey|Szabályzatkulcs, amely összekapcsolható a szabályzattal a policyName paraméter lekérése érdekében.|Windows 10 baseline|
|Hiba|A hibás állapotú egyedi eszközök száma.|10|
|Sikertelen|A sikertelen állapotú egyedi eszközök száma.|2|

### <a name="policyuseractivity"></a>PolicyUserActivity 

Az alábbi táblázat a sikeres, függő, sikertelen vagy hibás állapotú felhasználók napi számát tartalmazza. A szám a szabályzattípus-profilok szerinti adatot jelöli. Ha például az egyik felhasználó valamennyi hozzárendelt szabályzata tekintetében sikeres állapotú, akkor az entitás azon a napon eggyel növeli az értéket a sikeres állapotot jelző számlálón. Ha az adott felhasználó két hozzárendelt profillal rendelkezik, amelyek közül az egyik sikeres, míg a másik hibás állapotú, akkor a felhasználót hibás állapotúnak számítjuk. A PolicyUserActivity entitás azt sorolja fel, hogy hány felhasználó van az egyes állapotokban az elmúlt 30 napon belüli adott napon.


| Tulajdonság  |                                         Leírás                                         |       Példa       |
|-----------|---------------------------------------------------------------------------------------------|---------------------|
|  DateKey  | A dátumkulcs azt jelzi, hogy az adattárházban mikor lett rögzítve az eszközkonfigurációs profil bejelentkezése. |      20160703       |
|  Függőben lévő  |                         A függő állapotú egyedi eszközök száma.                          |         123         |
| Sikerült |                         A sikeres állapotú egyedi eszközök száma.                          |         12          |
| PolicyKey |                Szabályzatkulcs, amely összekapcsolható a szabályzattal a policyName paraméter lekérése érdekében.                 | Windows 10 baseline |
|   Hiba   |                          A hibás állapotú egyedi eszközök száma.                           |         10          |


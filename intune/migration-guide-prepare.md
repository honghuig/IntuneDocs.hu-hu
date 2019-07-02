---
title: Az Intune előkészítése mobileszköz-kezeléshez
titleSuffix: Microsoft Intune
description: A Microsoft Intune-ra migrálás előtt mérje fel az üzleti és technikai követelményeket.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 58591442-6606-4f39-a06b-f17a1f25af25
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4bd03075e6088b4cf06237429a723e93e87029fd
ms.sourcegitcommit: 116ef72b9da4d114782d4b8dd9f57556c9b01511
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/01/2019
ms.locfileid: "67494592"
---
# <a name="phase-1-prepare-microsoft-intune-for-mobile-device-management-mdm"></a>1\. fázis: A Microsoft Intune előkészítése a mobileszköz-felügyelet (MDM)

Mielőtt részletesen rátérnénk az Intune beállítására, tekintsük át a szervezet mobileszköz-felügyeleti követelményeit. Érdemes lehet a jelenlegi MDM-szolgáltatóban jelentéseket készíteni az aktív felhasználókról, ezáltal azonosítani a kritikus felhasználói csoportokat, Majd elkezdeni megválaszolni a kérdéseket a [MDM-követelmények felmérése](migration-guide-prepare.md#assess-mdm-requirements) szakaszban.

## <a name="assess-mdm-requirements"></a>Az MDM-követelmények felmérése

### <a name="what-kinds-of-devices-do-you-need-to-manage"></a>Milyen típusú eszközök felügyeletére van szükség?

-   Mely [platformokat](supported-devices-browsers.md) kell támogatni?

-   A támogatandó eszközök vállalati vagy személyes tulajdonban vannak?

-   Milyen a hálózati kapcsolat? Wi-Fi, mobil, VPN?

### <a name="what-do-your-users-need-to-do-on-managed-devices"></a>Mire van szükségük a felügyelt eszközök felhasználóinak?

-   Kell-e alkalmazásokat telepíteni a végfelhasználók számára?

-   Használnak-e egyéni üzletági alkalmazásokat? Vagy csak a nyilvános áruházakban elérhetőket?

-   Szükség van-e email-fiókok beállítására?

### <a name="what-kinds-of-users"></a>Milyen típusú felhasználói vannak?

-   Hány felhasználó használ majd egy eszközt?

-   Milyen használati feltételekre van szükség?

    -   Ebben a kérdésben mindenképp időben kérje a jogi osztály segítségét.
    -   Milyen honosításra van szükség?

-   Jártasak-e a felhasználók a technológia és általában a számítástechnika terén?

### <a name="what-is-your-device-security-policy"></a>Milyen eszközbiztonsági szabályzat van érvényben?

- Szükséges-e eszközszintű titkosítás?

- Mi az eszközök aktuális jelszavainak/PIN-kódjainak hossza?

- Szükség van-e eszközfunkciók letiltására vagy bizonyos fajta eszközműködés korlátozására? Az eszközkonfigurációs profilokkal számos platformspecifikus beállítást szabályozhat:
    - Kamera letiltása
    - Egyalkalmazásos mód<br/>

- Milyen hitelesítés támogatása szükséges? Ha tanúsítványalapú hitelesítésre van szükség, milyen fajta tanúsítványokat kell létrehozni?
  - Az Intune-nal erőforrás-hozzáférési szabályzatokban használható tanúsítványokat hozhat létre a regisztrált eszközökhöz.
  -   Milyen típusú nyilvános kulcsú infrastruktúra (PKI) támogatása szükséges?
  <br></br>
- Van-e szükség virtuális magánhálózat (VPN) támogatására eszköz- vagy alkalmazásszinten?

  -   Az Intune-nal külső VPN-szolgáltatókhoz is lehet VPN-konfigurációkat létrehozni.
  <br/><br/>
- Lehet-e átmeneti kivételeket tenni bizonyos követelmények alól az üzemszünet elkerülése érdekében? Vagy a hozzáférést kapó eszközöknek mindig meg kell felelniük az összes biztonsági követelménynek?

## <a name="next-steps"></a>További lépések
Ha kíváncsi, hogyan mérték fel egyes cégek saját mobileszköz-felügyeleti követelményeiket, tekintse meg ezeket a különféle iparágakból származó [esettanulmányokat](https://customers.microsoft.com/story/mwh-global-now-part-of-stantec-secures-mobile-devices-with-intune).

Az [Intune alapszintű beállításainak áttekintése](migration-guide-setup.md).

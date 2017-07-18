---
title: "Az Intune előkészítése mobileszköz-kezeléshez"
description: "Ez a cikk segítséget nyújt az olvasónak az Intune-migráció előtt felmérni az üzleti és műszaki követelményeket."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 58591442-6606-4f39-a06b-f17a1f25af25
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 65e3bb4b6a4e6e8dcfa1dd16738ae47758f4fb9b
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/01/2017
---
# <a name="phase-1-prepare-intune-for-mobile-device-management-mdm"></a>1. fázis: az Intune előkészítése a mobileszköz-felügyeletre (MDM)

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

Mielőtt részletesen rátérnénk az Intune beállítására, tekintsük át a szervezet mobileszköz-felügyeleti követelményeit. Érdemes lehet a jelenlegi MDM-szolgáltatóban jelentéseket készíteni az aktív felhasználókról, ezáltal azonosítani a kritikus felhasználói csoportokat, majd elkezdeni megválaszolni [Az MDM-követelmények felmérése](migration-guide-prepare.md#assess-mdm-requirements) című szakaszban szereplő kérdéseket.

## <a name="assess-mdm-requirements"></a>Az MDM-követelmények felmérése

### <a name="what-kinds-of-devices-do-you-need-to-manage"></a>Milyen típusú eszközök felügyeletére van szükség?

-   Mely [platformokat](/intune-classic/get-started/supported-mobile-devices-and-computers) kell támogatni?

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

-   Szükséges-e eszközszintű titkosítás?

-   Van-e megszabott hossza az eszközök jelszavainak/PIN-kódjainak?

-   Szükség van-e eszközfunkciók letiltására vagy bizonyos fajta eszközműködés korlátozására?

    -   Eszközkonfigurációs profilokkal számos platformspecifikus beállítást (például kamera letiltása, egyalkalmazásos mód stb.) lehet szabályozni.
<br></br>
-   Milyen hitelesítés támogatása szükséges?

    -   Ha tanúsítványalapú hitelesítésre van szükség, milyen fajta tanúsítványokat kell létrehozni?

        -   Az Intune-nal erőforrás-hozzáférési szabályzatokban használható tanúsítványokat hozhat létre a regisztrált eszközökhöz.
<br></br>
    -   Milyen típusú nyilvános kulcsú infrastruktúra (PKI) támogatása szükséges?
<br></br>
-   Van-e szükség virtuális magánhálózat (VPN) támogatására eszköz- vagy alkalmazásszinten?

    -   Az Intune-nal külső VPN-szolgáltatókhoz is lehet VPN-konfigurációkat létrehozni.
<br></br>
-   Lehet-e átmeneti kivételeket tenni bizonyos követelmények alól az üzemszünet elkerülése érdekében? Vagy a hozzáférést kapó eszközöknek mindig meg kell felelniük az összes biztonsági követelménynek?

## <a name="additional-information"></a>További információ

-   Részletesebb példákat talál ezekben a különféle iparágakból származó [esettanulmányokban](https://customers.microsoft.com/story/mwh-global-now-part-of-stantec-secures-mobile-devices-with-intune), amelyek azt írják le, hogyan mérték fel egyes cégek saját mobileszköz-felügyeleti követelményeiket.

## <a name="next-steps"></a>További lépések

[Alapszintű beállítás](migration-guide-setup.md)
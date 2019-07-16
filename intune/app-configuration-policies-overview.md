---
title: Alkalmazáskonfigurációs szabályzatok a Microsoft Intune-hoz
titleSuffix: ''
description: Ismertető a Microsoft Intune alkalmazáskonfigurációs szabályzatainak iOS- vagy Android-eszközön való használatához.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1e5ddf39a201f1a70f997e03f0b65706853adefa
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67885125"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Alkalmazáskonfigurációs szabályzatok a Microsoft Intune-hoz

iOS- vagy Android-alkalmazáshoz a Microsoft Intune alkalmazáskonfigurációs szabályzatainak használatával adhat meg konfigurációs beállításokat. Ezek a konfigurációs beállítások lehetővé teszik, hogy az alkalmazások testreszabhatók legyenek az alkalmazások konfigurációjának és felügyeletének iparági standard megközelítésével. A konfigurációs szabályzatbeállítások akkor használatosak, amikor egy alkalmazás keresi azokat (általában az első futtatáskor).

Alkalmazáskonfigurálási szabályzatot rendelhet a felhasználók és eszközök egy csoportjához belefoglalási és kizárási hozzárendelések kombinációjával. Miután hozzáadta az alkalmazáskonfigurálási szabályzatot, beállíthatja az alkalmazáskonfigurálási szabályzat hozzárendeléseit. A szabályzat hozzárendeléseinek beállításakor felvehet vagy kizárhat a szabályzat hatálya alá eső felhasználói csoportokat. Amikor felvesz egy vagy több csoportot, kiválaszthat bizonyos csoportokat, vagy választhat beépített csoportokat. Beépített csoportok a következők: **Minden felhasználó**, **Minden eszköz**, és **Minden felhasználó és minden eszköz**.

Az alkalmazás konfigurációs beállításai például a következők bármelyikének megadását tehetik szükségessé:

- Egyéni portszám
- Nyelvi beállítások
- Biztonsági beállítások
- Márkajelzési beállítások, például a vállalat logója

Ha a felhasználóknak ezeket a beállításokat kellene megadniuk, akkor ez nem megfelelő, ami növelheti az ügyfélszolgálatra nehezedő terheket, és lelassíthatja az új alkalmazások bevezetését.

Az alkalmazás-konfigurációs házirendek segíthetnek az alkalmazások telepítésével kapcsolatos problémák elhárításában azáltal, hogy a konfigurációk beállításait egy olyan házirendhez rendeli hozzá, amely az alkalmazás futtatása előtt hozzá van rendelve a felhasználókhoz. A beállítások megadása ezek után automatikusan történik, és nincs szükség felhasználói beavatkozásra.

A konfigurációs beállítások akkor használatosak, amikor egy alkalmazás keresi azokat. Az alkalmazások általában a felhasználó általi első futtatásukkor keresik a konfigurációs beállításokat.

Az Intune alkalmazáskonfigurációinak használatára két lehetőség van:
- **Felügyelt eszközök** – Az eszköz mobileszköz-kezelő (MDM) szolgáltatója az Intune.
- **Felügyelt alkalmazások** – Az alkalmazás eszközregisztráció nélküli felügyelet alá tartozik.

> [!NOTE]
> A Microsoft Intune rendszergazdájaként szabályozhatja, hogy melyik felhasználói fiókok legyenek hozzáadva a Microsoft Office-alkalmazásokhoz a felügyelt eszközökön. A hozzáférést korlátozhatja csak a szervezeti felhasználói fiókokra, és blokkolhatja a személyes fiókok használatát a regisztrált eszközökön. A támogató alkalmazások feldolgozzák az alkalmazáskonfigurációt, majd eltávolítják és letiltják a nem jóváhagyott fiókokat.

## <a name="apps-that-support-app-configuration"></a>Az alkalmazáskonfigurációt támogató alkalmazások

### <a name="managed-devices"></a>Felügyelt eszközök
Az alkalmazáskonfigurációs szabályzatokat az azokat támogató alkalmazásokhoz használhatja. Az Intune-ban az alkalmazások konfigurációjának támogatásához a [Appconfig-Közösség](https://www.appconfig.org/members)által meghatározott alkalmazás-konfigurációk használatát támogató alkalmazásokat kell írni. Részletekért forduljon az alkalmazás forgalmazójához.

### <a name="managed-apps"></a>Felügyelt alkalmazások
Előkészítheti az üzletági alkalmazásokat az Intune App SDK az alkalmazásba való belefoglalásával, vagy az alkalmazás annak fejlesztése utáni burkolásával. Az iOS és az Android rendszerhez elérhető Intune app SDK lehetővé teszi az alkalmazás számára az Intune app Protection konfigurációs házirendjeit. Arra törekszik, hogy minimálisra csökkentse az alkalmazásfejlesztő által végzendő kódmódosítás mennyiségét. További információ: [Az Intune App SDK áttekintése](app-sdk.md).

## <a name="graph-api-support-for-app-configuration"></a>Graph API-támogatás az alkalmazáskonfigurációhoz

Mindezek mellett az alkalmazáskonfigurációs feladatok elvégzéséhez a Graph API-t is használhatja. További információk: [Graph API-kézikönyv ‒ MAM célzott konfiguráció](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="next-steps"></a>További lépések

### <a name="managed-devices"></a>Felügyelt eszközök

- Megtudhatja, hogyan használhatja az alkalmazáskonfigurációt az iOS-eszközeivel.  Lásd: [alkalmazás-konfigurációs szabályzatok hozzáadása a felügyelt iOS](app-configuration-policies-use-ios.md)-eszközökhöz.
- Megtudhatja, hogyan használhatja az alkalmazáskonfigurációt az Android-eszközeivel.  Lásd: [Alkalmazáskonfigurációs szabályzatok hozzáadása kezelt Android-eszközökhöz](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>Felügyelt alkalmazások

- Megtudhatja, hogyan használhatja az alkalmazáskonfigurációt a felügyelt alkalmazásokkal. Lásd: [Alkalmazáskonfigurációs szabályzatok hozzáadása felügyelt alkalmazásokhoz eszközbeléptetés nélkül](app-configuration-policies-managed-app.md).

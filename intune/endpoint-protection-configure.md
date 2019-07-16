---
title: Endpoint Protection-beállítások konfigurálása a Microsoft Intune-ban – Azure | Microsoft Docs
description: macOS- vagy Windows 10-eszközprofil az Intune-ban való létrehozásakor létrehozhat Endpoint Protection-beállításokat is.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 5/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: 1a5cd898545bae51395352d5cf1e7b1ee9bd22dd
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67883248"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Endpoint Protection-beállítások hozzáadása az Intune-ban

Az Intune-nal az eszköz konfigurációs profiljaival kezelheti az Endpoint Protection általános biztonsági funkcióit az eszközökön, beleértve a következőket:
- Tűzfal 
- BitLocker
- Alkalmazások engedélyezése és letiltása  
- Windows Defender és titkosítás

Létrehozhat például egy olyan Endpoint Protection-profilt, amely csak a Maces App Store áruházból származó alkalmazásokat engedélyezi telepíteni a macOS felhasználók számára. Vagy engedélyezheti a Windows SmartScreent a Windows 10-eszközök alkalmazásain.

A profil létrehozása előtt tekintse át a következő cikkeket, amelyek részletesen ismertetik az Intune által a támogatott platformokon felügyelhető Endpoint Protection-beállításokat: 
- [macOS-beállítások](endpoint-protection-macos.md)
- [Windows 10-beállítások](endpoint-protection-windows-10.md)

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Endpoint Protection-beállításokat tartalmazó eszközprofil létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
3. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
4. Adja meg az Endpoint Protection-profil **nevét** és **leírását**.
5. A **Platform** legördülő listából válassza ki azt az eszközplatformot, amelyre egyéni beállításokat szeretne alkalmazni. Jelenleg az alábbi platformokra vonatkozóan lehet eszközkorlátozási beállításokat megadni:
   - **macOS**
   - **Windows 10 és újabb**
6. A **Profil típusa** legördülő listából válassza az **Endpoint Protection** lehetőséget. 
7. A kiválasztott platformtól függően a konfigurálható beállítások eltérőek. Lásd:
   - [macOS-beállítások](endpoint-protection-macos.md)
   - [Windows 10-beállítások](endpoint-protection-windows-10.md)  

8. A megfelelő beállítások konfigurálása után válassza a **Létrehozás** elemet a **profil létrehozása** lapon.

   Ekkor létrejön a profil, és megjelenik a profilok listáját tartalmazó lapon. Ha csoportokhoz szeretné hozzárendelni a profilt, tekintse meg az [eszközprofilok hozzárendelését](device-profile-assign.md) ismertető cikket.


## <a name="next-steps"></a>További lépések  

Ha csoportokhoz szeretne hozzárendelni egy profilt, tekintse meg az [eszközprofilok hozzárendelését](device-profile-assign.md) ismertető cikket.

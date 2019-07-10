---
title: Alkalmazások GCC magas és DOD-alapú környezetek
titleSuffix: Microsoft Intune
description: Ismerje meg az alkalmazások Microsoft Intune-nal GCC magas és DOD-alapú környezetek használata esetén.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 29329f86-1aa5-434f-9925-8dc28bf35348
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 17d94252dd957c5699b34e0b8c2cbae2eee0b66f
ms.sourcegitcommit: 63b55e81122e5c15893302b109ae137c30855b55
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67713362"
---
# <a name="deploying-apps-using-intune-on-the-gcc-high-and-dod-environments"></a>Az Intune-nal a GCC magas és a DoD környezetek alkalmazások üzembe helyezése 

A Microsoft Intune terjesztheti az alkalmazásokat, hogy a dolgozóknak a bérlői rendszergazdák által is használt. A munkaerő számára a céges alkalmazott, az alkalmazások felhasználóinak. Nincsenek számos különböző típusú alkalmazáshoz, az Intune-ból GCC magas vagy a védelmi Minisztérium környezetekben telepíthető. Ha egy rendszergazda kell feltöltése és terjesztése egy Windows-alkalmazás szánt GCC magas vagy DoD célközönség, cikkszámokkal, harmadik féltől által létrehozott, illetve az offline alkalmazások letöltöttként a [Microsoft Store vállalatoknak](https://businessstore.microsoft.com/store), a rendszergazda választhat osztja el, mint egy [– üzletági alkalmazás](apps-add.md#app-types-in-microsoft-intune).  

> [!NOTE]
> Kereskedelmi környezetek esetén egy Bérlői rendszergazda szinkronizálhatók a Store vállalatoknak az Intune-nal azonban GCC magas és DOD-alapú környezetek esetén ez a szolgáltatás nem érhető el. Ebben a helyzetben a rendszergazdák kell üzembe helyeznie egy alkalmazást fel kell töltenie közvetlenül az Intune-hoz.  

## <a name="add-line-of-business-apps-using-intune"></a>Az Intune-nal – üzletági alkalmazások hozzáadása 

Adjon hozzá egy Intune-nal GCC magas vagy a védelmi Minisztérium környezethez szánt üzleti alkalmazást, kövesse a [Windows LOB-alkalmazás](lob-apps-windows.md) utasításokat. Először telepítheti a céges portál a Microsoft Store vállalatoknak választhatja. Ha a vállalati portál használatát választja, manuálisan telepítse és a vállalati portál üzembe helyezése. További információkért lásd: [a Microsoft Intune vállalati portál alkalmazás konfigurálása](company-portal-app.md). 

## <a name="distribute-offline-apps-from-the-store-for-business-using-intune"></a>Kapcsolat nélküli módban a Store, az Intune-nal vállalati alkalmazások terjesztése  

Ha szeretne [offline licencelt alkalmazások letöltéséhez](https://docs.microsoft.com/microsoft-store/distribute-offline-apps#download-an-offline-licensed-app) , a Microsoft Store vállalatoknak, kövesse az alábbi lépéseket az alkalmazás letöltéséhez: 

1. Jelentkezzen be a [Store vállalatoknak](https://businessstore.microsoft.com/).
2. Válassza ki **kezelése** > **beállítások**.
3. A **vásárlási élmény**állítsa be **offline alkalmazások megjelenítéséhez** való **a**.

Vásárlás alkalmazások esetén, ha egy kapcsolat nélküli verzió érhető el, amikor kiválaszthatja a licenctípus módosítása kapcsolat nélküli módba. Ha az alkalmazást, majd annak kezelését elvégezheti kiválasztásával **kezelés** > **termékeit és szolgáltatásait** a a [Store vállalatoknak](https://businessstore.microsoft.com/). Továbbá letöltheti az alkalmazást és annak függőségeit. Ezt követően telepítheti a letöltött alkalmazást (és annak függőségeit) a felhasználók számára az Intune-nal.  

## <a name="syncing-intune-to-the-store-for-business"></a>A vállalati Intune-ban a Store szinkronizálása 

Kereskedelmi környezetben (nem kormányzati) egy rendszergazda szinkronizálhatók az Intune-t a Microsoft Store vállalatoknak. Ez nem egy elérhető funkciónak a kormányzati környezetekben. További információk a környezetek a kormányzat Intune kereskedelmi környezetben és az Intune közötti különbségek: [Enterprise Mobility + Security for US Government szolgáltatás leírása](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-govt-service-description).  

Az Intune a vállalati fiók Store szinkronizálni, lásd: [a Microsoft Store vállalatoknak a Microsoft Intune-nal áruházban vásárolt alkalmazások kezelése](windows-store-for-business.md).  

## <a name="compliance"></a>Megfelelőség 

Tekintse át az adatvédelmi és megfelelőségi utasításokat az alkalmazásokat, és hasonlítsa össze a vállalat megfelelőségi, biztonsági és adatvédelmi előírásainak megfelelő használatára vonatkozó ezek a szolgáltatások meghatározása során.   

## <a name="next-steps"></a>További lépések

További információ üzembe helyezése és alkalmazások hozzárendelésével kapcsolatban lásd: [alkalmazások hozzárendelése csoportokhoz a Microsoft Intune-nal](apps-deploy.md).

 

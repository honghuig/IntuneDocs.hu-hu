---
title: "Az alkalmazás-életciklus áttekintése | Microsoft Docs"
description: "Ismerje meg az Intune által felügyelt alkalmazások életciklusát, kezdve a hozzáadásuktól a végső eltávolításukig."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: c3394663b234ada70f724b750dfdffc8369cb203
ms.lasthandoff: 12/30/2016


---

# <a name="overview-of-the-app-lifecycle"></a>Az alkalmazás-életciklus áttekintése

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Az Intune-ban az alkalmazások életciklusa az alkalmazás felvételével kezdődik. Ezt követően az alkalmazás különböző fázisokon halad át egészen addig, amíg el nem távolítják.

![Az alkalmazások életciklusa](./media/app-lifecycle.png "Az alkalmazások életciklusa az Intune-ban")

## <a name="add"></a>Hozzáadás

Az alkalmazások központi telepítésének első lépéseként fel kell vennie az Intune-ba a felügyelni és telepíteni kívánt alkalmazásokat. Jóllehet számos különböző típusú alkalmazással dolgozhat, az alapvető eljárás mindegyiknél ugyanaz. Az Intune-ban [regisztrált eszközökhöz](add-apps-for-mobile-devices-in-microsoft-intune.md), valamint [az Intune ügyfélszoftverével felügyelt Windows-számítógépekhez](add-apps-for-windows-pcs-in-microsoft-intune.md) egyaránt vehet fel alkalmazásokat.

## <a name="deploy"></a>Telepítés

Az Intune-ba való felvételét követően [telepítheti az alkalmazást a felügyelni kívánt eszközökre](deploy-apps.md). Az Intune jelentős mértékben leegyszerűsíti ezt a folyamatot, ráadásul az alkalmazás telepítését követően az Intune felügyeleti konzoljából [ellenőrizheti a telepítés sikerességét](monitor-apps-in-microsoft-intune.md). Emellett egyes alkalmazás-áruházakban, például az [Apple](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md) és a [Windows](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md) alkalmazás-áruházaiban nagyban is vásárolhat alkalmazáslicenceket vállalata számára. Az Intune képes szinkronizálni az adatokat ezekkel az áruházakkal, így Ön közvetlenül az Intune felügyeleti konzoljából hajthatja végre a központi telepítést és követheti nyomon a licenchasználatot.

## <a name="configure"></a>Konfigurálás

Az alkalmazások életciklusa során általában az alkalmazás több új verziója is megjelenik. Az Intune számos eszközt kínál a központilag telepített alkalmazások [verziófrissítésére](update-apps-using-microsoft-intune.md). Ezen túlmenően bizonyos alkalmazásokhoz további funkciók is konfigurálhatók, például:
- Az [iOS-alkalmazáskonfigurációs szabályzatok](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md) segítségével meghatározhatja, hogy a kompatibilis iOS-alkalmazások futása esetén mely beállítások lépjenek érvénybe. Az alkalmazásokhoz megadhat például márkajelzési beállításokat, illetve meghatározhatja a kiszolgáló nevét, amelyhez szeretné, hogy az alkalmazás csatlakozzon.
- A [felügyeltböngésző-szabályzatok](manage-internet-access-using-managed-browser-policies.md) segítségével konfigurálhatja az Intune által felügyelt, az eszközök alapértelmezett böngészőjét felváltó böngésző beállításait, illetve korlátozhatja, hogy a felhasználók milyen weboldalakat nyithatnak meg.

## <a name="protect"></a>Védelem

Az Intune számos módszert kínál az alkalmazásokban tárolt adatok védelmére. A legfontosabb megoldások a következők:
- A [feltételes hozzáférés](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) az Ön által megadott feltételek alapján szabályozza az email és egyéb szolgáltatások elérését. Ilyen feltétel lehet az eszköz típusa, vagy az, hogy megfelel-e a központilag telepített [eszközmegfelelőségi szabályzatnak](introduction-to-device-compliance-policies-in-microsoft-intune.md).
- A [mobilalkalmazás-kezelés (MAM)](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md) funkció az egyes alkalmazásokkal együttműködve nyújt védelmet az általuk használt vállalati adatok számára. Letilthatja például az adatok másolását a nem felügyelt és a felügyelt alkalmazások között, illetve megakadályozhatja az alkalmazások futtatását függetlenített vagy feltört eszközökön.

## <a name="retire"></a>Kivonás

Az idő múlásával a telepített alkalmazások elavulttá válnak, így el kell őket távolítani. Az Intune segítségével egyszerűen [kivonhatja a kívánt alkalmazásokat a szolgáltatásból](retire-apps-using-microsoft-intune.md).

---
title: Milyen adatokhoz férhet hozzá a munkahelye, ha regisztrálja eszközét?
description: Ismerteti, hogy a rendszergazda mit láthat a felügyelt eszközön, és mit nem.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 12655728-a1af-4d89-97bc-925fe36c0dc4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1afdaa1bb21e3a13932202524eed9322d95479bb
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/03/2019
ms.locfileid: "67545641"
---
# <a name="what-information-can-my-organization-see-when-i-enroll-my-device"></a>Milyen adatok láthatók a szervezet számára, ha regisztrálom az eszközömet?

A szervezete számára nem láthatók az Ön személyes adatai, amikor eszközt regisztrál a Microsoft Intune-ban. Amikor regisztrálja eszközét, Ön engedélyezi a szervezetének bizonyos eszközadatoknak, például az eszköz típusának és sorozatszámának megtekintését. A szervezet ezt az információt az eszközön lévő vállalati adatok védelmére használja fel.

**A szervezet számára soha nem látható adatok:**

- Hívási és böngészési előzmények
- E-mailek és SMS-ek
- Névjegyek
- Naptár
- Jelszavak
- Képek, beleértve a Fényképezőgép alkalmazás vagy a Filmtekercs mappa tartalmát
- Fájlok

**A szervezet számára mindig látható adatok:**

- Eszközmodell, például Google Pixel
- Eszköz gyártója, például a Microsoft
- Operációs rendszer és annak verziója, például iOS 12.0.1
- Alkalmazásleltár és alkalmazásnevek, például a Microsoft Word. A személyes eszközökön a szervezet csak a felügyelt alkalmazásleltár látható. A vállalati tulajdonú eszközökön a szervezet a teljes alkalmazásleltárat láthatja.
- Az eszköz tulajdonosa
- Eszköz neve
- Eszköz sorozatszáma
- IMEI

**A szervezet számára esetlegesen látható adatok:**

- Telefonszám: A **vállalati**-tulajdonú eszközök esetében a teljes telefonszám látható. A **személyes** tulajdonú eszközök esetében csak a telefonszám utolsó négy számjegye látható a szervezet számára. Minden egyes eszköz **Tulajdonjogtípusát** megtekintheti az adott eszköz **Eszköz részletei** lapjának megnyitásával.
- Eszköz tárterület: Ha kötelező alkalmazást nem lehet telepíteni, a szervezet előfordulhat, hogy tekintse meg az eszköz tárolóhelyet döntse el, ha a terület értéke túl alacsony.  
- Hely: A szervezet számára soha nem látható az eszköz helye, kivéve, ha kell állítani egy elveszett, a felügyelt iOS-eszközt. Látogasson el a [Apple iOS dokumentációjában](https://go.microsoft.com/fwlink/?linkid=853816) tájékozódhat felügyelt eszközökön.  
- Alkalmazás-készlet részletei: Ha a szervezet használja a Mobile Threat Defense, lesz, amely az iOS-eszközön elérhető alkalmazásokról részleteinek megtekintéséhez. További információk: [Mobile Threat Defense](you-are-prompted-to-install-mtd-ios.md).
- Hálózati információkat: Android-eszközök hálózati kapcsolatairól bizonyos információkat lehet a cég informatikai támogatási szolgálata számára elérhető. Például ha a szervezet egyes eszközeinek egy bizonyos épületen belül kell maradniuk, az eszköz azonosítja a hálózatot, amelyhez csatlakozik. 

---
title: Felügyelt alkalmazások használata Android-eszközön | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ed10a62c-b026-4ad3-ac41-641933522df2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: efcb622681e4f3b3fba7b686551cca7db6bb4c3a
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/03/2019
ms.locfileid: "67546034"
---
# <a name="use-managed-apps-on-your-android-device"></a>Felügyelt alkalmazások használata Android-eszközön
A felügyelt alkalmazások úgy vannak konfigurálva, hogy megfeleljenek a szervezet biztonsági követelményeinek, és a védelmet biztosítsanak a munkahelyi és iskolai adatok számára. Ezek az alkalmazások telepíthetők vagy automatikusan használhatók az eszközén. 

Mielőtt megkapná és telepítené a felügyelt alkalmazást, a szervezet konfigurálja az engedélyeit. Ezek korlátozhatják az alkalmazás működését vagy a felhasználói interakciókat, hogy az alkalmazásadatokat illetéktelen személyek ne oszthassák meg és ne férjenek hozzá. Például egy szervezet blokkolhatja a másolást és a beillesztést az alkalmazásban. Vagy megakadályozhatja adatok mentését az eszköz helyi tárolójába.

A maximális adatvédelem érdekében a szervezet több felügyelt alkalmazást is konfigurálhat, hogy azok együttműködjenek. Példa:
1. Csatlakozik a szervezet hálózatához egy felügyelt böngészőalkalmazás, például a Microsoft Edge segítségével.
2. Rákattint egy hivatkozásra, hogy megnyissa munkatársa prezentációs fájlját.
3. A fájl megnyílik a megfelelő felügyelt alkalmazásban, például a Microsoft PowerPointban.

A szervezetek megkövetelhetik egy adott felügyelt alkalmazás használatát egy művelet elvégzéséhez, például egy munkafájl megnyitásához, vagy egy webes hivatkozáshoz való hozzáféréshez. Ha nem rendelkezik az alkalmazással, lehet, hogy nem tudja folytatni a feladatát. Bizonyos felügyelt alkalmazások telepíthetők, azonban nem szükségesek.

## <a name="how-do-i-know-im-using-a-managed-app"></a>Honnan tudhatom, felügyelt alkalmazást használok-e?
Amikor először fér hozzá munkahelyi vagy iskolai adatokhoz egy felügyelt alkalmazásban, a képernyőképen láthatóhoz hasonló üzenetet kap. Az üzenet felszólítja, hogy a folytatáshoz indítsa újra az alkalmazást.

![Képernyőkép arról az üzenetről, amely akkor jelenik meg, amikor egy felhasználó megnyit egy felügyelt alkalmazást az eszközén. Az üzenet a következő: „A szervezet nem védi az adatokat ebben az alkalmazásban. A folytatáshoz indítsa újra az alkalmazást.” Ezután egy OK gomb szerepel.](./media/managed-apps-message.png)

## <a name="commonly-managed-apps"></a>Gyakori felügyelt alkalmazások  
Példák gyakran szükséges vagy elérhető felügyelt alkalmazásokra az iskolában vagy a munkahelyen:

- Microsoft Edge

- Microsoft Outlook

- Microsoft Word, Excel és PowerPoint

## <a name="how-do-i-get-managed-apps"></a>Hogyan szerezhetők be a felügyelt alkalmazások?
Felügyelt alkalmazások három módja van.  
* A regisztráció során a szervezet automatikusan telepít alkalmazásokat az eszközére.  
* Telepíthet alkalmazásokat a Google Play Áruházból, majd bejelentkezhet az alkalmazásba munkahelyi vagy iskolai fiókjával.    
* A szervezet elérhetővé teszi a felügyelt alkalmazásokat a Céges portálon. Nyissa meg a céges portál alkalmazásban vagy webhelyen keresse, megtekintése és kereshessék az alkalmazásokat. Ezek az alkalmazások kapcsolatos további információkért lásd: a következő szakaszban [rendelkezésre álló alkalmazások](#available-apps).  

### <a name="available-apps"></a>Nem kötelező alkalmazások   
 A szervezet kiválaszthatja a megfelelő és hasznos az Ön számára a munkahelyi vagy iskolai rendszerhez, és elérhetővé tétele, hogy a céges portál alkalmazás.  

 Alkalmazások is elérhető lesz az eszköz típusa alapján. Például ha a vállalati portál alkalmazás androidos használ, hozzáférhet az Android-alkalmazások, de nem az iOS-alkalmazások.   

## <a name="request-an-app-for-work-or-school"></a>A kérelem egy alkalmazást a munkahelyi vagy iskolai fiók   
 Ha szükséges, de nem látható a vállalati portál alkalmazás, kérheti. Keresse meg a kapcsolattartási adatait a **segélyszolgálat** vagy alkalmazás **IT-csoport elérhetősége** fülre. Ugyanazokat az adatokat a látni fogja a [céges portál webhelyen](https://go.microsoft.com/fwlink/?linkid=2010980).   

## <a name="what-can-my-company-support-manage-in-an-app"></a>Mit felügyelhet a cég informatikai támogatási szolgálata az alkalmazásokban?  
A következőkben szerepelnek azok a beállítások, amelyeket a vállalat informatikai támogatási szolgálata felügyelhet az alkalmazásokban. Ezek a beállítások befolyásolják, hogyan tekintheti meg, hogyan férhet hozzá, és általában hogyan használja a munkahelyi vagy az iskolai adatokat az eszközén:

* Adott webhelyek hozzáférése  

* Belső céges webhelyet a Microsoft Edge és az Azure Active Directory-proxy használatával való hozzáférés  

* Az alkalmazás minimálisan szükséges verziója és az operációs rendszer verziója

* Adatok alkalmazások közötti megosztása és átvitele  

* A fájlok mentésének helye és módja  

* Másolási és beillesztési funkció  

* PIN-hozzáférési követelmények  

* A bejelentkezés módja vállalati hitelesítő adatokkal  

* Adatok biztonsági mentésének létrehozása a felhőben  

* Képernyőfelvételek készítésének lehetősége  

* Adattitkosítási követelmények  

Az eszközén lévő felügyelt alkalmazásokról további információért lépjen kapcsolatba a cég informatikai támogatási szolgálatával. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).

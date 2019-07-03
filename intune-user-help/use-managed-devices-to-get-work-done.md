---
title: Munkavégzés felügyelt eszközökkel | Microsoft Docs
description: Tudja meg, mit jelent az eszköz regisztrálása az Intune-felügyeletben.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 523caa6b-d792-4bb6-bddb-24b2479932d8
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 798ea14529c0cbf44a0530f1a9a16507b14d7397
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67527835"
---
# <a name="enroll-device-for-access-to-work-or-school-resources"></a>Munkahelyi vagy iskolai erőforrások eléréséhez az eszköz regisztrálása
Regisztrálja az eszközt, és hozzáférhet a levelezéshez és alkalmazásokhoz, kell telepíteni az Intune vállalati portál alkalmazás vagy a Microsoft Intune app. Ha regisztrál, az alapszintű felügyeleti házirendek, amelyek a szervezet konfigurált, például a jelszó, a PIN-kód és a titkosítás, az eszköz lépnek. Az Eszközbeállítások megfelelnek a szervezeti követelmények mindegyikének, miután gyakorlatilag bárhonnan biztonságosan elérheti a munkahelyi információkhoz.  

A céges portál és a Microsoft Intune-alkalmazások biztonsága a regisztrált eszközön annak biztosítása, hogy az eszköz beállításai megfelelnek-e a szervezeti szabályzatok szerint. 

A vállalati portál alkalmazást is:  
* A személyes és munkahelyi adatok külön tartja.  
* Egyszerűen megtalálhatók és telepíthetők a megfelelő munkahelyi és iskolai alkalmazásokhoz.   

## <a name="get-the-apps"></a>Az alkalmazások beszerzése
Beszerzése a vállalati portál:

- A vállalati portál alkalmazás telepítésekor a platform-specifikus alkalmazás-áruházból. Bizonyos esetekben a szervezet telepíti a vállalati portál alkalmazás az Ön számára.  
- Nyissa meg a [céges portál webhelyen](https://go.microsoft.com/fwlink/?linkid=2010980) az alkalmazás eléréséhez egy böngészőben.  

Ön kell használnia a Microsoft Intune-alkalmazást, a szervezet telepíti azt az Ön számára.  


## <a name="what-information-can-my-company-see-when-i-enroll"></a>Milyen információkat lehet saját munkahelye, ha regisztrálom az?
Miután az eszköz regisztrálva van, a szervezet támogatási személyek csak munkával, információk jelennek meg. Azonban nem tekinthetik meg a személyes adatok. Ha regisztrál egy személyes eszköz munkahelyi használatra [ismerje meg, pontosan mit láthatnak és mit nem látható](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).  


## <a name="whats-the-difference-between-the-apps-and-the-website"></a>Mi a különbség az alkalmazások és a webhely?
A vállalati portál alkalmazás Windows 10, iOS, macOS és Android-eszközökön érhető el. Zökkenőmentes integráció az eszköz megfelelő platform használatával. A webhelyverzión bármely eszközről elérhető, és a függetlenül attól, hogy melyik eszközt használja a azonos, univerzális élményt biztosít. 

A Microsoft Intune alkalmazás az Android-eszközök a vállalat által birtokolt.  

## <a name="what-kind-of-devices-can-you-enroll-with-company-portal"></a>Milyen típusú eszközöket, regisztrálhat a vállalati portál?
-   iOS (például iPhone és iPad) és macOS (például MacBook és iMac) rendszerű Apple-eszközök
-   Androidos eszközök
-   Windows-eszközök
    -   Windows 10 mobil verzió
    -   Windows 10 asztali verzió
    -   Windows Phone 8.1
    -   Windows 8.1

## <a name="what-kind-of-devices-can-you-enroll-with-the-microsoft-intune-app"></a>Milyen típusú eszközökről is regisztrál a Microsoft Intune alkalmazással?  
Vállalati tulajdonú Android-eszközök az alkalmazással szeretné használni a munkahelye beállította regisztrálásával. Az alkalmazás támogatja az Android 6.0-s és újabb verziók. 

## <a name="can-you-remove-a-computer-or-device-from-the-company-portal"></a>Eltávolítható egy számítógép vagy eszköz a Vállalati portálról?
Igen, a Vállalati portálról eltávolíthat vagy alaphelyzetbe állíthat egy számítógépet vagy eszközt. Az **eltávolítás** és az **alaphelyzetbe állítás** között azonban van különbség.

Ha eltávolítja egy számítógép vagy eszköz a vállalati portálról, az eszköz Intune-ból regisztrációja is törlődik. A regisztráció törlése után az adott eszközről többé nem fér hozzá a Vállalati portálhoz, és az is előfordulhat, hogy egyes vállalati adatok törlődnek az eszközről. Eltávolíthatja az eszközét a vállalati portálról való kezelésével kapcsolatos információkért tekintse meg az alábbi hivatkozásokat:  

- [Android rendszerű eszköz regisztrációjának törlése](unenroll-your-device-from-intune-android.md)
- [iOS rendszerű eszköz regisztrációjának törlése](unenroll-your-device-from-intune-ios.md)
- [macOS rendszerű eszköz regisztrációjának törlése](unenroll-your-device-from-intune-macos.md)
- [Windows rendszerű eszköz regisztrációjának törlése](unenroll-your-device-from-intune-windows.md)

Egy számítógép vagy eszköz alaphelyzetbe állításakor, a vállalati portál megpróbálja visszaállítani számítógépét vagy eszközét a gyári alapértelmezett beállításokra. Az eszköz alaphelyzetbe állításával töröl minden vállalati és személyes adatok az eszközről. Az eszköz elvesztése is visszaállíthatja rajta távolról a vállalati portál webhelyén.  

Az eszköz alaphelyzetbe állítása kapcsolatban lásd: [alaphelyzetbe állíthatja az eszközt a vállalati portál webhelyéről](reset-erase-your-device-cpwebsite.md).  

## <a name="can-you-remove-a-computer-or-device-from-the-microsoft-intune-app"></a>Eltávolítható egy számítógép vagy eszköz a Microsoft Intune-alkalmazásból?
Nem, nincs lehetőség, hogy a vállalat által birtokolt eszköz eltávolítása a Microsoft Intune-alkalmazást.  

## <a name="what-if-i-cant-see-my-device-in-the-company-portal-or-microsoft-intune-app"></a>Mi történik, ha az eszköz a céges portál vagy a Microsoft Intune app nem láthatók?
Az eszközök csak akkor láthatók, ha hozzáadja őket a Vállalati portálhoz. Látogasson el a rendszergazda által beállított Céges portálra, és kövesse az eszközére vonatkozó lépéseket. A vállalat által birtokolt vagy kezelt eszközöket sem fogja látni.

Ha a Microsoft Intune-alkalmazást használ, csak az aktuálisan használt eszköz láthatja. További regisztrált eszközök nem lesznek láthatók, akkor az alkalmazásban.  

## <a name="where-else-can-i-go-for-help"></a>Hol találhatok még segítségét?  
Gyakori problémák és kérdések elhárításához tekintse meg a platform-specifikus docs:  

- [Androidos eszközök gyakori problémáinak elhárítása](check-compliance-on-your-device-android.md)  
- [Az iOS-eszközök gyakori problémáinak elhárítása](troubleshoot-your-device-ios.md)
- [A macOS-eszközök gyakori problémáinak elhárítása](troubleshoot-your-device-macos.md)
- [A Windows-eszközök gyakori problémáinak elhárítása](troubleshoot-your-device-windows.md)

Akkor is is fel a kapcsolatot a támogatási szolgálathoz. A céges portál és a Microsoft Intune app nyújthat segítséget és lapokat, a kapcsolattartási adatokat és a probléma jelentéséhez módon támogatja. Kapcsolattartási adatait is érhető el a szervezet [céges portál webhelyen](https://go.microsoft.com/fwlink/?linkid=2010980).  

## <a name="next-steps"></a>További lépések  

Regisztráció esetén az eszköz platformjának adott kezdve segítséget kaphat:  

- [Android-eszköz használata](using-your-android-device-with-intune.md)
- [iOS-eszköz használata](using-your-ios-device-with-intune.md)
- [macOS-eszköz használata](using-your-macos-device-with-intune.md)
- [Windows-eszköz használata](using-your-windows-device-with-intune.md)
- [A Munkahelyi portál webhely használata](using-the-intune-company-portal-website.md)



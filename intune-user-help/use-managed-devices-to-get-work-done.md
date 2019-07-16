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
ms.openlocfilehash: 2f698f03ed3c7523ef1d768d2a1361d6d1a55008
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67883871"
---
# <a name="enroll-device-for-access-to-work-or-school-resources"></a>Eszköz regisztrálása munkahelyi vagy iskolai erőforrásokhoz való hozzáféréshez
Az eszköz regisztrálásához és az e-mailekhez és az alkalmazásokhoz való hozzáféréshez telepítenie kell a Intune Céges portál alkalmazást vagy Microsoft Intune alkalmazást. A regisztráláskor a szervezet által konfigurált alapszintű felügyeleti szabályzatok, például a jelszó, a PIN-kód és a titkosítás az eszközre vannak alkalmazva. Ha az eszközbeállítások eleget tesz a szervezeti követelményeknek, a munkahelyi információk gyakorlatilag bárhonnan biztonságosan elérhetők.  

A Céges portál és Microsoft Intune alkalmazások gondoskodnak a regisztrált eszköz biztonságáról azáltal, hogy az eszköz beállításai megfelelnek a szervezeti szabályzatoknak. 

A Céges portál alkalmazás emellett a következőket is:  
* A személyes és munkahelyi információk elkülönítve tartása.  
* Megkönnyíti a megfelelő munkahelyi és iskolai alkalmazások megkeresését és telepítését.   

## <a name="get-the-apps"></a>Alkalmazások beszerzése
Céges portál beszerzése:

- Telepítse a Céges portál alkalmazást a platform-specifikus App Store áruházból. Bizonyos esetekben a szervezet a Céges portál alkalmazást fogja telepíteni.  
- Az alkalmazás böngészőből való eléréséhez lépjen a [céges portál](https://go.microsoft.com/fwlink/?linkid=2010980) webhelyre.  

Ha a Microsoft Intune alkalmazást kell használnia, a szervezet telepíti azt Önnek.  


## <a name="what-information-can-my-company-see-when-i-enroll"></a>Milyen információkat láthatok a vállalatom a regisztráláskor?
Az eszköz regisztrálását követően a szervezete által támogatott személyek csak a munkához szükséges információkat láthatják. A személyes adatok nem jelennek meg. Ha személyes eszközt regisztrál a munkahelyi használatra, pontosan megtudhatja, [mit láthat és nem láthat](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).  


## <a name="whats-the-difference-between-the-apps-and-the-website"></a>Mi a különbség az alkalmazások és a webhely között?
A Céges portál alkalmazás Windows 10, iOS, macOS és Android rendszerű eszközökhöz érhető el. Zökkenőmentesen integrálható az eszköz megfelelő platformján. A webhely verziója bármely eszközről elérhető, és ugyanazt az univerzális élményt nyújtja, függetlenül attól, hogy milyen eszközt használ. 

A Microsoft Intune alkalmazás a vállalat által birtokolt Android-eszközökhöz használható.  

## <a name="what-kind-of-devices-can-you-enroll-with-company-portal"></a>Milyen típusú eszközöket regisztrálhat a Céges portál?
- iOS (például iPhone és iPad) és macOS (például MacBook és iMac) rendszerű Apple-eszközök
- Androidos eszközök
- Windows-eszközök
  - Windows 10 mobil verzió
  - Windows 10 asztali verzió
  - Windows Phone 8.1
  - Windows 8.1

## <a name="what-kind-of-devices-can-you-enroll-with-the-microsoft-intune-app"></a>Milyen típusú eszközök regisztrálhatók a Microsoft Intune alkalmazással?  
Regisztrálhat vállalati tulajdonú Android-eszközöket, amelyeket a szervezete az alkalmazással való használatra beállított. Az alkalmazás az Android 6,0-es és újabb verzióit támogatja. 

## <a name="can-you-remove-a-computer-or-device-from-the-company-portal"></a>Eltávolítható egy számítógép vagy eszköz a Vállalati portálról?
Igen, a Vállalati portálról eltávolíthat vagy alaphelyzetbe állíthat egy számítógépet vagy eszközt. Az **eltávolítás** és az **alaphelyzetbe állítás** között azonban van különbség.

Ha eltávolít egy számítógépet vagy eszközt a Céges portálről, az eszköz regisztrációját törli az Intune-ból. A regisztráció törlése után az adott eszközről többé nem fér hozzá a Vállalati portálhoz, és az is előfordulhat, hogy egyes vállalati adatok törlődnek az eszközről. Ha szeretné megtudni, hogyan távolíthatja el az eszközt a Céges portálről, tekintse meg az alábbi hivatkozásokat:  

- [Android rendszerű eszköz regisztrációjának törlése](unenroll-your-device-from-intune-android.md)
- [iOS rendszerű eszköz regisztrációjának törlése](unenroll-your-device-from-intune-ios.md)
- [macOS rendszerű eszköz regisztrációjának törlése](unenroll-your-device-from-intune-macos.md)
- [Windows rendszerű eszköz regisztrációjának törlése](unenroll-your-device-from-intune-windows.md)

Egy számítógép vagy eszköz alaphelyzetbe állításakor a Céges portál megkísérli visszaállítani a számítógépet vagy az eszközt a gyártó alapértelmezett beállításaira. Az eszköz alaphelyzetbe állításával megszűnik az eszközről származó összes vállalati és személyes adatok eltávolítása. Ha elvesztette az eszközét, távolról is visszaállíthatja a Céges portál webhelyről.  

Az eszköz alaphelyzetbe állításáról [az eszköz alaphelyzetbe állítása a céges portál](reset-erase-your-device-cpwebsite.md)webhelyről című témakörben olvashat bővebben.  

## <a name="can-you-remove-a-computer-or-device-from-the-microsoft-intune-app"></a>El tud távolítani egy számítógépet vagy eszközt a Microsoft Intune alkalmazásból?
Nem, a Microsoft Intune alkalmazásból nem lehet eltávolítani a vállalat által birtokolt eszközöket.  

## <a name="what-if-i-cant-see-my-device-in-the-company-portal-or-microsoft-intune-app"></a>Mi a teendő, ha nem látom az eszközt a Céges portál vagy Microsoft Intune alkalmazásban?
Az eszközök csak akkor láthatók, ha hozzáadja őket a Vállalati portálhoz. Látogasson el a rendszergazda által beállított Céges portálra, és kövesse az eszközére vonatkozó lépéseket. A vállalat által birtokolt vagy kezelt eszközöket sem fogja látni.

Ha a Microsoft Intune alkalmazást használja, akkor csak az éppen használt eszközt fogja látni. A többi regisztrált eszköz nem lesz látható az alkalmazásban.  

## <a name="where-else-can-i-go-for-help"></a>Hol találhatok még segítségét?  
A gyakori problémák és kérdések elhárításához tekintse meg ezeket a platform-specifikus dokumentumokat:  

- [Androidos eszközök gyakori problémáinak elhárítása](check-compliance-on-your-device-android.md)  
- [Az iOS-eszközök gyakori problémáinak elhárítása](troubleshoot-your-device-ios.md)
- [A macOS-eszközök gyakori problémáinak elhárítása](troubleshoot-your-device-macos.md)
- [A Windows-eszközök gyakori problémáinak elhárítása](troubleshoot-your-device-windows.md)

A támogatási személyt is elérheti. A Céges portál és Microsoft Intune alkalmazás Súgó és támogatás lapokat, amelyek a kapcsolattartási adatokat és a problémák jelentésének módjait listázza. A kapcsolattartási adatok a szervezeti [céges portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980)is elérhetők.  

## <a name="next-steps"></a>További lépések  

Szerezze be a regisztrációtól kezdődő segítséget, amely az eszköz platformjának megfelelő:  

- [Android-eszköz használata](using-your-android-device-with-intune.md)
- [iOS-eszköz használata](using-your-ios-device-with-intune.md)
- [macOS-eszköz használata](using-your-macos-device-with-intune.md)
- [Windows-eszköz használata](using-your-windows-device-with-intune.md)
- [A Munkahelyi portál webhely használata](using-the-intune-company-portal-website.md)



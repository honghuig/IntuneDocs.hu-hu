---
title: Keresse meg a Microsoft Intune eszköz elsődleges felhasználója.
titleSuffix: ''
description: Az elsődleges felhasználó (vagy a felhasználó-eszköz kapcsolat) az Intune eszköz megkeresése
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 21f62ad44d992d1f4adbb1945bdba02e526d9138
ms.sourcegitcommit: 2db7dc2baea0c159f70338e6a0529acc89580773
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67500645"
---
# <a name="find-the-primary-user-of-an-intune-device"></a>Keresse meg a elsődleges felhasználót egy Intune-eszköz

Elsődleges felhasználói, más néven felhasználó-eszköz kapcsolat, minden egyes Intune eszköz-tulajdonságra. Az Intune eszköz rendelkezhet hozzárendelt nulla vagy egy elsődleges felhasználói. Ha nincs hozzárendelt elsődleges felhasználó, az eszköz nevezzük egy "megosztott eszköz".

## <a name="how-to-find-a-devices-primary-user"></a>Elsődleges felhasználó-eszköz megkeresése

1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Válasszon **eszközök** > Válasszon egy eszközt.
3. Az a **áttekintése** lapon a **Továbbiak** és láthatja, hogy a felsorolt elsődleges felhasználói.

## <a name="what-is-the-primary-user"></a>Mi az az elsődleges felhasználója?
A felhasználó elsődleges tulajdonság egy Intune-licenccel rendelkező felhasználó leképezése az eszközeiket a használható:
- A céges portál alkalmazás
- A végfelhasználói webhely
- IT pro környezeteket, például az Azure Portalon oldalak hibaelhárítás. Ezeket az oldalakat eszközökre felhasználói fiókok társítsa az elsődleges felhasználói.    

### <a name="company-portal-app"></a>Vállalati portál alkalmazás
A vállalati portál alkalmazás vár, hogy a felhasználói fiókkal jelentkezett be a vállalati portálhoz,-e az eszköz elsődleges felhasználója. Ha az elsődleges felhasználó hozzá lett rendelve egy másik felhasználó, a vállalati portál figyelmeztetést jelenít meg:

"Az eszköz már hozzá van rendelve valaki a szervezetben. Lépjen kapcsolatba a cég informatikai támogatási arról, hogy az eszköz elsődleges felhasználója. Folytathatja az vállalati portált, de funkció korlátozott lesz."

Ha egy Intune-ban eszközhöz hozzárendelt elsődleges felhasználóval nem tartozik, majd a céges portál alkalmazás észleli ezt, közös használatú. Az eszköz csempéjén megjelenő "megosztott" címkével rendelkező megosztott eszközök vizuálisan azonosítható. Ebben a módban a vállalati portál továbbra is használható lekérheti és telepítheti az elérhető alkalmazások. Önkiszolgáló műveletek (alaphelyzetbe állítása/átnevezése vagy kivonása) azonban nem érhetők el.  

Megjelenik a vállalati portált a megosztott eszközök, elérhető alkalmazások hozzá kell rendelni egy felhasználói csoportot. Ezek a rendszerkörnyezetben vagy a felhasználói környezet, az alkalmazás lett konfigurációjától függően a rendszergazda fogja telepíteni. Alkalmazás helyi kapcsolatos további információkért lásd: [alkalmazások telepítése Windows 10 rendszerű eszközökön](apps-windows-10-app-deploy.md#installing-apps-on-windows-10-devices). Céges portál 10.3.4651.0 verzió vagy újabb a funkció használatához szükséges.


## <a name="who-is-assigned-as-the-primary-user"></a>Az elsődleges felhasználó rendelt személy?
Intune során vagy hamarosan a regisztrálás után automatikusan hozzáadja elsődleges felhasználói eszközökre. A regisztrációs módszer meghatározza, hogy az elsődleges felhasználó hozzáadásakor az eszközökre.

| Platform | Regisztráció módszere | Elsődleges felhasználó | Elsődleges felhasználó hozzá van rendelve. |
| ---- | ---- | ---- | ---- |
| Windows | Adja hozzá a munkahelyi vagy iskolai rendszerhez (a felhasználó közreműködésével) | Felhasználó beléptetése | Regisztráció során |   
| Windows | A modern alkalmazás be (a felhasználó közreműködésével) | Felhasználó beléptetése | Regisztráció során | 
| Windows | Mobileszköz-felügyeleti csak (a felhasználó közreműködésével) regisztrálása | Felhasználó beléptetése | Regisztráció során | 
| Windows | Az Azure AD join (OOBE) tartományon kívül | Felhasználó beléptetése | Regisztráció során | 
| Windows | Az Azure AD join (Autopilot kezdőélmény) | Felhasználó beléptetése | Regisztráció során | 
| Windows | MDM-ben csak regisztrálása | Felhasználó beléptetése | Regisztráció során | 
| Windows | Hibrid AADJ + automatikus regisztráció csoportházirend-objektum | Jelentkezzen be a Windows első felhasználót | Amikor a felhasználó először jelentkezik be Windows| 
| Windows | Közös felügyelet | Jelentkezzen be a Windows első felhasználót | Amikor a felhasználó először jelentkezik be Windows | 
| Windows | Az Azure AD join (tömeges regisztrációs jogkivonat) | Nincsenek | Nem alkalmazható | 
| Windows | Az Azure AD join (Autopilot helyi üzembe helyezése mód) | Nincsenek | Nem alkalmazható | 
| Cross-platform | Felhasználó modellvezérelt beléptetése a vállalati portál alkalmazással | Felhasználó beléptetése | Regisztráció során |
| Cross-platform | Eszközregisztráció-kezelő (DEM) | DEM-felhasználó beléptetése | Regisztráció során |
| iOS, macOS | Az Apple Eszközregisztrációs (felhasználói affinitással rendelkező DEP automatikus | Felhasználó beléptetése | Regisztráció során |
| iOS, macOS | Az automatikus Eszközregisztráció (a felhasználói affinitás nélküli DEP) Apple | None | Nem alkalmazható |
| Android | Vállalat által birtokolt, dedikált Android-eszközök | None | Nem alkalmazható |

## <a name="primary-user-and-azure-ad-device-owner"></a>Elsődleges felhasználó és eszköz tulajdonosa Azure ad-ben
Bizonyos esetekben az Azure AD eszköztől eltérő lehet az elsődleges Intune-felhasználó **tulajdonosa** tulajdonság (megtekinthető alatt **eszközök** > **Azure AD-eszközök**). Az Azure AD-eszköz tulajdonosa az Azure Active Directoryba kerül egy eszközregisztráció során.

## <a name="next-steps"></a>További lépések
[Az Intune-eszközök felügyeletére.](device-management.md)

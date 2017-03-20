---
title: "Alkalmazások telepítése | Microsoft Docs"
description: "Ez a témakör megmagyaráz néhány olyan fogalmat, amelynek a megértésére feltétlenül szüksége lesz ahhoz, hogy alkalmazásokat telepítsen az Intune-ban."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ad5ea85c-aa2e-4110-a184-172cd0b8f270
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: efa8245020b961797405a6f8b90df7e7b172b4c3
ms.lasthandoff: 12/30/2016


---

# <a name="deploy-apps-with-microsoft-intune"></a>Alkalmazások telepítése a Microsoft Intune-ban

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Ez a témakör ismerteti azokat a fogalmakat, amelyeknek a megértésére feltétlenül szükség van ahhoz, hogy alkalmazásokat telepítsen a Microsoft Intune-ban.


## <a name="app-deployment-actions"></a>Alkalmazástelepítési műveletek
Az alkalmazások telepítésekor a következő telepítési műveletek közül választhat:

-   **Szükséges telepítés** – az alkalmazás felhasználói beavatkozás nélkül települ az eszközön.

    > [!TIP]
    > Nem felügyelt üzemmódban működő IOS-eszközök és az összes Android-eszköz esetén az alkalmazás csak akkor települ, ha a felhasználó elfogadja az alkalmazásajánlatot.
    >
    >  Ha a felhasználó töröl egy kötelezően telepített alkalmazást, az Intune a következő leltározási ciklusban – amely általában 7 naponta következik be – automatikusan újratelepíti az alkalmazást.

-   **Elérhető telepítés** – az alkalmazás megjelenik a vállalati portálon, és a felhasználók igény szerint telepíthetik azt.

-   **Eltávolítás** – a rendszer eltávolítja az alkalmazást az eszközről.

-   **Nem alkalmazható** – az alkalmazás nem jelenik meg a vállalati portálon, és nem települ egyik eszközön sem.

#### <a name="understand-which-deployment-actions-are-available-for-each-installer-type"></a>Az egyes telepítőtípusokhoz elérhető telepítési műveletek

|Telepítő típusa|Szükséges telepítés|Elérhető telepítés|Eltávolítás|Nem alkalmazható|
|------------------|--------------------|---------------------|-------------|------------------|
|Windows-alkalmazáscsomag (felhasználói csoport számára telepített)|Igen|Igen|Igen|Igen|
|Windows-alkalmazáscsomag (eszközcsoport számára telepített)|Igen|Nem|Igen|Igen|
|Mobileszközökhöz készült alkalmazáscsomag (felhasználói csoport számára telepített)|Igen|Igen|Igen|Igen|
|Mobileszközökhöz készült alkalmazáscsomag (eszközcsoport számára telepített)|Igen|Nem|Igen|Igen|
|Windows Installer (felhasználói csoport számára telepített)|Nem|Igen|Nem|Igen|
|Windows Installer (eszközcsoport számára telepített)|Igen|Nem|Igen|Igen|
|Külső hivatkozás (felhasználói csoport számára telepített)|Nem|Igen|Nem|Igen|
|Külső hivatkozás (eszközcsoport számára telepített)|Nem|Nem|Nem|Nem|
|Felügyelt iOS-alkalmazás az App Store-ból (felhasználói csoport számára telepített)|Igen|Igen|Igen|Igen|
|Felügyelt iOS-alkalmazás az App Store-ból (eszközcsoport számára telepített)|Igen|Nem|Igen|Igen|
> [!TIP]
> Ha az alkalmazás telepítése során felhasználói és eszközcsoportokat egyaránt megad, az alkalmazást csak **Elérhető telepítés módban** telepítheti.

## <a name="deployment-conflicts"></a>A telepítés során fellépő ütközések
Arra az esetre, ha ugyanazon telepítési művelettel két telepítés érkezik egy eszközre, az alábbi szabályok vonatkoznak:

-   Az eszközcsoport számára végrehajtott telepítések elsőbbséget élveznek a felhasználói csoport számára végrehajtott telepítésekkel szemben. Ha azonban egy alkalmazást az **Elérhető** telepítési művelettel telepít egy felhasználói csoportnak, és ugyanazt az alkalmazást egy eszközcsoportnak is telepíti a **Nem alkalmazható** telepítési művelettel, a felhasználók elérhetik az alkalmazást a vállalati portálon, és telepíthetik azt.

-   A telepítési műveletek elsőbbséget élveznek az eltávolítási műveletekkel szemben.

-   Ha egy eszköz egyszerre kap szükséges és elérhető telepítést, a rendszer kombinálja a műveleteket. Más szóval a kötelező telepítés megkezdése előtt a felhasználó telepítheti az elérhető alkalmazást a vállalati portálról.


## <a name="next-steps"></a>További lépések

Ismerje meg, hogyan [telepíthet alkalmazásokat a Microsoft Intune-ban](deploy-apps-in-microsoft-intune.md).

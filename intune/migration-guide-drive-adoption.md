---
title: A végfelhasználói ösztönzése feltételes hozzáféréssel
titleSuffix: Microsoft Intune
description: Ismerje meg, hogyan ösztönözhető a regisztráció a Microsoft Intune feltételes hozzáférés használatával.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c2d7ce3f-fe97-4044-ad9e-25ac8fa301c9
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40e78d85c215bbb5cc126705f26041ce4f7786f4
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/03/2019
ms.locfileid: "67549459"
---
# <a name="drive-end-user-adoption-with-conditional-access-in-microsoft-intune"></a>A végfelhasználói ösztönzése feltételes hozzáféréssel Microsoft Intune-ban

Például a levelezés, a nem regisztrált eszközök az Intune-nal feltételes hozzáférési funkcióival segítséget, meghajtó eszközök regisztrációját és megfelelőségét, de ezek nem szükségesek a sikeres áttelepítéshez. ezt inkább az áttérési célértékek és a biztonsági követelmények alapján lehet megítélni.

## <a name="migration-campaign-with-conditional-access"></a>Migrációs kampány feltételes hozzáféréssel

Íme egy jellemző példán kerülésről egy migrációs kampány feltételes hozzáféréssel:

1. Feltételes hozzáférési szabályok kényszeríti ki az összes felhasználó számára, de konkrétan zárja ki azokat a felhasználókat, akik át kell állniuk a régi MDM-szolgáltató beállítása. Létrehozhat egy Azure AD felhasználói csoport az összes feltételes hozzáférésből kizárt felhasználóknak.

2. Felhasználók telepítheti át, a feltételes hozzáférés kizárási csoportból távolítsa el őket.

3. Áttelepítés befejezése után állítsa be az összes feltételes hozzáférési szabályzatok alapértelmezés szerint blokkolása, kivéve, ha az Intune lehetővé teszi a hozzáférést.

### <a name="advantages"></a>Előnyök

- Hozzáférés-vezérlést biztosít az új, illetve a korábbi megoldással nem felügyelt felhasználói fiókoknak is.

- Türelmi időszakot kínál az előző megoldás felhasználóinak a migrációra.

- Minimálisra szorítja a produktivitás csökkenését.

### <a name="disadvantages"></a>Hátrányok

- Az előző megoldás felhasználóinak előfordulhat hozzáférnek az erőforrásokhoz, nem felügyelt eszközök amíg feltételes hozzáférés engedélyezve van azok számára.


Ez csak egy megközelítés a sok közül: Választhat egy egyszerűbb folyamat, amely minden feltételes hozzáférést letilt, amíg késleltet minden fázist utasítást kapott regisztrálása után, vagy a feltételes hozzáférés érvénybe lépteti a pillanattól kezdve, és teljes megfelelőséget követel meg minden hozzáférés szigorúbb folyamat.

- További tudnivalók [a feltételes hozzáférésről](conditional-access.md)

## <a name="task-list-for-conditional-access"></a>Feladatlista a feltételes hozzáférés

### <a name="task-1-decide-how-you-are-going-to-implement-conditional-access"></a>1\. feladat: Annak eldöntése, hogyan kívánja a feltételes hozzáférés alkalmazása

[Feltételes hozzáférés használatának szokásos módjai](conditional-access-intune-common-ways-use.md).

### <a name="task-2-set-up-intune-conditional-access"></a>2\. feladat: Az Intune feltételes hozzáférés beállítása

Válasszon egyet az alábbi lehetőségek közül:

- [Az Azure Active Directory feltételes hozzáférés konfigurálása](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

- [A helyszíni Exchange-összekötő telepítése az Intune-nal](exchange-connector-install.md)

- [Alkalmazásalapú feltételes hozzáférési szabályzatok beállítása az Exchange online-hoz](app-based-conditional-access-intune-create.md)

- [Alkalmazásalapú feltételes hozzáférési szabályzatok beállítása a SharePoint online-hoz](app-based-conditional-access-intune-create.md)

- [Modern hitelesítés nélküli alkalmazások blokkolása (ADAL)](app-modern-authentication-block.md)

## <a name="next-steps"></a>További lépések

További tudnivalókat a [szokásos migrálási ciklus](migration-guide-cycle.md) ismertetőjében talál.

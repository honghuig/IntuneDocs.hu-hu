---
title: A Zimperium MTD integrálása a Microsoft Intune-nal
titleSuffix: Microsoft Intune
description: A Zimperium Mobile Threat Defense (MTD) beállítása a Microsoft Intune-ban a mobileszközök a vállalati erőforrásokhoz való hozzáférésének kezeléséhez.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/04/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dd666fd2ff521d7d7bca704c17fe23e157a1f933
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67528087"
---
# <a name="integrate-zimperium-with-intune"></a>A Zimperium integrálása az Intune-nal

A Zimperium mobilfenyegetések elleni megoldás Intune-beli integrálásához kövesse az alábbi lépéseket.

## <a name="before-you-begin"></a>Előkészületek

> [!NOTE]
> A következő lépéseket kell elvégezni a [Zimperium MTD-konzolon](https://www.zimperium.com/platform).

Mielőtt elkezdené a Zimperium integrálását az Intune-nal, ellenőrizze, hogy rendelkezik-e az alábbi előfizetéssel és hitelesítő adatokkal:

-   Microsoft Intune-előfizetés

-   Az Azure Active Directory globális rendszergazdájának rendszergazdai hitelesítő adataival a következő engedélyek megadására:

    -   Bejelentkezés és felhasználói profil olvasása

    -   A címtár elérése a bejelentkezett felhasználó nevében

    -   Címtáradatok olvasása

    -   Eszközadatok küldése az Intune-ba

-   Rendszergazdai hitelesítő adatok a Zimperium MTD konzol eléréséhez.

### <a name="zimperium-app-authorization"></a>A Zimperium alkalmazás engedélyezése

A Zimperium alkalmazás engedélyezési folyamata a következő:

-   Engedélyek biztosítása a Zimperium szolgáltatás az adatok az Eszközállapot vissza az Intune-hoz. Az engedélyek megadása a globális rendszergazdai hitelesítő adatokkal kell használnia. Engedélyek megadása az egy egyszeri művelet. Miután az engedélyek a globális rendszergazdai hitelesítő adatokkal nem szükségesek a napi művelethez.

-   A Zimperium szinkronizálást végez az Azure Active Directory (AD) regisztrációs csoporttagsággal az eszköz adatbázisának feltöltéséhez.

-   Engedélyezze a Zimperium felügyeleti konzolja számára az Azure AD-alapú egyszeri bejelentkezést (SSO-t).

-   Engedélyezze a Zimperium alkalmazás számára az Azure AD SSO használatát a bejelentkezéshez.

Jóváhagyás és Azure Active Directory-alkalmazásokkal kapcsolatos további információkért lásd: [engedélyeket kérhet a directory-rendszergazda](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent#request-the-permissions-from-a-directory-admin) az Azure Active Directory-cikkben *engedélyek és jóváhagyás az Azure Active Directory v2.0-végpont*.


## <a name="to-set-up-zimperium-integration"></a>A Zimperium-integráció beállítása

1.  Nyissa meg a [Zimperium MTD konzolt](https://www.zimperium.com/platform), és jelentkezzen be a hitelesítő adataival. A Zimperium-integráció telepítési folyamat végrehajtásához egy Azure Active Directory-felhasználó, aki rendelkezik a globális rendszergazdai szerepkörrel kell bejelentkeznie. Egyszeri beállítás művelet használja a globális rendszergazdai jogosultságokkal a Zimperium-alkalmazások kommunikálni az Intune-ban a szervezet engedélyt adni. 

2.  Válassza a bal oldali menü **Felügyelet** pontját.

3.  Válassza az **MDM-beállítások** panelt.

4.  Válassza az **MDM hozzáadása** elemet, majd az **MDM-szolgáltatók** listájából válassza ki a **Microsoft Intune** elemet.

5.  Miután beállította a Microsoft Intune mobileszköz-kezelési szolgáltatásként, a **a Microsoft Intune-konfiguráció** ablakban, válassza ki a **hozzáadása az Azure Active Directory** minden mód: **Zimperium zconsole-t**, **zIPS iOS- és Android-alkalmazások** Zimperium kommunikáljon az Intune és az Azure AD keresztül az Azure AD egyszeri bejelentkezés engedélyezéséhez.

    > [!IMPORTANT]  
    > Hozzá kell adnia a Zimperium zConsole, zIPS iOS és Android-alkalmazások az Intune-nal integrációs folyamat befejezéséhez.

6.  Válassza az **Elfogadás** elemet. Ezzel engedélyezi, hogy a Zimperium kommunikáljon az Intune-nal és az Azure Active Directoryval.

7.  Miután hozzáadta a **Zimperium zconsole-t** és a **zips iOS és Android-alkalmazást** az Azure AD-alkalmazások hozzáadása az Azure AD biztonsági csoportjait. A hozzáadás lehetővé teszi, hogy a Zimperium szinkronizálja a szolgáltatással az Azure AD biztonsági csoportját.

8.  A **Befejezés** elem kiválasztásával menti a konfigurációt, és elindítja az Azure AD biztonsági csoport első szinkronizálását.

9.  Jelentkezzen ki a Zimperium MTD-konzolon.

## <a name="next-steps"></a>További lépések

-   [Zimperium-alkalmazások beállítása](mtd-apps-ios-app-configuration-policy-add-assign.md)

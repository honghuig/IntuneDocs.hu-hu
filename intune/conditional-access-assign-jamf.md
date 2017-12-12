---
title: "Megfelelőségi szabályzatok alkalmazása Jamf által felügyelt eszközökön"
titlesuffix: Azure portal
description: "A megfelelőség alkalmazásával biztonságosabbá teheti a Jamf által felügyelt eszközöket."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/30/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 06cc4d70b30ec92946baefbc020aa4cda28b0c88
ms.sourcegitcommit: 520eb7712625e129b781e2f2b9fe16f9b9f3d08a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/01/2017
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Jamf Pro által felügyelt Mac számítógépek megfelelőségének kikényszerítése

|A következőkre vonatkozik: Intune az Azure Portalon |
|--|
|A klasszikus portálbeli Intune-ról keres dokumentációt? [Lépjen tovább ide](/intune/introduction-intune?toc=/intune-classic/toc.json).|
| |

|Jelenleg Private Preview verzióban|
|--|
|A jelen témakörben leírt funkciók jelenleg csak Private Preview verzióban érhetők el az ügyfelek számára. Miután a verzió minden felhasználó számára elérhetővé vált, eltávolítjuk ezt a megjegyzést.|
| |

Az Azure Active Directory és a Microsoft Intune feltételes hozzáférési szabályzatai biztosítják, hogy a végfelhasználók megfeleljenek a szervezeti követelményeknek. Ezeket a szabályzatokat a [Jamf Pro által felügyelt](conditional-access-integrate-jamf.md) Mac számítógépekre is alkalmazhatja. Ennek megvalósításához az Intune és a Jamf Pro konzolhoz egyaránt hozzáférésre van szüksége.

## <a name="set-up-device-compliance-policies-in-intune"></a>Eszközmegfelelőségi szabályzatok beállítása az Intune-ban

1. Nyissa meg a Microsoft Azure-t, majd az **Intune** > **Eszközmegfelelőség** > **Szabályzatok** oldalt. Szabályzatokat hozhat létre macOS eszközökre, beleértve számos, nem megfelelő felhasználókra és csoportokra vonatkozó műveletet (pl. figyelmeztető e-mailek küldése).
2. Keresse meg a kívánt csoportokat, és alkalmazza rájuk a szabályzatokat.

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>A macOS-hez készült Vállalati portál alkalmazás üzembe helyezése a Jamf Pro szolgáltatásban

A macOS-hez készült Vállalati portál alkalmazást kétféleképpen helyezheti üzembe a Jamf Pro szolgáltatásban:

- Elérhetővé teheti a Vállalati portál alkalmazás példányát a Jamf Self Service szolgáltatásban, vagy
- Háttérbeli telepítésként, melynek esetében a felhasználók az alábbi eljárást fogják követni:

1. A macOS-eszközön töltse le a [macOS-hez készült céges portál alkalmazás](https://go.microsoft.com/fwlink/?linkid=862280) jelenlegi verzióját.
2. Nyissa meg a Jamf Pro szolgáltatást, majd a **Számítógép-kezelés** > **Csomagok** oldalt.
3. Hozzon létre egy új csomagot a macOS-hez készült Céges portál alkalmazással, majd kattintson a **Mentés** elemre.
4. Nyissa meg a **Számítógépek** > **Szabályzatok** oldalt, majd kattintson az **Új** elemre.
5. Az **Általános** tartalom használatával konfigurálja a szabályzat beállításait. A következő beállításokat kell használnia: 
   - Eseményindító: válassza a **Regisztráció kész** és az **Ismétlődő bejelentkezés** beállítást.
   - Végrehajtás gyakorisága: válassza a **Számítógépenként egyszer** beállítást.
6. Válassza ki a **Csomagok** tartalmat, és kattintson a **Konfigurálás** elemre.
7. A **Hozzáadás** elemre kattintva válassza ki a csomagot a Céges portál alkalmazással.
8. A felugró **Művelet** menüből válassza ki a **Telepítés** lehetőséget.
9. Konfigurálja a csomag beállításait.
10. Kattintson a **Hatókör** lapra annak meghatározásához, hogy mely számítógépeken kell telepíteni a Céges portál alkalmazást. Kattintson a **Mentés**gombra. Legközelebb, amikor a megadott eseményindító kiváltódik a számítógépen, és megfelel az **Általános** tartalomban szereplő feltételeknek, a szabályzat lefut a hatókörbe bevont eszközökön.

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>Szabályzat létrehozása a Jamf Pro szolgáltatásban a felhasználók eszközének Azure Active Directoryban való regisztrálásához

> [!NOTE]
> A következő lépések előtt [üzembe kell helyeznie a macOS-eszközökhöz készült Céges portált](conditional-access-assign-jamf.md#require-the-company-portal-app-for-macos).  

Ahhoz, hogy az eszközt Jamf Pro által kezelt eszközként regisztrálhassák az Azure AD szolgáltatásban, a végfelhasználóknak a Jamf Self Service oldalról kell megnyitniuk a Céges portál alkalmazást. Ez egy művelet végrehajtását fogja igényelni a végfelhasználók részéről. Javasoljuk, hogy [lépjen kapcsolatba a végfelhasználókkal](end-user-educate.md) e-mailben, Jamf Pro-értesítésben vagy más módon, és kérje meg őket, hogy kattintsanak a gombra a Jamf Self Service szolgáltatásban.

> [!WARNING]
> Az eszközregisztráció sikeres megkezdéséhez a Céges portál alkalmazást mindenképpen a Jamf Self Service szolgáltatásból kell indítani. <br><br>A Céges portál alkalmazás manuális – például az alkalmazások vagy a letöltések mappájából való – indítása esetén az eszköz nem lesz regisztrálva. Ha egy végfelhasználó manuálisan indítja a Céges portál alkalmazást, az „AccountNotOnboarded” figyelmeztetést fogja látni.

1. A Jamf Pro oldalán nyissa meg a **Számítógépek** > **Szabályzatok** oldalt, és hozzon létre egy új eszközregisztrációs szabályzatot.
2. Konfigurálja a **Microsoft Intune-integráció** tartalmat, beleértve az eseményindítót és a végrehajtás gyakoriságát is. Állítsa a prioritást az **Utána** lehetőségre.
3. A **Hatókör** lapra kattintva terjessze ki a szabályzat hatókörét az összes megcélzott eszközre.
4. A **Self Service** lapra kattintva tegye elérhetővé a szabályzatot a Jamf Self Service szolgáltatásban. Adja hozzá a szabályzatot az **Eszközmegfelelőség** kategóriához. Kattintson a **Mentés**gombra.

## <a name="next-steps"></a>További lépések

- [Feltételes hozzáférés az Azure Active Directoryban](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Ismerkedés a feltételes hozzáféréssel Azure Active Directoryban](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
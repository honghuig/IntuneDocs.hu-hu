---
title: E-mail-beállítások konfigurálása a Microsoft Intune-ban – Azure | Microsoft Docs
titleSuffix: ''
description: E-mail-profilt hozhat létre a Microsoft Intune-ban, majd üzembe helyezheti ezt a profilt Android Enterprise-, iOS- és Windows-eszközökön. E-mail-profil használatával olyan gyakori e-mail-beállítások konfigurálhatók, mint a levelezési kiszolgáló, és az Ön által felügyelt eszközökön a vállalati levelezéshez való csatlakozáshoz használt hitelesítési módszer.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/10/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b579849d9afdb50470b7a772e003cc616e1f94a0
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67530050"
---
# <a name="add-email-settings-to-devices-using-intune"></a>E-mail-beállítások hozzáadása az Intune-t használó eszközökhöz

A Microsoft Intune különböző e-mail-beállításokat tartalmaz, amelyeket alkalmazhat a vállalati eszközökön. A rendszergazda e-mail-profilok olyan beállításokkal, például az Office 365 és a Gmail egy levelezési kiszolgálóhoz csatlakozni hoz létre. A végfelhasználók majd csatlakoztatása, hitelesítést és szinkronizálása a vállalati e-mail fiókjukat a mobileszközükön. Létrehozásával és központi telepítése egy e-mail-profilt, ellenőrizheti, számos eszközön egységesek legyenek a beállítások. Ezáltal a helyes e-mail-beállításokat nem ismerő végfelhasználóktól érkező támogatási hívások száma is csökkenthető.

E-mail-profilok segítségével a következő eszközökön konfigurálhatók a beépített e-mail-beállítások:

- Android Samsung Knox Standard (4.0-s és újabb verziók)
- Vállalati Android
- iOS 8.0 és újabb verziók
- Windows Phone 8.1 és újabb verziók
- Windows 10 (asztali rendszer) és Windows 10 Mobile

Ez a cikk azt mutatja be, hogyan hozható létre e-mail-profil a Microsoft Intune-ban. Az egyes platformok különleges beállításaira mutató hivatkozásokat is tartalmaz.

## <a name="create-a-device-profile"></a>Eszközprofil létrehozása

1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg az e-mail-profil **Nevét** és **Leírását**.
4. Válassza ki **Platformját** a legördülő listából. A választható lehetőségek:

    - **Android** (csak Samsung Android Knox Standard esetén)
    - **Vállalati Android**
    - **iOS**
    - **Windows Phone 8.1**
    - **Windows 10 és újabb**

5. A **Profil típusa** legördülő listában válassza az **E-mail** lehetőséget.
6. A konfigurálható beállítások platformonként eltérőek lehetnek. A specifikus beállítások megtekintéséhez válassza ki platformját:

    - [Android Samsung Knox Standard beállításai](email-settings-android.md)
    - [Az Android Enterprise-beállításai](email-settings-android-enterprise.md)
    - [iOS-beállítások](email-settings-ios.md)
    - [Windows Phone 8.1-beállítások](email-settings-windows-phone-8-1.md)
    - [Windows 10-beállítások](email-settings-windows-10.md)

A beállítások megadása és a profil létrehozása után a profil megjelenik a profilok listájában. A következő lépés a [profil hozzárendelése egyes csoportokhoz](device-profile-assign.md).

## <a name="remove-an-email-profile"></a>E-mail-profil eltávolítása

Az e-mail-profilok felhasználói csoportok helyett eszközcsoportokhoz vannak hozzárendelve. Az e-mail-profilokat az eszközről többféle módon lehet eltávolítani, még akkor is, ha az eszközön csak egy e-mail-profil található:

- **1. lehetőség**: Nyissa meg az e-mail-profil (**eszközkonfiguráció** > **profilok**), és válassza a **hozzárendelések**. A **Belefoglalás** lapon jelennek meg a profilhoz rendelt csoportok. Kattintson a jobb gombbal a csoportra, majd válassza az **Eltávolítás** lehetőséget. Ne felejtse el **menteni** a módosításokat.

- **2. lehetőség**: [Törölhetik vagy vonhatják vissza az eszköz](devices-wipe.md). A következő műveletekkel az összes adatot és beállítást, vagy azok egy részét is eltávolíthatja.

## <a name="secure-email-access"></a>Biztonságos e-mail-hozzáférés

Az e-mail-profilok biztonsága az alábbi módszerekkel fokozható:

- **Tanúsítványok**: Az e-mail-profil létrehozásakor válassza ki az Intune-ban korábban már létrehozott tanúsítványprofilt. Ez a tanúsítvány identitástanúsítványként is ismert. Ez hajtja végre a hitelesítést egy megbízható tanúsítványprofillal vagy főtanúsítvánnyal, így ellenőrizve, hogy a felhasználó eszközének csatlakoztatása engedélyezve van-e. A megbízható tanúsítvány az e-mail-kapcsolatot hitelesítő számítógéphez van rendelve. Ez a számítógép általában a natív levelezési kiszolgáló.

  A tanúsítványprofiloknak az Intune-ban történő létrehozásáról és használatáról a következő dokumentumban olvashat bővebben: [Tanúsítványok konfigurálása az Intune-nal](certificates-configure.md).

- **Felhasználónév és jelszó**: A felhasználó a natív levelezési kiszolgálón a felhasználónév és jelszó megadásával hitelesíti magát. A jelszó nem szerepel az e-mail-profilban. Így a végfelhasználó kell írnia a jelszót e-mailben való csatlakozáskor.

## <a name="how-intune-handles-existing-email-accounts"></a>Hogyan kezeli az Intune a meglévő e-mail-fiókokat?

Ha a felhasználó már konfigurált e-mail-fiókot, az e-mail-profil a platformtól függően, másként lesz hozzárendelve.

- **iOS**: A rendszer az állomásnév és az e-mail-cím alapján egy már meglévő e-mail-profilt észlel. Az ugyanezeket az adatokat tartalmazó e-mail-profil megakadályozza az Intune-profil hozzárendelését. Ebben az esetben a vállalati portál alkalmazás értesíti a felhasználót, hogy nem megfelelő, és felszólítja a végfelhasználót, manuálisan kell eltávolítania a konfigurált profil. Ebben a forgatókönyvben megelőzése érdekében ossza meg a végfelhasználók regisztrálhatják *előtt* egy e-mail profilt, amely lehetővé teszi az Intune a profil telepítése.

- **Windows:** A rendszer az állomásnév és az e-mail-cím alapján egy már meglévő e-mail-profilt észlel. Az Intune felülírja a végfelhasználók által létrehozott meglévő e-mail profilt.

- **Android Samsung Knox Standard**: A rendszer az e-mail-cím alapján egy már meglévő e-mail-profilt észlel, és felülírja az Intune-profillal. Az Android nem használ állomásnevet a profil azonosításához. Ne hozzon létre több e-mail-profilt ugyanazt az e-mail-címet több állomáson használva. A profilok felülírják egymást.

- **Androidos munkahelyi profilokat**: Az Intune két Android munkahelyi e-mail-profilok kínál: egyet a Gmail alkalmazás, és egyet a Nine Work alkalmazáshoz. Ezek az alkalmazások a Google Play áruházból érhetők el, és telepíthetők az eszköz munkahelyi profiljába. Ezek az alkalmazások ne hozzon létre ismétlődő profilokat. Mindkét alkalmazás támogatja az Exchange-kapcsolatokat. E-mail-kapcsolat használatához helyezze üzembe ezeknek az levelezőalkalmazásoknak az egyikét a felhasználók eszközén. Ezután hozza létre és helyezze üzembe a megfelelő e-mail-profilt. Lehetséges, hogy egyes e-mail-alkalmazások, például a Nine Work, nem ingyenesek. Olvassa el az alkalmazás licencelési információit, vagy kérdés esetén lépjen kapcsolatba az alkalmazás kibocsátójával.

## <a name="changes-to-assigned-email-profiles"></a>Hozzárendelt e-mail-profilok módosításai

Ha egy már hozzárendelt e-mail-profilt módosít, a végfelhasználókat a rendszer arra kérheti, hogy fogadják el az e-mail-beállítások újrakonfigurálását.

## <a name="next-steps"></a>További lépések

A létrehozott profil egyelőre semmit sem csinál. Ezután [a profil hozzárendelése az egyes eszközök](device-profile-assign.md).

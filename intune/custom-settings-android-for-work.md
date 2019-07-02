---
title: Egyéni beállítások hozzáadása Android Enterprise-eszközökhöz a Microsoft Intune-ban – Azure | Microsoft Docs
description: Egyéni profilok hozzáadása vagy létrehozása Android Enterprise-eszközökhöz a Microsoft Intune-ban
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/01/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7d1aa7cffd91049527df25436c083e97b849c229
ms.sourcegitcommit: 2db7dc2baea0c159f70338e6a0529acc89580773
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67500672"
---
# <a name="use-custom-settings-for-android-enterprise-devices-in-microsoft-intune"></a>Egyéni beállítások használata Android Enterprise-eszközökhöz a Microsoft Intune-ban

A Microsoft Intune-nal, hozzáadása, vagy hozzon létre egyéni beállítások az Android Enterprise munkahelyi profil eszközökhöz profillal "egyéni". Az egyéni profilok az Intune részét képezik. Akkor hasznosak, ha olyan eszközbeállításokat és funkciókat szeretne használni, amelyek nem érhetők el beépítetten az Intune-ban.

Az Android Enterprise rendszer egyéni profiljai az Open Mobile Alliance Uniform Resource Identifier (OMA-URI) beállításokat használják a különböző funkciók vezérléséhez Android Enterprise-eszközökön. Ezekkel a beállításokkal általában a mobileszközgyártók vezérlik ezeket a funkciókat.

Az Intune Android Enterprise egyéni profilok, beleértve a korlátozott számú támogatja:

- ./Vendor/MSFT/WiFi/Profile/SSID/Settings: [Wi-Fi profil létrehozása előmegosztott kulccsal ellátott](wi-fi-profile-shared-key.md) rendelkezik néhány példa.
- ./Vendor/MSFT/VPN/Profile/Name/PackageList: [Alkalmazásonkénti VPN-profil létrehozása](android-pulse-secure-per-app-vpn.md) rendelkezik néhány példa.
- ./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste: Tekintse meg a [példa](#example) (a jelen cikkben).

Ha további beállításokat van szüksége, tekintse meg [Android Enterprise OEMConfig](android-oem-configuration-overview.md).

Ebből a cikkből megtudhatja, hogyan hozhat létre egyéni profilt az Android Enterprise-eszközök számára. Emellett egy olyan egyéni profilra is mutat példát, amely nem engedélyezi a másolást és a beillesztést.

## <a name="create-the-profile"></a>A profil létrehozása

1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg a következő beállításokat:

    - **Név**: Adja meg egy nevet a profilnak, például: `android enterprise custom profile`
    - **Description** (Leírás): Adja meg a profil leírását
    - **Platform**: Válasszon **Android Enterprise**
    - **Profil típusa**: Válasszon **egyéni**

4. Az **Egyéni OMA-URI-beállítások** menüben válassza a **Hozzáadás** lehetőséget. Adja meg a következő beállításokat:

    - **Név**: Adja meg egy egyedi nevet az OMA-URI beállítás számára, hogy könnyen megtalálhassa.
    - **Description** (Leírás): Adjon meg egy leírást, amely áttekintést ad a beállítást, és bármilyen egyéb fontos részleteket.
    - **OMA-URI**: Adja meg az OMA-URI beállításai használni kívánt.
    - **Adattípus**: Válassza ki az adatokat fogja használni az OMA-URI-beállítás. A választható lehetőségek:

      - Sztring
      - Sztring (XML-fájl)
      - Dátum és időpont
      - Egész szám
      - Lebegőpontos szám
      - Logikai
      - Base64 (fájl)

    - **Érték**: A megadott OMA-URI társítani kívánt adatok értéket adjon meg. Az érték a választott adattípustól függ. A **Dátum és idő** típus esetén például a dátumválasztóból választhat értéket.

    Néhány beállítás megadása után válassza az **Exportálás** lehetőséget. Az **Exportálás** a hozzáadott értékek listáját hozza létre egy vesszővel tagolt (.csv) fájlban.

5. Válassza ki **OK** a módosítások mentéséhez. Szükség szerint adjon hozzá további beállításokat.
6. Ha elkészült, az Intune-profil létrehozásához kattintson az **OK** > **Létrehozás** lehetőségre. Ha a profil elkészült, megjelenik az **Eszközkonfiguráció – Profilok** listában.

## <a name="example"></a>Példa

Ebben a példában egy olyan egyéni profil jön létre, amely nem engedélyezi a másolási és a beillesztési műveleteket a munkahelyi és a személyes alkalmazások között Android Enterprise-eszközökön.

1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg a következő beállításokat:

    - **Név**: Adja meg egy nevet a profilnak, például `android ent block copy paste custom profile`.
    - **Description** (Leírás): Adja meg a profil leírását.
    - **Platform**: Válasszon **Android Enterprise**.
    - **Profil típusa**: Válasszon **egyéni**.

4. Az **Egyéni OMA-URI-beállítások** menüben válassza a **Hozzáadás** lehetőséget. Adja meg a következő beállításokat:

    - **Név**: Adja meg az alábbihoz hasonló `Block copy and paste`.
    - **Description** (Leírás): Adja meg az alábbihoz hasonló `Blocks copy/paste between work and personal apps`.
    - **OMA-URI**: Adja meg `./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste`.
    - **Adattípus**: Válasszon **logikai** , ez az OMA-URI értéke **igaz** vagy **hamis**.
    - **Érték**: Válasszon **igaz**.

5. Miután megadta a beállításokat, a környezetének a képhez hasonlónak kell kinéznie:

    ![Tiltsa le a másolást és a beillesztést az androidos munkahelyi profilban.](./media/custom-policy-afw-copy-paste.png)

Amikor hozzárendeli ezt a profilt az Ön által felügyelt Android Enterprise-eszközökhöz, a másolás és a beillesztés nem lesz engedélyezett a munkahelyi és a személyes profilok alkalmazásai között.

## <a name="next-steps"></a>További lépések

A profil létrejött, de egyelőre nem csinál semmit. Következő lépésként [végezze el a profil hozzárendelését](device-profile-assign.md).

Tekintse meg, hogyan [hozhat létre profilokat Android-eszközökön](custom-settings-android.md).

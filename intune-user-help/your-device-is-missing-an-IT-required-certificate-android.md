---
title: Az eszközhöz hiányzik egy tanúsítvány | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/04/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f0ba4cbb-ef0a-4335-86bf-f1d006867fa2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6bdf97e6a36a49bc6df5a182af7676c357440f3e
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67529326"
---
# <a name="your-android-device-is-missing-a-certificate-required-by-your-company-support"></a>Az androidos eszközhöz hiányzik egy, a cég informatikai támogató szolgálata által kért tanúsítvány

Ha az eszköz nincs regisztrálva az Intune-ban, és hiányzik róla egy, a cég informatikai támogatási szolgálata által kért tanúsítvány, nem fog tudni bejelentkezni a Céges portál alkalmazásba. Amikor megpróbál bejelentkezni, a következő üzenet jelenik meg:

![képernyőfelvétel-hibaüzenet-hiányzó-tanúsítványról](./media/andr-cert_install-1-cert_missing.png)

A probléma megoldásához és a szükséges tanúsítvány beszerzéséhez hajtsa végre a következő két fő lépést:

- Azonosítsa a hiányzó tanúsítványt azáltal, hogy megtekinti egy vállalati vagy iskolai számítógépen.
- Használja az eszközt a hiányzó tanúsítvány letöltéséhez az internetről.

## <a name="identify-the-missing-certificate-by-looking-on-a-company-or-school-pc"></a>Azonosítsa a hiányzó tanúsítványt azáltal, hogy megtekinti egy vállalati vagy iskolai számítógépen

1. Nyissa meg egy számítógépen az Internet Explorert. Ha nincs erre a célra használható számítógépe, forduljon a cég informatikai támogató szolgálatához. A cég informatikai támogató szolgálatának elérhetőségét a [Céges portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980) találja.

2. Lépjen a [Céges portál webhelyére](https://go.microsoft.com/fwlink/?linkid=2010980), és jelentkezzen be a munkahelyi vagy iskolai fiókjával.

3. A böngésző címsorának jobb szélén válassza az alábbi képernyőképen látható, lakat alakú szimbólumot.

    ![képernyőfelvétel-internet-explorer-címsor-lakat-szimbólum](./media/andr-missing-cert-ie-padlock-symbol.png)

    Ha nem látja a lakat alakú szimbólumot, ne lépjen tovább, hanem forduljon a cég informatikai támogató szolgálatához. A lakat azt jelenti, hogy biztonságosan jelentkezett be, ezért ha nem látja a szimbólumot, nem javasolt a továbblépés.

4. Válassza a **Tanúsítványok megtekintése** elemet.

    ![képernyőfelvétel-internet-explorer-tanúsítvány-megtekeintése-gomb-webhely-azonosítási-párbeszédpanelén](./media/andr-missg-cert-ie-view-cert-button.png)

5. A **Tanúsítvány** párbeszédpanelen válassza a **Tanúsítványlánc** elemet, majd azonosítsa a tanúsítványt, amelyet le kell töltenie az internetről. A szükséges tanúsítvány neve ugyanazon a helyen lesz, mint az előbbi képernyőfelvételen kiemelt tanúsítványé.

## <a name="download-and-install-the-missing-certificate-on-your-android-mobile-device"></a>Töltse le és telepítse a hiányzó tanúsítványt Android-mobileszközére

1. Ha keresőmotort, például Binget vagy Google-t használ, keressen rá az előző szakaszban azonosított hiányzó tanúsítvány nevére. A tanúsítvány különböző „kiterjesztésekkel” rendelkezhet, például „.crt”, „.pem” stb.

2. Töltse le a főtanúsítványt a webhelyről.

3. Miután a tanúsítvány letöltése befejeződött, húzza le az értesítéseket fentről, és koppintson a tanúsítvány nevére az értesítések listájában.

4. Az alábbi képernyőképen látható **Name the Certificate** (A tanúsítvány elnevezése) párbeszédpanelben fogadja el az alapértelmezett tanúsítványnevet.

5. Győződjön meg arról, hogy **Credential Use** (Hitelesítő adatok használata) beállítás értéke **Used for VPN and apps** (VPN-hez és az alkalmazásokhoz használt), és koppintson az **OK** gombra.

    ![képernyőkép-tanúsítványnevet-mutató-képernyő](./media/andr-missing-cert-cert-name.png)

6. Zárja be a Céges portál alkalmazást.

7. Nyissa ismét meg a Céges portál alkalmazást. Ekkor már be kell, hogy tudjon jelentkezni a Céges portál alkalmazásba. Ha segítségre van szüksége, lépjen kapcsolatba a cég informatikai támogató szolgálatával.

Ha ugyanazt a „Hiányzó tanúsítvány” üzenetet látja, mint amelyik fentebb is látható, és már követte a fenti lépéseket, akkor valószínűleg egy másik tanúsítvány is van, amelyet a cég informatikai támogató szolgálatának segítségével telepíteni kell. Kérje a cég informatikai támogató szolgálatának segítségét a [Céges portál webhelyen](https://go.microsoft.com/fwlink/?linkid=2010980) található elérhetőségeken.

---
title: Az Intune tesztelése és ellenőrzése
titleSuffix: Microsoft Intune
description: Teljes mértékben felhőalapú Intune-megoldás tesztelése és ellenőrzése saját környezetben.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 3/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4f82ee0c-4bd6-4623-9b10-9249d316ccf5
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7aaeb94aad7e31c3346b088239024c14f9e190da
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/03/2019
ms.locfileid: "67549353"
---
# <a name="intune-testing-and-validation"></a>Az Intune tesztelése és ellenőrzése

A Microsoft Intune üzemelésének tesztelésénél javasoljuk, hogy végezzen működésbeli ellenőrzést és különféle használati eseteken alapuló ellenőrzést. A funkcionális ellenőrzési tesztelés során minden egyes összetevő és konfiguráció tesztelésre kerül, melynek során megállapítható, hogy azok megfelelően működnek-e. A használati eseteken alapuló ellenőrzés részeként tesztelni érdemes, hogy többféle feladatot magában foglaló esetekben is megfelelő működés tapasztalható-e. 

A tesztelési folyamatba ajánlatos bevonni az informatikai és a támogatási munkatársakat, így elkészíthető a támogatási dokumentáció, és biztosítható, hogy a támogatási munkatársak megfelelő támogatást tudjanak nyújtani a termékhez. Ha a használati esetek alapján egyes összetevők vagy forgatókönyvek nem működnek megfelelően, a szükséges változtatásokat a változtatás okának feltüntetésével dokumentálni érdemes.

## <a name="before-you-begin"></a>Előkészületek

Ajánlott dokumentálni a következőket:

- **Tesztkritériumok:** Azonosítsa a referenciaalapok elleni mért.

- **Szerkezeti összetevők:** Léteznie kell legalább egy tesztkritériumban.

Ha egy adott szerkezeti összetevő nem szerepel legalább egy olyan tesztkritériumban, amely követelményhez vagy forgatókönyvhöz társul, érdemes megfontolni, valóban szükség van-e rá. Az alábbiak ugyancsak szükségesek:

- **Fiókok:** Az EMS és az összes használatieset-forgatókönyvek teszteléséhez Office 365-licencek tesztelni.

- **Eszközök:** Tesztelési célú eszközöket gyári beállítások visszaállítása vagy tartalmának végleges törléséig.

- **Integrációs összetevők:** Integrálási összetevőket (tanúsítvány-összekötőt, és a helyszíni Intune Exchange connector) kell telepíteni, és szükség esetén konfigurálva.

Az előre nem látható problémák elhárításához szerkezetátalakításokra lehet szükség. Minden szerkezeti változást teljes körűen dokumentálni kell a változás okának feltüntetésével. Az alábbi példa azt mutatja meg, mi indokolhat ilyen változást:

<blockquote>Kiderülhet, hogy nem teljesülnek az NDES (hálózati eszközök tanúsítványigénylési szolgáltatása) feltételei, mindemellett azonban legfelső szintű hitelesítésszolgáltatóval is konfigurálhatók a VPN- és a Wi-Fi profilok, és így is teljesíthetők ugyanezen feltételek NDES-megoldás nélkül is.</blockquote>

Előfordulhat, hogy a tesztelés és ellenőrzés során olyan problémák vagy kérdések merülnek fel, amelyek műszaki útmutatást vagy speciális hibaelhárítást tesznek szükségessé. Javasoljuk, hogy forduljon segítségért a Microsofthoz valamely támogatási csatornáján keresztül.

- [Útmutató Intune-támogatás kéréséhez](get-support.md)

- [Kapcsolatfelvétel a Microsoft Intune telefonos tanácsadással](get-support.md)

## <a name="functional-validation-testing"></a>Funkcionális ellenőrzési tesztelés

A funkcionális ellenőrzési tesztelés során minden egyes összetevő és konfiguráció tesztelésre kerül, melynek során megállapítható, hogy azok megfelelően működnek-e. Az alábbi táblázatban a funkcionális ellenőrzési tesztelésre látható példa.

![9\. szakasz, 1. táblázat](./media/section-9-image-1-table.PNG)

## <a name="use-case-validation-testing"></a>Használatieset-ellenőrzési tesztelés

A használatieset-ellenőrzési tesztelés a használati forgatókönyvek teljességének és működőképességének tesztelésére szolgál. Használati esetek két típusa van: Rendszergazdai és végfelhasználói.

### <a name="it-admin"></a>Rendszergazdai

A rendszergazdai ellenőrzési tesztelés célja annak ellenőrzése, hogy az eszközökre és a felhasználókra irányuló rendszergazdai tevékenységek megfelelően működnek-e. Az alábbiakban egy teljes körű rendszergazdai ellenőrzésre talál példát.

![9\. szakasz, 2. táblázat](./media/section-9-image-2-table.PNG)

### <a name="end-user"></a>Végfelhasználó

A végfelhasználói ellenőrzési tesztelés célja annak ellenőrzése, hogy a végfelhasználói élmény az elvárásoknak megfelelő-e, és hogy megfelelően jelenik-e meg minden felhasználói kommunikáció során. Fontos ellenőrizni, hogy megfelelő-e a végfelhasználói élmény. Ennek elmaradása a bevezetési szakasz sikerét csökkentheti, és a támogatási segítségkérések számának megnövekedéséhez vezethet.

![9\. szakasz, 3. táblázat](./media/section-9-image-3-table.PNG)

## <a name="next-steps"></a>További lépések

Most, hogy elvégezte az Intune funkcionális és használatieset-forgatókönyveinek ellenőrzését és tesztelését, készen áll az [Intune használatára éles környezetben](planning-guide-rollout-plan.md).

További tervezési sablonokért és információkért lásd a [további erőforrásokat](planning-guide-resources.md).

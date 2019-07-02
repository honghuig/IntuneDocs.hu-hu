---
title: Samsung Knox mobileszköz beléptetési használata Android-eszközök automatikus regisztrálása
titleSuffix: Microsoft Intune
description: Útmutató az Android-eszközök a Samsung KME-vel történő regisztrálásához
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: ''
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 30df0f9e-6e9e-4d75-a722-3819e33d480d
ms.reviewer: arnab
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d07d9466cda86270898d0e54e8d50b358bcb1b84
ms.sourcegitcommit: 116ef72b9da4d114782d4b8dd9f57556c9b01511
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/01/2019
ms.locfileid: "67494103"
---
# <a name="automatically-enroll-android-devices-by-using-samsungs-knox-mobile-enrollment"></a>Eszközök automatikus regisztrációja a Samsung Knox Mobile Enrollmenttel

Ez a témakör segít beállítani az Intune-t támogatott Android-eszközök a Samsung Knox Mobile Enrollmenttel (KME-vel) történő regisztrációjához. Az Intune a Samsung Knox Mobile Enrollmenttel (KME-vel) való használatával nagy mennyiségű céges tulajdonú Android-eszközt regisztrálhat, amikor a végfelhasználók először bekapcsolják az eszközüket, és egy Wi-Fi- vagy mobilhálózathoz csatlakoznak. A Knox Deployment App használatával az eszközök Bluetooth vagy NFC segítségével is regisztrálhatók.

Ha engedélyezni szeretné a Samsung KME-vel történő Intune-regisztrációt, az Intune és a Samsung Knox portálját is használnia kell, ebben a sorrendben:

1. A Knox portálján:
    1. [Hozzon létre egy MDM-profilt](#create-mdm-profile)
    2. [Adjon hozzá eszközöket](#add-devices)
    3. [Rendeljen hozzá MDM-profilokat az eszközökhöz](#assign-an-mdm-profile-to-devices)
2. A Knox portálon [konfigurálja a végfelhasználói bejelentkezést](#configure-how-end-users-sign-in).
3. [Terjessze az eszközöket](#distribute-devices).


A rendszer automatikusan hozzáadja az eszközazonosítókat (a sorozatszámokat és az IMEI-ket) a Knox portálhoz, amikor a Knox Deployment Programban részt vevő hivatalos viszonteladóktól vásárol eszközöket.


## <a name="prerequisites"></a>Előfeltételek

Ha regisztrálni szeretne eszközöket az Intune-ban a KME-vel, először a cégét kell regisztrálnia a Samsung Knox portálon. Ehhez kövesse az alábbi lépéseket:
1.  [Ellenőrizze, hogy az Ön régiójában érhető el KME](https://www.samsungknox.com/en/solutions/it-solutions/knox-configure/available-countries): KME több mint 55 országban érhető el. Győződjön meg róla, hogy az üzembe helyezés országa támogatott.

2.  [Támogatott eszközök](https://www.samsungknox.com/en/knox-platform/supported-devices/2.4+): Az összes Samsung-eszközök az Android-eszközök regisztrálási Knox 2.4 legalább és az Android vállalati regisztrációjának Knox 2.8 legalább KME érhető el.

3.  [Hálózati követelmények](https://docs.samsungknox.com/KME-Getting-Started/Content/firewall_exceptions.htm): Győződjön meg arról, hogy a szükséges tűzfal és a hálózatelérési szabályok használata engedélyezett a hálózaton.

4.  [Samsung-fiók regisztrálása](https://www2.samsungknox.com/en/user/register): Egy Samsung-fiók regisztrálása és KME engedélyezése és kezelése egyetlen helyen történő összes Knox vállalati jogosultságok van szükség.

5.  Regisztráció áttekintése: Után profilját befejeződött, és elküldeni, Samsung áttekinti az alkalmazást, és akár azonnal engedélyezi, vagy állapotba állítja azt egy folyamatban lévő felülvizsgálati további nyomon követés céljából. A fiók jóváhagyása után továbbhaladhat a következő lépésekre.

## <a name="create-mdm-profile"></a>MDM-profil létrehozása

Miután sikeresen regisztrálta a cégét, az alábbi adatokkal létrehozhat egy Microsoft Intune-os MDM-profilt a Knox portálon. A Knox portálon Android-és Android Enterprise-eszközökhöz egyaránt létrehozhat MDM-profilokat. 

### <a name="for-android-enterprise"></a>Android Enterprise számára

| MDM-profil – mezők| Kötelező? | értékek | 
|-------------------|-----------|-------| 
|MDM-kiszolgáló URI-azonosítója     | Nem        |Hagyja üresen a mezőt. 
|Profilnév       | Igen       |Adjon meg egy profilnevet. 
|Leírás        | Nem        |Adjon meg egy leírást a profilhoz. 
|MDM-ügynök APK-ja      | Igen       |https://aka.ms/intune_kme_deviceowner 
|Az alkalmazás engedélyezése Google-eszköztulajdonosként | Igen | A lehetőség kiválasztásával Android Enterprise-ként regisztrálhatja az eszközt. 
|Támogatott mobileszköz-kezelés      | Igen       |Microsoft Intune 
|A rendszeralkalmazások engedélyezettek maradnak | Nem | A lehetőség kiválasztásával biztosíthatja, hogy az összes alkalmazás engedélyezve legyen, és elérhető legyen a profilhoz. Ha ez a beállítás nincs bejelölve, csak nagyon korlátozott számú rendszeralkalmazás jelenik meg az eszköz alkalmazástálcáján. Az olyan alkalmazások, mint például az e-mail-alkalmazás, rejtve maradnak. 
|Egyéni JSON        | Nem        |{"com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN": "Adja meg az Intune regisztrációs jogkivonat-karakterláncot"}. Ismerje meg, a [Beléptetési profil létrehozásának](android-kiosk-enroll.md) folyamatát. 
| Jogi szerződések hozzáadása | Nem | Hagyja üresen a mezőt. 

### <a name="for-android"></a>Android rendszerhez

Lépésenkénti útmutatásért tekintse meg a [Samsung Knox profil beállítása varázsló](https://docs.samsungknox.com/KME-Getting-Started/Content/getting-started-wizard.htm) utasításokat.

| MDM-profil – mezők| Kötelező? | értékek |
|-------------------|-----------|-------|
|MDM-kiszolgáló URI-azonosítója     | Nem        |Hagyja üresen a mezőt.
|Profilnév       | Igen       |Adjon meg egy profilnevet.
|leírás        | Nem        |Adjon meg egy leírást a profilhoz.
|MDM-ügynök APK-ja      | Igen       |https://aka.ms/intune_kme
|Az alkalmazás engedélyezése Google-eszköztulajdonosként | Nem | Android esetén hagyja üresen a beállítást. A beállítás csak Android Enterprise esetén érvényes.
|A telepítővarázsló kihagyása  | Nem        |Válassza ezt a beállítást, ha ki szeretné hagyni a szabványos eszközbeállítási lépéseket a végfelhasználó nevében.
|Regisztráció megszakításának engedélyezése a végfelhasználó számára | Nem | Válassza ezt a beállítást, ha engedélyezni szeretné a felhasználók számára, hogy megszakítsák a KME-t.
|Egyéni JSON        | Nem        |Hagyja üresen a mezőt.
| Jogi szerződések hozzáadása | Nem | Hagyja üresen a mezőt.
Knox-licenc társítása a profilhoz | Nem | Hagyja üresen a beállítást. A KME-vel történő Intune-regisztrációhoz nincs szükség Knox-licencre.

## <a name="add-devices"></a>Eszközök felvétele

Ha MDM-profilokat szeretne hozzárendelni az eszközökhöz, a támogatott Samsung Knox-eszközöket hozzá kell adnia a Knox portálhoz az alábbi módszerek egyikével:
- **Samsung által jóváhagyott Reseller(s) használatával:** Ezt a módszert akkor használja, ha az egyik a Samsung által jóváhagyott viszonteladók eszközökön megvásárolt. Ha jóváhagyja, a viszonteladók automatikusan feltölthetnek eszközöket. [A viszonteladók hozzáadásáról tájékoztatást a Samsung Knox regisztrációs útmutatójában találhat](https://docs.samsungknox.com/KME-Getting-Started/Content/Register_resellers.htm).

- **A Knox-telepítésre kijelölt alkalmazás (KDA) használatával:** Ezt a módszert használja, ha meglévő eszközöket, amelyek segítségével KME regisztrálni kell. Ezzel a módszerrel Bluetooth vagy NFC használatával adhat hozzá eszközöket a Knox portálhoz. [A KDA használatáról tájékoztatást a Samsung Knox regisztrációs útmutatójában találhat](https://docs.samsungknox.com/KME-Getting-Started/Content/add-device-info.htm).

## <a name="assign-an-mdm-profile-to-devices"></a>MDM-profil hozzárendelése az eszközökhöz
A regisztráció előtt a Knox portálon hozzá kell rendelnie egy MDM-profilt a hozzáadott eszközökhöz. [Az eszközkonfigurációról tájékoztatást a Samsung Knox regisztrációs útmutatójában találhat](https://docs.samsungknox.com/KME-Getting-Started/Content/configure-devices.htm).

## <a name="configure-how-end-users-sign-in"></a>A végfelhasználói bejelentkezés konfigurálása

Az Intune-ba androidos KME-vel beléptetett eszközök esetében a következőképp konfigurálhatja a végfelhasználói bejelentkezést:

- **Nélkül társított felhasználónév:** A Knox portál **eszközadatok**, hagyja a **felhasználói azonosító** és **jelszó** mezőket a hozzáadott eszközök esetén üres. Így a végfelhasználónak az Intune-regisztráció során nevet és jelszót is meg kell adnia.

- **A felhasználónév-hozzárendelés:** A Knox portál **eszközadatok**, adjon meg egy **felhasználói azonosító** (például egy felhasználó nevét a hozzárendelt felhasználó vagy egy [Készülékregisztráció-kezelő](https://docs.microsoft.com/intune/device-enrollment-manager-enroll) fiók) a hozzáadott eszközökhöz. Így a végfelhasználó felhasználó neve előre ki lesz töltve, az Intune-regisztráció során pedig neki egy jelszót kell megadnia.

> [!NOTE]
>
>A felhasználó-hozzárendelés csak Android-eszközök beléptetésére vonatkozik. Ha meghatároz egy felhasználó-hozzárendelést, csak a hozzárendelt felhasználó regisztrálhatja az eszközt a KME-vel. Ez az eszköz gyári alaphelyzetbe állítása után is így marad. Ha nem határoz meg felhasználó-hozzárendelést a Knox portálon, bármely, érvényes Intune-licenccel rendelkező felhasználó regisztrálhatja az eszközt a KME-vel.
>

## <a name="distribute-devices"></a>Eszközök terjesztése

Az MDM-profil létrehozása és hozzárendelése, a felhasználónév társítása és az eszközök vállalati tulajdonúként való azonosítása után megkezdheti az eszközök terjesztését a felhasználók között.

További segítségre van szüksége? Tekintse meg a teljes [Knox mobileszköz-regisztrációs felhasználói útmutatót](https://docs.samsungknox.com/KME-Getting-Started/Content/get-started.htm).

## <a name="frequently-asked-questions"></a>Gyakori kérdések

- **Eszköz tulajdonosa támogatása:** Az Intune támogatja az eszközök regisztrálását csak Android enterprise használatával teljes képernyős módra. Egyéb Android Enterprise eszköztulajdonosi módok támogatására is sor kerül, amint elérhetővé válnak az Intune-ban.

- **Nincsenek munkahelyi profilt támogató:** KME a vállalati tulajdonú eszközök regisztrációs módszer és az Androidos munkahelyi profillal regisztrált eszközök biztosítása a munkahelyi és személyes adatok elkülönülnek a személyes eszközökhöz. Tehát eszközök regisztrálása a munkahelyi profilba KME használatával nem támogatjuk az Intune-ban.

- **A gyári beállítások visszaállítására Android Enterprise regisztrálása:** Ha átkonfigurálása eszközöket, amelyek már be van állítva, eszközök kell lennie a gyári beállításokat Android Enterprise regisztrálása során.

- **A frissítések a Google Play-fiók használatával:** Google Play-fiók már nem szükséges regisztrálni az eszközt a Microsoft Intune-bA. Az Intune Céges portál alkalmazás jövőbeli frissítései azonban ezt kötelezővé tehetik. A Google Eszköztulajdonos-regisztrációhoz nem szükséges Google Play-fiók.

- **"Password" mezőt a rendszer figyelmen kívül hagyja:** Ha a **jelszó** mező fel van töltve **eszközadatok** a Knox-portálon, figyelmen kívül hagyja az Intune vállalati portál alkalmazás Android-regisztráció során. A végfelhasználónak meg kell adnia egy jelszót az eszközön az eszközregisztráció befejezéséhez.


## <a name="getting-support"></a>Támogatás igénybevétele
További információ [a Samsung KME támogatásáról](https://docs.samsungknox.com/KME-Getting-Started/Content/to-get-kme-support.htm).



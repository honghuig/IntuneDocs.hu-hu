---
title: A Microsoft Intune App SDK for Android fejlesztői tesztelési útmutató
description: A Microsoft Intune App SDK Androidban tesztelési útmutató segítséget nyújt az Intune-nal felügyelt Android-alkalmazás teszteléséhez.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa6b07c77b0d92ceb7bdc960d8c2fd754c277499
ms.sourcegitcommit: 63b55e81122e5c15893302b109ae137c30855b55
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67713234"
---
# <a name="microsoft-intune-app-sdk-for-android-developers-testing-guide"></a>A Microsoft Intune App SDK tesztelési útmutató Androidos fejlesztőknek

Célja, hogy a Microsoft Intune App SDK Androidban tesztelési útmutató segítséget nyújt az Intune-nal felügyelt Android-alkalmazás teszteléséhez.  

## <a name="prerequisite-test-accounts"></a>Előfeltétel-ellenőrzési tesztelés fiókok
Új fiókokat is létrehozható, és anélkül előre létrehozott adatokat. Új fiók létrehozása:
1. Keresse meg a [Microsoft Demos](https://demos.microsoft.com/environments/create/tenant) hely. 
2. [Az Intune beállítása](https://docs.microsoft.com/intune/setup-steps) mobileszköz-felügyelet (MDM) engedélyezése.
3. [Felhasználók létrehozása](https://docs.microsoft.com/intune/users-add).
4. [Csoportok létrehozása a](https://docs.microsoft.com/intune/groups-add).
5. [Licencek hozzárendelése](https://docs.microsoft.com/intune/licenses-assign) szükség szerint a teszteléshez.


## <a name="azure-portal-policy-configuration"></a>Az Azure portal-házirend konfigurálása
[Alkalmazás alkalmazásvédelmi szabályzatok létrehozása és hozzárendelése](https://docs.microsoft.com/intune/app-protection-policies) a a [az Azure portal Intune panelén](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview). A [alkalmazáskonfigurációs szabályzat](https://docs.microsoft.com/intune/app-configuration-policies-overview) is létrehozva és hozzárendelve az Intune panelen.

> [!NOTE]
> Ha az alkalmazás nem szerepel az Azure Portalon, is cél szabályzat kiválasztásával a **további alkalmazások** lehetőséget és a kezeléséről a csomag nevét a szövegmezőbe.

> [!IMPORTANT]
> Alkalmazás-konfigurációs házirend alkalmazásához, a felhasználó regisztrálásának kell vonatkozni egy [az Intune alkalmazásvédelmi szabályzatának](https://docs.microsoft.com/intune/app-protection-policy).

## <a name="test-cases"></a>Vizsgálati eset

A következő esetek adja meg a konfigurációs és a megerősítő lépéseket. Ez az útmutató segítségével az Intune által felügyelt Android alkalmazásokkal kapcsolatos problémák elhárításához.

### <a name="required-pin-and-corporate-credentials"></a>Szükséges PIN-kód és a vállalati hitelesítő adatok

Vállalati erőforrások eléréséhez PIN-kód is szükséges. Is vállalati hitelesítés kényszerítése, mielőtt a felhasználók a felügyelt alkalmazások használhatják. Az alábbi lépések segítségével állítsa be ezeket a követelményeket:

1. Konfigurálása **PIN-kód megkövetelése a hozzáféréshez** és **vállalati hitelesítő adatok megkövetelése a hozzáféréshez** való **Igen**. További információkért lásd: [Androidos alkalmazásvédelmi szabályzat beállításai a Microsoft Intune-ban](app-protection-policy-settings-android.md#access-requirements).
2. Erősítse meg a következő feltételeknek:
    - Alkalmazásindítás kell mutatnia a PIN-kód beviteli/telepítés és/vagy a termelési felhasználó a céges portállal a regisztráció során használt kérdés.
    - Hiba egy érvényes bejelentkezési kérések jelenhetnek nyújtjuk egy helytelenül konfigurált android-jegyzékfájlban, kifejezetten az ADAL-integrációs (SkipBroker ClientID és hatóság) értékeit oka lehet.
    - Nyújtjuk bármilyen kérdés hibája okozhatja egy helytelenül integrált `MAMActivity` értéket. További információ `MAMActivity`, lásd: [Microsoft Intune App SDK Androidon – útmutató fejlesztőknek](app-sdk-android.md).

> [!NOTE] 
> Ha a fenti teszt nem működik, a tesztek az alábbi valószínűleg nem is. Felülvizsgálat [SDK](app-sdk-android.md##sdk-integration) és [ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal) integrációja.

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>Átvitele és fogadása, adatok más alkalmazásokkal korlátozása
Felügyelt vállalati alkalmazások közötti adatátvitel módon lehet szabályozni:

1. Állítsa be **///az alkalmazás átadhat adatokat más alkalmazásoknak** való **szabályzattal felügyelt alkalmazások**.
2. Állítsa be **alkalmazás fogadhat adatokat más alkalmazásokból** való **minden alkalmazás**. Ezek a szabályzatok által érintett leképezések és tartalomszolgáltatók használatát.
3. Erősítse meg a következő feltételeknek:
    - Nyissa meg egy nem felügyelt alkalmazásból való az alkalmazás működését megfelelően.
    - Tartalom megosztása a felügyelt alkalmazások között engedélyezett.
    - Nem felügyelt alkalmazásokba (például a Chrome böngészőben) a felügyelt alkalmazásokból való megosztása le van tiltva.

### <a name="restrict-cut-copy-and-paste"></a>Kivágás, másolás és beillesztés korlátozása
A rendszer vágólapjára az alábbiak szerint korlátozhatja a felügyelt alkalmazások:

1. Állítsa be **Kivágás, másolás és beillesztés korlátozása más alkalmazásokkal** való **szabályzat által felügyelt beillesztéssel**.
2. Erősítse meg a következő feltételeknek:
    - Az alkalmazás be egy felügyelt szöveget másol a nem felügyelt alkalmazások (például üzenetek) le van tiltva.

### <a name="prevent-save-as"></a>Megakadályozása **Mentés másként**
Szabályozhatja, **Mentés másként** funkciók az alábbiak szerint:

1. Ha az alkalmazásának [integrált "Mentés másként" vezérlők](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted)állítsa be **"Mentés másként" tiltása** való **Igen**.
2. Erősítse meg a következő feltételeknek:
    - Mentse a csak a megfelelő felügyelt helyekre korlátozódik.

### <a name="file-encryption"></a>Fájlok titkosítása
Az eszközön tárolt adatok módon titkosíthatók:

1. Állítsa be **titkosítja az alkalmazásadatokat** való **Igen**.
2. Erősítse meg a következő feltételeknek:
    - Ez nem érinti a normál alkalmazási viselkedését.

### <a name="prevent-android-backups"></a>Android-biztonsági mentések tiltása
Alkalmazás biztonsági másolatának módon lehet szabályozni:

1. Ha meg van [integrált biztonsági korlátozások](app-sdk-android.md#protecting-backup-data), konfigurálja **megakadályozása Android-biztonsági mentések** való **Igen**.
2. Erősítse meg a következő feltételeknek:
    - Biztonsági másolatok korlátozva.

### <a name="unenrollment"></a>Regisztráció törlésének
Távolról törölhetik a vállalati e-mailek és dokumentumok tartalmazó felügyelt alkalmazásokat, és a személyes adatok visszafejtése, amikor már nem felügyelt módon:

1. Az Azure Portalról [adja ki a Törlés](https://docs.microsoft.com/intune/apps-selective-wipe).
2. Ha az alkalmazás nem regisztrálható minden törlési kezelők erősítse meg a következő feltételeknek:
    - Az alkalmazás teljes törlést akkor fordul elő.
3. Ha az alkalmazás regisztrálva van `WIPE_USER_DATA` vagy `WIPE_USER_AUXILARY_DATA`, erősítse meg a következő feltételeknek:
    - A felügyelt tartalomra el lesznek távolítva az alkalmazásból. További információkért lásd: [Intune App SDK for Android fejlesztői útmutató – szelektív Törlés](app-sdk-android.md#selective-wipe).

### <a name="multi-identity"></a>Többszörös identitás
Integrálás [többszörös identitást támogató](app-sdk-android.md#multi-identity-optional) magas kockázatú módosítják, hogy alaposan tesztelni kell. A leggyakoribb problémák miatt nem megfelelő beállítást az identitás (környezet és a fenyegetettségi szint) és a is nyomon követi, fájlok lesznek (`MAMFileProtectionManager`).

A többszörös identitást a következő esetekben minimálisan kell ellenőrizhető:

- **Mentés másként** házirend a felügyelt identitásokból megfelelően működik.
- Másolás és beillesztés korlátozások érvényben vannak megfelelően a személyes felügyelt.
- Csak a felügyelt identitáshoz tartozó adatokat titkosítjuk, és a személyes fájlokat nem módosulnak.
- Regisztráció törlésének során szelektív törlés csak eltávolítja a felügyelt identitás adatait.
- A rendszer felszólítja a végfelhasználót a feltételes indítási felügyeltről felügyelt fiók (csak az első alkalommal) való módosításakor.

### <a name="app-configuration-optional"></a>Alkalmazások konfigurálása (nem kötelező)
Felügyelt alkalmazások viselkedése, így a következő konfigurálhatja:

1. Ha az alkalmazás minden olyan alkalmazás-konfigurációs beállítást használ fel, tesztelje, hogy az alkalmazás megfelelően kezeli az összes értéket, amely (rendszergazdaként) lehet. [Alkalmazáskonfigurációs szabályzatok](https://docs.microsoft.com/intune/app-configuration-policies-overview) hozhat létre és hozzárendelve az Intune-nal.

## <a name="next-steps"></a>További lépések

- [Android – üzletági alkalmazás hozzáadása a Microsoft Intune](lob-apps-android.md).

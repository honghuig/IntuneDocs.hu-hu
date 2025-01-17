---
title: IOS-eszközök regisztrálásával kapcsolatos problémák elhárítása Microsoft Intune
titleSuffix: Microsoft Intune
description: Javaslatok az iOS-eszközök Intune-beli regisztrálásával kapcsolatos leggyakoribb problémák elhárításához.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/25/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c826d27079e365670ba47aa22d1dd8e5d42f4b21
ms.sourcegitcommit: 1d4aec7b79c70d35ec3fc29df6ff9c6a1403412e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68496374"
---
# <a name="troubleshoot-ios-device-enrollment-problems-in-microsoft-intune"></a>IOS-eszközök regisztrálásával kapcsolatos problémák elhárítása Microsoft Intune

Ez a cikk segít az Intune-rendszergazdáknak az iOS-eszközök Intune-beli regisztrálásakor felmerülő problémák megértésében és hibaelhárításában.

## <a name="prerequisites"></a>Előfeltételek
Mielőtt elkezdené a hibaelhárítást, fontos, hogy gyűjtsön néhány alapvető információt. Ezek az információk segítenek jobban megérteni a problémát, és csökkenthetik a megoldási időt.

Gyűjtse össze a következő információkat a problémával kapcsolatban:
- Pontosan milyen hibaüzenet jelenik meg?
- Hol látja a hibaüzenetet?
- Mikor indult el a probléma? Valaha is működött a regisztráció? 
- Milyen platformon (Android, iOS, Windows) van probléma?
- Hány felhasználót érint a rendszer? Az összes érintett felhasználó vagy csak néhány?
- Hány eszközt érint a rendszer? Minden eszköz érintett vagy csak néhány?
- Mi a MDM-szolgáltató? Ha System Center Configuration Manager, a Configuration Manager milyen verzióját használja?
- Hogyan történik a beléptetés? A "saját eszközök használata" (BYOD) vagy Apple Készülékregisztrációs program (DEP) beléptetési profilokkal?

## <a name="error-messages"></a>Hibaüzenetek

### <a name="profile-installation-failed-a-network-error-has-occurred"></a>A profil telepítése nem sikerült. Hálózati hiba történt.

**Okozhat** Meghatározatlan probléma van az iOS-sel az eszközön.

#### <a name="resolution"></a>Megoldás:
1. Ha meg szeretné akadályozni az adatvesztést az alábbi lépésekben (az iOS visszaállítása törli az eszközön lévő összes adatmentést), ügyeljen arra, hogy készítsen biztonsági másolatot az adatairól.
2. Helyezze az eszközt helyreállítási módba, majd állítsa vissza. Győződjön meg arról, hogy új eszközként állítja be. További információ az iOS-eszközök visszaállításáról: [https://support.apple.com/HT201263](https://support.apple.com/HT201263).
3. Regisztrálja újra az eszközt.

### <a name="profile-installation-failed-connection-to-the-server-could-not-be-established"></a>A profil telepítése nem sikerült. Nem lehet csatlakozni a kiszolgálóhoz.

**Okozhat** Az Intune-bérlő úgy van konfigurálva, hogy csak a vállalat tulajdonában lévő eszközöket engedélyezze. 

#### <a name="resolution"></a>Megoldás:
1. Jelentkezzen be az Azure portálra.
2. Válassza a **További szolgáltatások**lehetőséget, keresse meg az Intune-t, majd válassza az **Intune**lehetőséget.
3. Válassza az **Eszközök regisztrálása** > **Regisztrációs korlátozások** lehetőséget.
4. Az **eszközök típusának korlátozása**területen válassza ki a > **Tulajdonságok** > beállításához használni kívánt korlátozást **> válassza** az **iOS** **lehetőséget** , majd kattintson **az OK**gombra.
5. Válassza a **platformok konfigurálása**lehetőséget, válassza a személyes tulajdonú iOS-eszközök **engedélyezése** lehetőséget, majd kattintson **az OK**gombra.
6. Regisztrálja újra az eszközt.

### <a name="this-service-is-not-supported-no-enrollment-policy"></a>Ez a szolgáltatás nem támogatott. Nincs beléptetési szabályzat.

**OK**: Az Apple MDM push-tanúsítvány nincs konfigurálva az Intune-ban, vagy a tanúsítvány érvénytelen. 

#### <a name="resolution"></a>Megoldás:

- Ha nincs konfigurálva az MDM push-tanúsítvány, kövesse az [Apple Mdm push-tanúsítvány](apple-mdm-push-certificate-get.md#steps-to-get-your-certificate)beszerzése című témakör lépéseit.
- Ha az MDM push-tanúsítvány érvénytelen, kövesse az [Apple Mdm push-tanúsítvány](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate)megújítása című témakör lépéseit.

### <a name="company-portal-temporarily-unavailable-the-company-portal-app-encountered-a-problem-if-the-problem-persists-contact-your-system-administrator"></a>Céges portál átmenetileg nem érhető el. A Céges portál alkalmazás hibát észlelt. Ha a probléma továbbra is fennáll, forduljon a rendszergazdához.

**Okozhat** A Céges portál alkalmazás elavult vagy sérült.

#### <a name="resolution"></a>Megoldás:
1. Távolítsa el a Céges portál alkalmazást az eszközről.
2. Töltse le és telepítse a **Microsoft Intune céges portál** alkalmazást az **App Store áruházból**.
3. Regisztrálja újra az eszközt.

### <a name="device-cap-reached"></a>Elérte az eszközök maximális száma

**Okozhat** A felhasználó több eszközt próbál regisztrálni az eszköz beléptetési korlátján kívül.

#### <a name="resolution"></a>Megoldás:
1. Nyissa meg az [Intune felügyeleti portál](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview) > **eszközök** > **minden eszköz**elemét, és győződjön meg arról, hogy a felhasználó hány eszközt regisztrált.
    > [!NOTE]
    > Az érintett felhasználói bejelentkezést is meg kell adnia az [Intune felhasználói portálon](https://portal.manage.microsoft.com/) , és ellenőriznie kell a regisztrált eszközöket. Előfordulhat, hogy az Intune-beli [felhasználói portálon](https://portal.manage.microsoft.com/) megjelenő eszközök nem az [Intune felügyeleti portálon](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview)jelennek meg, az ilyen eszközök pedig az eszközök regisztrálási korlátját is megszámolják.
2. Lépjen a  > **felügyelet mobileszköz-kezelés** > beléptetési**szabályok** > az eszközök regisztrálási korlátjának vizsgálatához. Alapértelmezés szerint a korlát értéke 15. 
3. Ha a regisztrált eszközök száma elérte a korlátot, távolítsa el a szükségtelen eszközöket, vagy növelje az eszköz beléptetési korlátját. Mivel minden regisztrált eszköz Intune-licencet használ, javasoljuk, hogy először mindig távolítsa el a szükségtelen eszközöket.
4. Regisztrálja újra az eszközt.

### <a name="workplace-join-failed"></a>Workplace Join sikertelen

**Okozhat** A Céges portál alkalmazás elavult vagy sérült.  

#### <a name="resolution"></a>Megoldás:
1. Távolítsa el a Céges portál alkalmazást az eszközről.
2. Töltse le és telepítse a **Microsoft Intune céges portál** alkalmazást az **App Store áruházból**.
3. Regisztrálja újra az eszközt.

### <a name="user-license-type-invalid"></a>A felhasználói licenc típusa érvénytelen

**Okozhat** Az eszközt regisztrálni próbáló felhasználónak nincs érvényes Intune-licence.

#### <a name="resolution"></a>Megoldás:
1. Nyissa meg a [Microsoft 365 felügyeleti](https://portal.office.com/adminportal/home#/homepage)központot, majd válassza a **felhasználók** > **aktív felhasználók**lehetőséget.
2. Válassza ki az érintett felhasználói fiókot > a **termék licencek** > **szerkesztése**elemet.
3. Ellenőrizze, hogy érvényes Intune-licenc van-e hozzárendelve ehhez a felhasználóhoz.
4. Regisztrálja újra az eszközt.

### <a name="user-name-not-recognized-this-user-account-is-not-authorized-to-use-microsoft-intune-contact-your-system-administrator-if-you-think-you-have-received-this-message-in-error"></a>A Felhasználónév nem ismerhető fel. Ez a felhasználói fiók nem rendelkezik jogosultsággal a Microsoft Intune használatára. Ha úgy gondolja, hogy hiba történt, forduljon a rendszergazdához.

**Okozhat** Az eszközt regisztrálni próbáló felhasználónak nincs érvényes Intune-licence.

1. Nyissa meg a [Microsoft 365 felügyeleti](https://portal.office.com/adminportal/home#/homepage)központot, majd válassza a **felhasználók** > **aktív felhasználók**lehetőséget.
2. Válassza ki az érintett felhasználói fiókot, majd válassza a **termék licencek** > **szerkesztése**lehetőséget.
3. Ellenőrizze, hogy érvényes Intune-licenc van-e hozzárendelve ehhez a felhasználóhoz.
4. Regisztrálja újra az eszközt.

### <a name="profile-installation-failed-the-new-mdm-payload-does-not-match-the-old-payload"></a>A profil telepítése nem sikerült. Az új MDM-tartalom nem felel meg a régi adattartalomnak.

**Okozhat** Már telepítve van egy felügyeleti profil az eszközön.

#### <a name="resolution"></a>Megoldás:

1. Nyissa meg az IOS-eszköz **beállításait** > **általános** > **eszközkezelés**.
2. Koppintson a meglévő felügyeleti profilra, és koppintson a **felügyelet eltávolítása**elemre.
3. Regisztrálja újra az eszközt.

### <a name="noenrollmentpolicy"></a>NoEnrollmentPolicy

**Okozhat** A Apple Push Notification Service-(APNs-) tanúsítvány hiányzik, érvénytelen vagy lejárt.

#### <a name="resolution"></a>Megoldás:
Ellenőrizze, hogy hozzá van-e adva érvényes APNs-tanúsítvány az Intune-hoz. További információ: az [iOS-és Mac-eszközök kezelésének beállítása](https://docs.microsoft.com/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune). 

### <a name="accountnotonboarded"></a>AccountNotOnboarded

**Okozhat** Probléma merült fel az Intune-ban konfigurált Apple push Notification szolgáltatás (APNs) tanúsítványával.

#### <a name="resolution"></a>Megoldás:
Újítsa meg az APNs-tanúsítványt, majd regisztrálja újra az eszközt.

> [!IMPORTANT]
> Győződjön meg arról, hogy megújítja a APNs-tanúsítványt. Ne cserélje le az APNs-tanúsítványt. Ha lecseréli a tanúsítványt, az összes iOS-eszközt újra regisztrálnia kell az Intune-ban. 

- Az APNs-tanúsítvány megújítása az Intune önálló verziójában: [Apple Mdm push-tanúsítvány](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate)megújítása.
- A APNs-tanúsítvány megújításához az Intune Hybrid with Configuration Manager használatával: az [iOS-es hibrid eszközkezelés beállítása System Center Configuration Manager és Microsoft Intune](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-ios-mac).
- A APNs-tanúsítvány megújításához az Office 365-ben lásd: [APNs-tanúsítvány létrehozása iOS](https://support.office.com/article/Create-an-APNs-Certificate-for-iOS-devices-522b43f4-a2ff-46f6-962a-dd4f47e546a7)-eszközökhöz.

### <a name="xpctypeerror-connection-invalid"></a>A XPC_TYPE_ERROR-kapcsolatok érvénytelenek

Ha bekapcsol egy, a beléptetési profilhoz hozzárendelt DEP által felügyelt eszközt, a regisztráció meghiúsul, és a következő hibaüzenet jelenik meg:

```
asciidoc
mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" } }
iPhone mobileassetd[83] <Notice>: Client connection invalid (Connection invalid); terminating connection
iPhone com.apple.accessibility.AccessibilityUIServer(MobileAsset)[288] <Notice>: [MobileAssetError:29] Unable to copy asset information from https://mesu.apple.com/assets/ for asset type com.apple.MobileAsset.VoiceServices.CombinedVocalizerVoices
iPhone mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" }
```

**Okozhat** Kapcsolati probléma van az eszköz és az Apple DEP szolgáltatás között.

#### <a name="resolution"></a>Megoldás:
Javítsa ki a kapcsolódási problémát, vagy használjon másik hálózati kapcsolódást az eszköz regisztrálásához. Előfordulhat, hogy kapcsolatba kell lépnie az Apple-vel, ha a probléma továbbra is fennáll.


## <a name="other-issues"></a>Egyéb problémák

### <a name="dep-enrollment-doesnt-start"></a>A DEP-regisztráció nem indul el
Ha bekapcsol egy, a beléptetési profilhoz hozzárendelt DEP által felügyelt eszközt, az Intune regisztrációs folyamata nem indul el.

**Okozhat** A beléptetési profilt a rendszer a DEP-jogkivonat Intune-ba való feltöltése előtt hozza létre.

#### <a name="resolution"></a>Megoldás:

1. Szerkessze a beléptetési profilt. Bármilyen módosítást végezhet a profilban. A cél a profil módosítási idejének frissítése.
2. DEP által felügyelt eszközök szinkronizálása: Nyissa meg az Intune  > -portált >**felügyelet mobileszköz-kezelés** > **iOS** > -**Készülékregisztrációs program** > **szinkronizálás most**. A szolgáltatás elküld egy szinkronizálási kérelmet az Apple-nek.

### <a name="dep-enrollment-stuck-at-user-login"></a>DEP-regisztráció megakadt a felhasználói bejelentkezéskor
Amikor bekapcsol egy beléptetési profilhoz rendelt DEP által felügyelt eszközt, a kezdeti beállítás a hitelesítő adatok megadása után fog megjelenni.

**Okozhat** A többtényezős hitelesítés (MFA) engedélyezve van. Az MFA jelenleg nem működik a DEP-eszközökön való regisztráció során.

#### <a name="resolution"></a>Megoldás:
Tiltsa le az MFA-t, majd regisztrálja újra az eszközt.

## <a name="next-steps"></a>További lépések

- [Eszközök regisztrálásával kapcsolatos problémák elhárítása az Intune-ban](troubleshoot-device-enrollment-in-intune.md)
- [Kérdés feltevése az Intune-fórumon](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [A Microsoft Intune támogatási csapatának blogja](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [A Microsoft nagyvállalati mobilitási és biztonsági blogjának beolvasása](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)

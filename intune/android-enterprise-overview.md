---
title: Kezelheti a vállalati Android munkahelyi profilos eszközök Microsoft Intune-ban
titleSuffix: ''
description: A Microsoft Intune vállalati Android munkahelyi profilos eszközök további felügyeleti lehetőségeket és adatvédelmet biztosít, amikor a munkahelyi használnak a személyes Android-eszközök kezelése.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2cc3c960-1fdd-47ca-a693-420d47b403de
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1649c6256e4df61b538e2adee87512617b677bb4
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/03/2019
ms.locfileid: "67547493"
---
# <a name="manage-android-work-profile-devices-with-intune"></a>Androidos munkahelyi profilos eszközök kezelése az Intune-nal

Android Enterprise tanúsítványigénylési beállításokat, amelyek biztosítható a felhasználók a legtöbb naprakészen tartását és védelmét a funkciók készletét kínálja. Android Enterprise munkahelyi profillal rendelkező regisztrálása lehetővé teszi a funkciók és szolgáltatások, amelyek elkülönítik a személyes alkalmazásait és adatait a munkahelyi alkalmazásokhoz és adatokhoz. Is biztosít a további felügyeleti lehetőségeket és adatvédelmet amikor a munkahelyi használnak a személyes Android-eszközökön. 

## <a name="supported-devices"></a>Támogatott eszközök

Android Enterprise-felügyeleti képességek szolgáltatásain újabb Android operációs rendszerek részét képezik. Olyan eszközökhöz, amelyek nem támogatják az Android Enterprise a hagyományos androidos eszközök kezelésének elérhető marad. További információkért lásd: [Android Enterprise követelmények](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="onboarding"></a>Bevezetés

Android Enterprise regisztrálása előtt munkahelyi profilos eszközök, kell végeznie néhány bevezető lépést. Ezeket a lépéseket az Intune-bérlő és a felügyelt Google Play közötti kapcsolatot létesíteni. További információkért lásd: [vállalati Android munkahelyi profilos eszközök regisztrációjának engedélyezése](android-work-profile-enroll.md).

## <a name="work-profile-management"></a>Munkahelyi profilok kezelése

Ha Ön kezeli az Android Enterprise munkahelyi profil eszköz az Intune-nal, nem kell felügyelnie az egész eszközt. A felügyeleti funkciók csak az eszközön a regisztráció során létrehozott munkahelyi profilra vonatkoznak. Minden olyan alkalmazás, amelyet az Intune-nal helyez üzembe az eszközön, a munkahelyi profilba települ. A munkahelyi profilban megjelenő alkalmazásikonok elkülönülnek az eszközön található személyes alkalmazásoktól. A vállalati Android hatókörén kívül eső összes Android-alkalmazás és adat személyes marad az eszközön, és a végfelhasználó felügyelete alá tartozik. Az eszköz személyes részén a felhasználók bármilyen alkalmazást telepíthetnek. A rendszergazdák a munkahelyi profil hatókörébe tartozó alkalmazásokat és műveleteket felügyelhetik és figyelhetik.

Az Intune az androidos munkahelyi profilos eszközökön konfigurálható, beépített általános beállítások széles választékát kínálja. További információt az [Androidos munkahelyi profilos eszközökre vonatkozó szabályzatbeállítások](compliance-policy-create-android-for-work.md) című témakörben talál.

## <a name="app-publishing-and-distribution"></a>Alkalmazások közzététele és terjesztése

A felügyelt Google Play Android Enterprise alkalmazásterjesztési és felügyeleti szerves részét képezi. Telepített vállalati Android munkahelyi profilos eszközök a munkahelyi profilban szereplő alkalmazások a felügyelt Google Play szolgáltatásból származnak. A Play áruházban található alkalmazások felügyeletéhez és üzembe helyezéséhez a Google-felügyeletre kijelölt céges rendszergazdai hitelesítő adatokkal kell bejelentkezni a Google Play webhelyére. Jóváhagyhatja alkalmazásokat Android Enterprise telepítésre az eszközök munkahelyi profiljában jelennek meg. Ezek az alkalmazások az Intune-konzolra szinkronizálódnak, ahol ezután telepíthetők és felügyelhetők az Intune-nal. A cége által fejlesztett üzletági (LOB) alkalmazásokat közzé kell tenni a Felügyelt Google Play szolgáltatásban a Google androidos alkalmazás-közzétételi konzoljával. Az üzletági alkalmazásokat az androidos alkalmazás-közzétételi konzolon kell konfigurálni a szervezethez való hozzáférés korlátozásához.

Az alkalmazások felhasználói beavatkozás nélkül telepíthetők, és az sem szükséges, hogy a felhasználó engedélyezze az **ismeretlen forrásból történő telepítést**. A választható vagy elérhető alkalmazások tallózásához és telepítéséhez a felhasználók a Play for Work áruházat használhatják az eszközükön. További információkért lásd: [alkalmazások hozzárendelése Android Enterprise munkahelyi profilos eszközök az Intune-nal](apps-add-android-for-work.md).

## <a name="app-configuration"></a>Alkalmazáskonfiguráció

Android Enterprise infrastruktúrát biztosít, amelyek támogatják ezt az alkalmazáskonfigurációs értékeinek megadására. A munkahelyi alkalmazások konfigurációs értékeinek megadásával biztosíthatja, hogy az alkalmazások megfelelően legyenek beállítva, amikor a felhasználók először indítják el őket. Az alkalmazáskonfiguráció támogatásához az alkalmazásfejlesztőknek úgy kell létrehozniuk az Android-alkalmazásaikat, hogy azok támogassák a felügyelt konfigurációs értékek használatát. Ilyen esetben az Intune-nal adhatja meg és alkalmazhatja ezeket a konfigurációs beállításokat. További információt az [Alkalmazáskonfigurációs szabályzatok hozzáadása kezelt Android-eszközökhöz](app-configuration-policies-use-android.md) című témakörben talál.

## <a name="email-configuration"></a>E-mail-konfiguráció

Android Enterprise nem biztosít egy alapértelmezett levelezőalkalmazást vagy natív e-mail-profil objektumot, például az iOS által biztosított. Ehelyett e-mail-konfigurációk adhatók meg az alkalmazáskonfigurációs beállítások használatával az olyan levelezőalkalmazásokhoz, amelyek támogatják ezt. A Gmail és egyet a Nine Work a két Exchange ActiveSync (EAS) ügyfél alkalmazások a Play Store, amely támogatja az Android Enterprise-alkalmazások konfigurálása.

Az Intune konfigurációsablonokat biztosít a Gmail és a Nine Work alkalmazáshoz, ha azok munkahelyi alkalmazásként vannak felügyelve. Az alkalmazáskonfigurációs profilokat támogató más levelezőalkalmazások mobilalkalmazás-konfigurációs szabályzatokkal konfigurálhatók.

Ha az Android Enterprise munkahelyi profil eszköz Exchange ActiveSync feltételes hozzáférést használ, fontolja meg a Gmail vagy a Nine Work levelezőalkalmazást. Szintén támogatott az Android rendszerhez készült Microsoft Outlook alkalmazás, illetve bármely olyan levelezőalkalmazás, amely modern ADAL-hitelesítést használ. További információt [Az e-mail-beállítások konfigurálása a Microsoft Intune-ban](email-settings-configure.md) című témakörben talál.

## <a name="app-protection-policies"></a>Alkalmazásvédelmi szabályzatok

Az érvényben lévő alkalmazásvédelmi szabályzatokat a munkahelyi és a személyes profil egyaránt teljes mértékben támogatja. Az üzletági alkalmazásokat a https://play.google.com/apps/publish címen elérhető androidos alkalmazás-közzétételi konzolon teheti közzé. Ez a konzol tartalmaz egy beállítást, amellyel az alkalmazások privátként jelölhetők meg a szervezet számára. További információkért lásd: [a vállalati Android munkahelyi profilos eszközök megfelelőségi szabályzatainak hozzáadása az Intune-ban](compliance-policy-create-android-for-work.md). Az alkalmazásvédelmi szabályzatok létrehozásáról általános információ: [Mik azok az alkalmazásvédelmi szabályzatok?](app-protection-policy.md)

## <a name="vpn-profiles"></a>VPN-profilok

A VPN-támogatás az Android VPN-profilokhoz hasonlít. Az ugyanazon VPN-szolgáltatók és alapbeállítások érhetők el az Android Enterprise management két eltéréssel:

- **Munkahelyi profil hatókörű VPN** – A VPN-kapcsolatok a munkahelyi profilban üzembe helyezett alkalmazásokra vannak korlátozva. Csak az Android Enterprise által felügyelt alkalmazások használhatja a VPN-kapcsolatot. Az eszközön lévő saját alkalmazások nem használhatnak felügyelt VPN-kapcsolatot. További információkért lásd: [Android Enterprise VPN-beállítások](vpn-settings-android.md#android-enterprise-vpn-settings).

- **Alkalmazásspecifikus VPN** – Az alkalmazásspecifikus VPN akkor konfigurálható az Intune-ban, ha a VPN-szolgáltató támogatja:
    - alkalmazásspecifikus VPN konfigurációja
    - a funkció konfigurálásához az alkalmazásonkénti VPN az Android Enterprise alkalmazáskonfigurációs profilján keresztül.
    További információt az [Alkalmazásonkénti VPN-profil létrehozása androidos eszközökhöz egyéni Microsoft Intune-profillal](android-pulse-secure-per-app-vpn.md) című témakörben talál.

## <a name="certificate-profiles"></a>Tanúsítványprofilok

Az azonos tanúsítvány profil konfigurációs beállításai Android-kezelés számára elérhető a vállalati Android munkahelyi profilos eszközök érhetők el. Android Enterprise kibővített tanúsítványkezelési API-kat biztosít. A kibővített tanúsítványkezelés a következő funkciókat tartalmazza:

- Biztosítja, hogy a tanúsítványok telepítése csendes módban és a felhasználó számára zökkenőmentesen történjen.
- Biztosítja a telepített tanúsítványok eltávolítását, amikor az eszközöket kivonják az Intune-ból, és törlik a munkahelyi profilt.
- Továbbfejlesztett üzenetküldést biztosít, amely tájékoztatja a felhasználókat arról, hogy az informatikai részleg telepítette és konfigurálta a tanúsítványt a felügyeleti szolgáltatáson keresztül.

További információt az [Eszközök tanúsítványprofiljainak konfigurálása a Microsoft Intune-ban](certificates-configure.md) című témakörben talál.

## <a name="wi-fi-profiles"></a>Wi-Fi profilok

Android Enterprise által felügyelt Wi-Fi profilok el lesznek távolítva, amikor az eszközt kivonják az Intune-ból, és törlik a munkahelyi profilt. További információt [A Wi-Fi-beállítások konfigurálása a Microsoft Intune-ban](wi-fi-settings-configure.md) című témakörben talál.

## <a name="next-steps"></a>További lépések
- [Androidos eszközök regisztrálása](android-enroll.md)
- [Alkalmazások hozzárendelése Android Enterprise munkahelyi profilos eszközök az Intune-nal](apps-add-android-for-work.md)

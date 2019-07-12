---
title: fájl belefoglalása
description: fájl belefoglalása
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: d907c5256469e86410c9916d117d3e322d43cfc3
ms.sourcegitcommit: 2614d1b08b8a78cd792aebd2ca9848f391df8550
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67812473"
---
Ezek a hirdetmények olyan fontos információkat tartalmaznak, amelyek segíthetnek a jövőbeli Intune-változások és-funkciók előkészítésében. 

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Android Céges portál-alkalmazás frissítése a legújabb verzióra <!--4536963-->
Az Intune rendszeres időközönként frissítéseket szabadít fel az Android Céges portál alkalmazásban. November 2018-én közzétettünk egy vállalati portál frissítést, amely tartalmaz egy back-end kapcsolót, amely felkészíti a Google-t a meglévő értesítési platformról a Google Firebase Cloud Messaging (FCM) szolgáltatásba való váltásra. Ha a Google kihasználja a meglévő értesítési platformot, és áthelyezi az FCM-re, a végfelhasználóknak legalább november 2018 kiadásban frissíteniük kell a vállalati portál alkalmazást, hogy továbbra is kommunikáljanak a Google Play áruházral.

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
A telemetria azt jelzi, hogy a 5.0.4269.0-nál korábbi Céges portál verzióval rendelkező eszközök vannak. Ha a vállalati portál alkalmazás ezen vagy későbbi verziója nincs telepítve, az informatikai részleg olyan műveleteket kezdeményezett, mint például a törlés, a jelszó alaphelyzetbe állítása, az elérhető és a szükséges alkalmazások telepítése, és előfordulhat, hogy a tanúsítványigénylés nem a várt módon működik. Ha az eszközök MDM regisztrálva vannak az Intune-ban, akkor a vállalati portál verzióit és a felhasználókat a Client apps – észlelt alkalmazások oldalon tekintheti meg. Ha kijelöli a Céges portál korábbi verzióit, megtekintheti, hogy a végfelhasználók milyen eszközökkel rendelkeznek a vállalati portál frissítésével.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
Kérje meg az Android-eszközök végfelhasználóit, amelyek nem frissültek a vállalati portál Google Play használatával történő frissítéséhez. Értesítse az ügyfélszolgálatot abban az esetben, ha egy felhasználó nem tartotta meg a vállalati portál alkalmazás automatikus frissítését. További információ a Google FCM platformról és a változásról: további információk a hivatkozáson.

#### <a name="additional-information"></a>További információ
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-fullscreen-experience-coming-to-intune---4593669--"></a>Új teljes képernyős élmény az Intune-hoz <!--4593669-->
Folyamatban van a felhasználói felületi tapasztalatok létrehozása és szerkesztése az Intune-ban a Azure Portal. Ez az új felhasználói élmény leegyszerűsíti a meglévő munkafolyamatokat egy olyan varázsló-stílusú formátum használatával, amely egy panelen van tömörítve. Ez a frissítés elvégezhető a "panel terjeszkedésével", vagy olyan létrehozási és szerkesztési folyamatokkal, amelyekkel részletesen lehatolhat a Deep Blade-útvonalak. A munkafolyamatok létrehozása is frissül, hogy tartalmazza a hozzárendeléseket (kivéve az alkalmazás-hozzárendelést).

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
A teljes képernyős élmény a következő néhány hónapban a portal.azure.com és a devicemanagement.microsoft.com szolgáltatásban is elérhető az Intune-ban. A felhasználói felület ezen frissítése nem befolyásolja a meglévő szabályzatok és profilok funkcióit, de egy kissé módosított munkafolyamatot fog látni. Új szabályzatok létrehozásakor például beállíthatja, hogy a folyamat részeként bizonyos hozzárendeléseket a szabályzat létrehozása után is be lehessen állítani. Tekintse meg a blogbejegyzés további információit, amelyekkel az új felhasználói élmény a-konzolon fog kinézni.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
Semmilyen műveletet nem kell elvégeznie, de szükség esetén érdemes lehet az IT Pro-útmutatást is frissíteni. Frissítjük a dokumentációt, mivel ez a folyamat a Azure Portal-beli Intune-ban található különféle pengéket összesíti.

#### <a name="additional-information"></a>További információ 
https://aka.ms/intune_fullscreen

### <a name="plan-for-change-intune-moving-to-support-ios-11-and-higher-in-september----4665342--"></a>Tervezze meg a változást: Az Intune az iOS 11 és újabb verzióinak támogatására való áttérés szeptemberben <!-- 4665342-->
Szeptemberben azt várjuk, hogy az iOS 13 az Apple számára legyen felszabadítva. Az Intune-regisztráció, a Céges portál és a Managed Browser az iOS 11 kiadása után nem sokkal magasabban támogatja az iOS 11-es verzióját.

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
Ha a O365 Mobile apps iOS 11,0-es és újabb verziókban is támogatott, akkor ez nem érinti Önt; valószínűleg már frissítette az operációs rendszert vagy az eszközöket. Ha azonban rendelkezik az alább felsorolt eszközök bármelyikével, vagy dönthet úgy, hogy az alább felsorolt eszközök bármelyikét regisztrálja, akkor tudja, hogy az alábbi eszközök nem támogatják az iOS 10 rendszernél nagyobb operációs rendszert. Ezeket az eszközöket frissíteni kell egy olyan eszközre, amely támogatja az iOS 11 vagy újabb verzióját:

- iPhone 5
- iPhone 5c
- iPad (4. generáció)

A júliustól kezdődően az iOS 10-es MDM regisztrált eszközök, a Céges portál pedig az operációs rendszer vagy az eszköz frissítésére vonatkozó kérést kapnak. Ha alkalmazás-védelmi házirendeket (alkalmazást) használ, beállíthatja az "iOS minimálisan szükséges operációs rendszer (csak figyelmeztetés)" hozzáférési beállítást is.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
Tekintse meg az Intune-jelentéskészítést, hogy megtekintse, milyen eszközökre vagy felhasználókra lehet hatással. Válassza az **eszközök** > **minden eszköz** lehetőséget, és szűrje az operációs rendszer alapján. További oszlopokat is hozzáadhat, amelyekkel azonosítható, hogy a szervezeten belül kik rendelkeznek iOS 10 rendszerű eszközökkel. Kérje meg, hogy a végfelhasználók szeptember előtt frissítsenek eszközeiket egy támogatott operációsrendszer-verzióra.

### <a name="plan-for-change-support-for-version-811-and-higher-of-intune-app-sdk-for-ios----3586942--"></a>Tervezze meg a változást: Az iOS-hez készült Intune app SDK 8.1.1 és újabb verziójának támogatása <!-- 3586942-->
Az Intune 2019-től kezdve az iOS-alkalmazások támogatásához az Intune app SDK 8.1.1 és újabb verzióit fogja támogatni. A 8.1.1-nál kisebb SDK-verziókkal létrehozott alkalmazások már nem támogatottak. Ez a módosítás hatályba lép az Apple iOS 13 kiadásával, amely várhatóan szeptemberben érkezik, és a MC181399-ben jelent meg.

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
Az Intune app SDK-val vagy az alkalmazások csomagolásának integrálásával az adatok titkosításával biztosíthatja a nem jóváhagyott alkalmazásokból és felhasználóktól származó vállalati adatok védelmet. Az iOS-hez készült Intune app SDK a 256 bites titkosítási kulcsokat alapértelmezés szerint a Intune App Protection szabályzatok (alkalmazás) általi titkosítás engedélyezésekor fogja használni. Ennek a változásnak a megkezdése után minden, a 128 bites titkosítási kulcsokat használó SDK-verzióhoz tartozó iOS-alkalmazás a továbbiakban nem fogja tudni megosztani az SDK-8.1.1 integrált és a 256 bites kulcsokat használó alkalmazásokkal rendelkező 8.1.1. A védett adatmegosztás engedélyezéséhez minden iOS-alkalmazáshoz 8.1.1 vagy újabb SDK-verzió szükséges.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
Keresse meg a Microsoft, harmadik féltől származó és üzletági (LOB) alkalmazásokat. Győződjön meg arról, hogy az Intune-ALKALMAZÁSsal védett összes alkalmazás az SDK 8.1.1 vagy újabb verzióját használja.

- LOB-alkalmazások esetén: Előfordulhat, hogy újra kell közzétennie az SDK-8.1.1 vagy újabb verzióval integrált alkalmazásokat. A legújabb SDK-verziót ajánljuk. Az ÜZLETÁGI alkalmazások alkalmazás-védelmi házirendekkel való előkészítésével kapcsolatos információkért lásd: üzletági [alkalmazások előkészítése az App Protection-szabályzatokhoz](../apps-prepare-mobile-application-management.md).
- Microsoft/harmadik féltől származó alkalmazások esetén: Győződjön meg arról, hogy az alkalmazások legújabb verzióját telepíti a felhasználók számára.

A dokumentációt és a fejlesztői útmutatót is frissítenie kell, ha ez a módosítás az SDK támogatásában is szerepel.

#### <a name="additional-information"></a>További információ
https://docs.microsoft.com/intune/apps-prepare-mobile-application-management

### <a name="plan-for-change-new-windows-updates-settings-in-intune----4464404---"></a>Tervezze meg a változást: Új Windows Update-beállítások az Intune-ban <!-- 4464404 -->
Az Intune szolgáltatásra vagy a 1908-re vonatkozó augusztusi kiadástól kezdődően új "határidő-beállításokat" adunk hozzá, amelyek a "felhasználó újraindításának engedélyezése (lefoglalt újraindítás)" beállítások helyett konfigurálhatók. Azt tervezzük, hogy letiltjuk a bekapcsolt újraindítási beállításokat a felhasználói felületen a 1909-as vagy a szeptemberi frissítés után, majd a konzolról teljesen el kell távolítani őket a konzolról október végére. 

#### <a name="how-does-this-affect-me"></a>Hogyan érint ez engem?
Ha Windows 10-es eszközöket kezel a környezetben: 
- Az Intune frissítésével vagy 1908-as verziójában az új határidő-beállítások jelennek meg a konzolon a régi, lefolytatott újraindítási beállítások mellett.
- Ha a régi és az új beállítások is konfigurálva vannak, a határidő-beállítási értékek felülbírálják a befoglalt újraindítási beállítások értékeit.
- A határidő beállításai lecserélik a "felhasználó újraindításának engedélyezése (a művelet újraindítása)" beállítást a konzolon a 1910-es frissítésben.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Hogyan készüljek fel a változásra?
Az 1908-as határidő-beállítások használatával kezdje meg a kívánt értékeket beállítani. Ha ezt megtörtént, beállíthatja a bekapcsolt újraindítási beállítást a "nincs konfigurálva" értékre, hogy előkészítse ezeket az eltávolítást a konzolról októberben.

Szükség esetén frissítse a dokumentációt és az Automation-parancsfájlokat. 

Folyamatosan frissítjük, és egy emlékeztetőt teszünk közzé az üzenetközpont előtt, mielőtt eltávolítjuk a befoglalt újraindítási beállításokat.

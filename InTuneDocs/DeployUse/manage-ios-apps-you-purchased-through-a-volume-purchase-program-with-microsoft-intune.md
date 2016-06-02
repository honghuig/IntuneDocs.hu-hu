---
# required metadata

title: Mennyiségi vásárlási program keretében vásárolt iOS-alkalmazások kezelése| Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 1dafc28a-7f8b-4fe0-8619-f977c93d1140

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Mennyiségi vásárlási program keretében vásárolt iOS-alkalmazások kezelése a Microsoft Intune-nal
Egyes alkalmazás-áruházak lehetővé teszik, hogy több licencet is vásároljon a vállalatban futtatni kívánt alkalmazásokhoz. Ezzel a megoldással csökkenthetők az alkalmazások különböző megvásárolt példányainak nyilvántartásával járó adminisztratív terhek.

A Microsoft Intune segít az ilyen programok keretében vásárolt alkalmazások kezelésében. Ehhez importálja a licencadatokat az App Store áruházból, figyelemmel kíséri, hogy hány licencet használt fel, és meggátolja, hogy több alkalmazáspéldányt használjon, mint amennyit vásárolt.

> [!Important]
> Az iOS VPP-alkalmazások licenceit az Intune jelenleg a felhasználókhoz, és nem az eszközökhöz rendeli. Emiatt az alkalmazás telepítéséhez a végfelhasználóknak meg kell adniuk Apple ID azonosítójukhoz tartozó jelszavukat.

## Nagy mennyiségben vásárolt alkalmazások felügyelete iOS-eszközökön
Az [Apple Volume Purchase Program for Business (VPP)](http://www.apple.com/business/vpp/) programon keresztül vásárolhat egyszerre több licencet az iOS-alkalmazásokhoz. Ebbe beletartozik az Apple VPP-fiók beállítása az Apple webhelyén és az Apple VPP-token feltöltése az Intune-ba.  Ezután szinkronizálhatja a mennyiségi vásárlás adatait az Intune-nal, és nyomon követheti a mennyiségi programban vásárolt alkalmazás használatát.

## Előkészületek
Mielőtt hozzálát, be kell szereznie a VPP-tokent az Apple-től, és fel kell töltenie azt az Intune-fiókjába. Ezenkívül tisztában kell lennie a következőkkel:

* Egy szervezet csak egy VPP-fiókkal és -tokennel rendelkezhet.
* Miután társította az Apple VPP-fiókot az Intune-nal, nem lehet hozzárendelni egy másik fiókot. Emiatt nagyon fontos, hogy több személy rendelkezzen az Ön által használt fiók adataival.
* Ha korábban VPP-tokent használt egy másik termékkel, egy újat kell létrehoznia az Intune használatához.
* A tokenek egy évig érvényesek.
* Alapértelmezés szerint az Intune naponta kétszer szinkronizál az Apple VPP szolgáltatással. Manuális szinkronizálás azonban bármikor kezdeményezhető.
* Miután a VPP tokent az Intune-ba importálta, ne importálja ugyanezt a tokent egy másik eszközfelügyeleti megoldásba. Ez a licenc-hozzárendelések és a felhasználói rekordok elvesztését eredményezheti.
* Mielőtt az iOS VPP-t az Intune-nal kezdené használni, távolítsa el a más MDM-megoldás használatával létrehozott összes meglévő VPP-felhasználói fiókot. Az Intune biztonsági okokból nem szinkronizálja ezeket a felhasználói fiókokat az Intune-ba. Az Intune csak az Intune által létrehozott adatokat szinkronizálja az Apple VPP szolgáltatásból. 

## Apple VPP-token beszerzése és feltöltése

1.  A [Microsoft Intune felügyeleti konzolján](https://manage.microsoft.com) kattintson a **Felügyelet** &gt; **iOS és Mac OS X** &gt;  **Volume Purchase Program** elemre.

2.  Kattintson az **Apple VPP-fiók** hivatkozásra, és ha még nem tette meg, regisztráljon a Volume Purchase Program for Business programba. Miután bejelentkezett, töltse le a fiókjához tartozó Apple VPP-tokent.

3.  Az Intune-konzol **Apple Volume Purchase Program (VPP) kezelése** oldalán kattintson a **VPP-token feltöltése** lehetőségre..

4.  A **VPP-token feltöltése** párbeszédpanelen írja be vagy másolja be a VPP-token nevét és az Apple ID-ját, majd kattintson a **Feltöltés** gombra..

5.  A figyelmeztető párbeszédpanelen a jelölőnégyzet bejelölésével jelezze, hogy tudomásul veszi, hogy később nem válthat másik VPP-fiókra, majd kattintson az **Igen** gombra..

A **Volume Purchase Program** oldalon most megtekintheti az Apple VPP-token információit, beleértve az utolsó frissítés idejét, a lejárat idejét, valamint hogy mikor volt utoljára szinkronizálva az Intune-nal.

Az Apple által tárolt adatok bármikor szinkronizálhatók az Intune-nal a **Szinkronizálás** gombra kattintva..

## Mennyiségi vásárlási programban vásárolt alkalmazás frissítése és telepítése

1.  A [Microsoft Intune felügyeleti konzolban](https://manage.microsoft.com) kattintson az **Alkalmazások** &gt; **Felügyelt szoftver** &gt; **Mennyiségi licencszerződés keretében vásárolt alkalmazások** elemre..

2.  Az [Alkalmazások hozzáadása Microsoft Intune-beli mobileszközökhöz](add-apps-for-mobile-devices-in-microsoft-intune.md) című témakörben megtalálja az alkalmazás feltöltésének, létrehozásának és telepítésének útmutatásait.

Amikor az alkalmazást **Szükséges** telepítésként telepíti, akkor az alkalmazást telepítő összes felhasználó felhasznál egy licencet.

A licencek visszanyeréséhez módosítania kell a központi telepítési műveletet az **Eltávolítás** műveletre. A licenc az alkalmazás eltávolítása után felszabadul.

Amikor egy jogosult eszközzel rendelkező felhasználó először próbál VPP-alkalmazást telepíteni, a rendszer megkéri, hogy csatlakozzon az Apple Volume Purchase programhoz. Ezt a lépést az alkalmazás telepítésének folytatása előtt kell megtennie.

> [!TIP]
> A **VPP-feltételek állapota** oszlopban azon felhasználók elfogadási állapotát tekintheti meg, akiknél az alkalmazás telepítve lett.

Ha nincsenek további elérhető licencek, a telepítés meghiúsul.

## Apple VPP-alkalmazások figyelése
A **Felügyelt szoftver** &gt; **Mennyiségi licencszerződés keretében vásárolt alkalmazások** csomópont **Alkalmazások** munkaterületén követheti nyomon, hogy mely VPP-alkalmazások lettek telepítve, és hogy hány licencet használtak fel.

> [!TIP]
> Az alkalmazás **Szűrőivel** megvizsgálhatja az egyes alkalmazástelepítések állapotát.

### Lásd még:
[Alkalmazások hozzáadása Microsoft Intune-beli mobileszközökhöz](add-apps-for-mobile-devices-in-microsoft-intune.md)



<!--HONumber=May16_HO1-->


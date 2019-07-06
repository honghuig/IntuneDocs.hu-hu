---
title: Eszközkorlátozási beállítások Android rendszerhez az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: Megtekintheti az összes olyan androidos eszközbeállítást, amelyet vezérelhet és korlátozhat a Microsoft Intune-ban. Ezekkel a beállításokkal vezérelheti a jelszavakat, a Google Playhez való hozzáférést, az alkalmazások engedélyezését vagy letiltását, a böngészőbeállításokat, az alkalmazások blokkolását, a Google-felhőbe való biztonsági mentéseket, valamint az üzenetkezelés, a hang, az adatroaming, a Wi-Fi és a Bluetooth beállításait.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ayesham, chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ac25a0f3305cdfac9f3eeaa75b9e2106b3571b0
ms.sourcegitcommit: ede86a3cb094c12e3e218b956abb9935bec76902
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/05/2019
ms.locfileid: "67572504"
---
# <a name="android-and-samsung-knox-standard-device-restriction-settings-lists-in-intune"></a>Android és Samsung Knox Standard-eszközök korlátozási beállítások listák az Intune-ban

A cikk bemutatja a Microsoft Intune összes olyan eszközkorlátozásokra vonatkozó beállítását, melyek konfigurálhatók Android rendszerű eszközökhöz.

>[!TIP]
>Ha a kívánt beállítások nem elérhetőek, lehet, hogy konfigurálni tudja az eszközöket egy [egyéni profil](custom-settings-android.md) használatával.

## <a name="general"></a>Általános

- **Kamera**: Válasszon **blokk** , hogy megakadályozza a hozzáférést a kamerához való. **Nincs konfigurálva** engedélyezi a hozzáférést az eszköz kamerájának használatát.
- **Másolás és beillesztés (csak Samsung Knox esetén)** : Válasszon **blokk** másolás és beillesztés megelőzése érdekében. **Nincs konfigurálva** az eszköz másolási és beillesztési funkcióinak engedélyezése.
- **Vágólap megosztása az alkalmazások (csak Samsung Knox esetén) közötti**: Válasszon **blokk** , hogy a másolás és beillesztés alkalmazások között a Vágólap használatával. **Nincs konfigurálva** lehetővé teszi, hogy a vágólap alkalmazások közötti másolásra és beillesztésre használatával.
- **Diagnosztikai adatok küldése (csak Samsung Knox esetén)** : Válasszon **blokk** leállítja a felhasználó az eszköz diagnosztikai adatokat küldjön. **Nincs konfigurálva** lehetővé teszi a felhasználó az adatok elküldéséhez.
- **(Csak Samsung Knox esetén) törlési**: Lehetővé teszi, hogy a felhasználó futtasson egy [törlési](devices-wipe.md) műveletet az eszközön.
- **Földrajzi hely meghatározása (csak Samsung Knox esetén)** : Válasszon **blokk** letiltani az eszközt a helyadatok használatát. **Nincs konfigurálva** lehetővé teszi, hogy az eszköz számára a helyadatok használatát.
- **Kikapcsolás (csak Samsung Knox esetén)** : Válasszon **blokk** , hogy a felhasználó általi kikapcsolásának eszköz. Ez a beállítás le van tiltva, ha a **eszköz törlése előtt bejelentkezési hibák száma** a beállítás nem állítható be, és nem működik. **Nincs konfigurálva** lehetővé teszi, hogy a felhasználót, hogy kapcsolja ki az eszközt.
- **Képernyőfelvétel (csak Samsung Knox esetén)** : Válasszon **blokk** képernyőképek elkerülése érdekében. **Nincs konfigurálva** lehetővé teszi, hogy a felhasználó képként rögzítse a képernyőn látható tartalmat.
- **Beszédfelismerési asszisztens (csak Samsung Knox esetén)** : Válasszon **blokk** a S beszédfelismerési szolgáltatás letiltása. **Nincs konfigurálva** engedélyezi a S beszédfelismerési szolgáltatás és alkalmazás az eszközön. Ez a beállítás nem alkalmazható Bixby vagy a beszédfelismerési asszisztens kisegítő lehetőségek, amely hangosan a képernyő tartalmát.
- **YouTube (csak Samsung Knox esetén)** : Válasszon **blokk** meg, hogy a felhasználók a YouTube alkalmazás használatát. **Nincs konfigurálva** lehetővé teszi, hogy az eszközön a YouTube alkalmazás használatával.
- **Megosztott eszközök (csak Samsung Knox esetén)** : Felügyelt Samsung Knox Standard-eszközök konfigurálása megosztáshoz. Ha a beállítása **engedélyezése**, a végfelhasználók az eszközt az Azure AD-beli hitelesítő adataikkal jelentkezhetnek be. Az eszköz felügyelt, marad, akár használatban van-e.</br>Használt SCEP-tanúsítványprofil be, amikor ez a funkció lehetővé teszi a végfelhasználók számára, hogy egy eszköz megoszthatja ugyanazok az alkalmazások az összes felhasználó számára. Azonban minden felhasználó rendelkezik a saját SCEP-felhasználói tanúsítványt. A felhasználói kijelentkezéskor az összes alkalmazásadat törlődik. Ez a szolgáltatás csak az üzletági alkalmazásokra érvényes. </br>**Nincs konfigurálva** megakadályozza, hogy a végfelhasználók több bejelentkezik a vállalati portál alkalmazás az eszközön, az Azure AD hitelesítő adataik használatával.
- **Dátum és időmódosítás letiltása (Samsung Knox esetén)** : Válasszon **blokk** megakadályozza, hogy a felhasználó általi módosításának dátumát és az eszköz időbeállításait. **Nincs konfigurálva** lehetővé teszi a felhasználóknak módosíthatja a dátum és idő beállítása.

## <a name="password"></a>Windows 10

- **Jelszó**: **Szükséges** a végfelhasználó számára adjon meg egy jelszót az eszköz elérésére. **Nincs konfigurálva** lehetővé teszi a felhasználóknak az eszköz elérésére anélkül, hogy jelszót írna be.

    > [!NOTE]
    > A Samsung Knox-eszközök automatikusan megkövetelnek egy 4 számjegyű PIN-kódot az MDM-regisztráció során. Natív Android-eszközök automatikusan szükség lehet a feltételes hozzáférés megfelelő PIN-kódot.

- **Jelszó minimális hossza**: Adja meg a felhasználónak meg kell adnia, (4 és 16 karakter között) jelszó minimális hosszát.
- **Ennyi perc inaktivitás képernyőzárolás**: Adja meg legfeljebb ennyi perc inaktivitás engedélyezett az eszközön a képernyőzárolás. Az eszközön a végfelhasználó nem adhat meg a profilban konfigurált időnél nagyobb értéket. A végfelhasználó kisebb értéket azonban megadhat. Ha például a profilban 15 perc van megadva, a végfelhasználó beállíthat 5 percet. 30 perces értéket azonban már nem adhat meg. 
- **Bejelentkezési hibák eszköz törlése előtt**: Adja meg a bejelentkezési hibák, hogy az eszköz törlése előtt.
- **Jelszó érvényessége (napokban)** : Adja meg a hány nap elteltével kell megváltoztatni az eszköz jelszavát.
- **Kötelező jelszótípus**: Adja meg a jelszó erősségének szintjét, és hogy használható-e biometrikus eszköz. A választható lehetőségek:
  - **Eszköz alapértelmezése**
  - **Alacsony biztonságú biometrikus**
  - **Legalább számok**
  - **Komplex numerikus**: Ismétlődő vagy egymást követő számokat, például az "1111" vagy "1234", nem engedélyezett. <sup>1</sup>
  - **Legalább betűk**
  - **Legalább alfanumerikus karakterek**
  - **Legalább alfanumerikus karakterek és szimbólumok**
- **Korábbi jelszavak újbóli használatának tiltása**: Megakadályozza, hogy a végfelhasználó általa korábban már használt jelszót hozzon létre.
- **Ujjlenyomattal történő Zárolásfeloldás (csak Samsung Knox esetén)** : Válasszon **blokk** az eszközzárolás ujjlenyomattal történő elkerülése érdekében. **Nincs konfigurálva** lehetővé teszi, hogy a felhasználó számára az eszközzárolás ujjlenyomattal történő használatával.
- **Smart Lock és más megbízhatósági ügynökök**: Válasszon **blokk** , hogy a Smart Lock és más megbízhatósági ügynökök módosíthassák a zárolási képernyő beállításai (Samsung KNOX Standard 5.0 +). A telefon, más néven bizalmi ügynök funkcióval letiltását vagy megkerülését az eszköz zárolási képernyője jelszavának, ha az eszköz megbízható helyen van. Például ez a szolgáltatás használható, ha az eszköz egy adott Bluetooth-eszközhöz van csatlakoztatva, vagy ha egy bizonyos NFC-címke közelében van. Ezzel a beállítással letilthatja, hogy a felhasználók konfigurálják az intelligens zárolást.
- **Titkosítási**: Válasszon **megkövetelése** úgy, hogy az eszközön található összes fájlnak titkosítva. Nem minden eszköz támogatja a titkosítást. Ez a funkció is használata: 
  1. Állítsa be **jelszó** való **megkövetelése**.
  2. Állítsa be **jelszó kötelező típusa** való **legalább numerikus**.
  3. Állítsa be **jelszó minimális hossza** való megfelelőség jelentéséhez ehhez a beállításhoz legalább 4-re.

  > [!NOTE]
  > Ha kényszerítve van egy titkosítási szabályzat, a Samsung Knox-eszközökön a felhasználónak be kell állítania egy 6 karakterből álló összetett jelszót eszközjelszóként.

<sup>1</sup> mielőtt ezt a beállítást eszközökhöz rendeli, ügyeljen arra, hogy a vállalati portál alkalmazás frissítése az eszközökön a legújabb verzióra.

Ha **jelszó kötelező típusa** való **komplex numerikus**, majd rendelje hozzá az Android 5.0-s verziójánál régebbi verziót futtató eszközre, majd a következő viselkedés érvényes:

- Ha a vállalati portál alkalmazás 1704-nél korábbi verziója fut., nem érvényesül PIN-kód-szabályzat sem az eszközön, és a egy hibaüzenet jelenik meg az Azure Portalon.
- Ha a Céges portál alkalmazás 1704-es vagy későbbi verzióját futtatja, csak egyszerű PIN-kód alkalmazható. Az Android korábbi verziói 5.0-nál nem támogatják ezt a beállítást. Nincs hibaüzenet jelenik meg az Azure Portalon.

## <a name="google-play-store"></a>Google Play Áruház

- **Google Play áruház (csak Samsung Knox esetén)** : Válasszon **blokk** megakadályozza, hogy a felhasználók a Google Play áruház használatával. **Nincs konfigurálva** lehetővé teszi, hogy a felhasználó számára a Google Play áruház az eszközön.

## <a name="restricted-apps"></a>Korlátozott alkalmazások

Ezek a beállítások használatával engedélyezése vagy letiltása az eszközön lévő meghatározott alkalmazások. Ez a funkció támogatott Android és Samsung Knox Standard-eszközökön:

- **Tiltott alkalmazások**: Nincs telepítve az eszközön, amelyet szeretne Intune által kezelt alkalmazások listáját. Ha a felhasználó telepít egy alkalmazást a listából, értesítést kap az Intune által.
- **Jóváhagyott alkalmazások**: Azon alkalmazások listáját, amelyek telepítése engedélyezett a felhasználók számára. Maradni megfelelő, a felhasználók nem telepíthetnek egyéb alkalmazásokat. Az Intune által kezelt alkalmazások automatikusan engedélyezettek.

Alkalmazás hozzáadása a listák, a következőket teheti:

- **Adjon hozzá** a Google Play Store URL-címét a kívánt alkalmazást. Írja be például a Microsoft távoli asztal alkalmazást Android hozzáadásához `https://play.google.com/store/apps/details?id=com.microsoft.rdc.android`. Az URL-címét egy alkalmazást, nyissa meg a [Google Play áruház](https://play.google.com/store/apps), és keresse meg az alkalmazást. Például keresse meg `Microsoft Remote Desktop Play Store` vagy `Microsoft Planner`. Válassza ki az alkalmazást, és másolja az URL-címet.
- Az alkalmazást, beleértve az URL-cím adatait tartalmazó CSV-fájl importálása. Használja a <*alkalmazás URL-címe*>, <*alkalmazásnév*>, <*alkalmazás kiadója*> formátumot. Vagy, **exportálása** egy meglévő lista, amely ugyanebben a formátumban a korlátozott alkalmazások listáját tartalmazza.

> [!IMPORTANT]
> Eszközprofilok a tiltott alkalmazások beállításait használó felhasználói csoportok hozzá kell rendelni.

## <a name="browser"></a>Browser

- **Webböngésző (csak Samsung Knox esetén)** : Válasszon **blokk** megakadályozza, hogy az alapértelmezett webböngészőjét használja az eszközön. **Nincs konfigurálva** lehetővé teszi, hogy az eszköz alapértelmezett webböngészőjét használható.
- **Automatikus kitöltés (csak Samsung Knox esetén)** : Válasszon **blokk** a szöveg a böngésző automatikus kitöltési elkerülése érdekében. **Nincs konfigurálva** lehetővé teszi, hogy a használandó a webböngésző automatikus kitöltési funkcióját.
- **Cookie-k (csak Samsung Knox)** : Válassza ki, hogyan szeretné kezelni az eszközt a webhelyek cookie-kat. A választható lehetőségek:
  - Engedélyezés
  - Az összes cookie blokkolása
  - A felkeresett webhelyek cookie-k engedélyezése
  - A jelenlegi webhely cookie-k engedélyezése
- **JavaScript (csak Samsung Knox esetén)** : Válasszon **blokk** megakadályozza, hogy a böngésző Java-parancsfájlok futtatásakor. **Nincs konfigurálva** lehetővé teszi, hogy az eszköz webböngészője Java-parancsfájlok futtatását.
- **Előugró ablakok (csak Samsung Knox esetén)** : Válasszon **blokk** , hogy az előugró ablakokat a böngészőben. **Nincs konfigurálva** lehetővé teszi, hogy az előugró ablakokat a böngészőben.

## <a name="allow-or-block-apps"></a>Alkalmazások engedélyezése és letiltása

Ezek a beállítások használatával engedélyezheti, letiltása, vagy Samsung Knox Standard-eszközökön az adott alkalmazások elrejtése. Rejtett alkalmazások nem nyitható meg, vagy a felhasználó által futtatott.

A választható lehetőségek:

- **Telepíthető alkalmazások (csak Samsung Knox Standard esetén)**
- **Nem indítható alkalmazások (csak Samsung Knox Standard esetén)**
- **Felhasználó elől elrejtett alkalmazások (csak Samsung Knox Standard esetén)**

Mindegyik beállításnál adja hozzá azokat az alkalmazásokat. A választható lehetőségek:

- **Alkalmazások hozzáadása csomagnév szerint**: Elsősorban az üzletági alkalmazásokhoz. Adja meg az alkalmazás nevét, majd az alkalmazáscsomag nevét.
- **Alkalmazások hozzáadása URL-címe szerint**: Az alkalmazás nevét, és az URL-CÍMÉT adja meg a Google Play áruházban.
- **Áruházbeli alkalmazás hozzáadása**: Az Intune-ban kezelt alkalmazások meglévő listájából válasszon ki egy alkalmazást.

## <a name="cloud-and-storage"></a>Felhő és tárolás

- **Google biztonsági mentés (csak Samsung Knox esetén)** : Válasszon **blokk** megakadályozza, hogy az eszköz szinkronizálása a Google biztonsági mentés. **Nincs konfigurálva** engedélyezi a Google biztonsági mentés.
- **Google-fiók automatikus szinkronizálása (csak Samsung Knox esetén)** : Válasszon **blokk** , hogy a Google-automatikus szinkronizálás funkciót az eszközön. **Nincs konfigurálva** lehetővé teszi, hogy a Google-Fiókbeállítások automatikus szinkronizálását.
- **Cserélhető tárolók (csak Samsung Knox esetén)** : Válasszon **blokk** megakadályozza, hogy az eszköz a cserélhető tároló használatával. **Nincs konfigurálva** lehetővé teszi, hogy az eszköz számára cserélhető tárolók, például SD-kártyák használatát.
- **Titkosítás tárolókártyákon (csak Samsung Knox esetén)** : **Szükséges** kikényszeríti, hogy a tárolókártyák titkosítva kell lennie. **Nincs konfigurálva** lehetővé teszi, hogy titkosítatlan tárolókártyák használható. Nem minden eszköz támogatja a memóriakártya titkosítását. Győződjön meg arról, hogy ellenőrizze az eszköz gyártója.

## <a name="cellular-and-connectivity"></a>Mobilhálózati és egyéb kapcsolatok

- **Adatroaming (csak Samsung Knox esetén)** : Válasszon **blokk** a mobilhálózati adatroaming elkerülése érdekében. **Nincs konfigurálva** engedélyezi az adatroaming használatát, ha az eszköz mobilhálózati.
- **Az SMS-és MMS (csak Samsung Knox esetén)** : Válasszon **blokk** , hogy a szöveg üzenetküldést az eszközön. **Nincs konfigurálva** engedélyezi az SMS- és MMS-üzenetküldést az eszközön.
- **Hangtárcsázás (csak Samsung Knox esetén)** : Válasszon **blokk** megakadályozza, hogy a felhasználók a hangtárcsázás funkciót az eszközön található használatával. **Nincs konfigurálva** lehetővé teszi, hogy a hangtárcsázási az eszközön.
- **Központi (csak Samsung Knox esetén) hangtípus**: Válasszon **blokk** a mobilhálózati hangroaming elkerülése érdekében. **Nincs konfigurálva** engedélyezi a hangroaming használatát, ha az eszköz mobilhálózati.
- **Bluetooth (csak Samsung Knox esetén)** : Válasszon **blokk** , hogy az eszköz Bluetooth használatával. **Nincs konfigurálva** lehetővé teszi, hogy a Bluetooth használatát az eszközön.
- **NFC (csak Samsung Knox esetén)** : Válasszon **blokk** leállítani a kis hatótávolságú kommunikációs (NFC) technológiát. **Nincs konfigurálva** engedélyezi kis hatótávolságú kommunikációt a támogatott eszközökön használó műveleteket.
- **Wi-Fi (csak Samsung Knox esetén)** : Válasszon **blokk** , hogy az eszköz Wi-Fi használatával. **Nincs konfigurálva** lehetővé teszi, hogy az eszköz Wi-Fi funkciót.
- **Wi-Fi alapú internetmegosztás (csak Samsung Knox esetén)** : Válasszon **blokk** , az eszköz Wi-Fi alapú internetmegosztás használatának letiltása. **Nincs konfigurálva** engedélyezi a Wi-Fi-alapú internetmegosztást az eszközön.

## <a name="kiosk"></a>Kioszkmód

A kioszkmód csak a Samsung Knox Standard eszközökre, és csak az Intune-nal felügyelt alkalmazásokra vonatkozik.

- Amennyiben az eszköz kioszk módban futtatni kívánt alkalmazások hozzáadása. Teljes képernyős módban csak a hozzáadott alkalmazások futtatásának; nincs hozzáadva alkalmazások nem futnak. Előtelepített böngészők nem futtató alkalmazás, amikor az eszköz kioszk módban van. Ha böngészőre van szüksége, fontolja meg a [Felügyelt böngésző](app-configuration-managed-browser.md) használatát.

  Az alkalmazás beállításai:

  - **Alkalmazások hozzáadása csomagnév szerint**: Elsősorban az üzletági alkalmazásokhoz. Adja meg az alkalmazás nevét, majd az alkalmazáscsomag nevét.
  - **Alkalmazások hozzáadása URL-címe szerint**: Az alkalmazás nevét, és az URL-CÍMÉT adja meg a Google Play áruházban.
  - **Áruházbeli alkalmazás hozzáadása**: Az Intune-ban kezelt alkalmazások meglévő listájából válasszon ki egy alkalmazást.

- **Képernyőalvás gombja**: Válasszon **blokk** megelőzése, vagy a képernyőalvás gombja elrejtése. **Nincs konfigurálva** lehetővé teszi, hogy a képernyő ébresztőgombját az eszközön.
- **Hangerőgombok**: Válasszon **blokk** megakadályozza, hogy a felhasználó a kötet módosításával letiltja a Hangerőszabályzó gombok használatát. **Nincs konfigurálva** lehetővé teszi, hogy a Hangerőszabályzó gombok használatát az eszközön.

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).

Teljes képernyős profilok is létrehozhat [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings) és [Windows 10-es](kiosk-settings.md) eszközök.

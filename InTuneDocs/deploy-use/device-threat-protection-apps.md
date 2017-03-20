---
title: "A Lookout for Work alkalmazás telepítése | Microsoft Docs"
description: "Lookout for Work alkalmazások konfigurálása és telepítése Android operációs rendszeren."
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 524c4209-ad57-4d35-955e-a00d796bf858
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 6f687a1db84b49bc173d2067ab95598b4485daa8
ms.openlocfilehash: ab94439d9fd5300d61c5991434d41f7fdca693d2


---

# <a name="configure-and-deploy-lookout-for-work-apps"></a>Lookout for Work alkalmazások konfigurálása és telepítése

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Ez a cikk részletes információval szolgál arról, hogyan konfigurálhatja és telepítheti a Lookout for Work alkalmazást Android és iOS eszközökre.

## <a name="android-google-play-store-app"></a>Android (Google Play Áruház alkalmazás)

1.    A [Microsoft Intune felügyeleti konzolján](https://manage.microsoft.com) válassza az **Alkalmazások**, majd az **Alkalmazások felvétele** lehetőséget.
2.    A közzétevő **Szoftver telepítése** lapján válassza a **Külső hivatkozás** elemet, és adja meg a következő URL-címet: https://play.google.com/store/apps/details?id=com.lookout.enterprise
  >[!NOTE]
  >Ne jelölje be a felügyelt böngészőt előíró jelölőnégyzetet.

3.    A **Szoftver leírása** lapon adja meg a következő információkat:
  * **Közzétevő:** Lookout Mobile Security
  * **Név:** Lookout for Work
  * **Leírás:** A Lookout a leghatékonyabb védelmet kínálja a mobil fenyegetésekkel szemben az eszköz biztonsága érdekében. Ha telepíti a Lookout alkalmazást az eszközön, az védelmet nyújt a fenyegetésekkel szemben és riasztja a felhasználót és a vállalati rendszergazdát, ha ilyet talál.
  * **Kategória:** Számítógép-felügyelet

4. A sikeres telepítést követően a következő üzenet jelenik meg: **Sikeresen befejeződött az adatok feltöltése a Microsoft Intune-ba**.

  Ha az Intune-konzolon az **Alkalmazások** elemre kattint, a listában megjelenik a **Lookout for Work** alkalmazás ![az Intune felügyeleti konzol alkalmazások lapjának képernyőképe, amelyen a listában látható a Lookout for Work alkalmazás](../media/mtp/lookout-app-listed-intune-console.png)

5. Telepítse az alkalmazást a felhasználók részére úgy, hogy kiválasztja a Lookout for Work alkalmazást, és a **Központi telepítés kezelése** lehetőséget választja.

  Ugyanazokat a felhasználókat kell kiválasztania, akiket hozzáadott a Beléptetés kezelése opcióhoz a Lookout MTP-konzolon.  A felhasználói csoportok Lookout MTP-hez történő hozzáadásáról bővebben lásd [Az előfizetés konfigurálása a Lookout MTP használatához](configure-and-deploy-lookout-for-work-apps.md) című szakasz 3. lépését.

  >[!IMPORTANT]
  > Az Intune alkalmazástelepítési varázslója nem érzékeli az Azure AD felhasználói csoportokat; ezek helyett az Intune felhasználói csoportokat használja. Ennek megfelelően a Lookout MTP-konzolon az [ebben a témakörben](plan-your-user-and-device-groups.md) leírtak szerint beléptetett Azure AD felhasználói csoport alapján létre kell hoznia egy Intune felhasználói csoportot.

6. Válassza a **Szükséges telepítés** beállítást, hogy a Lookout alkalmazás telepítését kötelezővé tegye a felhasználók eszközein.

## <a name="ios-enterprise-signed-version-of-lookout-app"></a>iOS (A Lookout alkalmazás vállalat által aláírt verziója)

1. Győződjön meg róla, hogy az **iOS-kezelés** be van állítva az eszközén. Utasítások az iOS-eszköz kezelésének beállításához:[ iOS- és Mac-eszközök kezelésének beállítása](set-up-ios-and-mac-management-with-microsoft-intune.md).

2. **Írja alá újra** a Lookout for work iOS alkalmazást. A Lookout az iOS App Store-on kívül terjeszti a Lookout for Work alkalmazását. **Az alkalmazás terjesztése előtt** újra alá kell írnia az alkalmazást az iOS vállalati fejlesztői tanúsítványával. A részletes leírást a Lookout for Work iOS alkalmazás újbóli aláírásáról lásd: [Lookout for Work iOS alkalmazás újbóli aláírásának folyamata](https://personal.support.lookout.com/hc/en-us/articles/114094038714) a Lookout oldalán.

3. Engedélyezze az Azure Active Directory-hitelesítést iOS-felhasználók számára az alábbiak szerint:
  1.  Jelentkezzen be az [Azure Active Directory felügyeleti portálon](https://manage.windowsazure.com), és keresse meg az alkalmazáslapot.
  2.  Adja hozzá a **Lookout for Work iOS alkalmazást** **natív ügyfélalkalmazásként**.
  ![a natív ügyfélalkalmazás lehetőséget mutató képernyőkép az alkalmazás hozzáadása párbeszédpanelről](../media/mtp/aad-add-app.png)
  3. Cserélje le a **com.lookout.enterprise.yourcompanyname** sort az IPA aláírásakor választott ügyfélcsomag-azonosítóval.
  4.  Adjon hozzá további átirányítási URI-t: **&lt;companyportal://code/>**, valamint az eredeti átirányítási URI-ja URLencoded verzióját.
  5.  Adjon hozzá **Delegált engedélyeket** az alkalmazásához.

  További részletek: [Natív ügyfélalkalmazás konfigurálása](https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application).

4. Töltse fel az újból aláírt .ipa fájlt az [Alkalmazások hozzáadása mobileszközökhöz a Microsoft Intune-ban](https://docs.microsoft.com/en-us/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune) témakörben leírtaknak megfelelően. Állítsa a minimum OS verziót iOS 8.0-ra vagy újabbra.

  ![képernyőkép az alkalmazások oldalról az Intune felügyeleti konzoljában, amely a Lookout for work alkalmazást mutatja az alkalmazások listáján](../media/mtp/ios-app-uploaded-intune.png)

5. Hozza létre a felügyelt alkalmazás konfigurációs szabályzatát az [iOS-alkalmazások konfigurálása mobilalkalmazás-konfigurációs szabályzatok segítségével a Microsoft Intune-ban](https://docs.microsoft.com/en-us/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune) témakörben leírtaknak megfelelően.

  ![képernyőkép egy új szabályzat létrehozása varázslóról, kiemelve az iOS 8.0 vagy újabb alkalmazás-konfigurációs szabályzatot](../media/mtp/ios-app-config.png)

6. **Telepítse az alkalmazást a felhasználók részére** úgy, hogy kiválasztja a Lookout for Work alkalmazást, és a **Központi telepítés kezelése** lehetőséget választja.

  Ugyanazokat a felhasználókat kell kiválasztania, akiket a Lookout-konzolon az Enrollment Management (Regisztráció kezelése) beállítás alatt felvett.  A felhasználói csoportok Lookout MTP-hez történő hozzáadásáról bővebben lásd [Az előfizetés konfigurálása a Lookout veszélyforrások elleni eszközvédelmének használatához](https://docs.microsoft.com/sccm/protect/deploy-use/configure-and-deploy-lookout-for-work-apps) című szakasz 3. lépését.

  >[!IMPORTANT]
  > Az Intune alkalmazástelepítési varázslója nem érzékeli az Azure AD-beli felhasználói csoportokat; ezek helyett az Intune-alapú felhasználói csoportokat használja, így azon az Azure AD-beli felhasználói csoporton alapuló Intune-os felhasználói csoportot kell létrehoznia, amely [ennek](plan-your-user-and-device-groups.md) a témakörnek megfelelően lett regisztrálva a Lookout-konzolon.

  Válassza a **Szükséges telepítés** beállítást, hogy a Lookout alkalmazás telepítését kötelezővé tegye a felhasználók eszközein.

## <a name="what-happens-when-the-deployed-app-is-opened-on-the-device"></a>Mi történik ha telepített alkalmazást megnyitja az eszközön

Amikor a felhasználó megnyitja a Lookout for Work alkalmazást az eszközön, a rendszer felszólítja a felhasználót, hogy aktiválja az alkalmazást, majd válassza a Bejelentkezés Azure Active Directoryval opciót. A végfelhasználói folyamat részletes áttekintése a következő témakörökben található:

* [A rendszer felszólítja a Lookout for Work telepítésére az Android-eszközön](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [El kell hárítania egy fenyegetést, amit a Lookout for Work talált az Android-eszközön](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## <a name="next-steps"></a>További lépések
* [Az eszközök fenyegetések elleni védelmét szolgáló szabály engedélyezése a megfelelőségi szabályzatban](https://docs.microsoft.com/sccm/protect/deploy-use/enable-device-threat-protection-rule-compliance-policy)



<!--HONumber=Feb17_HO4-->


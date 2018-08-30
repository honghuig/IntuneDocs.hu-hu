---
title: macOS-eszközök regisztrálása – Készülékregisztrációs program
titleSuffix: Microsoft Intune
description: Céges tulajdonú macOS-es eszközök regisztrálása az Apple készülékregisztrációs programjával (DEP).
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d6f9035b5a31d04e7d6ec6c5ec5b8f69a7c0943f
ms.sourcegitcommit: 0ac196d1d06f4f52f01610eb26060419d248168b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/13/2018
ms.locfileid: "40090136"
---
# <a name="automatically-enroll-macos-devices-with-apples-device-enrollment-program"></a>macOS-eszközök automatikus regisztrálása az Apple készülékregisztrációs programjával (DEP)

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Ez a cikk az Apple [Készülékregisztrációs programja (DEP)](https://deploy.apple.com) keretében vásárolt macOS-eszközök regisztrálásához nyújt segítséget. Nagyszámú eszköz DEP-regisztrálását állíthatja be anélkül, hogy kézbe venné őket. A macOS-eszközöket közvetlenül a felhasználóknak küldheti el. Amikor a felhasználó bekapcsolja az eszközt, a Beállítási asszisztens az előre konfigurált beállítások szerint fut, és regisztrálja az eszközt az Intune felügyeleti szolgáltatásban.

DEP-regisztráció beállításához az Intune- és az Apple DEP-portált is használnia kell. Olyan DEP-regisztrációs profilokat hoz létre, amelyek tartalmazzák a regisztráció során az eszközre vonatkozó beállításokat.

A DEP-regisztráció egyébként nem működik az [eszközregisztráció-kezelővel](device-enrollment-manager-enroll.md).

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>Előfeltételek
- [Apple készülékregisztrációs program](http://deploy.apple.com) keretében vásárolt eszközök
- Sorozatszámok listája vagy vásárlási megrendelési szám. 
- [MDM-szolgáltató ](mdm-authority-set.md)
- [Apple MDM Push-tanúsítvány](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Apple DEP-token beszerzése

Az macOS-eszközök DEP-regisztrációjához először is egy Apple-től származó DEP-tokenre (.p7m) van szükség. Ez a token (jogkivonat) teszi lehetővé az Intune számára a vállalat által birtokolt DEP-eszközök adatainak szinkronizálását. A token ezenkívül lehetővé teszi, hogy az Intune feltöltse a regisztrációs profilokat az Apple adatbázisába, és eszközöket rendeljen az egyes profilokhoz.

A DEP-tokent az Apple DEP-portálon hozhatja létre. Szintén a DEP-portál használatával rendelheti hozzá az eszközök felügyeletét az Intune-hoz.

> [!NOTE]
> Ha törli a tokent a klasszikus Intune-portálról az Azure-ba történő migrálás előtt, előfordulhat, hogy az Intune visszaállít egy korábban törölt Apple DEP-tokent. Ilyenkor a DEP-tokent ismét törölheti az Azure Portalról.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>1. lépés Töltse le a nyilvános kulcsú Intune-tanúsítványt, amelyre szükség van a token létrehozásához.

1. Az [Azure-beli Intune-portálon](https://aka.ms/intuneportal) válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** > **Hozzáadás** elemet.

    ![Szerezzen be egy készülékregisztrációs programbeli tokent.](./media/device-enrollment-program-enroll-ios/image01.png)

2. Engedélyezze a Microsoftnak az **Elfogadom** lehetőség választásával a felhasználó- és eszközadatok Apple-nek való elküldését.

   ![Képernyőkép – A Készülékregisztrációs program tokenje panel az Apple tanúsítványok munkaterületen – nyilvános kulcs letöltése.](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. Kattintson a **Nyilvános kulcs letöltése** elemre a titkosításikulcs-fájl (.pem) letöltéséhez és helyi mentéséhez. A .pem fájllal megbízhatósági kapcsolati tanúsítványt kérhet az Apple Device Enrollment Program portálról.


### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>2. lépés Töltsön le a kulcsa segítségével egy tokent az Apple-től.

1. A **Token létrehozása az Apple Készülékregisztrációs programjában** elemre kattintva nyissa meg az Apple Központi Telepítési Program portálját, és jelentkezzen be a cége Apple-azonosítójával. A későbbiekben ezt az Apple ID-t használhatja a DEP-token megújításához.
2.  Az Apple [Központi Telepítési Program portálján ](https://deploy.apple.com) válassza a**Készülékregisztrációs program** **Első lépések** elemét.

3. A **Kiszolgálók kezelése** lapon válassza az **MDM-kiszolgáló hozzáadása** lehetőséget.
4. Az **MDM Server Name** (MDM-kiszolgáló neve) mezőben adja meg az MDM-kiszolgáló nevét, majd kattintson a **Next** (Tovább) gombra. A kiszolgálónév Önnek segít a mobileszköz-felügyeleti (MDM-) kiszolgáló azonosításában, nem ez a Microsoft Intune-kiszolgáló URL-címe vagy neve.

5. Megjelenik a **Hozzáadás:&lt;Kiszolgálónév&gt;** párbeszédablak, és kéri **a nyilvános kulcs feltöltését**. Kattintson a **Choose File…** (Fájl kiválasztása…) elemre a .pem-fájl feltöltéséhez, majd válassza a **Next** (Tovább) lehetőséget.

6. Válassza a **Deployment Programs** (Telepítési programok) &gt; **Device Enrollment Program** (Készülékregisztrációs program) &gt; **Manage Devices** (Eszközök kezelése) lehetőséget.
7. Az **Eszközök kiválasztásának szempontja** alatt adja meg az eszközök azonosításának módját:
    - **Sorozatszám**
    - **Sorszám**
    - **CSV-fájl feltöltése**.

   ![Képernyőkép – Eszközök kiválasztásának beállítása: sorozatszám alapján. Választott tevékenység: hozzárendelés kiszolgálóhoz. Kiszolgálónév megadása.](./media/enrollment-program-token-specify-serial.png)

8. A **Választott tevékenység** területen jelölje ki a **Hozzárendelés kiszolgálóhoz** elemet, válassza Microsoft Intune-hoz megadott &lt;Kiszolgálónevet&gt;, majd kattintson az **OK** gombra. Az Apple-portál az Intune-kiszolgálóhoz rendeli a megadott eszközök kezelését, majd megjeleníti a **Hozzárendelés kész** üzenetet.

   Az Apple-portál **Központi telepítési programok** &gt; **Készülékregisztrációs program** &gt; **Hozzárendelési előzmények** menüpontjában jeleníthető meg az eszközök és a hozzájuk tartozó MDM-kiszolgálók listája.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>3. lépés. Mentse a token létrehozásához használt Apple ID-t.

Az Azure-beli Intune-portálon adja meg az Apple ID azonosítót későbbi felhasználásra.

![Képernyőkép – A DEP-token létrehozásához használt Apple ID megadása és a DEP-token megkeresése.](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>4. lépés. Töltse fel a tokent.
Az **Apple-token** mezőben keresse meg tallózással a tanúsítványfájlt (.pem), és válassza a **Megnyitás**, majd a **Létrehozás** lehetőséget. A leküldéses tanúsítvány lehetővé teszi, hogy az Intune regisztrálja és felügyelje a macOS-eszközöket a szabályzatoknak a regisztrált eszközökre való leküldésével. Az Intune automatikusan szinkronizálja az Apple-lel a regisztrációs programfiók adatait.

## <a name="create-an-apple-enrollment-profile"></a>Apple-regisztrációs profil létrehozása

Most, hogy telepítette a jogkivonatot, létrehozhatja a regisztrációs profilt a DEP-eszközökhöz. A regisztrálás során az eszközök csoportjára alkalmazott beállításokat egy készülékregisztrációs profil határozza meg.

1. Az Azure-beli Intune-portálon válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** elemet.
2. Válasszon egy tokent, és válassza a **Profilok**, majd a **Profil létrehozása** lehetőséget.

    ![Képernyőkép a profil létrehozásáról.](./media/device-enrollment-program-enroll-ios/image04.png)

3. A **Profil létrehozása** panelen adminisztrációs célból adja meg a profil **Nevét** és **Leírását**. Ezeket a felhasználók nem fogják látni. A **Név** mező felhasználásával dinamikus csoportot hozhat létre az Azure Active Directoryban. Használja a profilnevet az enrollmentProfileName paraméter meghatározásához, hogy ezzel a regisztrációs profillal rendelhesse hozzá az eszközöket. További információk az [Azure Active Directory-alapú dinamikus csoportokról](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).

    ![A profil neve és leírása.](./media/device-enrollment-program-enroll-macos/createprofile.png)

4. A **Platform** területen válassza az **macOS** lehetőséget.

5. A **Felhasználói affinitást** aszerint állítsa be, hogy a profilhoz tartozó eszközöket hozzárendelt felhasználóval vagy anélkül szükséges-e regisztrálni.
    - **Regisztráció felhasználói affinitással** – Ezt a lehetőséget olyan eszközökhöz válassza, amelyek a felhasználók tulajdonában vannak, de egyes szolgáltatásokhoz, például alkalmazások telepítéséhez, a Céges portál alkalmazást kívánják használni. ADFS használata esetén a felhasználói affinitáshoz [WS-Trust 1.3 Username/Mixed végpont](https://technet.microsoft.com/library/adfs2-help-endpoints) szükséges. [További információ](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).A többtényezős hitelesítés nincs támogatva felhasználói affinitást használó macOS DEP-eszközökön.

    - **Regisztráció felhasználói affinitás nélkül** – Ezt a lehetőséget olyan eszközökhöz válassza, amelyek nincsenek egy adott felhasználóhoz társítva. Olyan eszközökhöz használja, amelyek a helyi felhasználói adatokhoz való hozzáférés nélkül végeznek feladatokat. Egyes alkalmazások, mint például a Céges portál alkalmazás, nem működnek.

6. Válassza az **Eszközkezelési beállításokat**, és válassza ki, hogy zárolt regisztrációt szeretne-e alkalmazni az ezt a profilt használó eszközökhöz. A **Zárolt regisztráció** letiltja azokat a macOS-beállításokat, amelyek segítségével eltávolítható a felügyeleti profil a **Rendszerbeállítások** menü vagy a **Terminál** használatával. Az eszköz regisztrálása után ez a beállítás nem módosítható az eszköz gyári beállításainak visszaállítása állítása nélkül.

    ![Az Eszközkezelési beállítások képernyőképe.](./media/device-enrollment-program-enroll-macos/devicemanagementsettingsblade-macos.png)
 
7. Válassza az **OK** gombot.

8. Válassza a **Beállítási asszisztens beállításai** elemet, és konfigurálja az alábbi profilbeállításokat:  ![A beállítási asszisztens testreszabása.](./media/device-enrollment-program-enroll-macos/setupassistantcustom-macos.png)


    |                 Beállítás                  |                                                                                               Description                                                                                               |
    |------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    |     <strong>Részleg neve</strong>     |                                                             Akkor jelenik meg, ha a felhasználó az aktiválás során a <strong>Konfiguráció névjegye</strong> elemre koppint.                                                              |
    |    <strong>Részleg telefonszáma</strong>     |                                                          Akkor jelenik meg, ha a felhasználó az aktiválás során a <strong>Segítségre van szüksége?</strong> gombra kattint.                                                          |
    | <strong>Beállítási asszisztens – Beállítások</strong> |                                                     Ezeknek a beállításoknak a megadása nem kötelező, és a macOS <strong>Beállítások</strong> menüjében később is konfigurálhatók.                                                      |
    |        <strong>PIN-kód</strong>         | PIN-kód kérése aktiváláskor. PIN-kód megadására mindig szükség van, kivéve, ha az eszköz biztonságát, illetve elérésének szabályozását valamilyen más módszer biztosítja (például teljes képernyős mód, amely egyetlen alkalmazás futtatására korlátozza az eszközt). |
    |    <strong>Helyalapú szolgáltatások</strong>    |                                                                 Ha bekapcsolja ezt a funkciót, a Beállítási asszisztens az aktiválás során kérni fogja ezt a szolgáltatást.                                                                  |
    |         <strong>Visszaállítás</strong>         |                                                                Ha bekapcsolja ezt a funkciót, a Beállítási asszisztens az aktiválás során iCloud-alapú biztonsági mentést fog kérni.                                                                 |
    |   <strong>iCloud és Apple ID</strong>   |                         Ha bekapcsolja ezt a funkciót, a Beállítási asszisztens kéri a felhasználót, hogy jelentkezzen be egy Apple ID azonosítóval, és az Alkalmazások és adatok képernyőn lehetőség lesz majd az eszköz iCloud-alapú biztonsági mentésből való visszaállítására.                         |
    |  <strong>Feltételek és kikötések</strong>   |                                                   Ha bekapcsolja ezt a funkciót, a Beállítási asszisztens az aktiválás során arra fogja kérni a felhasználót, hogy fogadja el az Apple használati feltételeit.                                                   |
    |        <strong>Touch ID</strong>         |                                                                 Ha bekapcsolja ezt a funkciót, a Beállítási asszisztens az aktiválás során kérni fogja ezt a szolgáltatást.                                                                 |
    |        <strong>Apple Pay</strong>        |                                                                 Ha bekapcsolja ezt a funkciót, a Beállítási asszisztens az aktiválás során kérni fogja ezt a szolgáltatást.                                                                 |
    |          <strong>Nagyítás</strong>           |                                                                 Ha bekapcsolja ezt a funkciót, a Beállítási asszisztens az aktiválás során kérni fogja ezt a szolgáltatást.                                                                 |
    |          <strong>Siri</strong>           |                                                                 Ha bekapcsolja ezt a funkciót, a Beállítási asszisztens az aktiválás során kérni fogja ezt a szolgáltatást.                                                                 |
    |     <strong>Diagnosztikai adatok</strong>     |                                                                 Ha bekapcsolja ezt a funkciót, a Beállítási asszisztens az aktiválás során kérni fogja ezt a szolgáltatást.                                                                 |
    |     <strong>FileVault</strong>           |  |
    |     <strong>iCloud-diagnosztika</strong>  |  |
    |     <strong>Regisztráció</strong>        |  |


10. Válassza az **OK** gombot.

11. Válassz a **Létrehozás** elemet a profil mentéséhez.

## <a name="sync-managed-devices"></a>Felügyelt eszközök szinkronizálása
Miután az Intune engedélyt kapott az eszközei felügyeletére, szinkronizálhatja az Intune-t az Apple-lel, hogy megtekinthesse a felügyelt eszközöket az Azure-beli Intune-portálon.

1. Az Azure-beli Intune-portálon válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** lehetőséget, válasszon egy tokent a listából, majd válassza az **Eszközök** > **Szinkronizálás** lehetőséget. ![Képernyőkép – A Szinkronizálás hivatkozás választása a Készülékregisztrációs programba felvett eszközök mező kijelölése után.](./media/device-enrollment-program-enroll-ios/image06.png)

   Az Apple elfogadható regisztrációs programforgalomra vonatkozó feltételeinek teljesítése céljából az Intune az alábbi korlátozásokat írja elő:
   - Teljes szinkronizálás legfeljebb hétnaponta futtatható. A teljes szinkronizálás során az Intune beolvassa az Intune-hoz csatlakoztatott Apple MDM-kiszolgálóhoz rendelt sorozatszámok frissített teljes listáját. Miután egy Készülékregisztrációs programbeli eszközt úgy törölnek az Intune portálról, hogy nem szüntetik meg az Apple MDM-kiszolgálóval való társítását a DEP-portálon, csak a teljes szinkronizálás lefuttatása után lesz újraimportálva az Intune-ba.   
   - A szinkronizálás futtatása automatikusan történik 24 óránként. A **Szinkronizálás** gombra kattintva is végezhet szinkronizálást (legfeljebb 15 percenként egyszer). Az összes szinkronizálási kérelemnek 15 percen belül kell befejeződnie. A szinkronizálás befejeződéséig a **Szinkronizálás** gomb letiltott. A szinkronizálás frissíti a meglévő eszközök állapotát, és a importálja az Apple MDM-kiszolgálóhoz rendelt új eszközöket.   


## <a name="assign-an-enrollment-profile-to-devices"></a>Regisztrálási profil eszközökhöz rendelése
Ahhoz, hogy egy eszközt regisztrálni lehessen, először hozzá kell rendelni egy regisztrációs programprofilt.

1. Az Azure-beli Intune-portálon válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** lehetőséget, és válasszon egy tokent a listából.
2. Válassza az **Eszközök** lehetőséget, válasszon eszközöket a listából, majd válassza a **Profil hozzárendelése** elemet.
3. A **Profil hozzárendelése** területen válasszon egy profilt az eszközökhöz, majd válassza a **Hozzárendelés** lehetőséget.

### <a name="assign-a-default-profile"></a>Alapértelmezett profil hozzárendelése

Választhat egy alapértelmezett macOS- vagy iOS-profilt, amelyet a rendszer az adott tokennel regisztráló összes eszközre alkalmaz. 

1. Az Azure-beli Intune-portálon válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** lehetőséget, és válasszon egy tokent a listából.
2. Válassza az **Alapértelmezett profil beállítása** lehetőséget, válasszon egy profilt a legördülő listából, majd válassza a **Mentés** lehetőséget. A választott profil alkalmazva lesz az adott tokennel regisztráló összes eszközre.

## <a name="distribute-devices"></a>Eszközök terjesztése
Az eddigiekben engedélyezte az eszközfelügyeletet és a szinkronizálást az Apple és az Intune között, valamint a DEP-eszközök regisztrálása céljából hozzárendelt egy profilt. Az eszközök ekkor már kioszthatók a felhasználóknak. Felhasználói affinitással rendelkező eszközök esetén minden felhasználóhoz hozzá kell rendelni egy Intune-licencet. A felhasználói affinitás nélküli eszközökhöz licenc szükséges. Regisztrációs profil csak akkor léptethető érvénybe egy aktivált eszközön, ha előtte visszaállítják az eszköz gyári beállításait.

## <a name="renew-a-dep-token"></a>DEP-token megújítása  
1. Ugrás a deploy.apple.com címre.  
2. A **Manage Servers** (Kiszolgálók kezelése) területen válassza ki a megújítani kívánt token-fájlhoz társított MDM-kiszolgálót.
3. Válassza a **Generate New Token** (Új token létrehozása) lehetőséget.

    ![Képernyőkép új token generálásáról.](./media/device-enrollment-program-enroll-ios/generatenewtoken.png)

4. Válassza a **Your Server Token** (Saját kiszolgálói token) lehetőséget.  
5. Az [Azure-beli Intune-portálon](https://aka.ms/intuneportal) válassza az **Eszközök regisztrálása** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** lehetőséget, és válasszon ki a tokent.
    ![Képernyőkép a regisztrációs program jogkivonatairól.](./media/device-enrollment-program-enroll-ios/enrollmentprogramtokens.png)

6. Válassza a **Jogkivonat megújítása** lehetőséget, majd adja meg az eredeti jogkivonat létrehozásához használt Apple ID-t.  
    ![Képernyőkép új token generálásáról.](./media/device-enrollment-program-enroll-ios/renewtoken.png)

8. Töltse fel az újonnan letöltött tokent.  
9. Válassza a **Token megújítása** lehetőséget. Látni fogja a token megújításáról szóló megerősítő üzenetet.   
    ![Képernyőkép a megerősítésről.](./media/device-enrollment-program-enroll-ios/confirmation.png)

## <a name="next-steps"></a>További lépések

A macOS-eszközöket a regisztrálás után azonnal [kezelheti is](device-management.md).
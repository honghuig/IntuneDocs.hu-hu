---
title: Oktatóanyag – használja az Apple üzleti vezető vagy a Készülékregisztrációs programmal az Intune-ban iOS-eszközök regisztrálása
titleSuffix: Microsoft Intune
description: Ebben az oktatóanyagban kell beállítani az Apple vállalati tulajdonú eszközök regisztrálási funkciók ABM az iOS-eszközök regisztrálásához.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up the Apple's corporate device enrollment features so that corporate devices can automatically enroll in Intune.
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1fda4268e66703c8bd2132c9af22fed52f1791b1
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/03/2019
ms.locfileid: "67548961"
---
# <a name="tutorial-use-apples-corporate-device-enrollment-features-in-apple-business-manager-abm-to-enroll-ios-devices-in-intune"></a>Oktatóanyag: Az Intune-ban iOS-eszközök regisztrálása az Apple üzleti Manager (ABM) az Apple munkahelyi eszközök regisztrációja funkciók használata
Az Eszközregisztrációs szolgáltatás az Apple üzleti Managerben egyszerűbbé teszi az eszközök regisztrálását. Az Intune is támogatja a régebbi az Apple Készülékregisztrációs Program (DEP), portál, de javasoljuk, hogy kezdhet tiszta lappal Apple üzleti vezető. A Microsoft Intune és a vállalati Apple-eszközök regisztrálása az eszközök automatikusan biztonságosan lesz regisztrálva az első alkalommal a felhasználó bekapcsolja az eszközt. Ezért el olyan eszközöket, számos felhasználó számára anélkül, hogy minden egyes eszköz beállításához külön-külön kellene. 

Az oktatóanyag segítségével megtanulhatja a következőket:
> [!div class="checklist"]
> * Az Apple-Eszközbeléptetési jogkivonat beszerzése
> * Az Intune-hoz a felügyelt eszközök szinkronizálása
> * Beléptetési profil létrehozása
> * A regisztrációs profil hozzárendelése eszközökhöz

Ha nem rendelkezik Intune-előfizetéssel, [regisztráljon egy ingyenes próbafiókkal](free-trial-sign-up.md).

## <a name="prerequisites"></a>Előfeltételek
- Keretében vásárolt eszközök [Apple üzleti vezető](https://business.apple.com) vagy [az Apple Készülékregisztrációs Program](http://deploy.apple.com)
- Állítsa be a [mobileszköz-felügyeleti szolgáltatóként](mdm-authority-set.md)
- Get- [Apple MDM Push-tanúsítvány](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-device-enrollment-token"></a>Az Apple-Eszközbeléptetési jogkivonat beszerzése
Vállalati beléptetési funkciókat az Apple iOS eszközök beléptetése előtt kell egy Apple-Eszközbeléptetési jogkivonat (.pem) fájlt. Ez a token lehetővé teszi, hogy a vállalat által birtokolt Apple-eszközök az Intune szinkronizálja az adatait. Azt is engedélyezi, hogy az Intune regisztrációs profilokat töltsön fel az Apple számára, és eszközöket rendeljen ezen profilokhoz.

A ABM vagy DEP portal segítségével egy Eszközregisztráció-token létrehozásához. A portálok az eszközök hozzárendelése kezelés céljából az Intune-hoz is használhatja.

1. Az [Azure-beli Intune-portálon](https://aka.ms/intuneportal) válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** > **Hozzáadás** elemet.

2. Engedélyezze a Microsoftnak az **Elfogadom** lehetőség választásával a felhasználó- és eszközadatok Apple-nek való elküldését.

   ![Képernyőkép – A Készülékregisztrációs program tokenje panel az Apple tanúsítványok munkaterületen – nyilvános kulcs letöltése.](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. Kattintson a **Nyilvános kulcs letöltése** elemre a titkosításikulcs-fájl (.pem) letöltéséhez és helyi mentéséhez. A PEM-fájllal megbízhatósági kapcsolati tanúsítványt kérhet az ABM vagy DEP portálról szolgál.

4. A **Token létrehozása az Apple Készülékregisztrációs programjában** elemre kattintva nyissa meg az Apple Központi Telepítési Program portálját, és jelentkezzen be a cége Apple-azonosítójával. A későbbiekben ezt az Apple ID-t használhatja a DEP-token megújításához.

5. Az Apple [Központi Telepítési Program portálján ](https://deploy.apple.com) válassza a**Készülékregisztrációs program** **Első lépések** elemét. Lehet, hogy a folyamat kissé eltérő, mint az alábbi lépések [Apple üzleti vezető](https://business.apple.com).

4. A **Kiszolgálók kezelése** lapon válassza az **MDM-kiszolgáló hozzáadása** lehetőséget.

5. A **MDM-kiszolgáló nevét**, adja meg *TestMDMServer* majd **tovább**. A kiszolgálónév Önnek segít a mobileszköz-felügyeleti (MDM-) kiszolgáló azonosításában, A neve vagy URL-címét a Microsoft Intune-kiszolgáló nem.

6. Megjelenik a **Hozzáadás:&lt;Kiszolgálónév&gt;** párbeszédablak, és kéri **a nyilvános kulcs feltöltését**. Válassza ki **fájl kiválasztása...** a .pem-fájl feltöltéséhez, majd válassza a **Next** (Tovább) lehetőséget.

6. Lépjen a **központi telepítési program** > **Device Enrollment Program** > **Eszközkezelés**.
7. A **Choose Devices By**, válassza a **sorozatszám**. <!--ask Tiffany about this-->

8. A **Választott tevékenység** területen jelölje ki a **Hozzárendelés kiszolgálóhoz** elemet, válassza Microsoft Intune-hoz megadott &lt;Kiszolgálónevet&gt;, majd kattintson az **OK** gombra. Az Apple-portál az Intune-kiszolgálóhoz rendeli a megadott eszközök kezelését, majd megjeleníti a **Hozzárendelés kész** üzenetet.

   Az Apple-portál **Központi telepítési programok** &gt; **Készülékregisztrációs program** &gt; **Hozzárendelési előzmények** menüpontjában jeleníthető meg az eszközök és a hozzájuk tartozó MDM-kiszolgálók listája.

9. Adja meg a token létrehozásához használt Apple ID Azonosítót későbbi felhasználás céljából, az Intune-ban az Azure Portalon.

    ![Képernyőkép – A DEP-token létrehozásához használt Apple ID megadása és a DEP-token megkeresése.](./media/device-enrollment-program-enroll-ios/image03.png)

10. Az **Apple-token** mezőben keresse meg tallózással a tanúsítványfájlt (.pem), és válassza a **Megnyitás**, majd a **Létrehozás** lehetőséget. 

11. Ha szeretné, hogy mely rendszergazdák rendelkeznek jogosultsággal az ezt a jogkivonatot korlát Hatókörcímkék alkalmazandó, a hatókörök kiválasztása.

## <a name="create-an-apple-enrollment-profile"></a>Apple-regisztrációs profil létrehozása
Most, hogy telepítette a jogkivonatot, létrehozhat egy regisztrációs profilt a vállalat által birtokolt iOS-eszközökhöz. A regisztrálás során az eszközök csoportjára alkalmazott beállításokat egy készülékregisztrációs profil határozza meg.

1. Az Azure-beli Intune-portálon válassza az **Eszközök beléptetése** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** elemet.

2. Válassza ki az imént telepített jogkivonat, válassza a **profilok** > **profil létrehozása**.

3. A **profil létrehozása**, adja meg *TestDEPProfile* a **neve** és *tesztelés DEP iOS-eszközök* a **leírása** . Ezeket a felhasználók nem fogják látni.

4. Válasszon **iOS** alatt **Platform**.

5. Határozza meg, hogy az eszközök regisztrálása nélkül szeretné **felhasználói affinitással**. Adott felhasználók által használt eszközök felhasználói affinitással tervezték. Ha a felhasználók érdemes használni a céges portál például alkalmazások telepítéséhez, válassza a **felhasználói affinitással való regisztrálást**. Ha a felhasználóknak nem kell a vállalati portálon, vagy a legtöbb felhasználó-eszköz kiépítése, válassza a kívánt **felhasználói affinitás nélküli regisztrálást**.

6. Ha úgy döntött, hogy regisztráció felhasználói affinitással, állapítsa meg, ha szeretné, hogy végezzen hitelesítést a céges portál vagy az Apple beállítási asszisztens. Ha szeretné használni a multi-factor Authentication engedélyezése esetén az első bejelentkezéskor jelszómódosítást vagy felhasználóktól, hogy lejárt jelszavukat visszaállítása a regisztráció során, válassza a **Igen** alatt **hitelesítéshez Céges portál az Apple beállítási asszisztens helyett**. Ha kényelmes Apple által megadott használatával az Apple beállítási asszisztens segítségével alapszintű HTTP-hitelesítést, válassza a **nem**.

7. Ha úgy döntött, hogy regisztrálja a felhasználói affinitás és a céges portálon való hitelesítéssel, határozza meg, ha szeretné-e telepíteni a vállalati portált az Apple Volume Purchase Program (VPP). A vállalati portál telepít a VPP-tokent, ha a felhasználó nem kell a vállalati portál letöltése az app store-ból a regisztráció során egy Apple ID Azonosítóját és jelszavát adja meg. Válasszon **Token használata:** alatt **céges portál telepítése a VPP-** jelölje be a VPP-tokent, amely elérhető a céges portál ingyenes licenccel rendelkezik. Ha nem szeretné telepíteni a vállalati portált, válassza a VPP használatával **ne használjon VPP** alatt **céges portál telepítése a VPP-** . 

8. Ha úgy döntött, hogy regisztráció felhasználói affinitással, hitelesítés, a céges portál és a VPP, a vállalati portál telepítése döntse el, ha szeretné-e a céges portált hitelesítési egyetlen alkalmazás módban futtatott. Ez a beállítás lehetővé teszi annak érdekében, hogy a felhasználó nem rendelkezik más alkalmazásokhoz való hozzáférés, amíg befejezését követően a vállalati regisztrációra. Ha ezt a folyamatot, amíg a felhasználó korlátozni szeretné a regisztráció befejezését, válassza a **Igen** alatt **egyetlen alkalmazás módba, amíg a hitelesítést a céges portál futtassa**. 

9. Válasszon **Eszközfelügyeleti beállítások** válassza **Igen** alatt **felügyelt**. Felügyelt eszközökön a vállalati iOS-eszközök esetén a legtöbb felügyeleti lehetőségeket biztosítanak.

10. Válasszon **Igen** alatt **zárolt regisztráció** annak érdekében, hogy a felhasználók nem távolítható el a céges eszközök felügyeletét. 

11. Válasszon egy beállítást **szinkronizálást számítógépekkel** meghatározni, ha az iOS-eszközöket fog tudni szinkronizálni számítógépekkel.

12. Alapértelmezés szerint az Apple-neveket az eszközre az eszköz típusától (pl. Ipaden). Ha szeretné adjon meg egy másik nevet sablont, válassza a **Igen** alatt **eszköz neve sablon alkalmazása**. Adja meg a nevét, amelyet szeretne alkalmazni az eszközökre, ahol a karakterláncok *{{soros}}* és *{{MEGTALÁLT}}* minden egyes eszköz sorozatszámát és eszköztípus helyettesíti. Ellenkező esetben válasszon **nem** alatt **eszköz neve sablon alkalmazása**.

13. Válassza az **OK** gombot.

14. Válasszon **beállítási asszisztens testreszabása** , és adja meg *oktatóanyag részleg* a **részleg neve**. Ez a karakterlánc mit látnak a felhasználók Ha rákoppintanak **konfigurációjával kapcsolatos** eszköz az aktiválás során.

15. A **részleg telefonszáma**, adjon meg egy telefonszámot. Ez a szám jelenik meg, amikor a felhasználók a **segítségre van szüksége** gomb az aktiválás során.

16. Is **megjelenítése** vagy **elrejtése** különböző képernyőkkel eszköz az aktiválás során. A legjobb beléptetést, jelölje be minden képernyőjén **elrejtése**.

17. Válassza az **OK** > **Létrehozás** lehetőségeket.

## <a name="sync-managed-devices-to-intune"></a>Az Intune-hoz a felügyelt eszközök szinkronizálása

Miután Portal ABM, ASM vagy DEP készülékregisztrációs programbeli token beállítása, és ott eszközöket rendeljen az MDM-kiszolgáló, várja meg, ezek az eszközök szinkronizálása az Intune szolgáltatásba, vagy manuálisan leküldése a szinkronizálást. A manuális szinkronizálás nélkül eszközök megjelennek az Azure Portalon akár 24 órát hozhat.

1. Az Intune-ban az Azure Portalon, válassza ki a **eszközregisztráció** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** > Válasszon egy tokent a a lista > **eszközök** > **szinkronizálási**.

## <a name="assign-an-enrollment-profile-to-ios-devices"></a>IOS-eszközökre egy regisztrációs profil hozzárendelése

Ahhoz, hogy egy eszközt regisztrálni lehessen, először hozzá kell rendelni egy regisztrációs programprofilt. Ezek az eszközök szinkronizálva lesznek az Intune-ban az Apple-től, és hozzá kell rendelni a megfelelő MDM-kiszolgálói jogkivonat a ABM, ASM vagy DEP-portálon.

1. Az Intune-ban az Azure Portalon, válassza ki a **eszközregisztráció** > **Apple-regisztráció** > **Készülékregisztrációs programbeli token** > Válassza ki a tokent a listában.
2. Válassza az **Eszközök** lehetőséget, válasszon eszközöket a listából, majd válassza a **Profil hozzárendelése** elemet.
3. A **Profil hozzárendelése** területen válasszon egy profilt az eszközökhöz, majd válassza a **Hozzárendelés** lehetőséget.

## <a name="distribute-devices-to-users"></a>Eszközök terjesztése a felhasználóknak

Beállított felügyeleti és az Apple és az Intune közötti szinkronizálása és hozzárendelt egy profilt a DEP-eszközök regisztrálása lehetővé teszik. Az eszközök ekkor már kioszthatók a felhasználóknak. Felhasználói affinitással rendelkező eszközök esetén minden felhasználóhoz hozzá kell rendelni egy Intune-licencet.

## <a name="next-steps"></a>További lépések

IOS-eszközök regisztrációjával kapcsolatos annak elérhető egyéb beállításokkal kapcsolatos további információkért.

> [!div class="nextstepaction"]
> [Részletes iOS DEP regisztrációs cikk](device-enrollment-program-enroll-ios.md)

<!--commenting out because inaccurate>
## Clean up resources
<!--If you don't want to use iOS corporate enrolled devices anymore, you can delete them.>
<!--- If the devices are enrolled in Intune, you must first [delete them from the Azure Active Directory portal](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).>

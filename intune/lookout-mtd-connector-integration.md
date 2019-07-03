---
title: A Lookout-integráció beállítása a Microsoft Intune-ban
titleSuffix: Microsoft Intune
description: Ismerje meg az Intune integrálása a Lookout Mobile Endpoint Securityhez, a Mobile Threat Defense megoldásban, a vállalati erőforrások mobil elérése.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/11/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5b0d7644-3183-45ba-a165-0d82d70cb71e
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be2e9371288961d0afdf7ad6e8cfec8f734087f6
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67529833"
---
# <a name="set-up-lookout-mobile-endpoint-security-integration-with-intune"></a>Intune Lookout Mobility Endpoint Security-integráció beállítása
Egy olyan környezetben, amely megfelel a [Előfeltételek](lookout-mobile-threat-defense-connector.md#prerequisites), az Intune-nal integrálható a Lookout Mobile Endpoint Securityhez. Ebben a cikkben található információk végigvezeti az integráció beállításával és a fontos beállítások konfigurálása a Lookout Intune-ban való használatra.  

> [!IMPORTANT]
> Egy olyan létező Lookout Mobility Endpoint Security-bérlő, amely még nincs társítva az Azure AD-bérlőjéhez, nem használható fel az Azure AD-val és az Intune-nal való integrációhoz. Új Lookout Mobility Endpoint Security-bérlő létrehozásához lépjen kapcsolatba a Lookout támogatási csapatával. Azure AD-felhasználói számára használja az új bérlőt.

## <a name="collect-azure-ad-information"></a>Azure AD-információk gyűjtése  
Az Intune-nal integrált lookout a Lookout Mobility Endpoint Security-bérlő az Azure Active Directory (AD) előfizetés társítania.

A Lookout Mobile Endpoint Securityhez előfizetés integrációjának engedélyezése az Intune-ban, adja meg a következő információkat a Lookout-támogatásnak (enterprisesupport@lookout.com):  

- **Azure AD-bérlő címtár-azonosító**  

- **Az Azure AD-csoport Objektumazonosító** csoport **teljes** hozzáféréséhez a konzolhoz a Lookout Mobile Endpoint Security (MES).  
  A felhasználói csoportot hoz létre az Azure AD-felhasználókkal rendelkező *teljes hozzáférés* való bejelentkezéshez a **Lookout-konzolon**. Felhasználók tagjai ennek a csoportnak, vagy a választható csak akkor *korlátozott hozzáférés* csoport, a Lookout konzolra való bejelentkezéshez. 

- **Az Azure AD-csoport Objektumazonosító** csoport **korlátozott** Lookout MES konzolhozzáférés *(nem kötelező csoport)* . 
  Az Azure AD-hozzáférés több konfigurációs és regisztrációval kapcsolatos moduljához a Lookout-konzolon nem rendelkező felhasználókat tartalmazzák, ez nem kötelező felhasználói csoportot hoz létre. Ehelyett ezeket a felhasználók csak olvasási hozzáféréssel rendelkeznek a **biztonsági házirend** modul a Lookout konzolra. Felhasználók csak akkor nem kötelező ehhez a csoporthoz, vagy a szükséges tagjai *teljes hozzáférés* csoport, a Lookout konzolra való bejelentkezéshez.

 > [!TIP] 
 > Az engedélyekről további információt talál a Lookout-webhelyen, [ebben a cikkben](https://personal.support.lookout.com/hc/articles/114094105653).

### <a name="collect-information-from-azure-ad"></a>Az Azure AD-fájlokból gyűjt adatokat 

1. Jelentkezzen be a [az Azure portal](https://portal.azure.com) egy globális rendszergazdai fiókkal.

2. Lépjen a **Azure Active Directory** > **tulajdonságok** , és keresse meg a **címtár-azonosító**. Használja a *másolási* gombra kattintva másolja a címtár-azonosító, és mentse egy szövegfájlba.

   ![Az Azure AD tulajdonságok](./media/lookout-mtd-connector-integration/azure-ad-properties.png)  

3. Az Azure AD-Csoportazonosító követően keresse meg a fiókok hozzáférést biztosítani Azure Active Directory-felhasználók a Lookout-konzol használatával. Egy csoport van, a *teljes hozzáférés*, és a második csoportot, ehhez a *korlátozott hozzáférés* nem kötelező. Az első a *Objektumazonosító*, az egyes fiókok számára:  
   1. Lépjen a **Azure Active Directory** > **csoportok** megnyitásához a *csoportok – összes csoport* ablaktáblán.  

   2. Válassza ki a létrehozott csoport *teljes hozzáférés* megnyitásához a *áttekintése* ablaktáblán.  

   3. Használja a *másolási* gombra kattint, hogy az objektum azonosítóját, és mentse egy szövegfájlba.  

   4. Ismételje meg a folyamatot a *korlátozott hozzáférés* csoportban, ha az adott csoport használata.  

      ![Az Azure AD-csoport objektum azonosítója](./media/lookout-mtd-connector-integration/azure-ad-group-id.png)  

   Miután az információk gyűjtésére, forduljon a Lookout támogatási (e-mail: enterprisesupport@lookout.com). A lookout-támogatás a a elsődleges kapcsolattartóval együttműködve előkészíti az előfizetést, és a vállalati Lookout-fiókot létrehozni, az Ön által megadott információk.  

## <a name="configure-your-lookout-subscription"></a>A Lookout-előfizetés konfigurálása  
Miután a Lookout ügyfélszolgálata elkészítette a vállalati Lookout-fiókot, a Lookout támogatási egy e-mailt küld elsődleges a vállalat a bejelentkezési URL-cím mutató hivatkozást tartalmazó: https://aad.lookout.com/les?action=consent. 

### <a name="initial-sign-in"></a>Kezdeti bejelentkezési  
Az első jelentkezzen be a Lookout-konzolon MES használatával jeleníti meg egy hozzájárulást kérő lap (https://aad.lookout.com/les?action=consent). Csak jelentkezzen be az Azure AD globális rendszergazda és **elfogadás**. További bejelentkezési nem kéri a felhasználótól a szintű Azure AD-jogosultságot használni. 

 Egy hozzájárulást kérő lap jelenik meg. A regisztráció befejezéséhez válassza az **elfogad** lehetőséget. 
   ![Képernyőkép a először jelentkezzen be a Lookout-konzolon](./media/lookout-mtd-connector-integration/lookout_mtp_initial_login.png)

Fogadja el, és hozzájárul, amikor a program átirányítja a Lookout-konzolon.

Miután befejeződött a kezdeti bejelentkezési és a jóváhagyás, felhasználók, amelyek jelentkezhessen be https://aad.lookout.com rendszer átirányítja a MES konzol. Ha jóváhagyás még nem kapott, minden bejelentkezési kísérlet a helytelen bejelentkezési hiba eredményez.

### <a name="configure-the-intune-connector"></a>Az Intune-összekötő konfigurálása  
A következő eljárás azt feltételezi, hogy az Azure ad-ben a Lookout központi telepítés tesztelésekor a korábban már létrehozott egy felhasználói csoportot. Az ajánlott eljárás az, hogy a Lookout és az Intune rendszergazdák, hogy megismerkedjen a termékintegrációk egy kisebb csoportot használ első lépésként. Ismeri azokat, miután a regisztrációt kiterjesztheti újabb felhasználói csoportokra is.

1. Jelentkezzen be a [MES Lookout-konzolon](https://aad.lookout.com) , majd **rendszer** > **összekötők**, majd válassza ki **összekötő hozzáadása**.  Válassza ki **Intune**.

   ![A Lookout-konzolon az Intune-ban kapcsolóval az összekötők lapon képe](./media/lookout-mtd-connector-integration/lookout_mtp_setup-intune-connector.png)

2. Az a *a Microsoft Intune* ablaktáblán válassza **kapcsolatbeállítások** , és adja meg a **szívverés gyakorisága** percek alatt. 

   ![A kapcsolat beállítása lapról szívverés gyakorisága már konfigurálva van, képe](./media/lookout-mtd-connector-integration/lookout-mtp-connection-settings.png)

3. Válassza ki **Enrollment Management**, és a **a következő Azure AD biztonsági csoportok használatával azonosíthatja azokat az eszközöket, amelyek regisztrálva lesznek a Lookout for Work**, adja meg a *csoportnév*az Lookout, majd válassza ki az Azure AD-csoport **módosítások mentése**.

    ![képernyőkép az Intune-összekötő regisztrálási oldaláról](./media/lookout-mtd-connector-integration/lookout-mtp-enrollment.png)  

   **A csoportokkal kapcsolatos használhatja**:
   - Ajánlott eljárásként indítsa el az Azure AD biztonsági csoportot, amely tartalmazza a Lookout-integráció teszteléséhez kis számú.
   - A **csoportnév** nagybetűket, ahogy az a **tulajdonságok** a biztonsági csoport az Azure Portalon.  
   - A megadott csoportok **Enrollment Management** felhasználók, akiknek az eszközei regisztrálva lesznek a Lookoutban definiálásához. Amikor egy felhasználó tagja egy regisztrációs csoportnak, eszközeiket az Azure ad-ben is regisztrálható és aktiválható a Lookout MES használatával. Az első alkalommal a felhasználó megnyitja a *Lookout for Work* alkalmazást a támogatott eszközön kell adnia az aktiválást.

4. Válassza ki **Állapotszinkronizálás** és ellenőrizze, hogy mindkét *Eszközállapot* és *fenyegetés állapota* vannak beállítva, hogy **a**.  A Lookout és az Intune-integráció megfelelő működéséhez szükségesek.  

5. Válassza ki **hibakezelés**, adja meg az e-mail címet, amely a hibajelentéseket fogadó kell, és válassza ki **módosítások mentése**.
 
   ![képernyőkép az Intune-összekötő hibakezelési oldaláról](./media/lookout-mtd-connector-integration/lookout-mtp-connector-error-notifications.png)

6. Válassza ki **összekötő létrehozása** az összekötő konfigurálásának befejezéséhez. Később amikor már elégedett az eredménnyel, bővítheti regisztrációs további felhasználói csoportokra.

## <a name="configure-intune-to-use-lookout-as-a-mobile-threat-defense-provider"></a>Használja a Lookout Mobile Threat Defense-szolgáltatóként az Intune konfigurálása
Miután konfigurálta a Lookout MES, be kell állítania egy kapcsolatot a Lookout Intune-ban.  

1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

2. Lépjen a **eszközmegfelelőség** > **Mobile Threat Defense** válassza **Hozzáadás**.

3. Az a *hozzáadása összekötő* panelre, használja a legördülő menüből, és válassza **Lookout for Work**.  

4. Kattintson a **Létrehozás** gombra. Miután az összekötőt hoz létre a Lookout MES használatával, forduljon a *összekötő-beállítások* elérhetővé válnak.

5. Állítsa be **alkalmazás-szinkronizálás engedélyezése iOS-eszközök** való **a**. 

6. Válassza ki **mentése** konfigurálásának befejezéséhez.  Az Intune és a Lookout MES immár integrált, és készen áll a használatra.


## <a name="additional-settings-in-the-lookout-mes-console"></a>További beállítások a Lookout-konzolon MES használatával
Az alábbiakban további beállításokat konfigurálhat a MES Lookout-konzolon.  

### <a name="configure-enrollment-settings"></a>Regisztrációs beállítások konfigurálása
Válassza ki a MES használatával a Lookout konzolon **rendszer** > **regisztráció kezelése** > **regisztrációs beállítások**.  

- A **leválasztott állapot**, adja meg, hány nap elteltével egy csatlakoztatott eszközön van megjelölve, mert leválasztása.  

  A leválasztott eszközöket nem megfelelőnek tekinti a program, és az Intune-beli feltételes hozzáférésre vonatkozó szabályzatok alapján törli a munkahelyi alkalmazásokhoz való hozzáférésüket. 1 és 90 nap közötti időtartam adható meg.

  ![A rendszer a modul a lookout regisztrációs beállításai](./media/lookout-mtd-connector-integration/lookout-console-enrollment-settings.png)

### <a name="configure-email-notifications"></a>E-mail értesítések konfigurálása
E-mailes riasztásokhoz fenyegetések kapni, jelentkezzen be a [MES Lookout-konzolon](https://aad.lookout.com) a felhasználói fiókkal, amelyre értesítéseket szeretné kapni.  

- Lépjen a **beállítások** és adja meg az értesítéseket szeretne kapni a **ON**, majd **mentése** a módosításokat.  

- Ha már nem szeretne email értesítéseket kapni, állítsa be az értesítéseket **OFF** és mentse a módosításokat.

  ![Képernyőkép a beállítások lapról a felhasználói fiókkal](./media/lookout-mtd-connector-integration/lookout-mtp-email-notifications.png)



## <a name="configure-threat-classifications"></a>Veszélyforrás-besorolásaiban konfigurálása  
A lookout Mobile Endpoint Securityhez osztályokba sorolja a különféle fenyegetési típusokat. A Lookout veszélyforrás-besorolásaiban tartoznak a fenyegetésekhez alapértelmezett kockázati szintek rendelkezik. A kockázati szintek a vállalat igényeinek bármikor módosítható.

További információ a szolgáltatói veszélyforrás-besorolásaiban, és hogyan kezelheti a hozzájuk társított kockázati szintek: [a Lookout veszélyforrások elleni referencia](https://enterprise.support.lookout.com/hc/articles/360011812974).

>[!IMPORTANT]
> Kockázati szintek fontos elemét alkotják a Mobile Endpoint Securityhez, mert az Intune-integráció eszközmegfelelőség futásidőben kockázati szintek alapján számítja ki.  
> 
> Az Intune-rendszergazda állítja be a szabályzatban, hogy egy eszköz akkor nem megfelelő, ha egy olyan aktív fenyegetés található rajta, amelynek a szintje: **Magas**, **Közepes** vagy **Alacsony**. A Lookout Mobile Endpoint Securityhez veszélyforrás-besorolási szabályzata közvetlen lezajló eszközmegfelelőségi számításnak az Intune-ban.  

## <a name="monitor-enrollment"></a>A regisztráció figyelése
Telepítés befejezése után a Lookout Mobile Endpoint Securityhez elkezdi lekérdezni az Azure AD-eszközökhöz, amelyek megfelelnek a megadott regisztrációs csoportoknak.  A regisztrált eszközökre vonatkozó információkat talál **eszközök** a MES Lookout-konzolon.  
- Az eszközök kezdeti állapota *függőben lévő*.  
- Az eszköz állapota után frissíti a *Lookout for Work* alkalmazás van telepítve, megnyílik, és az eszközön aktiválni.

A részleteket az első a *Lookout for Work* egy eszközön üzembe helyezett alkalmazás megtekintéséhez [Lookout for work alkalmazások hozzáadása az Intune-nal](mtd-apps-ios-app-configuration-policy-add-assign.md).

## <a name="next-steps"></a>További lépések

[Lookout-alkalmazások beállítása](mtd-apps-ios-app-configuration-policy-add-assign.md)

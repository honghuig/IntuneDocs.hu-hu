---
title: Webhely-hozzáférés kezelése a Microsoft Edge Microsoft Intune-nal
titleSuffix: ''
description: A Microsoft Edge az Intune alkalmazásvédelmi szabályzatok használatával biztosíthatja a vállalati webhelyek mindig érhetők el a védelmi szolgáltatás helyen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3fb2f050-ec94-42ab-be05-c3d4101148bb
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 50574a2d3dc4ba5731b1a90f563ddd1a08e7f833
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67529635"
---
# <a name="manage-web-access-using-microsoft-edge-with-microsoft-intune"></a>Webhely-hozzáférés kezelése a Microsoft Edge Microsoft Intune-nal

Az Intune alkalmazásvédelmi szabályzatokat használó alkalmazásokat a Microsoft Edge biztosíthatja a vállalati webhelyek mindig érhetők el a védelmi szolgáltatás helyen. A következő Microsoft Edge az Intune szabályzatai által engedélyezett vállalati funkciók érhetők el. Ezek a vállalati szolgáltatások a következők:

1. **Kettős-Identity** -felhasználók hozzáadhatnak, mind a munkahelyi fiókot, valamint egy személyes fiók, történő tallózásának tartalombeállításait. Nincs teljes elválasztását, amely hasonló az architektúra és a felhasználói felület az Office 365 és az Outlook két identitások között. Intune-rendszergazdák a munkahelyi fiók belül védett böngészési élményt a kívánt házirendeket állíthat be lesz.
2. **Az Intune app protection házirend-integráció** – mivel a Microsoft Edge integrálva van az Intune SDK-val, alkalmazásvédelmi szabályzatok adatvesztés ellen biztosítása érdekében célba. Ezek közé tartozik a kivágási, másolási, irányítását és beillesztési műveleteket, megakadályozhatja a képernyő rögzíti, és annak biztosítása, hogy a felhasználó által kiválasztott hivatkozások csak nyissa meg a felügyelt alkalmazások.
3. **Az Azure Application Proxy-integráció** – szabályozhatja a hozzáférést az SaaS-alkalmazásokhoz és a web apps szolgáltatásban, így biztosítja, hogy csak a böngészőalapú alkalmazások futtatása a biztonságos Microsoft Edge böngészőben a végfelhasználók számára a vállalati hálózathoz való csatlakozáshoz, vagy az internetről kapcsolódnak-e .
4. **Alkalmazás konfigurációja** – erősítse meg a szervezet biztonsági állapotát, és a könnyű használat szolgáltatások konfigurálása a végfelhasználók számára az alkalmazás-konfigurációs beállítások is élvezheti. Megadhatja például a könyvjelzők, a kezdőlap helyi, engedélyezett/letiltott webhelyek, Azure Application Proxy és több.
A Microsoft Intune alkalmazásvédelmi szabályzatokat a Microsoft Edge segítenek a szervezet adatok és erőforrások védelmét. Ezek a házirendek használatával a Microsoft Edge biztosítja, hogy a vállalati erőforrások védelme nem csak a natív módon telepített alkalmazások belül is a webböngészőn keresztül elérhető.

## <a name="getting-started"></a>Első lépések

Ön és a végfelhasználók számára letölthető a Microsoft Edge használható nyilvános alkalmazás-áruházakból a szervezet. Az operációs rendszerre vonatkozó követelmények a böngésző szabályzataival kapcsolatban:
- Android 4 és újabb verziók, vagy
- iOS 8.0 és újabb verziók

## <a name="application-protection-policies-for-microsoft-edge"></a>Alkalmazásvédelmi szabályzatokat a Microsoft Edge

Mivel a Microsoft Edge-nal való integrálása az Intune SDK alkalmazhat alkalmazásvédelmi szabályzatokat, ideértve azokat:
- Kivágás, másolás és beillesztés műveletek korlátozása.
- Képernyőmentés megakadályozása.
- Annak biztosítása, hogy a vállalati hivatkozásokat csak a felügyelt alkalmazásokon és böngészőkön belül lehessen megnyitni.

További információkért lásd:, Mik azok az alkalmazásvédelmi szabályzatok?
Ezek a beállítások az alábbiakra alkalmazhatók:
- Az Intune-ban regisztrált eszközök
- Más MDM-termékben regisztrált eszközök
- Nem felügyelt eszközök

Ha az Intune-szabályzat nem vonatkozik a Microsoft Edge, felhasználók nem használhatja más Intune által felügyelt alkalmazások, például az Office-alkalmazások adatok eléréséhez. 

## <a name="conditional-access-for-microsoft-edge"></a>Feltételes hozzáférés a Microsoft Edge-ben

Kihasználhatja az Azure AD feltételes hozzáférés a felhasználók férhetnek hozzá a vállalati tartalomhoz csak a Microsoft Edge keresztül átirányítani. Ez korlátozná a mobilböngészők hozzáférését az Azure AD-hez csatlakozó webalkalmazásokhoz, házirend által védett Microsoft Edge, és ez például a Safarit vagy a Chrome más nem védett böngészőkkel történő hozzáférés le fog állni. Feltételes hozzáférés az Azure erőforrásokhoz, mint az Exchange online-hoz és a SharePoint online-hoz, a Microsoft 365 felügyeleti központot és még akkor is, amelyekhez külső felhasználók számára keresztül a helyszíni helyek alkalmazhatók a [Azure AD-alkalmazásproxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started).

Korlátozza az Azure AD-hez csatlakozó webalkalmazásokhoz használata a Microsoft Edge iOS és Android rendszeren, kövesse az alábbi lépéseket:
1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Válassza ki az Intune-ban csomópont alatt **feltételes hozzáférési** > **új szabályzat**.
3. Ezután válassza a panel **Hozzáférés-szabályozási** szakaszában a **Hozzáférés** lehetőséget.
4. Kattintson a **Jóváhagyott ügyfélalkalmazás megkövetelése** lehetőségre.
5. A **Hozzáférés** panelen kattintson a **Kiválasztás** elemre. Ezt a szabályzatot hozzá kell rendelni azokhoz a felhőalkalmazásokhoz, amelyek esetében azt szeretné, hogy csak az Intune Managed Browser alkalmazásból legyenek elérhetők.

    ![Feltételes hozzáférési házirend - támogatás](./media/manage-microsoft-edge/manage-microsoft-edge-01.png)

6. A hozzárendelések szakaszban feltételek kiválasztása > ügyfélalkalmazások. Az ügyfél panelen jelenik meg.
7. A szabályzat adott ügyfélalkalmazásokra való konfigurálás alatt kattintson az Igen gombra.
8. Győződjön meg arról, hogy böngészőben van-e kiválasztva ügyfélalkalmazásként.

    ![Feltételes hozzáférési szabályzat – ügyfélalkalmazások kiválasztása](./media/manage-microsoft-edge/manage-microsoft-edge-02.png)

    > [!NOTE]
    > Ha korlátozni szeretné, hogy mely natív (nem böngészőbeli) alkalmazások férhetnek hozzá ezekhez a felhőalkalmazásokhoz, válassza a **Mobilalkalmazások és asztali ügyfelek** lehetőséget.

9. A **Hozzárendelések** szakaszban válassza a **Felhasználók és csoportok** lehetőséget, majd válassza ki azokat a felhasználókat és csoportokat, akikhez hozzá szeretné rendelni ezt a szabályzatot.

    > [!NOTE]
    > Az alkalmazáskonfigurációs szabályzatok fogadása érdekében a felhasználókat Intune App Protection-szabályzattal kell megcélozni. További információ az Intune App Protection szabályzatainak létrehozásáról: [Mik azok az alkalmazásvédelmi szabályzatok?](app-protection-policy.md)

10. A szabályzat védelme alá tartozó alkalmazások megadásához a **Hozzárendelések** szakaszban válassza a **Felhőalkalmazások** lehetőséget.

Miután konfigurálta a fenti szabályzatot, a felhasználókat az Azure AD-hez csatlakozó webalkalmazásokhoz, ez a szabályzat védelme alá eléréséhez használható a Microsoft Edge kényszeríti ki. Felhasználók megpróbálnak egy nem felügyelt böngésző használata ebben a forgatókönyvben, azok megjelenik egy üzenet, hogy a Microsoft Edge kell használniuk.

> [!TIP]
> A feltételes hozzáférés az Azure Active Directory (Azure AD) technológiája. A feltételes hozzáférés csomópontot az Intune-ból elért ugyanazon a csomóponton megegyezik az Azure ad-ből érhető el.

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>Egyszeri bejelentkezés az Azure AD-hez kapcsolódó webalkalmazásokba a szabályzat által védett böngészőkben

A Microsoft Edge az iOS és Android rendszerhez is igénybe vehet SSO-t minden webalkalmazáshoz (SaaS és helyszíni), amely az Azure AD-hez csatlakozó. Egyszeri bejelentkezés lehetővé teszi, hogy a felhasználók hozzáférhessenek az Azure AD-hez csatlakozó webalkalmazásokhoz keresztül a Microsoft Edge írja be újra a hitelesítő adatok nélkül.

Egyszeri bejelentkezés szükséges regisztrálni az iOS-eszközök a Microsoft Authenticator alkalmazást, vagy az Intune vállalati portál Android-eszközét. Ha a felhasználók a hitelesítő alkalmazás vagy az Intune vállalati portál, kérni fogja regisztrálni az eszközt egy Azure AD-hez csatlakozó webalkalmazást egy házirend által védett böngészőben, ha eszközük nem már regisztrált még ha. Után az eszköz regisztrálva van a felhasználó fiókját az Intune által felügyelt, a fiók már az Azure AD-hez csatlakozó webalkalmazások esetében SSO.

> [!NOTE]
> Az eszközregisztráció egy egyszerű bejelentkezés az Azure AD szolgáltatással. Nem igényel teljes eszközregisztrációt, és nem ad az eszközre vonatkozó további jogosultságokat az informatikai részlegnek.

## <a name="create-a-protected-browser-app-configuration"></a>Egy védett böngésző alkalmazáskonfigurációjának létrehozása

Az alkalmazáskonfigurációk a alkalmazni, a felhasználó a böngésző által védett, vagy egy másik alkalmazást az eszközön már felügyelni [az Intune alkalmazásvédelmi szabályzatának](app-protection-policy.md).

A következő lépések segítségével hozzon létre egy védett browser alkalmazás konfigurációjának:

1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Válassza ki **ügyfélalkalmazás** > **alkalmazáskonfigurációs szabályzatok** > **Hozzáadás**.
3. A **Konfigurációs szabályzat hozzáadása** panelen az alkalmazáskonfigurációs beállításokhoz írja be a **Nevet** és a **Leírást** (ez utóbbi nem kötelező).
4. Az **Eszközregisztráció** típusaként válassza a **Felügyelt alkalmazások** lehetőséget.
5. Válassza a **Kötelező alkalmazás kiválasztása** elemet, majd a **Célalkalmazások** panelen válassza a **Managed Browser** vagy a **Microsoft Edge** lehetőséget iOS-hez, Androidhoz vagy igény szerint mindkettőhöz.
6. Az **OK** kiválasztásával visszatérhet a **Konfigurációs szabályzat hozzáadása** panelre.
7. Kattintson a **Konfigurációs beállítások** elemre. Az a **konfigurációs** panelen kulcs-érték párok definiálásával konfigurációk a Microsoft Edge, határozza meg. A jelen cikk későbbi részeiben további információt talál a definiálható kulcs-érték párokról.

    > [!NOTE]
    > A Microsoft Edge ugyanazokat a kulcs-érték párokat használja, mint a Managed Browser. 

8. Amikor elkészült, kattintson az **OK**gombra.
9. A **Konfigurációs szabályzat hozzáadása** panelen válassza a **Hozzáadás** lehetőséget.<br>
    Az új konfiguráció létrehozása és jelenik meg a **Alkalmazáskonfiguráció** panelen.

## <a name="assign-the-configuration-settings-you-created"></a>A létrehozott konfigurációs beállítások hozzárendelése 

A beállításokat Azure AD-beli felhasználói csoportokhoz lehet hozzárendelni. Ha az illető felhasználó rendelkezik a célzott védett böngésző telepített példányával, akkor az alkalmazás felügyelete a megadott beállításokkal történik.

1. Az Intune mobilalkalmazás-kezelési irányítópult **Ügyfélalkalmazások** paneljén válassza az **Alkalmazáskonfigurációs szabályzatok** lehetőséget.
2. A listából válassza ki a hozzárendelni kívánt alkalmazáskonfigurációt.
3. Válassza ki a következő panelen a **Hozzárendelések** elemet.
4. A **Hozzárendelések** panelen válassza ki azt az Azure AD-csoportot, amelyhez az alkalmazáskonfigurációt hozzá szeretné rendelni, majd válassza az **OK** elemet.

## <a name="how-to-configure-application-proxy-settings-for-protected-browsers"></a>Alkalmazásproxy-beállítások konfigurálása a védett böngészőkhöz

A Microsoft Edge és [Azure AD-alkalmazásproxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) együtt használható a mobileszközükön az intranetes helyek való hozzáférés engedélyezése a felhasználók számára. 

Néhány példa a forgatókönyveket, AD-alkalmazásproxy engedélyezése az alábbiak: 

- Egy felhasználó az Outlook mobilalkalmazást az, amely az Intune által védett használ. Majd kattintson egy e-mailben egy intranetes webhelyre mutató hivatkozást, és a Microsoft Edge felismeri, hogy az adott intranetes webhely az alkalmazásproxyn keresztül a felhasználó számára elérhető-e. A felhasználó automatikusan továbbít a Proxy, minden lehetséges többtényezős hitelesítés és feltételes hozzáférési érhesse el az intranetes webhelyek hitelesítésére. A felhasználók átállíthatják most még a mobileszközeiket a belső webhelyek eléréséhez, és az Outlook-beli hivatkozás megfelelően működik-e.
- A felhasználó megnyitja a Microsoft Edge az iOS és Android rendszerű eszközökön. Ha a Microsoft Edge védelme az Intune-nal, és az alkalmazásproxy engedélyezve van, a felhasználó kaphatnak egy intranetes webhelyet használja őket belső URL-cím használatával. A Microsoft Edge felismeri, hogy az adott intranetes webhely az alkalmazásproxyn keresztül a felhasználó megnyílt, és a felhasználó automatikusan áthalad az alkalmazásproxy érhesse el az intranetes webhelyek hitelesítésére. 

### <a name="before-you-start"></a>Előkészületek

- Állítsa be a belső alkalmazásokat az Azure AD alkalmazásproxyban.
    - Az Alkalmazásproxy konfigurálásáról és az alkalmazások közzétételéről a [telepítési dokumentációban](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy) olvashat.
- Rendelkeznie kell a Microsoft Edge alkalmazás [az Intune alkalmazásvédelmi szabályzatának](app-protection-policy.md) hozzárendelve.

> [!NOTE]
> Az Alkalmazásproxy frissített átirányítási adatainak érvénybe lépése a Managed Browserben és a Microsoft Edge-ben akár 24 órát is igénybe vehet.

#### <a name="step-1-enable-automatic-redirection-to-a-protected-browser-from-outlook"></a>1\. lépés: Automatikus átirányítás engedélyezése az Outlookból egy védett böngészőhöz
Az Outlook kell konfigurálni egy alkalmazásvédelmi szabályzatot, amely lehetővé teszi, hogy a beállítás **megosztás webes tartalom házirenddel felügyelt böngészők**.

![Alkalmazásvédelmi szabályzat - megosztás webes tartalom házirenddel felügyelt böngészőket](./media/manage-microsoft-edge/manage-microsoft-edge-03.png)

#### <a name="step-2-set-the-app-configuration-setting-to-enable-app-proxy"></a>2\. lépés: Állítsa be az alkalmazás a konfigurációs beállítás alkalmazásproxy engedélyezése
A Microsoft Edge-cél az alábbi kulcs-érték pár, a Microsoft Edge-alkalmazásproxy engedélyezése:

|    Kulcs    |    Value    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.AppProxyRedirection    |    true    |

Hogyan Microsoft Edge és az Azure AD-alkalmazásproxy használható területtel helyszíni webalkalmazásokhoz való zökkenőmentes (és védett) hozzáférés kapcsolatos további információkért lásd: az Enterprise Mobility + Security blogbejegyzésben [együtt jobb: Az Intune és az Azure Active Directory együtt teszi jobbá a felhasználói hozzáférést](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access) című blogbejegyzésében találhat. Az ebben a blogbejegyzésben hivatkozások az Intune Managed Browser, de a tartalom is vonatkozik a Microsoft Edge.

## <a name="how-to-configure-a-homepage-shortcut-for-microsoft-edge"></a>A kezdőlap helyi konfigurálása a Microsoft Edge

Ezzel a beállítással konfigurálhatja a kezdőlap parancsikont a Microsoft Edge.  A kezdőlap helyi konfigurálása a Microsoft Edge-ben egy új lap megnyitásakor az első ikon a keresősáv alatt fog megjelenni. A felhasználó nem fogja tudni szerkesztheti vagy törölheti a helyi a felügyelt környezetben. A kezdőlap parancsikonja megjeleníti a szervezet nevét a megkülönböztethetőség érdekében. 

Használja az alábbi kulcs-érték pár kezdőlap parancsikon konfigurálása:

|    Kulcs    |    Érték    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.homepage   |    Adjon meg egy érvényes URL-címet. A helytelen URL-címek biztonsági intézkedésként le vannak tiltva.<br>**Példa:** `<https://www.bing.com`>
    |

## <a name="how-to-configure-managed-bookmarks-for-microsoft-edge"></a>Felügyelt könyvjelzőinek beállítása a Microsoft Edge

A könnyű hozzáférést konfigurálhatja úgy, hogy szeretné a felhasználókat, hogy elérhető a Microsoft Edge használatakor a könyvjelzők. Az alábbiakban néhány részletei:

- Ezek a könyvjelzők az Microsoft Edge vállalati mód használata csak fog megjelenni a felhasználók számára. 
- Ezeket a könyvjelzőket nem törölhető és nem módosíthatják a felhasználók.
- Ezek a könyvjelzők a lista tetején jelennek meg. A felhasználók által készített könyvjelzők ezek alá kerülnek.
- Ha engedélyezte az alkalmazásproxy-átirányítást, akkor alkalmazásproxyval rendelkező webalkalmazásokat akár belső, akár külső URL-cím használatával is hozzáadhat.

Felügyelt könyvjelzők konfigurálásához kövesse az alábbi kulcs-érték párt:

|    Kulcs    |    Value    |
|---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.bookmarks    |    Ez a konfiguráció értéke egy könyvjelzőlista. Minden könyvjelző címből, és a könyvjelző URL-cím áll. Külön, a címet és az URL-CÍMÉT a `|` karakter.      **Példa:**<br>`Microsoft Bing|https://www.bing.com`<br>Több könyvjelző megadásakor külön minden párból az karakterpárt `||`.<p>**Példa:**<br>`Microsoft Bing|https://www.bing.com||Contoso|https://www.contoso.com`    |

## <a name="how-to-display-myapps-within-microsoft-edge-bookmarks"></a>A Microsoft Edge-könyvjelzők belül MyApps megjelenítése

Alapértelmezés szerint a felhasználók számára megjelenik a MyApps helyek konfigurált őket a Microsoft Edge-könyvjelzők belül egy adott mappában. A mappa neve a szervezet nevét.

|    Kulcs    |    Érték    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.MyApps    |    **Igaz** MyApps bemutatja a Microsoft Edge-könyvjelzők belül.<p>**FALSE (hamis)** elrejti a MyApps Microsoft Edge belül.    |

## <a name="how-to-specify-allowed-or-blocked-sites-list-for-microsoft-edge"></a>A Microsoft Edge engedélyezett vagy tiltott helyek listájának megadása
Alkalmazáskonfiguráció segítségével megadhatja a felhasználók férhetnek hozzá a munkahelyi profil használatakor webhelyeket. Engedélyezési lista használatakor a felhasználók csak lesz érhetik el a kifejezetten felsorolt helyek. Ha egy tiltólista használja, a felhasználók érhessék el az összes hely a helyek, explicit módon letiltotta lesz. Érdemes csak bevezetése vagy egy engedélyezett vagy letiltási listát, nem mindkettőt. Ha mindkét célozzák meg az eszközön, az engedélyezett listára lesz figyelembe véve.  

Használhatja az alábbi kulcs-érték párok konfigurálása a Microsoft Edge vagy az engedélyezett vagy tiltott helyek listája. Érvényes URL-formátumok kapcsolatos további információért olvassa tovább. 

|    Kulcs    |    Value    |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    A következő lehetőségek közül választhat:<p>1. Engedélyezett URL-címek megadása (csak ezek az URL-címek engedélyezettek, más webhelyek nem érhetők el):<br>`com.microsoft.intune.mam.managedbrowser.AllowListURLs`<p>2. Tiltott URL-címek megadása (minden más webhely elérhető lesz):<br>`com.microsoft.intune.mam.managedbrowser.BlockListURLs`    |    A kulcs megfelelő értéke egy URL-címlista. A kívánt engedélyezheti vagy letilthatja a egyetlen értékként, a függőleges vonallal elválasztott URL-címeket `|` karakter.<br>**Példák:**<br>`URL1|URL2|URL3`<br>`http://.contoso.com/|https://.bing.com/|https://expenses.contoso.com`  |

### <a name="url-formats-for-allowed-and-blocked-site-list"></a>Az URL-formátumok engedélyezett, és a Tiltott helyek listája 
Különböző URL-formátumok használatával hozhat létre az engedélyezett/letiltott webhelyek listája. Az alábbi táblázat részletezi ezeket a mintákat. Néhány megjegyzés a Kezdés előtt: 
- Az URL-címek listába történő bevitelekor ellenőrizze, hogy az URL-címet a **http** vagy a **https** előtaggal adta-e meg.
- Használható helyettesítő karakter és szimbólum (\*) a megengedett minták alábbi listájának szabályai szerint.
- Helyettesítő karakter csak meg tudja egy teljes compoment állomásnév (elválasztott) vagy az elérési út (a perjelet elválasztva) teljes részei. Ha például `http://*contoso.com` van **nem** támogatott.
- A címben portszámokat is megadhat. Ha nem ad meg portszámot, a rendszer a következő értékeket használja:
    - HTTP – 80-as port
    - HTTPS – 443-as port
- A portszám helyettesítő karakterek használatával **nem** támogatott. Például a `http://www.contoso.com:*` és a `http://www.contoso.com:*/` nem támogatottak. 

    |    URL    |    Részletek    |    Egyezik    |    Nem egyezik    |
    |-------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
    |    `http://www.contoso.com`    |    Egyetlen lapnak felel meg    |    `www.contoso.com`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`contoso.com/`    |
    |    `http://contoso.com`    |    Egyetlen lapnak felel meg    |    `contoso.com/`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com`    |
    |    `http://www.contoso.com/&#42;`   |    Az összes `www.contoso.com` karakterlánccal kezdődő URL-cím    |    `www.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com/videos/tvshows`    |    `host.contoso.com`<br>`host.contoso.com/images`    |
    |    `http://*.contoso.com/*`    |    Összes altartománya `contoso.com`    |    `developer.contoso.com/resources`<br>`news.contoso.com/images`<br>`news.contoso.com/videos`    |    `contoso.host.com`    |
    |    `http://www.contoso.com/images`    |    Egyetlen mappa    |    `www.contoso.com/images`    |    `www.contoso.com/images/dogs`    |
    |    `http://www.contoso.com:80`    |    Egyetlen lap, megegyezik a portszám használatával    |    http://www.contoso.com:80    |         |
    |    `https://www.contoso.com`    |    Egyetlen biztonságos lap    |    `https://www.contoso.com`    |    `http://www.contoso.com`    |
    |    `http://www.contoso.com/images/*`    |    Egyetlen mappa és annak összes almappája    |    `www.contoso.com/images/dogs`<br>`www.contoso.com/images/cats`    |    `www.contoso.com/videos`    |
  
- Az alábbi példák nem engedélyezett beviteleket szemléltetnek:
    - `*.com`
    - `*.contoso/*`
    - `www.contoso.com/*images`
    - `www.contoso.com/*images*pigs`
    - `www.contoso.com/page*`
    - IP-címek
    - `https://*`
    - `http://*`
    - `https://*contoso.com`
    - `http://www.contoso.com:*`
    - `http://www.contoso.com: /*`
  
## <a name="defining-behavior-when-users-try-to-access-a-blocked-site"></a>Viselkedés meghatározása, amikor a felhasználó megpróbál hozzáférni egy letiltott hely

A kettős-identity-modell beépítve a Microsoft Edge egy olyan rugalmasabb élmény a végfelhasználók számára, amely nem volt lehetséges a az Intune Managed Browser számára engedélyezheti. Amikor a felhasználó eléri a Microsoft Edge-ben egy letiltott hely, akkor a hivatkozás megnyitásához a saját személyes környezet helyett a munkahelyi környezetben, amely lehetővé teszi, hogy maradjon a védett, miközben gondoskodik a vállalati erőforrások biztonságos is kérni. Például ha egy felhasználó egy hivatkozást küld az Outlook keresztül hír, fogják tudni megnyitni a hivatkozást a környezetükben személyes vagy a munkahelyi környezetben, amely nem engedélyezi a hírek webhelyek helyett egy InPrivate-lapon. Alapértelmezés szerint az átmenetek engedélyezettek.

Használja az alábbi kulcs-érték pár konfigurálása, ha az enyhe átmenetek engedélyezettek:

|    Kulcs    |    Value    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock`    |    **Igaz** lehetővé teszi, hogy a Microsoft Edge átmenet felhasználók számára a személyes környezet, nyissa meg a letiltott webhelyek<p>**Blokk** megakadályozza, hogy a Microsoft Edge transitioning felhasználókat, és a felhasználók egyszerűen megjelenik egy üzenet arról, hogy az elérni kívánt webhely le van tiltva.    |

## <a name="directing-users-to-microsoft-edge-instead-of-the-intune-managed-browser"></a>Irányítja a felhasználókat a Microsoft Edge helyett az Intune Managed Browser 

Az Intune Managed Browser és a Microsoft Edge most is a házirend által védett böngészők is használható. Győződjön meg arról, hogy a felhasználók vannak irányítja a megfelelő browser alkalmazás használatához, jelölje ki az Intune által felügyelt alkalmazások (pl. az Outlook, OneDrive és SharePoint) az alábbi konfigurációs beállítás az összes:

|    Kulcs    |    Value    |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.useEdge`    |    Az érték `true` átirányítja a felhasználókat, hogy töltse le és használja a Microsoft Edge.<br>Az érték `false` lehetővé teszi a felhasználók az Intune Managed Browser használatára.    |

Ha az alkalmazás konfigurációs érték **nem** állítja, az alábbi logikával határozza meg böngésző használható vállalati hivatkozások megnyitásához.

Androidon:
- Az Intune Managed Browser fog elindulni, ha egy felhasználó az Intune Managed Browser és a Microsoft Edge az eszköz letöltése. 
- A Microsoft Edge megnyílik, ha csak a Microsoft Edge letöltődik az eszközön, és az Intune-szabályzat vonatkozik.
- A felügyelt böngészőben megnyílik, ha csak a Managed Browser az eszközön, és az Intune-szabályzat vonatkozik.

Az iOS rendszeren, ha az alkalmazásokban integrálva van az Intune SDK for iOS 9.0.9+ verziója:
- Az Intune Managed Browser fog elindulni, ha a Managed Browser és a Microsoft Edge az eszközön.  
- A Microsoft Edge fog elindulni, ha csak a Microsoft Edge az eszközön, és az Intune-szabályzat vonatkozik.
- Felügyelt böngésző, ha csak a Managed Browser az eszközön, és az Intune-szabályzat vonatkozik.

## <a name="using-microsoft-edge-on-ios-to-access-managed-app-logs"></a>A Microsoft Edge használatával iOS rendszeren a felügyelt alkalmazások naplóinak elérése 

A Microsoft Edge IOS rendszerű eszközén telepítve van a végfelhasználók megtekinthetik a minden felügyeleti állapotát a Microsoft közzétett alkalmazást. Elküldhetik a naplófájlokat a felügyelt iOS-eszköz hibaelhárítása céljából.
1. Nyissa meg a Microsoft Edge az iOS-eszközön.
2. A címsorba gépelje be a következőt: `about:intunehelp` 
3. Hibaelhárítási módban elindul a Microsoft Edge belül.

Az alkalmazásnaplókban tárolt beállítások listáját az [Alkalmazásvédelmi naplók áttekintése a Managed Browserben](app-protection-policy-settings-log.md) című témakörben találja.

Naplók megtekintése az Android-eszközökön, olvassa el [naplók elküldése a rendszergazdának e-mailben](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). 

## <a name="security-and-privacy-for-microsoft-edge"></a>Biztonság és adatvédelem a Microsoft Edge

A Microsoft Edge további biztonsági és adatvédelmi szempontjai:

- Microsoft Edge nincs szükség beállításokat, amelyeket a felhasználók saját eszközeiken, a natív böngészőben meg, mert a Microsoft Edge férhetnek hozzá ezekhez a beállításokhoz.
- Ha a beállítás **egyszerű PIN-kód megkövetelése a hozzáféréshez** vagy **vállalati hitelesítő adatok megkövetelése a hozzáféréshez** az alkalmazás a Microsoft Edge hozzárendelt alkalmazásvédelmi szabályzatban, és egy felhasználó a Súgó hivatkozásra lehetőséget választja a hitelesítés lap, bármely internetes webhelyet, függetlenül attól, hogy azok lettek adva a szabályzat blokklistájához megnyithassák.
- A Microsoft Edge képes blokkolni a hozzáférést a webhelyekhez, csak akkor, ha azokat közvetlenül érik el. Nem blokkolja a hozzáférést, ha a felhasználó köztes szolgáltatások (például egy fordítási szolgáltatás) használatával éri el a webhelyet.
- Hitelesítés engedélyezése, és elérheti az Intune-dokumentáció * **. microsoft.com** mentesül az engedélyezési és blokkolási beállítások. És mindig engedélyezve van.
Kapcsolja ki a Microsoft használati adatokat automatikusan névtelen adatokat gyűjt a teljesítmény és a Managed Browser számára a Microsoft termék-és használatáról. A felhasználók kikapcsolhatják az adatgyűjtést az eszköz **Használati adatok** beállításával. Nem tudja befolyásolni ezen adatok gyűjtését. Az iOS-eszközökön nem nyithatók meg azok a felhasználók által felkeresett webhelyek, amelyek lejárt vagy nem megbízható tanúsítvánnyal rendelkeznek.

## <a name="next-steps"></a>További lépések

- [Mik azok az alkalmazásvédelmi szabályzatok?](app-protection-policy.md) 

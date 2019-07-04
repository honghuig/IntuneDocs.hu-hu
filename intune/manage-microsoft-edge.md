---
title: Webes hozzáférés felügyelete a Microsoft Edge Microsoft Intune-nal való használatával
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
ms.openlocfilehash: b267e1c59ab59737b58b73054b90b0f8e026e959
ms.sourcegitcommit: cb4e71cd48311ea693001979ee59f621237a6e6f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/03/2019
ms.locfileid: "67558119"
---
# <a name="manage-web-access-by-using-microsoft-edge-with-microsoft-intune"></a>Webes hozzáférés felügyelete a Microsoft Edge Microsoft Intune-nal való használatával

Győződjön meg arról, hogy a vállalati webhelyek mindig elérhető helyen védelmi funkciók az Intune alkalmazásvédelmi szabályzatokat használó alkalmazásokat a Microsoft Edge segítségével. A következő Microsoft Edge az Intune szabályzatai által engedélyezett vállalati funkciók érhetők el:

- **Dual-Identity.** A felhasználók hozzáadhatnak egy munkahelyi fiókot, valamint egy személyes fiók, történő tallózásának tartalombeállításait. Nincs teljes elválasztását, amely hasonló az architektúra és a felhasználói felület az Office 365 és az Outlook két identitások között. Intune-rendszergazdák állíthatja be a kívánt házirendeket, a munkahelyi fiók belül védett böngészési élményt.
- **Az Intune app protection házirend-integráció.** A Microsoft Edge az Intune SDK integrálva van, mert az alkalmazásvédelmi szabályzatok adatvesztés elleni védelem érdekében célba. Ezek a képességek közé tartozik az ellenőrző kivágási, másolási és beillesztési, képernyőfelvételek, és annak biztosítása, hogy a felhasználó által kiválasztott hivatkozások csak nyissa meg a felügyelt alkalmazások.
- **Az Azure Application Proxy-integráció.** Ki férhet hozzá szoftver (SaaS) szolgáltatottszoftver-alkalmazásokat, és webes alkalmazásokat. Ezzel biztosíthatja, hogy a böngészőben megjelenő alkalmazásokat csak futtassa a biztonságos Microsoft Edge böngészőben a végfelhasználók számára a vállalati hálózathoz való csatlakozáshoz, vagy az internetről kapcsolódnak-e.
- **Alkalmazás konfigurációja.** Alkalmazás-konfigurációs beállítások segítségével erősítse a szervezet biztonsági állapotát, és konfigurálja a szolgáltatások egyszerű használatára a végfelhasználók számára. Megadhatja például a könyvjelzők, a kezdőlap helyi, engedélyezett vagy tiltott webhelyek és Azure Active Directory (Azure AD) alkalmazásproxy.

A Microsoft Intune alkalmazásvédelmi szabályzatokat a Microsoft Edge segítenek a szervezet adatok és erőforrások védelmét. Ezek a házirendek használatával a Microsoft Edge biztosítja, hogy a vállalati erőforrások védelme nem csak a natív módon telepített alkalmazások belül is a webböngészőn keresztül elérhető.

## <a name="getting-started"></a>Első lépések

Ön és a végfelhasználók számára letölthető a Microsoft Edge használható nyilvános alkalmazás-áruházakból a szervezet. Operációs rendszer által támasztott követelmények a felügyeltböngésző-szabályzatok a következő lehetőségek közül:
- Android 4 és újabb verziók
- iOS 8.0 és újabb verziók

## <a name="application-protection-policies-for-microsoft-edge"></a>Alkalmazásvédelmi szabályzatokat a Microsoft Edge

Microsoft Edge az Intune SDK integrálva van, mert azokat az alkalmazásvédelmi szabályzatokat is alkalmazhat.

Ezek a beállítások az alábbiakra alkalmazhatók:
- Az Intune-ban regisztrált eszközökön.
- Egy másik mobileszköz kezelése termékben regisztrált eszközök.
- Nem felügyelt eszközökről.

Ha az Intune-szabályzat nem vonatkozik a Microsoft Edge, felhasználók nem használhatja más Intune által felügyelt alkalmazások, például az Office-alkalmazások adatok eléréséhez. 

## <a name="conditional-access-for-microsoft-edge"></a>Feltételes hozzáférés a Microsoft Edge-ben

Azure AD feltételes hozzáférés segítségével a felhasználók férhetnek hozzá a vállalati tartalomhoz csak a Microsoft Edge keresztül átirányítani. Ez korlátozza a mobilböngészők hozzáférését az Azure AD-hez csatlakozó webalkalmazásokhoz, házirend által védett Microsoft Edge. A bármely más böngészőkkel nem védett, például a Safarit vagy a Chrome blokkolja a hozzáférést. Alkalmazhat például Exchange online-hoz és a SharePoint online-hoz, a Microsoft 365 felügyeleti központot és még akkor is, amelyekhez külső felhasználók számára keresztül a helyszíni helyek Azure-erőforrásokhoz való feltételes hozzáférés a [Azure AD-alkalmazásproxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started).

Az Azure AD-hez csatlakozó webalkalmazásokhoz használata a Microsoft Edge iOS és Android rendszeren korlátozása:
1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Válassza ki az Intune-ban csomópont alatt **feltételes hozzáférési** > **új szabályzat**.
3. Válassza ki **Grant** származó a **hozzáférés-vezérlés** részében.
4. Válassza ki a **Jóváhagyott ügyfélalkalmazás megkövetelése** elemet.
5. Válasszon **válassza** a a **Grant** panelen. Ezt a szabályzatot hozzá kell rendelni azokhoz a felhőalkalmazásokhoz, amelyek esetében azt szeretné, hogy csak az Intune Managed Browser alkalmazásból legyenek elérhetők.

    ![Képernyőkép a feltételes hozzáférési szabályzat - támogatás](./media/manage-microsoft-edge/manage-microsoft-edge-01.png)

6. A hozzárendelések területen válassza ki a **feltételek** > **ügyfélalkalmazás**. A **ügyfélalkalmazás** panel jelenik meg.
7. A **konfigurálása**válassza **Igen** a szabályzat adott ügyfélalkalmazásokra való érvényesítéséhez.
8. Ellenőrizze, hogy a **Browser** van-e kiválasztva ügyfélalkalmazásként.

    ![Képernyőfelvétel: a feltételes hozzáférési szabályzat – ügyfélalkalmazások kiválasztása](./media/manage-microsoft-edge/manage-microsoft-edge-02.png)

    > [!NOTE]
    > Ha korlátozni szeretné, hogy mely natív (nem böngészőbeli) alkalmazások férhetnek hozzá ezekhez a felhőalkalmazásokhoz, válassza a **Mobilalkalmazások és asztali ügyfelek** lehetőséget.

9. Az a **hozzárendelések** szakaszban jelölje be **felhasználók és csoportok**, majd válassza a felhasználók vagy csoportok a házirendhez hozzárendelni kívánt.

    > [!NOTE]
    > Az alkalmazáskonfigurációs szabályzatok fogadása érdekében a felhasználókat Intune App Protection-szabályzattal kell megcélozni. További információ az Intune alkalmazásvédelmi szabályzatainak létrehozásáról: [Mik azok az alkalmazásvédelmi szabályzatok?](app-protection-policy.md)

10. A szabályzat védelme alá tartozó alkalmazások megadásához a **Hozzárendelések** szakaszban válassza a **Felhőalkalmazások** lehetőséget.

A fenti szabályzat konfigurálása után felhasználók kényszerítve a Microsoft Edge használata az Azure AD-hez csatlakozó webalkalmazásokhoz, ez a szabályzat védelme alá eléréséhez. Ha a felhasználók megpróbálnak egy nem felügyelt böngésző használata ebben a forgatókönyvben, egy megjelenő üzenet, hogy a Microsoft Edge kell használniuk.

> [!TIP]
> Feltételes hozzáférés egy Azure AD-technológia. A feltételes hozzáférés csomópontot az Intune-ból elért ugyanazon a csomóponton megegyezik az Azure ad-ből érhető el.

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>Egyszeri bejelentkezés az Azure AD-hez csatlakozó webalkalmazásokhoz böngészőkben házirend által védett

IOS-eszközökön a Microsoft Edge és az Android kihasználhatja egyszeri bejelentkezés (SSO) minden webalkalmazáshoz (SaaS- és a helyszínen), amely az Azure AD-hez csatlakozó. Egyszeri bejelentkezés lehetővé teszi, hogy a felhasználók hozzáférhessenek az Azure AD-hez csatlakozó webalkalmazásokhoz keresztül a Microsoft Edge, írja be újra a hitelesítő adatok nélkül.

Egyszeri bejelentkezés szükséges regisztrálni az iOS-eszközök a Microsoft Authenticator alkalmazást, vagy az Intune vállalati portál Android-eszközét. Amikor a felhasználó rendelkezik mindkét, bekapcsolják eszközüket egy Azure AD-hez csatlakozó webes alkalmazást egy házirend által védett böngészőben való regisztrálásáról. (Ez a tulajdonság csak akkor igaz, ha még nem eszköz már regisztrálva van.) Miután az eszköz regisztrálva van a felhasználó fiókját az Intune által felügyelt, az adott fiók által az Azure AD-hez csatlakozó webalkalmazások esetében SSO.

> [!NOTE]
> Az eszközregisztráció egy egyszerű bejelentkezés az Azure AD szolgáltatással. Nem igényel teljes eszközregisztrációt, és nem ad informatikai további jogosultságokra az eszközön.

## <a name="create-a-protected-browser-app-configuration"></a>Egy védett böngésző alkalmazáskonfigurációjának létrehozása

Az alkalmazáskonfigurációk a alkalmazni, a felhasználó a böngésző által védett, vagy egy másik alkalmazást az eszközön már felügyelni kívánja a [az Intune alkalmazásvédelmi szabályzatának](app-protection-policy.md).

Egy védett browser alkalmazás konfigurációjának létrehozása:

1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Válassza ki **ügyfélalkalmazás** > **alkalmazáskonfigurációs szabályzatok** > **Hozzáadás**.
3. A **Konfigurációs szabályzat hozzáadása** panelen az alkalmazáskonfigurációs beállításokhoz írja be a **Nevet** és a **Leírást** (ez utóbbi nem kötelező).
4. Az **Eszközregisztráció** típusaként válassza a **Felügyelt alkalmazások** lehetőséget.
5. Válasszon **kötelező alkalmazások kiválasztása**. Ezután a a **megcélzott alkalmazások** panelen válassza ki a **Managed Browser** vagy **Edge** iOS-hez, androidhoz vagy esetében is.
6. Válassza ki **OK** térjen vissza a **alkalmazáskonfigurációs szabályzat felvételéhez** panelen.
7. Válassza a **Konfigurációs beállítások** lehetőséget. Az a **konfigurációs** panelen kulcs-érték párok definiálásával konfigurációk a Microsoft Edge, határozza meg. A jelen cikk későbbi részeiben további információt talál a definiálható kulcs-érték párokról.

    > [!NOTE]
    > A Microsoft Edge ugyanazokat a kulcs-érték párokat használja, mint a Managed Browser. 

8. Amikor elkészült, válassza ki a **OK**.
9. A **Konfigurációs szabályzat hozzáadása** panelen válassza a **Hozzáadás** lehetőséget.<br>
    Az új konfiguráció létrehozása és jelenik meg a **Alkalmazáskonfiguráció** panelen.

## <a name="assign-the-configuration-settings-you-created"></a>A létrehozott konfigurációs beállítások hozzárendelése 

A beállítások felhasználói csoportokhoz rendelhet az Azure ad-ben. Ha az illető felhasználó rendelkezik a célzott védett böngésző telepített példányával, akkor az alkalmazás felügyelete a megadott beállításokkal történik.

1. A a **ügyfélalkalmazás** az Intune mobilalkalmazás-kezelési irányítópult válassza a panel **alkalmazáskonfigurációs szabályzatok**.
2. A listából válassza ki a hozzárendelni kívánt alkalmazáskonfigurációt.
3. A következő panelen válassza ki a **hozzárendelések**.
4. Az a **hozzárendelések** panelen, és válassza ki azt az Azure AD-csoportot, amelyhez az alkalmazáskonfigurációt hozzárendelni, és válassza ki szeretné **OK**.

## <a name="configure-application-proxy-settings-for-protected-browsers"></a>Védett böngészők az alkalmazásproxy beállításainak konfigurálása

Használhatja a Microsoft Edge és [Azure AD-alkalmazásproxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) együtt való hozzáférést a felhasználóknak az intranetes webhelyekre a mobileszközükön. 

Néhány példa a forgatókönyvek az Azure AD-alkalmazásproxy engedélyezése az alábbiak: 

- Egy felhasználó az Outlook mobilalkalmazást az, amely az Intune által védett használ. Majd kattintson egy e-mailben egy intranetes webhelyre mutató hivatkozást, és a Microsoft Edge felismeri, hogy a felhasználó alkalmazásproxyn keresztül megnyílt adott intranetes webhely. A felhasználó automatikusan irányítja a proxyn keresztül történő alkalmazás, minden lehetséges többtényezős hitelesítés és feltételes hozzáférési érhesse el az intranetes webhelyek hitelesítésére. A felhasználó mostantól hozzáférhetnek a belső helyek, még a mobileszközeikről, és az Outlook-beli hivatkozás megfelelően működik-e.
- A felhasználó megnyitja a Microsoft Edge az iOS és Android rendszerű eszközökön. A Microsoft Edge védelme az Intune-nal, és az alkalmazásproxy engedélyezve van, a felhasználó meg egy intranetes webhelyet használja őket belső URL-cím használatával. A Microsoft Edge felismeri, hogy a felhasználó alkalmazásproxyn keresztül megnyílt adott intranetes webhely. A felhasználó automatikusan áthalad alkalmazásproxy érhesse el az intranetes webhelyek hitelesítésére. 

### <a name="before-you-start"></a>Előkészületek

- Állítsa be a belső alkalmazásokat az Azure AD-alkalmazásproxyn keresztül.
    - Az Alkalmazásproxy konfigurálásáról és az alkalmazások közzétételéről a [telepítési dokumentációban](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy) olvashat.
- Rendelkeznie kell a Microsoft Edge app [az Intune alkalmazásvédelmi szabályzatának](app-protection-policy.md) hozzárendelve.

> [!NOTE]
> Az Alkalmazásproxy frissített átirányítási adatainak érvénybe lépése a Managed Browserben és a Microsoft Edge-ben akár 24 órát is igénybe vehet.

#### <a name="step-1-enable-automatic-redirection-to-a-protected-browser-from-outlook"></a>1\. lépés: Automatikus átirányítás engedélyezése az Outlookból egy védett böngészőhöz
Az Outlook állítson be egy alkalmazásvédelmi szabályzatot, amely lehetővé teszi, hogy a beállítás **megosztás webes tartalom házirenddel felügyelt böngészők**.

![Képernyőkép az alkalmazásvédelmi szabályzat - megosztás webes tartalom házirenddel felügyelt böngészőket](./media/manage-microsoft-edge/manage-microsoft-edge-03.png)

#### <a name="step-2-set-the-app-configuration-setting-to-enable-app-proxy"></a>2\. lépés: Állítsa be az alkalmazás a konfigurációs beállítás alkalmazásproxy engedélyezése
A következő kulcs/érték pár, hogy engedélyezze az alkalmazásproxyt a Microsoft Edge Microsoft Edge céljaként:

|    Kulcs    |    Value    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.AppProxyRedirection    |    true    |

A Microsoft Edge és az Azure AD-alkalmazásproxy használatával párhuzamosan helyszíni webalkalmazásokhoz való zökkenőmentes (és védett) hozzáféréshez kapcsolatos további információkért lásd: [együtt jobb: Az Intune és az Azure Active Directory együtt teszi jobbá a felhasználói hozzáférést](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access) című blogbejegyzésében találhat. Az ebben a blogbejegyzésben hivatkozások az Intune Managed Browser, de a tartalom is vonatkozik a Microsoft Edge.

## <a name="configure-a-homepage-shortcut-for-microsoft-edge"></a>A kezdőlap helyi konfigurálása a Microsoft Edge

Ezzel a beállítással konfigurálhatja a kezdőlap parancsikont a Microsoft Edge. Amikor a felhasználó Microsoft Edge-ben egy új lapon nyílik meg a kezdőlapon helyi konfigurálása jelenik meg az első ikon a keresősáv alatt. A felhasználó nem szerkeszthetők, és a felügyelt környezetben a parancsikon törlése. A kezdőlap helyi jeleníti meg, hogy megkülönböztesse a cég nevére. 

A kezdőlap helyi konfigurálásához kövesse az alábbi kulcs-érték párt:

|    Kulcs    |    Value    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.homepage   |    Adjon meg egy érvényes URL-címet. A helytelen URL-címek biztonsági intézkedésként le vannak tiltva.<br>**Példa:**  <`https://www.bing.com`>
    |

## <a name="configure-managed-bookmarks-for-microsoft-edge"></a>Felügyelt könyvjelzőinek beállítása a Microsoft Edge

A könnyű hozzáférést konfigurálhatja úgy, hogy szeretné a felhasználókat, hogy elérhető a Microsoft Edge használatakor a könyvjelzők. 

Az alábbiakban néhány részletei:

- Ezek a könyvjelzők csak jelennek meg a felhasználók számára a vállalati üzemmód a Microsoft Edge használatakor. 
- Ezeket a könyvjelzőket nem törölhető és nem módosíthatják a felhasználók.
- Ezek a könyvjelzők a lista tetején jelennek meg. Felhasználók által könyvjelzők jelennek meg a könyvjelzők ezek alá kerülnek.
- Ha engedélyezte az alkalmazásproxy átirányítás, a webalkalmazások Application Proxy vagy a belső vagy külső URL-cím használatával is hozzáadhat.

Felügyelt könyvjelzők konfigurálásához kövesse az alábbi kulcs-érték párt:

|    Kulcs    |    Érték    |
|---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.bookmarks    |    Ez a konfiguráció értéke egy könyvjelzőlista. Minden könyvjelző címből és a könyvjelző URL-cím áll. A title és az URL-CÍMÉT a `|` karakter.      Példa:<br>`Microsoft Bing|https://www.bing.com`<br>Több könyvjelző megadásakor külön minden párból az karakterpárt `||`.<p>Példa:<br>`Microsoft Bing|https://www.bing.com||Contoso|https://www.contoso.com`    |

## <a name="display-myapps-within-microsoft-edge-bookmarks"></a>A Microsoft Edge-könyvjelzők belül MyApps megjelenítése

Alapértelmezés szerint a felhasználók számára jelennek meg, hogy a Microsoft Edge-könyvjelzők belül egy adott mappában megtörténik MyApps webhelyeket. A mappa célállapotba a saját szervezetének nevére.

|    Kulcs    |    Érték    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.MyApps    |    **Igaz** MyApps bemutatja a Microsoft Edge-könyvjelzők belül.<p>**FALSE (hamis)** elrejti a MyApps Microsoft Edge belül.    |

## <a name="specify-allowed-or-blocked-sites-list-for-microsoft-edge"></a>Adja meg az engedélyezett vagy tiltott helyek listája a Microsoft Edge
Alkalmazáskonfiguráció segítségével megadhatja a felhasználók férhetnek hozzá a munkahelyi profil használatakor webhelyeket. Engedélyezési lista használatakor a felhasználók képesek csak a kifejezetten felsorolt helyek eléréséhez. Ha használ egy tiltólista, a felhasználók kivéve azokat, explicit módon letiltott összes hely férhet hozzá. Engedélyezett vagy letiltott listájából, nem mindkettőt kivetett csak kell. Mindkét írnak elő, ha az engedélyezett listára van figyelembe véve.  

Használja az alábbi kulcs-érték párok konfigurálásához vagy egy engedélyezett vagy tiltott helyek listája a Microsoft Edge. 

|    Kulcs    |    Érték    |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    A következő lehetőségek közül választhat:<p>1. Engedélyezett URL-címek megadása (csak ezek az URL-címek engedélyezettek, más webhelyek nem érhetők el):<br>`com.microsoft.intune.mam.managedbrowser.AllowListURLs`<p>2. Tiltott URL-címek megadása (minden más webhely elérhető lesz):<br>`com.microsoft.intune.mam.managedbrowser.BlockListURLs`    |    A kulcs megfelelő értéke egy URL-címlista. A kívánt engedélyezheti vagy letilthatja a egyetlen értékként, a függőleges vonallal elválasztott URL-címeket `|` karakter.<br>**Példák:**<br>`URL1|URL2|URL3`<br>`http://.contoso.com/|https://.bing.com/|https://expenses.contoso.com`  |

### <a name="url-formats-for-allowed-and-blocked-site-list"></a>Az URL-formátumok engedélyezett, és a Tiltott helyek listája 
Különböző URL-formátumok használatával hozhat létre az engedélyezett/letiltott webhelyek listája. Ezek a minták engedélyezett az alábbi táblázat részletezi. Néhány megjegyzés a Kezdés előtt: 
- Az URL-címek listába történő bevitelekor ellenőrizze, hogy az URL-címet a **http** vagy a **https** előtaggal adta-e meg.
- Használható helyettesítő karakter és szimbólum (\*) a megengedett minták alábbi listájának szabályai szerint.
- Helyettesítő karakter csak meg tudja a teljes összetevője az állomásnevet (elválasztott) vagy az elérési út (a perjelet elválasztva) teljes részei. Ha például `http://*contoso.com` van **nem** támogatott.
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
    |    `http://www.contoso.com:80`    |    Egyetlen lap, megegyezik a portszám használatával    |    `http://www.contoso.com:80`    |         |
    |    `https://www.contoso.com`    |    Egyetlen biztonságos lap    |    `https://www.contoso.com`    |    `http://www.contoso.com`    |
    |    `http://www.contoso.com/images/*`    |    Egyetlen mappa és annak összes almappája    |    `www.contoso.com/images/dogs`<br>`www.contoso.com/images/cats`    |    `www.contoso.com/videos`    |
  
- Az alábbi példák engedélyezett beviteleket, amely nem adható meg:
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
  
## <a name="define-behavior-when-users-try-to-access-a-blocked-site"></a>Viselkedés határozza meg, amikor a felhasználó megpróbál hozzáférni egy letiltott hely

A kettős-identity-modell beépítve a Microsoft Edge egy olyan rugalmasabb élmény a végfelhasználók számára, mint az Intune Managed Browser for engedélyezheti. Amikor a felhasználók a Microsoft Edge-ben egy letiltott hely találat, megkérheti őket a hivatkozás megnyitásához a saját személyes környezet helyett a munkahelyi környezetben. Ez lehetővé teszi, hogy maradjon a védett, miközben gondoskodik a vállalati erőforrások biztonságos. Például ha egy felhasználó egy hivatkozást küld Outlook keresztül hír, akkor megnyithatják a hivatkozás saját személyes környezetben vagy egy InPrivate-lapon. A munkahelyi környezetben hírek webhelyek nem teszi lehetővé. Alapértelmezés szerint az átmenetek engedélyezettek.

Az enyhe átmenetek engedélyezettek-e konfigurálásához kövesse az alábbi kulcs-érték párt:

|    Kulcs    |    Érték    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock`    |    **Igaz** lehetővé teszi, hogy a Microsoft Edge átmenet felhasználók számára a személyes környezet, nyissa meg a letiltott webhelyek.<p>**Blokk** megakadályozza, hogy a Microsoft Edge transitioning felhasználók. Felhasználó egyszerűen megjelenik egy üzenet, amely megállapítja, hogy blokkolva van-e a hely, amelyhez hozzá szeretne férni.    |

## <a name="direct-users-to-microsoft-edge-instead-of-the-intune-managed-browser"></a>A Microsoft Edge helyett az Intune Managed Browser közvetlen felhasználók 

Az Intune Managed Browser és a Microsoft Edge böngésző házirend által védett is használható. Győződjön meg arról, hogy a felhasználók vannak irányítja a megfelelő browser alkalmazás használatához, jelölje ki az Intune által felügyelt alkalmazások (például az Outlook, OneDrive és SharePoint) az összes az alábbi konfigurációs beállítás:

|    Kulcs    |    Érték    |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.useEdge`    |    Az érték `true` átirányítja a felhasználókat, hogy töltse le és használja a Microsoft Edge.<br>Az érték `false` lehetővé teszi a felhasználók az Intune Managed Browser használatára.    |

Ha az alkalmazás konfigurációs érték **nem** állítja, az alábbi logikával határozza meg böngésző használható vállalati hivatkozások megnyitásához.

Androidon:
- Az Intune Managed Browser indít, ha egy felhasználó az Intune Managed Browser és a Microsoft Edge az eszköz letöltése. 
- A Microsoft Edge indít, ha csak a Microsoft Edge letöltődik az eszközön, és az Intune-szabályzat vonatkozik.
- Felügyelt böngésző elindítja, ha csak a Managed Browser az eszközön, és az Intune-szabályzat vonatkozik.

Az iOS rendszeren, ha az alkalmazásokban integrálva van az Intune SDK for iOS 9.0.9+ verziója:
- Az Intune Managed Browser indít, ha a Managed Browser és a Microsoft Edge az eszközön.  
- A Microsoft Edge indít, ha csak a Microsoft Edge az eszközön, és az Intune-szabályzat vonatkozik.
- Felügyelt böngésző elindítja, ha csak a Managed Browser az eszközön, és az Intune-szabályzat vonatkozik.

## <a name="use-microsoft-edge-on-ios-to-access-managed-app-logs"></a>IOS-es Microsoft Edge használatával felügyelt alkalmazások naplóinak elérése 

A Microsoft Edge IOS-es eszközére telepített felhasználók megtekinthetik az összes felügyeleti állapotát a Microsoft közzétett alkalmazást. Elküldhetik a naplófájlokat a felügyelt iOS-eszköz hibaelhárítása céljából. Ezt a következőképpen teheti meg:
1. Nyissa meg a Microsoft Edge az iOS-eszközön.
2. A címsorba gépelje be a következőt: `about:intunehelp` 
3. A Microsoft Edge hibaelhárítási módban indul el.

Az alkalmazásnaplókban tárolt beállítások listáját az [Alkalmazásvédelmi naplók áttekintése a Managed Browserben](app-protection-policy-settings-log.md) című témakörben találja.

Naplók megtekintése az Android-eszközökön, olvassa el [naplók elküldése a rendszergazdának e-mailben](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). 

## <a name="security-and-privacy-for-microsoft-edge"></a>Biztonság és adatvédelem a Microsoft Edge

A Microsoft Edge további biztonsági és adatvédelmi szempontjai a következők:

- A Microsoft Edge ne fogyaszthassa beállításokat, amelyeket a felhasználók saját eszközeiken, a natív böngészőben meg, mert a Microsoft Edge ezeket a beállításokat nem érhető el.
- Konfigurálhatja a beállítást **egyszerű PIN-kód megkövetelése a hozzáféréshez** vagy **vállalati hitelesítő adatok megkövetelése a hozzáféréshez** a Microsoft Edge társított egy alkalmazásvédelmi szabályzatot. Ha egy felhasználó kijelöli a hitelesítési lapon a súgóhivatkozásra, bármely internetes webhelyet, függetlenül attól, hogy bekerültek a szabályzatban egy tiltólista megnyithassák.
- A Microsoft Edge képes blokkolni a hozzáférést a webhelyekhez, csak akkor, ha azokat közvetlenül érik el. Amikor a felhasználó köztes szolgáltatások (például egy fordítási szolgáltatás) használja a webhely elérésére nem blokkolja a hozzáférést.
- Hitelesítés engedélyezése, és elérheti az Intune-dokumentáció * **. microsoft.com** mentesül az engedélyezési és blokkolási beállítások. Mindig engedélyezve van.
- Bármikor kikapcsolhatják az adatgyűjtést. A Microsoft termék- és szolgáltatásfejlesztési célból automatikus módszerekkel név nélküli adatokat gyűjt a Managed Browser teljesítményéről és használatáról. A felhasználók kikapcsolhatják az adatgyűjtést az eszköz **Használati adatok** beállításával. Nem tudja befolyásolni ezen adatok gyűjtését. Az iOS-eszközökön nem lehet megnyitni a felhasználók által meglátogatott webhelyeknek lejárt vagy nem megbízható tanúsítvánnyal rendelkeznek.

## <a name="next-steps"></a>További lépések

- [Mik azok az alkalmazásvédelmi szabályzatok?](app-protection-policy.md) 

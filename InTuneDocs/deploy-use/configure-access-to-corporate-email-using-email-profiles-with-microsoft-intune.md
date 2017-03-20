---
title: "Vállalati e-mailek elérése e-mail-profilokkal | Microsoft Docs"
description: "Az e-mail-profil beállításainak segítségével konfigurálhatók az e-mail-hozzáférési beállítások a mobileszközökön futó konkrét e-mail-ügyfélprogramok számára."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 10f0cd61-e514-4e44-b13e-aeb85a8e53ae
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 51f9d7bad6a1411ff68fa94c62421e2c0a43ab5a
ms.openlocfilehash: d60b9afdf7fe9f78dd5cc4693259b8667fb17299
ms.lasthandoff: 02/25/2017


---

# <a name="configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune"></a>Vállalati levelezéshez való hozzáférés konfigurálása e-mail profilokkal a Microsoft Intune-ban

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Sok mobilplatform az operációs rendszer részét képező natív e-mail-ügyfélprogramot tartalmaz. Egyes ügyfelek a jelen témakörben ismertetett módon e-mail-profilok használatával állíthatók be.

Az e-mail-profil beállításainak segítségével konfigurálhatók a mobileszközökön futó adott e-mail-ügyfélprogramok e-mail-hozzáférési beállításai. A támogatott platformokon a natív e-mail-ügyfélprogramok a Microsoft Intune segítségével beállíthatók úgy, hogy a felhasználók saját eszközeiken további beállítások nélkül hozzáférhessenek a vállalati e-mailjeikhez.

Ha további adatveszteség-megelőzési intézkedéseket szeretne foganatosítani, használja a [ltételes hozzáférést](restrict-access-to-email-and-o365-services-with-microsoft-intune.md), amely szabályozza a hozzáférést a felhasználó postaládájához, bármilyen levelezőprogramot is használjon (beleértve a natív levelezőprogramokat).

A rendszergazdák vagy a felhasználók alternatív e-mail-ügyfélprogramokat is telepíthetnek (például a Microsoft Outlook Android vagy iOS rendszerhez készült változatát). Előfordulhat, hogy ezek az e-mail-ügyfélprogramok nem támogatják az e-mail-profilokat, és nem állíthatók be a Microsoft Intune e-mail-profilok használatával.  

A következő eszköztípusokon konfigurálható a natív e-mail-ügyfélprogram e-mail-profilok segítségével:
-    Windows Phone 8.1 és újabb verziók
-    Windows 10 (asztali verzió), Windows 10 Mobile és újabb verziók
-    iOS 8.0 és újabb verziók
-    Samsung KNOX Standard (4.0-s és újabb verzió)
-    Android for Work

>[!NOTE]
>Az Intune két Android for Work e-mail profilt biztosít, egyet a Gmail és egyet a Nine Work email-alkalmazás számára. Ezek az alkalmazások a Google Play áruházból érhetők el és támogatják a kapcsolatot az Exchange-dzsel. Az e-mail-kapcsolat létrehozásához telepítse a két email-alkalmazás valamelyikét a felhasználók eszközein, majd hozza létre és telepítse a megfelelő profilt. Lehetséges, hogy egyes e-mail alkalmazások, például a Nine Work, csak díjfizetés mellett használhatók. Olvassa el az alkalmazás licencelési információit, vagy kérdés esetén lépjen kapcsolatba az alkalmazás kibocsátójával.

Azon kívül, hogy beállít egy e-mail-fiókot az eszközön, megadhatja a szinkronizálni kívánt e-mailek mennyiségét, és eszköztípustól függően a szinkronizálni kívánt tartalmakat is.

>[!NOTE]
>
>Ha a felhasználó azelőtt telepített egy e-mail profilt, hogy az Intune beállított volna egyet, akkor az Intune e-mail profil telepítésének eredménye az eszköz platformjától függ:

>**iOS**: A rendszer az állomásnév és az e-mail cím alapján egy meglévő, duplikált e-mail profilt észlelt. A felhasználó által létrehozott, duplikált e-mail profil meggátolja az Intune-rendszergazda által létrehozott profil telepítését. Ez gyakori probléma, mivel az iOS-felhasználók gyakran hoznak létre egy e-mail-profilt a regisztráció előtt. A vállalati portál tájékoztatja a felhasználót, hogy a manuálisan beállított e-mail-profil nem megfelelő, és megkéri, hogy távolítsa el a profilt. A felhasználónak ekkor törölnie kell az e-mail-profilt, hogy az Intune-profilt telepíthesse. A probléma elkerülése érdekében kérje meg a felhasználókat, hogy az e-mail profil telepítése előtt regisztrálják eszközeiket, és engedélyezzék az Intune-nak, hogy telepítse a profilt.

>**Windows**: A rendszer az állomásnév és az e-mail cím alapján egy meglévő, duplikált e-mail profilt észlelt. Az Intune felülírja a felhasználó által létrehozott meglévő e-mail profilt.

>**Samsung KNOX**: A rendszer az e-mail cím alapján egy meglévő, duplikált e-mail profilt észlelt, és felülírja azt az Intune-profillal. Ha a felhasználó ezt az észlelt fiókot állítja be, az Intune-profil ismételten felülírja. Ez megzavarhatja a felhasználót.

>Mivel a Samsung KNOX nem használja az állomásnevet a profil azonosításához, azt javasoljuk, hogy ne hozzon létre több e-mail profilt azért, hogy ugyanahhoz az e-mail címhez használja őket a különböző gazdagépeken, mivel ezek felülírják egymást.

>**Android for Work**: Az Intune-profil csak az eszköz munkahelyi profiljának adott e-mail-alkalmazásaira vonatkozik, és nem befolyásolja az eszköz felhasználói profiljának e-mail-beállításait.


## <a name="secure-email-profiles"></a>Az e-mail-profilok biztonságossá tétele
Az e-mail-profilokat tanúsítvánnyal vagy jelszóval lehet biztonságossá tenni.

### <a name="certificates"></a>Tanúsítványok
Az e-mail-profil létrehozásakor válassza ki a korábban az Intune-ban már létrehozott tanúsítványprofilt. Ez identitástanúsítványként is ismert. Ezt hitelesíti a rendszer egy megbízható tanúsítványprofil (vagy főtanúsítvány) segítségével, hogy ellenőrizze a felhasználó eszközének csatlakozásra való jogosultságát. A megbízható tanúsítvány az e-mail-kapcsolatot hitelesítő számítógépre van telepítve. Ez általában a natív levelezési kiszolgáló.

További információt a tanúsítványprofilok Intune-ban történő létrehozásáról és használatáról [Az erőforrások biztonságos elérése tanúsítványprofilokkal](secure-resource-access-with-certificate-profiles.md) című témakörben találhat.

### <a name="user-name-and-password"></a>Felhasználónév és jelszó
A felhasználó a natív levelezési kiszolgálón a felhasználónév és a jelszó megadásával hitelesíti magát.

A jelszó nem szerepel az e-mail profilban, így a felhasználónak ezt minden alkalommal meg kell adnia, amikor az e-mail szolgáltatáshoz csatlakozik.

### <a name="create-an-email-profile"></a>E-mail profil létrehozása

1.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com) válassza a **Házirend** &gt; **Házirend hozzáadása** elemet.

2.  Állítsa be a következő házirendtípusok egyikét:

    -   **A Samsung KNOX szabvány e-mail profilja (4.0-s és újabb)**

    -   **E-mail-profil (iOS 8.0 és újabb)**

    -   **E-mail-profil (Windows Phone 8.1 és újabb)**

    -   **E-mail-profil (Windows 10 és újabb asztali és mobil rendszerek)**

    -   **E-mail-profil (Android for Work - Gmail)**

    -    **E-mail-profil (Android for Work - Nine Work)**

    Csak egyéni e-mail profilházirendet hozhat létre és telepíthet. Ajánlott beállítások nem állnak rendelkezésre.

3.  A következő táblázat segítségével konfigurálja az e-mail-profil beállításait:

|Beállítás neve | További információ|
| ----------- | --------------- |
    |**Név**|Az e-mail-profil egyedi neve.|
    |**Leírás**|A profil azonosítását megkönnyítő leírás.|
    |**Gazdagép**|Annak a vállalati kiszolgálónak az állomásneve, amelyen a natív e-mail-szolgáltatás fut.|
    |**Fióknév**|Az e-mail-fiók megjelenítendő neve. Ez fog megjelenni a felhasználók eszközein.|
    |**Felhasználónév**|Ez az Active Directory (AD) vagy az Azure AD egy attribútuma, ennek alapján fogja generálni a rendszer ennek az e-mail-profilnak a felhasználónevét. Válassza az elsődleges SMTP-címet (például *user1@contoso.com*) vagy az egyszerű felhasználónevet (például *user1* vagy *user1@contoso.com*).|
    |**E-mail cím**|A felhasználóhoz tartozó e-mail-cím előállításának módja az egyes eszközökön. Ha az elsődleges SMTP-cím használatával kíván bejelentkezni az Exchange-be, válassza az **Elsődleges SMTP-cím** lehetőséget; ha e-mail-címként a teljes egyszerű felhasználónevet kívánja használni, válassza az **Egyszerű felhasználónév** lehetőséget.|
    |**Hitelesítési módszer** (Android for Work, Samsung KNOX és iOS)|Az e-mail-profil által használandó hitelesítési módszernek válassza a **Felhasználónév és jelszó** vagy a **Tanúsítványok** lehetőséget.|
    |**Válasszon ki egy, az ügyfél-hitelesítéshez használandó ügyféltanúsítványt (identitástanúsítványt)** (Android for Work, Samsung KNOX és iOS)|Válassza ki az ügyfél korábban létrehozott SCEP tanúsítványát, amelyet az Exchange-kapcsolat hitelesítésére kíván használni. További információt a tanúsítványprofilok Intune-ban történő használatáról [Az erőforrások biztonságos elérése tanúsítványprofilokkal](secure-resource-access-with-certificate-profiles.md) című témakörben találhat. Ez a beállítás csak akkor látható, ha a hitelesítési módszer a **Tanúsítványok**.|
    |**S/MIME használata** (Samsung KNOX és iOS)|Kimenő e-mailek küldése S/MIME aláírással.|
    |**Aláíró tanúsítvány** (Samsung KNOX és iOS)|Válassza ki a kimenő e-mailek aláírására használt aláíró tanúsítványt. Ez a lehetőség csak akkor jelenik meg, ha az **S/MIME használata** lehetőséget választotta.|
    |**E-mailek szinkronizálása ennyi napra visszamenőleg**|Azt adja meg, hogy hány napra visszamenőleg kívánja szinkronizálni az e-maileket; az összes e-mail szinkronizálásához válassza a **Korlátlan** lehetőséget.|
    |**Szinkronizálás ütemezése** (Android for Work, Samsung KNOX, Windows Phone 8 és újabb verziók, Windows 10)|Válassza ki, hogy az eszközök milyen ütemezés szerint szinkronizálják az adatokat az Exchange-kiszolgálóról. **Az üzenetek érkezésekor** lehetőség kiválasztásával a rendszer azonnal szinkronizálja az adatokat, amint megérkeznek, a **Manuális** beállítás esetén pedig a felhasználónak kell kezdeményeznie a szinkronizálást.|
    |**SSL használata**|SSL-kommunikáció használata az e-mailek küldésekor és fogadásakor, valamint az Exchange-kiszolgálóval való kommunikációhoz. A Samsung KNOX 4.0-s vagy újabb verzióját futtató eszközök számára exportálja az Exchange Server SSL-tanúsítványát, és telepítse az Intune-ban androidos megbízható tanúsítványprofilként. Az Intune nem támogatja a hozzáférést ehhez a tanúsítványhoz, ha ez más módon telepítve van az Exchange-kiszolgálón.|
    |**Szinkronizálandó tartalomtípus** (minden platform az Android for Work Gmail kivételével)|Válassza ki az eszközökre szinkronizálni kívánt tartalomtípusokat.|
    |**Harmadik felek alkalmazásaiból is engedélyezett az e-mailek küldése** (csak iOS esetén)|A felhasználók alapértelmezett e-mail-küldési fiókként választhatják ki ezt a profilt, és engedélyezhetik a külső alkalmazások számára az e-maileknek a natív e-mail alkalmazásban történő megnyitását, például fájlok e-mailhez való csatolásához.|

> [!IMPORTANT]
>
> Ha már telepített egy e-mail-profilt, de szeretné megváltoztatni az **állomás** vagy az **E-mail cím** beállítás értékét, akkor törölje a meglévő e-mail-profilt, majd hozzon létre egy újat a kívánt értékekkel.

4.  Ha elkészült, kattintson a **Házirend mentése**gombra.

Az új szabályzat a **Házirend** munkaterület **Konfigurációs szabályzatok** csomópontjában jelenik meg.

## <a name="deploy-the-policy"></a>A szabályzat telepítése

1.  A **Házirend** munkaterületen válassza ki a telepíteni kívánt házirendet, majd kattintson a **Központi telepítés kezelése** elemre.

2.  A **Telepítések kezelése** párbeszédpanelen:

    -   **A házirend telepítése** – Válasszon ki egy vagy több olyan csoportot, amelyhez telepíteni kívánja a házirendet, majd kattintson a **Hozzáadás** &gt; **OK** gombra.

    -   **A párbeszédpanel bezárása telepítés nélkül** – Kattintson a **Mégse** gombra.

A **Házirend** munkaterület **Áttekintés** lapján található állapotösszegzés és riasztások segítségével azonosíthatók a szabályzattal kapcsolatos, figyelmet igénylő problémák. Ezen felül egy állapotösszegzés megjelenik az Irányítópult munkaterületen is.

> [!NOTE]
> - Android for Work használatakor az adott e-mail-profilon kívül telepítse a Gmail vagy a Nine Work alkalmazást is.
> - Ha egy eszközről ki szeretne törölni egy e-mail profilt, módosítsa a telepítését, és távolítson el minden olyan csoportot, amelyeknek tagja az eszköz. Megjegyzendő, hogy ha ez az egy e-mail-profil van az eszközön, nem lehet ezzel a módszerrel eltávolítani.

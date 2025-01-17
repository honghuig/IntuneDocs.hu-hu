---
title: Feltételes Exchange-hozzáférési szabályzat létrehozása
titleSuffix: Microsoft Intune
description: Feltételes hozzáférési szabályzat konfigurálása a helyszíni Exchange-hez és régi Dedikált Exchange Online-hoz az Intune-nal.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/15/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 003e6e5aa78440861e6aff5be138c4a302171c1b
ms.sourcegitcommit: a2cd14c30949cef17bfc6576513e7660a8015669
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/15/2019
ms.locfileid: "59571739"
---
# <a name="create-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated"></a>Feltételes hozzáférési szabályzat létrehozása a helyszíni Exchange-hez és régi Dedikált Exchange Online-hoz

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A cikk azt mutatja be, hogyan konfigurálható az eszközök megfelelősége alapján feltételes hozzáférés a helyszíni Exchange-hez.

Ha dedikált Exchange Online-környezettel rendelkezik, és szeretné tudni, hogy az új vagy az örökölt konfiguráció tartozik-e hozzá, lépjen kapcsolatba a fiókkezelővel. A helyszíni Exchange-hez vagy az örökölt dedikált Exchange Online környezethez való e-mail hozzáférés szabályozásához az Intune-ban konfiguráljon feltételes hozzáférést a helyszíni Exchange-hez.

## <a name="before-you-begin"></a>Előkészületek

Mielőtt konfigurálja a feltételes hozzáférést, ellenőrizze a következőket:

- Az Exchange esetében **Exchange 2010 SP1 vagy újabb verzió** szükséges. Az Exchange-kiszolgáló ügyfél-hozzáférési kiszolgálótömbje (CAS) nem támogatott.

- Az [Exchange Active Sync helyszíni Exchange-összekötőt](exchange-connector-install.md) kell használni, amely összekapcsolja az Intune-t a helyszíni Exchange-dzsel.

    >[!IMPORTANT]
    >Az Exchange-összekötő az Intune-bérlőjéhez tartozik, és semmilyen más bérlővel nem használható. Az Intune mostantól egy előfizetésben több helyszíni Exchange-összekötőt is támogat. Ha a cég egynél több helyszíni Exchange-összekötővel rendelkezik, minden Exchange-szervezet részére külön összekötőt építhet ki.

- A helyszíni Exchange-szervezet összekötője bármely gépen telepíthető, amennyiben az képes az Exchange-kiszolgálóval való kommunikációra.

- Ez az összekötő támogatja az **Exchange CAS-környezetet**. Ha szeretné, technikailag az is megoldható, hogy közvetlenül az Exchange CAS-kiszolgálóra telepítse az összetevőt, ez azonban nem javasolt, mert növeli a kiszolgálót érő terhelést. Az összekötőt úgy kell konfigurálni, hogy az kommunikáljon az Exchange CAS-kiszolgálók valamelyikével.

- Az **Exchange ActiveSync** tanúsítványalapú hitelesítéssel vagy felhasználó által megadott hitelesítő adatokkal konfigurálandó.

- Amikor feltételes hozzáférési szabályzatokat konfigurál és rendel hozzá felhasználókhoz, a felhasználók csak akkor csatlakozhatnak az e-mail fiókjukhoz, ha a használt **eszköz**:
    - **Regisztrálva** van az Intune-ban, vagy olyan számítógép, amely csatlakoztatva van egy tartományhoz.
    - **Regisztrálva van az Azure Active Directoryban**. Ezenkívül az ügyfél Exchange ActiveSync-azonosítójának regisztrálva kell lennie az Azure Active Directoryban.
<br></br>
- Az Azure AD eszközregisztrációs szolgáltatása (DRS) automatikusan aktiválódik az Intune-t és az Office 365-öt használó ügyfelek számára. Azon ügyfelek számára, akik már telepítették az ADFS eszközregisztrációs szolgáltatását, nem láthatók a regisztrált eszközök a helyszíni Active Directoryban. **Ez nem érvényes a Windows rendszerű számítógépekre és a Windows Phone-eszközökre**.

- **Meg kell felelnie** az eszközre telepített összes megfelelőségi szabályzatnak.

- Ha az eszköz nem felel meg a feltételes hozzáférés beállításainak, a felhasználó a következő üzenetek valamelyikét kapja bejelentkezéskor:
    - Ha az eszköz nincs regisztrálva az Intune-ban vagy az Azure Active Directoryban, megjelenik egy üzenet, amely leírja, hogyan kell telepíteni a Munkahelyi portál alkalmazást, regisztrálni az eszközt és aktiválni az e-mailt. Ez a folyamat hozzárendeli az eszköz Exchange ActiveSync-azonosítóját is az Azure Active Directoryban lévő eszközrekordhoz.
    - Ha az eszköz nem felel meg a feltételeknek, egy üzenet jelenik meg, amely a felhasználót az Intune Munkahelyi portál webhelyére vagy a Munkahelyi portál alkalmazásba irányítja, ahol további információt talál a problémáról és megoldásáról.

### <a name="support-for-mobile-devices"></a>A mobileszközök támogatása

- Windows Phone 8.1 és újabb verziók
- Natív e-mail alkalmazás iOS rendszerű eszközökön.
- EAS levelezési ügyfélprogramok, mint például a Gmail az Android 4-es vagy újabb verzióiban.
- EAS levelezési ügyfélprogramok **Android munkahelyi profilos eszközök:** Csak **Gmail** és **Nine Work Android Enterprise** a a **munkahelyi profil** Android munkahelyi profilos eszközök támogatottak. Ahhoz, hogy a feltételes hozzáférés működjön az androidos munkahelyi profilos eszközökön, telepíteni kell egy e-mail-profilt a Gmail vagy a Nine Work for Android Enterprise alkalmazáshoz, és ezeket az alkalmazásokat kötelező telepítésként kell központilag telepíteni.

> [!NOTE]
> A Microsoft Outlook Androidra és IOS-es nem támogatott az Exchange helyszíni összekötő keresztül. Ha szeretné kihasználni az Azure Active Directory feltételes hozzáférési szabályzatok és az Intune alkalmazásvédelmi szabályzatok IOS rendszerhez készült Outlook és a helyileg üzemeltetett postaládák esetében az Android, tekintse meg [használata hibrid IOS rendszerhez készült Outlook Modern hitelesítést és Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth). 

### <a name="support-for-pcs"></a>Számítógépek támogatása

A natív **Posta** alkalmazás a Windows 8.1-es és újabb verzióiban (az Intune-ban regisztrálva)


## <a name="configure-exchange-on-premises-access"></a>A helyszíni Exchange-hozzáférés konfigurálása

1. Az [Azure Portalon](https://portal.azure.com/) jelentkezzen be az Intune-os hitelesítő adataival.

2. Lépjen a **Intune** > **Exchange-hozzáférés**, majd válassza ki **a helyszíni Exchange-hozzáférés**. 

3. Az a **a helyszíni Exchange-hozzáférés** panelen válassza a **Igen** való *engedélyezése a helyszíni Exchange-hozzáférés-vezérlés*.

4. Válassza a bal oldali menü **Minden szolgáltatás** pontját, majd írja be a szűrő szövegmezőbe az **Intune** nevet.

5. Az **Intune** kiválasztásával megjelenik az **Intune irányítópultja**.

6. Válassza a **Helyszíni hozzáférés** lehetőséget. A **Helyszíni hozzáférés** panelen látható a feltételes hozzáférési szabályzat állapota, és az, hogy mely eszközökre van hatással.

7. Válassza a **Kezelés** terület **Helyszíni Exchange-hozzáférés** elemét.

8. Engedélyezze a helyszíni Exchange hozzáférés-vezérlését az **Helyszíni Exchange-hozzáférés** panel **Igen** elemét választva.

    > [!NOTE]
    > Ha nem konfigurált Exchange Active Sync helyszíni összekötőt, ez a beállítás nem érhető el.  Először telepítenie és konfigurálnia kell legalább egy összekötőt, és csak azt követően aktiválhatja a feltételes hozzáférést a helyszíni Exchange-hez. További részletek [A helyszíni Intune Exchange Connector telepítése](exchange-connector-install.md) című cikkben olvashatók.

9. A **Hozzárendelés** beállításnál válassza a **Tartalmazott csoportok** lehetőséget.  Használja azt a biztonsági felhasználócsoportot, amelynek feltételes hozzáférést szeretne előírni. Ez a művelet megköveteli a felhasználóktól, hogy regisztrálják az eszközüket az Intune-ban, és megfeleljenek a megfelelőségi profiloknak.

10. Ha ki szeretne zárni bizonyos felhasználócsoportokat, akkor válassza a **Kizárt csoportok** lehetőséget, majd egy olyan felhasználócsoportot, amelyet mentesíteni szeretne a kötelező eszközregisztráció és a feltételeknek való megfelelés alól.

11. Válassza a **Beállítások** terület **Felhasználói értesítések** elemét, és módosítsa az alapértelmezett e-mail szövegét. Ezt az üzenetet küldi el a rendszer a felhasználóknak, ha egy a feltételeknek nem megfelelő eszközzel próbálják meg elérni a helyszíni Exchange-et. Az üzenetsablon egy jelölőnyelvet használ.  Amint beírja az üzenetet, azt is követheti, hogy mit fog látni a címzett.
    > [!TIP]
    > A jelölőnyelvekről ez a [Wikipedia-cikk](https://en.wikipedia.org/wiki/Markup_language) nyújt tájékoztatást.

12. Az **Exchange ActiveSync speciális hozzáférési beállításai** panelen adja meg a következő két lépésben ismertetett módon az Intune által nem kezelt eszközökre vonatkozó alapértelmezett globális hozzáférési szabályt, illetve a platformszintű szabályokat. A Speciális beállítások panelen a beolvasásához a *Exchange-hozzáférés – helyszíni Exchange-hozzáférés* nézetben válassza *– az Exchange ActiveSync helyszíni összekötő*.

13. Választhat, hogy engedélyezi vagy letiltja az Exchange elérését az olyan eszközök számára, amelyekre nem vonatkoznak feltételes hozzáférési vagy egyéb szabályok.

   - Ha itt a hozzáférés engedélyezését állítja be, azonnal minden eszköz hozzáfér a helyszíni Exchange-hez.  A **Tartalmazott csoportokban** foglalt felhasználók eszközeinek hozzáférését letiltja a rendszer, ha a kiértékelés során nem felelnek meg a megfelelőségi szabályzatoknak, vagy nincsenek regisztrálva az Intune-ban.
   - Ha ezt a beállítást a hozzáférés letiltására állítja be, akkor a rendszer kezdetben azonnal megakadályoz minden eszközt a helyszíni Exchange elérésében.  A **Tartalmazott csoportokban** foglalt eszközök felhasználói viszont hozzáférést kapnak, ha az eszközük regisztrálva van az Intune-ban, és a kiértékeléskor megfelel a feltételeknek. A nem Samsung Knox Standard rendszerű androidos eszközöket mindig letiltja a rendszer, mert az ilyen eszközök nem támogatják ezt a beállítást.

14. Válassza az **Eszközplatform-kivételek** terület **Hozzáadás** gombját a platformok megadásához. Ha a **Nem felügyelt eszközhozzáférés** beállítása a **Letiltva** értékre van állítva, a regisztrált és a feltételeknek megfelelő eszközök akkor is hozzáférést kapnak, ha egy platformkivétel letiltja őket. Mentse a beállításokat az **OK** gombra kattintva.

15. Mentse a feltételes hozzáférési szabályzatot a **Helyszíni** panel **Mentés** gombjára kattintva.

## <a name="create-azure-ad-conditional-access-policies-in-intune"></a>Azure AD feltételes hozzáférési szabályzatok létrehozása az Intune-ban

A feltételes hozzáférés az Azure Active Directory (Azure AD) technológiája. Az *Intune-ból* elérhető feltételes hozzáférési csomópont ugyanaz a csomópont, amelyet az *Azure AD-ből* is el lehet érni.  

> [!IMPORTANT]
> Ahhoz, hogy Azure AD feltételes hozzáférési szabályzatokat hozhasson létre az Intune Azure Portal webhelyen, Azure AD Premium szintű előfizetésre van szükség.

### <a name="to-create-a-conditional-access-policy"></a>Egy feltételes hozzáférési szabályzat létrehozása

1. Az a **Intune irányítópult**válassza **feltételes hozzáférési**.

2. Az a **házirendek** ablaktáblán válassza előbb **új szabályzat** hozhat létre az új Azure AD feltételes hozzáférési szabályzat.

## <a name="see-also"></a>Lásd még:

[Feltételes hozzáférés az Azure Active Directoryban](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)

---
title: Oktatóanyag – nem felügyelt eszközökön az Exchange Online e-mailek védelme
titleSuffix: Microsoft Intune
description: Ismerje meg, az Intune alkalmazásvédelmi szabályzataival és Azure AD feltételes hozzáférés az Office 365 Exchange Online biztonságossá tételéhez.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/10/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7868d5f9ef97f4b054457deff6f24cd91d6c31d8
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67528682"
---
# <a name="tutorial-protect-exchange-online-email-on-unmanaged-devices"></a>Oktatóanyag: Nem felügyelt eszközökön az Exchange Online e-mailek védelme

Ismerje meg az alkalmazásvédelmi szabályzatok használata a feltételes hozzáférés Exchange Online védelme akkor is, ha az eszközök nincsenek regisztrálva az Intune-ban például eszközfelügyeleti megoldás. Az oktatóanyag segítségével megtanulhatja a következőket: 

> [!div class="checklist"]
> * Hozzon létre az Outlook alkalmazás az Intune alkalmazásvédelmi szabályzat. Fogja korlátozzák, hogy a felhasználó milyen alkalmazásadatok mindenre megakadályozzák, hogy a "Mentés másként" és korlátozása kivágási, másolási és beillesztési műveleteket. 
> * Hozzon létre az Azure Active Directory (Azure AD) feltételes hozzáférési szabályzatai csak az Outlook alkalmazás vállalati e-mailek elérését az Exchange Online. Többtényezős hitelesítés (MFA) is a Modern hitelesítési ügyfelek, például az Outlook iOS-hez és az Android lesz szükséges.

## <a name="prerequisites"></a>Előfeltételek
  - Az oktatóanyag végrehajtásához szüksége lesz egy tesztelési bérlőre a következő előfizetésekkel:
    - Prémium szintű Azure Active Directory ([ingyenes próbaverzió](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
    - Intune-előfizetés ([az ingyenes próbaidőszak](free-trial-sign-up.md))
    - Office 365 Vállalati előfizetés, ami magában foglalja az Exchange-et ([ingyenes próbaverzió](https://go.microsoft.com/fwlink/p/?LinkID=510938))

## <a name="sign-in-to-intune"></a>Bejelentkezés az Intune-ba

Jelentkezzen be az [Intune-ba](https://go.microsoft.com/fwlink/?linkid=2090973) globális rendszergazdaként vagy Intune-beli szolgáltatásadminisztrátorként. Az Intune-t az Azure Portalon a **Minden szolgáltatás** > **Intune** útvonalon érheti el.

## <a name="create-the-app-protection-policy"></a>Az alkalmazásvédelmi szabályzat létrehozása
Ebben az oktatóanyagban állítunk be az Outlook alkalmazás az alkalmazási szintű védelmet bevezetni az Intune alkalmazásvédelmi szabályzat. Mi lesz PIN-kódot, nyissa meg az alkalmazást munkahelyi környezetben. Azt fogjuk is korlátozhatja az adatok megosztása az alkalmazások között, és megakadályozza, hogy a vállalati adatokat a személyes helyre való mentését.

1. Jelentkezzen be a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) , majd **ügyfélalkalmazás** > **alkalmazásvédelmi szabályzatok** > **szabályzat létrehozása**.  
2. Adja meg a következő beállítást:  
   - **Név**: Adja meg **Outlook alkalmazás házirend tesztelése**.  
   - **Description** (Leírás): Adja meg **Outlook alkalmazás házirend tesztelése**.  
   - **Platform**: Válassza ki **iOS**.  
   - **Minden alkalmazástípusra cél**: Válassza ki **nem**, majd **alkalmazástípusok**, jelölje be a **nem felügyelt eszközökön futó alkalmazások**.  
3. Válassza ki **alkalmazások**. Az alkalmazások listájában jelölje ki a **Outlook**, és válassza a **kiválasztása**.
4. Válassza ki **beállítások** a beállítások panel megnyitásához. 
5. A beállítások panelen válassza ki a **adatvédelem**. A Data protection panelen alábbi *adatátviteli*, ebben az oktatóanyagban a következő beállításokat:

   - A **Org küldhet adatokat más alkalmazásokból**válassza **None**.  
   - A **fogadhat adatokat más alkalmazásokból**válassza **None**.  
   - A **szervezeti adatok másolatának mentése**válassza **blokk**.  
   - A **Kivágás, másolás és beillesztés más alkalmazások között**válassza **letiltott**. 
   - Hagyja a többi beállítás az alapértelmezett értéken. 
   
   ![Válassza ki az Outlook alkalmazás alkalmazásvédelmi szabályzat adatáthelyezési beállítások](media/tutorial-protect-email-on-unmanaged-devices/data-protection-settings.png)

   Válassza ki **OK** térjen vissza a beállítások panel.  

6. Válassza ki **a hozzáférési követelmények** , majd konfigurálja a következő beállításokat:  

   - A **hozzáférési PIN-kód**válassza **megkövetelése**.
   - A **munkahelyi vagy iskolai fiók hitelesítő adatait a hozzáféréshez**válassza **megkövetelése**.
   - Hagyja a többi beállítás az alapértelmezett értéken.
 
    ![Válassza ki az Outlook alkalmazás alkalmazásvédelmi szabályzat hozzáférési műveletek](media/tutorial-protect-email-on-unmanaged-devices/access-requirements-settings.png)

    Válassza ki **OK** térjen vissza a beállítások panel.  

7. A beállítások panelen válassza ki a **OK**, majd a szabályzat létrehozás panelen válassza ki **létrehozás**.

Az Outlook az alkalmazásvédelmi szabályzat jön létre. Ezt követően kell beállítani a feltételes hozzáférés az eszközök használata az Outlook alkalmazás megkövetelése.

## <a name="create-conditional-access-policies"></a>Feltételes hozzáférési szabályzatok létrehozása
Most, hogy biztosítsák az összes eszközplatformot két feltételes hozzáférési szabályzatok hozunk létre.  

- Az első házirend, hogy a Modern hitelesítési ügyfelek a jóváhagyott Outlook alkalmazás és a többtényezős hitelesítés (MFA) használata szükséges. Modern hitelesítési ügyfelek például az Outlook iOS-hez és Androidhoz készült Outlook.  

- A második házirend szükséges, hogy az Exchange ActiveSync-ügyfelek az engedélyezett az Outlook alkalmazás használata. (Jelenleg az Exchange Active Sync nem támogatja a feltételek eszközplatform kivételével). Konfigurálhatja a feltételes hozzáférési szabályzatokat az Azure AD portálon vagy az Intune-portálon. Mivel már az Intune portálon vagyunk, itt fogjuk létrehozni a szabályzatot.  

### <a name="create-an-mfa-policy-for-modern-authentication-clients"></a>Az MFA-szabályzat létrehozása a Modern hitelesítési ügyfelek  

1. Válassza ki az Intune-ban **feltételes hozzáférési** > **házirendek** > **új szabályzat**.  

2. A **neve**, adja meg **házirend tesztelése a modern hitelesítési ügyfelek**.  

3. A **Hozzárendelések** alatt válassza a **Felhasználók és csoportok** lehetőséget. A **Belefoglalás** lapon válassza a **Minden felhasználó** lehetőséget, majd a **Kész** elemet.

4. A **hozzárendelések**válassza **alkalmazások vagy műveleteket a felhő**. Mivel az Office 365 Exchange Online e-mailjeit szeretnénk megvédeni, a következő lépések segítségével választhatjuk ki:  
     
   1. A **Belefoglalás** lapon válassza az **Alkalmazások kiválasztása** elemet.  
   2. Válassza a **Kiválasztás** lehetőséget  
   3. Az alkalmazások listájában jelölje ki a **Office 365 Exchange Online**, és válassza a **válassza**.  
   4. Válassza ki **kész** térjen vissza az új szabályzat paneljén.  
  
   ![Az Office 365 Exchange Online alkalmazás kiválasztása](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-cloud-apps.png)

5. A **Hozzárendelések** alatt válassza a **Feltételek** > **Eszközplatformok** lehetőséget.  
   1. A **Konfigurálás** alatt válassza az **Igen** lehetőséget.  
   2. Az a **Belefoglalás** lapon jelölje be **bármilyen eszközön**.  
   3. Válassza a **Done** (Kész) lehetőséget.  
   
6. Az a **feltételek** ablaktáblán válassza **ügyfélalkalmazás**.  
   1. A **Konfigurálás** alatt válassza az **Igen** lehetőséget.  
   2. Válassza ki **mobilalkalmazások és asztali ügyfelek** és **Modern hitelesítési ügyfelek**.  
   3. Törölje a többi jelölőnégyzet jelölését.  
   4. Válassza ki **kész** > **kész** térjen vissza az új szabályzat paneljén.  

   ![Az Office 365 Exchange Online alkalmazás kiválasztása](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-client-apps.png)

7. A **Hozzáférés-vezérlés** alatt válassza ki az **Engedélyezés** elemet. 
     
   1. Az **Engedélyezés** lapon válassza az **Engedélyek megadása** lehetőséget.
   2. Válassza ki **többtényezős hitelesítés megkövetelése**.
   3. Válassza ki a **Jóváhagyott ügyfélalkalmazás megkövetelése** elemet.
   4. A **Több vezérlő esetén** elem alatt válassza a **minden kiválasztott vezérlő megkövetelésére** szolgáló lehetőséget. Ez a beállítás biztosítja, hogy mindkét kiválasztott követelmény érvényben legyen, amikor egy eszköz hozzá próbál férni az e-mailekhez.
   5. Válassza a **Kiválasztás** lehetőséget
     
   ![Az Office 365 Exchange Online alkalmazás kiválasztása](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-mfa.png)

7. Alatt **házirend engedélyezése**válassza **a**, majd válassza ki **létrehozás**.  
     
    ![Az Office 365 Exchange Online alkalmazás kiválasztása](media/tutorial-protect-email-on-unmanaged-devices/enable-policy.png)  

A Modern hitelesítési ügyfelek feltételes hozzáférési szabályzat jön létre. Most már létrehozhat egy szabályzatot Exchange ActiveSync-ügyfelek.

### <a name="create-a-policy-for-exchange-active-sync-clients"></a>Hozzon létre egy házirendet az Exchange Active Sync-ügyfelek  
1. Válassza ki az Intune-ban **feltételes hozzáférési** > **házirendek** > **új szabályzat**.  
2. A **neve**, adja meg **Tesztszabályzat EAS-ügyfelek**.  
3. A **Hozzárendelések** alatt válassza a **Felhasználók és csoportok** lehetőséget.  
4. A *Belefoglalás* lapon válassza a **Minden felhasználó** lehetőséget, majd a **Kész** elemet.  

5. A **hozzárendelések**válassza **alkalmazások vagy műveleteket a felhő**. Válassza ki az Office 365 Exchange Online e-mailt a következő lépésekkel:  
   1. A *Belefoglalás* lapon válassza az **Alkalmazások kiválasztása** elemet.  
   2. Válassza a **Kiválasztás** lehetőséget  
   3. Listájából *alkalmazások*válassza **Office 365 Exchange Online**, és válassza a **válassza**, majd **kész**.  
  
6. A **Hozzárendelések** alatt válassza a **Feltételek** > **Eszközplatformok** lehetőséget.  
   1. A **Konfigurálás** alatt válassza az **Igen** lehetőséget.  
   2. Az a **Belefoglalás** lapon jelölje be **bármilyen eszközön**, majd válassza ki **kész**.  

7. Az a **feltételek** ablaktáblán válassza **ügyfélalkalmazás**.  
   1. A **Konfigurálás** alatt válassza az **Igen** lehetőséget.  
   2. Válassza ki **mobilalkalmazások és asztali ügyfelek**.  
   3. Válassza ki **Exchange ActiveSync-ügyfelek** és **házirend alkalmazása csak a támogatott platformok**.  
   4. Az összes többi jelölőnégyzet jelölését törölje.  
   5. Kattintson a **Kész**, majd ismét a **Kész** gombra.  
    
   ![Az Office 365 Exchange Online alkalmazás kiválasztása](media/tutorial-protect-email-on-unmanaged-devices/eas-client-apps.png)  

7. A **Hozzáférés-vezérlés** alatt válassza ki az **Engedélyezés** elemet.  
   1. Az **Engedélyezés** lapon válassza az **Engedélyek megadása** lehetőséget.  
   2. Válassza ki a **Jóváhagyott ügyfélalkalmazás megkövetelése** elemet. Az összes többi jelölőnégyzet jelölését törölje.  
   3. Válassza a **Kiválasztás** lehetőséget  
     
   ![Az Office 365 Exchange Online alkalmazás kiválasztása](media/tutorial-protect-email-on-unmanaged-devices/eas-grant-access.png)  

8. A **Szabályzat engedélyezése** alatt válassza a **Bekapcsolás** elemet.  

9. Kattintson a **Létrehozás** gombra.  

Az alkalmazásvédelmi szabályzatok és a feltételes hozzáférés mostantól vannak érvényben, és készen áll teszteléséhez.  

## <a name="try-it-out"></a>Próbálja ki!  
A létrehozott szabályzatok az eszközök regisztrálása az Intune-ban, és az Outlook mobilalkalmazást az Office 365 e-mailek elérését kell. A forgatókönyv teszteléséhez egy iOS-eszközön próbáljon meg a tesztelési bérlő egyik felhasználójának hitelesítő adataival bejelentkezni az Exchange Online-ra.  
1. iPhone-on történő teszteléshez válassza a **Beállítások** > **Jelszavak és fiókok** > **Fiók hozzáadása** > **Exchange** elemet.  
2. Adja meg a tesztelési bérlő felhasználójának e-mail-címét, és válassza a **Tovább** gombot.  
3. Válassza a **Bejelentkezés** elemet.  
4. Adja meg a tesztfelhasználó jelszavát, és válassza a **Bejelentkezés** gombot.  
5. Az üzenet **további információra szükség** jelenik meg, ami azt jelenti, hogy kéri, hogy többtényezős hitelesítés beállítása. Lépjen tovább, és állítsa be további hitelesítési módszer.  
6. Ezután megjelenik egy üzenetet arról, hogy a próbál megnyitni ezt az erőforrást, hogy az informatikai részleg által nem engedélyezett. Az üzenet azt jelenti, hogy hozzáférése blokkolva van, a natív e-mail alkalmazással. A bejelentkezés megszakítása.  
7. Nyissa meg az Outlookot és **beállítások** > **fiók hozzáadása** > **E-mail-fiók hozzáadása**.  
8. Adja meg a tesztelési bérlő felhasználójának e-mail-címét, és válassza a **Tovább** gombot.  
9. Nyomja meg **jelentkezzen be az Office 365**. Kérni fogja a további hitelesítési és nyilvántartási. Miután bejelentkezett, tesztelheti a műveleteket, mint például a kivágási, másolási, beillesztési és "Mentés másként".  

## <a name="clean-up-resources"></a>Az erőforrások eltávolítása  
Ha már nincs szükség a tesztszabályzatokra, eltávolíthatja őket.  
1. Jelentkezzen be az [Intune-ba](https://go.microsoft.com/fwlink/?linkid=2090973) globális rendszergazdaként vagy Intune-beli szolgáltatásadminisztrátorként.  
2. Válassza az **Eszközmegfelelőség** > **Szabályzatok** elemet.  
3. A **Szabályzat neve** listában válassza a tesztszabályzat helyi menüjét ( **...** ), majd válassza a **Törlés** elemet. Válassza az **OK** lehetőséget a megerősítéshez.  
4. Válassza a **Feltételes hozzáférés** > **Szabályzatok** elemet.  
5. Az a **házirendnév** listájához, válassza ki a helyi menüt ( **...** ) a tesztszabályzattal, és válassza ki az egyes **törlése**. Válassza az **Igen** lehetőséget a megerősítéshez.  

## <a name="next-steps"></a>További lépések  
Ebben az oktatóanyagban létrehozott alkalmazásvédelmi szabályzatok korlátozni, mi a felhasználó visszaállíthatja-e az Outlook alkalmazással, és az Outlook alkalmazás megkövetelése és a többtényezős hitelesítés megkövetelése a Modern hitelesítési ügyfelek feltételes hozzáférési szabályzatok létrehozott. Feltételes hozzáférés az Intune használatát más alkalmazások és szolgáltatások védelmét kapcsolatos további információkért lásd: [feltételes hozzáférés beállítása](conditional-access.md).

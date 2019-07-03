---
title: Hogyan kell bejelentkezni a Céges portál alkalmazásba | Microsoft Docs
description: Információk arról, hogyan lehet bejelentkezni a Céges portál alkalmazásba különféle platformokon.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: cfd214bc-f072-4808-af2e-a3cbf7af9bca
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6bfd8496061b4b3aba2589b73c3e98bce94a5011
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67528649"
---
# <a name="sign-in-to-company-portal"></a>Jelentkezzen be céges portál  

Jelentkezzen be a vállalati portál alkalmazást a három módja van:

* Jelentkezzen be a munkahelyi e-mail címét és jelszavát.  
* Jelentkezzen be a tanúsítvány alapú hitelesítést.  
* Bejelentkezés másik eszközről.    


## <a name="sign-in-with-your-email-address-and-password"></a>Jelentkezzen be az e-mail cím és jelszó
A következő lépések bemutatják a képernyőképek a vállalati portál iOS-hez.  

1. Nyissa meg az alkalmazást az eszközön, és koppintson **bejelentkezés**.  

   ![A Céges portál bejelentkezési oldala, amelyen egy webhely rajza előtt látható egy ember ikonja. Alatta a "Férjen hozzá a vállalati erőforrásokhoz, és megőrizheti azok biztonságát" szöveg, de a "Bejelentkezés" gomb. Az oldal alján látható egy hivatkozás, amely a Microsoft Adatvédelem és cookie-k oldalára mutat.](/intune-user-help/media/cp_ios_aad_signin_after_1804_001.png)



2. Adja meg **munkahelyi vagy iskolai fiókját**, és koppintson a **Tovább** lehetőségre.

   ![A felhasználónak ugyanazon az oldalon csak az e-mail-címét kell megadnia, nem pedig mind az e-mail-címét, mind a jelszavát.](/intune-user-help/media/cp_ios_aad_signin_after_1804_002.png)

3. Adja meg a jelszót, majd koppintson a **Bejelentkezés** elemre.

   ![A felhasználótól csak akkor kéri a rendszer a jelszavát ha már helyesen megadta az e-mail-címét.](/intune-user-help/media/cp_ios_aad_signin_after_1804_003.png)

4. Az alkalmazás ellenőrzi, hogy a hitelesítő adatait. Ha elkészült, a munkahelyi erőforrások eléréséhez, és kereshessék az alkalmazásokat.  

   ![Miután a hitelesítési folyamaton keresztül, a vállalati portál alkalmazás bejelentkezik, egy betöltési sáv jeleníti meg.](/intune-user-help/media/cp_ios_aad_signin_after_1804_004.png)

## <a name="sign-in-with-certificate-based-authentication"></a>Jelentkezzen be a Tanúsítványalapú hitelesítés

1. Nyissa meg az eszközén a Céges portál alkalmazást.  

2. Adja meg a **munkahelyi vagy iskolai fiókját**.  

3. Koppintson a **Bejelentkezés tanúsítvánnyal** lehetőségre.  

4. A tanúsítvány használatához koppintson a **Folytatás** lehetőségre.  

## <a name="sign-in-from-another-device"></a>Bejelentkezés másik eszközről

Ha a vállalat intelligens kártyákat használ a számítógépek eléréséhez, valószínű, hogy jelentkezzen be a másik eszközről történő hitelesítéséhez.  

1. Nyissa meg az eszközén a Céges portál alkalmazást. Győződjön meg arról, hogy az eszköz a munkahelyi erőforrások eléréséhez fog használni.       

1. Válassza ki **bejelentkezés másik eszközről**.  

   ![A céges portál bejelentkező oldala kéri a felhasználó e-mail-cím.  A Next (Tovább) gombra, és a egy hivatkozás látható a "Bejelentkezés másik eszközről." Tartalmaz egy „Nem tud hozzáférni a fiókjához?” hivatkozást is. Az oldal alján látható egy hivatkozás, amely a Microsoft Adatvédelem és cookie-k oldalára mutat.](/intune-user-help/media/cp_ios_aad_signin_after_1804_005.png)

2. Ekkor egy egyedi, egyszer használatos kódot kap a Céges portálra történő bejelentkezéshez. A kód másolásához.

   ![A rendszer arra kéri a felhasználót, hogy látogassa meg az https://microsoft.com/devicelogin oldalt a munkahelyi számítógéphez tartozó, megjelenített egyedi kódot használva a bejelentkezéshez.](/intune-user-help/media/cp_ios_aad_signin_after_1804_006.png)

3. Az eszközön más (a hitelesítéshez használ egy), nyissa meg a böngészőt, és nyissa meg [ https://microsoft.com/devicelogin ](https://microsoft.com/devicelogin). Írja be vagy illessze be a kódot.  

   ![A felhasználó munkagépén futó böngészőablak képe (nem pedig a Céges portál alkalmazásé). A megjelenített „Eszközbejelentkezés” oldal arra kéri a felhasználót, hogy adja meg a Céges portál alkalmazástól kapott kódot.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

4. Válassza ki __Folytatás__ , hogy jelentkezzen be a munkahelyi eszközét a céges portál.   

   ![A felhasználó beírta a mezőbe az egyedi kódját, az „Eszközbejelentkezés” webhely pedig a felhasználó megerősítését kéri, hogy az Intune Céges portálnak kell-e bejelentkezési engedélyt kapnia.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

5. A kód ellenőrzése után bezárhatja az ablakot.  

   ![Jóváhagyást jelző oldal, amely megerősíti, hogy a felhasználó bejelentkezett a Céges portál alkalmazásra az eszközén, és hogy ez az oldal bezárható.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

6. A vállalati portál alkalmazás bejelentkezik a munkahelyi eszközén.  

   ![Miután a hitelesítési folyamat lezárult, bejelentkezik a Céges portál alkalmazás, és a folyamatot egy betöltést jelző sáv mutatja.](/intune-user-help/media/cp_ios_aad_signin_after_1804_007.png)

További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).  

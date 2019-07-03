---
title: Android-eszköz regisztrációjának törlése az Intune-ból | Microsoft Docs
description: Androidos eszköz regisztrációjának törlése az Intune vállalati portál
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f40aab26-7613-48cc-a74e-de83df9465a4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: b68ea31a6c5d902e66c0eda8127e0f68383910f8
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67529132"
---
# <a name="unenroll-your-android-device-from-management"></a>Android-eszköz regisztrációjának törlése  

Regisztrált Android-eszköz eltávolítása a szervezet által felügyelt eszközök közül. Ez a cikk azt ismerteti, hogyan távolíthatja el az eszközt a Céges portál alkalmazásból. Miután eltávolította az eszközt:  

* Az eszköz nem fogja tudni elérni a szervezet védett adatait és erőforrásait.
* Az eszköz nem fog megjelenni a Céges portálon.
* Nem telepíthet alkalmazásokat a Céges portálról.
* Az eszközön annak regisztrálásakor módosult beállítások (például a kamera letiltása vagy meghatározott hosszúságú jelszó megkövetelése) hatályukat vesztik.  

> [!NOTE]
> Nem regisztrációját, és nem a vállalat által birtokolt eszközök eltávolítása a Microsoft Intune app. Az eszköz regisztrálva lett a kezdeti Eszközbeállítás során, és regisztrálva kell lenniük a szervezet erőforrásaihoz.  

1. A Céges portálon koppintson a jobb felső sarokban található három függőleges pontra. Megnyílik a műveletmenü.

   ![Az androidhoz készült céges portál alkalmazást, a jobb felső sarokban a megnyitott művelet menü képernyőképe. A „Saját profil” és a „beállítások” lehetőség alatt harmadikként megjelenik az új „céges portál eltávolítása” lehetőség is, alatta a „használati feltételek”, a „súgó és visszajelzés” és végül a „névjegy”.](./media/android_remove_cp_menu_action_after_1705.png)

2. Koppintson a **Céges portál eltávolítása** elemre.  

3. Megjelenik egy üzenet, amely tájékoztatja arról, mi történik, ha törli az eszköz regisztrációját. Koppintson az **OK** lehetőségre annak megerősítéséhez, hogy eltávolítja az eszközt a Céges portálról.

   ![A megerősítés megjelenő műveleti menüben az új "Céges portál eltávolítása" lehetőség kiválasztása után rendelkezésre álló képernyőképe.](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="remove-data-collected-by-the-company-portal-app"></a>A vállalati portál alkalmazás által gyűjtött adatok eltávolítása  

Az Android-eszközhöz készült Céges portál alkalmazás által az eszközön tárolt adatok törlésének módja a következő:

- Alkalmazások adatainak törlése elemre koppintva **alkalmazások** >  **[*nevű alkalmazás*]**  > **adat törlése**.
- Törölje a következő mappát: \storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal.

## <a name="uninstall-the-company-portal-app"></a>A Céges portál alkalmazás eltávolítása  
Céges portál egy eszközfelügyeleti alkalmazáshoz. Azt nem lehet eltávolítani, amíg nem törli a felügyelet alól az eszköz regisztrációját. Miután ezt megtette, koppintson a Céges portál alkalmazás ikonjára, és tartsa nyomva addig, amíg az **Eltávolítás** lehetőség meg nem jelenik. Koppintson az **Eltávolítás** lehetőségre az alkalmazás eszközről való eltávolításához.  

Azt is megteheti, koppintson **beállítások** > **alkalmazások** > **céges portál** > **Eltávolítás**.  

### <a name="remove-the-company-portal-app-as-a-device-administrator"></a>Eszköz-rendszergazdaként a vállalati portál alkalmazás eltávolítása  
Végső megoldásként a eszközadminisztrátorként eltávolíthatja az alkalmazást az eszközről.  

Ha a vállalat által birtokolt eszközök, a szervezet előfordulhat, hogy követelmény, hogy vállalati portál az eszközön mindig. Ha eltávolítja, akkor előfordulhat, hogy férhet hozzá, védett vállalati erőforrásokba, például e-mail, alkalmazások, Wi-Fi vagy VPN-, mindaddig, amíg az alkalmazás újratelepítése után. Telepítésével kapcsolatos további információkért frissítése, vagy távolítsa el a kötelező alkalmazásokat, lásd: [alkalmazások hozzáadása Microsoft Intune-bA](https://docs.microsoft.com/intune/apps-add#apps-that-are-added-automatically-by-intune).  

Itt látható, hogyan tilthatja le a céges portál egy eszköz rendszergazdaként. Tényleges nevét, az egyes beállítások az Android-eszközön eltérő lehet.  

**1. lehetőség**:  
1. Válassza ki **beállítások** > **biztonsági** > **további biztonsági beállítások** > **Eszközadminisztrátorok** .  
2. Törölje a **céges portál** kiválasztása.  

**2. lehetőség**:  
1. Válassza ki **beállítások** > **zárolási képernyő és biztonság** > **további biztonsági beállítások** > **Eszközfelügyelet alkalmazások**.  
2. Törölje a **céges portál** kiválasztása.    

További segítségre van szüksége? Forduljon a cég informatikai támogatásához. Az elérhetőségét keresse meg a [Vállalati portál webhelyén](https://go.microsoft.com/fwlink/?linkid=2010980).

---
title: "E-mail-beállítások az Intune-ban iOS-eszközök esetén"
titleSuffix: Intune Azure preview
description: "Intune az Azure-on – előzetes: Útmutató az e-mail-kapcsolatok iOS-eszközökön való konfigurálásához használható Intune-beállításokról."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9f0fa6af-3669-439a-bd0d-75d8b1a0b135
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 78f99bba07180c06f979fec997a7bfb749d879c8
ms.openlocfilehash: f18fd3ceee5c73a96444092691c590c7d9a7419c
ms.lasthandoff: 02/24/2017


---

# <a name="email-profile-settings-for-ios-devices-in-microsoft-intune"></a>iOS-eszközökre vonatkozó e-mail-profilbeállítások a Microsoft Intune-ban

[!INCLUDE[azure_preview](../includes/azure_preview.md)]



- **E-mail-kiszolgáló** – Itt adja meg az Exchange-kiszolgáló állomásnevét.
- **Fióknév** – Adja meg az e-mail-fiók megjelenítendő nevét (ez lesz látható a felhasználók eszközén).
- **Felhasználónév attribútum az AAD-ből** – Ez az Active Directory (AD) vagy az Azure AD egy attribútuma, ennek alapján fogja generálni a rendszer ennek az e-mail-profilnak a felhasználónevét. Válassza az **Elsődleges SMTP-cím** (például **user1@contoso.com**) lehetőséget, vagy az **Egyszerű felhasználónév** (például **user1** vagy **user1@contoso.com**) lehetőséget.
- **E-mail-cím attribútuma az AAD-ből** – Válassza ki, hogyan jöjjön létre a felhasználói e-mail-cím az egyes eszközökön. Ha az elsődleges SMTP-címmel kíván bejelentkezni az Exchange-be, válassza az **Elsődleges SMTP-cím** lehetőséget; ha a teljes egyszerű felhasználónevet kívánja használni e-mail-címként, válassza az **Egyszerű felhasználónév** lehetőséget.
- **Hitelesítési módszer** – Az e-mail-profil által használandó hitelesítési módszernek válassza a **Felhasználónév és jelszó** vagy a **Tanúsítványok** lehetőséget.
    - Ha a **Tanúsítványok** lehetőséget választotta, válassza ki az ügyfél korábban létrehozott SCEP- vagy PKCS-tanúsítványát, amelyet az Exchange-kapcsolat hitelesítésére kíván használni.
- **SSL** – SSL-kommunikáció használata az e-mailek küldésekor és fogadásakor, valamint az Exchange-kiszolgálóval való kommunikációhoz.
- **S/MIME** – Kimenő e-mailek küldése S/MIME aláírással.
    - Ha a **Tanúsítványok** lehetőséget választotta, válassza ki az ügyfél korábban létrehozott SCEP- vagy PKCS-tanúsítványát, amelyet az Exchange-kapcsolat hitelesítésére kíván használni.
- **Szinkronizálandó e-mailek mennyisége** – Válassza ki, hogy hány napra visszamenőleg szeretné szinkronizálni az e-maileket, vagy az összes e-mail szinkronizálásához válassza a **Korlátlan** lehetőséget.
- **Üzenetek más e-mail fiókba való áthelyezésének engedélyezése** – Lehetővé teszi a felhasználóknak az e-mailek áthelyezését az eszközön konfigurált más fiókokba.
- **E-mailek küldésének engedélyezése külső gyártótól származó alkalmazásokból** – A felhasználók kiválaszthatják alapértelmezett e-mail-küldési fiókként ezt a profilt, és engedélyezhetik a külső alkalmazások számára az e-maileknek a natív e-mail alkalmazásban történő megnyitását, például fájlok e-mailhez való csatolásához.
- **Utoljára használt e-mail címek szinkronizálása** – Ezzel a funkcióval a felhasználók szinkronizálni tudják az eszközön utoljára használt e-mail címek listáját a kiszolgálóval.

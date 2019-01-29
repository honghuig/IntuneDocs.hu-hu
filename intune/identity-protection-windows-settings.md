---
title: Windows Hello for Business beállításai a Microsoft Intune – Azure |} A Microsoft Docs
description: Megjelenítheti az összes PIN-kód, biometrikus, és az identity protection profilban hamisításszűrés beállítások használata és konfigurálása Windows Hello for Business a Microsoft Intune-ban Windows 10-eszközök listáját.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b5eb25c48e3724fdc9277a790d01908e976c75be
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831678"
---
# <a name="windows-10-and-newer-device-settings-to-enable-windows-hello-for-business-in-intune"></a>A Windows 10 (és újabb) eszközbeállítások engedélyezése Windows Hello for Business az Intune-ban

Ez a cikk felsorolja és ismerteti a Windows Hello for Business beállításaival szabályozhatja az Intune-ban Windows 10 rendszerű eszközökön. A mobileszköz-felügyelet (MDM) megoldás részeként használja ezeket a beállításokat, jelentkezzen be a PIN-kód vagy ujjlenyomat használatával és egyéb.

Intune-rendszergazdák hozzon létre, és ezek a beállítások hozzárendelése Windows 10-es és újabb rendszerű eszközök.

Tudjon meg többet a Windows Hello-profilok az Intune-ban, tekintse meg [identity protection konfigurálása](identity-protection-configure.md).

## <a name="before-you-begin"></a>Előkészületek

[Hozzon létre egy konfigurációs profil](identity-protection-configure.md#create-the-device-profile).

## <a name="windows-hello-for-business"></a>Vállalati Windows Hello

- **A vállalati Windows Hello konfigurálása**: Ezzel a szolgáltatással és a beállítások megadásához válassza a **engedélyezése**.
- **PIN kód minimális hosszának**: Adja meg a minimális PIN kód hossz szeretné lehetővé tenni az eszközök számára. Az alapértelmezett PIN-kód hossza 6 karakter. A minimális PIN-kód hossza négy (4) karakter lehet.
- **PIN-kód maximális hosszának**: Adja meg a PIN kód maximális hosszának szeretné lehetővé tenni az eszközök számára. Az alapértelmezett PIN-kód hossza hat (6) karakter lehet. A PIN-kód legfeljebb 127 karakter hosszú lehet.  
- **Kisbetűk használata a PIN-kód**: Erősebb PIN-kód kényszerítheti a végfelhasználók által kisbetűket tartalmazza. A választható lehetőségek:

  - **Nem engedélyezett** (alapértelmezett): Felhasználók blokkolása a kisbetűk használatát a PIN-kódban. Ez a viselkedés akkor is előfordul, ha a beállítás nincs konfigurálva.
  - **Engedélyezett**: Engedélyezése a felhasználóknak a kisbetűk használata a PIN-kódban, de ez nem szükséges.
  - **Szükséges**: Felhasználók tartalmaznia kell legalább egy kisbetű a PIN-kódban. Például általános gyakorlat legalább egy nagybetű és egy speciális karakter megkövetelése.

- **Nagybetűk használata a PIN-kód**: Erősebb PIN-kód kényszerítheti a végfelhasználók által közé tartozik a nagybetűk. A választható lehetőségek:

  - **Nem engedélyezett** (alapértelmezett): Felhasználók blokkolása a nagybetűk használatát a PIN-kódban. Ez a viselkedés akkor is előfordul, ha a beállítás nincs konfigurálva.
  - **Engedélyezett**: Engedélyezése a felhasználóknak a nagybetűk használata a PIN-kódban, de ez nem szükséges.
  - **Szükséges**: Felhasználók tartalmaznia kell legalább egy nagybetű a PIN-kódban. Például általános gyakorlat legalább egy nagybetű és egy speciális karakter megkövetelése.

- **Speciális karakterek a PIN-kód**: Erősebb PIN-kód azzal, hogy a végfelhasználók kényszerítheti a különleges karaktereket. A választható lehetőségek:

  - **Nem engedélyezett** (alapértelmezett): Felhasználók blokkolása a speciális karakterek a PIN-kód használatát. Ez a viselkedés akkor is előfordul, ha a beállítás nincs konfigurálva.
    Speciális karakterek a következők: `! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~`
  - **Engedélyezett**: Engedélyezése a felhasználóknak a nagybetűk használata a PIN-kódban, de ez nem szükséges.
  - **Szükséges**: Felhasználók tartalmaznia kell legalább egy nagybetű a PIN-kódban. Például általános gyakorlat legalább egy nagybetű és egy speciális karakter megkövetelése.

- **PIN-kód lejárata (nap)**: A PIN-kódhoz célszerű lejárati időt megadni, amelynek eltelte után a felhasználóknak módosítaniuk kell a PIN-kódot. Az alapértelmezett érték 41 nap.

- **PIN-előzmények megjegyzése**: Korlátozza a korábban használt PIN-kódok ismételt használatát. Alapértelmezés szerint az utolsó 5 PIN-kód nem használható fel újra.  
- **Helyreállítási PIN-kód engedélyezése**: A felhasználó a PIN-KÓDJUKAT használatával a Windows Hello PIN-KÓDJÁBAN recovery szolgáltatáshoz.

       - **Enable**: The cloud service encrypts a PIN recovery secret to store on the device. The user can change their PIN if needed.  
       - **Not configured** (default): A PIN recovery secret is not created or stored. If the user's PIN is forgotten, the only way to get a new PIN is by deleting the existing PIN and creating a new one. The user will need to re-register with any services the old PIN provided access to.  

- **Platformmegbízhatósági modul (TPM) használata**: A TPM lapka használata további adatbiztonsági réteget biztosít. Válasszon egyet az alábbi lehetőségek közül:  
  - **Engedélyezése**: A Vállalati Windows Hello csak az elérhető TPM modullal rendelkező eszközökön építhető ki.
  - **Nincs konfigurálva**: A Vállalati Windows Hello minden eszközön telepíthető, még akkor is, ha nincs használható TPM. Az eszközök először megpróbálják a TPM-et használni, de ha nem áll rendelkezésre, akkor szoftveres titkosítást alkalmaznak.  

- **Biometrikus hitelesítés engedélyezése**: Lehetővé teszi a biometrikus hitelesítést, például az arcfelismerést vagy az ujjlenyomat használatát a PIN-kód alternatívájaként a Vállalati Windows Hello szolgáltatásban. A felhasználóknak ekkor is be kell állítaniuk egy PIN-kódot arra az esetre, ha a biometrikus hitelesítés nem sikerül. A következő lehetőségek közül választhat:

  - **Engedélyezése**: A Vállalati Windows Hello lehetővé teszi a biometrikus hitelesítést.
  - **Nincs konfigurálva** (alapértelmezett): A Vállalati Windows Hello meggátolja a biometrikus hitelesítést (minden fióktípus esetében).

- **Használja a hamisítások kibővített szűrését, ha elérhető**: Válassza ki, ha hamisításszűrés Windows Hello hamisításszűrési funkcióit használják az azt támogató eszközökön. Ha például észleli egy arcról egy valós arc helyett.

  - **Engedélyezése**: A Windows minden felhasználótól megköveteli a kibővített hamisításszűrés alkalmazását arcfelismerés esetén, ha az támogatott.  
  - **Nincs konfigurálva** (alapértelmezett): A Windows figyelembe veszi a hamisításszűrési konfigurációkat az eszközön.

- **A tanúsítvány a helyi erőforrások**: 

  - **Engedélyezése**: Engedélyezi a Vállalati Windows Hello számára, hogy tanúsítványokkal végezzen hitelesítést a helyszíni erőforrásokban.
  - **Nincs konfigurálva** (alapértelmezett): Megakadályozz, hogy a Vállalati Windows Hello tanúsítványokkal végezzen hitelesítést a helyszíni erőforrásokban.  

## <a name="next-steps"></a>További lépések

[Rendelje hozzá a profilt](device-profile-assign.md), és [kövesse nyomon az állapotát](device-profile-monitor.md).
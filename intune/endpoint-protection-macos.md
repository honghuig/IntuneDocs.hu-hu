---
title: Végpontvédelem hozzáadása macOS rendszeren az Azure-beli Microsoft Intune-ban | Microsoft Docs
description: macOS rendszerű eszközökön használjon forgalomirányítót annak meghatározására, hogy honnan lehet alkalmazásokat telepíteni, beleértve a Mac App Store áruházat is. Engedélyezzen vagy konfiguráljon tűzfalat is egyes alkalmazások engedélyezésére, alkalmazások tiltására, rejtett üzemmód használatára vagy akár bizonyos bejövő kapcsolattípusok tiltására a Microsoft Intune használatával.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3a885abfdd7f23f453f03c63fdb0086bed40a7b1
ms.sourcegitcommit: c3a4fefbac8ff7badc42b1711b7ed2da81d1ad67
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375037"
---
# <a name="macos-endpoint-protection-settings-in-intune"></a>MacOS Endpoint Protection-beállítások az Intune-ban  

Ez a cikk a macOS-t futtató eszközökhöz konfigurálható Endpoint Protection-beállításokat ismerteti. Ezeket a beállításokat [MacOS-eszköz](endpoint-protection-configure.md) konfigurációs profiljának használatával konfigurálhatja az Intune-ban.  

## <a name="gatekeeper"></a>Forgalomirányító  

- **Ezen helyekről letöltött alkalmazások engedélyezése**  
  Korlátozza az eszköz által elindítható alkalmazásokat attól függően, hogy az alkalmazások Honnan tölthetők le. A cél az, hogy megvédje az eszközöket a kártevők ellen, és csak a megbízható forrásból származó alkalmazásokat engedélyezze.  

  - **Nincs konfigurálva**  
  - **Mac App Store**  
  - **Mac App Store és ismert fejlesztők**  
  - **Bárhonnan**  

  **Alapértelmezett**: Nincs konfigurálva  

- **A felhasználó felülbírálhatja a forgalomirányítót**  
  Megakadályozza, hogy a felhasználók felülbírálják a forgalomirányító beállítását, és megakadályozza, hogy a felhasználók egy alkalmazás telepítésére rákattintanak. Ha engedélyezve van, akkor a felhasználók bármilyen alkalmazást telepíteni tudnak, ha a Ctrl billentyűt lenyomva rákattintanak.  
 
  - **Nincs konfigurálva** – a felhasználók vezérelhetik az alkalmazások telepítését.  
  - **Letiltás** – megakadályozza, hogy a felhasználók ne használják a vezérlőt – kattintson az alkalmazások telepítéséhez.  

  **Alapértelmezett**: Nincs konfigurálva  

## <a name="firewall"></a>Tűzfal  

A tűzfalat inkább a kapcsolatok alkalmazásonkénti, nem pedig portonkénti korlátozására használja. Az alkalmazásonkénti beállítások használatával könnyebben kihasználhatók a tűzfal védelmének előnyei. Segít annak megelőzésében is, hogy nem kívánt alkalmazások átvegyék a megbízható alkalmazások számára nyitott portok irányítását.  

**Általános**
- **Tűzfal**  
  Engedélyezze a tűzfalat annak konfigurálásához, hogy a rendszer hogyan kezelje a bejövő kapcsolatokat a környezetben.  
  - **Nincs konfigurálva**  
  - **Engedélyezése**  

  **Alapértelmezett**: Nincs konfigurálva  

- **Bejövő kapcsolatok**  
  Letiltja az összes bejövő kapcsolatot, kivéve az alapszintű internetes szolgáltatásokhoz szükséges kapcsolatokat, például a DHCP-t, a Bonjour-t és az IPSec-t. Ez a funkció a megosztási szolgáltatásokat, például a fájlmegosztást és a képernyőmegosztást is letiltja. Ha megosztási szolgáltatásokat használ, hagyja ezt a beállítást a *Nincs konfigurálva* értéken.  
  - **Nincs konfigurálva**  
  - **Tiltás**  

  **Alapértelmezett**: Nincs konfigurálva  

**Adott alkalmazások bejövő kapcsolatainak engedélyezése vagy letiltása.**  

  - **Engedélyezett alkalmazások**  
    Válassza ki azokat az alkalmazásokat, amelyek számára kifejezetten engedélyezett a bejövő kapcsolatok fogadása.  

  - **Blokkolt alkalmazások**  
    Válassza ki azokat az alkalmazásokat, amelyeknek le kell tiltaniuk a bejövő kapcsolatokat.  

  - **Rejtett üzemmód**  
    Ha meg szeretné akadályozni, hogy a számítógép válaszoljon a Szondázási kérelmekre, engedélyezze a rejtett üzemmódot. Az eszköz továbbra is válaszol az engedélyezett alkalmazásoktól érkező kérelmekre. Az olyan váratlan kérelmeket, mint az ICMP (ping), a rendszer figyelmen kívül hagyja.  
    - **Nincs konfigurálva**  
    - **Engedélyezése**  

    **Alapértelmezett**: Nincs konfigurálva  

## <a name="filevault"></a>FileVault  
Az Apple FileVault beállításaival kapcsolatos további információkért lásd: [FDEFileVault](https://developer.apple.com/documentation/devicemanagement/fdefilevault) az Apple fejlesztői tartalomban. 

- **FileVault**  
  A XTS  -AES 128 és újabb rendszerű 10,13 eszközökön a FileVault használatával engedélyezheti a teljes lemezes titkosítást.  
  - **Nincs konfigurálva**  
  - **Engedélyezése**  

  **Alapértelmezett**: Nincs konfigurálva  

  - **Helyreállítási kulcs típusa**  
    A rendszer létrehozza a *személyes kulcs* helyreállítási kulcsait az eszközökhöz. Adja meg a következő beállításokat a személyes kulcshoz.  

    - **Személyes helyreállítási kulcs helye** – adja meg a felhasználó rövid üzenetét, amely elmagyarázza, hogyan kérheti le a személyes helyreállítási kulcsot. A rendszer beszúrja a szöveget a FileVault engedélyezésekor a felhasználó által megjelenő üzenetbe.  
      
    - **Személyes helyreállítási kulcs** elforgatása – Itt adhatja meg, hogy az eszköz személyes helyreállítási kulcsa milyen gyakran legyen elforgatva. Kiválaszthatja a **nincs konfigurálva**beállítás alapértelmezett értékét, vagy **1** és **12** hónap közötti értéket is megadhat.  

  - **FileVault késleltetése a kijelentkezésig**  
    > [!NOTE]
    > A FileVault támogatása korlátozott, amíg a júliusi kiadás befejeződik néhány nap alatt. Amíg a bevezetést be nem fejeződik, a FileVault konfigurálásakor be kell állítania a *késleltetés FileVault, amíg ki nem jelentkezik* az **Engedélyezés**gombra.   

    A FileVault csak akkor lesz engedélyezve, ha a felhasználó kijelentkezik. A rendszer a helyi felhasználó vagy a mobil fiók felhasználójának a kijelentkezéskor vagy a következő bejelentkezéskor fogja kérni a FileVault engedélyezését.  
    - **Nincs konfigurálva**  
    - **Engedélyezése**  
    **Alapértelmezett**: Nincs konfigurálva  



    - **Figyelmeztetés letiltása a kijelentkezéskor**  
      Megakadályozza, hogy a rendszer felszólítsa a felhasználót, hogy engedélyezze a FileVault a kijelentkezéskor.  
      - **Nincs konfigurálva**  
      - **Engedélyezése**  

      **Alapértelmezett**: Nincs konfigurálva  

    - **Megkerülő időpontok száma**  
    Állítsa be, hogy a felhasználó hányszor hagyhatja figyelmen kívül a kéréseket, hogy engedélyezze a FileVault, mielőtt FileVault a felhasználónak a bejelentkezéshez.  

      - **Nincs konfigurálva** – az eszközön a következő bejelentkezés engedélyezése előtt titkosítás szükséges.  
      -  **1** – **10** – lehetővé teszi, hogy a felhasználó 1 – 10 alkalommal figyelmen kívül hagyja a kérést, mielőtt titkosítást kellene megadnia az eszközön.  
      - **Nincs korlát, mindig** Rákérdezés – a rendszer felszólítja a felhasználót, hogy engedélyezze a FileVault, de a titkosítás soha nem szükséges.  
 
      **Alapértelmezett**: Nincs konfigurálva  



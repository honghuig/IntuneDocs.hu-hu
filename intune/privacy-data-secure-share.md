---
title: Adatbiztonság és -megosztás az Intune-ban
description: Ismertető a személyes adatok Intune-beli védelméről és megosztásáról.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 68921fd6-5f50-456c-a3af-83d7bc4b134b
ms.reviewer: angerobe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 085b6a3a68964a200a5d6c462b3710b9744ac99f
ms.sourcegitcommit: 07528df71460589522a2e1b3e5f9ed63eb773eea
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34474615"
---
# <a name="data-security-and-sharing-in-intune"></a>Adatbiztonság és -megosztás az Intune-ban


## <a name="data-security"></a>Adatbiztonság

A Microsoft Intune a Microsoft Enterprise Mobility and Security Suite felhőszolgáltatási ajánlat lényeges része. Az [adatirányítási stratégia](https://www.microsoft.com/en-us/TrustCenter/Security/default.aspx) támogatása érdekében minden Microsoft-felhőszolgáltatást a [Microsoft Privacy](https://www.microsoft.com/en-us/trustcenter/privacy) (adatvédelem) és a [Microsoft Security](https://www.microsoft.com/en-us/trustcenter/security/) (biztonság) módszertan alapján fejlesztünk.  

A Microsoft Intune ugyanazokat a technikai és szervezési elveket követi, amelyeket a Microsoft Azure szervizcsapatai alkalmaznak az adatvédelmi incidensek ellen.

További információ a [Szolgáltatásmegbízhatósági portálon](https://www.microsoft.com/en-us/TrustCenter/stp).

Az Intune olyan adatmennyiség-csökkentő technikákat használ, mint az

- összesítés
- feltételes adatgyűjtés bizonyos funkciókhoz
- adatok pontosságának vagy bizalmasságának csökkentése

Az Intune ezen kívül olyan technikák használatával is gondoskodik az alapértelmezés szerinti adatvédelemről, mint az RBAC és a JiT. 

### <a name="data-breach-reporting"></a>Adatbiztonsági incidens jelentése

Ügyfél által jelenthető biztonsági incidens (CRSI) észlelésekor az ügyfél értesítést kap. Ennek az eljárásnak része a Microsoft O365 csapatával való együttműködés, hogy az incidensről az Intune-t használó Microsoft O365-ügyfelek mindig tájékoztatást kapjanak.

## <a name="data-sharing"></a>Adatok megosztása

Ha egy bérlői rendszergazda bekapcsol bizonyos funkciókat (például az Apple Készülékregisztrációs programot), a Microsoft Intune a rendszergazda jóváhagyását kéri az adatoknak az érintett külső féllel való megosztásához. Ilyen esetben az Intune a következőkkel oszthat meg személyes adatokat:

- A Microsoft ügynökeként eljáró külső fél.
- Nem a Microsoft ügynökeként eljáró külső fél, de csak akkor, ha a bérlői rendszergazdák erre egyértelmű engedélyt adnak az Intune-nak.

A Microsoft ügynökeként eljáró külső felek mindegyike szerepel az [Online szolgáltatások alvállalkozóinak listáján](https://aka.ms/Online_Serv_Subcontractor_List).

Az adatok megosztása ilyen entitásokkal mindig az ügyfél érdekében, műszaki támogatás, szolgáltatás-karbantartás és más műveletek céljából történik.

A külső fél szolgáltatásában tárolt személyes Intune-adatok körét a bérlő és a külső fél közötti szerződés szabja meg. Ez egyben felhatalmazza az Intune-t, hogy személyes adatokat adjon át a külső fél szolgáltatásának.  

Az egyes külső felekkel megosztott adatokról a következő cikkekből tájékozódhat:
- [Az Intune által az Apple-nek küldött adatok](data-intune-sends-to-apple.md)
- [Az Intune által a Google-nek küldött adatok](data-intune-sends-to-google.md)
- [Az Apple által az Intune-nak küldött adatok](data-apple-sends-to-intune.md)
- [A Google által az Intune-nak küldött adatok](data-google-sends-to-intune.md)
- [A Jamf Pro-ból az Intune számára megosztott információk](conditional-access-integrate-jamf.md#information-shared-from-jamf-pro-to-intune)

### <a name="system-center-configuration-manager-data-sharing"></a>Adatmegosztás a System Center Configuration Managerben

A Microsoft Intune semmilyen adatot sem oszt meg a System Center Configuration Managerrel. A Microsoft Intune közvetlenül az ügyfél által telepített, felügyelt és üzemeltetett helyszíni termék. A Configuration Manager által gyűjtött diagnosztikai és használati adatokat kizárólag a telepítési élmény, a minőség és a jövőbeli kiadások biztonságának javításához használja fel.

További információ: [Diagnosztikai és használati adatok az SCCM számára](https://docs.microsoft.com/en-us/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data.md). 


## <a name="next-steps"></a>További lépések

Ismertető a személyes adatok Intune-beli [megtekintéséhez és javításához](privacy-data-view-correct.md).
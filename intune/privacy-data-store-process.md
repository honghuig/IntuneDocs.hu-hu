---
title: Adattárolás és -feldolgozás az Intune-ban
description: Ismertető a személyes adatok Intune-beli tárolásáról és feldolgozásáról.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: edb07842-6a16-482e-8c1d-541a29e169a8
ms.reviewer: angerobe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5f7c24775f03011bd936b22e41cfd318e92b5d64
ms.sourcegitcommit: 07528df71460589522a2e1b3e5f9ed63eb773eea
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34474649"
---
# <a name="data-storage-and-processing-in-intune"></a>Adattárolás és -feldolgozás az Intune-ban

Miután az Intune [összegyűjtötte az adatokat](privacy-data-collect.md), az adatok tárolása és feldolgozása az alábbiak szerint történik.

## <a name="storing-personal-data"></a>Személyes adatok tárolása

Az összegyűjtött nem telemetrikus adatok mindegyike az Intune szolgáltatáson belül lesz feldolgozva, és az alábbi tárolási helyek közül egy vagy több használatával lesz tárolva: 

- SQLAzure 
- Megbízható gyűjtemények (Service Fabric)  
- Azure-tároló 

Azok a telemetrikus adatok (szolgáltatásnaplók, teljesítménynaplók, hibák stb.), amelyek kulcsfontosságúak a megbízható szolgáltatás nyújtásához, a Microsoft telemetriai adatokat tároló tárhelyére kerülnek.

### <a name="storage-locations"></a>Tárolási helyek

A Microsoft világszerte számos régióban kínál és működtet Intune-szolgáltatásokat. Az Intune az egyéni adatok esetén a rendszergazda által kiválasztott tárolási helyeket használja.

További információt a [Microsoft Intune: hol vannak az ügyféladataim?](For more information, see Microsoft Intune Where is my customer data?) című témakörben talál.

### <a name="personal-data-retention"></a>Személyes adatok megtartása

Az Intune a személyes adatokat általában a felhasználó Intune-felügyeletből való eltávolítását követő 30 napig őrzi meg.

Az Intune-használat részeként gyűjtött telemetriai adatokat legfeljebb 30 napig őrizzük meg.

Az auditnaplókat legfeljebb egy évig őrizzük meg.

## <a name="processing-personal-data"></a>Személyes adatok feldolgozása

Az Intune a személyes adatokat ISO-hitelesítéssel rendelkező rendszerben dolgozza fel. További információ a [Szolgáltatásmegbízhatósági portálon](https://www.microsoft.com/en-us/TrustCenter/stp) található.

### <a name="profiling-and-marketing"></a>Profilkészítés és marketing

A Microsoft Intune a szolgáltatás nyújtása során gyűjtött személyes adatok egyikét sem használja fel profilkészítési vagy marketing célokra. 

### <a name="restrict-processing-of-personal-data"></a>Személyes adatok feldolgozásának korlátozása

Ha korlátozni szeretné egy felhasználó személyes adatainak feldolgozását, a felhasználó fiókját az alábbiak szerint törölheti:
1. A felhasználó személyes adatainak exportálása elektronikus formában, többek között:
    - fiókok
    - szolgáltatásadatok
    - kapcsolódó naplók
2. Felhasználó fiókjának és a kapcsolódó adatoknak a törlése az Intune-ból.

## <a name="next-steps"></a>További lépések

További információ arról, ahogyan az Intune a személyes adatokat [védi és megosztja](privacy-data-secure-share.md). 
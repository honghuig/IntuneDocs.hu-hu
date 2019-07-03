---
title: Szerepköralapú hozzáférés-vezérlés (RBAC) a Microsoft Intune-nal
description: Ismerje meg, hogyan RBAC lehetővé teszi, hogy ki hajthat végre műveletet, és hajtsa végre a módosításokat a Microsoft Intune-ban.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: eaefcc904d9969c7f356e3eceb924e8d153f912d
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67528240"
---
# <a name="role-based-access-control-rbac-with-microsoft-intune"></a>Szerepköralapú hozzáférés-vezérlés (RBAC) a Microsoft Intune-nal

Szerepköralapú hozzáférés-vezérlés (RBAC) segítségével kezelhetők ki férhet hozzá a szervezet erőforrásokat, és mit tehet a erőforrásokkal.  Által [szerepkörök hozzárendelése](assign-role.md) , az Intune-felhasználók korlátozhatja, hogy mit talál és mit módosítása. Egyes szerepkörök, engedélyek, amelyek meghatározzák, hogy az adott szerepkörhöz tartozó felhasználók hozzáférhetnek, és módosítsa a szervezeten belül rendelkezik.

A szerepkörök létrehozásához, szerkesztéséhez vagy hozzárendeléséhez a fióknak rendelkeznie kell a következő jogosultságok egyikével az Azure AD-ben:
- **Globális rendszergazda**
- **Intune-Szolgáltatásadminisztrátor** (más néven **Intune-rendszergazda**)

Tanácsokat és javaslatokat kapcsolatos Intune-os RBAC Ez a videósorozat a öt, példák és útmutatók bemutatására megtekinthet: [1](https://www.youtube.com/watch?v=5deXLMLcnKY), [2](https://www.youtube.com/watch?v=38dnMBLuxbQ), [3](https://www.youtube.com/watch?v=6vqg9cAkMbY), [4](https://www.youtube.com/watch?v=5yOLajFFMHE), [5](https://www.youtube.com/watch?v=P5DDvsSF4Wk).

## <a name="roles"></a>Szerepkörök
A szerepkör határozza meg, az adott szerepkörhöz rendelt felhasználók számára biztosított engedélyeket.
A beépített és egyéni szerepkörök is használhatja. Beépített szerepköröket bizonyos gyakori Intune forgatókönyvek terjed ki. Is [hozhat létre saját egyéni szerepköröket](create-custom-role.md) az pontos szükséges engedélyekkel együtt. Több Azure Active Directory-szerepkör rendelkezik engedélyekkel az Intune-hoz.
Egy szerepkör megtekintéséhez válassza ki **Intune** > **szerepkörök** > **minden szerepkör** > Válassza ki a szerepkört. Ekkor megjelenik a következő lapokon:

- **Tulajdonságok**: A nevét, leírását, típus, hozzárendelések és a szerepkör hatókörcímkék. 
- **Engedélyek**: Számos olyan hosszú újraengedélyezi a kapcsolókat, milyen engedélyekkel rendelkezik a szerepkör meghatározása.
- **Hozzárendelések**: Listáját [szerepkör-hozzárendelések]( assign-role.md) meghatározása, hogy mely felhasználók férhetnek hozzá mely felhasználókra vagy eszközökre. A szerepkör lehet több hozzárendeléseket, és egy felhasználó több hozzárendelések is lehet.

### <a name="built-in-roles"></a>Beépített szerepkörök
Beépített szerepkörök további konfiguráció nélkül csoportokhoz is hozzárendelhet. Nem lehet törölni, vagy szerkesztheti a név, leírás, típus vagy egy beépített szerepkör engedélyei. Az engedélyek minden beépített szerepkör teljes listáját lásd: a [Intune RBAC-táblázat](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a).

- **Ügyfélszolgálat**: A felhasználók és eszközök távoli feladatokat hajtja végre, és alkalmazásokat és szabályzatokat rendelhet a felhasználókhoz vagy eszközökhöz.
- **A házirend- és Profilkezelő**: Megfelelőségi szabályzat, konfigurációs profilokat, az Apple regisztrációs, cégeseszköz-azonosítók és biztonsági előírások kezeli.
- **Csak olvasási operátor**: Nézetek felhasználói, eszköz, regisztráció, konfigurációs és alkalmazással kapcsolatos adatok. Az Intune-hoz nem végezhet módosításokat.
- **Application Manager**: Kezeli a mobil- és felügyelt alkalmazásokat, olvashatja az eszközadatokat, és megtekintheti az eszközkonfigurációs profilok.
- **Intune-rendszergazda szerepkör**: Egyéni Intune-szerepkörök kezeli, és hozzáadja a beépített Intune-szerepkörök hozzárendeléseit. A csak az Intune-szerepkör, amely a rendszergazdák engedélyeket rendelhet.
- **Iskolai rendszergazda**: Kezeli a Windows 10 rendszerű eszközökhöz az [az Intune for Education](introduction-intune-education.md).

### <a name="custom-roles"></a>Egyéni szerepkörök
Saját szerepköröket is létrehozhat egyéni engedélyekkel. Egyéni szerepkörökkel kapcsolatos további információkért lásd: [hozzon létre egy egyéni szerepkört](create-custom-role.md).

### <a name="azure-active-directory-roles-with-intune-access"></a>Az Intune hozzáférés az Azure Active Directory-szerepkör
| Az Azure Active Directory-szerepkör | Az összes Intune-beli adatokhoz | Az Intune-naplóadatok |
| --- | :---: | :---: |
| Globális rendszergazda | Olvasási/írási | Olvasási/írási |
| Intune szolgáltatás rendszergazdája | Olvasási/írási | Olvasási/írási |
| Feltételes hozzáférésű rendszergazda | Nincsenek | Nincsenek |
| Biztonsági rendszergazda | Csak olvasható | Csak olvasható |
| Biztonsági operátor | Csak olvasható | Csak olvasható |
| Biztonsági olvasó | Csak olvasható | Csak olvasható |
| Szabályozási ügyintéző | Nincsenek | Csak olvasható |
| Megfelelőségi adatok rendszergazda | Nincsenek | Csak olvasható |

> [!TIP]
> Intune-ban három olyan Azure AD-bővítmény látható: **Felhasználók**, **csoportok**, és **feltételes hozzáférési**, amely Azure AD RBAC segítségével szabályozhat. A **Felhasználóifiók-adminisztrátori** szerepkör csak az Azure AD-felhasználói vagy -csoporttevékenységek végrehajtására jogosít fel, és nem biztosít teljes körű engedélyt az összes Intune-beli tevékenységhez. További információkért lásd: [az Azure AD RBAC](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles).
### <a name="roles-created-in-the-intune-classic-portal"></a>Klasszikus Intune-portálon létrehozott szerepkörök
Csak a „Teljes körű” engedéllyel rendelkező Intune-beli **szolgáltatás-rendszergazdákat** migrálja a rendszer a klasszikus Intune-portálról az Azure Portalbeli Intune-ba. Intune-ban kell újbóli **szolgáltatás-rendszergazdák** felhasználók "Csak Olvasás" vagy "Ügyfélszolgálat" hozzáféréssel az Intune-szerepkörök az Azure Portalon, és távolítsa el őket a klasszikus portálról.
> [!IMPORTANT]
> Szüksége lehet az Intune szolgáltatás-rendszergazda hozzáférést tartani a klasszikus portálon, ha a rendszergazdák továbbra is hozzáférhetnek a számítógépek az Intune-nal kezelheti.

## <a name="role-assignments"></a>Szerepkör-hozzárendelések
Szerepkör-hozzárendelés meghatározása:

- melyik felhasználók vannak hozzárendelve a szerepkörhöz
- megjelenik az erőforrásokat
- milyen erőforrások módosításához.

Egyéni és a beépített szerepkörök hozzárendelheti a felhasználókhoz. Az Intune-szerepkörhöz hozzárendelni, a felhasználó Intune-licenccel kell rendelkeznie.
Szerepkör-hozzárendelés megtekintéséhez válassza ki **Intune** > **szerepkörök** > **minden szerepkör** > Válassza ki a szerepkört > Válassza ki a hozzárendelést. Ekkor megjelenik a következő lapokon:

- **Tulajdonságok**: A neve, leírása, szerepkör, a tagok, hatókörök és címkék a hozzárendelés.
- **A tagok**: A listán szereplő csoportok minden felhasználó rendelkezik a hatókör (csoportok) szereplő felhasználók és eszközök kezelésére jogosult.
- **Hatókör (csoportok)** : Összes felhasználók és eszközök a megadott csoportokban szereplő felhasználók tagok által kezelhetők.
- **[Hatókör (címkék)](scope-tags.md)** : A tagok felhasználója láthatja az erőforrásokat, amelyek az ugyanazon hatókörcímkék.

### <a name="multiple-role-assignments"></a>Több szerepkör-hozzárendelések
Ha egy felhasználó több szerepkör-hozzárendeléseket, azokat a szerepkör-hozzárendeléseket az engedélyek kiterjesztése a különböző objektumokat a következő:

- Rendeljen engedélyeket csak az objektumok (például a szabályzatokat vagy alkalmazásokat) az adott szerepkör-hozzárendelési hatókör (csoportok) vonatkoznak. Rendeljen engedélyeket nem vonatkoznak más szerepkör-hozzárendelések objektumokat, ha a többi hozzárendelés kifejezetten megadja számára.
- Egyéb engedélyek (például a létrehozás és olvasás), sem a felhasználó-hozzárendelés az azonos típusú (például az összes házirend vagy az összes alkalmazás) összes objektumra vonatkozik.
- Engedélyek (például a szabályzatokat vagy alkalmazásokat) a különböző típusú objektumok egymáshoz nem érvényesek. Olvasási engedély egy házirendet, például egy olvasási engedélyt a felhasználó-hozzárendeléseket az alkalmazások nem biztosít.

## <a name="next-steps"></a>További lépések
- [Szerepkör hozzárendelése felhasználóhoz](assign-role.md)
- [Egyéni szerepkör létrehozása](create-custom-role.md)

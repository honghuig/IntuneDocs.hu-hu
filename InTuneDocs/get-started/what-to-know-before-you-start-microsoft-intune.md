---
title: "Támogatott eszközök – Microsoft Intune | Microsoft Docs"
description: "Az Intune-eszközkezelés által támogatott eszközplatformok és böngészők listája"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b3732d0c6461f9fb8462ae5584055204d597aae0
ms.openlocfilehash: 0af4f49713a65900079d69a09f20d210797c935c


---

# <a name="supported-devices-and-browsers"></a>Támogatott eszközök és böngészők

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Ez a cikk a vállalatnál az eszközkezelésért felelős rendszergazdák számára készült. A következő témakörben találhat segítséget az Intune telefonra való telepítéséhez: [Using managed devices to get work done](https://docs.microsoft.com/intune/enduser/company-portal-frequently-asked-questions) (Feladatok elvégzése kezelt eszközökön).

A Microsoft Intune beállítása előtt tekintse át az alábbi követelményeket:

- [Támogatott eszközök és számítógépek](#intune-supported-devices)
- [Az Intune használatára alkalmas böngészők listája](#intune-supported-web-browsers)

Ismerkedjen meg [az Intune hálózatisávszélesség-felhasználásával](network-bandwidth-use.md) is.

## <a name="intune-supported-devices"></a>Az Intune által támogatott eszközök

Az Intune a következő eszközöket képes felügyelni a mobileszköz-felügyeleti funkciókkal:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

Az Intune nem használható a Windows Server operációs rendszer felügyeletére.

Az Intune-beli eszközfelügyelet [ezeket a funkciókat biztosítja](mobile-device-management-capabilities-in-microsoft-intune.md).

### <a name="windows-pc-software-client"></a>Windowsos számítógépeken futó szoftveres ügyfél

A windowsos számítógépekre a regisztráció alternatívájaként telepítheti az [Intune szoftveres ügyfelet](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune) is. Az Intune szoftveres ügyfele segítségével a Windows 7 és újabb rendszerű számítógépeket felügyelheti (kivéve a Windows 10 Home verziót). A számítógépek ügyfélszoftverrel történő felügyelete az [alábbi funkciókat](windows-pc-management-capabilities-in-microsoft-intune.md) biztosítja.

### <a name="exchange-activesync-management"></a>Felügyelet az Exchange ActiveSync segítségével

Az Intune-konzolból az [Exchange ActiveSync-eszközöket](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune) is felügyelheti. E módszer használata esetén csak a felügyeleti funkciók korlátozott körét érheti el. A támogatott eszközök listáját [az Office 365 beépített mobileszköz-felügyeleti funkcióit ismertető](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) cikk tartalmazza.

## <a name="intune-supported-web-browsers"></a>Az Intune által támogatott webböngészők

A különféle felügyeleti tevékenységek elvégzésére a következő két felügyeleti webhely valamelyikét kell használnia.

- [Office 365 portál](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Microsoft Intune felügyeleti konzol](https://admin.manage.microsoft.com/)

|Intune-funkció |Támogatott böngészők|
|---------|---------|
|**Intune felügyeleti konzol**     |  Internet Explorer 10 vagy újabb<br /><br />Google Chrome (42-es vagy korábbi verziók)<br /><br />Mozilla Firefox (a Silverlightot engedélyezni kell)<br />**Megjegyzés:** A Mozilla 2017 márciusától megszünteti a Silverlight támogatását. [További információ](https://go.microsoft.com/fwlink/?linkid=836872). |
|**Office 365 felügyeleti portál**     |Minden böngésző, beleértve a mobilböngészőket és a felügyelt böngészőket  |
|**Munkahelyi portál webhely**     |**Mobileszközökön:** használja a támogatott platformhoz tartozó alapértelmezett webböngészőt   <br /><br />**Windows rendszerű számítógépeken:** Internet Explorer 10 vagy újabb, illetve Microsoft Edge<br /><br />**Mac OS X 10.9 vagy újabb:** Apple Safari    |

> [!Note]
> A Microsoft Edge és a mobilböngészők nem támogatottak a felügyeleti konzolon, mivel nem támogatják a [Microsoft Silverlight](https://msdn.microsoft.com/en-us/library/cc838158(v=vs.95).aspx) összetevőt. Az Intune-konzol egy idő múlva kikerül a Silverlight-megoldásból, és az Intune összes mobileszköze és alkalmazásfelügyeleti funkciója végül [az új Microsoft Azure portálon válik majd elérhetővé](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/).


A portálra szolgáltatás-rendszergazdák, valamint globális rendszergazda szerepkörrel rendelkező bérlői rendszergazdák jelentkezhetnek be. A felügyeleti konzol eléréséhez a fióknak az Intune használatához szükséges licenccel, illetve **Engedélyezett** bejelentkezési állapottal kell rendelkeznie.

>[!div class="step-by-step"]

>[**Hálózatkezelés**&rarr;](network-bandwidth-use.md)  



<!--HONumber=Feb17_HO2-->


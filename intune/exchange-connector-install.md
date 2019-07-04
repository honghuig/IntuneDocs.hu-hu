---
title: A Microsoft Intune helyszíni Exchange-összekötőjének beállítása
titleSuffix: Microsoft Intune
description: A helyszíni Exchange-összekötővel kezelheti az eszközök az Exchange-postaládákhoz való hozzáférését az Intune-regisztráció és az Exchange Active Sync (EAS) alapján.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9d8cd91d55c90fd4b4f26ee0e6b1b99d37bcce08
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/03/2019
ms.locfileid: "67547601"
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune"></a>Állítsa be az Intune helyszíni Exchange-összekötő a Microsoft Intune-ban
Ebben a cikkben található információk segítséget telepítse, és figyelje az Exchange Active Sync helyszíni összekötőt az Intune-hoz.  Az Intune helyszíni Exchange connector használata az [engedélyezi vagy letiltja a hozzáférést az Exchange feltételes hozzáférési szabályzatok a helyszíni postaládák](conditional-access-exchange-create.md). 

Ha egy eszközt próbál a helyszíni Exchange-hozzáférést, az Exchange-összekötő az Exchange Active Sync (EAS) rögzíti az Exchange Server eszközök regisztrálása az Intune-nal, és az eszköz megfelelőségét a megfelelőség ellenőrzése az Intune-rekordok képezi le. Attól függően, a feltételes hozzáférési szabályzatokat az eszköz hozzáférése engedélyezett, vagy letiltva. További információkért lásd: [Mik azok az Intune-nal feltételes hozzáférés használatának szokásos módjai?](conditional-access-intune-common-ways-use.md)

Az Intune támogatja a több helyszíni Exchange-összekötők előfizetésenként telepítése. Ha egynél több helyszíni Exchange-szervezethez, akkor állíthat be egy különálló összekötő minden. Azonban lehet, csak egy összekötőt használatra telepített minden egyes Exchange-szervezet. 

Kapcsolatot hoz létre, amely lehetővé teszi a helyszíni Exchange-kiszolgálóval való kommunikációhoz az Intune beállítása az általános lépések a következők:

1. Töltse le az Intune helyszíni Exchange-összekötő az Intune-portálon.
2. Telepítse és konfigurálja az Exchange-összekötőt a helyszíni Exchange-szervezet egyik számítógépén.
3. Az Exchange-kapcsolat ellenőrzése.
4. Ismételje meg ezeket a lépéseket minden további Exchange-szervezethez, amelyhez csatlakozni az Intune-hoz.

## <a name="intune-on-premises-exchange-connector-requirements"></a>Az Intune helyszíni Exchange-összekötő követelményei
Szüksége lesz egy fiókra az Intune-licencet az összekötővel csatlakozhat az Exchange-hez használható. A fiók van megadva, az összekötő telepítésekor.  

A következő táblázat a helyszíni Exchange-összekötő számítógépre vonatkozó követelményeit tartalmazza.  

|  Követelmény  |   További információ     |
|---------------|------------------------|
|  Operációs rendszerek        | Az Intune a helyszíni Exchange-összekötőt olyan számítógépen támogatja, amelyen a Windows Server 2008 SP2 64 bites, a Windows Server 2008 R2, a Windows Server 2012, a Windows Server 2012 R2 vagy a Windows Server 2016 rendszer valamelyik kiadása fut.<br /><br />Az összekötő nem támogatott a Server Core telepítéseken.  |
| Microsoft Exchange          | A helyszíni összekötőhöz a Microsoft Exchange 2010 SP3 vagy újabb verziójára, vagy régi dedikált Exchange Online-ra van szükség. Lépjen kapcsolatba a fiókkezelővel annak megállapításához, hogy a dedikált Exchange Online-környezet <strong>új</strong> vagy <strong>régi</strong> konfigurációval rendelkezik-e. |
| Mobileszköz-kezelő szolgáltató           | [Mobileszköz-kezelő szolgáltatóként a Microsoft Intune-t állítsa be](mdm-authority-set.md). |
| Hardver              | Azon számítógépnek, amelyre az összekötőt telepíteni kívánja, 1,6 GHz-es processzorral, 2 GB memóriával és legalább 10 GB szabad lemezterülettel kell rendelkeznie. |
|  Active Directory-szinkronizálás             | Mielőtt az Intune-t az összekötő segítségével csatlakoztathatná az Exchange-kiszolgálóhoz, [állítsa be az Active Directory-szinkronizálást](users-add.md), hogy a helyi felhasználók és biztonsági csoportok szinkronizálva legyenek az Azure Active Directory meglévő példányával. |
| További szoftverek         | Az összekötőt futtató számítógépnek a Microsoft .NET-keretrendszer 4.5-ös és a Windows PowerShell 2.0-s verziójának teljes telepítésével kell rendelkeznie. |
| Network (Hálózat)               | Az összekötő telepítéséhez használt számítógépnek olyan tartományhoz kell tartoznia, amely megbízhatósági kapcsolatban áll az Exchange Server-t üzemeltető tartománnyal.<br /><br />A számítógépet úgy kell beállítani, hogy a 80-as és a 443-as porton, a tűzfalakon és a proxykiszolgálókon keresztül hozzáférjen az Intune szolgáltatáshoz. Az Intune által használt tartományok a következők: manage.microsoft.com, &#42;manage.microsoft.com és &#42;.manage.microsoft.com. |

### <a name="exchange-cmdlet-requirements"></a>Exchange-parancsmagokkal kapcsolatos követelmények

Hozzon létre egy Active Directory a helyszíni Exchange-összekötő által használt felhasználói fiók. A fióknak engedéllyel kell rendelkeznie az alábbi szükséges Windows PowerShell Exchange-parancsmagok futtatásához:


 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-CasMailbox, Set-CasMailbox
 - Get-ActiveSyncMailboxPolicy, Set-ActiveSyncMailboxPolicy, New-ActiveSyncMailboxPolicy, Remove-ActiveSyncMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 - Get-ActiveSyncDeviceStatistics
 - Get-ActiveSyncDevice
 - Get-ExchangeServer
 - Get-ActiveSyncDeviceClass
 - Get-Recipient
 - Clear-ActiveSyncDevice, Remove-ActiveSyncDevice
 - Set-ADServerSettings
 - Get-Command

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>A helyszíni Exchange-összekötő szoftver telepítőcsomagjának letöltése

1. Egy, a helyszíni Exchange-összekötőt támogató Windows Server rendszerben nyissa meg az [Azure Portalt](https://portal.azure.com), és jelentkezzen be egy olyan felhasználói fiókkal, amely rendszergazda a helyszíni Exchange Serveren, és rendelkezik licenccel az Exchange Server használatához.

2. Lépjen a **Intune** > **Exchange-hozzáférés**  

3. Alatt **telepítő**, válassza a **Exchange ActiveSync helyszíni összekötő**, majd válassza ki **Hozzáadás**.

4. Az a **hozzáadása összekötő** lapon jelölje be **a helyszíni összekötő letöltése**. A helyszíni Exchange connector van egy tömörített (.zip) mappa, amely képes megnyitni vagy menteni. A **Fájl letöltése** párbeszédpanelen kattintson a **Mentés** parancsra a tömörített mappa biztonságos helyre való mentéséhez.

    > [!IMPORTANT]
    > Ne nevezze és ne helyezze át a helyszíni Exchange-összekötő mappájában levő fájlokat. A mappa tartalmának áthelyezése vagy átnevezése az Exchange-összekötő sikertelen telepítését eredményezi.

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>A helyszíni Intune Exchange-összekötő telepítése és konfigurálása
A helyszíni Intune Exchange-összekötő telepítéséhez hajtsa végre az alábbi lépéseket. Ha több Exchange-szervezettel rendelkezik, ismételje meg ezeket a lépéseket az összes további beállítandó Exchange-összekötő esetében.

1. Egy, a helyszíni Exchange-összekötő által támogatott operációs rendszerben bontsa ki az **Exchange_Connector_Setup.zip** fájl tartalmát egy biztonságos helyre.

2. A fájlok kibontása után nyissa meg a kibontott mappát, majd kattintson duplán az **Exchange_Connector_Setup.exe** fájlra a helyszíni Exchange-összekötő telepítéséhez.

   > [!IMPORTANT]
   > Ha a célmappa nem biztonságos hely, akkor a helyszíni összekötők telepítése után törölje a **MicrosoftIntune.accountcert** tanúsítványfájlt.

3. A **Microsoft Intune Exchange Connector** párbeszédpanelen válassza ki a **Helyszíni Microsoft Exchange Server** vagy **Üzemeltetett Microsoft Exchange Server** lehetőségek egyikét.

   ![Kép az Exchange-kiszolgáló típusának kiválasztási helyéről](./media/intune-sa-exchange-connector-config.png)

   Helyszíni Exchange-kiszolgáló esetén adja meg az **Ügyfél-hozzáférési kiszolgáló** szerepkört futtató Exchange-kiszolgáló nevét vagy teljes tartománynevét.

   Üzemeltetett Exchange-kiszolgáló esetén adja meg az Exchange-kiszolgáló címét. Az üzemeltetett Exchange-kiszolgáló URL-címének megkeresése:

   1. Nyissa meg az Office 365-ös Webes Outlookot.

   2. Kattintson a **?** ikonra baloldalt felül, majd válassza a **Névjegy** lehetőséget.

   3. Keresse meg a **POP külső kiszolgáló** értéket.

   4. Kattintson a **Proxykiszolgáló** elemre az üzemeltetett Exchange proxykiszolgáló-beállításainak megadásához.
       1. Válassza a **Proxykiszolgáló használata mobileszköz-információk szinkronizálásakor**lehetőséget.

       2. Adja meg a **proxykiszolgáló nevét** és **portszámát** a kiszolgálóhoz való hozzáféréshez.

       3. Ha a proxykiszolgálóhoz való csatlakozáshoz hitelesítő adatok megadása szükséges, válassza a **Hitelesítő adatok használata a proxykiszolgálóhoz való csatlakozáshoz** lehetőséget. Ezután adja meg a **tartomány\felhasználó** és a **jelszó** értékét.

       4. Válassza az **OK** gombot.

4. A **Felhasználó (Tartomány\felhasználó)** és **Jelszó** mezőknél adja meg az Exchange-kiszolgálóhoz való csatlakozáshoz szükséges hitelesítő adatokat. A megadott fióknak rendelkeznie kell az Intune használatához szükséges licenc. 

5. Adja meg azokat a hitelesítő adatokat, amelyek szükségesek ahhoz, hogy az értesítéseket egy felhasználó Exchange Server-postaládájába küldhesse a rendszer. Ezt a felhasználót dedikálhatja kizárólag az értékesítésekre. Az értesítések felhasználói e-mailes értesítések küldése az Exchange-postaládára van szüksége. Ezeket az értesítéseket a feltételes hozzáférési szabályzatokon keresztül konfigurálhatja az Intune-ban.  

       Ensure that the Autodiscover service and Exchange Web Services are configured on the Exchange Client Access Server. For more information, see [Client Access server](https://technet.microsoft.com/library/dd298114.aspx).

6. A **Jelszó** mezőben adja meg a fiók jelszavát, hogy az Intune hozzáférhessen az Exchange-kiszolgálóhoz.

7. Válassza a **Csatlakozás** elemet.

   > [!NOTE]
   > A kapcsolat konfigurálása néhány percig is eltarthat.

A konfiguráció során az Exchange-összekötő tárolja a proxybeállításait, hogy lehetővé tegye a kapcsolódást az internethez. Ha a proxybeállításai megváltoznak, kell konfigurálnia az Exchange-összekötő az Exchange-összekötő a frissített proxybeállítások alkalmazandó.

Miután az Exchange-összekötő létrehozta a kapcsolatot, azokat a mobileszközöket, amelyek az Exchange-ben felügyelt felhasználókhoz vannak társítva, a rendszer automatikusan szinkronizálja és hozzáadja az Exchange-összekötőhöz. Ez a szinkronizálás eltarthat egy ideig.

> [!NOTE]
> Ha telepítette a helyszíni Exchange-összekötőt, de később törli az Exchange-kapcsolatot, akkor el kell távolítania a helyszíni Exchange-összekötőt is arról a számítógépről, amelyre telepítette.



## <a name="install-connectors-for-multiple-exchange-organizations"></a>Összekötők telepítése több Exchange-szervezethez
Az Intune egy előfizetésben több helyszíni Exchange-összekötőt is támogat. Több Exchange-szervezet egy bérlőt beállíthat egy összekötőt, az egyes Exchange-szervezethez, de csak egy összekötőt bármely egyetlen szervezet számára. 

Ha több Exchange-szervezet csatlakozni összekötők telepít, töltse le a .zip mappát egyszer, és használja fel újra, hogy azonos töltse le az egyes összekötők telepítése. Minden további összekötő kövesse az előző szakasz kibontása és a telepítőprogramot az Exchange-szervezeten belüli kiszolgálón.

A magas rendelkezésre állás figyelése és manuális szinkronizálást a következő szakaszokban ismertetett szolgáltatása támogatott az egyes Exchange-szervezethez, amely összeköti az Intune-hoz.

## <a name="on-premises-exchange-connector-high-availability-support"></a>Magas rendelkezésre állású helyszíni Exchange Connector támogatása 
A helyszíni Exchange connector azt jelenti, hogy az Exchange ügyfél hozzáférési kiszolgálói (CAS) az összekötő által használt elérhetetlenné kell magas rendelkezésre állású, az összekötő válthat, hogy az Exchange-szervezet egy másik CAS használandó. Maga az Exchange-összekötő nem támogatja a magas rendelkezésre állás. Ha az összekötő nem tud, nincs automatikus feladatátvétel van, és cserélje le ezt az összekötőt úgy [új összekötő telepítéséhez](#reinstall-the-on-premises-exchange-connector). 

A feladatátvétel után az összekötő hoz létre sikeres kapcsolatot a megadott CAS az Exchange el az összekötő további CAS kiszolgálókat is, hogy az Exchange-szervezet deríti fel. További CAS kiszolgálókat is ismerete lehetővé teszi a feladatátvételt egy másik CAS-összekötő, ha ilyen, amíg az elsődleges CAS elérhetősége elérhetővé válik. További CAS kiszolgálókat is a felderítés alapértelmezés szerint engedélyezve van. Kikapcsolhatja a feladatátvételt, az alábbi eljárás segítségével:  
1. A kiszolgálón, ahol az Exchange connector telepítve van-e, nyissa meg a %*ProgramData*%\Microsoft\Windows Intune Exchange Connectort. 
2. Nyissa meg egy szövegszerkesztőben az **OnPremisesExchangeConnectorServiceConfiguration.xml** fájlt.
3. Módosítsa az &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt; értéket az &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt; értékre a funkció letiltásához.    
 

## <a name="reinstall-the-on-premises-exchange-connector"></a>A helyszíni Exchange connector újratelepítése
Szüksége lehet az Exchange connector újratelepítése. Egy összekötőt szeretne csatlakozni az egyes Exchange-szervezethez, akkor támogatott, ha a szervezet számára egy második összekötőt telepíti, mert az új összekötő telepítése felülírja az eredeti összekötőket.

1. Lépéssorral [telepítése és konfigurálása az Intune helyszíni Exchange connector](#install-and-configure-the-intune-on-premises-exchange-connector) az új összekötő a telepítés elindításához. 
2. Amikor a rendszer kéri, válassza ki a **cseréje** az új összekötő telepítéséhez.  
   ![Cserélje le az összekötő konfigurációs kérése](./media/exchange-connector-install/prompt-to-replace.png)

3. Továbbra is a lépéseket az előző eljárásban alkotnak, és ismét jelentkezzen be az Intune használatával.
4. Ha az meg fog jelenni a végső képernyő, válassza ki a **Bezárás** a telepítés befejezéséhez.  
   ![Befejezniük a telepítést](./media/exchange-connector-install/successful-reinstall.png)
 

## <a name="monitor-the-exchange-connector-activity"></a>Az Exchange Connector tevékenységének figyelése

Miután sikeresen konfigurálta az Exchange-összekötő, megtekintheti a kapcsolatok és a legutóbbi sikeres szinkronizálási kísérlet állapotát. Az Exchange connector-kapcsolat ellenőrzése:

1. Az Intune irányítópultján válassza **Exchange-hozzáférés**.
2. Válassza ki **a helyszíni Exchange-hozzáférés** minden egyes Exchange-összekötő a kapcsolat állapotának ellenőrzése.

Ellenőrizheti a legutóbbi sikeres szinkronizálási kísérlet dátumát és időpontját is.
--> 

### <a name="system-center-operations-manager-management-pack"></a>A System Center Operations Manager felügyeleti csomag

Az Intune 1710-es kiadásától kezdve használhatja a [az Operations Manager felügyeleti csomag az Exchange- összekötővel](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True). A felügyeleti csomag segítségével biztosít az Exchange connector figyelésére, amikor szüksége van a hibák elhárításához.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>Gyors szinkronizálás vagy teljes szinkronizálás manuális kényszerítése
A helyszíni Exchange connector szoftverből automatikusan szinkronizálja az EAS és az Intune-eszközrekordoknak rendszeresen. Ha egy eszköz megfelelőségi állapota megváltozik, az automatikus szinkronizálási folyamat rendszeresen frissíti a rekordokat, hogy az eszközök hozzáférésének letiltott vagy engedélyezett.

   - **Gyors szinkronizálás** rendszeresen történik, naponta többször. Gyors szinkronizálási eszköz adatait kérdezi le az Intune-licenccel rendelkező és a helyszíni Exchange feltételes hozzáférési megcélzott felhasználók, amelyek a legutóbbi szinkronizálás óta.

   - **Teljes szinkronizálás** naponta egyszer történik alapértelmezés szerint. A teljes szinkronizálás az összes eszköz adatait kérdezi le az Intune-licenccel rendelkező és a helyszíni Exchange feltételes hozzáférési megcélzott felhasználók. A teljes szinkronizálás emellett beolvassa az Exchange kiszolgálói adatait is, és biztosítja, hogy az Intune által az Azure Portalon megadott konfiguráció frissüljön az Exchange-kiszolgálón. 


Kényszerítheti a szinkronizálás futtatását egy összekötőn, ha a **Gyors szinkronizálás** vagy a **Teljes szinkronizálás** lehetőséget választja az Intune-irányítópulton. Ehhez kövesse az alábbi lépéseket:

   1. Az Intune irányítópultján válassza **Exchange-hozzáférés**.
   2. Válassza ki **a helyszíni Exchange-hozzáférés**.
   3. Válassza a szinkronizálni kívánt összekötőt, majd válassza a **Gyors szinkronizálás** vagy a **Teljes szinkronizálás** lehetőséget.

## <a name="next-steps"></a>További lépések
[A helyszíni Exchange feltételes hozzáférési szabályzat létrehozása](conditional-access-exchange-create.md)

---
# required metadata

title: A Windows rendszerű számítógépek általános felügyeleti feladatai | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: eb912c73-54d2-4d78-ac34-3cbe825804c7

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# A Windows rendszerű számítógépek a Microsoft Intune számítógépügyféllel való felügyeletének általános feladatai
Az ebben a témakörben található feladatok áttekintésével megismerheti, hogyan felügyelheti az Intune-ügyfelet futtató számítógépeket. Ha még nem telepítette az ügyfelet a számítógépeken, olvassa el [A Windows rendszerű számítógépügyfél telepítése a Microsoft Intune-nal](install-the-windows-pc-client-with-microsoft-intune.md) című cikket.


## A számítógépek felügyelete szabályzatok használatával egyszerűsíthető
### A Windows tűzfal felügyelete
A házirendek egyszerűbbé teszik a Windows tűzfal beállításainak adminisztrációját a felügyelt számítógépeken. Részletekért olvassa el [A Windows rendszerű számítógépek védelme Windows tűzfalházirendek használatával a Microsoft Intune-ban](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) című cikket.

### A Microsoft Intune Center felügyelete
A Microsoft Intune Center a következőket teszi lehetővé a felhasználók számára:

-   alkalmazások beszerzése a vállalati portálról;

-   frissítések keresése;

-   A Microsoft Intune Endpoint Protection felügyelete

-   távsegítség kérése.

A Microsoft Intune Center minden felügyelt számítógépre telepítve van. Az alábbi beállításokat konfigurálhatja egy Intune-szabályzatban, és ezek jelennek meg a felhasználóknak a Microsoft Intune Centerben:

|Házirend-beállítás|Részletek|
|------------------|--------------------|
|**Név**|A számítógépet felügyelő rendszergazda neve.<br /><br />Maximális hossz: 40 karakter|
|**Telefonszám**|A számítógépet felügyelő rendszergazda telefonszáma.<br /><br />Maximális hossz: 20 karakter|
|**E-mail cím**|A számítógépet felügyelő rendszergazda e-mail címe.<br /><br />Maximális hossz: 40 karakter|
|**Webhely neve**|A felhasználói támogatási webhely neve.<br /><br />Maximális hossz: 40 karakter|
|**Webhely URL-címe**|A támogatási webhely URL-címe.<br /><br />Maximális hossz: 150 karakter|
|**Megjegyzések**|A felhasználóknak megjelenített megjegyzés.<br /><br />Maximális hossz: 120 karakter|

### Szoftverfrissítések beállításainak kezelése
Házirendek használata azon beállítások konfigurálásához, amelyeket a felügyelt számítógépek a Microsofttól és külső gyártóktól származó frissítések kereséséhez és letöltéséhez használnak. További információkért lásd: [Windows rendszerű számítógépek naprakészen tartása szoftverfrissítésekkel a Microsoft Intune-ban](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)..

### Endpoint Protection-beállítások felügyelete
Szabályzatok használata az Endpoint Protection beállításainak konfigurálásához, amelyek később a felügyelt számítógépekre lesznek telepítve. Ez tartalmazza a vizsgálatütemezéseket, a kártevők észlelésekor végrehajtott műveleteket stb. További információkért lásd: [Windows rendszerű számítógépek biztonságossá tétele a Microsoft Intune-hoz készült Endpoint Protection szolgáltatással](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)..

## Hardver- és szoftverleltár megtekintése
Az Intune részletes információkat gyűjt a felügyelt számítógépek hardvereiről és szoftvereiről. Az alábbi eljárásokban lévő információkból megtudhatja:

-   Hogyan hozhat létre olyan jelentést, amely a számítógépek hardvertulajdonságaival kapcsolatos információkat tartalmazza.

-   Hogyan hozhat létre olyan jelentést, amely az egyes számítógépekre telepített szoftvereket tartalmazza.

-   Hogyan frissítheti a számítógépleltárat, hogy a jelentésben szereplő adatok naprakészek legyenek.

### A számítógépekkel kapcsolatos információk megjelenítése

1.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) válassza a **Jelentések** &gt; **Számítógépleltár-jelentések** lehetőséget..

2.  Az **Új jelentés létrehozása** lapon fogadja el az alapértelmezett értékeket, vagy állítsa be őket a jelentés által visszaadott eredmények szűrésére. Kiválaszthatja például, hogy csak a Windows 8.1-et futtató számítógépek jelenjenek meg a jelentésben.

3.  A **Jelentés megtekintése** elemet választva megnyithatja a **Számítógépleltár-jelentést** egy új ablakban.

    Az egyes oszlopok fejlécét választva a jelentést bármelyik oszlop, például a **Név**, a **Ház típusa** vagy a **Gyártó** szerint rendezheti.

### A számítógépekre telepített szoftverek megjelenítése

1.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) válassza a **Jelentések** &gt; **Észlelt szoftverek jelentései** elemet..

2.  Az **Új jelentés létrehozása** lapon fogadja el az alapértelmezett értékeket, vagy állítsa be őket a jelentés által visszaadott eredmények szűrésére. Kiválaszthatja például, hogy csak a Microsoft által kiadott szoftverek jelenjenek meg a jelentésben.

3.  A **Jelentés megtekintése** elemet választva megnyithatja az **Észlelt szoftverek jelentéseit** egy új ablakban.

    Az egyes oszlopok fejlécét választva a jelentést bármelyik oszlop, például a **Név**, a **Kiadó** vagy a **Kategória** alapján rendezheti. A listában lévő frissítések kibontásával, a listaelem mellett lévő, irányt mutató nyílra kattintva részletes információkat jeleníthet meg (például a számítógépeket, amelyeken telepítve van).

### A számítógépleltár frissítése a naprakész állapot biztosításához

1.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) válassza a **Csoportok** &gt; **Minden eszköz** elemet (vagy egy másik csoportot, amely tartalmazza azt a számítógépet, amelynek a leltárát frissíteni szeretné).

2.  Válasszon ki egy számítógépet, vagy tartsa lenyomva a **Ctrl** billentyűt több számítógép kijelöléséhez.

3.  A tálcán válassza a **Távoli feladatok** &gt; **Leltár frissítése** elemet..

4.  A feladat állapotának megtekintéséhez válassza a lap jobb alsó sarkában található **Távoli feladatok** elemet.

    A **Feladat állapota** párbeszédpanel megjeleníti az aktuális távoli feladatokat, a feladatok állapotát, az eszköz nevét és minden jelentett hibát, valamint egy hivatkozást kínál a hibaelhárítási információkhoz.


## Windows rendszerű számítógépek távoli újraindítása

1.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) válassza a **Csoportok** &gt; **Minden eszköz** elemet (vagy egy másik csoportot, amely tartalmazza azt a számítógépet, amelyet újra szeretne indítani).

2.  Jelöljön ki egy vagy több számítógépet, majd válassza a **Távoli feladatok** &gt; **Számítógép újraindítása** elemet.

3.  A feladat állapotának megtekintéséhez válassza a lap jobb alsó sarkában található **Távoli feladatok** elemet.

4.  A **Feladat állapota** párbeszédpanelen áttekintheti az aktuális távoli feladatokat, a feladatok állapotát, az eszköz nevét és minden jelentett hibát.

## Számítógépek kivonása

1.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) válassza a **Csoportok** &gt; **Minden eszköz** elemet (vagy egy másik csoportot, amely tartalmazza a kivonni kívánt számítógépet).

2.  Jelölje ki a kivonni kívánt eszközöket, majd válassza a **Kivonás/Összes adat törlése** elemet..

Ha a számítógépet újból regisztrálni szeretné az Intune-ban, telepítse újra az ügyfélszoftvert a számítógépen [A Windows rendszerű számítógépügyfél telepítése a Microsoft Intune-nal](install-the-windows-pc-client-with-microsoft-intune.md) című témakörben található információk segítségével.

Ha a számítógép nem tud csatlakozni az Intune-hoz, egy üzenet jelenik meg az **Irányítópult** munkaterületen.

A számítógép eltávolításakor:

-   A rendszer eltávolítja az Intune-leltárból, és a számítógéphez társított licenc ismét felhasználhatóvá válik.

-   Az állapota már nem jelenik meg az Intune-konzolon.

-   Az Intune eltávolítja az ügyfélszoftvert a számítógépről. Ha a számítógép nincs csatlakoztatva az Intune-hoz, a rendszer a számítógép következő csatlakozásakor távolítja el az ügyfélszoftvert.

-   Megtörténik a Microsoft Intune Endpoint Protection eltávolítása a számítógépről. Ha a számítógépre telepítve van egy másik végponti alkalmazás, és le van tiltva, akkor az alkalmazás a Microsoft Intune Endpoint Protection eltávolítása után újból engedélyezhető a számítógépek védelmének biztosításához.

-   A rendszer eltávolít minden házirendet a számítógépről, és módosulnak a házirendek által beállított értékek.

-   A számítógép többé nem kap szoftver- vagy a kártevődefiníció-frissítéseket az Intune szolgáltatástól.

-   Konfigurációjuktól függően az eltávolított számítógépek a Windows Server Update Services, a Windows Update vagy a Microsoft Update használatával továbbra is kaphatnak frissítéseket.

    > [!IMPORTANT]
    > Ha az ügyfélszoftver egy csoportházirend-objektummal (GPO) lett telepítve, akkor az ügyfélszoftver eltávolítása előtt el kell távolítania a csoportházirend-objektumot (GPO), hogy megakadályozza a szoftver újratelepítését.

    Ha az ügyfél eltávolítása nem sikerült, további segítséget itt találhat: [Az Endpoint Protection hibáinak elhárítása](/intune/troubleshoot/troubleshoot-endpoint-protection-in-microsoft-intune).

## Felhasználók és eszközök összekapcsolásának felügyelete
Mielőtt szoftvereket telepítene egy felhasználónak, a felhasználót egy számítógéphez kell kapcsolni. Egy felhasználót több számítógéphez is kapcsolhat, de minden gép csak egyetlen felhasználóhoz kapcsolható. A felhasználókat a rendszer automatikusan összekapcsolja azokkal a számítógépekkel, amelyeket a vállalati portálon keresztül regisztráltak az Intune-ban.

### Felhasználók kapcsolása számítógépekhez

1.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) válassza a **Csoportok** &gt; **Minden eszköz** elemet (vagy egy másik csoportot, amely tartalmazza azt a számítógépet, amelyet egy felhasználóhoz szeretne kapcsolni).

2.  Jelölje ki a felhasználóval összekapcsolni kívánt számítógépet, majd válassza a **Felhasználó összekapcsolása** elemet..

    A **Felhasználó összekapcsolása** párbeszédpanel megjeleníti az elérhető felhasználók listáját a megjelenített nevükkel, a felhasználói azonosítójukkal és azon számítógépek számával, amelyekhez az egyes felhasználók jelenleg kapcsolva vannak. Ha a kijelölt számítógéphez már van felhasználó kapcsolva, akkor annak a felhasználónak a neve és felhasználói azonosítója megjelenik az **Aktuális felhasználó**területen. Ha a számítógép nincs felhasználóhoz kapcsolva, akkor az **Aktuális felhasználó** területen a **Nincs felhasználó** felirat jelenik meg..

3.  Tegye a következők valamelyikét:

    -   Ha azt szeretné, hogy a számítógép továbbra is az aktuális felhasználóhoz legyen kapcsolva (ha van ilyen), válassza a **Mégse** lehetőséget..

    -   Ha el szeretné távolítani az aktuális felhasználóhoz való kapcsolatot (ha van ilyen), válassza a **Kapcsolat eltávolítása**&gt;**OK** lehetőséget.

    -   Ha a számítógépet egy új felhasználóhoz szeretné kapcsolni, válasszon ki egy felhasználót a **Minden felhasználó** listában. Erősítse meg, hogy a felhasználói adatok helyesek, majd válassza az **OK** lehetőséget..

> [!TIP]
> Ha korlátozni szeretné végfelhasználókat abban, hogy önmagukat számítógépekkel kössék össze, engedélyezze **A felhasználók korlátozása abban, hogy önmagukat számítógépekhez csatolhassák** beállítást A **Microsoft Intune-ügynök beállításai** házirendben.

## Válasz távsegítségre vonatkozó kérésre
A felhasználók a felügyelt számítógépekre automatikusan telepített Microsoft Easy Assist Távsegítség funkciója segítségével kérhetnek segítséget. A kérések elküldésekor egy riasztás jelenik meg az Intune-konzolon.

> [!IMPORTANT]
> A távsegítség Windows 8 vagy újabb rendszert futtató számítógépeken nem támogatott.
>
> Ha olyan számítógépről fogad el távsegítségre vonatkozó kérést, amelyen nincs telepítve a Microsoft Easy Assist, akkor a rendszer felajánlja a felhasználónak a telepítését. A telepítés után a számítógépet újra kell indítani. Az újraindítás elkerülése érdekében fontolja meg a Microsoft Easy Assist előzetes feltöltését a felhasználók számítógépeire.

### Távsegítségre vonatkozó kérések felügyelete

1.  A [Microsoft Intune felügyeleti konzolon](https://manage.microsoft.com/) válassza a **Riasztások** &gt; **Távsegítség** elemet..

2.  A kérelem Tulajdonságok lapjának megnyitásához válassza ki a távsegítségre vonatkozó kérést a **Riasztások** listában.

3.  Válassza a **Kérelem jóváhagyása és távsegítség indítása** elemet egy párbeszédpanel megnyitásához, amely lehetőségeket kínál a riasztás feloldásához.

4.  Tegye a következők valamelyikét:

    -   **A kérés elfogadása** – A távoli munkamenethez való csatlakozáshoz válassza **A távsegítségkérés elfogadása** elemet..

        A felhasználónál a következő üzenet jelenik meg: **A rendszergazda elfogadta a kérést. A megfelelő programot vagy az asztal tartalmát az Easy Assist alkalmazásban található útmutatást követve oszthatja meg a rendszergazdával.**.

        > [!IMPORTANT]
        > Az Intune felügyeleti konzolt futtató Mac gépeken nem fogadhat el távsegítségre vonatkozó kéréseket.

    -   **A kérés elutasítása** – Zárja be a **Hibaelhárítási információk megjelenítése** ablakot, majd válassza **A riasztás bezárása** elemet a riasztás tulajdonságai ablakban.

        A kérés bezárul, és a felhasználó egy üzenetet kap, hogy a kérelmet elutasították. Távsegítség ismételt kéréséhez a felhasználónak új távsegítségre vonatkozó kérést kell küldenie. Ha véletlenül bezárta a távsegítségre vonatkozó riasztást, lépjen kapcsolatba a távsegítségre vonatkozó kérést küldő felhasználóval, és kérje meg, hogy küldjön egy új kérést.


<!--HONumber=May16_HO1-->


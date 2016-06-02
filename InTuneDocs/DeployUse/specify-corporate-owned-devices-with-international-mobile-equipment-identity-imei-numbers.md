---
# required metadata

title: Vállalati tulajdonban lévő eszközök megadása IMEI-számokkal | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 1712bd39-562b-4409-9cec-155d5f4d8a39

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Vállalati tulajdonban lévő eszközök megadása IMEI-számokkal
A Microsoft Intune lehetővé teszi, hogy a rendszergazdák nemzetközi mobilkészülék-azonosító (IMEI-) számokat importáljanak IMEI-számokkal rendelkező mobileszköz-platformok esetén, hogy könnyebben azonosítsák a vállalati tulajdonban lévő mobileszközöket. Az Intune-ban történő regisztráció után az importált IMEI-számokkal rendelkező eszközök Vállalati címkével rendelkeznek, amellyel a személyes eszközökre alkalmazott házirendektől eltérő házirendek alkalmazhatók.

1. A [Microsoft Intune felügyeleti konzolján](http://manage.microsoft.com) lépjen a  **Csoportok** &gt; **Minden eszköz** &gt; **Minden előre regisztrált vállalati eszköz** &gt; **IMEI szerint (minden platform)** területre, majd kattintson az **Eszközök felvétele** gombra. Két módon adhat hozzá eszközöket:

    -   **Sorozatszámokat tartalmazó CSV-fájl feltöltése** – Hozzon létre egy vesszővel elválasztott, kétoszlopos, fejléc nélküli értéklistát (.csv), amelyben maximum 5000 eszköz szerepel. A csv-fájl mérete nem haladja meg az 5 MB-ot.

        |||
        |-|-|
        |&lt;1. IMEI azonosító&gt;|&lt;1. eszköz részletei&gt;|
        |&lt;2. IMEI azonosító&gt;|&lt;2. eszköz részletei&gt;|
        Ez a .csv- fájl egy szövegszerkesztőben megtekintve így jelenik meg:

        ```
        AA-BBBBBB-CCCCCC-D,PO 1234
        AA-BBBBBB-CCCCCC-E,PO 1234
        ```

    -   **Eszközadatok kézi megadása** – Adja meg legfeljebb öt eszköz sorozatszámát és eszközrészleteit

   A *Részletek* adminisztrációs célokat szolgál, az eszközökkel társított IMEI-számok beazonosítása érdekében. Ezek az információk nem kerülnek át az eszközre, csak az Intune konzoljában jelennek meg.

2.   Kattintson a **Tovább** gombra..
3.  Az **Eszközök felülvizsgálata** panelen ellenőrizheti, hogy melyik IMEI-eszközszámok lettek importálva. Eldöntheti azt is, hogy felülírja-e az újraimportált IMEI-számok **Részleteit**. A **Felülírás** jelölőnégyzet jelölését törölve megőrizheti az aktuális részleteket. Kattintson a **Befejezés** gombra az IMEI-számok importálásához.
4.  A hozzáadott IMEI-számok és leírások az **IMEI szerint (minden platform)** listába kerülnek.

Amikor az adott IMEI-számmal rendelkező eszközt regisztrálják – általában akkor, amikor egy felhasználó telepíti a Vállalati portál alkalmazást, és elvégzi a regisztrációs folyamatot –, az eszköz Vállalati címkével fog rendelkezni, és regisztráltként jelenik meg az **IMEI-eszközök** csoportban.


<!--HONumber=May16_HO1-->


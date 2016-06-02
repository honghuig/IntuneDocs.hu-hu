---
# required metadata

title: Vállalati tulajdonban lévő eszközök regisztrálása az Eszközregisztráció-kezelővel a Microsoft Intune-ban | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Vállalati tulajdonban lévő eszközök regisztrálása az Eszközregisztráció-kezelővel
A szervezetek az Intune használatával nagyszámú mobileszközt felügyelhetnek egyetlen felhasználói fiókkal. Az *eszközregisztráció-kezelői* fiók több mint öt eszköz regisztrálására vonatkozó engedéllyel rendelkező speciális Intune-fiók. Hozzárendelhet egy tárolókezelői vagy felügyeleti, például eszközregisztráció-kezelői felhasználói fiókot, hogy végrehajthassa az alábbiakat:

-   Eszközök regisztrálása az Intune-ban

-   Bejelentkezés vállalati portálra vállalati alkalmazások beszerzéséhez

-   Szoftverek telepítése és eltávolítása

-   Vállalati adatok elérésének konfigurálása

Csak olyan eszközökhöz használja az eszközkezelő fiókot, amely nem fogad e-mailt, illetve nem konkrét felhasználóként jelentkezik be. Az eszközkezelő fiókkal kezelt eszközökön nem konfigurálható a feltételes hozzáférés, hiszen ezek is felhasználónkénti forgatókönyvek. A tárolókezelő nem állíthatja alaphelyzetbe az eszközt a vállalati portálról.

**Eszközregisztráció-kezelői forgatókönyvek példái:**
Egy étterem pénztári táblagépeket szeretne beállítani a felszolgálóknak és rendelési monitorokat a konyhai személyzetnek. Az alkalmazottaknak nincs szükségük hozzáférésre a vállalati adatokhoz, illetve nem kell felhasználóként bejelentkezniük. Az Intune-rendszergazda létrehoz egy eszközregisztráció-kezelői fiókot, és a fiókot használva regisztrálja a vállalat tulajdonában álló eszközöket. Másik lehetőségként a rendszergazda eszközregisztráció-kezelői hitelesítő adatokat adhat egy étterem vezetőjének, lehetővé téve, hogy regisztrálja és felügyelje az eszközöket.

A rendszergazda vagy vezető szerepkör-specifikus alkalmazásokat telepíthet az éttermi eszközökre. A rendszergazdák kijelölhetik az eszközt az Intune-konzolon, és a felügyeleti konzollal kivonhatják a mobileszköz-felügyelet alól.

> [!NOTE]
> A több mint 20 regisztrált eszközzel rendelkező eszközregisztráció-kezelői felhasználói fiókoknak problémái lehetnek a Vállalati portál alkalmazás használatával. A vállalati alkalmazások eszközregisztráció-kezelővel felügyelt eszközökre történő telepítéséhez telepítse a Vállalati portál alkalmazást **Szükséges telepítésként** az eszközregisztráció-kezelő felhasználói fiókjára.

## Eszközregisztráció-kezelői fiókok létrehozása
Az eszközregisztráció-kezelői fiókok nagyszámú vállalati eszköz regisztrálására vonatkozó engedéllyel rendelkező felhasználói fiókok. Csak az Intune-konzolon szereplő felhasználók lehetnek eszközregisztráció-kezelők.

#### Eszközregisztráció-kezelő hozzáadása az Intune-hoz

1.  Nyissa meg a [Microsoft Intune fiókportált](http://go.microsoft.com/fwlink/?LinkId=698854), és jelentkezzen be a rendszergazdai fiókjával.

2.  Kattintson a **Felhasználó hozzáadása** elemre..

3.  Győződjön meg arról, hogy a listán szerepel az a felhasználói fiók, amely az eszközregisztráció-kezelő lesz. Ha nem szerepel, az **Új** elemre kattintva és a felhasználó-hozzáadási folyamatot végrehajtva vegye fel a felhasználót. Előfizetési licencre van szükség minden olyan felhasználóhoz, aki hozzáfér a szolgáltatáshoz, és az *eszközregisztráció-kezelő* nem lehet Intune-rendszergazda. Határozza meg, hogy a szolgáltatás használata előtt hozzá kell-e adnia további licenceket.

4.  Jelentkezzen be a [Microsoft Intune felügyeleti konzolra](http://manage.microsoft.com) a rendszergazdai bejelentkezési adataival.

5.  A navigációs ablaktáblában kattintson a **Rendszergazda**elemre, lépjen a **Rendszergazdai felügyelet** beállításra, és válassza az **Eszközregisztráció-kezelő**lehetőséget. Megnyílik az Eszközregisztráció-kezelő lap.

6.  Kattintson a **Hozzáadás**lehetőségre. Megnyílik az **Eszközregisztráció-kezelő hozzáadása** párbeszédpanel.

7.  Adja meg az Intune-fiók **felhasználói azonosítóját** , és kattintson az **OK**gombra. Az eszközregisztráció-kezelő felhasználó nem lehet Intune-rendszergazda.

8.  Az eszközregisztráció-kezelő most már ugyanazzal az eljárással regisztrálhat mobileszközöket, amelyet a végfelhasználók használnak a vállalati portálon a saját eszközök használata esetén.

## Eszközregisztráció-kezelő törlése az Intune-ból

1.  Jelentkezzen be a [Microsoft Intune felügyeleti portálra](http://manage.microsoft.com) a rendszergazdai bejelentkezési adataival.

2.  A navigációs ablaktáblában kattintson a **Rendszergazda** elemre, lépjen a **Rendszergazdai felügyelet** beállításra, és válassza az **Eszközregisztráció-kezelő**lehetőséget. Megnyílik az Eszközregisztráció-kezelő lap.

3.  Jelölje ki a törölni kívánt eszközregisztráció-kezelő **felhasználót** , és kattintson a **Törlés**lehetőségre. Ez a felhasználó nem törlődik az Intune-ból, és a felhasználó által felügyelt eszközök regisztrálása megmarad az Intune-ban. Az eszközregisztráció-kezelő törlése megakadályozza, hogy az adott felhasználó további eszközöket regisztráljon az Intune-ban.

4.  Kattintson az **Igen** lehetőségre az eszközregisztráció-kezelő törlésének a jóváhagyásához.

Az eszközregisztráció-kezelő törlése nincs hatással a regisztrált eszközökre. Az eszközregisztráció-kezelő törlésekor:

-   A regisztrált eszközöket nem érinti

-   A regisztrált eszközök továbbra is teljes mértékben felügyeltek

-   A törölt eszközregisztráció-kezelői fiók hitelesítő adatai továbbra is érvényesek a bejelentkezéshez a vállalati portálra az alkalmazások eléréséhez

-   A törölt eszközregisztráció-kezelői fiók hitelesítő adatai nem törölhetik vagy vonhatják vissza az eszközöket

-   A törölt eszközregisztráció-kezelői fiók kapcsolata megmarad a regisztrált fiókokkal, de további eszközöket nem lehet regisztrálni


<!--HONumber=May16_HO1-->


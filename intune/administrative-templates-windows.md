---
title: Sablonok használata Windows 10-es eszközökhöz a Microsoft Intune-Azure-ban | Microsoft Docs
description: A Windows 10-es eszközökhöz tartozó beállítási csoportok létrehozásához használja a Microsoft Intune felügyeleti sablonjait. Ezekkel a beállításokkal konfigurálhatja az Office-programokat, a biztonságos szolgáltatásokat az Internet Explorerben, vezérelheti a OneDrive elérését, a távoli asztal funkcióinak használatát, az Automatikus lejátszást, az energiagazdálkodási beállítások beállítását, a HTTP-nyomtatás használatát, a különböző funkciók használatát felhasználói bejelentkezés beállításai és az Eseménynapló méretének szabályozása.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0bfad3feed6daef1930c235bec9c25e809da46c5
ms.sourcegitcommit: ce9cae824a79223eab3c291fd5d5e377efac84cb
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/12/2019
ms.locfileid: "67842743"
---
# <a name="use-windows-10-templates-to-configure-group-policy-settings-in-microsoft-intune"></a>Csoportházirend-beállítások konfigurálása a Windows 10-es sablonokkal Microsoft Intune

A szervezeten belüli eszközök kezelésekor olyan beállításokat szeretne létrehozni, amelyek a különböző eszközök csoportjaira vonatkoznak. Például több eszközosztály is van. A Groupa esetében a beállítások egy adott készletét szeretné hozzárendelni. A GroupB esetében más beállításokat szeretne hozzárendelni. Azt is szeretné, hogy a konfigurálható beállítások egyszerű áttekintése legyen.

Ezt a feladatot Microsoft Intune **Felügyeleti sablonok** használatával végezheti el. A felügyeleti sablonok több száz olyan beállítást tartalmaznak, amelyek az Internet Explorer, Microsoft Office programok, a távoli asztal, a OneDrive, a jelszavak és a PIN-kódok funkcióit vezérlik. Ezek a beállítások lehetővé teszik a csoport rendszergazdái számára a csoportházirendek kezelését a felhő használatával.

A Windows beállításai hasonlóak a csoportházirend (GPO) beállításaihoz Active Directory (AD). Ezek a beállítások a Windowsba vannak építve, és az [ADMX-alapú beállítások](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies) (egy másik Microsoft-webhely megnyitása), amely XML-t használ. Az Office-beállítások az ADMX-betöltés alatt állnak, és az ADMX-beállításokat használják az [Office felügyeleti sablon fájljaiban](https://www.microsoft.com/download/details.aspx?id=49030). Az Intune-sablonok azonban 100%-os felhő-alapúak. Egyszerű és közvetlen továbbítási módot kínálnak a beállítások konfigurálásához, és megkeresik a kívánt beállításokat.

**Felügyeleti sablonok** beépítettek az Intune-ba, és nincs szükség testreszabásra, beleértve az OMA-URI használatát is. A mobileszköz-kezelési (MDM) megoldás részeként ezeket a sablonokat a Windows 10-es eszközök felügyeletéhez használja egyablakos szolgáltatásként.

Ez a cikk a Windows 10-es eszközökhöz készült sablonok létrehozásának lépéseit ismerteti, és bemutatja, hogyan szűrheti az összes elérhető beállítást az Intune-ban. A sablon létrehozásakor létrehoz egy eszköz-konfigurációs profilt. Ezt a profilt ezután hozzárendelheti vagy üzembe helyezheti a szervezet Windows 10-es eszközein.

## <a name="before-you-begin"></a>Előkészületek

- Ezen beállítások némelyike a Windows 10 1703-es (RS2) verziótól kezdődően érhető el. A legjobb megoldás az, ha a Windows 10 Enterprise 1903 (19H1) és újabb verzióját használja.

- A Windows-beállítások a [Windows házirend](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies) -kriptográfiai szolgáltatásait használják (egy másik Microsoft-webhelyet nyit meg). A kriptográfiai szolgáltatók a Windows különböző kiadásaiban működnek, például a Home, a Professional, a Enterprise stb. Ha szeretné megtekinteni, hogy a CSP egy adott kiadáson működik-e, lépjen a [Windows házirend](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies) -kriptográfiai (egy másik Microsoft-webhely megnyitása) elemre

## <a name="create-a-template"></a>Sablon létrehozása

1. Jelentkezzen be az [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-ba.
2. Válassza az **Eszközkonfiguráció** > **Profilok** > **Profil létrehozása** lehetőséget.
3. Adja meg a következő tulajdonságokat:

    - **Név**: Adja meg a profil nevét.
    - **Description** (Leírás): Adja meg a profil leírását. A beállítás használata nem kötelező, de ajánlott.
    - **Platform**: Válassza **a Windows 10 és újabb**lehetőséget.
    - **Profil típusa**: Válassza a **Felügyeleti sablonok**lehetőséget.

4. Kattintson a **Létrehozás** gombra. Az új ablakban válassza a **Beállítások**lehetőséget. Minden beállítás fel van sorolva, és az előző és a következő nyilak használatával további beállításokat tekinthet meg:

    ![Tekintse meg a beállítások listáját, és használja az előző és a tovább gombokat](./media/administrative-templates-windows/administrative-templates-sample-settings-list.png)

    > [!TIP]
    > Az Intune-ban található Windows-beállítások a helyi csoportházirend elérési útjára vonatkoznak Helyicsoportházirend-szerkesztő (`gpedit`).

5. Alapértelmezés szerint a legördülő lista az **összes terméket**megjeleníti. A listából úgy is szűrheti a beállításokat, hogy csak a **Windows** -beállításokat jelenjen meg, vagy csak az **Office** -beállításokat jeleníti meg:

    ![A lista szűrése az összes Windows vagy az összes Office-beállítás megjelenítéséhez a felügyeleti sablonokban az Intune-ban](./media/administrative-templates-windows/administrative-templates-choose-windows-office-all-products.png)

6. Válassza ki a kívánt beállításokat. Például az **Office**-on, és válassza a **korlátozott böngészés aktiválása**lehetőséget. Megjelenik a beállítás részletes leírása. Válassza az **engedélyezve**, Letiltva lehetőséget, vagy hagyja meg a beállítást **nincs konfigurálva** (alapértelmezett). A részletes leírás azt is ismerteti, hogy mi történik, ha az **engedélyezve**, a Letiltva vagy a **nincs konfigurálva**beállítást választja.
7. Válassza ki **OK** a módosítások mentéséhez.

Folytassa a beállítások listájának átadását, és konfigurálja a kívánt beállításokat a környezetében. Néhány példa:

- A **VBA-makró értesítési beállításainak** beállításával különböző Microsoft Office programokban, például a Wordben és az Excelben kezelheti a VBA-makrókat.
- A fájlok letöltésének **engedélyezése** beállítással engedélyezheti vagy tilthatja le a letöltéseket az Internet Explorerben.
- A **jelszó kérése, ha a számítógép felébred (csatlakoztatva)** beállítást, hogy a felhasználók jelszót kérjenek, amikor az eszközök alvó üzemmódból felébrednek.
- Az aláíratlan **ActiveX-vezérlők letöltése** beállítással megakadályozhatja, hogy a felhasználók aláíratlan ActiveX-vezérlőket töltsenek le az Internet Explorerben.
- A **rendszer-visszaállítás kikapcsolása** beállítás használatával engedélyezheti vagy megakadályozhatja, hogy a felhasználók futtassák a rendszer-visszaállítást az eszközön.
- És még sok más...

## <a name="find-some-settings"></a>Néhány beállítás megkeresése

Ezekben a sablonokban több száz beállítás érhető el. A beépített funkciókkal könnyebben megtalálhatja a konkrét beállításokat:

- A sablonban válassza a **Beállítások**, az **állapot**, a **beállítás típusa**vagy az **elérési út** oszlopok elemet a lista rendezéséhez. Például a Path ( **elérési út** ) oszlopra kattintva megtekintheti `Microsoft Excel` az elérési út összes beállítását:

  ![Kattintson a Path (elérési út) elemre a csoportházirend vagy az ADMX elérési útja szerint csoportosított összes beállítás megjelenítéséhez az Intune-ban.](./media/administrative-templates-windows/path-filter-shows-excel-options.png)

- A sablonban a **keresőmező** segítségével megtalálhatja a kívánt beállításokat. A kereséshez állítsa be a címet vagy az elérési utat. Keresse meg például a következőt `copy`:. Az összes beállítás `copy` látható:

  ![Az Intune-beli felügyeleti sablonokban található összes Windows-és Office-beállítás megjelenítésének keresése a másolásban](./media/administrative-templates-windows/search-copy-settings.png) 

  Egy másik példában keresse meg a `microsoft word`következőt:. Megjelenik a Microsoft Word programhoz beállítható összes beállítás. A kifejezésre `explorer` való kereséssel megtekintheti a sablonhoz felvehető Internet Explorer-beállításokat.

## <a name="next-steps"></a>További lépések

A sablon létre lett hozva, de még nem csinál semmit. Ezután [rendelje hozzá a sablont, más néven profilt](device-profile-assign.md) , és [Figyelje annak állapotát](device-profile-monitor.md).

---
# required metadata

title: Mobileszközök regisztrálása és alkalmazások telepítése| Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 5d3215e7-0a5c-44bd-afb0-aeafce98c43f

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Mobileszközök regisztrálása és alkalmazások telepítése
Az Intune szolgáltatással történő mobileszköz-kezelés beállításához először meg kell adnia a mobileszköz-kezelő szolgáltatót, engedélyeznie kell a mobileszköz-kezelést az eszközplatformhoz, majd regisztrálnia kell az eszközöket a Vállalati portál alkalmazással. Ezután telepítheti a 6. lépésben közzétett Microsoft Skype alkalmazást.

## Eszközkezelés engedélyezése és eszközök regisztrálása

1.  **Az Intune beállítása mobileszköz-kezelő szolgáltatóként**
    Az [Intune felügyeleti konzolon](https://manage.microsoft.com/) kattintson a **Felügyelet** > **Mobileszköz-kezelés** lehetőségre, majd válassza az **MDM-szolgáltató megadása** lehetőséget a **Feladatok** területen.  Kattintson a Mobileszköz-kezelő szolgáltató párbeszédpanel **Igen** gombjára.
    ![Felügyeleti konzol. Mobileszköz-kezelés beállítása az Intune-hoz](./media/mdmAuthority.png)

2.  **Mobileszköz-kezelés engedélyezése az eszközplatformhoz**
    A mobileszköz-kezelés engedélyezése a kezelni kívánt eszközplatform esetén. A követelmények a platformtól függően eltérőek:

    -   **iOS és Mac OS X** esetén lásd: [iOS- és Mac-eszközök kezelésének beállítása a Microsoft Intune-ban](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) című témakört..

    -   **Windows Phone** rendszer esetén lásd: [Windows Phone-telefonok Microsoft Intune-beli kezelésének beállítása](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune)..

    -   **Android**: A felhasználók a [Google Play](https://play.google.com/store/apps/details?id=com.skype.raider) áruházból letölthető Vállalati portál alkalmazással regisztrálhatják androidos mobileszközeiket. Így nincs szükség további Intune konfigurációra.

3.  **Eszközök regisztrálása**:

    -   **Android** – Telepítse a Microsoft Corporation által kiadott **Intune Vállalati portál** alkalmazást, melyet a [Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612) áruházban érhet el, és jelentkezzen be az Intune szolgáltatás fent megadott hitelesítő adataival.

    -   **iOS és Mac OS X** – Telepítse a Microsoft Corporation által kiadott **Microsoft Intune Vállalati portál** alkalmazást, melyet az App Store áruházban érhet el, és jelentkezzen be az Intune fent megadott hitelesítő adataival. Az eszköz felvételéhez tekintse át a **Regisztrált eszközök** listát.

    -   **Windows Phone 8.1** – Telepítse a Microsoft Corporation által kiadott **Vállalati portál** alkalmazást, melyet a Windows Phone Áruházban érhet el, és jelentkezzen be az Intune szolgáltatás fent megadott hitelesítő adataival.  Az eszköz felvételéhez tekintse át a **Regisztrált eszközök** listát.

    -   **Windows Phone 8.0** – A felhasználóknak a **Rendszerbeállítások** &gt; **Vállalati alkalmazások** lehetőségre kell kattintaniuk, és be kell jelentkezniük az Intune-hoz fent megadott felhasználói hitelesítő adatokkal. A telefonján ezzel meg is történt a vállalati portál alkalmazás telepítése.

    Ha a program a **kiszolgáló címét**kéri, írja be a manage.microsoft.com címet.

## Alkalmazás telepítése egy regisztrált eszközre
Az első lépéseket ismertető jelen útmutató [6. lépésében](start-with-a-paid-subscription-to-microsoft-intune-step-6.md) közzétette a Skype alkalmazást a saját Intune-felhasználók csoportja számára. Most ezt az alkalmazást egy újonnan regisztrált eszközre fogja telepíteni.

Nyissa meg a Vállalati portált a regisztrált mobileszközön, majd válassza az **Alkalmazások** lehetőséget, és telepítse a **Microsoft Skype** alkalmazást..

A mobileszközök [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-nal történő kezelésével kapcsolatosan bővebb információk a [Felkészülés az eszközök regisztrálására a Microsoft Intune-ban](/intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune) című témakörben olvashatók..


### További lépések
Gratulálunk! Ezzel befejezte az *Intune – Első lépések útmutatójának* utolsó lépését. Most, hogy a kezdeti konfigurálást befejezte, további MDM-funkciók engedélyezését is fontolóra veheti.

>[!div class="step-by-step"]

>[&larr; **Eszközök regisztrálása**](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)     [**Konfigurációt követő feladatok** &rarr;](.\post-configuration-tasks.md)  


<!--HONumber=May16_HO1-->


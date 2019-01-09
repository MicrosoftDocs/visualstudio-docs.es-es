---
title: Beneficio de WhiteSource Bolt | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 12/19/2018
ms.topic: Get-Started-Article
description: Obtenga más información sobre cómo activar la suscripción de WhiteSource Bolt que se incluye con la suscripción a Visual Studio.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: d9f4db463dad3ee2fbb216284791018dc504d7b6
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2018
ms.locfileid: "53739989"
---
#  <a name="whitesource-bolt-in-visual-studio-subscriptions"></a>WhiteSource Bolt en las suscripciones de Visual Studio

Descubra y corrija vulnerabilidades del código abierto y genere informes completos de inventario y licencias de todos los componentes de código abierto de su compilación. Algunas suscripciones de Visual Studio incluyen seis meses de acceso gratuito.

## <a name="activation-steps"></a>Pasos para la activación

1. Para activar el beneficio de WhiteSource Bolt, inicie sesión en [https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs) .

2. Busque el icono de WhiteSource Bolt en la sección Herramientas y haga clic en el vínculo **Obtener código** en la parte inferior del icono del beneficio.
   > [!div class="mx-imgBorder"]
   > ![Icono de la ventaja WhiteSource Bolt](_img/vs-whitesource/vs-whitesource-tile.png)

3. Recibirá una notificación con el código de activación.  **Copie el código en el Portapapeles** y haga clic en **Activar**.
   > [!div class="mx-imgBorder"]
   > ![Código de la ventaja WhiteSource Bolt](_img/vs-whitesource/vs-whitesource-code.png)

4. En la página web de WhiteSource, haga clic en el botón **Activar** o desplácese hacia abajo hasta la sección **Activate your account** (Activación de la cuenta).
   > [!div class="mx-imgBorder"]
   > ![Activación de la ventaja WhiteSource Bolt](_img/vs-whitesource/vs-whitesource-activate-page-cropped.png)

5. En la sección **Activate your account** (Activación de la cuenta) de la página, se le guiará a través de cuatro pasos:

   - [Instale](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt) la extensión de WhiteSource Bolt desde Microsoft Visual Studio Marketplace. Si no tiene permisos para instalar las extensiones, consulte [Install free extensions for Azure DevOps Services](/azure/devops/marketplace/install-vsts-extension?view=vsts) (Instalar extensiones gratuitas para Azure DevOps Services).


~~~
Click the green **Install** button if you are using Azure DevOps Services, or the **Download** button for Team Foundation Server.  For this example, we will use Azure DevOps Services.
> [!div class="mx-imgBorder"]
> ![WhiteSource Benefit Install Extension](_img\vs-whitesource\vs-whitesource-download-install.png)

- Next, select the Azure DevOps organization you want to use and click **Confirm**.  (If you have not yet set up Azure DevOps Services, visit the [Benefits](https://my.visualstudio.com/benefits) page and activate your Azure DevOps Services benefit.)

> [!div class="mx-imgBorder"]
> ![WhiteSource Benefit Confirm Account](_img\vs-whitesource\vs-whitesource-confirm-account.png)

- You’ll receive a confirmation that the extension is installed and ready to use.  Click **Get started** to return to the WhiteSource Bolt page and continue.
> [!div class="mx-imgBorder"]
> ![WhiteSource Benefit Install Complete](_img\vs-whitesource\vs-whitesource-install-complete.png)
~~~

5. Abra el panel del proyecto de Azure DevOps Services, haga clic en el menú **Azure Pipelines** y elija **WhiteSource Bolt**.
   > [!div class="mx-imgBorder"]
   > ![Agregar la extensión de la ventaja WhiteSource](_img/vs-whitesource/vs-whitesource-installed-cropped.png)

6. Pegue el código de activación del icono de la ventaja WhiteSource Bolt y haga clic en **Activar**. Cada uno de los códigos de activación solo puede usarse para activar un proyecto.
   > [!div class="mx-imgBorder"]
   > ![Activación del código de la ventaja WhiteSource Bolt](_img/vs-whitesource/vs-whitesource-activate-code-cropped.png)

7. La activación ya se ha completado y dispondrá de 180 días restantes en la suscripción.

8. Tendrá que agregar la extensión de WhiteSource Bolt como uno de los pasos de la compilación.  Hay un vídeo disponible en la [página de WhiteSource Bolt](https://www.whitesourcesoftware.com/whitesource_bolt_visualstudio_2017/#activate) en el que se indica cómo hacerlo.

9. Cuando haya ejecutado la compilación, se generarán automáticamente los siguientes informes y paneles completos:
    - Panel de vulnerabilidades de seguridad
    - Informe de vulnerabilidades de seguridad
    - Informe de bibliotecas obsoletas
    - Panel de riesgos y cumplimiento de licencias
    - Informe de inventario

## <a name="eligibility"></a>Elegibilidad

| Nivel de suscripción                                                 |     Canales                                            | Prestación                                                          | ¿Renovable?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (estándar)   | Licencia por volumen, Azure, venta directa, no para reventa<sup>1</sup> | 6 meses       |  Sí          |
| Visual Studio Professional (estándar) | Licencia por volumen, Azure, venta directa                                       | No disponible                                                           |NA         |
| Visual Studio Test Professional (estándar)                         | Licencia por volumen, venta directa                                              | No disponible                                             |  NA         |
| Plataformas MSDN (estándar)                                          | Licencia por volumen, venta directa                                              | No disponible                                              | NA         |
| Visual Studio Dev Essentials | NA  | No disponible |NA |
| Visual Studio Enterprise, Visual Studio Professional (de nube mensual) | Azure                                       | No disponible                                                           |NA|

<sup>1</sup>  *Incluye:  Microsoft Partner Network (Enterprise).  Excluye: Otros No para reventa (NFR), Visual Studio Industry Partner (VSIP), FTE, MCT Software & Services Developer, BizSpark, Imagine, Microsoft Valued Professional (MVP), Region Director (RD), MCT Software & Services, Microsoft Partner Network (Professional).*


> [!NOTE]
> Microsoft ya no ofrece suscripciones anuales ni de Visual Studio Professional ni de Visual Studio Enterprise en las suscripciones de nube. Esto no supone cambio alguno en la experiencia actual de los clientes y ni en su capacidad para renovar, aumentar, reducir o cancelar las suscripciones. Conviene que los clientes nuevos vayan a [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) para explorar las diferentes opciones de compra de Visual Studio.


¿No sabe con seguridad qué suscripción usa?  Conéctese a [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) para ver todas las suscripciones asignadas a su dirección de correo electrónico. Si no ve todas las suscripciones, es posible que haya una o varias asignadas a una dirección de correo electrónico diferente.  Debe iniciar sesión con esa dirección de correo electrónico para ver esas suscripciones.

## <a name="support-resources"></a>Recursos de soporte técnico

-  ¿Necesita ayuda con WhiteSource Bolt?  Hable con un representante de WhiteSource Bolt en vivo en https://www.whitesourcesoftware.com/vse_whitesource_bolt/.
-  Para obtener ayuda con las ventas, las suscripciones, las cuentas y la facturación para suscripciones de Visual Studio, póngase en contacto con el [soporte para suscripciones](https://visualstudio.microsoft.com/subscriptions/support/) de Visual Studio.
-  ¿Tiene alguna pregunta sobre el IDE de Visual Studio, Azure DevOps Services u otros productos o servicios de Visual Studio?  Visite el [soporte técnico de Visual Studio](https://visualstudio.microsoft.com/support/).
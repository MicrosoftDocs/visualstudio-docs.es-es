---
title: Ventaja WhiteSource Bolt
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: "Obtenga más información sobre cómo activar la suscripción de WhiteSource Bolt que se incluye con la suscripción a Visual Studio."
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: c1976d9eaa6ef18978a9e9d5453c3080741223d5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
#  <a name="activating-the-whitesource-bolt-benefit-in-visual-studio-subscriptions"></a>Activación de la ventaja WhiteSource Bolt en suscripciones de Visual Studio

Descubra y corrija vulnerabilidades del código abierto y genere informes completos de inventario y licencias de todos los componentes de código abierto de su compilación.  La suscripción Enterprise incluye una suscripción gratuita de seis meses. 

1.  Para usar la ventaja WhiteSource Bolt, haga clic en el vínculo **Obtener código** que se encuentra en la parte inferior del icono de la ventaja.    

![Icono de la ventaja WhiteSource Bolt](_img\vs-whitesource\vs-whitesource-tile.png)

2.  Recibirá una notificación con el código de activación.  **Copie el código en el Portapapeles** y haga clic en **Activar**. 

![Código de la ventaja WhiteSource Bolt ](_img\vs-whitesource\vs-whitesource-code.png)

3.  En la página web de WhiteSource, haga clic en el botón **Activar** o desplácese hacia abajo hasta la sección **Activate your account** (Activación de la cuenta).  

![Activación de la ventaja WhiteSource Bolt](_img\vs-whitesource\vs-whitesource-activate-page-cropped.png)

4.  En la sección **Activate your account** (Activación de la cuenta) de la página, se le guiará a través de cuatro pasos:
- [Instale](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt) la extensión de WhiteSource Bolt desde Microsoft Visual Studio Marketplace. Si no dispone de permisos para instalar extensiones, visite [esta página](https://www.visualstudio.com/en-us/docs/marketplace/get-vsts-extensions#request).

    Haga clic en el botón verde **Instalar** si usa VSTS o, en el caso de Team Foundation Server, en el botón **Descargar**.  En este ejemplo se usará VSTS. 

![Instalación de la extensión de la ventaja WhiteSource Bolt](_img\vs-whitesource\vs-whitesource-download-install.png)

- Después, seleccione la cuenta de VSTS que quiere usar y haga clic en **Confirmar**.  (Si todavía no ha configurado VSTS, visite la página [Ventajas](https://my.visualstudio.com/benefits) y active la ventaja VSTS).

![Confirmación de la cuenta de la ventaja WhiteSource](_img\vs-whitesource\vs-whitesource-confirm-account.png)

- Recibirá una confirmación de que la extensión está instalada y lista para su uso.  Haga clic en **Comenzar** para volver a la página de WhiteSource Bolt y continuar.  

![Instalación de la ventaja WhiteSource completada](_img\vs-whitesource\vs-whitesource-install-complete.png)

5.  Abra el panel del proyecto de Visual Studio Team Services (VSTS), haga clic en el menú **Compilación y versión** y elija **WhiteSource Bolt**.

![Agregar la extensión de la ventaja WhiteSource](_img\vs-whitesource\vs-whitesource-installed-cropped.png)

6. Pegue el código de activación del icono de la ventaja WhiteSource Bolt y haga clic en **Activar**. Cada uno de los códigos de activación solo puede usarse para activar un proyecto. 

![Activación del código de la ventaja WhiteSource Bolt](_img\vs-whitesource\vs-whitesource-activate-code-cropped.png)

7.  La activación ya se ha completado y dispondrá de 180 días restantes en la suscripción. 
8.  Tendrá que agregar la extensión de WhiteSource Bolt como uno de los pasos de la compilación.  Hay un vídeo disponible en la [página de WhiteSource Bolt](https://www.whitesourcesoftware.com/whitesource_bolt_visualstudio_2017/#activate) en el que se indica cómo hacerlo.  
9. Cuando haya ejecutado la compilación, se generarán automáticamente los siguientes informes y paneles completos:
- Panel de vulnerabilidades de seguridad
- Informe de vulnerabilidades de seguridad
- Informe de bibliotecas obsoletas
- Panel de riesgos y cumplimiento de licencias
- Informe de inventario

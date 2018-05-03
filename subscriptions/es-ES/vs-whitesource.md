---
title: Beneficio de WhiteSource Bolt | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/11/2017
ms.topic: Get-Started-Article
description: Obtenga más información sobre cómo activar la suscripción de WhiteSource Bolt que se incluye con la suscripción a Visual Studio.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 0c2eed9efdcca076c20a240d60b4d38cdda23019
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
#  <a name="whitesource-bolt-in-visual-studio-subscriptions"></a>WhiteSource Bolt en las suscripciones de Visual Studio

Descubra y corrija vulnerabilidades del código abierto y genere informes completos de inventario y licencias de todos los componentes de código abierto de su compilación.  Algunas suscripciones de Visual Studio incluyen seis meses de acceso gratuito. 

## <a name="activation-steps"></a>Pasos para la activación

1.  Para activar el beneficio de WhiteSource Bolt, inicie sesión en [https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs) .

2.  Busque el icono de WhiteSource Bolt en la sección Herramientas y haga clic en el vínculo **Obtener código** en la parte inferior del icono del beneficio.    

    ![Icono de la ventaja WhiteSource Bolt](_img\vs-whitesource\vs-whitesource-tile.png)

2.  Recibirá una notificación con el código de activación.  **Copie el código en el Portapapeles** y haga clic en **Activar**. 

    ![Código de la ventaja WhiteSource Bolt ](_img\vs-whitesource\vs-whitesource-code.png)

3.  En la página web de WhiteSource, haga clic en el botón **Activar** o desplácese hacia abajo hasta la sección **Activate your account** (Activación de la cuenta).  

    ![Activación de la ventaja WhiteSource Bolt](_img\vs-whitesource\vs-whitesource-activate-page-cropped.png)

4.  En la sección **Activate your account** (Activación de la cuenta) de la página, se le guiará a través de cuatro pasos:
    - [Instale](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt) la extensión de WhiteSource Bolt desde Microsoft Visual Studio Marketplace. Si no dispone de permisos para instalar extensiones, visite [esta página](https://www.visualstudio.com/docs/marketplace/get-vsts-extensions#request).

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

## <a name="eligibility"></a>Elegibilidad
| Nivel de suscripción                                                 |     Canales                                            | Prestación                                                          | ¿Renovable?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (estándar, de nube anual)   | Licencia por volumen, Azure, venta directa, no para reventa<sup>1</sup> | 6 meses       |  Sí          |
| Visual Studio Professional (estándar, de nube anual) | Licencia por volumen, Azure, venta directa                                       | No disponible                                                           |NA         |
| Visual Studio Test Professional (estándar)                         | Licencia por volumen, venta directa                                              | No disponible                                             |  NA         |
| Plataformas MSDN (estándar)                                          | Licencia por volumen, venta directa                                              | No disponible                                              | NA         |
| Visual Studio Dev Essentials | NA  | No disponible |NA |
| Visual Studio Enterprise, Visual Studio Professional (de nube mensual) | Azure                                       | No disponible                                                           |NA|

<sup>1</sup>  *Incluye:  Microsoft Partner Network (Enterprise).  Excluye: Otros No para reventa (NFR), Visual Studio Industry Partner (VSIP), FTE, MCT Software & Services Developer, BizSpark, Imagine, Microsoft Valued Partner (MVP), Region Director (RD), MCT Software & Services, Microsoft Partner Network (Professional).*

¿No sabe con seguridad qué suscripción usa?  Conéctese a [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) para ver todas las suscripciones asignadas a su dirección de correo electrónico. Si no ve todas las suscripciones, es posible que haya una o varias asignadas a una dirección de correo electrónico diferente.  Debe iniciar sesión con esa dirección de correo electrónico para ver esas suscripciones. 


## <a name="support-resources"></a>Recursos de soporte técnico
-  ¿Necesita ayuda con WhiteSource Bolt?  Hable con un representante de WhiteSource Bolt en vivo en https://www.whitesourcesoftware.com/vse_whitesource_bolt/. 
-  Para obtener ayuda con las ventas, las suscripciones, las cuentas y la facturación para suscripciones de Visual Studio, póngase en contacto con el [soporte para suscripciones](https://www.visualstudio.com/subscriptions/support/) de Visual Studio.
-  ¿Tiene alguna pregunta sobre el IDE de Visual Studio, Visual Studio Team Services u otros productos o servicios de Visual Studio?  Visite el [soporte técnico de Visual Studio](https://www.visualstudio.com/support/). 


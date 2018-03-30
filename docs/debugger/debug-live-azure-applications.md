---
title: Depurar aplicaciones de Azure de ASP.NET en vivo - Visual Studio | Documentos de Microsoft
ms.description: Learn how to set snappoints and view snapshots with the Snapshot Debugger
ms.custom: mvc
ms.date: 03/16/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: adb22512-4d4d-40e5-9564-1af421b7087e
caps.latest.revision: 1
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 0382f720e73504147c5f38ba61b5407db039a487
ms.sourcegitcommit: 064f8678f4a918e1dce60285090a9803d37dc34b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2018
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Depurar aplicaciones de Azure de ASP.NET en directo con el depurador de instantánea

El depurador de instantánea toma una instantánea de las aplicaciones de producción cuando se ejecuta código que le interesa. Para indicar al depurador que tome una instantánea, establezca puntos de acoplamiento y puntos de registro en el código. El depurador le permite ver exactamente qué salió mal, sin afectar el tráfico de la aplicación de producción. El Depurador de instantáneas puede permitirle disminuir considerablemente el tiempo que tarda en resolver los problemas que se producen en los entornos de producción.

Snappoints y logpoints son similares a los puntos de interrupción, pero a diferencia de los puntos de interrupción, snappoints no detendrá la aplicación cuando se produce. Normalmente, la captura una instantánea en un snappoint tiene 10 a 20 milisegundos. 

La colección de instantáneas está disponible para las siguientes aplicaciones web que se ejecutan en Azure App Service:

- Aplicaciones ASP.NET que se ejecutan en .NET Framework 4.6.1 o versiones posteriores.
- Aplicaciones ASP.NET Core que se ejecutan en .NET Core 2.0 o posteriores en Windows.

Además, el depurador de instantánea solo está disponible para Visual Studio de 2017 Enterprise versión 15.5 o superior y los planes de servicio de aplicaciones básica o superiores. 

En este tutorial, aprenderá lo siguiente:

> [!div class="checklist"]
> * Iniciar al depurador de instantánea
> * Establecer un snappoint y ver una instantánea
> * Establecer un logpoint

## <a name="start-the-snapshot-debugger"></a>Iniciar al depurador de instantánea

1. Instalar [Visual Studio 2017 Enterprise versión 15,5](https://www.visualstudio.com/downloads/) o una versión posterior. Si está actualizando desde una instalación anterior de Visual Studio de 2017, ejecute al instalador de Visual Studio y compruebe el componente del depurador de instantánea en la carga de trabajo de desarrollo web y ASP.NET.

2. Abra el proyecto que le gustaría depuración instantánea. 

    > [!IMPORTANT] 
    > Para depurar de instantánea, deberá abrir el **misma versión de código fuente** que se publica en el servicio de aplicaciones de Azure. 

3. En el Explorador de la nube (**Vista > Explorador de nube**), haga clic en el proyecto se implementa en el servicio de aplicaciones de Azure y seleccione **adjuntar depurador de instantánea**.

   ![Iniciar al depurador de instantánea](../debugger/media/snapshot-launch.png)

    La primera vez que selecciona **adjuntar depurador de instantánea**, se le pedirá que instale la extensión del depurador de instantánea de sitio en el servicio de aplicaciones de Azure. Esta instalación requiere un reinicio del servicio en la aplicación de Azure. 

   Visual Studio ya está en modo de depuración de instantánea.

    > [!NOTE]
    > La extensión de sitio de Application Insights también admite la depuración instantánea. Si se produce un mensaje de error "no está actualizado de la extensión del sitio", consulte [solución de problemas de sugerencias y problemas conocidos para la depuración instantánea](../debugger/debug-live-azure-apps-troubleshooting.md) para actualizar los detalles.

   ![Modo de depuración instantánea](../debugger/media/snapshot-message.png)

   El **módulos** ventana muestra cuando todos los módulos han cargado para el servicio de aplicaciones de Azure (elija **Debug / Windows / módulos** para abrir esta ventana).

   ![Comprobación de la ventana módulos](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Establecer un snappoint

1. En el editor de código, haga clic en el margen interno izquierdo al lado de una línea de código que le interesen establecer un snappoint. Asegúrese de que se trata de código que sepa que se ejecutará.

   ![Establecer un snappoint](../debugger/media/snapshot-set-snappoint.png)

2. Haga clic en **iniciar colección** para activar el snappoint.  

   ![Activar la snappoint](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > No puede pasar al ver una instantánea, sino que puede colocar varios snappoints en el código de seguimiento de ejecución en diferentes líneas de código. Si tiene varios snappoints en el código, el depurador de instantánea se asegura de que las instantáneas correspondientes son de la misma sesión del usuario final. El depurador de instantánea será así incluso si hay muchos usuarios alcanzar la aplicación.

## <a name="take-a-snapshot"></a>Tomar una instantánea

Cuando se activa un snappoint, capturará una instantánea cada vez que se ejecuta la línea de código donde se coloca el snappoint. La ejecución puede deberse a una solicitud real en el servidor. Para forzar la snappoint de llamadas, vaya a la vista de explorador del sitio web y tomar las medidas necesarias que causan el snappoint se va a alcanzar.

## <a name="inspect-snapshot-data"></a>Inspeccionar los datos de instantánea

1. Cuando se visita el snappoint, aparece una instantánea en la ventana de herramientas de diagnóstico. Para abrir esta ventana, elija **Debug / Windows / Mostrar herramientas de diagnóstico**.

   ![Abrir un snappoint](../debugger/media/snapshot-diagsession-window.png)

1. Haga doble clic en el snappoint para abrir la instantánea en el editor de código.

   ![Inspeccionar los datos de instantánea](../debugger/media/snapshot-inspect-data.png)

   Desde esta vista, puede mantener el mouse sobre las variables para ver información sobre datos, utilice la **locales**, **inspecciones**, y **pila de llamadas** windows y también evaluar expresiones.

    El sitio Web de sí mismo está todavía activo y no afecta a los usuarios finales. Solo una instantánea se captura por snappoint de forma predeterminada: después de captura una instantánea se desactiva el snappoint. Si desea capturar otra instantánea en el snappoint, se puede volver a activar el snappoint haciendo clic en **actualización colección**.

También puede agregar más snappoints a la aplicación y activar con el **actualización colección** botón.

**¿Necesita ayuda?** Consulte la [solución de problemas y problemas conocidos](../debugger/debug-live-azure-apps-troubleshooting.md) y [preguntas más frecuentes sobre depuración instantánea](../debugger/debug-live-azure-apps-faq.md) páginas.

## <a name="set-a-conditional-snappoint"></a>Establecer un snappoint condicional

Si es difícil volver a un estado concreto en la aplicación, considere la posibilidad de si el uso de un snappoint condicional puede ayudar. Ayuda de snappoints condicional que evitar tomar una instantánea hasta que la aplicación entra en un estado deseado, por ejemplo, cuando una variable tiene un valor concreto que desea inspeccionar. Puede establecer condiciones de uso de expresiones, filtros, o el número de visitas.

#### <a name="to-create-a-conditional-snappoint"></a>Para crear un snappoint condicional

1. Haga clic en un icono de snappoint (la bola hueco) y elija **configuración**.

   ![Elija la configuración](../debugger/media/snapshot-snappoint-settings.png)

1. En la ventana de configuración snappoint, escriba una expresión.

   ![Escriba una expresión](../debugger/media/snapshot-snappoint-conditions.png)

   En la ilustración anterior, solo se toma la instantánea para la snappoint cuando `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Establecer un logpoint

Además de tomar una instantánea cuando se alcanza un snappoint, también puede configurar un snappoint para registrar un mensaje (es decir, crear una logpoint). Puede establecer logpoints sin tener que volver a implementar la aplicación. Logpoints se ejecutan prácticamente y no causar ningún impacto o los efectos secundarios a la aplicación en ejecución.

#### <a name="to-create-a-logpoint"></a>Para crear un logpoint

1. Haga clic en un icono de snappoint (el hexágonos azul) y elija **configuración**.

1. En la ventana de configuración snappoint, seleccione **acciones**.

    ![Crear un logpoint](../debugger/media/snapshot-logpoint.png)

1. En el campo de mensaje, puede escribir el nuevo mensaje de registro que desee registrar. También puede evaluar las variables en el mensaje de registro colocándolos dentro de llaves.

    Si elige **enviar a la ventana de salida**, cuando se visita el logpoint, el mensaje aparece en la ventana de herramientas de diagnóstico.

    ![Datos de Logpoint en la ventana de diagsession](../debugger/media/snapshot-logpoint-output.png)

    Si elige **envía al registro de aplicación**, cuando se visita el logpoint, aparece el mensaje en cualquier lugar que puede ver mensajes de `System.Diagnostics.Trace` (o `ILogger` en .NET Core), como [aplicación visión](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha aprendido cómo utilizar al depurador de instantánea. Puede obtener más información acerca de esta característica.

> [!div class="nextstepaction"]
> [P+F sobre depuración de instantáneas](../debugger/debug-live-azure-apps-faq.md)

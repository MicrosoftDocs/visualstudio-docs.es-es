---
title: Depurar aplicaciones de Azure de ASP.NET en vivo - Visual Studio | Documentos de Microsoft
ms.date: 12/06/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugger
ms.assetid: adb22512-4d4d-40e5-9564-1af421b7087e
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 5317c06dc5ff6515627e562d576785c2ff25a98a
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2018
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Depurar aplicaciones de Azure de ASP.NET en directo con el depurador de instantánea

El depurador de instantánea toma una instantánea de las aplicaciones de producción cuando se ejecuta código que le interesa. Para indicar al depurador que tome una instantánea, establezca puntos de acoplamiento y puntos de registro en el código. El depurador le permite ver exactamente qué salió mal, sin afectar el tráfico de la aplicación de producción. El Depurador de instantáneas puede permitirle disminuir considerablemente el tiempo que tarda en resolver los problemas que se producen en los entornos de producción.

Snappoints y logpoints son similares a los puntos de interrupción. A diferencia de los puntos de interrupción, snappoints no detienen la aplicación cuando se produce. Normalmente, la captura una instantánea en un snappoint tiene 10 a 20 milisegundos. 

La colección de instantáneas está disponible para las siguientes aplicaciones web que se ejecutan en Azure App Service:

- Aplicaciones ASP.NET que se ejecutan en .NET Framework 4.6.1 o versiones posteriores.
- Aplicaciones ASP.NET Core que se ejecutan en .NET Core 2.0 o posteriores en Windows.

Además, el depurador de instantánea solo está disponible para Visual Studio de 2017 Enterprise versión 15.5 o superior y los planes de servicio de aplicaciones básica o superiores. 

## <a name="start-the-snapshot-debugger"></a>Iniciar al depurador de instantánea

1. Instalar [Visual Studio 2017 Enterprise versión 15,5](https://www.visualstudio.com/downloads/) o una versión posterior. Si está actualizando desde una instalación anterior de Visual Studio de 2017, ejecute al instalador de Visual Studio y compruebe el componente del depurador de instantánea en la carga de trabajo de desarrollo web y ASP.NET.

2. Abra el proyecto que le gustaría depuración instantánea. 

    > [!IMPORTANT] 
    > En orden para depuración instantánea, deberá abrir el **misma versión de código fuente** que se publica en el servicio de aplicaciones de Azure. 

3. En el Explorador de la nube (seleccione **Vista > Explorador de nube**), haga clic en el proyecto se implementa en el servicio de aplicaciones de Azure y seleccione **adjuntar depurador de instantánea** para iniciar el depurador de instantánea.

   ![Iniciar el depurador de instantánea](../debugger/media/snapshot-launch.png "iniciar el depurador de instantánea")

    La primera vez que selecciona **adjuntar depurador de instantánea**, se le pedirá que instale la extensión del depurador de instantánea de sitio en el servicio de aplicaciones de Azure. Esta instalación requiere un reinicio del servicio en la aplicación de Azure. 

   Visual Studio ya está en modo de depuración de instantánea.

    > [!NOTE]
    > La extensión de sitio de Application Insights también admite la depuración instantánea. Si se produce un mensaje de error "no está actualizado de la extensión del sitio", vea [solución de problemas de sugerencias y problemas conocidos para la depuración instantánea](../debugger/debug-live-azure-apps-troubleshooting.md) para actualizar los detalles.

   ![Modo de depuración de instantánea](../debugger/media/snapshot-message.png "el modo de depuración instantánea")

   El **módulos** ventana muestra cuando todos los módulos han cargado para el servicio de aplicaciones de Azure (elija **Debug / Windows / módulos** para abrir esta ventana).

   ![Compruebe la ventana módulos](../debugger/media/snapshot-modules.png "comprobar la módulos (ventana)")

## <a name="set-a-snappoint"></a>Establecer un snappoint

1. En el editor de código, haga clic en el margen interno izquierdo al lado de una línea de código que le interesen establecer un snappoint. Asegúrese de que se trata de código que sepa que se ejecutará.

   ![Establecer un snappoint](../debugger/media/snapshot-set-snappoint.png "establecer un snappoint")

2. Haga clic en **iniciar colección** para activar el snappoint.  

   ![Activar la snappoint](../debugger/media/snapshot-start-collection.png "activar el snappoint")

    > [!TIP]
    > No puede pasar al ver una instantánea, sino que puede colocar varios snappoints en el código de seguimiento de ejecución en diferentes líneas de código. Si tiene varios snappoints en el código, el depurador de instantánea garantiza que las instantáneas correspondientes están en la misma sesión del usuario final, incluso si hay varios usuarios alcanzar la aplicación.

## <a name="take-a-snapshot"></a>Tomar una instantánea

Cuando se activa un snappoint, capturará una instantánea cada vez que se ejecuta la línea de código donde se coloca el snappoint. La ejecución puede deberse a una solicitud real en el servidor. Para forzar la snappoint se alcanza, también puede ir a la vista del explorador de su sitio web y realice que las acciones necesitan que causan el snappoint se va a alcanzar.

## <a name="inspect-snapshot-data"></a>Inspeccionar los datos de instantánea

1. Cuando se visita el snappoint, aparece una instantánea en la ventana de herramientas de diagnóstico. Elija **Debug / Windows / Mostrar herramientas de diagnóstico** para abrir esta ventana.

   ![Abrir un snappoint](../debugger/media/snapshot-diagsession-window.png "abrir un snappoint")

1. Haga doble clic en el snappoint para abrir la instantánea en el editor de código.

   ![Inspeccionar los datos de instantánea](../debugger/media/snapshot-inspect-data.png "inspeccionar los datos de instantánea")

   Desde esta vista, puede mantener el mouse sobre las variables para ver información sobre datos, utilice la **locales**, **inspecciones**, y **pila de llamadas** windows y también evaluar expresiones.

    El sitio Web de sí misma sigue siendo en vivo y no afectan a los usuarios finales. Solo una instantánea se captura por snappoint de forma predeterminada: después de captura una instantánea se desactiva el snappoint. Si desea capturar otra instantánea en el snappoint, se puede volver a activar el snappoint haciendo clic en **actualización colección**.

También puede agregar más snappoints a la aplicación y activar con el **actualización colección** botón.

**¿Necesita ayuda?** Consulte la [solución de problemas y problemas conocidos](../debugger/debug-live-azure-apps-troubleshooting.md) y [preguntas más frecuentes sobre depuración instantánea](../debugger/debug-live-azure-apps-faq.md) páginas.

## <a name="set-a-conditional-snappoint"></a>Establecer un snappoint condicional

Si es difícil volver a un estado concreto en la aplicación, considere la posibilidad de si el uso de un snappoint condicional puede ayudar. Puede usar snappoints condicional para evitar realizar una instantánea hasta que la aplicación entra en un estado deseado, como cuando una variable tiene un valor concreto que le interesa. Puede establecer condiciones de uso de expresiones, filtros, o el número de visitas.

#### <a name="to-create-a-conditional-snappoint"></a>Para crear un snappoint condicional

1. Haga clic en un icono de snappoint (la bola hueco) y elija **configuración**.

   ![Elija la configuración](../debugger/media/snapshot-snappoint-settings.png "elegir configuraciones")

1. En la ventana de configuración snappoint, escriba una expresión.

   ![Escriba una expresión](../debugger/media/snapshot-snappoint-conditions.png "escriba una expresión")

   En la ilustración anterior, solo se toma la instantánea para la snappoint cuando `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Establecer un logpoint

Además de tomar una instantánea cuando se alcanza un snappoint, también puede configurar un snappoint para registrar un mensaje (es decir, crear una logpoint). Puede establecer logpoints sin tener que volver a implementar la aplicación. Logpoints se ejecutan prácticamente y no causar ningún impacto o los efectos secundarios a la aplicación en ejecución.

#### <a name="to-create-a-logpoint"></a>Para crear un logpoint

1. Haga clic en un icono de snappoint (el hexágonos azul) y elija **configuración**.

1. En la ventana de configuración snappoint, seleccione **acciones**.

    ![Crear un logpoint](../debugger/media/snapshot-logpoint.png "crear un logpoint")

1. En el campo de mensaje, puede escribir el nuevo mensaje de registro que desee registrar. También puede evaluar las variables en el mensaje de registro colocándolos dentro de llaves.

    Si elige **enviar a la ventana de salida**, cuando se visita el logpoint, el mensaje aparece en la ventana de herramientas de diagnóstico.

    ![Logpoint datos en la ventana .diagsession](../debugger/media/snapshot-logpoint-output.png "Logpoint datos en la ventana .diagsession")

    Si elige **envía al registro de aplicación**, cuando se visita el logpoint, aparece el mensaje en cualquier lugar que puede ver mensajes de `System.Diagnostics.Trace` (o `ILogger` en .NET Core), como [aplicación visión](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Pasos siguientes

- Para obtener información sobre cómo inspeccionar las variables durante la visualización de una instantánea, vea [depurador paseo](../debugger/debugger-feature-tour.md).
- Ver el [preguntas más frecuentes sobre depuración instantánea](../debugger/debug-live-azure-apps-faq.md).
- Vista [solución de problemas de sugerencias y problemas conocidos para la depuración instantánea](../debugger/debug-live-azure-apps-troubleshooting.md).
- Si desea ver las instantáneas en Application Insights cuando la aplicación produce una excepción, puede hacerlo. Para obtener más información, consulte [depurar las instantáneas de las excepciones en aplicaciones de .NET](/azure/application-insights/app-insights-snapshot-debugger). Visión de la aplicación es compatible con aplicaciones de Service Fabric además de servicio de aplicaciones de Azure.

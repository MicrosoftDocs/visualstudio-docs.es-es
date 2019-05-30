---
title: Depuración en vivo las máquinas virtuales de Azure de ASP.NET y los conjuntos de escalado
description: Obtenga información sobre cómo establecer puntos de instantánea y ver las instantáneas con Snapshot Debugger.
ms.custom: ''
ms.date: 02/06/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 38cf8b5c2af174b026c507fc5c668f826707adf3
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263358"
---
# <a name="debug-live-aspnet-apps-on-azure-virtual-machines-and-azure-virtual-machine-scale-sets-using-the-snapshot-debugger"></a>Depuración de aplicaciones de ASP.NET en vivo en Azure Virtual Machines y Azure Virtual Machines Scale Sets con Snapshot Debugger

Snapshot Debugger toma una instantánea de las aplicaciones en producción cuando se ejecuta el código que le interesa. Para indicar al depurador que tome una instantánea, establezca puntos de acoplamiento y puntos de registro en el código. El depurador le permite ver exactamente qué salió mal, sin afectar el tráfico de la aplicación de producción. El Depurador de instantáneas puede permitirle disminuir considerablemente el tiempo que tarda en resolver los problemas que se producen en los entornos de producción.

Los puntos de instantánea y los puntos de registro son similares a los puntos de interrupción, pero a diferencia de estos últimos, los puntos de instantánea no detienen la aplicación cuando se alcanzan dichos puntos. Normalmente, la captura de una instantánea en un punto de instantánea tarda 10-20 milisegundos.

En este tutorial va a:

> [!div class="checklist"]
> * Iniciar Snapshot Debugger
> * Establecer un punto de instantánea y ver una instantánea
> * Establecer un punto de registro

## <a name="prerequisites"></a>Requisitos previos

* Depurador de instantáneas para las máquinas virtuales (VM) de Azure y Azure Virtual Machine Scale Sets solo está disponible para Visual Studio 2019 Enterprise o posterior con el **carga de trabajo de desarrollo de Azure**. (En la pestaña **Componentes individuales**, puede encontrarlo en **Depuración y pruebas** > **Snapshot Debugger**).

    Si aún no está instalado, instale [Visual Studio Enterprise de 2019](https://visualstudio.microsoft.com/vs/).

* Recopilación de instantáneas está disponible para las siguientes aplicaciones web de Azure Virtual Machines\Virtual Machine Scale Sets:
  * Aplicaciones ASP.NET que se ejecutan en .NET Framework 4.6.1 o versiones posteriores.
  * Aplicaciones ASP.NET Core que se ejecutan en .NET Core 2.0 o posteriores en Windows.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Apertura del proyecto e inicio de Snapshot Debugger

1. Abra el proyecto de cuya depuración desea realizar una instantánea.

    > [!IMPORTANT]
    > Depuración de instantáneas, deberá abrir el *misma versión de código fuente* que se publica en el servicio de Azure Virtual Machine\Virtual equipo conjunto de escalado.

1. Elija **Depurar > Asociar Snapshot Debugger...** Seleccione una cuenta de almacenamiento de Azure y el Virtual Machine\Virtual equipo conjunto de escalado Azure se implementa la aplicación web en y, a continuación, haga clic en **adjuntar**.

      ![Inicio de Snapshot Debugger desde el menú Depurar](../debugger/media/snapshot-debug-menu-attach.png)

      ![Seleccione un recurso de Azure](../debugger/media/snapshot-select-azure-resource-vm.png) 

    > [!IMPORTANT]
    > La primera vez que selecciona **Asociar Snapshot Debugger** para la máquina virtual, IIS se reinicia automáticamente.
    > La primera vez que selecciona **asociar Snapshot Debugger** para los conjuntos de escalado de máquinas virtuales, requiere la actualización manual de cada instancia de los conjuntos de escalado de máquinas virtuales.

    Los metadatos de los **módulos** no se activarán inicialmente; vaya a la aplicación web y el botón **Iniciar colección** se activará. Visual Studio ahora está en modo de depuración de instantáneas.

   ![Modo de depuración de instantáneas](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > La extensión de sitio de Application Insights también admite la depuración de instantáneas. Si aparece un mensaje de error "la extensión de sitio no está actualizada", vea las [sugerencias de solución de problemas y los problemas conocidos con la depuración de instantáneas](../debugger/debug-live-azure-apps-troubleshooting.md) para actualizar los detalles.
    > Para VMSS es necesario actualizar manualmente las instancias de sus conjuntos de escalado de máquinas virtuales después de adjuntar al depurador de instantáneas por primera vez el usuario.

   El **módulos** ventana muestra cuando todos los módulos han cargado para la Azure Virtual Machine\Virtual equipo conjunto de escalado (elija **Depurar > Windows > módulos** para abrir esta ventana).

   ![Comprobación de la ventana Módulos](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Definición de un punto de instantánea

1. En el editor de código, haga clic en el medianil izquierdo junto a una línea de código en la que le interesa establecer un punto de instantánea. Asegúrese de que se trata de código que sabe que se ejecutará.

   ![Definición de un punto de instantánea](../debugger/media/snapshot-set-snappoint.png)

1. Haga clic en **Iniciar colección** para activar el punto de instantánea.

   ![Activar el punto de instantánea](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > No puede detenerse al visualizar una instantánea, pero puede colocar varios puntos de instantánea en el código para seguir la ejecución en diferentes líneas de código. Si tiene varios puntos de instantánea en el código, Snapshot Debugger garantiza que las instantáneas correspondientes sean de la misma sesión de usuario final. Snapshot Debugger hace esto aunque muchos usuarios visiten la aplicación.

## <a name="take-a-snapshot"></a>Tomar una instantánea

Cuando se activa un punto de instantánea, este capturará una instantánea cada vez que se ejecuta la línea de código donde se coloca el punto de instantánea. Esta ejecución puede derivar de una solicitud real en el servidor. Para forzar que se alcance el punto de instantánea, vaya a la vista del explorador del sitio web y realice las acciones necesarias que provocan que se alcance el punto de instantánea.

## <a name="inspect-snapshot-data"></a>Inspección de los datos de instantánea

1. Cuando se alcanza el punto de instantánea, aparece una instantánea en la ventana Herramientas de diagnóstico. Para abrir esta ventana, elija **Depurar > Windows > Mostrar herramientas de diagnóstico**.

   ![Apertura de un punto de instantánea](../debugger/media/snapshot-diagsession-window.png)

1. Haga doble clic en el punto de instantánea para abrir la instantánea en el editor de código.

   ![Inspección de los datos de instantánea](../debugger/media/snapshot-inspect-data.png)

   Desde esta vista, puede mantener el puntero sobre las variables para ver información sobre datos, usar las ventanas **Variables locales**, **Inspecciones** y **Pila de llamadas** y también evaluar expresiones.

    El propio sitio web está todavía activo y los usuarios finales no se ve afectados. Solo se captura una instantánea por cada punto de instantánea de forma predeterminada: una vez que se captura una instantánea, se desactiva el punto de instantánea. Si desea capturar otra instantánea en el punto de instantánea, puede volver a activar el punto de instantánea si hace clic en **Actualizar colección**.

También puede agregar más puntos de instantánea a la aplicación y activarlos con el botón **Actualizar colección**.

**¿Necesita ayuda?** Consulte las páginas [Solución de problemas y problemas conocidos](../debugger/debug-live-azure-apps-troubleshooting.md) y [Preguntas frecuentes sobre depuración de instantáneas](../debugger/debug-live-azure-apps-faq.md).

## <a name="set-a-conditional-snappoint"></a>Definición de un punto de instantánea condicional

Si es difícil volver a crear un estado determinado en la aplicación, considere si utilizar un punto de instantánea condicional puede resultar útil. Los puntos de instantánea condicionales evitan realizar una instantánea hasta que la aplicación entra en un estado deseado, por ejemplo, cuando una variable tiene un valor concreto que desea inspeccionar. Puede establecer las condiciones con expresiones, filtros o números de llamadas.

#### <a name="to-create-a-conditional-snappoint"></a>Para crear un punto de instantánea condicional

1. Haga clic con el botón derecho en un icono de punto de instantánea (el círculo hueco) y elija **Configuración**.

   ![Selección de Configuración](../debugger/media/snapshot-snappoint-settings.png)

1. En la ventana de configuración del punto de instantánea, escriba una expresión.

   ![Escribir una expresión](../debugger/media/snapshot-snappoint-conditions.png)

   En la ilustración anterior, la instantánea solo se realiza para el punto de instantánea cuando `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Establecer un punto de registro

Además de realizar una instantánea cuando se alcanza un punto de instantánea, también puede configurar un punto de instantánea para registrar un mensaje (es decir, crear un punto de registro). Puede establecer puntos de registro sin tener que volver a implementar la aplicación. Los puntos de registro se ejecutan de forma práctica y no causan ningún impacto o efecto secundario en la aplicación en ejecución.

#### <a name="to-create-a-logpoint"></a>Para crear un punto de registro

1. Haga clic con el botón derecho en un icono de punto de instantánea (el hexágono azul) y elija **Configuración**.

1. En la ventana de configuración del punto de instantánea, seleccione **Acciones**.

    ![Creación de un punto de registro](../debugger/media/snapshot-logpoint.png)

1. En el campo **mensaje**, puede escribir el nuevo mensaje de registro que desea registrar. También puede evaluar las variables del mensaje de registro si se colocan entre llaves.

    Si elige **Se envía a la ventana de salida**, cuando se alcanza el punto de registro, el mensaje aparece en la ventana Herramientas de diagnóstico.

    ![Datos del punto de registro en la ventana Herramientas de diagnóstico](../debugger/media/snapshot-logpoint-output.png)

    Si elige **Se envía al registro de aplicaciones**, cuando se alcanza el punto de registro, el mensaje aparece en cualquier lugar en el que puede ver los mensajes de `System.Diagnostics.Trace`, o `ILogger` en .NET Core, como [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha aprendido cómo utilizar Snapshot Debugger para Azure Virtual Machines y Azure Virtual Machine Scale Sets. Es posible que desee obtener más información sobre esta característica.

> [!div class="nextstepaction"]
> [P+F sobre depuración de instantáneas](../debugger/debug-live-azure-apps-faq.md)

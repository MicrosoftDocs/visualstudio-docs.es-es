---
title: Las máquinas virtuales de Azure de ASP.NET en vivo de depuración y conjuntos de escalado de máquina virtual de Azure
description: Obtenga información sobre cómo establecer puntos de acoplamiento y ver las instantáneas con el depurador de instantáneas.
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
ms.openlocfilehash: 608745fc2c96836163e1406abda6869d52b1da1b
ms.sourcegitcommit: 62149c96de0811415e99bb1e0194e76c320e1a1e
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2019
ms.locfileid: "57007280"
---
# <a name="debug-live-aspnet-apps-on-azure-virtual-machines-and-azure-virtual-machine-scale-sets-using-the-snapshot-debugger"></a>Depurar aplicaciones ASP.NET activas en Azure virtual machines y conjuntos de escalado de máquina virtual de Azure con el depurador de instantáneas

El depurador de instantáneas toma una instantánea de sus aplicaciones en producción cuando se ejecuta código que le interesa. Para indicar al depurador que tome una instantánea, establezca puntos de acoplamiento y puntos de registro en el código. El depurador le permite ver exactamente qué salió mal, sin afectar el tráfico de la aplicación de producción. El Depurador de instantáneas puede permitirle disminuir considerablemente el tiempo que tarda en resolver los problemas que se producen en los entornos de producción.

Puntos de acoplamiento y puntos de registro son similares a los puntos de interrupción, pero a diferencia de los puntos de interrupción, puntos de acoplamiento no detendrá la aplicación cuando se llama. Normalmente, la captura una instantánea en un punto de acoplamiento tarda 10-20 milisegundos.

En este tutorial va a:

> [!div class="checklist"]
> * Iniciar al depurador de instantáneas
> * Establecer un punto de acoplamiento y ver una instantánea
> * Establecer un punto de registro

## <a name="prerequisites"></a>Requisitos previos

* Snapshot Debugger para Azure Virtual Machines (VM) y conjuntos de escalado de máquinas virtuales (VMSS) de Azure solo está disponible en versión preliminar de Visual Studio 2019 Enterprise o posterior con el **carga de trabajo de desarrollo de Azure**. (En el **componentes individuales** pestaña, se encuentra en **depuración y pruebas** > **depurador de instantáneas**.)

    Si aún no está instalado, instale [versión preliminar de Visual Studio Enterprise de 2019](https://visualstudio.microsoft.com/vs/preview/).

* Recopilación de instantáneas está disponible para las siguientes aplicaciones web de Azure VM/VMSS:
  * Aplicaciones ASP.NET que se ejecutan en .NET Framework 4.6.1 o versiones posteriores.
  * Aplicaciones ASP.NET Core que se ejecutan en .NET Core 2.0 o posteriores en Windows.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Abra el proyecto e iniciar al depurador de instantáneas

1. Abra el proyecto que le gustaría depuración instantánea.

    > [!IMPORTANT]
    > Depuración de instantáneas, deberá abrir el *misma versión de código fuente* que se publica en el servicio de Azure VM/VMSS.

1. Adjunte al depurador de instantáneas. Puede usar varios métodos diferentes:

    * Elija **Depurar > asociar Snapshot Debugger...** . Seleccione la la aplicación web se implementa en VM/VMSS de Azure y una cuenta de almacenamiento de Azure y, a continuación, haga clic en **adjuntar**.

      ![Iniciar al depurador de instantáneas en el menú Depurar](../debugger/media/snapshot-debug-menu-attach.png)

    * Haga clic con el botón derecho en el proyecto y seleccione **publicar**y, a continuación, en la página de publicación, haga clic en **asociar Snapshot Debugger**. Seleccione la la aplicación web se implementa en VM/VMSS de Azure y una cuenta de almacenamiento de Azure y, a continuación, haga clic en **adjuntar**.
    ![Iniciar al depurador de instantáneas desde la página de publicación](../debugger/media/snapshot-publish-attach.png)

    * Menú desplegable, seleccione como destino de depuración **Snapshot Debugger**, presione **F5** si es necesario selecciona la la aplicación web se implementa en VM/VMSS de Azure y un almacenamiento de Azure de la cuenta y, a continuación, haga clic en  **Adjuntar**.
    ![Iniciar al depurador de instantáneas en el menú desplegable de F5](../debugger/media/snapshot-F5-dropdown-attach.png)

    * Mediante el explorador en la nube (**Ver > Cloud Explorer**), haga clic en Azure VM/VMSS se implementa la aplicación web en y seleccionar una cuenta de almacenamiento de Azure y, a continuación, haga clic en **asociar Snapshot Debugger**.

      ![Iniciar al depurador de instantáneas desde el Explorador de nube](../debugger/media/snapshot-launch.png)

    > [!IMPORTANT]
    > La primera vez que selecciona **asociar Snapshot Debugger** para la máquina virtual, IIS se reinicia automáticamente.
    > La primera vez que selecciona **asociar Snapshot Debugger** para el VMSS, requieren la actualización manual de cada instancia de lo VMSS.

    Los metadatos para el **módulos** inicialmente no se activará, vaya a la aplicación web y la **iniciar colección** se activará el botón. Visual Studio ahora está en modo de depuración de instantáneas.

    > [!NOTE]
    > La extensión de sitio de Application Insights también admite la depuración de instantáneas. Si se produce un mensaje de error "el sitio actualizado de la extensión", consulte [sugerencias y problemas conocidos de depuración de instantáneas de la solución de problemas](../debugger/debug-live-azure-apps-troubleshooting.md) para actualizar los detalles.
    > Para VMSS es necesario actualizar manualmente las instancias de sus VMSS después de adjuntar al depurador de instantáneas por primera vez el usuario.

   ![Modo de depuración instantánea](../debugger/media/snapshot-message.png)

   El **módulos** ventana muestra cuando todos los módulos han cargado para Azure VM/VMSS (elija **Depurar > Windows > módulos** para abrir esta ventana).

   ![Comprobación de la ventana módulos](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Establecer un punto de acoplamiento

1. En el editor de código, haga clic en el margen interno izquierdo junto a una línea de código que esté interesado en establecer un punto de acoplamiento. Asegúrese de que se trata de código que sabe que se ejecutará.

   ![Establecer un punto de acoplamiento](../debugger/media/snapshot-set-snappoint.png)

1. Haga clic en **iniciar colección** para activar el punto de acoplamiento.

   ![Activar el punto de acoplamiento](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > No puede pasar al ver una instantánea, pero puede colocar varios puntos de acoplamiento en el código para seguir la ejecución en diferentes líneas de código. Si tiene varios puntos de acoplamiento en el código, el depurador de instantáneas se asegura de que las instantáneas correspondientes son de la misma sesión del usuario final. El depurador de instantáneas hace esto, incluso si hay muchos usuarios que visitan su aplicación.

## <a name="take-a-snapshot"></a>Tomar una instantánea

Cuando se activa un punto de acoplamiento, capturará una instantánea cada vez que ejecuta la línea de código donde se coloca el punto de acoplamiento. Esta ejecución puede deberse a una solicitud real en el servidor. Para forzar que el punto de acoplamiento de posicionamiento, vaya a la vista de explorador del sitio web y tomar las medidas necesarias que provocan que se alcance el punto de acoplamiento.

## <a name="inspect-snapshot-data"></a>Inspeccionar los datos de instantánea

1. Cuando se alcanza el punto de acoplamiento, aparece una instantánea en la ventana de herramientas de diagnóstico. Para abrir esta ventana, elija **Depurar > Windows > Mostrar herramientas de diagnóstico**.

   ![Abra un punto de acoplamiento](../debugger/media/snapshot-diagsession-window.png)

1. Haga doble clic en el punto de acoplamiento para abrir la instantánea en el editor de código.

   ![Inspeccionar los datos de instantánea](../debugger/media/snapshot-inspect-data.png)

   Desde esta vista, puede desplazar el puntero sobre las variables para ver información sobre datos, utilice el **variables locales**, **inspecciones**, y **pila de llamadas** windows y también evaluar expresiones.

    El mismo sitio Web está todavía activo y los usuarios finales no se ve afectados. Sólo una instantánea se captura por punto de acoplamiento de forma predeterminada: una vez que se captura una instantánea se desactiva el punto de acoplamiento. Si desea capturar otra instantánea en el punto de acoplamiento, puede activar el punto de acoplamiento en haciendo **actualizar colección**.

También puede agregar más puntos de acoplamiento a la aplicación y activar con el **actualizar colección** botón.

**¿Necesita ayuda?** Consulte la [problemas conocidos y solución de problemas](../debugger/debug-live-azure-apps-troubleshooting.md) y [preguntas más frecuentes sobre depuración de instantáneas](../debugger/debug-live-azure-apps-faq.md) páginas.

## <a name="set-a-conditional-snappoint"></a>Establecer un punto de acoplamiento condicional

Si es difícil volver a crear un estado determinado en la aplicación, considere la posibilidad de si el uso de un punto de acoplamiento condicional puede ayudar. Puntos de acoplamiento condicional le evitan tomando una instantánea hasta que la aplicación entra en un estado deseado, por ejemplo, cuando una variable tiene un valor concreto que desea inspeccionar. Puede establecer las condiciones de uso de expresiones, los filtros, o el número de visitas.

#### <a name="to-create-a-conditional-snappoint"></a>Para crear un punto de acoplamiento condicional

1. Haga clic en un icono de punto de acoplamiento (la bola hueco) y elija **configuración**.

   ![Selección de Configuración](../debugger/media/snapshot-snappoint-settings.png)

1. En la ventana de configuración de punto de acoplamiento, escriba una expresión.

   ![Escriba una expresión](../debugger/media/snapshot-snappoint-conditions.png)

   En la ilustración anterior, solo se toma la instantánea para el punto de acoplamiento cuando `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Establecer un punto de registro

Además de tomar una instantánea cuando se alcanza un punto de acoplamiento, también puede configurar un punto de acoplamiento para registrar un mensaje (es decir, crear un punto de registro). Puede establecer puntos de registro sin tener que volver a implementar la aplicación. Puntos de registro se ejecutan prácticamente y no causar ningún impacto ni efectos secundarios a la aplicación en ejecución.

#### <a name="to-create-a-logpoint"></a>Para crear un punto de registro

1. Haga clic en un icono de punto de acoplamiento (el Hexágono azul) y elija **configuración**.

1. En la ventana de configuración de punto de acoplamiento, seleccione **acciones**.

    ![Crear un punto de registro](../debugger/media/snapshot-logpoint.png)

1. En el **mensaje** campo, puede escribir el nuevo mensaje de registro que desee registrar. También puede evaluar las variables en el mensaje del registro si se colocan dentro de llaves.

    Si elige **enviar a la ventana de salida**, cuando se alcanza el punto de registro, el mensaje aparece en la ventana de herramientas de diagnóstico.

    ![Datos de punto de registro en la ventana de diagsession](../debugger/media/snapshot-logpoint-output.png)

    Si elige **envía al registro de aplicación**, cuando se alcanza el punto de registro, el mensaje aparece en cualquier lugar que puede ver los mensajes de `System.Diagnostics.Trace` (o `ILogger` en .NET Core), como [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha aprendido cómo utilizar al depurador de instantáneas para las máquinas virtuales de Azure y Azure Virtual Machine Scale Sets. Es posible que desee Obtenga más información sobre esta característica.

> [!div class="nextstepaction"]
> [P+F sobre depuración de instantáneas](../debugger/debug-live-azure-apps-faq.md)
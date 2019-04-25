---
title: Página de inicio para el depurador de instantáneas
ms.date: 07/14/2018
robots: noindex, nofollow
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf2aba33089623dc98a90c23166291bb2d6e7123
ms.sourcegitcommit: cdcbf254db737d42275e95de4ffc4f8c14e87e00
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57428653"
---
# <a name="getting-started-with-the-snapshot-debugger"></a>Introducción a Snapshot Debugger

Visual Studio Snapshot Debugger ahora está conectado a su servicio y puede comenzar a recopilar las instantáneas para ayudar con la depuración.

Para usar al depurador de instantáneas, establezca algunos puntos de acoplamiento en el código, haga clic en el botón para comenzar a recopilar las instantáneas y, a continuación, ejecute el escenario. Cuando se ejecuta el código en el que se ha establecido un punto de acoplamiento, se toma una instantánea de la aplicación. A continuación, abra la instantánea haciendo clic en él en Visual Studio en la ventana de herramientas de diagnóstico. Ahora puede depurar la instantánea de su servicio como si fuera local. Para obtener instrucciones detalladas, siga leyendo.

## <a name="collect-and-view-snapshots"></a>Recopilar y ver las instantáneas

Snapshot Debugger recopila instantáneas de la aplicación. Las instantáneas son como las imágenes de su appication en un momento dado. Indicarle a Visual Studio cuándo y dónde se recopila una instantánea mediante el establecimiento de un punto de acoplamiento en el código. En el punto de acoplamiento, establezca las condiciones que debe asegurarse de que obtener una instantánea del problema que está investigando.

### <a name="set-a-snappoint"></a>Establecer un punto de acoplamiento

1. En el editor de código, haga clic en el margen interno izquierdo junto a una línea de código que está interesado en establecer un punto de acoplamiento. Asegúrese de que se trata de código que sabe que se ejecutará.

    ![Establecer un punto de acoplamiento en el Editor](../media/snapshot-startpage-set-snappoint.png)

    Un hexágono púrpura aparecerá donde haga clic en la izquierda.

2. Haga clic en **iniciar colección** para activar el punto de acoplamiento.

### <a name="open-a-snapshot"></a>Abrir una instantánea

1. Cuando se alcanza el punto de acoplamiento, aparece una instantánea en la ventana de herramientas de diagnóstico de la derecha. Si no se abre la ventana, ábralo eligiendo **depurar** > **Windows** > **Mostrar herramientas de diagnóstico**.

    ![Instantánea en la ventana de herramientas de diagnóstico](../media/snapshot-startpage-diagsession-window.png)

2. Haga doble clic en la instantánea para abrirlo.

### <a name="inspect-snapshot-data"></a>Inspeccionar los datos de instantánea

Desde esta vista, puede desplazar el puntero sobre las variables para ver información sobre datos, use las variables locales, relojes y llamar a la pila de windows y también evaluar expresiones.

El mismo sitio Web está todavía activo y los usuarios finales no se ve afectados. De forma predeterminada, sólo una instantánea es capturada por el punto de acoplamiento. Es decir, una vez que se captura una instantánea, el punto de acoplamiento se desactiva. Si desea capturar otra instantánea en el punto de acoplamiento, puede activar el punto de acoplamiento en haciendo **actualizar colección**.

### <a name="set-a-logpoint"></a>Establecer un punto de registro

1. Haga clic en un icono de punto de acoplamiento (el Hexágono púrpura) y elija **configuración**.

2. En el **configuración de punto de acoplamiento** ventana, seleccione **acciones**.

    ![Condiciones de punto de acoplamiento](../media/snapshot-startpage-logpoint.png)

3. En el **mensaje** , escriba un mensaje de registro que desea registrar. También puede evaluar las variables en el mensaje del registro si se colocan dentro de llaves.

    Si elige **enviar a la ventana de salida**, aparece el mensaje en la ventana de herramientas de diagnóstico cuando se alcanza el punto de registro.

    Si elige **envía al registro de aplicación**, aparece el mensaje en cualquier lugar que puede ver los mensajes de `System.Diagnostics.Trace` (o `ILogger` en .NET Core), como App Insights, cuando se alcanza el punto de registro.

## <a name="learn-more"></a>Obtener más información

Puede encontrar más información sobre el depurador de instantáneas en el [página de documentos](../debug-live-azure-applications.md). Más información acerca de cómo establecer las condiciones para que sea más fácil encontrar errores.

## <a name="dont-show-me-this-again"></a>No volver a mostrar

Para no volver a mostrar la página de inicio del depurador de instantáneas al conectar el depurador de instantáneas, cambie el **mostrar la página "Introducción" en el inicio de sesión** opción **herramientas**  >   **Opciones de** > **depurador de instantáneas**.

![Página de opciones de herramienta de depurador de instantáneas](../media/snapshot-startpage-tools-options.png)

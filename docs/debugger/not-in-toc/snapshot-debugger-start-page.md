---
title: Página de inicio de Snapshot Debugger
ms.date: 07/14/2018
robots: noindex, nofollow
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9f237f121d0bd0a5eaa57cd2b198024d22951622
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942001"
---
# <a name="getting-started-with-the-snapshot-debugger"></a>Introducción a Snapshot Debugger

Visual Studio Snapshot Debugger ahora está conectado a su servicio y puede empezar a recopilar instantáneas que le ayuden con la depuración.

Para usar Snapshot Debugger, establezca algunos puntos de instantánea en el código, haga clic en el botón para empezar a recopilar instantáneas y, luego, ejecute el escenario. Cuando se ejecuta código en el que se ha establecido un punto de instantánea, se toma una instantánea de la aplicación. Después, se abre; para ello, haga clic en ella en Visual Studio en la ventana Herramientas de diagnóstico. Ahora puede depurar la instantánea desde el servicio como si fuera local. Para encontrar instrucciones detalladas, siga leyendo.

## <a name="collect-and-view-snapshots"></a>Recopilación y visualización de instantáneas

Snapshot Debugger recopila instantáneas de la aplicación. Las instantáneas son como imágenes de la aplicación en un momento dado. A Visual Studio se le debe indica cuándo y dónde recopilar una instantánea mediante el establecimiento de un punto de instantánea en el código. En el punto de instantánea, establezca las condiciones que necesita para asegurarse de que obtiene una instantánea del problema que está investigando.

### <a name="set-a-snappoint"></a>Establecimiento de un punto de instantánea

1. En el editor de código, haga clic en el medianil izquierdo junto a una línea de código en la que le interese establecer un punto de instantánea. Asegúrese de que sea código que sabe que se ejecutará.

    ![Establecimiento de un punto de instantánea en el editor](../media/snapshot-startpage-set-snappoint.png)

    Donde hace clic a la izquierda aparece un hexágono púrpura.

2. Haga clic en **Iniciar colección** para activar el punto de instantánea.

### <a name="open-a-snapshot"></a>Apertura de una instantánea

1. Cuando se alcanza el punto de instantánea, aparece una instantánea en la ventana Herramientas de diagnóstico a la derecha. Si la ventana no se abre, elija **Depurar** > **Windows** > **Mostrar herramientas de diagnóstico** para abrirla.

    ![Instantánea en la ventana Herramientas de diagnóstico](../media/snapshot-startpage-diagsession-window.png)

2. Haga doble clic en la instantánea para abrirla.

### <a name="inspect-snapshot-data"></a>Inspección de los datos de la instantánea

Desde esta vista, puede mantener el puntero sobre las variables para ver información sobre datos, usar las ventanas Variables locales, Inspecciones y Pila de llamadas y también evaluar expresiones.

El propio sitio web está todavía activo y los usuarios finales no se ve afectados. De forma predeterminada, solo se captura una instantánea por punto de instantánea. Es decir, después de capturar una instantánea, el punto de instantánea se desactiva. Si desea capturar otra instantánea en el punto de instantánea, puede volver a activar el punto de instantánea si hace clic en **Actualizar colección**.

### <a name="set-a-logpoint"></a>Establecimiento de un punto de registro

1. Haga clic con el botón derecho en un icono de punto de instantánea (el hexágono azul) y elija **Configuración**.

2. En la ventana **Configuración del punto de instantánea**, seleccione **Acciones**.

    ![Condiciones del punto de instantánea](../media/snapshot-startpage-logpoint.png)

3. En el campo **Mensaje**, escriba un mensaje de registro que quiera registrar. También puede evaluar las variables del mensaje de registro si se colocan entre llaves.

    Si elige **Enviar a la ventana de salida**, cuando se alcanza el punto de registro, el mensaje aparece en la ventana Herramientas de diagnóstico.

    Si elige **Send to application log** (Enviar al registro de aplicaciones), cuando se alcanza el punto de registro, el mensaje aparece en cualquier lugar en el que puede ver los mensajes de `System.Diagnostics.Trace` (o `ILogger` en .NET Core), como App Insights.

## <a name="learn-more"></a>Obtener más información

Puede encontrar más información sobre Snapshot Debugger en la [página de documentos](../debug-live-azure-applications.md). Aprenda más sobre cómo establecer las condiciones que facilitan la búsqueda de errores.

## <a name="dont-show-me-this-again"></a>No volver a mostrar

Para no mostrar nunca la página de inicio de Snapshot Debugger cuando se conecte a él, cambie la opción **Show 'Getting Started' page on session start** (Mostrar la página de inicio al comienzo de la sesión) en **Herramientas** > **Opciones** > **Snapshot Debugger**.

![Página de opciones de la herramienta Snapshot Debugger](../media/snapshot-startpage-tools-options.png)

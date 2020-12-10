---
title: Diagnóstico de retrasos de la interfaz de usuario de extensión en Visual Studio | Microsoft Docs
description: Visual Studio le notifica si los retrasos de la interfaz de usuario pueden estar causados por una extensión. Obtenga información sobre cómo diagnosticar qué en el código de extensión está causando retrasos de la interfaz de usuario.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: conceptual
author: PooyaZv
ms.author: pozandev
manager: jillfra
ms.workload: multiple
ms.openlocfilehash: 965e96a7881e20eca035b61ed7fd6f29398e71c6
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994269"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>Cómo: Diagnosticar retrasos de la interfaz de usuario causados por las extensiones

Cuando la interfaz de usuario deja de responder, Visual Studio examina la pila de llamadas del subproceso de la interfaz de usuario, empezando por la hoja y trabajando hacia la base. Si Visual Studio determina que un marco de pila de llamadas pertenece a un módulo que forma parte de una extensión instalada y habilitada, muestra una notificación.

![Notificación de retraso de la interfaz de usuario (no responde)](media/ui-delay-notification-in-vs.png)

La notificación informa al usuario de que el retraso de la interfaz de usuario (es decir, la falta de respuesta en la interfaz de usuario) podría haber sido el resultado del código de una extensión. También proporciona al usuario opciones para deshabilitar la extensión o las notificaciones futuras para esa extensión.

En este documento se describe cómo diagnosticar qué en el código de extensión está causando notificaciones de retraso de la interfaz de usuario.

> [!NOTE]
> No use la instancia experimental de Visual Studio para diagnosticar los retrasos de la interfaz de usuario. Algunas partes del análisis de la pila de llamadas necesarias para las notificaciones de retraso de la interfaz de usuario se desactivan al usar la instancia experimental, lo que significa que es posible que no se muestren notificaciones de retraso de la interfaz de usuario.

Una introducción al proceso de diagnóstico es la siguiente:
1. Identifique el escenario del desencadenador.
2. Reinicie VS con el inicio de sesión de actividad.
3. Inicie el seguimiento de ETW.
4. Desencadene la notificación para que aparezca de nuevo.
5. Detenga el seguimiento de ETW.
6. Examine el registro de actividad para obtener el identificador de retraso.
7. Analice el seguimiento de ETW con el identificador de retraso del paso 6.

En las secciones siguientes, seguiremos estos pasos con más detalle.

## <a name="identify-the-trigger-scenario"></a>Identificar el escenario de desencadenador

Para diagnosticar un retraso de la interfaz de usuario, primero debe identificar qué (secuencia de acciones) hace que Visual Studio muestre la notificación. Esto está disponible para que pueda desencadenar la notificación más adelante con el registro activado.

## <a name="restart-vs-with-activity-logging-on"></a>Reiniciar VS con el registro de actividades

Visual Studio puede generar un "registro de actividad" que proporciona información útil al depurar un problema. Para activar el registro de actividad en Visual Studio, abra Visual Studio con la `/log` opción de línea de comandos. Una vez que Visual Studio se inicia, el registro de actividad se almacena en la siguiente ubicación:

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

Para obtener más información sobre cómo encontrar el identificador de la instancia de VS, vea [herramientas para detectar y administrar instancias de Visual Studio](../install/tools-for-managing-visual-studio-instances.md). Más adelante usaremos este registro de actividad para obtener más información sobre los retrasos de la interfaz de usuario y las notificaciones relacionadas.

## <a name="starting-etw-tracing"></a>Inicio del seguimiento de ETW

Puede usar [PerfView](https://github.com/Microsoft/perfview/) para recopilar un seguimiento de ETW. PerfView proporciona una interfaz fácil de usar para recopilar un seguimiento de ETW y para analizarlo. Use el comando siguiente para recopilar un seguimiento:

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

Esto habilita el proveedor de "Microsoft-VisualStudio", que es el proveedor que Visual Studio usa para los eventos relacionados con las notificaciones de retraso de la interfaz de usuario. También especifica la palabra clave para el proveedor de kernel que PerfView puede usar para generar la vista de **pilas de tiempo de subproceso** .

## <a name="trigger-the-notification-to-appear-again"></a>Desencadenar la notificación para que aparezca de nuevo

Una vez que PerfView ha iniciado la recopilación de seguimiento, puede usar la secuencia de acción desencadenadora (del paso 1) para que la notificación vuelva a aparecer. Una vez que se muestra la notificación, puede detener la recopilación de seguimiento de PerfView para procesar y generar el archivo de seguimiento de salida.

## <a name="stop-etw-tracing"></a>Detener seguimiento de ETW

Para detener la recopilación de seguimiento, basta con usar el botón **detener colección** de la ventana de PerfView. Después de detener la recopilación de seguimiento, PerfView procesará automáticamente los eventos ETW y generará un archivo de seguimiento de salida.

## <a name="examine-the-activity-log-to-get-the-delay-id"></a>Examinar el registro de actividad para obtener el identificador de retraso

Como se mencionó anteriormente, puede encontrar el registro de actividad en *%APPDATA%\Microsoft\VisualStudio \<vs_instance_id>\ActivityLog.xml*. Cada vez que Visual Studio detecta un retraso de la interfaz de usuario de la extensión, escribe un nodo en el registro de actividad con `UIDelayNotifications` como origen. Este nodo contiene cuatro fragmentos de información sobre el retraso de la interfaz de usuario:

- El identificador de retraso de la interfaz de usuario, un número secuencial que identifica de forma única un retraso de la interfaz de usuario en una sesión de VS
- El identificador de sesión, que identifica de forma única la sesión de Visual Studio de inicio a cerrar
- Indica si se ha mostrado o no una notificación para el retraso de la interfaz de usuario
- La extensión que probablemente causó el retraso de la interfaz de usuario

```xml
<entry>
  <record>271</record>
  <time>2018/02/03 12:02:52.867</time>
  <type>Information</type>
  <source>UIDelayNotifications</source>
  <description>A UI delay (Delay ID = 0) has been detected. (Session ID=16e49d4b-26c2-4247-ad1c-488edeb185e0; Blamed extension="UIDelayR2"; Notification shown? Yes.)</description>
</entry>
```

> [!NOTE]
> No todos los retrasos de la interfaz de usuario generan una notificación. Por lo tanto, siempre debe comprobar la **notificación que se muestra?** valor para identificar correctamente el retraso de la interfaz de usuario correcto.

Después de encontrar el retraso de la interfaz de usuario correcto en el registro de actividad, anote el identificador de retraso de la interfaz de usuario especificado en el nodo. Usará el identificador para buscar el evento ETW correspondiente en el paso siguiente.

## <a name="analyze-the-etw-trace"></a>Analizar el seguimiento de ETW

A continuación, abra el archivo de seguimiento. Para ello, puede usar la misma instancia de PerfView o iniciar una nueva instancia y establecer la ruta de acceso de la carpeta actual en la parte superior izquierda de la ventana en la ubicación del archivo de seguimiento.

![Establecimiento de la ruta de acceso de la carpeta en Perfview](media/perfview-set-path.png)

A continuación, seleccione el archivo de seguimiento en el panel izquierdo y ábralo eligiendo **abrir** en el menú contextual.

> [!NOTE]
> De forma predeterminada, PerfView genera un archivo zip. Al abrir *trace.zip*, descomprime automáticamente el archivo y abre el seguimiento. Para omitir esto, desactive el cuadro **zip** durante la recopilación de seguimiento. Sin embargo, si planea transferir y usar seguimientos en diferentes equipos, se recomienda encarecidamente no desactivar el cuadro **zip** . Sin esta opción, los archivos PDB necesarios para los ensamblados Ngen no se adjuntarán al seguimiento y, por tanto, los símbolos de los ensamblados Ngen no se resolverán en el equipo de destino. (Vea [esta entrada de blog](https://devblogs.microsoft.com/devops/creating-ngen-pdbs-for-profiling-reports/) para obtener más información sobre los archivos PDB para los ensamblados Ngen).

La PerfView puede tardar varios minutos en procesar y abrir el seguimiento. Una vez que el seguimiento está abierto, aparece una lista de las distintas "vistas" en él.

![Vista de Resumen de seguimiento de PerfView](media/perfview-summary-view-events-selected.png)

En primer lugar, usaremos la vista de **eventos** para obtener el intervalo de tiempo del retraso de la interfaz de usuario:

1. Abra la vista **eventos** seleccionando `Events` nodo en el seguimiento y eligiendo **abrir** en el menú contextual.
2. Seleccione " `Microsoft-VisualStudio/ExtensionUIUnresponsiveness` " en el panel izquierdo.
3. Presione Entrar.

La selección se aplica y todos los `ExtensionUIUnresponsiveness` eventos se muestran en el panel derecho.

![Seleccionar eventos en la vista eventos](media/perfview-event-selection.png)

Cada fila del panel derecho corresponde a un retraso de la interfaz de usuario. El evento incluye un valor de "ID. de retraso" que debe coincidir con el ID. de retraso del registro de actividad del paso 6. Dado que `ExtensionUIUnresponsiveness` se desencadena al final del retraso de la interfaz de usuario, la marca de tiempo del evento (aproximadamente) marca la hora de finalización del retraso de la interfaz de usuario. El evento también contiene la duración del retraso. Podemos restar la duración de la marca de tiempo final para obtener la marca de tiempo de Cuándo se inició el retraso de la interfaz de usuario.

![Calcular el intervalo de tiempo de retraso de la interfaz de usuario](media/ui-delay-time-range.png)

En la captura de pantalla anterior, por ejemplo, la marca de tiempo del evento es 12.125,679 y la duración del retraso es 6.143,085 (MS). Así,
* El inicio del retraso es 12.125,679-6.143,085 = 5.982,594.
* El intervalo de tiempo de retraso de la interfaz de usuario es de 5.982,594 a 12.125,679.

Una vez que tenemos el intervalo de tiempo, podemos cerrar la vista de **eventos** y abrir la vista de **pilas de tiempo del subproceso (con actividades de StartStop)** . Esta vista es especialmente útil porque, a menudo, las extensiones que están bloqueando el subproceso de la interfaz de usuario simplemente están esperando en otros subprocesos o en una operación enlazada a e/s. Por lo tanto, la vista de pila de la **CPU** , que es la opción de ir a para la mayoría de los casos, no puede capturar el tiempo que el subproceso invierte en el bloqueo, ya que no está usando la CPU durante ese tiempo. La **pila de tiempo de subprocesos** resuelve este problema mostrando correctamente el tiempo de bloqueo.

![Nodo pilas de tiempo de subproceso (con actividades StartStop) en la vista de Resumen de PerfView](media/perfview-thread-time-with-startstop-activities-stacks.png)

Al abrir la vista **pilas de tiempo de subprocesos** , elija el proceso **devenv** para iniciar el análisis.

![Vista de pilas de tiempo de subproceso para el análisis de retraso de la interfaz de usuario](media/ui-delay-thread-time-stacks.png)

En la vista de **pilas de tiempo de subproceso** , en la parte superior izquierda de la página, puede establecer el intervalo de tiempo en los valores calculados en el paso anterior y presionar **entrar** para que las pilas se ajusten a ese intervalo de tiempo.

> [!NOTE]
> Determinar qué subproceso es el subproceso de interfaz de usuario (Inicio) puede ser intuitivo si la colección de seguimiento se inicia después de que Visual Studio ya esté abierto. Sin embargo, los primeros elementos de la pila del subproceso de interfaz de usuario (Inicio) son siempre los archivos DLL del sistema operativo más probables (*ntdll.dll* y *kernel32.dll*) seguidos de `devenv!?` y, a continuación, `msenv!?` . Esta secuencia puede ayudar a identificar el subproceso de la interfaz de usuario.

 ![Identificación del subproceso de inicio](media/ui-delay-startup-thread.png)

También puede filtrar aún más esta vista si solo incluye pilas que contienen módulos del paquete.

* Establezca **GroupPats** en texto vacío para quitar cualquier agrupación agregada de forma predeterminada.
* Establezca **IncPats** para incluir parte del nombre del ensamblado además del filtro de proceso existente. En este caso, debe ser **devenv; UIDelayR2**.

![Establecer GroupPath y IncPath en la vista de pilas de tiempo de subprocesos](media/perfview-tts-group-path-inc-path.png)

PerfView tiene instrucciones detalladas en el menú **ayuda** que puede usar para identificar cuellos de botella de rendimiento en el código. Además, los vínculos siguientes proporcionan más información sobre cómo se usan las API de subprocesos de Visual Studio para optimizar el código:

* [https://github.com/Microsoft/vs-threading/blob/master/doc/index.md](https://github.com/Microsoft/vs-threading/blob/master/doc/index.md)
* [https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md)

También puede usar los nuevos Analizadores estáticos de Visual Studio para extensiones (paquete NuGet [aquí](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers)), que proporcionan instrucciones sobre los procedimientos recomendados para escribir extensiones eficientes. Vea una lista de [analizadores de vs SDK](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md) y [analizadores de subprocesos](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md).

> [!NOTE]
> Si no puede solucionar la falta de respuesta debido a las dependencias en las que no tiene control (por ejemplo, si la extensión tiene que llamar a servicios de VS sincrónicos en el subproceso de la interfaz de usuario), nos gustaría conocerlo. Si es miembro de nuestro programa de Partners de Visual Studio, puede ponerse en contacto con nosotros enviando una solicitud de soporte técnico para desarrolladores. De lo contrario, use la herramienta "Notificar un problema" para enviar sus comentarios e incluirlos `"Extension UI Delay Notifications"` en el título. También debe incluir una descripción detallada del análisis.

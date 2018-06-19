---
title: Diagnóstico de extensión de interfaz de usuario retrasa en Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 01/26/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
author: PooyaZv
ms.author: pozandev
manager: douge
ms.workload: multiple
ms.openlocfilehash: b63f9538c916b74874031704a1f60d0646f8d032
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134375"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>Cómo: diagnosticar la interfaz de usuario retrasos causados por las extensiones

Cuando la interfaz de usuario deja de responder, Visual Studio examina la pila de llamadas del subproceso de interfaz de usuario, empezando por la hoja y continuando hacia la base. Si Visual Studio determina que un marco de pila de llamadas pertenece a un módulo que forma parte de una extensión instalada y habilitada, muestra una notificación.

![Retraso de la interfaz de usuario (falta de respuesta) notificación](media/ui-delay-notification-in-vs.png)

La notificación informa al usuario que el retraso de la interfaz de usuario (es decir, en la falta de respuesta en la interfaz de usuario) podría haber sido el resultado del código de una extensión. También proporciona al usuario con opciones para deshabilitar la extensión o las notificaciones futuras de esa extensión.

Este documento describe cómo puede diagnosticar en el código de extensión causa de las notificaciones de retraso de interfaz de usuario. 

> [!NOTE]
> No utilice la instancia experimental de Visual Studio para diagnosticar los retrasos de la interfaz de usuario. Algunas partes de lo análisis de pila de llamadas necesario para las notificaciones de retraso de interfaz de usuario están desactivadas cuando se usa la instancia experimental, lo que significa que no se pueden mostrar notificaciones de retraso de interfaz de usuario.

Información general sobre el proceso de diagnóstico es como sigue:
1. Identifique el escenario de desencadenador.
2. Reiniciar VS con registro de actividad.
3. Iniciar el seguimiento de ETW.
4. Desencadenar la notificación aparecerá de nuevo.
5. Detener traza de ETW.
6. Examine el registro de actividad para obtener el identificador de retraso.
7. Analizar el seguimiento ETW con el Id. de retraso en el paso 6.

En las secciones siguientes, veremos estos pasos con más detalle.

## <a name="identifying-the-trigger-scenario"></a>Identificar el escenario de desencadenador

Para diagnosticar un retraso de la interfaz de usuario, primero debe identificar qué (secuencia de acciones) hace que Visual Studio mostrar la notificación. Esto está en orden para puede desencadenar la notificación más adelante con activado el registro.

## <a name="restarting-vs-with-activity-logging-on"></a>Reiniciar VS con la actividad iniciar sesión

Visual Studio puede generar un "registro de actividad" que proporciona información útil al depurar un problema. Para activar la actividad de registro en Visual Studio, inicie Visual Studio con el `/log` opción de línea de comandos. Una vez que inicie Visual Studio, el registro de actividad se almacena en la siguiente ubicación:

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

Para obtener más información acerca de cómo puede averiguar frente a su Id. de instancia, vea [herramientas para detectar y administrar instancias de Visual Studio](../install/tools-for-managing-visual-studio-instances.md). Usaremos este registro de actividad más adelante para obtener más información acerca de retrasos de la interfaz de usuario y las notificaciones relacionadas.

## <a name="starting-etw-tracing"></a>Iniciar la traza de ETW

Puede usar [PerfView](https://github.com/Microsoft/perfview/) para recopilar un seguimiento ETW. PerfView proporciona una interfaz fácil de usar para recopilar un seguimiento ETW y para analizarlos. Use el comando siguiente para recopilar un seguimiento:

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

Esto permite que el proveedor de "Microsoft VisualStudio", que es el proveedor que usa Visual Studio para los eventos relacionados con las notificaciones de retraso de interfaz de usuario. También se especifica la palabra clave para el proveedor de kernel que se puede usar PerfView para generar la vista "De subprocesos de pilas de tiempo".

## <a name="triggering-the-notification-to-appear-again"></a>Desencadenar la notificación aparecerá de nuevo

Una vez que PerfView ha iniciado la recopilación de seguimiento, puede usar la secuencia de acción de desencadenador (desde el paso 1) para la notificación de que aparezca de nuevo. Una vez que se muestra la notificación, puede detener la recolección de seguimiento de PerfView procesar y generar el archivo de seguimiento de salida.

## <a name="stopping-etw-tracing"></a>Detener traza de ETW

Para detener la recopilación de seguimiento, use simplemente el `Stop collection` botón en la ventana de PerfView. Después de detener la recopilación de seguimiento, PerfView automáticamente procesará los eventos ETW y genera un archivo de seguimiento de salida.

## <a name="examining-the-activity-log-to-get-the-delay-id"></a>Examinar el registro de actividad para obtener el identificador de retraso

Como se mencionó anteriormente, puede encontrar el registro de actividad en `%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml`. Cada vez que Visual Studio detecta un retraso de la interfaz de usuario de extensión, escribe un nodo en el registro de actividad con `UIDelayNotifications` como el origen. Este nodo contiene cuatro elementos de información sobre el retraso de la interfaz de usuario:

- El identificador de retraso de la interfaz de usuario, un número secuencial que identifica de forma única un retraso de la interfaz de usuario en una sesión de VS
- El identificador de sesión, que identifica de forma única la sesión de Visual Studio desde el principio hasta el cierre
- Si no se muestra una notificación para el retraso de la interfaz de usuario
- La extensión que es probable que provocó el retraso de la interfaz de usuario

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
> No todos los resultados de retrasos de interfaz de usuario en una notificación. ¿Por lo tanto, debe comprobar siempre las "notificaciones se muestra"? valor que se va a identificar correctamente el retraso de la interfaz de usuario correcto.

Cuando encuentre el retraso de la interfaz de usuario correcto en el registro de actividad, anote el identificador de retraso de la interfaz de usuario especificado en el nodo. Deberá usar el identificador para buscar el correspondiente evento ETW en el paso siguiente.

## <a name="analyzing-the-etw-trace"></a>Analizar el seguimiento ETW

A continuación, abra el archivo de seguimiento. Para ello, ya sea con la misma instancia de PerfView o a partir de una nueva instancia y establecer la ruta de acceso de la carpeta actual en la parte superior izquierda de la ventana a la ubicación del archivo de seguimiento.

![Establecer la ruta de acceso de carpeta en Perfview](media/perfview-set-path.png)

A continuación, seleccione el archivo de seguimiento en el panel izquierdo y ábralo eligiendo abrir en el menú contextual o en contexto.

> [!NOTE]
> De forma predeterminada PerfView da como resultado un archivo Zip. Cuando se abre trace.zip, automáticamente descomprime el archivo y abre el seguimiento. Puede omitir este para ello, desactive la casilla "Zip" durante la recopilación de seguimiento. Sin embargo, si va a transferir y utilizar seguimientos en distintos equipos, se recomienda en desactivando la casilla "Zip". Sin esta opción, los archivos PDB necesarios para los ensamblados Ngen no se adjuntará a la traza y, por tanto, no se resolverán símbolos de Ngen ensamblados en el equipo de destino. (Consulte [esta entrada de blog](https://blogs.msdn.microsoft.com/devops/2012/12/10/creating-ngen-pdbs-for-profiling-reports/) para obtener más información sobre los archivos PDB para ensamblados Ngen.) 

Puede tardar varios minutos para que PerfView procesar y abrir el seguimiento. Una vez abierto el seguimiento, aparecerá una lista de varias "vistas" en él.

![Vista de resumen de seguimiento de PerfView](media/perfview-summary-view-events-selected.png)

En primer lugar se usará la vista "Eventos" para obtener el intervalo de tiempo de retraso de la interfaz de usuario:

1. Abra la vista "Eventos" seleccionando el nodo de "Eventos" en el seguimiento y elegir abrir en el menú contextual o en contexto.
2. Seleccione "`Microsoft-VisualStudio/ExtensionUIUnresponsiveness`" en el panel izquierdo.
3. Presione ENTRAR

Se aplica la selección y todos los `ExtensionUIUnresponsiveness` eventos se muestran en el panel derecho.

![Seleccionar los eventos en la vista de eventos](media/perfview-event-selection.png)

Cada fila en el panel derecho corresponde a un retraso de la interfaz de usuario. El evento incluye un valor de "Retraso ID" que debe coincidir con el identificador de retraso en el registro de actividad en el paso 6. Puesto que `ExtensionUIUnresponsiveness` se activa al final del retraso de interfaz de usuario, la marca de tiempo del evento (aproximadamente) las marcas de hora de finalización del retraso de la interfaz de usuario. El evento también contiene la duración del retraso. Le podemos resta la duración de la marca de tiempo de finalización para obtener la marca de tiempo cuando inicia el retraso de la interfaz de usuario.

![Calcular el intervalo de tiempo de retraso de interfaz de usuario](media/ui-delay-time-range.png)

En la captura de pantalla anterior, por ejemplo, la marca de tiempo del evento es 12,125.679 y la duración del retraso es 6,143.085 (ms). Así,
* El retraso de inicio es 12,125.679 6,143.085 = 5,982.594.
* El intervalo de tiempo de retraso de interfaz de usuario es 5,982.594 a 12,125.679.

Una vez que tenemos el intervalo de tiempo, podemos cerrar fuera de la vista de eventos y abra la vista "Pilas de subprocesos tiempo (con actividades de StartStop)". Esta vista es especialmente útil porque a menudo las extensiones que están bloqueando el subproceso de interfaz de usuario simplemente están esperando una operación enlazados a E/s o de otros subprocesos. Por lo tanto, la vista "Pila de CPU", que es la opción preferida para la mayoría de los casos, no puede capturar el tiempo que el subproceso invierte bloqueo dado que no usa la CPU durante ese tiempo. El "pilas de tiempo de subproceso" resuelve este problema, tiempo de mostrando bloqueado correctamente.

![Nodo de pilas de tiempo (con actividades de StartStop) del subproceso en la vista de resumen de PerfView](media/perfview-thread-time-with-startstop-activities-stacks.png)

Al abrir "Subprocesos de pilas de tiempo" ver, elija el proceso de "devenv" para iniciar el análisis.

![Vista de pilas de tiempo para el análisis de retraso de interfaz de usuario del subproceso](media/ui-delay-thread-time-stacks.png)

En la vista "De subprocesos de pilas de tiempo", en la parte superior izquierda de la página, puede establecer el intervalo de tiempo en los valores que se calcula en el paso anterior y presione ENTRAR, por lo que las pilas se ajustan a ese intervalo de tiempo.

> [!NOTE]
> Determinar el subproceso es la interfaz de usuario (inicio) subproceso puede estar intuitivos si se inicia la recopilación de seguimiento después de que Visual Studio ya está abierto. ¿Sin embargo, los primeros elementos en la pila del subproceso de interfaz de usuario (inicio) más probable siempre son archivos DLL de sistema operativo (ntdll.dll y kernel32.dll) seguidas de devenv!? y, a continuación, msenv!?. Esta secuencia puede ayudar a identificar el subproceso de interfaz de usuario.

 ![Identifica el subproceso de inicio](media/ui-delay-startup-thread.png)

Puede filtrar aún más esta vista solo incluyendo pilas que contienen módulos desde el paquete.

* Establezca "GroupPats" en el texto vacío para quitar cualquier agrupación agregada de forma predeterminada.
* Conjunto "IncPats" para incluir parte de su nombre de ensamblado además de filtro de proceso existente. En este caso, debe ser "devenv; UIDelayR2 ".

![Establecer GroupPath y IncPath en la vista de pilas de subprocesos de tiempo](media/perfview-tts-group-path-inc-path.png)

PerfView, detallaron instrucciones en el menú de ayuda que puede usar para identificar los cuellos de botella de rendimiento en el código. Además, los siguientes vínculos proporcionan más información acerca de cómo utilizar las API para optimizar el código de subprocesamiento de Visual Studio:

* [https://aka.ms/vsthreading](https://aka.ms/vsthreading)
* [https://aka.ms/vsthreadingcookbook](https://aka.ms/vsthreadingcookbook)

También puede utilizar los analizadores estáticos nuevo de Visual Studio para extensiones (paquete de NuGet [aquí](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers)), que ofrecen orientación sobre los procedimientos recomendados para escribir extensiones eficaces. Ver una lista de [analizadores de SDK de VS](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md) y [subprocesamiento analizadores](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md).

> [!NOTE]
> Si no puede solucionar la falta de respuesta debido a dependencias no tiene control sobre (por ejemplo, si la extensión debe llamar a los servicios de VS sincrónicos en el subproceso de interfaz de usuario), nos gustaría saber sobre él. Si es un miembro de nuestro programa de partners de Visual Studio, puede establecer contacto con nosotros enviando una solicitud de soporte para desarrolladores. En caso contrario, use la herramienta "Informar de un problema" para enviar sus comentarios e incluir `"Extension UI Delay Notifications"` en el título. También incluya una descripción detallada del análisis.

---
title: Retrasa la interfaz de usuario de la extensión de diagnóstico en Visual Studio | Microsoft Docs
ms.date: 01/26/2018
ms.topic: conceptual
author: PooyaZv
ms.author: pozandev
manager: jillfra
ms.workload: multiple
ms.openlocfilehash: 00266fd8fbc881707652247e08b093ca4b15a88d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912077"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>Procedimiento Diagnosticar retrasos de la interfaz de usuario causados por las extensiones

Cuando la interfaz de usuario deja de responder, Visual Studio examina la pila de llamadas del subproceso de interfaz de usuario, comenzando por la hoja y dirigiéndose a la base. Si Visual Studio determina que un marco de pila de llamadas pertenece a un módulo que forma parte de una extensión habilitada e instalada, muestra una notificación.

![(Falta de respuesta) notificación de retraso de la interfaz de usuario](media/ui-delay-notification-in-vs.png)

La notificación informa al usuario que el retraso de la interfaz de usuario (es decir, en la falta de respuesta en la interfaz de usuario) podría haber sido el resultado del código de una extensión. También proporciona al usuario con opciones para deshabilitar la extensión o las notificaciones futuras de esa extensión.

Este documento describe cómo puede diagnosticar qué en el código de extensión está causando las notificaciones de retraso de la interfaz de usuario.

> [!NOTE]
> No use la instancia experimental de Visual Studio para diagnosticar retrasos de la interfaz de usuario. Algunas partes de los análisis de la pila de llamadas necesarios para las notificaciones de retraso de la interfaz de usuario se desactivan cuando se usa la instancia experimental, lo que significa que no se muestren las notificaciones de retraso de la interfaz de usuario.

Información general sobre el proceso de diagnóstico es como sigue:
1. Identificar el escenario de desencadenador.
2. Reinicie VS con la actividad de inicio de sesión.
3. Iniciar el seguimiento de ETW.
4. Desencadenar la notificación aparecerá de nuevo.
5. Detenga el seguimiento de ETW.
6. Examine el registro de actividad para obtener el identificador de retraso.
7. Analizar el seguimiento ETW mediante el identificador de retraso del paso 6.

En las secciones siguientes, se pasará a través de estos pasos con más detalle.

## <a name="identify-the-trigger-scenario"></a>Identificar el escenario de desencadenador

Para diagnosticar un retraso de la interfaz de usuario, primero debe identificar qué (secuencia de acciones) hace que Visual Studio mostrar la notificación. Esto está en orden para puede desencadenar la notificación más adelante con activado el registro.

## <a name="restart-vs-with-activity-logging-on"></a>Reinicie VS con la actividad de inicio de sesión

Visual Studio puede generar un "registro de actividad" que proporciona información útil al depurar un problema. Para activar la actividad de registro en Visual Studio, abra Visual Studio con el `/log` opción de línea de comandos. Cuando se inicia Visual Studio, el registro de actividad se almacena en la siguiente ubicación:

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

Para obtener más información acerca de cómo puede encontrar sus VS Id. de instancia, vea [herramientas para detectar y administrar instancias de Visual Studio](../install/tools-for-managing-visual-studio-instances.md). Usaremos este registro de actividad más adelante para obtener más información sobre los retrasos de la interfaz de usuario y las notificaciones relacionadas.

## <a name="starting-etw-tracing"></a>Iniciar el seguimiento de ETW

Puede usar [PerfView](https://github.com/Microsoft/perfview/) para recopilar un seguimiento ETW. PerfView proporciona una interfaz fácil de usar tanto para recopilar un seguimiento ETW para analizarlos. Para recopilar un seguimiento, use el siguiente comando:

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

Esto permite al proveedor de "Microsoft VisualStudio", que es el proveedor que usa Visual Studio para eventos relacionados con las notificaciones de retraso de la interfaz de usuario. También especifica la palabra clave para el proveedor de kernel que se puede usar PerfView para generar el **las pilas de subprocesos en tiempo** vista.

## <a name="trigger-the-notification-to-appear-again"></a>Desencadenar la notificación aparecerá de nuevo

Una vez que PerfView ha iniciado la recopilación de seguimiento, puede usar la secuencia de acciones del desencadenador (del paso 1) para la notificación aparecerá de nuevo. Una vez que se muestra la notificación, puede detener la recopilación de seguimiento de PerfView procesar y generar el archivo de seguimiento de salida.

## <a name="stop-etw-tracing"></a>Detener el seguimiento de ETW

Para detener la recopilación de seguimiento, use simplemente el **Detener colección** botón en la ventana de PerfView. Después de detener la recopilación de seguimiento, PerfView automáticamente procesará los eventos ETW y genera un archivo de seguimiento de salida.

## <a name="examine-the-activity-log-to-get-the-delay-id"></a>Examine el registro de actividad para obtener el identificador de retraso

Como se mencionó anteriormente, puede encontrar el registro de actividad en *%APPDATA%\Microsoft\VisualStudio\<vs_instance_id > \ActivityLog.xml*. Cada vez que Visual Studio detecta un retraso de la interfaz de usuario de extensión, escribe un nodo en el registro de actividad con `UIDelayNotifications` como origen. Este nodo contiene cuatro elementos de información sobre el retraso de la interfaz de usuario:

- El identificador de retraso de la interfaz de usuario, un número secuencial que identifica de forma única un retraso de la interfaz de usuario en una sesión de VS
- El identificador de sesión que identifica de forma única la sesión de Visual Studio desde el principio hasta el cierre
- Si se muestra una notificación para el retraso de la interfaz de usuario
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
> No todos los retrasos de la interfaz de usuario como resultado una notificación. Por lo tanto, debe comprobar siempre el **notificación se muestra?** valor para identificar correctamente el retraso de la interfaz de usuario correcto.

Después de encontrar el retraso de la interfaz de usuario correcto en el registro de actividad, anote el identificador de retraso de la interfaz de usuario especificado en el nodo. Usará el identificador para buscar el evento ETW correspondiente en el paso siguiente.

## <a name="analyze-the-etw-trace"></a>Analizar el seguimiento ETW

A continuación, abra el archivo de seguimiento. Para ello, ya sea mediante la misma instancia de PerfView o iniciando una nueva instancia y establecer la ruta de acceso de la carpeta actual en la parte superior izquierda de la ventana a la ubicación del archivo de seguimiento.

![Establecer la ruta de acceso de carpeta en Perfview](media/perfview-set-path.png)

A continuación, seleccione el archivo de seguimiento en el panel izquierdo y ábrala eligiendo **abrir** en el menú contextual.

> [!NOTE]
> De forma predeterminada PerfView da como resultado un archivo Zip. Al abrir *trace.zip*, descomprime el archivo automáticamente y se abre el seguimiento. Puede omitir esto desactivando el **Zip** cuadro durante la recolección de seguimiento. Sin embargo, si va a transferir y utilizar seguimientos en las distintas máquinas, se recomienda desactivar la **Zip** cuadro. Sin esta opción, los archivos PDB necesarios para los ensamblados Ngen no se adjuntará a la traza y, por tanto, no se resolverán símbolos de los ensamblados Ngen en el equipo de destino. (Consulte [esta entrada de blog](https://devblogs.microsoft.com/devops/creating-ngen-pdbs-for-profiling-reports/) para obtener más información sobre los archivos PDB para ensamblados Ngen.)

Puede tardar varios minutos en PerfView procesar y abrir el seguimiento. Una vez que el seguimiento está abierto, aparecerá una lista de diversas "vistas" debajo de él.

![Vista de resumen de seguimiento de PerfView](media/perfview-summary-view-events-selected.png)

En primer lugar se usará el **eventos** vista para obtener el intervalo de tiempo de retraso de la interfaz de usuario:

1. Abra el **eventos** vista seleccionando `Events` nodo en el seguimiento y eligiendo **abierto** en el menú contextual.
2. Seleccione "`Microsoft-VisualStudio/ExtensionUIUnresponsiveness`" en el panel izquierdo.
3. Presione ENTRAR

Se aplica a la selección y todos los `ExtensionUIUnresponsiveness` se muestran los eventos en el panel derecho.

![Seleccionar los eventos en la vista de eventos](media/perfview-event-selection.png)

Cada fila en el panel derecho se corresponde a un retraso de la interfaz de usuario. El evento incluye un valor de "Retraso ID" que debe coincidir con el identificador de retraso en el registro de actividad en el paso 6. Puesto que `ExtensionUIUnresponsiveness` se desencadena al final del retraso de la interfaz de usuario, la marca de tiempo del evento (aproximadamente) las marcas de hora de finalización de la demora de la interfaz de usuario. El evento también contiene la duración del retraso. Podemos restamos la duración de la marca de tiempo final para obtener la marca de tiempo en que comenzó el retraso de la interfaz de usuario.

![Calcular el intervalo de tiempo de retraso de la interfaz de usuario](media/ui-delay-time-range.png)

En la captura de pantalla anterior, por ejemplo, la marca de tiempo del evento es 12,125.679 y la duración del retraso es 6,143.085 (ms). Así,
* El retraso de inicio es 12,125.679 6,143.085 = 5,982.594.
* El intervalo de tiempo de retraso de la interfaz de usuario es 5,982.594 a 12,125.679.

Una vez que tenemos el intervalo de tiempo, podemos cerrar fuera de la **eventos** ver y abrir el **pilas de subprocesos de tiempo (con las actividades de StartStop)** vista. Esta vista es especialmente útil porque a menudo las extensiones que están bloqueando el subproceso de interfaz de usuario simplemente están esperando una operación dependientes de E/s o de otros subprocesos. Por lo tanto, el **CPU pila** vista, que es la mejor opción para la mayoría de los casos, no puede capturar el tiempo que invierte en el subproceso de bloqueo como no se utiliza la CPU durante ese tiempo. El **las pilas de subprocesos en tiempo** resuelve este problema al tiempo de mostrando bloqueado correctamente.

![Nodo de las pilas en tiempo (con actividades StartStop) del subproceso en la vista de resumen de PerfView](media/perfview-thread-time-with-startstop-activities-stacks.png)

Mientras se abre **las pilas de subprocesos en tiempo** ver, elija el **devenv** proceso para iniciar el análisis.

![Vista de pilas de tiempo para el análisis de retraso de la interfaz de usuario del subproceso](media/ui-delay-thread-time-stacks.png)

En el **las pilas de subprocesos en tiempo** ver, en la parte superior izquierda de la página, puede establecer el intervalo de tiempo en los valores se calculan en el paso anterior y presione **ENTRAR** por lo que se ajustan las pilas para ese intervalo de tiempo.

> [!NOTE]
> Determinar qué subproceso es la interfaz de usuario (inicio) subproceso puede estar contradictorio si la colección de seguimiento se ha iniciado después de que Visual Studio ya está abierto. Sin embargo, los primeros elementos en la pila del subproceso de interfaz de usuario (inicio) más probable siempre son archivos DLL del sistema operativo (*ntdll.dll* y *kernel32.dll*) seguido por `devenv!?` y, a continuación, `msenv!?` . Esta secuencia puede ayudar a identificar el subproceso de interfaz de usuario.

 ![Que identifica el subproceso de inicio](media/ui-delay-startup-thread.png)

También puede filtrar esta vista solo incluyendo pilas que contienen módulos desde el paquete.

* Establecer **GroupPats** en texto vacío para quitar cualquier agrupación que se agrega de forma predeterminada.
* Establecer **IncPats** para incluir parte de su nombre de ensamblado, además de filtro de proceso existente. En este caso, debe ser **devenv; UIDelayR2**.

![Establecer GroupPath y IncPath en la vista de pilas de subprocesos de tiempo](media/perfview-tts-group-path-inc-path.png)

PerfView contiene detallada guía en la **ayuda** menú que puede usar para identificar los cuellos de botella en el código. Además, los vínculos siguientes proporcionan más información sobre cómo usar las API para optimizar el código de subprocesos de Visual Studio:

* [https://aka.ms/vsthreading](https://aka.ms/vsthreading)
* [https://aka.ms/vsthreadingcookbook](https://aka.ms/vsthreadingcookbook)

También puede usar los analizadores estáticos nueva de Visual Studio para extensiones (paquetes de NuGet [aquí](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers)), que proporcionan instrucciones sobre los procedimientos recomendados para escribir extensiones eficaces. Ver una lista de [analizadores de SDK de VS](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md) y [threading analizadores](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md).

> [!NOTE]
> Si no puede solucionar la falta de respuesta debido a las dependencias no tiene control sobre (por ejemplo, si la extensión tiene que llamar a los servicios de VS sincrónicos en el subproceso de interfaz de usuario), nos gustaría tener conocimientos sobre él. Si es un miembro de nuestro programa de socio de Visual Studio, puede en contacto con nosotros enviando una solicitud de soporte técnico para desarrolladores. En caso contrario, use la herramienta "Notificar un problema" para enviar sus comentarios e incluir `"Extension UI Delay Notifications"` en el título. Incluya también una descripción detallada del análisis.

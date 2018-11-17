---
title: Vista de subprocesos (rendimiento paralelo) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.threadblocking
helpviewer_keywords:
- Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 39457684ba19ecbb0ad2ef82caa349e67cdaf8a7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756332"
---
# <a name="threads-view-parallel-performance"></a>Vista de subprocesos (rendimiento paralelo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vista de subprocesos es la vista más detallada y con más características del visualizador de simultaneidad. Con esta vista puede identificar si los subprocesos se están ejecutando o se bloquearon por causa de la sincronización, E/S o algún otro motivo.  
  
 Durante el análisis de perfiles, el visualizador de simultaneidad examina todos los eventos de cambio de contexto de sistema operativo para cada subproceso de la aplicación. Los cambios de contexto pueden producirse por varias razones, como las siguientes:  
  
- Un subproceso se bloquea en una sincronización primitiva.  
  
- Expira el cuanto de un subproceso.  
  
- Un subproceso realiza una solicitud de E/S de bloqueo.  
  
  La vista de subprocesos asigna una categoría a cada cambio de contexto cuando se ha detenido un subproceso. Las categorías se muestran en la leyenda en la parte inferior izquierda de la vista. El visualizador de simultaneidad clasifica los eventos de cambio de contexto buscando API de bloqueo conocidas en la pila de llamadas del subproceso. Si no hay ninguna coincidencia de la pila de llamadas, se utiliza la razón de espera proporcionada por [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)]. Sin embargo, la categoría de [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] puede basarse en un detalle de implementación y puede no reflejar la intención del usuario. Por ejemplo, [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] indica el motivo de la espera de bloqueo en un bloqueo de lectura-escritura delgado nativo como E/S, en lugar de la sincronización. En la mayoría de los casos, puede identificar la causa de un evento de bloqueo examinando las pilas de llamadas que corresponden a los eventos de cambio de contexto.  
  
  La vista de subprocesos también muestra las dependencias entre subprocesos. Por ejemplo, si se identifica un subproceso que está bloqueado en un objeto de sincronización, puede buscar el subproceso que lo desbloqueó y examinar la actividad en la pila de llamadas del subproceso en el momento que desbloqueó el otro.  
  
  Cuando se ejecutan los subprocesos, el visualizador de simultaneidad recopila muestras. En la vista de subprocesos, puede analizar el código que ejecuta uno o más subprocesos durante un segmento de ejecución. También puede examinar informes de bloqueo e informes que generan perfiles de ejecución del árbol de pila de llamadas.  
  
## <a name="usage"></a>Uso  
 Estas son algunas de las maneras en las que puede usar la vista de subprocesos:  
  
-   Identificar las razones por las que la interfaz de usuario (UI) de una aplicación no responde durante ciertas fases de ejecución.  
  
-   Identificar la cantidad de tiempo dedicado al bloqueo de sincronización, E/S, errores de página y otros eventos.  
  
-   Identificar el grado de interferencias de otros procesos que se ejecutan en el sistema.  
  
-   Identificar problemas de equilibrio de carga para la ejecución en paralelo.  
  
-   Identificar los motivos por los que la escalabilidad es poco óptima o no existe (por ejemplo, por qué no mejora el rendimiento de una aplicación paralela cuando están disponibles más núcleos lógicos).  
  
-   Entender el grado de simultaneidad en la aplicación, para ayudar en la ejecución en paralelo.  
  
-   Comprender las dependencias entre los subprocesos de trabajo y las rutas críticas de ejecución.  
  
## <a name="examining-specific-time-intervals-and-threads"></a>Examinando los subprocesos y los intervalos de tiempo específicos  
 La vista de subprocesos muestra una escala de tiempo. Puede hacer zoom y desplazarse dentro de la escala de tiempo para examinar intervalos específicos y subprocesos de la aplicación. En el eje x está el tiempo y en el eje y están varios canales:  
  
- Dos canales de E/S para cada unidad de disco en el sistema, un canal para las lecturas y otro para las escrituras.  
  
- Un canal para cada subproceso del proceso.  
  
- Canales de marcador, si hay eventos de marcador en el seguimiento. Los canales de marcador aparecen inicialmente en los canales de subproceso que generaron los eventos.  
  
- Canales de GPU.  
  
  Aquí tiene una ilustración de la vista de subprocesos:  
  
  ![Vista de subprocesos](../profiling/media/threadsviewnarrowing.png "ThreadsViewNarrowing")  
  Vista de subprocesos  
  
  Inicialmente, los subprocesos se ordenan en el orden en que se crean, por lo que el subproceso de aplicación principal es el primero. Puede utilizar la opción de ordenación en la esquina superior izquierda de la vista para ordenar los subprocesos por otro criterio (por ejemplo, por la mayor parte de trabajo de ejecución realizado).  
  
  Puede ocultar los subprocesos que no están realizando trabajo seleccionando sus nombres en la columna de la izquierda y después eligiendo el botón **Ocultar subprocesos seleccionados** en la barra de herramientas. Se recomienda que oculte los subprocesos completamente bloqueados porque sus estadísticas son irrelevantes y pueden bloquear los informes.  
  
  Para identificar los subprocesos adicionales que se deben ocultar, en la leyenda activa, elija el informe **Resumen por subproceso** en la pestaña **Informe de perfil**. Esto muestra el gráfico de desglose de ejecución, que muestra el estado de los subprocesos para el intervalo de tiempo seleccionado. En algunos niveles de zoom, podrían no mostrarse algunos subprocesos. Cuando esto ocurre, se muestran puntos suspensivos situados a la derecha.  
  
  Cuando haya seleccionado un intervalo de tiempo y algunos subprocesos en él, puede iniciar el análisis de rendimiento.  
  
## <a name="analysis-tools"></a>Herramientas de análisis  
 Esta sección describe los informes y otras herramientas de análisis.  
  
### <a name="thread-blocking-details"></a>Detalles del bloqueo de subproceso  
 Para obtener información acerca de los eventos de bloqueo en una región determinada de un subproceso, sitúe el puntero en dicha región para mostrar una información sobre herramientas. Contiene información como la categoría, la hora de inicio de la región, la duración del bloqueo y una API de bloqueo si hay alguna. Si selecciona la región de bloqueo, la pila en ese momento en el tiempo se muestra en el panel inferior, junto con la misma información que se muestra en la información sobre herramientas. Al examinar la pila de llamadas puede determinar la razón subyacente para el evento de bloqueo de subprocesos. Puede encontrar información de procesos y subprocesos adicional seleccionando el segmento y examinando la ficha actual.  
  
 Una ruta de acceso de ejecución puede tener varios eventos de bloqueo. Puede examinarla por categoría de bloqueo para poder encontrar áreas problemáticas más rápidamente. Elija una de las categorías de bloqueo en la leyenda de la izquierda.  
  
### <a name="dependencies-between-threads"></a>Dependencias entre subprocesos  
 El visualizador de simultaneidad puede mostrar las dependencias entre los subprocesos del proceso para que pueda determinar lo que estaba intentando hacer un subproceso bloqueado y obtener información acerca de qué otro subproceso le permitió ejecutarse. Para determinar qué subproceso desbloqueó otro subproceso, seleccione el segmento de bloqueo pertinente. Si el visualizador de simultaneidad puede determinar el subproceso de desbloqueo, dibuja una línea entre el subproceso de desbloqueo y el segmento de ejecución que sigue el segmento de bloqueo. Además, la pestaña **Pila de desbloqueo** muestra la pila de llamadas pertinente.  
  
### <a name="thread-execution-details"></a>Detalles de ejecución de subprocesos  
 En el gráfico de escala de tiempo de un subproceso, los segmentos verdes muestran cuando se ejecuta código. Puede obtener información más detallada sobre un segmento de ejecución.  
  
 Cuando se selecciona un punto en un segmento de ejecución, el visualizador de simultaneidad busca ese punto en el tiempo en la pila de llamadas correspondiente y después muestra un símbolo de intercalación negro sobre el punto seleccionado en el segmento de ejecución y muestra la propia pila de llamadas en la pestaña **Pila actual**. Puede seleccionar varios puntos en el segmento de ejecución.  
  
> [!NOTE]
>  Es posible que el visualizador de simultaneidad no pueda resolver una selección en un segmento de ejecución. Normalmente, esto ocurre cuando la duración del segmento es inferior a un milisegundo.  
  
 Para obtener un perfil de ejecución para todos los subprocesos habilitados (no ocultos) en el intervalo de tiempo seleccionado, elija el botón **Ejecución** en la leyenda activa.  
  
### <a name="timeline-graph"></a>Gráfico de escala de tiempo  
 El gráfico de escala de tiempo muestra la actividad de todos los subprocesos en el proceso y todos los dispositivos de disco físico en el equipo host. También muestra los eventos de actividad y de marcador de GPU.  Puede ampliar para ver más detalles o reducir para ver un intervalo más largo de tiempo. También puede seleccionar puntos en el gráfico para obtener detalles sobre las categorías, las horas de inicio, las duraciones y los estados de la pila de llamadas.  
  
 En el gráfico de escala de tiempo, un color indica el estado de un subproceso en un momento dado. Por ejemplo, los segmentos verdes se estaban ejecutando, los segmentos rojos se bloquearon para la sincronización, los segmentos amarillos se adelantaron y los segmentos púrpura realizaban E/S del dispositivo. Puede utilizar esta vista para examinar el equilibro de trabajo entre los subprocesos que intervienen en un bucle paralelo o en tareas simultáneas. Si un subproceso está tardando más tiempo en completarse que otros, el trabajo puede verse desequilibrado. Puede utilizar esta información para mejorar el rendimiento del programa distribuyendo el trabajo uniformemente entre los subprocesos.  
  
 Si solo hay un subproceso verde (en ejecución) en un momento determinado, es posible que la aplicación no esté aprovechando la simultaneidad en el sistema. Puede usar el gráfico de escala de tiempo para examinar las dependencias entre los subprocesos y las relaciones temporales entre y los subprocesos de bloqueo y bloqueados. Para reorganizar los subprocesos, seleccione uno y después, en la barra de herramientas, elija el botón Arriba o Abajo. Para ocultar los subprocesos, selecciónelos y después elija el botón **Ocultar subprocesos**.  
  
### <a name="profile-reports"></a>Informes de perfil  
 Debajo de la gráfica de escala de tiempo se encuentra un perfil de escala de tiempo y un panel con pestañas para varios informes. Los informes se actualizan automáticamente a medida que cambia la vista de subprocesos. Para seguimientos de gran tamaño, el panel de informes podría no estar disponible mientras se calculan las actualizaciones. Cada informe tiene dos ajustes de filtro: reducción de ruido y Solo mi código. Utilice la reducción de ruido para filtrar las entradas del árbol de llamadas en las que se empleó poco tiempo. El valor de filtro predeterminado es 2 por ciento, pero puede ajustarlo desde 0 hasta 99 por ciento. Para ver solo el árbol de llamadas para su código, seleccione la casilla **Solo mi código**. Para ver todos los árboles de llamadas, desmárquela.  
  
#### <a name="profile-report"></a>Informe de perfil  
 Esta ficha muestra los informes que se corresponden con las entradas de la leyenda activa. Para mostrar un informe, elija una de las entradas.  
  
#### <a name="current-stack"></a>Pila actual  
 Esta pestaña muestra la pila de llamadas para un punto seleccionado en un segmento de subproceso en el gráfico de escala de tiempo. Las pilas de llamadas se recortan para mostrar únicamente la actividad relacionada con el programa.  
  
#### <a name="unblocking-stack"></a>Pila de desbloqueo  
 Para ver qué subproceso desbloqueó el subproceso seleccionado, y en qué línea de código lo hizo, elija la pestaña **Pila de desbloqueo**.  
  
#### <a name="execution"></a>Execution  
 El informe de ejecución muestra el desglose del tiempo que la aplicación estuvo ejecutándose.  
  
 Para buscar la línea de código donde transcurre el tiempo de ejecución, expanda el árbol de llamadas y después, en el menú de función para la entrada del árbol de llamadas, elija **Ver código fuente** o **Ver sitios de llamada**. **Ver código fuente** localiza la línea de código ejecutada. **Ver sitios de llamada** localiza la línea de código que llamó a la línea de código ejecutada. Si solo existe un sitio de llamada, se resalta su línea de código. Si existen varios sitios de llamada, puede seleccionar la que desee en el cuadro de diálogo que aparece y después elija el botón **Ir a código fuente** para resaltar el código del sitio de llamada. A menudo resulta más útil buscar el sitio de llamada que tiene el mayor número de instancias, más tiempo o ambos valores. Para obtener más información, consulte [Informe de perfil de ejecución](../profiling/execution-profile-report.md).  
  
#### <a name="synchronization"></a>Sincronización  
 El informe de sincronización muestra las llamadas responsables de los bloqueos de sincronización, junto con el tiempo de bloqueo agregado de cada pila de llamadas. Para obtener más información, consulte [Tiempo de sincronización](../profiling/synchronization-time.md).  
  
#### <a name="io"></a>E/S  
 El informe de E/S muestra las llamadas responsables de los bloqueos de E/S, junto con el tiempo de bloqueo agregado de cada pila de llamadas. Para obtener más información, Consulte [Tiempo de E/S (Vista de subprocesos)](../profiling/i-o-time-threads-view.md).  
  
#### <a name="sleep"></a>Sleep  
 El informe de reposo muestra las llamadas responsables de los bloqueos de reposo, junto con el tiempo de bloqueo agregado de cada pila de llamadas. Para obtener más información, consulte [Tiempo de reposo](../profiling/sleep-time.md).  
  
#### <a name="memory-management"></a>Administración de memoria  
 El informe de administración de memoria muestra las llamadas en las que se produjeron bloqueos de la administración de memoria, junto con el tiempo de bloqueo agregado de cada pila de llamadas. Puede utilizar esta información para identificar las áreas que tienen problemas de recolección de elementos no utilizados o de paginación excesiva.  Para obtener más información, consulte [Tiempo de administración de memoria](../profiling/memory-management-time.md).  
  
#### <a name="preemption"></a>Adelantamiento  
 El informe de adelantamiento muestra las instancias donde los procesos del sistema se adelantaron al proceso actual y los subprocesos individuales que reemplazaron subprocesos del proceso actual. Puede utilizar esta información para identificar los procesos y subprocesos más responsables del adelantamiento. Para obtener más información, consulte [Duración del adelantamiento](../profiling/preemption-time.md).  
  
#### <a name="ui-processing"></a>Procesamiento de IU  
 El informe de procesamiento de IU muestra las llamadas responsables de los bloqueos de procesamiento de IU, junto con el tiempo de bloqueo agregado de cada pila de llamadas. Para obtener más información, consulte [Duración de procesamiento de IU](../profiling/ui-processing-time.md).  
  
#### <a name="per-thread-summary"></a>Resumen por subproceso  
 Esta pestaña muestra una vista de columna codificada por colores del tiempo total que cada subproceso ha estado en ejecución, bloqueado, en E/S y en otros estados. Las columnas se etiquetan en la parte inferior. Al ajustar el nivel de zoom en el gráfico de escala de tiempo, esta ficha se actualiza automáticamente. En algunos niveles de zoom, podrían no mostrarse algunos subprocesos. Cuando esto ocurre, se muestran puntos suspensivos situados a la derecha. Si el subproceso que desea no aparece, puede ocultar otros subprocesos. Para obtener más información, consulte [Informe de resumen por subproceso](../profiling/per-thread-summary-report.md).  
  
#### <a name="disk-operations"></a>Operaciones en disco  
 Esta pestaña muestra los procesos y subprocesos implicados en E/S de disco en nombre del proceso actual, los archivos que modifican (por ejemplo, archivos DLL cargados), cuántos bytes se leyeron y otra información. Este informe puede usarse para evaluar el tiempo invertido en obtener acceso a archivos durante la ejecución, especialmente si el proceso parece estar enlazado a E/S. Para obtener más información, consulte [Informe de operaciones en disco](../profiling/disk-operations-report-threads-view.md).  
  
## <a name="see-also"></a>Vea también  
 [Visualizador de simultaneidad](../profiling/concurrency-visualizer.md)




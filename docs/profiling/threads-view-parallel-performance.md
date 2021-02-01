---
title: Vista Subprocesos del Visualizador de simultaneidad | Microsoft Docs
description: Obtenga información sobre cómo en la vista de subprocesos puede identificar qué subprocesos ejecutan código durante un segmento de ejecución.
ms.date: 11/04/2018
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threadblocking
helpviewer_keywords:
- Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 619e76b3db67314119782ebc3010465ac7fa622f
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722729"
---
# <a name="threads-view-in-the-concurrency-visualizer"></a>Vista Subprocesos del Visualizador de simultaneidad

La vista **Subprocesos** es la más detallada y la que tiene más características del Visualizador de simultaneidad. En la vista **Subprocesos**, puede identificar qué subprocesos están ejecutando código durante un segmento de ejecución y analizar si los subprocesos se están ejecutando o bloqueando debido a la sincronización, la E/S u otras razones. La vista **Subprocesos** además informa de subprocesos de ejecución y desbloqueo del árbol de pila de llamadas de perfil.

Mientras se ejecutan los subprocesos, el Visualizador de simultaneidad recopila muestras. Cuando un subproceso deja de ejecutarse, el visualizador examina todos los eventos de cambio de contexto del sistema operativo del subproceso. Los cambios de contexto pueden producirse porque:

- Un subproceso se bloquea en una sincronización primitiva.
- Expira el cuanto de un subproceso.
- Un subproceso realiza una solicitud de E/S de bloqueo.

El Visualizador de simultaneidad clasifica los eventos de subproceso y cambio de contexto y busca API de bloqueo conocidas en la pila de llamadas de subprocesos. Muestra las categorías de subprocesos en la leyenda activa de la parte inferior izquierda de la vista **Subprocesos**. En la mayoría de los casos, puede identificar la causa de un evento de bloqueo examinando las pilas de llamadas que corresponden a los eventos de cambio de contexto.

Si no hay ninguna coincidencia de la pila de llamadas, el Visualizador de simultaneidad usa la razón de espera proporcionada por [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]. Pero la categoría de [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] puede basarse en un detalle de implementación y puede no reflejar la intención del usuario. Por ejemplo, [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] indica la razón de espera de bloqueo en un bloqueo de lectura-escritura delgado nativo como E/S, en lugar de Sincronización.

La vista **Subprocesos** también muestra las dependencias entre subprocesos. Por ejemplo, si identifica un subproceso bloqueado en un objeto de sincronización, puede encontrar el subproceso que lo ha desbloqueado. Puede examinar la pila de llamadas del subproceso de desbloqueo en el punto en que ha desbloqueado al otro.

Puede usar la vista **Subprocesos** para:

- Identificar las razones por las que la interfaz de usuario (UI) de una aplicación no responde durante ciertas fases de ejecución.
- Determinar la cantidad de tiempo dedicada al bloqueo en sincronización, E/S, errores de página y otros eventos.
- Descubrir el grado de interferencia de otros procesos que se ejecutan en el sistema.
- Identificar problemas de equilibrio de carga para la ejecución en paralelo.
- Encontrar los motivos de una escalabilidad inexistente o no óptima. Por ejemplo, por qué no mejora el rendimiento de una aplicación paralela cuando hay más núcleos lógicos disponibles.
- Entender el grado de simultaneidad en la aplicación, para ayudar en la ejecución en paralelo.
- Identificar las dependencias entre los subprocesos de trabajo y las rutas críticas de ejecución.

## <a name="use-threads-view"></a>Usar la vista Subprocesos

Para iniciar el Visualizador de simultaneidad, seleccione **Analizar** > **Visualizador de simultaneidad** y luego seleccione una opción, como **Iniciar nuevo proceso**.

El Visualizador de simultaneidad inicia la aplicación y recopila un seguimiento hasta que se selecciona **Detener recolección**. Luego el visualizador analiza el seguimiento y muestra los resultados en la página de informe de seguimiento.

Seleccione la pestaña **Subprocesos** de la parte superior izquierda del informe para abrir la vista **Subprocesos**.

![Vista Subprocesos](../profiling/media/threadsviewnarrowing.png "Vista de subprocesos")

Seleccione los intervalos de tiempo y los subprocesos para iniciar un análisis de rendimiento.

## <a name="timeline-analysis"></a>Análisis de la escala de tiempo

La parte superior de la vista **Subprocesos** es una escala de tiempo. La escala de tiempo muestra la actividad de todos los subprocesos del proceso y todos los dispositivos de disco físicos en el equipo host. También muestra los eventos de actividad y de marcador de GPU.

En la escala de tiempo, el eje x es el tiempo, mientras que en el eje y hay varios canales:

- Dos canales de E/S para cada unidad de disco en el sistema, un canal para las lecturas y otro para las escrituras.
- Un canal para cada subproceso del proceso.
- Canales de marcador, si hay eventos de marcador en el seguimiento. Los canales de marcador aparecen inicialmente en los canales de subproceso que generaron los eventos.
- Canales de GPU.

En principio, los subprocesos se clasifican en el orden en que se han creado, por lo que el subproceso de aplicación principal es el primero. Seleccione otra opción de la lista desplegable **Ordenar por** para ordenar los subprocesos por otro criterio, como **Ejecución**.

Los colores de la escala de tiempo indican el estado de un subproceso en un momento dado. Los segmentos verdes se están ejecutando, los segmentos rojos tienen la sincronización bloqueada, los segmentos amarillos se han adelantado y los segmentos púrpura están ocupados en la E/S del dispositivo.

Puede ampliar para ver más detalles o reducir para ver un intervalo de tiempo más largo. Seleccione segmentos y puntos en el gráfico para obtener detalles sobre categorías, horas de inicio, retrasos y estados de la pila de llamadas.

Use la escala de tiempo para examinar el equilibro de trabajo entre los subprocesos que intervienen en un bucle paralelo o en tareas simultáneas. Si un subproceso está tardando más tiempo en completarse que los demás, el trabajo puede estar desequilibrado. Puede mejorar el rendimiento de la aplicación si distribuye el trabajo de manera más uniforme entre los subprocesos.

Si solo hay un subproceso en ejecución en un momento determinado, es posible que la aplicación no esté aprovechando la simultaneidad en el sistema. Puede usar el gráfico de escala de tiempo para examinar las dependencias entre los subprocesos y las relaciones temporales entre los subprocesos de bloqueo y bloqueados. Para reorganizar los subprocesos, seleccione uno y luego el icono Arriba o Abajo en la barra de herramientas.

Puede ocultar los subprocesos que no realizan ningún trabajo o que están completamente bloqueados, ya que sus estadísticas son irrelevantes y pueden colapsar los informes. Oculte subprocesos al seleccionar sus nombres y luego los iconos **Ocultar subprocesos seleccionados** u **Ocultar todos salvo los subprocesos seleccionados** en la barra de herramientas. Para identificar los subprocesos que se van a ocultar, seleccione el vínculo **Resumen por subproceso** de la parte inferior izquierda. Puede ocultar los subprocesos que no tienen actividad en el gráfico **Resumen por subproceso**.

### <a name="thread-execution-details"></a>Detalles de ejecución de subprocesos
Para obtener información más detallada sobre un segmento de ejecución, seleccione un punto en un segmento verde de la escala de tiempo. El Visualizador de simultaneidad muestra un símbolo de intercalación negro sobre el punto seleccionado y presenta su pila de llamadas en la pestaña **Actual** del panel inferior. Puede seleccionar varios puntos en el segmento de ejecución.

>[!NOTE]
>Es posible que el Visualizador de simultaneidad no pueda resolver una selección en un segmento de ejecución si la duración del segmento es inferior a un milisegundo.

Para obtener un perfil de ejecución de todos los subprocesos no ocultos del intervalo de tiempo seleccionado, seleccione **Ejecución** en la leyenda de la parte inferior izquierda.

### <a name="thread-blocking-details"></a>Detalles del bloqueo de subproceso
Para obtener información sobre una región determinada de un subproceso, mantenga el puntero sobre esa región en la escala de tiempo para mostrar una información sobre herramientas. La información sobre herramientas tiene información como la categoría, la hora de inicio y el retraso. Seleccione la región para mostrar la pila de llamadas en ese momento dado en la pestaña **Actual** del panel inferior. El panel también muestra la categoría, el retraso, la API de bloqueo, si la hubiera, y el subproceso de desbloqueo, si hubiera alguno. Al examinar la pila de llamadas, puede determinar las razones subyacentes de los eventos de bloqueo de subprocesos.

Una ruta de acceso de ejecución puede tener varios eventos de bloqueo. Para examinarlos por categoría de bloqueo e identificar las áreas problemáticas más rápidamente, seleccione una categoría de bloqueo en la leyenda de la izquierda.

### <a name="dependencies-between-threads"></a>Dependencias entre subprocesos
El Visualizador de simultaneidad muestra dependencias entre subprocesos, así que puede determinar lo que estaba intentando hacer un subproceso bloqueado y qué otro subproceso le ha permitido ejecutarse.

Para determinar qué subproceso ha desbloqueado a otro, seleccione el segmento de bloqueo en la escala de tiempo. Si el visualizador de simultaneidad puede determinar el subproceso de desbloqueo, dibuja una línea entre el subproceso de desbloqueo y el segmento de ejecución que sigue el segmento de bloqueo. Seleccione la pestaña **Pila de desbloqueo** en el panel inferior para ver la pila de llamadas correspondiente.

## <a name="profile-reports"></a>Informes de perfil
Debajo del gráfico de escala de tiempo hay un panel con las pestañas de informe **Informe de perfil**, **Actual** y **Pila de desbloqueo**. Los informes se actualizan automáticamente a medida que se cambian las selecciones de la escala de tiempo y los subprocesos. En el caso de seguimientos de gran tamaño, el panel de informes podría no estar disponible temporalmente mientras se calculan las actualizaciones.

### <a name="profile-report-tab"></a>Pestaña Informe de perfil

**Informe de perfil** tiene dos filtros:

- Para filtrar las entradas del árbol de llamadas en las que se ha invertido poco tiempo, escriba un valor de filtro entre 0 y 99 por ciento en el campo **Reducción de nodos irrelevantes en**. El valor predeterminado es 2 por ciento.
- Para ver los árboles de llamadas únicamente de su código, active la casilla **Solo mi código**. Para ver todos los árboles de llamadas, desactive la casilla.

La pestaña **Informe de perfil** muestra informes de las categorías y los vínculos de la leyenda. Para mostrar un informe, seleccione una de las entradas de la izquierda:

- **Ejecución** El informe **Ejecución** muestra el desglose del tiempo que la aplicación ha invertido en la ejecución.

  Para buscar la línea de código donde transcurre el tiempo de ejecución, expanda el árbol de llamadas y, en el menú contextual de la entrada del árbol de llamadas, seleccione **Ver código fuente** o **Ver sitios de llamada**. **Ver código fuente** localiza la línea de código ejecutada. **Ver sitios de llamada** localiza la línea de código que ha llamado a la línea ejecutada. Si solo existe una línea de sitio de llamada, se resalta su código. Si hay varios sitios de llamada, seleccione el que quiera en el cuadro de diálogo y luego **Ir a código fuente**. A menudo resulta más útil buscar el sitio de llamada que tiene el mayor número de instancias, más tiempo o ambos valores. Para obtener más información, vea [Informe de perfil de ejecución](../profiling/execution-profile-report.md).

- **Sincronización** El informe **Sincronización** muestra las llamadas responsables de los bloqueos de sincronización, junto con el tiempo de bloqueo total de cada pila de llamadas. Para obtener más información, vea [Tiempo de sincronización](../profiling/synchronization-time.md).

- **E/S** El informe **E/S** muestra las llamadas responsables de los bloqueos de E/S, junto con el tiempo de bloqueo total de cada pila de llamadas. Para obtener más información, vea [Tiempo de E/S (Vista de subprocesos)](../profiling/i-o-time-threads-view.md).

- **Suspensión** El informe **Suspensión** muestra las llamadas responsables de los bloqueos de suspensión, junto con el tiempo de bloqueo total de cada pila de llamadas. Para más información, vea [Tiempo de suspensión](../profiling/sleep-time.md).

- **Administración de memoria** El informe **Administración de memoria** muestra las llamadas en las que se han producido bloqueos de administración de memoria, junto con el tiempo de bloqueo total de cada pila de llamadas. Use esta información para identificar las áreas que tienen problemas de recolección de elementos no utilizados o de paginación excesiva.  Para más información, vea [Tiempo de administración de la memoria](../profiling/memory-management-time.md).

- **Adelantamiento** El informe **Adelantamiento** muestra los puntos en que los procesos del sistema han adelantado al proceso actual, así como los subprocesos individuales que han reemplazado a los subprocesos del proceso actual. Puede utilizar esta información para identificar los procesos y subprocesos más responsables del adelantamiento. Para más información, vea [Tiempo de adelantamiento](../profiling/preemption-time.md).

- **Procesamiento de UI** El informe **Procesamiento de UI** muestra las llamadas responsables de los bloqueos de procesamiento de UI, junto con el tiempo de bloqueo total de cada pila de llamadas. Para más información, vea [Tiempo de procesamiento de la interfaz de usuario](../profiling/ui-processing-time.md).

- **Resumen por subproceso** Seleccione **Resumen por subproceso** para ver un gráfico que muestra el estado de los subprocesos del intervalo de tiempo seleccionado. Las columnas codificadas por colores muestran el tiempo total que cada subproceso ha estado en ejecución, bloqueado, en E/S y en otros estados. Los subprocesos se etiquetan en la parte inferior. Al ajustar el nivel de zoom en el gráfico de escala de tiempo, este gráfico se actualiza automáticamente.

  En algunos niveles de zoom, es posible que algunos subprocesos no se muestren en el gráfico. Si sucede eso, aparecen puntos suspensivos (**...**) a la derecha. Si el subproceso que desea no aparece, puede ocultar otros subprocesos. Para obtener más información, vea [Informe de resumen por subproceso](../profiling/per-thread-summary-report.md).

- **Operaciones en disco** Seleccione **Operaciones en disco** para mostrar los procesos y subprocesos implicados en la E/S de disco del proceso actual, los archivos que han modificado (por ejemplo, archivos DLL cargados), cuántos bytes leen y otra información. Puede usar este informe para evaluar el tiempo invertido en acceder a archivos durante la ejecución, especialmente si el proceso parece estar enlazado a E/S. Para obtener más información, vea [Informe de operaciones en disco](../profiling/disk-operations-report-threads-view.md).

### <a name="current-tab"></a>Pestaña actual
Esta pestaña muestra la pila de llamadas para un punto seleccionado en un segmento de subproceso en el gráfico de escala de tiempo. Las pilas de llamadas se recortan para mostrar únicamente la actividad relacionada con la aplicación.

### <a name="unblocking-stack-tab"></a>Pestaña Pila de desbloqueo
Esta pestaña muestra qué subproceso ha desbloqueado el subproceso seleccionado y la pila de llamadas de desbloqueo.

## <a name="see-also"></a>Consulte también
- [Visualizador de simultaneidad](../profiling/concurrency-visualizer.md)

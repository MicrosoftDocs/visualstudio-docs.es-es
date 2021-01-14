---
title: Uso de la ventana Tareas | Microsoft Docs
description: Las tareas son operaciones asincrónicas que se pueden ejecutar simultáneamente. Se pueden ejecutar varias tareas en el mismo subproceso. Use Tareas para ver la información de la tarea y del objeto WinJS.Promise.
ms.custom: SEO-VS-2020
ms.date: 03/18/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7df43a02dbda1fbcbe93decb58721032cd84d657
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150072"
---
# <a name="using-the-tasks-window-c-visual-basic-c"></a>Uso de la ventana Tareas (C#, Visual Basic, C++)

La ventana **Tareas** se parece a la ventana **Subprocesos**, solo que muestra información sobre cada objeto <xref:System.Threading.Tasks.Task?displayProperty=fullName>, [task_handle](/cpp/parallel/concrt/reference/task-group-class) o [WinJS.Promise](/previous-versions/windows/apps/br211867(v=win.10)) en lugar de cada subproceso. Como los subprocesos, las tareas representan operaciones asincrónicas que se pueden ejecutar simultáneamente; sin embargo, varias tareas se pueden ejecutar en el mismo subproceso.

En código administrado, puede utilizar la ventana **Tareas** cuando trabaje con objetos <xref:System.Threading.Tasks.Task?displayProperty=fullName> o con las palabras clave de **await** y **async** (**Await** y **Async** en Visual Basic). Para más información sobre las tareas en código administrado, consulte [Programación paralela](/dotnet/standard/parallel-programming/index).

En código nativo, puede utilizar la ventana **Tareas** cuando trabaje con [grupos de tareas](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [algoritmos paralelos](/cpp/parallel/concrt/parallel-algorithms), [agentes asincrónicos](/cpp/parallel/concrt/asynchronous-agents) y [tareas ligeras](/cpp/parallel/concrt/task-scheduler-concurrency-runtime). Para más información sobre tareas en código nativo, consulte [Runtime de simultaneidad](/cpp/parallel/concrt/concurrency-runtime).

En JavaScript, puede usar la ventana Tareas cuando trabaje con código de la sugerencia `.then`. Consulte [Programación asincrónica en JavaScript (aplicaciones para UWP)](/previous-versions/windows/apps/hh700330(v=win.10)) para más información.

Puede utilizar la ventana **Tareas** cada vez que interrumpa el depurador. Puede tener acceso a ella en el menú **Depurar** haciendo clic en **Ventanas** y, a continuación, en **Tareas**. En la siguiente ilustración se muestra la ventana **Tareas** en su modo predeterminado.

![Ventana Tareas](../debugger/media/parallel_tasks_window.png "Parallel_Tasks_Window")

> [!NOTE]
> En código administrado, un elemento <xref:System.Threading.Tasks.Task> que tiene un estado de [TaskStatus.Created](<xref:System.Threading.Tasks.TaskStatus.Created>), [TaskStatus.WaitingForActivation](<xref:System.Threading.Tasks.TaskStatus.WaitingForActivation>) o [TaskStatus.WaitingToRun](<xref:System.Threading.Tasks.TaskStatus.WaitingToRun>) podría no mostrarse en la ventana **Tareas** cuando los subprocesos administrados están en estado de suspensión o unión.

## <a name="tasks-column-information"></a>Información de la columna Tareas

Las columnas de la ventana **Tareas** muestran la siguiente información.

|Nombre de columna|Descripción|
|-----------------|-----------------|
|**Marcas**|Muestra las tareas que están marcadas y permiten marcar o desmarcar una tarea.|
|**Iconos**|Una flecha amarilla indica la tarea actual. La tarea actual es la tarea de nivel superior del subproceso actual.<br /><br /> Una flecha blanca indica la tarea de ruptura, es decir, la tarea en curso cuando se invocó el depurador.<br /><br /> El icono de pausa indica una tarea inmovilizada por el usuario. Puede inmovilizar y liberar una tarea haciendo clic con el botón secundario en ella en la lista.|
|**ID**|Un número proporcionado por sistema para la tarea. En código nativo, ésta es la dirección de la tarea.|
|**Estado**|El estado actual (programado, activo, bloqueado, interbloqueado, en espera o completado) de la tarea. Una tarea programada es la que aún no se ha ejecutado y, por consiguiente, no tiene pila de llamadas, subproceso asignado ni información relacionada.<br /><br /> Una tarea activa es la que estaba ejecutando código antes de la interrupción del depurador.<br /><br /> Una tarea en espera o bloqueada es la que se bloquea porque está esperando a que se señalice un evento, se libere un bloqueo o termine otra tarea.<br /><br /> Una tarea interbloqueada es una tarea en espera cuyo subproceso está en interbloqueo con otro subproceso.<br /><br /> Mantenga el mouse sobre la celda **Estado** de una tarea interbloqueada o en espera para ver más información sobre el bloqueo. **Advertencia:**  La ventana **Tareas** notifica un interbloqueo solo para una tarea bloqueada que utilice una sincronización primitiva compatible con WCT (Wait Chain Traversal). Por ejemplo, para un objeto <xref:System.Threading.Tasks.Task> interbloqueado, que usa WCT, el depurador notifica **Awaiting-deadlocked** (En espera con interbloqueo). Para una tarea interbloqueada administrada por el Runtime de simultaneidad, que no utiliza WCT, el depurador notifica **En espera**. Para más información sobre WCT, consulte [Wait Chain Traversal](/windows/desktop/Debug/wait-chain-traversal).|
|**Hora de inicio**|La hora en la que se activó la tarea.|
|**Duración**|El número de segundos que la tarea ha estado activa.|
|**Tiempo de finalización**|La hora en la que se completó la tarea.|
|**Ubicación**|La ubicación actual en la pila de llamadas de la tarea. Desplace el puntero del mouse sobre esta celda para ver la pila de llamadas completa de la tarea. Las tareas programadas no tienen un valor en esta columna.|
|**Task**|El método inicial y los argumentos que se pasaron a la tarea cuando se creó.|
|**AsyncState**|En el código administrado, el estado de la tarea. De forma predeterminada, se oculta esta columna. Para mostrar esta columna, abra el menú contextual de uno de los encabezados de columna. Elija **Columnas**, **AsyncState**.|
|**Parent**|El identificador del subproceso que creó esta ventana. Si está en blanco, la tarea tiene ningún primario. Esto solo es aplicable a los programas administrados.|
|**Asignación de subproceso**|El identificador y nombre del subproceso en el que la tarea se está ejecutando.|
|**AppDomain**|En código administrado, el dominio de aplicación en el que la tarea se está ejecutando.|
|**task_group**|En código nativo, la dirección del objeto [task_group](/cpp/parallel/concrt/reference/task-group-class) que programó la tarea. En los agentes asincrónicos y las tareas ligeras, esta columna se establece en 0.|
|**Process**|El identificador del proceso en el que se está ejecutando la tarea.|

 Puede agregar columnas a la vista haciendo clic con el botón secundario en un encabezado de columna y seleccionando las columnas que desea. (Quite columnas borrando las selecciones). También puede reordenar las columnas arrastrándolas a izquierda o derecha. El menú contextual de la columna se muestra en la siguiente ilustración.

 ![Menú de vista contextual en la ventana Tareas](../debugger/media/parallel_tasks_contextmenu.png "Parallel_Tasks_ContextMenu")

## <a name="sorting-tasks"></a>Ordenar Tareas
 Para ordenar las tareas por columnas, haga clic en el encabezado de columna. Por ejemplo, si hace clic en el encabezado de columna **Id.** , puede ordenar las tareas por el identificador de tarea: 1,2,3,4,5 y así sucesivamente. Para invertir el criterio de ordenación, haga clic en el encabezado de columna de nuevo. Una flecha en la columna indica el criterio y la columna de ordenación.

## <a name="grouping-tasks"></a>Agrupar tareas
 Puede agrupar tareas por cualquier columna en la vista de lista. Por ejemplo, haciendo clic con el botón derecho en el encabezado de columna **Estado** y **Agrupar por** > **[*estado*]** , puede agrupar todas las tareas que tienen el mismo estado. Por ejemplo, podría ver rápidamente las tareas en espera para que pueda centrarse en por qué se bloquean. También puede contraer un grupo que no es de interés durante la sesión de depuración. De la misma manera, puede agrupar por otras columnas. Se puede marcar o quitar la marca de un grupo haciendo clic en el botón del encabezado de grupo. En la siguiente ilustración se muestra la ventana **Tareas** en modo agrupado.

 ![Modo agrupado en la ventana Tareas](../debugger/media/parallel_tasks_groupedmode.png "Parallel_Tasks_GroupedMode")

## <a name="parent-child-view"></a>Vista de elemento primario y secundario
 (Esta vista solo está disponible en código administrado). Al hacer clic con el botón derecho en el encabezado de columna **Estado** y, luego, hacer clic en **Agrupar por** > **Primario**, puede cambiar la lista de tareas a una vista jerárquica, en la que cada tarea secundaria es un subnodo que se puede mostrar u ocultar bajo su elemento primario.

## <a name="flagging-tasks"></a>Marcar tareas
 Puede marcar el subproceso en el que se está ejecutando una tarea seleccionando el elemento de lista de tareas y, luego, eligiendo **Marcar subproceso asignado** en el menú contextual, o haciendo clic en el icono de marca de la primera columna. Si marca varias tareas, después puede ordenarlas en la columna para llevar todas las tareas marcadas a la parte superior de forma que se pueda concentrar en ellas. También puede utilizar la ventana **Pilas paralelas** para ver las tareas marcadas solamente. Esto le permite filtrar las tareas que no le interesa depurar. Las marcas no se conservan entre sesiones de depuración.

## <a name="freezing-and-thawing-tasks"></a>Inmovilizar y reanudar tareas
 Puede inmovilizar el subproceso en el que una tarea se está ejecutando haciendo clic con el botón derecho en el elemento de lista de tareas y haciendo clic en **Inmovilizar subproceso** asignado. (Si la tarea ya está inmovilizada, el comando es **Reanudar subproceso asignado**). Al inmovilizar un subproceso, no se ejecutará cuando se examine el código después del punto de interrupción actual. El comando **Inmovilizar todos los subprocesos excepto este** inmoviliza todos los subprocesos salvo el que ejecuta el elemento de la lista de tareas.

 En la siguiente ilustración se muestran el resto de elementos de menú para cada tarea.

 ![Menú de subproceso contextual en la ventana Tareas](../debugger/media/parallel_tasks_contextmenu2.png "Parallel_Tasks_ContextMenu2")

## <a name="switching-the-active-task-or-frame"></a>Cambio de la tarea o el marco activos

El comando **Cambiar a tarea** hace que la tarea actual sea la tarea activa. El comando **Cambiar a marco** hace que el marco de pila seleccionado sea el marco de pila activo. El contexto del depurador cambia a la tarea actual o al marco de pila seleccionado.

## <a name="see-also"></a>Vea también

- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
- [Depurar código administrado](../debugger/debugging-managed-code.md)
- [Programación en paralelo](/dotnet/standard/parallel-programming/index)
- [Runtime de simultaneidad](/cpp/parallel/concrt/concurrency-runtime)
- [Uso de la ventana Pilas paralelas](../debugger/using-the-parallel-stacks-window.md)
- [Tutorial: Depuración de una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md)
---
title: Usar la ventana tareas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cdf7c5fe724ff4b043ca304eee3e5e0f31b0dd85
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437706"
---
# <a name="using-the-tasks-window"></a>Usar la ventana Tareas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La ventana **Tareas** se parece a la ventana **Subprocesos**, solo que muestra información sobre cada objeto <xref:System.Threading.Tasks.Task?displayProperty=fullName>, [task_handle](http://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7) o [WinJS.Promise](http://msdn.microsoft.com/library/windows/apps/br211867.aspx) en lugar de cada subproceso. Como los subprocesos, las tareas representan operaciones asincrónicas que se pueden ejecutar simultáneamente; sin embargo, varias tareas se pueden ejecutar en el mismo subproceso. Consulte [programación asincrónica en JavaScript (aplicaciones de Windows Store)](http://msdn.microsoft.com/library/windows/apps/hh700330.aspx) para obtener más información.  
  
 En código administrado, puede utilizar la ventana **Tareas** cuando trabaje con objetos <xref:System.Threading.Tasks.Task?displayProperty=fullName> o con las palabras clave de **await** y **async** (**Await** y **Async** en Visual Basic). Para obtener más información acerca de las tareas en código administrado, consulte [Parallel Programming](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d).  
  
 En código nativo, puede utilizar la ventana **Tareas** cuando trabaje con [grupos de tareas](http://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077), [algoritmos paralelos](http://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473), [agentes asincrónicos](http://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a) y [tareas ligeras](http://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90). Para más información sobre tareas en código nativo, consulte [Runtime de simultaneidad](http://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c).  
  
 En JavaScript, puede usar la ventana Tareas cuando trabaje con código de la sugerencia .then.  
  
 Puede utilizar la ventana **Tareas** cada vez que interrumpa el depurador. Puede tener acceso a ella en el menú **Depurar** haciendo clic en **Ventanas** y, a continuación, en **Tareas**. En la siguiente ilustración se muestra la ventana **Tareas** en su modo predeterminado.  
  
 ![Ventana Tareas paralelas](../debugger/media/parallel-tasks-window.png "Parallel_Tasks_Window")  
  
> [!NOTE]
> En el código administrado, una tarea <xref:System.Threading.Tasks.Task> que tiene un estado de <xref:System.Threading.Tasks.TaskStatus>, <xref:System.Threading.Tasks.TaskStatus>, o <xref:System.Threading.Tasks.TaskStatus> podría no mostrarse en la ventana Tareas si los subprocesos administrados están en un estado de suspensión o combinación.  
  
## <a name="tasks-column-information"></a>Información de la columna Tareas  
 Las columnas de la ventana **Tareas** muestran la siguiente información.  
  
|Nombre de columna|Descripción|  
|-----------------|-----------------|  
|**Marcas**|Muestra las tareas que están marcadas y permiten marcar o desmarcar una tarea.|  
|**Iconos**|Una flecha amarilla indica la tarea actual. La tarea actual es la tarea de nivel superior del subproceso actual.<br /><br /> Una flecha blanca indica la tarea de ruptura, es decir, la tarea en curso cuando se invocó el depurador.<br /><br /> El icono de pausa indica una tarea inmovilizada por el usuario. Puede inmovilizar y liberar una tarea haciendo clic con el botón secundario en ella en la lista.|  
|**ID**|Un número proporcionado por sistema para la tarea. En código nativo, ésta es la dirección de la tarea.|  
|**Estado**|El estado actual (programado, activo, interbloqueado, en espera o completado) de la tarea. Una tarea programada es la que aún no se ha ejecutado y, por consiguiente, no tiene pila de llamadas, subproceso asignado ni información relacionada.<br /><br /> Una tarea activa es la que estaba ejecutando código antes de la interrupción del depurador.<br /><br /> Una tarea en espera es la que se bloquea porque está esperando a que se señalice un evento, se libere un bloqueo o termine otra tarea.<br /><br /> Una tarea interbloqueada es una tarea en espera cuyo subproceso está en interbloqueo con otro subproceso.<br /><br /> Mantenga el mouse sobre el **estado** celda para una tarea interbloqueada o en espera obtener más información acerca del bloque. **Advertencia:**  La ventana **Tareas** notifica un interbloqueo solo para una tarea bloqueada que utilice una sincronización primitiva compatible con WCT (Wait Chain Traversal). Por ejemplo, para un interbloqueo <xref:System.Threading.Tasks.Task> objeto, que utiliza WCT, el depurador notifica **espera con interbloqueo**. Para una tarea interbloqueada administrada por el Runtime de simultaneidad, que no utiliza WCT, el depurador notifica **En espera**. Para más información sobre WCT, consulte [Wait Chain Traversal](http://msdn.microsoft.com/library/ms681622\(VS.85\).aspx).|  
|**Hora de inicio**|La hora en la que se activó la tarea.|  
|**Duración**|El número de segundos que la tarea ha estado activa.|  
|**Tiempo de finalización**|La hora en la que se completó la tarea.|  
|**Ubicación**|La ubicación actual en la pila de llamadas de la tarea. Desplace el puntero del mouse sobre esta celda para ver la pila de llamadas completa de la tarea. Las tareas programadas no tienen un valor en esta columna.|  
|**Task**|El método inicial y los argumentos que se pasaron a la tarea cuando se creó.|  
|**Parent**|El identificador del subproceso que creó esta ventana. Si está en blanco, la tarea tiene ningún primario. Esto solo es aplicable a los programas administrados.|  
|**Asignación de subproceso**|El identificador y nombre del subproceso en el que la tarea se está ejecutando.|  
|**Estado de retorno**|El estado de la tarea cuando se completó. Los valores de estado de retorno son **éxito**, **Cancelled**, y **Error**.|  
|**AppDomain**|En código administrado, el dominio de aplicación en el que la tarea se está ejecutando.|  
|**task_group**|En código nativo, la dirección del objeto [task_group](http://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7) que programó la tarea. En los agentes asincrónicos y las tareas ligeras, esta columna se establece en 0.|  
|Proceso|El identificador del proceso en el que se está ejecutando la tarea.|  
|Estado asincrónico|En el código administrado, el estado de la tarea. De forma predeterminada, se oculta esta columna. Para mostrar esta columna, abra el menú contextual de uno de los encabezados de columna. Elija **Columnas**, **AsyncState**.|  
  
 Puede agregar columnas a la vista haciendo clic con el botón secundario en un encabezado de columna y seleccionando las columnas que desea. (Quite columnas borrando las selecciones). También puede reordenar las columnas arrastrándolas a izquierda o derecha. El menú contextual de la columna se muestra en la siguiente ilustración.  
  
 ![Menú de la vista de método abreviado en la ventana Tareas paralelas](../debugger/media/parallel-tasks-contextmenu.png "Parallel_Tasks_ContextMenu")  
  
## <a name="sorting-tasks"></a>Ordenar Tareas  
 Para ordenar las tareas por columnas, haga clic en el encabezado de columna. Por ejemplo, al hacer clic en el **ID** encabezado de columna, puede ordenar las tareas por Id. de tarea: 1,2,3,4,5 y así sucesivamente. Para invertir el criterio de ordenación, haga clic en el encabezado de columna de nuevo. Una flecha en la columna indica el criterio y la columna de ordenación.  
  
## <a name="grouping-tasks"></a>Agrupar tareas  
 Puede agrupar tareas por cualquier columna en la vista de lista. Por ejemplo, haciendo clic con el **estado** encabezado de columna y, a continuación, haga clic en **Agrupar por estado**, puede agrupar todas las tareas que tienen el mismo estado. Por ejemplo, podría ver rápidamente las tareas en espera para ver por qué se bloquean. También puede contraer un grupo que no es de interés durante la sesión de depuración. De la misma manera, puede agrupar por otras columnas. Se puede marcar o quitar la marca de un grupo haciendo clic en el botón del encabezado de grupo. En la siguiente ilustración se muestra la ventana **Tareas** en modo agrupado.  
  
 ![Modo agrupado en la ventana Tareas paralelas](../debugger/media/parallel-tasks-groupedmode.png "Parallel_Tasks_GroupedMode")  
  
## <a name="parent-child-view"></a>Vista de elemento primario y secundario  
 (Esta vista solo está disponible en código administrado). Haciendo clic en un encabezado de columna y, a continuación, haga clic en **vista de elemento primario**, puede cambiar la lista de tareas para una vista jerárquica, en los secundarios de cada tarea es un subnodo que se puede mostrar u ocultar bajo su elemento primario. En la siguiente ilustración se muestran las tareas en vista de elemento secundario y primario.  
  
 ![Elemento primario&#45;vista secundaria en la ventana Tareas paralelas](../debugger/media/parallel-tasks-parentchildview.png "Parallel_Tasks_ParentChildView")  
  
## <a name="flagging-tasks"></a>Marcar tareas  
 Puede marcar el subproceso de la lista de la tarea en el que se ejecuta una tarea seleccionando la tarea de elemento y, a continuación, elija **marca** desde el menú contextual, o haciendo clic en el icono de marca en la primera columna. Si marca varias tareas, después puede ordenarlas en la columna para llevar todas las tareas marcadas a la parte superior de forma que se pueda concentrar en ellas. También puede utilizar la ventana **Pilas paralelas** para ver las tareas marcadas solamente. Esto le permite filtrar las tareas que no le interesa depurar. Las marcas no se conservan entre sesiones de depuración.  
  
## <a name="freezing-and-thawing-tasks"></a>Inmovilizar y reanudar tareas  
 Puede inmovilizar el subproceso en el que una tarea se está ejecutando haciendo clic con el botón derecho en el elemento de lista de tareas y haciendo clic en **Inmovilizar subproceso** asignado. (Si la tarea ya está inmovilizada, el comando es **Reanudar subproceso asignado**). Al inmovilizar un subproceso, no se ejecutará cuando se recorra el código después del punto de interrupción actual. El **inmovilizar todos los subprocesos excepto este** comando inmoviliza todos los subprocesos excepto al que se está ejecutando el elemento de lista de tareas.  
  
 En la siguiente ilustración se muestran el resto de elementos de menú para cada tarea.  
  
 ![Menú de subproceso contextual en la ventana Tareas paralelas](../debugger/media/parallel-tasks-contextmenu2.png "Parallel_Tasks_ContextMenu2")  
  
## <a name="see-also"></a>Vea también  
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)   
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Parallel Programming](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)  (Programación en paralelo)  
 [Runtime de simultaneidad](http://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)   
 [Uso de la ventana Pilas paralelas](../debugger/using-the-parallel-stacks-window.md)   
 [Tutorial: Depuración de una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md)

---
title: Ver los subprocesos en la ventana Pilas paralelas | Microsoft Docs
ms.date: 11/20/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelstacks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d40df6c68b9d62ab6e96483357e45e5c8c122a0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55019598"
---
# <a name="view-threads-and-tasks-in-the-parallel-stacks-window-c-visual-basic-c"></a>Ver tareas y subprocesos en la ventana Pilas paralelas (C#, Visual Basic, C++)

El **pilas paralelas** ventana es útil para depurar aplicaciones multiproceso. Dispone de varias vistas:

- [Vista de subprocesos](#threads-view) muestra información de la pila de llamadas de todos los subprocesos en la aplicación. Puede navegar entre los subprocesos y marcos de pila de esos subprocesos. 

- [Vista tareas](#tasks-view) muestra información de la pila de llamadas centrado en la tarea. 
  - En código administrado, **tareas** vista muestra las pilas de llamadas de <xref:System.Threading.Tasks.Task?displayProperty=fullName> objetos. 
  - En código nativo, **tareas** vista muestra las pilas de llamadas de [grupos de tareas](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [algoritmos paralelos](/cpp/parallel/concrt/parallel-algorithms), [agentes asincrónicos](/cpp/parallel/concrt/asynchronous-agents)y [tareas ligeras](/cpp/parallel/concrt/task-scheduler-concurrency-runtime).  
  
- [Vista de método](#method-view) desvía la pila de llamadas en un método seleccionado. 

## <a name="use-the-parallel-stacks-window"></a>Usar la ventana Tareas paralelas 

Para abrir el **pilas paralelas** ventana, debe estar en una sesión de depuración. Seleccione **depurar** > **Windows** > **pilas paralelas**. 

### <a name="toolbar-controls"></a>Controles de la barra de herramientas

El **pilas paralelas** ventana tiene los siguientes controles de barra de herramientas: 

![Barra de herramientas de la ventana Pilas paralelas](../debugger/media/parallel_stackstoolbar.png "barra de herramientas pilas paralelas")  
  
|Iconos|Control|Descripción|  
|-|-|-|  
|![Cuadro combinado de subprocesos/tareas](media/parallel_toolbar1.png "cuadro combinado de subprocesos/tareas")|**Subprocesos**/**tareas** cuadro combinado|Intercambia la vista entre las pilas de llamadas de subprocesos y las pilas de llamadas de tareas. Para obtener más información, vea [Vista de tareas](#tasks-view) y [Vista de subprocesos](#threads-view).|  
|![Mostrar marcadas únicamente icono](media/parallel_toolbar2.png "icono Mostrar marcadas únicamente")|Mostrar marcadas únicamente|Muestra las pilas de llamadas solo para los subprocesos que están marcados en otras ventanas del depurador, como la **subprocesos de GPU** ventana y la **inspección paralela** ventana.|  
|![Alternar vista de método](media/parallel_toolbar3.png "icono Alternar vista de método")|Alternar **vista de método**|Cambia entre las vistas de pila de llamadas y **vista de método**. Para obtener más información, vea [Vista de método](#method-view).|  
|![Desplazarse de forma automática al icono actual](media/parallel_toolbar4.png "desplazar automáticamente a icono actual")|Desplazar automáticamente al marco de pila actual|Desplaza automáticamente el gráfico para que el marco de pila actual está en la vista. Esta característica es útil cuando se cambia el marco de pila actual de otras ventanas o cuando se alcanza un nuevo punto de interrupción en los gráficos de gran tamaño.|  
|![Icono de Zoom de alternancia](media/parallel_toolbar5.png "icono de Zoom del botón de alternancia")|Alternar control Zoom|Muestra u oculta el control de zoom a la izquierda de la ventana. <br /><br />Independientemente de la visibilidad del control de zoom, también puede hacer zoom presionando **Ctrl** y activar la rueda del mouse o presionando **Ctrl**+**MAYÚS** + **+** para acercar y **Ctrl**+**MAYÚS** + **-** Para alejar. |  
  
### <a name="stack-frame-icons"></a>Iconos de marco de pila
Los iconos siguientes proporcionan información sobre los marcos de pila activos actuales de todas las vistas:

|Iconos|Descripción|  
|-|-|  
|![Flecha amarilla](media/icon_parallelyellowarrow.gif)|Indica la ubicación actual (marco de pila activo) del subproceso actual.|
|![Icono de subprocesos](media/icon_parallelthreads.gif)|Indica la ubicación actual (marco de pila activo) de un subproceso distinto del actual.|
|![Flecha verde](media/icon_parallelgreenarrow.gif)|Indica el marco de pila actual (el contexto actual del depurador). El nombre del método está en negrita, siempre que aparezca.|  

### <a name="context-menu-items"></a>Elementos del menú contextual  
Los elementos de menú contextual siguientes están disponibles cuando hace clic en un método en **subprocesos** vista o **tareas** vista. Los últimos seis elementos son los mismos que en el [ventana Pila de llamadas](how-to-use-the-call-stack-window.md).  

![Menú contextual de la ventana Pilas paralelas](../debugger/media/parallel_contmenu.png "menú contextual en la ventana Pilas paralelas")  

|Elemento de menú|Descripción|  
|-|-|  
|**Marcar**|Marca el elemento seleccionado.|  
|**Quitar marcador**|Quita la marca del elemento seleccionado.|  
|**Inmovilizar**|Inmoviliza el elemento seleccionado.|  
|**Reanudar**|Reanuda el elemento seleccionado.|  
|**Cambiar a marco**|Igual que el menú correspondiente de comandos en el **pila de llamadas** ventana. Sin embargo, en el **pilas paralelas** ventana, puede ser un método en varios marcos. Puede seleccionar el fotograma que desee en el submenú de este elemento. Si uno de los marcos de pila se encuentra en el subproceso actual, ese marco se selecciona de forma predeterminada en el submenú.|  
|**Vaya a la tarea** o **ir a subproceso**|Se activa en el **tarea** o **subprocesos** vista y mantiene el mismo resaltado de marco de pila.|  
|**Ir al código fuente**|Se dirige a la ubicación correspondiente en la ventana de código fuente. |  
|**Ir al desensamblado**|Se dirige a la ubicación correspondiente en el **desensamblado** ventana.|  
|**Mostrar código externo**|Muestra u oculta el código externo.|  
|**Presentación hexadecimal**|Alterna entre la presentación hexadecimal y decimal.|  
|**Mostrar subprocesos en código fuente**|Marca la ubicación del subproceso en la ventana de código fuente. |  
|**Información de carga de símbolos**|Se abre el **información de carga de símbolos** cuadro de diálogo.|  
|**Configuración de símbolos**|Se abre el **configuración de símbolos** cuadro de diálogo. |  
  
## <a name="threads-view"></a>Vista de subprocesos  

En **subprocesos** ver, el marco de pila y la ruta de acceso de llamada del subproceso actual se resaltan en azul. Se muestra la ubicación actual del subproceso mediante la flecha amarilla. 

Para cambiar el marco de pila actual, haga doble clic en un método diferente. Esto podría cambiar también el subproceso actual, dependiendo de si el método seleccionado es parte del subproceso actual o en otro subproceso. 

Cuando el **subprocesos** ver gráfico es demasiado grande para caber en la ventana, un **vista aérea** control aparece en la ventana. Puede mover el fotograma en el control para navegar a distintas partes del gráfico.  
  
La siguiente ilustración muestra un subproceso que va de Main a una administrada para la transición de código nativo. Seis subprocesos están en el método actual. Uno sigue Thread.Sleep y otro continúa a Console.WriteLine y, a continuación, SyncTextWriter.WriteLine.  

 ![Vista en la ventana Pilas paralelas de subprocesos](../debugger/media/parallel_stack1.png "vista en la ventana Pilas paralelas de subprocesos")  

La tabla siguiente describen las características principales de la **subprocesos** vista:  
  
|Llamada|Nombre del elemento|Descripción|  
|-|-|-|  
|1|Nodo o segmento de pila de llamadas|Contiene una serie de métodos para uno o varios subprocesos. Si el marco no tiene ninguna línea de flecha conectada a ella, el marco muestra la ruta de acceso de llamadas completa para los subprocesos.|  
|2|Resaltado azul|Indica la ruta de acceso de la llamada del subproceso actual.|  
|3|Líneas de flecha|Conecta nodos para recuperar la ruta de acceso completa de la llamada de subprocesos.|  
|4|Encabezado de nodo|Muestra el número de procesos y subprocesos para el nodo.|  
|5|Método|Representa uno o más marcos de pila del mismo método.|  
|6|Información sobre herramientas en el método|Aparece cuando mantenga el mouse sobre un método. En **subprocesos** vista, la información sobre herramientas muestra todos los subprocesos en una tabla similar a la **subprocesos** ventana. |  

## <a name="tasks-view"></a>Vista de tareas  
Si su aplicación usa <xref:System.Threading.Tasks.Task?displayProperty=fullName> objetos (código administrado) o `task_handle` objetos (código nativo) para expresar el paralelismo, puede usar **tareas** vista. La **vista de tareas** muestra las pilas de llamadas de las tareas en lugar de los subprocesos. 

En **tareas** vista:  
  
- No se muestran las pilas de llamadas de subprocesos que no están ejecutando tareas.  
- Las pilas de llamadas de subprocesos que están ejecutando tareas se recortan visualmente en la parte superior e inferior, para mostrar los marcos más pertinentes para las tareas.  
- Cuando varias tareas están en un subproceso, se muestran las pilas de llamadas de esas tareas en nodos independientes.  

Para ver una pila de llamadas completa, cambie a **subprocesos** vista con el botón secundario en un marco de pila y seleccionando **ir a subproceso**.  

La siguiente ilustración muestra el **subprocesos** vista en la parte superior y el correspondiente **tareas** vista en la parte inferior.  

![Vistas de subprocesos y tareas](../debugger/media/parallel_threads-tasks.png "vistas de subprocesos y tareas")  

Mantenga el mouse sobre un método para mostrar una información sobre herramientas con información adicional. En **tareas** vista, la información sobre herramientas muestra todas las tareas en una tabla similar a la **tareas** ventana. 

La siguiente imagen muestra la información sobre herramientas para un método en el **subprocesos** vista en la parte superior y el correspondiente **tareas** vista en la parte inferior.  

![Información sobre herramientas de subprocesos y tareas](../debugger/media/parallel_threads-tasks-tooltips.png "informaciones sobre herramientas de subprocesos y tareas")  

## <a name="method-view"></a>Vista de método  
Desde **subprocesos** vista o **tareas** vista, puede dinamizar el gráfico en el método actual seleccionando el **Alternar vista de método** icono en la barra de herramientas. La **vista de método** muestra de una ojeada todos los métodos de todos los subprocesos que llaman o a los que llama el método actual. La ilustración siguiente muestra qué aspecto tiene la misma información en **subprocesos** ver a la izquierda y en **vista de método** a la derecha.  

![Subprocesos de vista y vista de método](../debugger/media/parallel_methodview.png "subprocesos vista y vista de método")  
  
Si cambia a un nuevo marco de pila, convertir ese método del método actual, y **vista de método** muestra todos los llamadores y destinatarios para el nuevo método. Esto puede hacer que algunos subprocesos aparezcan o desaparezcan de la vista, dependiendo de si ese método aparece en sus pilas de llamadas. Para volver a la vista de la pila de llamadas, seleccione el **vista de método** nuevo icono de barra de herramientas.  
  
## <a name="see-also"></a>Vea también  
 [Empezar a depurar una aplicación multiproceso](../debugger/get-started-debugging-multithreaded-apps.md)   
 [Tutorial: Depuración de una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [En primer lugar, examine el depurador](../debugger/debugger-feature-tour.md) [depurar código administrado](../debugger/debugging-managed-code.md)   
 [Programación en paralelo](/dotnet/standard/parallel-programming/index)   
 [Usar la ventana Tareas](../debugger/using-the-tasks-window.md)   
 [Clase de tarea: miembros internos](../extensibility/debugger/task-class-internal-members.md)

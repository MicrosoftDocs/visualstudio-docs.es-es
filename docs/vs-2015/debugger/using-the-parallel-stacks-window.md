---
title: Utilizando el paralelo ventana pilas | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelstacks
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df364440f544df663eff294dfd53dcd671dea049
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998683"
---
# <a name="using-the-parallel-stacks-window"></a>Uso de la ventana Tareas paralelas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El **pilas paralelas** ventana es útil cuando se depuran aplicaciones multithreading. Su **vista de subprocesos** muestra información de la pila de llamadas de todos los subprocesos en la aplicación. Permite navegar entre los subprocesos y marcos de pila de esos subprocesos. En código administrado, el **vista tareas** muestra pilas de llamadas de <xref:System.Threading.Tasks.Task?displayProperty=fullName> objetos. En código nativo, el **vista tareas** muestra pilas de llamadas de [grupos de tareas](http://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077), [algoritmos paralelos](http://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473), [agentes asincrónicos](http://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a)y [tareas ligeras](http://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90).  
  
## <a name="threads-view"></a>Vista de subprocesos  
 En la siguiente ilustración se muestra un subproceso que fue de Main a A a B y después a código externo. Otros dos subprocesos se iniciaron en código externo y fueron a A, pero uno de los subprocesos continuó a B y después a código externo, y el otro subproceso continuó a C y después a un AnonymousMethod.  
  
 ![Vista en la ventana Pilas paralelas de subprocesos](../debugger/media/parallel-stacksthread.png "Parallel_StacksThread")  
  
 En la ilustración, la ruta de acceso de la llamada del subproceso actual se resalta en azul y la flecha amarilla representa el marco de pila activo. Puede cambiar el marco de pila seleccionando un método diferente en el **pilas paralelas** ventana. Esto también puede producir el cambio del subproceso actual, dependiendo de si el método que seleccionó ya forma parte del subproceso actual o de otro. La tabla siguiente describen las características principales de la **pilas paralelas** ventana, tal como se muestra en la ilustración.  
  
|Letra de la llamada|Nombre del elemento|Descripción|  
|--------------------|------------------|-----------------|  
|A|Nodo o segmento de pila de llamadas|Contiene una serie de contextos de método para uno o más subprocesos. Si el nodo no tiene ninguna línea de flecha conectada, representa la ruta de acceso completa de la llamada de subprocesos.|  
|B|Resaltado azul|Indica la ruta de acceso de la llamada del subproceso actual.|  
|C|Líneas de flecha|Conecta nodos para recuperar la ruta de acceso completa de la llamada de subprocesos.|  
|D|Información sobre herramientas en los encabezados de nodo|Muestra el identificador y el nombre definido por el usuario de cada subproceso cuya ruta de acceso de llamada comparte este nodo.|  
|E|Contexto del método|Representa uno o más marcos de pila del mismo método.|  
|F|Información sobre herramientas en el contexto del método|En la vista de subprocesos, muestra todos los subprocesos en una tabla similar a la **subprocesos** ventana. En la vista de tareas, muestra todas las tareas en una tabla similar a la **tareas paralelas** ventana.|  
  
 Además, se muestra la ventana Pilas paralelas un **vista aérea** icono en el panel principal cuando el gráfico es demasiado grande para caber en la ventana. Puede hacer clic en este icono para ver el gráfico completo en la ventana.  
  
## <a name="method-context-icons"></a>Iconos del contexto del método  
 En la siguiente tabla se describen los iconos que proporcionan información sobre los marcos de pila activos actuales:  
  
|||  
|-|-|  
|Iconos|Descripción|  
|![Flecha amarilla de pilas paralelas](../debugger/media/icon-parallelyellowarrow.gif "Icon_ParallelYellowArrow")|Indica que el contexto del método contiene el marco de pila activo del subproceso actual.|  
|![Icono de subprocesos de pilas paralelas](../debugger/media/icon-parallelthreads.gif "Icon_ParallelThreads")|Indica que el contexto del método contiene el marco de pila activo de un subproceso que no es el actual.|  
|![Flecha verde de pilas paralelas](../debugger/media/icon-parallelgreenarrow.gif "Icon_ParallelGreenArrow")|Indica que el contexto del método contiene el marco de pila actual. Ese nombre de método está negrita en todos los nodos en los que aparece.|  
  
## <a name="toolbar-controls"></a>Controles de la barra de herramientas  
 En la siguiente ilustración y tabla se describen los controles que están disponibles en la barra de herramientas Pilas paralelas.  
  
 ![Barra de herramientas de la ventana Pilas paralelas](../debugger/media/parallel-stackstoolbar.png "Parallel_StacksToolbar")  
  
|Letra de la llamada|Control|Descripción|  
|--------------------|-------------|-----------------|  
|A|Cuadro combinado de subprocesos/tareas|Intercambia la vista entre las pilas de llamadas de subprocesos y las pilas de llamadas de tareas. Para obtener más información, vea Vista de tareas y subprocesos.|  
|B|Mostrar marcadas únicamente|Muestra las pilas de llamadas solo para los subprocesos que están marcados en otras ventanas de depuración, como la **subprocesos de GPU** ventana y la **inspección paralela** ventana.|  
|C|Alternar vista de método|Alterna entre la vista de pila y la vista de método. Para obtener más información, vea Vista de método.|  
|D|Desplazar automáticamente al marco de pila actual|Desplaza automáticamente el diagrama para que el marco de pila actual esté a la vista. Esta característica es útil cuando está cambiando el marco de pila actual de otras ventanas o cuando está alcanzando un nuevo punto de interrupción en diagramas grandes.|  
|E|Alternar control Zoom|Muestra u oculta el control Zoom. También puede hacer zoom presionando CTRL y girando la rueda del mouse, independientemente de la visibilidad del control de zoom, o mediante **CTRL + MAYÚS + '+'** para acercar y **CTRL + MAYÚS +'-'** para alejar. Al presionar **CTRL+F8** irá para ajustarse a la pantalla.|  
  
### <a name="context-menu-items"></a>Elementos del menú contextual  
 En la siguiente ilustración y tabla se describen los elementos de menú contextual que están disponibles al hacer clic con el botón secundario en un contexto de método en la vista de subprocesos o de tareas. Los últimos seis elementos se toman prestados directamente en la ventana Pila de llamadas y no presentan nuevo comportamiento.  
  
 ![Menú contextual de la ventana Pilas paralelas](../debugger/media/parallel-contmenu.png "Parallel_ContMenu")  
  
|Elemento de menú|Descripción|  
|---------------|-----------------|  
|Marcar|Marca el elemento seleccionado.|  
|Quitar marcador|Quita la marca del elemento seleccionado.|  
|Inmovilizar|Inmoviliza el elemento seleccionado.|  
|Reanudar|Reanuda el elemento seleccionado.|  
|Ir a tarea (Subproceso)|Realiza la misma función que el cuadro combinado de la barra de herramientas, pero mantiene el mismo marco de pila resaltado.|  
|Ir al código fuente|Navega hasta la ubicación en el código fuente que corresponde al marco de pila en el que el usuario hizo clic con el botón secundario.|  
|Cambiar a marco|Igual que el comando de menú correspondiente de la ventana Pila de llamadas. Sin embargo, con Pilas paralelas, varios marcos pueden corresponder a un contexto de método. Por consiguiente, el elemento de menú tiene submenús, cada uno de los cuales representa un marco de pila concreto. Si uno de los marcos de pila está en el subproceso actual, el menú que corresponde a ese marco de pila está seleccionado.|  
|Ir al desensamblado|Se desplaza hasta la ubicación en la ventana del desensamblado que corresponde al marco de pila en el que el usuario hizo clic con el botón secundario.|  
|Mostrar código externo|Muestra u oculta el código externo.|  
|Presentación hexadecimal|Alterna entre la presentación hexadecimal y decimal.|  
|Información de carga de símbolos|Muestra el cuadro de diálogo correspondiente.|  
|Valores de los símbolos|Muestra el cuadro de diálogo correspondiente.|  
  
## <a name="tasks-view"></a>Vista de tareas  
 Si la aplicación utiliza <xref:System.Threading.Tasks.Task?displayProperty=fullName> objetos (código administrado) o `task_handle` objetos (código nativo) para expresar el paralelismo, puede usar el cuadro combinado en la barra de herramientas de la ventana Pilas paralelas para pasar a *vista tareas*. La vista de tareas muestra las pilas de llamadas de las tareas en lugar de los subprocesos. La vista de tareas difiere en la vista de subprocesos en lo siguiente:  
  
- No se muestran las pilas de llamadas de los subprocesos que no están ejecutando tareas.  
  
- Las pilas de llamadas de los subprocesos que están ejecutando tareas se recortan visualmente en la parte superior y superior para mostrar los marcos más pertinentes que pertenecen a las tareas.  
  
- Cuando varias tareas están en un subproceso, las pilas de llamadas de esas tareas se dividen en nodos independientes.  
  
  En la siguiente ilustración se muestra la vista de tareas de pilas paralelas a la derecha y la vista de subprocesos correspondiente a la izquierda.  
  
  ![Vista en la ventana Pilas paralelas tareas](../debugger/media/parallel-tasksview.png "Parallel_TasksView")  
  
  Para ver la pila de llamadas completa, simplemente cambie a la vista subprocesos haciendo clic en un marco de pila y, a continuación, haga clic en **ir a subproceso**.  
  
  Tal y como se describe en la tabla anterior, desplazando el puntero del mouse sobre un contexto de método, puede ver información adicional. En la imagen siguiente se muestra la información de la información sobre herramientas para la vista de subprocesos y de tareas.  
  
  ![Información sobre herramientas en la ventana Pilas paralelas](../debugger/media/parallel-stack-tooltips.png "Parallel_Stack_Tooltips")  
  
## <a name="method-view"></a>Vista de método  
 Desde la vista de subprocesos o la de tareas, puede dinamizar el gráfico del método actual haciendo clic en el icono Vista de método de la barra de herramientas. La vista de método muestra de una ojeada todos los métodos de todos los subprocesos que llaman o a los que llama el método actual. En la siguiente ilustración se muestra un vista de subprocesos y también el aspecto que tiene la misma información en la vista de método.  
  
 ![Vista de método en la ventana Pilas paralelas](../debugger/media/parallel-methodview.png "Parallel_MethodView")  
  
 Si se pasa a un nuevo marco de pila, ese método se convierte en el método actual y hace que la ventana muestre todos los llamadores y destinatarios del nuevo método. Esto puede hacer que algunos subprocesos aparezcan o desaparezcan de la vista, dependiendo de si ese método aparece en sus pilas de llamadas. Para volver a la vista de pilas, haga clic de nuevo en el botón de la barra de herramientas de la vista de método.  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Depurar una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)   
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Parallel Programming](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)  (Programación en paralelo)  
 [Usar la ventana tareas](../debugger/using-the-tasks-window.md)   
 [Tutorial: Depurar una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Clase Task](../extensibility/debugger/task-class-internal-members.md)

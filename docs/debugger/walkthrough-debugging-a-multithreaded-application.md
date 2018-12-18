---
title: Ver conversaciones en el depurador | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 14b170e6f8259776941ce0fcc2a2866a9084cffb
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607723"
---
# <a name="view-threads-in-the-visual-studio-debugger-by-using-the-threads-window"></a>Vista de subprocesos en el depurador de Visual Studio mediante el uso de la ventana subprocesos
En el **subprocesos** ventana, puede examinar y trabajar con los subprocesos en la aplicación que está depurando. Para obtener instrucciones detalladas sobre cómo usar el **subprocesos** ventana, consulte [Tutorial: depurar mediante el uso de la ventana subprocesos](../debugger/how-to-use-the-threads-window.md).

## <a name="use-the-threads-window"></a>Usar la ventana Subprocesos 
 El **subprocesos** ventana contiene una tabla donde cada fila describe un subproceso independiente en la aplicación. De forma predeterminada, la tabla enumeran todos los subprocesos en la aplicación, pero puede filtrar la lista para mostrar únicamente los subprocesos que le interesen. Cada columna describe un tipo diferente de información. También puede ocultar algunas columnas. Si muestra todas las columnas, aparecerán las siguientes columnas, de izquierda a derecha:  
  
- **Marca**: en esta columna no etiquetada, puede marcar un subproceso al que desea prestar atención especial. Para obtener información acerca de cómo marcar un subproceso, vea [Cómo: marca y desmarcar subprocesos](../debugger/how-to-flag-and-unflag-threads.md).  
  
- **Subproceso actual**: en esta columna no etiquetada, una flecha amarilla indica que el subproceso actual. Esquema de una flecha indica el contexto del depurador actual para un subproceso distinto del actual.
  
- **Id. de**: muestra el número de identificación para cada subproceso.  
  
- **Identificador administrado**: muestra los números de identificación administrados para los subprocesos administrados.  
  
- **Categoría**: muestra la categoría de subprocesos como subprocesos de interfaz de usuario, controladores de llamadas a procedimientos remotos o subprocesos de trabajo. Una categoría especial identifica el subproceso principal de la aplicación.  
  
- **Nombre**: identifica cada subproceso por su nombre, si lo tiene, o como \<sin nombre >.  
  
- **Ubicación**: muestra donde se está ejecutando el subproceso. Puede expandir esta ubicación para mostrar la pila de llamadas completa del subproceso.  
  
- **Prioridad**: una columna avanzada (oculta de forma predeterminada) que muestra la prioridad o prioridad que el sistema ha asignado a cada subproceso.  
  
- **Máscara de afinidad**: una columna avanzada (oculta de forma predeterminada) que se muestra la máscara de afinidad de procesador para cada subproceso. En un sistema multiprocesador, la máscara de afinidad determina los procesadores en los que se puede ejecutar un subproceso.  
  
- **Recuento de suspendidos**: una columna avanzada (oculta de forma predeterminada) que muestra el recuento de suspensión. Este recuento determina si un subproceso se puede ejecutar. Para obtener más información sobre recuentos suspendidos, consulte [inmovilizar y reanudar subprocesos](#freeze-and-thaw-threads).  
  
- **Nombre del proceso**: una columna avanzada (oculta de forma predeterminada) que muestra el proceso al que pertenece cada subproceso. Los datos de esta columna pueden ser útiles al depurar varios procesos.  

- **Id. de proceso**: Id. de una columna avanzada (oculta de forma predeterminada) que muestra el proceso al que pertenece cada subproceso. 

- **Calificador de transporte**: una columna avanzada (oculta de forma predeterminada) que identifica el equipo al que está conectado el depurador. 
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Para mostrar la ventana Subprocesos en modo de interrupción o modo de ejecución  
  
-   Mientras Visual Studio está en modo de depuración, seleccione el **depurar** menú, elija **Windows**y, a continuación, seleccione **subprocesos**.  
  
### <a name="to-display-or-hide-a-column"></a>Mostrar u ocultar columnas  
  
-   En la barra de herramientas en la parte superior de la **subprocesos** ventana, seleccione **columnas**. A continuación, active o desactive el nombre de la columna que desea mostrar u ocultar.  

## <a name="display-flagged-threads"></a>Mostrar subprocesos marcados  
 Puede marcar un subproceso que desea prestar atención especial con un icono en el **subprocesos** ventana. Para obtener más información, consulte [Cómo: marcar y desmarcar subprocesos](../debugger/how-to-flag-and-unflag-threads.md). En el **subprocesos** ventana, puede elegir mostrar todos los subprocesos o solo los subprocesos marcados.  
  
### <a name="to-display-only-flagged-threads"></a>Para mostrar solo los subprocesos marcados  
  
-   Elija **mostrar solo subprocesos de marcados** en la barra de herramientas en la parte superior de la **subprocesos** ventana. (Si lo está atenuado, deberá marcar algunos subprocesos en primer lugar.) 

## <a name="freeze-and-thaw-threads"></a>Inmovilizar y reanudar subprocesos  
 Al inmovilizar un subproceso, el sistema no inicia la ejecución del subproceso incluso si hay recursos disponibles.  
  
 En código nativo, puede suspender o reanudar subprocesos mediante una llamada a las funciones de Windows `SuspendThread` y `ResumeThread`. O bien, llamar a las funciones MFC [CWinThread:: SuspendThread](/cpp/mfc/reference/CWinThread-class#suspendthread) y [CWinThread:: ResumeThread](/cpp/mfc/reference/CWinThread-class#resumethread). Si se llama a `SuspendThread` o `ResumeThread`, *recuento de suspendidos* se muestra en el **subprocesos** se cambiará la ventana. El recuento de suspensión no cambia si inmoviliza o reanuda un subproceso nativo. No se puede ejecutar un subproceso en código nativo, a menos que se reanude y tiene un recuento de suspensión de cero.  
  
 En código administrado, el recuento de suspensión cambia al inmovilizar o reanudar un subproceso. Si se inmoviliza un subproceso en código administrado, su recuento de suspensión es 1. Al inmovilizar un subproceso en código nativo, su recuento de suspensión es 0, a menos que se usó el `SuspendThread` llamar.  
  
> [!NOTE]
>  Cuando se depura una llamada de código nativo a código administrado, el código administrado se ejecuta en el mismo subproceso físico que el código nativo que lo llama. La suspensión o la inmovilización del subproceso nativo inmoviliza también el código administrado.  
  
### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Para inmovilizar o reanudar la ejecución de un subproceso  
  
-   En la barra de herramientas en la parte superior de la **subprocesos** ventana, seleccione **inmovilizar subprocesos** o **reanudar subprocesos**.  
  
     Esta acción afecta solo a los subprocesos que están seleccionados en el **subprocesos** ventana. 

### <a name="switch-to-another-thread"></a>Cambiar a otro subproceso 

Una flecha amarilla indica el subproceso actual (y la ubicación del puntero de ejecución). Una flecha verde con una cola rizada indica que un subproceso distinto del actual tiene el contexto actual del depurador.

#### <a name="to-switch-to-another-thread"></a>Para cambiar a otro subproceso  
  
-   Siga cualquiera de los pasos siguientes:  
  
    -   Haga doble clic en un subproceso cualquiera.  
  
    -   Haga clic en un subproceso y seleccione **cambiar a subproceso**.

## <a name="group-and-sort-threads"></a>Agrupar y ordenar subprocesos  
 Al agrupar los subprocesos, aparece un encabezado en la tabla para cada grupo. El encabezado contiene una descripción del grupo, como **subproceso de trabajo** o **subprocesos sin marcar**y un control de árbol. Los subprocesos de los miembros de cada de grupo aparecen bajo el título del grupo. Si desea ocultar los subprocesos de los miembros de un grupo, utilice el control de árbol para contraer el grupo.  
  
 Dado que la agrupación tiene prioridad sobre la ordenación, puede agrupar los subprocesos por categoría, por ejemplo, y, a continuación, ordenarlos por el identificador de cada categoría.  
  
### <a name="to-sort-threads"></a>Para ordenar los subprocesos  
  
1.  En la barra de herramientas en la parte superior de la **subprocesos** ventana, seleccione el botón situado en la parte superior de cualquier columna.  
  
     Los subprocesos están ahora ordenados según los valores de esa columna.  
  
2.  Si desea invertir el criterio de ordenación, seleccione el mismo botón de nuevo.  
  
     Los subprocesos que aparecieron en la parte superior de la lista aparecen ahora en la parte inferior.  
  
### <a name="to-group-threads"></a>Para agrupar subprocesos  
  
-   En el **subprocesos** barra de herramientas, seleccione el **Agrupar por** lista y, después, seleccione los criterios que desea agrupar los subprocesos.  
  
### <a name="to-sort-threads-within-groups"></a>Para ordenar los subprocesos dentro de los grupos  
  
1.  En la barra de herramientas en la parte superior de la **subprocesos** ventana, seleccione el **Agrupar por** lista y, después, seleccione los criterios que desea agrupar los subprocesos.  
  
2.  En el **subprocesos** ventana, seleccione el botón situado en la parte superior de cualquier columna.  
  
     Los subprocesos están ahora ordenados según los valores de esa columna.  
  
### <a name="to-expand-or-collapse-all-groups"></a>Expandir o contraer todos los grupos  
  
-   En la barra de herramientas en la parte superior de la **subprocesos** ventana, seleccione **expandir grupos** o **contraer grupos**.  
  
## <a name="search-for-specific-threads"></a>Buscar subprocesos concretos  
 Puede buscar subprocesos que coincidan con una cadena especificada en el **subprocesos** ventana. Cuando busque subprocesos, la ventana muestra todos los subprocesos de coincidencia de la cadena de búsqueda en cualquier columna. Esta información incluye la ubicación del subproceso que aparece en la parte superior de la pila de llamadas en el **ubicación** columna. De forma predeterminada, no se buscará en la pila de llamadas completa.  
  
### <a name="to-search-for-specific-threads"></a>Para buscar subprocesos concretos  
  
1. En la barra de herramientas en la parte superior de la **subprocesos** ventana, vaya a la **búsqueda** cuadro y, o bien:  

     - Escriba una cadena de búsqueda y, a continuación, presione **ENTRAR**.  
  
     \- o -  
  
     - Seleccione la lista desplegable situada junto a la **búsqueda** cuadro y seleccione una cadena de búsqueda de una búsqueda anterior.  
  
2. (Opcional) Para incluir la pila de llamadas completa en la búsqueda, seleccione **pila de llamadas de búsqueda**.   
  
## <a name="display-thread-call-stacks-and-switch-between-frames"></a>Mostrar pilas de llamadas de subprocesos y cambiar entre marcos  
En un programa multiproceso, cada subproceso tiene su propia pila de llamadas. El **subprocesos** ventana proporciona una manera cómoda de ver estas pilas.

> [!TIP]
> Para obtener una representación visual de la pila de llamadas para cada subproceso, use el [pilas paralelas](../debugger/get-started-debugging-multithreaded-apps.md) ventana.
  
### <a name="to-view-the-call-stack-of-a-thread"></a>Para ver la pila de llamadas de un subproceso  
  
-   En el **ubicación** columna, seleccione el triángulo invertido situado junto a la ubicación del subproceso.  
  
     La ubicación se expande para mostrar la pila de llamadas del subproceso.  
  
### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Para ver o contraer las pilas de llamadas de todos los subprocesos  
  
-   En la barra de herramientas en la parte superior de la **subprocesos** ventana, seleccione **Expandir pilas de llamadas** o **Contraer pilas de llamadas**.  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Empezar a depurar aplicaciones multiproceso](../debugger/get-started-debugging-multithreaded-apps.md)
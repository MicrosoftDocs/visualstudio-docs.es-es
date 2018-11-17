---
title: 'Cómo: utilizar la ventana subprocesos | Microsoft Docs'
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
- vs.debug.threads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 925e5ec609c07fa1ca6d703943cf3437f0f9bf84
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791704"
---
# <a name="how-to-use-the-threads-window"></a>Cómo: Utilizar la ventana Subprocesos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En el **subprocesos** ventana, puede examinar y trabajar con los subprocesos en la aplicación que está depurando.  
  
 El **subprocesos** ventana contiene una tabla donde cada fila representa un subproceso de la aplicación. De forma predeterminada, la tabla hace una lista de todos los subprocesos, pero puede filtrar la lista para mostrar solo los que le interesan. Cada columna contiene un tipo diferente de información. También puede ocultar algunas columnas. Si muestra todas las columnas, la siguiente información aparece de izquierda a derecha:  
  
-   La columna de marcas, donde puede marcar un subproceso al que desea prestar atención especial. Para obtener información acerca de cómo marcar un subproceso, vea [Cómo: quitar marcadores de subprocesos y marca](../debugger/how-to-flag-and-unflag-threads.md).  
  
-   La columna del subproceso activo, donde una flecha amarilla indica un subproceso activo. El contorno de una flecha indica el subproceso donde la ejecución interrumpió el depurador.  
  
-   El **ID** columna, que contiene el número de identificación para cada subproceso.  
  
-   El **Managed ID** columna, que contiene los números de identificación administrados para los subprocesos administrados.  
  
-   El **categoría** columna, que clasifica los subprocesos como subprocesos de interfaz de usuario, controladores de llamadas a procedimientos remotos o subprocesos de trabajo. Una categoría especial identifica el subproceso principal de la aplicación.  
  
-   El **nombre** columna, que identifica cada subproceso por su nombre, si lo tiene, o como \<sin nombre >.  
  
-   El **ubicación** columna, que muestra dónde se está ejecutando el subproceso. Puede expandir esta ubicación para mostrar la pila de llamadas completa del subproceso.  
  
-   El **prioridad** columna, que contiene la prioridad o prioridad que el sistema ha asignado a cada subproceso.  
  
-   El **Affinity Mask** columna, que es una columna avanzada que normalmente se oculta. Esta columna muestra la máscara de afinidad del procesador para cada subproceso. En un sistema multiprocesador, la máscara de afinidad determina los procesadores en los que se puede ejecutar un subproceso.  
  
-   El **número de suspendidos** columna, que contiene el recuento de suspensión. Este recuento determina si un subproceso se puede ejecutar. Para obtener una explicación sobre el recuento de suspensión, vea la sección Inmovilizar y reanudar subprocesos más adelante en este tema.  
  
-   El **nombre del proceso** columna, que contiene el proceso al que pertenece cada subproceso. Esta columna puede ser útil cuando está depurando varios procesos, pero normalmente se oculta.  
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Para mostrar la ventana Subprocesos en modo de interrupción o modo de ejecución  
  
-   En el **depurar** menú, elija **Windows**y, a continuación, haga clic en **subprocesos**.  
  
### <a name="to-display-or-hide-a-column"></a>Mostrar u ocultar columnas  
  
-   En la barra de herramientas en la parte superior de la **subprocesos** ventana, haga clic en **columnas**, a continuación, active o desactive el nombre de la columna que desea mostrar u ocultar.  
  
### <a name="to-switch-the-active-thread"></a>Para cambiar el subproceso activo  
  
-   Realice uno de estos pasos:  
  
    -   Haga doble clic en un subproceso cualquiera.  
  
    -   Haga clic en un subproceso y haga clic en **cambiar a subproceso**.  
  
         La flecha amarilla aparece al lado del nuevo subproceso activo. El contorno deshabilitado de una flecha identifica el subproceso donde la ejecución interrumpió el depurador.  
  
## <a name="grouping-and-sorting-threads"></a>Agrupar y ordenar subprocesos  
 Al agrupar los subprocesos, aparece un encabezado en la tabla para cada grupo. El encabezado contiene una descripción de grupo, como "Subproceso de trabajadores" o "Subprocesos sin marcar" y un control de árbol. Los subprocesos de los miembros de cada de grupo aparecen bajo el título del grupo. Si desea ocultar los subprocesos de los miembros de un grupo, puede utilizar el control de árbol para contraer el grupo.  
  
 Dado que la agrupación tiene prioridad sobre la ordenación, puede agrupar los subprocesos por categoría, por ejemplo, y, a continuación, ordenarlos por el identificador de cada categoría.  
  
#### <a name="to-sort-threads"></a>Para ordenar los subprocesos  
  
1.  En la barra de herramientas en la parte superior de la **subprocesos** ventana, haga clic en el botón situado en la parte superior de cualquier columna.  
  
     Los subprocesos están ahora ordenados según los valores de esa columna.  
  
2.  Si desea invertir el criterio de ordenación, haga clic de nuevo en el mismo botón.  
  
     Los subprocesos que aparecieron en la parte superior de la lista aparecen ahora en la parte inferior.  
  
#### <a name="to-group-threads"></a>Para agrupar subprocesos  
  
-   En el **subprocesos** barra de herramientas de la ventana, haga clic en el **Agrupar por** lista y, después, haga clic en los criterios que desea agrupar los subprocesos.  
  
#### <a name="to-sort-threads-within-groups"></a>Para ordenar los subprocesos dentro de los grupos  
  
1.  En la barra de herramientas en la parte superior de la **subprocesos** ventana, haga clic en el **Agrupar por** lista y, después, haga clic en los criterios que desea agrupar los subprocesos.  
  
2.  En el **subprocesos** ventana, haga clic en el botón situado en la parte superior de cualquier columna.  
  
     Los subprocesos están ahora ordenados según los valores de esa columna.  
  
#### <a name="to-expand-or-collapse-all-groups"></a>Expandir o contraer todos los grupos  
  
-   En la barra de herramientas en la parte superior de la **subprocesos** ventana, haga clic en **expandir grupos** o **contraer grupos**.  
  
## <a name="searching-for-specific-threads"></a>Buscar Subprocesos concretos  
 En [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], puede buscar subprocesos que coincidan con una cadena especificada. Cuando busque subprocesos en la **subprocesos** ventana, la ventana muestra todos los subprocesos que coincidan con la cadena de búsqueda en cualquier columna. Esa información incluye la ubicación del subproceso que aparece en la parte superior de la pila de llamadas en el **ubicación** columna. De forma predeterminada, sin embargo, la pila de llamadas completa no se busca.  
  
#### <a name="to-search-for-specific-threads"></a>Para buscar subprocesos concretos  
  
-   En la barra de herramientas en la parte superior de la **subprocesos** ventana, vaya a la **búsqueda** cuadro y, o bien:  
  
    -   Escriba una cadena de búsqueda y, a continuación, presione ENTRAR.  
  
         \- o -  
  
    -   Haga clic en la lista desplegable situada junto a la **búsqueda** cuadro y seleccione una cadena de búsqueda de una búsqueda anterior.  
  
-   (Opcional) Para incluir la pila de llamadas completa en la búsqueda, seleccione **pila de llamadas de búsqueda**.  
  
## <a name="freezing-and-thawing-threads"></a>Inmovilizar y reanudar subprocesos  
 Cuando se inmoviliza un subproceso, el sistema no iniciará su ejecución aunque haya recursos disponibles.  
  
 En código nativo, puede suspender o reanudar subprocesos mediante una llamada a las funciones de Windows `SuspendThread` y `ResumeThread` o las funciones MFC [CWinThread:: SuspendThread](http://msdn.microsoft.com/library/57189c7e-fd71-42e5-bc4b-3de7cd373d28) y [CWinThread:: ResumeThread](http://msdn.microsoft.com/library/d6f97a2f-5c9f-4ee1-b978-d74938784db5). Si se llama a `SuspendThread` o `ResumeThread`, cambia el *recuento de suspendidos*, que aparece en el **subprocesos** ventana. Sin embargo, si inmoviliza o reanuda un subproceso nativo, no cambia el recuento de suspendidos. En código nativo, un subproceso no se puede ejecutar a menos que se reanude y tenga un recuento de suspensión de cero.  
  
 En código administrado, la inmovilización o la reanudación de un subproceso no cambia el recuento de suspensión. En código administrado, un subproceso inmovilizado tiene un recuento de suspensión de 1. En código nativo, un subproceso inmovilizado tiene un recuento de suspensión de 0, a menos que el subproceso se haya suspendido con una llamada a `SuspendThread`.  
  
> [!NOTE]
>  Cuando se depura una llamada de código nativo a código administrado, el código administrado se ejecuta en el mismo subproceso físico que el código nativo que lo llama. La suspensión o la inmovilización del subproceso nativo inmoviliza también el código administrado.  
  
#### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Para inmovilizar o reanudar la ejecución de un subproceso  
  
-   En la barra de herramientas en la parte superior de la **subprocesos** ventana, haga clic en **inmovilizar subprocesos** o **reanudar subprocesos**.  
  
     Esta acción afecta solo a los subprocesos que están seleccionados en el **subprocesos** ventana.  
  
## <a name="displaying-flagged-threads"></a>Mostrar los subprocesos marcados  
 Puede marcar un subproceso que desea prestar atención especial con un icono en el **subprocesos** ventana. Para obtener más información, consulte [Cómo: quitar marcadores de subprocesos y marca](../debugger/how-to-flag-and-unflag-threads.md). En la ventana Subprocesos puede decidir si desea mostrar todos los subprocesos o solo los subprocesos marcados.  
  
#### <a name="to-display-only-flagged-threads"></a>Para mostrar solo los subprocesos marcados  
  
-   Elija el botón de marca en la esquina superior izquierda de la **subprocesos** ventana.  
  
## <a name="displaying-thread-call-stacks-and-switching-between-frames"></a>Mostrar pilas de llamadas de subprocesos y cambiar entre marcos  
 En un programa multiproceso, cada subproceso tiene su propia pila de llamadas. El **subprocesos** ventana proporciona una manera cómoda de ver estas pilas.  
  
#### <a name="to-view-the-call-stack-of-a-thread"></a>Para ver la pila de llamadas de un subproceso  
  
-   En el **ubicación** columna, haga clic en el triángulo invertido situado junto a la ubicación del subproceso.  
  
     La ubicación se expande para mostrar la pila de llamadas del subproceso.  
  
#### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Para ver o contraer las pilas de llamadas de todos los subprocesos  
  
-   En la barra de herramientas en la parte superior de la **subprocesos** ventana, haga clic en **Expandir pilas de llamadas** o **Contraer pilas de llamadas**.  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Tutorial: Depurar una aplicación multiproceso](../debugger/walkthrough-debugging-a-multithreaded-application.md)




---
title: Visualización de subprocesos en el depurador | Microsoft Docs
description: Use la opción Subprocesos para examinar y controlar los subprocesos. Puede agrupar, ordenar, marcar, inmovilizar, reanudar y buscar subprocesos, seleccionar columnas y mostrar pilas de llamadas.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cd11e722886b77e9faaace768cc30a74c759903f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884213"
---
# <a name="view-threads-in-the-visual-studio-debugger-by-using-the-threads-window-c-visual-basic-c"></a>Visualización de subprocesos en el depurador de Visual Studio mediante la ventana Subprocesos (C#, Visual Basic, C++)
Desde la ventana **Subprocesos**, puede examinar y trabajar con los subprocesos de la aplicación que esté depurando. Para obtener instrucciones paso a paso sobre cómo usar la ventana **Subprocesos**, vea [Tutorial: Depuración con la ventana Subprocesos](../debugger/how-to-use-the-threads-window.md).

## <a name="use-the-threads-window"></a>Usar la ventana Subprocesos
 La ventana **Subprocesos** contiene una tabla donde cada fila describe un subproceso distinto de la aplicación. De forma predeterminada, en la tabla se enumeran todos los subprocesos, pero puede filtrar la lista para mostrar solo los que le interesen. Cada columna describe un tipo diferente de información. También puede ocultar algunas columnas. Si muestra todas las columnas, aparecen las siguientes de izquierda a derecha:

- **Marca**: en esta columna sin etiquetar, puede marcar un subproceso al que quiera prestar atención especial. Para obtener información sobre cómo marcar un subproceso, vea [Procedimiento para marcar y desmarcar subprocesos](../debugger/how-to-flag-and-unflag-threads.md).

- **Subproceso actual**: en esta columna sin etiquetar, una flecha de color amarillo indica el subproceso actual. Un contorno de flecha indica el contexto del depurador actual para un subproceso no actual.

- **Identificador**: muestra el número de identificación de cada subproceso.

- **Identificador administrado**: muestra los números de identificación administrados para los subprocesos administrados.

- **Categoría**: muestra la categoría de los subprocesos como subprocesos de interfaz de usuario, controladores de llamadas a procedimientos remotos o subprocesos de trabajo. Una categoría especial identifica el subproceso principal de la aplicación.

- **Name**: identifica cada subproceso por nombre, si lo tiene, o como \<No Name>.

- **Ubicación**: muestra dónde se ejecuta el subproceso. Puede expandir esta ubicación para mostrar la pila de llamadas completa del subproceso.

- **Prioridad**: una columna avanzada (oculta de forma predeterminada) en la que se muestra la prioridad que el sistema ha asignado a cada subproceso.

- **Máscara de afinidad**: una columna avanzada (oculta de forma predeterminada) en la que se muestra la máscara de afinidad de procesador para cada subproceso. En un sistema multiprocesador, la máscara de afinidad determina los procesadores en los que se puede ejecutar un subproceso.

- **Número de suspendidos**: una columna avanzada (oculta de forma predeterminada) en la que se muestra el número de suspendidos. Este recuento determina si un subproceso se puede ejecutar. Para obtener más información sobre el número de suspendidos, vea [Inmovilizar y reanudar subprocesos](#freeze-and-thaw-threads).

- **Nombre del proceso**: una columna avanzada (oculta de forma predeterminada) en la que se muestra el proceso al que pertenece cada subproceso. Los datos de esta columna pueden ser útiles cuando se depuran muchos procesos.

- **Identificador de proceso**: una columna avanzada (oculta de forma predeterminada) en la que se muestra el identificador de proceso al que pertenece cada subproceso.

- **Calificador de transporte**: una columna avanzada (oculta de forma predeterminada) en la que se identifica el equipo al que está conectado el depurador.

### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Para mostrar la ventana Subprocesos en modo de interrupción o modo de ejecución

- Mientras Visual Studio está en modo de depuración, seleccione el menú **Depurar**, **Ventanas** y, después, **Subprocesos**.

### <a name="to-display-or-hide-a-column"></a>Mostrar u ocultar columnas

- En la barra de herramientas de la parte superior de la ventana **Subprocesos**, seleccione **Columnas**. Después, active o desactive el nombre de la columna que quiera mostrar u ocultar.

## <a name="display-flagged-threads"></a>Representación de subprocesos marcados
 Puede marcar un subproceso al que quiera prestar atención especial con un icono en la ventana **Subprocesos**. Para obtener más información, vea [Cómo: marcar y desmarcar subprocesos](../debugger/how-to-flag-and-unflag-threads.md). En la ventana **Subprocesos** puede decidir si quiere mostrar todos los subprocesos o solo los marcados.

### <a name="to-display-only-flagged-threads"></a>Para mostrar solo los subprocesos marcados

- Elija **Mostrar solo subprocesos marcados** en la barra de herramientas situada en la parte superior de la ventana **Subprocesos**. (Si está atenuada, primero tendrá que marcar algunos subprocesos).

## <a name="freeze-and-thaw-threads"></a>Inmovilizar y reanudar subprocesos
 Cuando se inmoviliza un subproceso, el sistema no iniciará su ejecución aunque haya recursos disponibles.

 En código nativo, los subprocesos se pueden suspender o reanudar si se llama a las funciones `SuspendThread` y `ResumeThread` de Windows. O bien, llame a las funciones de MFC [CWinThread::SuspendThread](/cpp/mfc/reference/CWinThread-class#suspendthread) y [CWinThread::ResumeThread](/cpp/mfc/reference/CWinThread-class#resumethread). Si llama a `SuspendThread` o `ResumeThread`, se cambiará el *número de suspendidos* en la ventana **Subprocesos**. El número de suspendidos no cambia si inmoviliza o reanuda un subproceso nativo. En código nativo, un subproceso no se puede ejecutar a menos que se reanude y tenga un número de suspendidos de cero.

 En código administrado, el número de suspendidos cambia al inmovilizar o reanudar un subproceso. Si inmoviliza un subproceso en código administrado, su número de suspendidos es 1. Al inmovilizar un subproceso en código nativo, su número de suspendidos es 0, a menos que se use la llamada a `SuspendThread`.

> [!NOTE]
> Cuando se depura una llamada de código nativo a código administrado, el código administrado se ejecuta en el mismo subproceso físico que el código nativo que lo llama. La suspensión o la inmovilización del subproceso nativo inmoviliza también el código administrado.

### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Para inmovilizar o reanudar la ejecución de un subproceso

- En la barra de herramientas de la parte superior de la ventana **Subprocesos**, seleccione **Inmovilizar subprocesos** o **Reanudar subprocesos**.

     Esta acción solo afecta a los subprocesos que están seleccionados en la ventana **Subprocesos**.

### <a name="switch-to-another-thread"></a>Cambio a otro subproceso

Una flecha de color amarillo indica el subproceso actual (y la ubicación del puntero de ejecución). Una flecha de color verde con un extremo curvo indica que un subproceso no actual tiene el contexto del depurador actual.

#### <a name="to-switch-to-another-thread"></a>Para cambiar a otro subproceso

- Siga uno de estos pasos:

  - Haga doble clic en un subproceso cualquiera.

  - Haga clic con el botón derecho en otro subproceso y seleccione **Cambiar a subproceso**.

## <a name="group-and-sort-threads"></a>Agrupación y ordenación de subprocesos
 Al agrupar los subprocesos, aparece un encabezado en la tabla para cada grupo. El título contiene una descripción de grupo, como **Subproceso de trabajadores** o **Subprocesos sin marcar** y un control de árbol. Los subprocesos de los miembros de cada de grupo aparecen bajo el título del grupo. Si quiere ocultar los subprocesos de los miembros de un grupo, use el control de árbol para contraer el grupo.

 Dado que la agrupación tiene prioridad sobre la ordenación, puede agrupar los subprocesos por categoría, por ejemplo, y, a continuación, ordenarlos por el identificador de cada categoría.

### <a name="to-sort-threads"></a>Para ordenar los subprocesos

1. En la barra de herramientas de la parte superior de la ventana **Subprocesos**, seleccione el botón situado en la parte superior de cualquier columna.

     Los subprocesos están ahora ordenados según los valores de esa columna.

2. Si quiere invertir el criterio de ordenación, vuelva a hacer clic en el mismo botón.

     Los subprocesos que aparecieron en la parte superior de la lista aparecen ahora en la parte inferior.

### <a name="to-group-threads"></a>Para agrupar subprocesos

- En la barra de herramientas de la ventana **Subprocesos**, seleccione la lista **Agrupar por** y después los criterios por los que quiere agrupar los subprocesos.

### <a name="to-sort-threads-within-groups"></a>Para ordenar los subprocesos dentro de los grupos

1. En la barra de herramientas de la parte superior de la ventana **Subprocesos**, seleccione la lista **Agrupar por** y después los criterios por los que quiera agrupar los subprocesos.

2. En la ventana **Subprocesos**, seleccione el botón situado en la parte superior de cualquier columna.

     Los subprocesos están ahora ordenados según los valores de esa columna.

### <a name="to-expand-or-collapse-all-groups"></a>Expandir o contraer todos los grupos

- En la barra de herramientas de la parte superior de la ventana **Subprocesos**, seleccione **Expandir grupos** o **Contraer grupos**.

## <a name="search-for-specific-threads"></a>Búsqueda de subprocesos concretos
 En la ventana **Subprocesos**, puede buscar subprocesos que coincidan con una cadena especificada. Cuando busque subprocesos, en la ventana se muestran todos los que coincidan con la cadena de búsqueda de cualquier columna. Esta información incluye la ubicación del subproceso que aparece en la parte superior de la pila de llamadas de la columna **Ubicación**. De forma predeterminada, no se busca en la pila de llamadas completa.

### <a name="to-search-for-specific-threads"></a>Para buscar subprocesos concretos

1. En la barra de herramientas de la parte superior de la ventana **Subprocesos**, vaya al cuadro **Buscar** y:

     - Escriba una cadena de búsqueda y, después, presione **Entrar**.

     \- o -

     - Seleccione la lista desplegable situada junto al cuadro **Buscar** y seleccione una cadena de búsqueda de una búsqueda anterior.

2. (Opcional) Para incluir la pila de llamadas completa en la búsqueda, seleccione **Buscar en pila de llamadas**.

## <a name="display-thread-call-stacks-and-switch-between-frames"></a>Representación de pilas de llamadas de subprocesos y cambio entre fotogramas
En un programa multiproceso, cada subproceso tiene su propia pila de llamadas. La ventana **Subprocesos** proporciona un medio cómodo para ver estas pilas.

> [!TIP]
> Para obtener una representación visual de la pila de llamadas de cada subproceso, use la ventana [Pilas paralelas](../debugger/get-started-debugging-multithreaded-apps.md).

### <a name="to-view-the-call-stack-of-a-thread"></a>Para ver la pila de llamadas de un subproceso

- En la columna **Ubicación**, seleccione el triángulo invertido situado junto a la ubicación del subproceso.

     La ubicación se expande para mostrar la pila de llamadas del subproceso.

### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Para ver o contraer las pilas de llamadas de todos los subprocesos

- En la barra de herramientas de la parte superior de la ventana **Subprocesos**, seleccione **Expandir pilas de llamadas** o **Contraer pilas de llamadas**.

## <a name="see-also"></a>Vea también
- [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Introducción a la depuración de aplicaciones multiproceso](../debugger/get-started-debugging-multithreaded-apps.md)

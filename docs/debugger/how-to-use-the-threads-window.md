---
title: "C&#243;mo: Utilizar la ventana Subprocesos | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.threads"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "subprocesos [Visual Studio], depurar"
  - "Thread.Name (propiedad)"
  - "depurador, ventana Subprocesos"
  - "SetThreadName (función)"
  - "Ventana Subprocesos"
  - "@TIB"
  - "depurar [Visual Studio], subprocesos"
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
caps.latest.revision: 44
caps.handback.revision: 44
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Utilizar la ventana Subprocesos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Desde la ventana **Subprocesos**, puede examinar y trabajar con los subprocesos de la aplicación que esté depurando.  
  
 La ventana **Subprocesos** contiene una tabla donde cada fila representa un subproceso de la aplicación.  De forma predeterminada, la tabla hace una lista de todos los subprocesos, pero puede filtrar la lista para mostrar solo los que le interesan.  Cada columna contiene un tipo diferente de información.  También puede ocultar algunas columnas.  Si muestra todas las columnas, la siguiente información aparece de izquierda a derecha:  
  
-   La columna de marcas, donde puede marcar un subproceso al que desea prestar atención especial.  Para obtener más información sobre cómo marcar un subproceso, vea [Cómo: Marcar y quitar marcadores de subprocesos](../debugger/how-to-flag-and-unflag-threads.md).  
  
-   La columna del subproceso activo, donde una flecha amarilla indica un subproceso activo.  El contorno de una flecha indica el subproceso donde la ejecución interrumpió el depurador.  
  
-   La columna **Id.**, que contiene el número de identificación de cada subproceso.  
  
-   La columna **Identificador administrado**, que contiene los números de identificación administrados para los subprocesos administrados.  
  
-   La columna **Categoría**, que clasifica los subprocesos como subprocesos de interfaz de usuario, controladores de llamadas a procedimientos remotos o subprocesos de trabajo.  Una categoría especial identifica el subproceso principal de la aplicación.  
  
-   La columna **Nombre**, que identifica cada subproceso por su nombre, si lo tiene, o como \<Sin nombre\>.  
  
-   La columna **Ubicación**, que muestra dónde se está ejecutando el subproceso.  Puede expandir esta ubicación para mostrar la pila de llamadas completa del subproceso.  
  
-   La columna **Prioridad**, que muestra la prioridad que el sistema ha asignado a cada subproceso.  
  
-   La columna **Máscara de afinidad**, que es una columna avanzada que normalmente se oculta.  Esta columna muestra la máscara de afinidad del procesador para cada subproceso.  En un sistema multiprocesador, la máscara de afinidad determina los procesadores en los que se puede ejecutar un subproceso.  
  
-   La columna **Número de suspendidos**, que contiene el recuento de suspensión.  Este recuento determina si un subproceso se puede ejecutar.  Para obtener una explicación sobre el recuento de suspensión, vea la sección Inmovilizar y reanudar subprocesos más adelante en este tema.  
  
-   La columna **Nombre de proceso**, que contiene el proceso al que pertenece cada subproceso.  Esta columna puede ser útil cuando está depurando varios procesos, pero normalmente se oculta.  
  
### Para mostrar la ventana Subprocesos en modo de interrupción o modo de ejecución  
  
-   En el menú **Depurar**, elija **Ventanas** y, a continuación, haga clic en **Subprocesos**.  
  
### Mostrar u ocultar columnas  
  
-   En la barra de herramientas situada en la parte superior de la ventana **Subprocesos**, haga clic en **Columnas** y, a continuación, seleccione el nombre de la columna que desee mostrar u ocultar.  
  
### Para cambiar el subproceso activo  
  
-   Realice uno de estos pasos:  
  
    -   Haga doble clic en un subproceso cualquiera.  
  
    -   Haga clic con el botón secundario en otro subproceso y, a continuación, haga clic en **Cambiar a subproceso**.  
  
         La flecha amarilla aparece al lado del nuevo subproceso activo.  El contorno deshabilitado de una flecha identifica el subproceso donde la ejecución interrumpió el depurador.  
  
## Agrupar y ordenar subprocesos  
 Al agrupar los subprocesos, aparece un encabezado en la tabla para cada grupo.  El encabezado contiene una descripción de grupo, como "Subproceso de trabajadores" o "Subprocesos sin marcar" y un control de árbol.  Los subprocesos de los miembros de cada de grupo aparecen bajo el título del grupo.  Si desea ocultar los subprocesos de los miembros de un grupo, puede utilizar el control de árbol para contraer el grupo.  
  
 Dado que la agrupación tiene prioridad sobre la ordenación, puede agrupar los subprocesos por categoría, por ejemplo, y, a continuación, ordenarlos por el identificador de cada categoría.  
  
#### Para ordenar los subprocesos  
  
1.  En la barra de herramientas de la ventana **Subprocesos**, haga clic en el botón situado en la parte superior de cualquier columna.  
  
     Los subprocesos están ahora ordenados según los valores de esa columna.  
  
2.  Si desea invertir el criterio de ordenación, haga clic de nuevo en el mismo botón.  
  
     Los subprocesos que aparecieron en la parte superior de la lista aparecen ahora en la parte inferior.  
  
#### Para agrupar subprocesos  
  
-   En la barra de herramientas de la ventana **Subprocesos**, haga clic en la lista **Agrupar por** y, a continuación, haga clic en los criterios por los que desea agrupar los subprocesos.  
  
#### Para ordenar los subprocesos dentro de los grupos  
  
1.  En la barra de herramientas de la parte superior de la ventana **Subprocesos**, haga clic en la lista **Agrupar por**, a continuación, haga clic en los criterios por los que desea agrupar los subprocesos.  
  
2.  En la ventana **Subprocesos**, haga clic en el botón situado en la parte superior de cualquier columna.  
  
     Los subprocesos están ahora ordenados según los valores de esa columna.  
  
#### Expandir o contraer todos los grupos  
  
-   En la barra de herramientas de la parte superior de la ventana **Subprocesos**, haga clic en **Expandir grupos** o en **Contraer grupos**.  
  
## Buscar Subprocesos concretos  
 En [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], puede buscar subprocesos que coincidan con una cadena especificada.  Cuando busque subprocesos en la ventana **Subprocesos**, se mostrarán todos los subprocesos que coincidan con la cadena de búsqueda de cualquier columna.  Esa información incluye la ubicación del subproceso que aparece en la parte superior de la pila de llamadas de la columna **Ubicación**.  Sin embargo, no se busca en la pila de llamadas completa de forma predeterminada.  
  
#### Para buscar subprocesos concretos  
  
-   En la barra de herramientas de la parte superior de la ventana **Subprocesos**, vaya al cuadro **Buscar** y:  
  
    -   Escriba una cadena de búsqueda y, a continuación, presione ENTRAR.  
  
         \-O bien\-  
  
    -   Haga clic en la lista desplegable situada junto al cuadro **Buscar** y seleccione una cadena de búsqueda de una búsqueda anterior.  
  
-   \(Opcional\) para incluir la pila de llamadas completa en la búsqueda, seleccione **Buscar en pila de llamadas**.  
  
## Inmovilizar y reanudar subprocesos  
 Cuando se inmoviliza un subproceso, el sistema no iniciará su ejecución aunque haya recursos disponibles.  
  
 En código nativo, los subprocesos se pueden suspender o reanudar llamando a las funciones de Windows `SuspendThread` y `ResumeThread` o a las funciones de MFC [CWinThread::SuspendThread](../Topic/CWinThread::SuspendThread.md) y [CWinThread::ResumeThread](../Topic/CWinThread::ResumeThread.md).  Si llama a `SuspendThread` o `ResumeThread`, cambia el *recuento de suspendidos*, que aparece en la ventana **Subprocesos**.  Sin embargo, si inmoviliza o reanuda un subproceso nativo, no cambia el recuento de suspendidos.  En código nativo, un subproceso no se puede ejecutar a menos que se reanude y tenga un recuento de suspensión de cero.  
  
 En código administrado, la inmovilización o la reanudación de un subproceso no cambia el recuento de suspensión.  En código administrado, un subproceso inmovilizado tiene un recuento de suspensión de 1.  En código nativo, un subproceso inmovilizado tiene un recuento de suspensión de 0, a menos que el subproceso se haya suspendido con una llamada a `SuspendThread`.  
  
> [!NOTE]
>  Cuando se depura una llamada de código nativo a código administrado, el código administrado se ejecuta en el mismo subproceso físico que el código nativo que lo llama.  La suspensión o la inmovilización del subproceso nativo inmoviliza también el código administrado.  
  
#### Para inmovilizar o reanudar la ejecución de un subproceso  
  
-   En la barra de herramientas de la parte superior de la ventana **Subprocesos**, haga clic en **Inmovilizar subprocesos** o **Reanudar subprocesos**.  
  
     Esta acción solo afecta a los subprocesos que están seleccionados en la ventana **Subprocesos**.  
  
## Mostrar los subprocesos marcados  
 Puede marcar un subproceso al que desea prestar atención especial con un icono en la ventana **Subprocesos**.  Para obtener más información, vea [Cómo: Marcar y quitar marcadores de subprocesos](../debugger/how-to-flag-and-unflag-threads.md).  En la ventana Subprocesos puede decidir si desea mostrar todos los subprocesos o solo los subprocesos marcados.  
  
#### Para mostrar solo los subprocesos marcados  
  
-   Elija el botón de marcador en la esquina superior izquierda de la ventana **Subprocesos**.  
  
## Mostrar pilas de llamadas de subprocesos y cambiar entre marcos  
 En un programa multiproceso, cada subproceso tiene su propia pila de llamadas.  La ventana **Subprocesos** proporciona un medio cómodo para ver estas pilas de llamadas.  
  
#### Para ver la pila de llamadas de un subproceso  
  
-   En la columna **Ubicación**, haga clic en el triángulo invertido situado junto a la ubicación del subproceso.  
  
     La ubicación se expande para mostrar la pila de llamadas del subproceso.  
  
#### Para ver o contraer las pilas de llamadas de todos los subprocesos  
  
-   En la barra de herramientas de la parte superior de la ventana **Subprocesos**, haga clic en **Expandir pilas de llamadas** o **Contraer pilas de llamadas**.  
  
## Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Tutorial: Depurar una aplicación multiproceso](../debugger/walkthrough-debugging-a-multithreaded-application.md)
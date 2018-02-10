---
title: "Asignar métodos en la pila de llamadas durante la depuración en Visual Studio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-modeling
ms.topic: get-started-article
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- call stacks, code maps
- Call Stack window, mapping calls
- debugging [Visual Studio], diagramming the call stack
- call stacks, mapping
- Call Stack window, visualizing
- debugging code visually
- debugging [Visual Studio], mapping the call stack
- call stacks, visualizing
- debugging, code maps
- Call Stack window, tracing calls visually
- Call Stack window, show on code map
- debugging [Visual Studio], tracing the call stack visually
- debugging [Visual Studio], visualizing the call stack
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 86ecdd628515376c057abfdf8b545e8686b3d25d
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Asignar métodos en la pila de llamadas durante la depuración en Visual Studio
Cree un mapa de código para realizar un seguimiento la pila de llamadas durante la depuración. Puede hacer anotaciones en el mapa para llevar a cabo el seguimiento de lo que hace el código y poder concentrarse en encontrar errores.  
  
 ![Depuración con pilas de llamadas en mapas de código](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")  
  
 Necesitará:  
  
-   [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)  
  
-   Código que pueda Depurar, por ejemplo, Visual C#, Visual Basic, C++, JavaScript o X ++.  
  
 Vea:  
  
-   [Vídeo: Depurar visualmente con la integración de depurador de mapa de código (Channel 9)](http://go.microsoft.com/fwlink/?LinkId=293418)
  
-   [Asignar la pila de llamadas](#MapStack)
  
-   [Hacer notas sobre el código](#MakeNotes)
  
-   [Actualizar el mapa con la siguiente pila de llamadas](#UpdateMap)
  
-   [Agregar código relacionado al mapa](#AddRelatedCode)
  
-   [Buscar errores usando el mapa](#FindBugs)
  
-   [PREGUNTAS Y RESPUESTAS](#QA)  
  
 Para obtener información detallada de los comandos y las acciones que puede utilizar cuando se trabaja con mapas de código, vea [examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md).  
  
##  <a name="MapStack"></a>Asignar la pila de llamadas  
  
1.  Inicie la depuración. (Teclado: **F5**)  
  
2.  Cuando la aplicación entra en modo de interrupción o entre en una función, elija **mapa de código**. (Teclado: **Ctrl** + **MAYÚS** + **`**)  
  
     ![Elegir mapa de código para iniciar la pila de llamadas de asignación](../debugger/media/debuggermap_choosecodemap.png "DebuggerMap_ChooseCodeMap")  
  
     La pila de llamadas actual aparece en naranja en un nuevo mapa de código:  
  
     ![Ver pila de llamadas en mapa de código](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")  
  
     El mapa se actualiza automáticamente a la vez que continúa depurando. Vea [actualizar el mapa con la siguiente pila de llamadas](#UpdateMap).  
  
##  <a name="MakeNotes"></a>Hacer notas sobre el código  
 Agregar comentarios para realizar un seguimiento de lo que está sucediendo en el código. Para agregar una nueva línea en un comentario, presione **MAYÚS + ENTRAR**.  
  
 ![Agregar comentario a la pila de llamadas en mapa de código](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")  
  
##  <a name="UpdateMap"></a>Actualizar el mapa con la siguiente pila de llamadas  
 Ejecute la aplicación hasta el siguiente punto de interrupción o entre en una función. El mapa agrega una nueva pila de llamadas.  
  
 ![Actualizar el mapa de código con la siguiente pila de llamadas](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")  
  
##  <a name="AddRelatedCode"></a>Agregar código relacionado al mapa  
 ¿Ahora ya tiene un mapa: lo que a continuación? Si está trabajando con C# o Visual Basic, agregue elementos, como campos, propiedades y otros métodos, para realizar un seguimiento de lo que está sucediendo en el código.  
  
 Haga doble clic en un método para ver su definición de código, o bien use el menú contextual para el método. (Teclado: seleccione el método en el mapa y presione **F12**)  
  
 ![Vaya a la definición de código de un método en el mapa de código](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")  
  
 Agregue los elementos de los que desee realizar el seguimiento al mapa.  
  
 ![Mostrar campos en un método en el mapa de código de pila de llamadas](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")  
  
> [!NOTE]
>  De forma predeterminada, al agregar elementos al mapa también se agregan nodos del grupo primario, como clase, espacio de nombres y ensamblado. Aunque esto es útil, puede simplificar el mapa si desactiva esta característica mediante el **incluir elementos primarios** botón en la barra de herramientas del mapa, o bien presionando **CTRL** cuando se agregan elementos.  
  
 ![Campos relacionados con un método en el mapa de código de pila de llamadas](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")  
  
 Aquí puede ver fácilmente los métodos que utilizan los mismos campos. Los elementos agregados más recientemente aparecen en verde.  
  
 Continúe con la compilación del mapa para ver más código.  
  
 ![Ver métodos que usan un campo: mapa de código de pila de llamadas](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")  
  
 ![Métodos que usan un campo en el mapa de código de pila de llamadas](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")  
  
##  <a name="FindBugs"></a>Buscar errores usando el mapa  
 La visualización del código puede ayudarle a encontrar errores con mayor rapidez. Por ejemplo, suponga que se está investigando un error en un programa de dibujo. Cuando dibuja una línea e intenta deshacerla, no sucede nada hasta que dibuja otra línea.  
  
 Por tanto, establece los puntos de interrupción en los métodos  `clear`, `undo` y `Repaint`, inicia la depuración y compila un mapa como este:  
  
 ![Agregar otra pila de llamadas al mapa de código](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")  
  
 Observe que todos los gestos de usuario en el mapa llaman a `Repaint`, salvo `undo`. Esto podría explicar por qué `undo` no funciona inmediatamente.  
  
 Tras corregir el error y seguir ejecutando el programa, el mapa agrega la nueva llamada de `undo` a `Repaint`:  
  
 ![Agregar nuevo método a la llamada a otra pila en el mapa de código](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")  
  
##  <a name="QA"></a> Preguntas y respuestas  
  
-   **No todas las llamadas aparecen en el mapa. ¿Por qué?**  
  
     De forma predeterminada, en el mapa solo se muestra su código. Para ver el código externo, actívelo en la **pila de llamadas** ventana:  
  
     ![Mostrar código externo mediante la ventana Pila de llamadas](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")  
  
     o desactive la opción **habilitar solo mi código** en las opciones de depuración de Visual Studio:  
  
     ![Mostrar código externo mediante el cuadro de diálogo Opciones](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")  
  
-   **¿Cambiar el mapa afecta el código?**  
  
     Cambiar el mapa no afecta al código de ninguna manera. No dude en cambiar el nombre, mover o quitar contenido del mapa.  
  
-   **¿Qué significa este mensaje: "el diagrama se puede basar en una versión anterior del código"?**  
  
     El código podría haber cambiado después de la última actualización del mapa. Por ejemplo, una llamada en el mapa tal vez ya no exista en el código. Cierre el mensaje y, a continuación, intente volver a compilar la solución antes de actualizar el mapa de nuevo.  
  
-   **¿Cómo se puede controlar el diseño del mapa?**  
  
     Abra la **diseño** menú en la barra de herramientas de asignación:  
  
    -   Cambie el diseño predeterminado.  
  
    -   Para dejar de reorganizar el mapa automáticamente, desactive la opción **diseñar automáticamente al depurar**.  
  
    -   Para reorganizar el mapa lo mínimo posible cuando se agregan elementos, desactive la opción **diseño Incremental**.  
  
-   **¿Puedo compartir el mapa con otros usuarios?**  
  
     Puede exportar el mapa, enviarlo a otros usuarios si tiene Microsoft Outlook o guardarlo en la solución para protegerlo en el control de versiones de Team Foundation.  
  
     ![Compartir el mapa de código de pila de llamadas con otros](../debugger/media/debuggermap_sharewithothers.png "DebuggerMap_ShareWithOthers")  
  
-   **¿Cómo se impide la asignación de agregar automáticamente nuevas pilas de llamadas?**  
  
     Elija ![botón &#45; Mostrar pila de llamadas en mapa de código automáticamente](../debugger/media/debuggermap_automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") en la barra de herramientas del mapa. Para agregar manualmente la pila de llamadas actual al mapa, presione **Ctrl** + **MAYÚS** + **`**.  
  
     El mapa continuará resaltando las pilas de llamadas existentes en el mapa durante la depuración.  
  
-   **¿Qué los iconos de los elementos y las flechas significan?**  
  
     Para obtener más información sobre un elemento, mueva el puntero del mouse sobre él y buscar información sobre herramientas del elemento. También puede mirar el **leyenda** para obtener información sobre lo que significa cada icono.  
  
     ![¿Qué significan los iconos en el mapa de código de la pila de llamadas? ] (../debugger/media/debuggermap_showlegend.png "DebuggerMap_ShowLegend")  
  
 Vea:  
  
-   [Asignar la pila de llamadas](#MapStack)
  
-   [Hacer notas sobre el código](#MakeNotes)
  
-   [Actualizar el mapa con la siguiente pila de llamadas](#UpdateMap)
  
-   [Agregar código relacionado al mapa](#AddRelatedCode)
  
-   [Buscar errores usando el mapa](#FindBugs)  
  
## <a name="see-also"></a>Vea también  
 [Asignar dependencias en sus soluciones](../modeling/map-dependencies-across-your-solutions.md)   
 [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)   
 [Examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md)
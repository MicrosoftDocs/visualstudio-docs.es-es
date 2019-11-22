---
title: Asignar métodos en la pila de llamadas durante la depuración
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
ms.assetid: d6a72e5e-f88d-46fc-94a3-1789d34805ef
caps.latest.revision: 43
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3ddf45a48f6b9d8a5ac8155012f168703c67aa3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300789"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Asignar métodos en la pila de llamadas durante la depuración en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cree un mapa de código para hacer un seguimiento visual de la pila de llamadas durante la depuración. Puede hacer anotaciones en el mapa para llevar a cabo el seguimiento de lo que hace el código y poder concentrarse en encontrar errores.

 ![Debugging with call stacks on code maps](../debugger/media/debuggermap-overview.png "DebuggerMap_Overview")

 Necesitará:

- [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)

- Código que pueda depurar, por ejemplo, Visual C# .NET, Visual Basic .NET, C++, JavaScript o X++.

  See: [Video: Debug visually with Code Map debugger integration (Channel 9)](https://go.microsoft.com/fwlink/?LinkId=293418) • [Map the call stack](#MapStack) • [Make notes about the code](#MakeNotes) • [Update the map with the next call stack](#UpdateMap) • [Add related code to the map](#AddRelatedCode) • [Find bugs using the map](#FindBugs) • [Q & A](#QA)

  For details of the commands and actions you can use when working with code maps, see [Browse and rearrange code maps](../modeling/browse-and-rearrange-code-maps.md).

## <a name="MapStack"></a> Asignar la pila de llamadas

1. Inicie la depuración. (Keyboard: **F5**)

2. After your app enters break mode or you step into a function, choose **Code Map**. (Keyboard: **Ctrl** + **Shift** +  **`** )

     ![Choose Code Map to start mapping call stack](../debugger/media/debuggermap-choosecodemap.png "DebuggerMap_ChooseCodeMap")

     La pila de llamadas actual aparece en naranja en un nuevo mapa de código:

     ![See call stack on code map](../debugger/media/debuggermap-seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

     El mapa se actualiza automáticamente a la vez que continúa depurando. See [Update the map with the next call stack](#UpdateMap).

## <a name="MakeNotes"></a> Hacer notas sobre el código
 Agregue comentarios para el hacer seguimiento de lo que pasa en el código. To add a new line in a comment, press **Shift + Return**.

 ![Add comment to call stack on code map](../debugger/media/debuggermap-addcomment.png "DebuggerMap_AddComment")

## <a name="UpdateMap"></a> Actualizar el mapa con la siguiente pila de llamadas
 Ejecute la aplicación hasta el siguiente punto de interrupción o entre en una función. El mapa agrega una nueva pila de llamadas.

 ![Update code map with next call stack](../debugger/media/debuggermap-addclearcallstack.png "DebuggerMap_AddClearCallStack")

## <a name="AddRelatedCode"></a> Agregar código relacionado al mapa
 Ahora ya tiene un mapa, ¿qué viene después? Si trabaja con Visual C# .NET o Visual Basic .NET, agregue elementos, como campos, propiedades y otros métodos, para hacer el seguimiento de lo que pasa en el código.

 Haga doble clic en un método para ver su definición de código, o bien use el menú contextual para el método. (Keyboard: Select the method on the map and press **F12**)

 ![Go to code definition for a method on code map](../debugger/media/debuggermap-gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

 Agregue los elementos de los que desee realizar el seguimiento al mapa.

 ![Show fields in a method on call stack code map](../debugger/media/debuggermap-showfields.png "DebuggerMap_ShowFields")

> [!NOTE]
> De forma predeterminada, al agregar elementos al mapa también se agregan nodos del grupo primario, como clase, espacio de nombres y ensamblado. While this is useful, you can keep the map simple by turning off this feature using the **Include Parents** button on the map toolbar, or by pressing **CTRL** when you add items.

 ![Fields related to a method on call stack code map](../debugger/media/debuggermap-showedfields.png "DebuggerMap_ShowedFields")

 Aquí puede ver fácilmente los métodos que utilizan los mismos campos. Los elementos agregados más recientemente aparecen en verde.

 Continúe con la compilación del mapa para ver más código.

 ![See methods that use a field: call stack code map](../debugger/media/debuggermap-findallreferences.png "DebuggerMap_FindAllReferences")

 ![Methods that use a field on call stack code map](../debugger/media/debuggermap-foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="FindBugs"></a> Buscar errores usando el mapa
 La visualización del código puede ayudarle a encontrar errores con mayor rapidez. Por ejemplo, suponga que está investigando un error en un programa de dibujo. Cuando dibuja una línea e intenta deshacerla, no sucede nada hasta que dibuja otra línea.

 Por tanto, establece los puntos de interrupción en los métodos  `clear`, `undo` y `Repaint`, inicia la depuración y compila un mapa como este:

 ![Add another call stack to code map](../debugger/media/debuggermap-addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Observe que todos los gestos de usuario en el mapa llaman a `Repaint`, salvo `undo`. Esto podría explicar por qué `undo` no funciona inmediatamente.

 Tras corregir el error y seguir ejecutando el programa, el mapa agrega la nueva llamada de `undo` a `Repaint`:

 ![Add new method call to call stack on code map](../debugger/media/debuggermap-addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="QA"></a> Preguntas y respuestas

- **Not all calls appear on the map. Why?**

   De forma predeterminada, en el mapa solo se muestra su código. To see external code, turn it on in the **Call Stack** window:

   ![Display external code using the Call Stack window](../debugger/media/debuggermap-callstackmenu.png "DebuggerMap_CallStackMenu")

   or turn off **Enable Just My Code** in the Visual Studio debugging options:

   ![Show external code using Options dialog](../debugger/media/debuggermap-debugoptions.png "DebuggerMap_DebugOptions")

- **Does changing the map affect the code?**

   Cambiar el mapa no afecta al código en forma alguna. No dude en cambiar el nombre, mover o quitar contenido del mapa.

- **What does this message mean: “The diagram may be based on an older version of the code”?**

   El código podría haber cambiado después de la última actualización del mapa. Por ejemplo, una llamada en el mapa tal vez ya no exista en el código. Cierre el mensaje y, a continuación, intente volver a compilar la solución antes de actualizar el mapa de nuevo.

- **How do I control the map’s layout?**

   Open the **Layout** menu on the map toolbar:

  - Cambie el diseño predeterminado.

  - To stop rearranging the map automatically, turn off **Automatically Layout when Debugging**.

  - To rearrange the map as little as possible when you add items, turn off **Incremental Layout**.

- **Can I share the map with others?**

   Puede exportar el mapa, enviarlo a otros usuarios si tiene Microsoft Outlook o guardarlo en la solución para protegerlo en el control de versiones de Team Foundation.

   ![Share call stack code map with others](../debugger/media/debuggermap-sharewithothers.png "DebuggerMap_ShareWithOthers")

- **How do I stop the map from adding new call stacks automatically?**

   Choose ![Button &#45; Show call stack on code map automatically](../debugger/media/debuggermap-automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") on the map toolbar. To manually add the current call stack to the map, press **Ctrl** + **Shift** +  **`** .

   El mapa continuará resaltando las pilas de llamadas existentes mientras se está depurando.

- **What do the item icons and arrows mean?**

   Para obtener más información sobre un elemento, mueva el puntero del mouse sobre él y examine la información sobre herramientas del elemento. You can also look at the **Legend** to learn what each icon means.

   ![What do icons on the call stack code map mean?](../debugger/media/debuggermap-showlegend.png "DebuggerMap_ShowLegend")

  See: [Map the call stack](#MapStack) • [Make notes about the code](#MakeNotes) • [Update the map with the next call stack](#UpdateMap) • [Add related code to the map](#AddRelatedCode) • [Find bugs using the map](#FindBugs)

## <a name="see-also"></a>Vea también
 [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md) [Use code maps to debug your applications](../modeling/use-code-maps-to-debug-your-applications.md) [Find potential problems using code map analyzers](../modeling/find-potential-problems-using-code-map-analyzers.md) [Browse and rearrange code maps](../modeling/browse-and-rearrange-code-maps.md)

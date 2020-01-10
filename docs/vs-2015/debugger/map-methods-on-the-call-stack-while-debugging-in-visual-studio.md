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
ms.openlocfilehash: 2e8376884f72aeca2f3bf56f0d7bbc1636379a18
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75847309"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Asignar métodos en la pila de llamadas durante la depuración en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cree un mapa de código para hacer un seguimiento visual de la pila de llamadas durante la depuración. Puede hacer anotaciones en el mapa para llevar a cabo el seguimiento de lo que hace el código y poder concentrarse en encontrar errores.

 ![Depurar con pilas de llamadas en mapas de código](../debugger/media/debuggermap-overview.png "DebuggerMap_Overview")

 Necesitará:

- [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)

- Código que pueda depurar, por ejemplo, Visual C# .NET, Visual Basic .NET, C++, JavaScript o X++.

  Vea: [vídeo: depurar visualmente con la integración del depurador del mapa de código (Channel 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration) • [asignar la pila de llamadas](#MapStack) • [hacer notas sobre el código](#MakeNotes) • [actualizar el mapa con la siguiente pila de llamadas](#UpdateMap) • [Agregar código relacionado al mapa](#AddRelatedCode) • [buscar errores mediante el mapa](#FindBugs) • [Q & A](#QA)

  Para obtener detalles de los comandos y las acciones que puede utilizar cuando se trabaja con mapas de código, vea [examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md).

## <a name="MapStack"></a> Asignar la pila de llamadas

1. Inicie la depuración. (Teclado: **F5**)

2. Después de la aplicación entra en modo de interrupción o entra en una función, elija **mapa de código**. (Teclado: **Ctrl** + **MAYÚS** +  **`** )

     ![Elija el mapa de código para empezar a asignar la pila de llamadas](../debugger/media/debuggermap-choosecodemap.png "DebuggerMap_ChooseCodeMap")

     La pila de llamadas actual aparece en naranja en un nuevo mapa de código:

     ![Vea pila de llamadas en el mapa de código](../debugger/media/debuggermap-seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

     El mapa se actualiza automáticamente a la vez que continúa depurando. Consulte [actualizar el mapa con la siguiente pila de llamadas](#UpdateMap).

## <a name="MakeNotes"></a> Hacer notas sobre el código
 Agregue comentarios para el hacer seguimiento de lo que pasa en el código. Para agregar una nueva línea en un comentario, presione **MAYÚS + ENTRAR**.

 ![Agregar un comentario a la pila de llamadas en el mapa de código](../debugger/media/debuggermap-addcomment.png "DebuggerMap_AddComment")

## <a name="UpdateMap"></a> Actualizar el mapa con la siguiente pila de llamadas
 Ejecute la aplicación hasta el siguiente punto de interrupción o entre en una función. El mapa agrega una nueva pila de llamadas.

 ![Actualizar mapa de código con la siguiente pila de llamadas](../debugger/media/debuggermap-addclearcallstack.png "DebuggerMap_AddClearCallStack")

## <a name="AddRelatedCode"></a> Agregar código relacionado al mapa
 Ahora ya tiene un mapa, ¿qué viene después? Si trabaja con Visual C# .NET o Visual Basic .NET, agregue elementos, como campos, propiedades y otros métodos, para hacer el seguimiento de lo que pasa en el código.

 Haga doble clic en un método para ver su definición de código, o bien use el menú contextual para el método. (Teclado: seleccione el método en el mapa y presione **F12**)

 ![Ir a definición de código para un método en el mapa de código](../debugger/media/debuggermap-gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

 Agregue los elementos de los que desee realizar el seguimiento al mapa.

 ![Mostrar los campos de un método en el mapa de código de la pila de llamadas](../debugger/media/debuggermap-showfields.png "DebuggerMap_ShowFields")

> [!NOTE]
> De forma predeterminada, al agregar elementos al mapa también se agregan nodos del grupo primario, como clase, espacio de nombres y ensamblado. Aunque esto es útil, puede simplificar el mapa si desactiva esta característica mediante la **incluir elementos primarios** botón en la barra de herramientas del mapa, o bien presionar **CTRL** cuando se agregan elementos.

 ![Campos relacionados con un método en el mapa de código de la pila de llamadas](../debugger/media/debuggermap-showedfields.png "DebuggerMap_ShowedFields")

 Aquí puede ver fácilmente los métodos que utilizan los mismos campos. Los elementos agregados más recientemente aparecen en verde.

 Continúe con la compilación del mapa para ver más código.

 ![Vea los métodos que usan un campo: mapa de código de pila de llamadas](../debugger/media/debuggermap-findallreferences.png "DebuggerMap_FindAllReferences")

 ![Métodos que usan un campo en el mapa de código de la pila de llamadas](../debugger/media/debuggermap-foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="FindBugs"></a> Buscar errores usando el mapa
 La visualización del código puede ayudarle a encontrar errores con mayor rapidez. Por ejemplo, suponga que está investigando un error en un programa de dibujo. Cuando dibuja una línea e intenta deshacerla, no sucede nada hasta que dibuja otra línea.

 Por tanto, establece los puntos de interrupción en los métodos  `clear`, `undo` y `Repaint`, inicia la depuración y compila un mapa como este:

 ![Agregar otra pila de llamadas al mapa de código](../debugger/media/debuggermap-addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Observe que todos los gestos de usuario en el mapa llaman a `Repaint`, salvo `undo`. Esto podría explicar por qué `undo` no funciona inmediatamente.

 Tras corregir el error y seguir ejecutando el programa, el mapa agrega la nueva llamada de `undo` a `Repaint`:

 ![Agregar nueva llamada de método a la pila de llamadas en el mapa de código](../debugger/media/debuggermap-addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="QA"></a> Preguntas y respuestas

- **No todas las llamadas aparecen en el mapa. ¿Por qué?**

   De forma predeterminada, en el mapa solo se muestra su código. Para ver código externo, actívelo en el **pila de llamadas** ventana:

   ![Mostrar código externo mediante la ventana pila de llamadas](../debugger/media/debuggermap-callstackmenu.png "DebuggerMap_CallStackMenu")

   o desactivar **habilitar solo mi código** en Visual Studio, opciones de depuración:

   ![Cuadro de diálogo Mostrar código externo mediante opciones](../debugger/media/debuggermap-debugoptions.png "DebuggerMap_DebugOptions")

- **¿Cambiar el mapa afecta el código?**

   Cambiar el mapa no afecta al código en forma alguna. No dude en cambiar el nombre, mover o quitar contenido del mapa.

- **¿Qué significa este mensaje: "el diagrama se puede basar en una versión anterior del código"?**

   El código podría haber cambiado después de la última actualización del mapa. Por ejemplo, una llamada en el mapa tal vez ya no exista en el código. Cierre el mensaje y, a continuación, intente volver a compilar la solución antes de actualizar el mapa de nuevo.

- **Cómo controlar el diseño del mapa?**

   Abra el **diseño** menú en la barra de herramientas del mapa:

  - Cambie el diseño predeterminado.

  - Para detener reorganizar el mapa automáticamente, desactive la opción **diseñar automáticamente al depurar**.

  - Para reorganizar el mapa lo mínimo posible al agregar elementos, desactive la opción **diseño Incremental**.

- **¿Puedo compartir el mapa con otros usuarios?**

   Puede exportar el mapa, enviarlo a otros usuarios si tiene Microsoft Outlook o guardarlo en la solución para protegerlo en el control de versiones de Team Foundation.

   ![Compartir el mapa de código de la pila de llamadas con otros usuarios](../debugger/media/debuggermap-sharewithothers.png "DebuggerMap_ShareWithOthers")

- **¿Cómo se puede detener el mapa de agregar automáticamente nuevas pilas de llamadas?**

   Elija ![botón &#45; pila de llamadas Mostrar en mapa de código automáticamente](../debugger/media/debuggermap-automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") en la barra de herramientas del mapa. Para agregar manualmente la pila de llamadas actual al mapa, presione **Ctrl** + **MAYÚS** +  **`** .

   El mapa continuará resaltando las pilas de llamadas existentes mientras se está depurando.

- **¿Qué los iconos de los elementos y las flechas significan?**

   Para obtener más información sobre un elemento, mueva el puntero del mouse sobre él y examine la información sobre herramientas del elemento. También puede mirar el **leyenda** para obtener información sobre lo que significa cada icono.

   ![¿Qué significan los iconos del mapa de código de la pila de llamadas?](../debugger/media/debuggermap-showlegend.png "DebuggerMap_ShowLegend")

  Vea: [asignar la pila de llamadas](#MapStack) • [hacer notas sobre el código](#MakeNotes) • [actualizar el mapa con la siguiente pila de llamadas](#UpdateMap) • [Agregar código relacionado al mapa](#AddRelatedCode) • [buscar errores mediante la asignación](#FindBugs)

## <a name="see-also"></a>Vea también
 [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md) [usar mapas de código para depurar las aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md) [buscar posibles problemas mediante analizadores de mapa de código](../modeling/find-potential-problems-using-code-map-analyzers.md) [examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md)

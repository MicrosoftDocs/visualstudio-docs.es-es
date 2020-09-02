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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75847309"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Asignar métodos en la pila de llamadas durante la depuración en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cree un mapa de código para hacer un seguimiento visual de la pila de llamadas durante la depuración. Puede hacer anotaciones en el mapa para llevar a cabo el seguimiento de lo que hace el código y poder concentrarse en encontrar errores.

 ![Depuración con pilas de llamadas en los mapas de código](../debugger/media/debuggermap-overview.png "DebuggerMap_Overview")

 Necesitará:

- [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)

- Código que pueda depurar, por ejemplo, Visual C# .NET, Visual Basic .NET, C++, JavaScript o X++.

  Vea: [vídeo: depurar visualmente con la integración del depurador del mapa de código (Channel 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration) • [asignar la pila de llamadas](#MapStack) • [hacer notas sobre el código](#MakeNotes) • [actualizar el mapa con la siguiente pila de llamadas](#UpdateMap) • [Agregar código relacionado al mapa](#AddRelatedCode) • [buscar errores mediante el mapa](#FindBugs) • [Q & A](#QA)

  Para obtener detalles de los comandos y las acciones que se pueden usar al trabajar con mapas de código, vea [examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md).

## <a name="map-the-call-stack"></a><a name="MapStack"></a> Asignar la pila de llamadas

1. Inicie la depuración. (Teclado: **F5**)

2. Después de que la aplicación entre en modo de interrupción o entre en una función, elija **mapa de código**. (Teclado: **Ctrl**  +  **Shift**  +  **`** )

     ![Elegir Mapa de código para empezar a asignar la pila de llamadas](../debugger/media/debuggermap-choosecodemap.png "DebuggerMap_ChooseCodeMap")

     La pila de llamadas actual aparece en naranja en un nuevo mapa de código:

     ![Ver pila de llamadas en el mapa de código](../debugger/media/debuggermap-seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

     El mapa se actualiza automáticamente a la vez que continúa depurando. Vea [actualizar el mapa con la siguiente pila de llamadas](#UpdateMap).

## <a name="make-notes-about-the-code"></a><a name="MakeNotes"></a> Hacer notas sobre el código
 Agregue comentarios para el hacer seguimiento de lo que pasa en el código. Para agregar una nueva línea a un comentario, presione **MAYÚS + entrar**.

 ![Agregar comentario a la pila de llamadas en el mapa de código](../debugger/media/debuggermap-addcomment.png "DebuggerMap_AddComment")

## <a name="update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a> Actualizar el mapa con la siguiente pila de llamadas
 Ejecute la aplicación hasta el siguiente punto de interrupción o entre en una función. El mapa agrega una nueva pila de llamadas.

 ![Actualizar mapa de código con la siguiente pila de llamadas](../debugger/media/debuggermap-addclearcallstack.png "DebuggerMap_AddClearCallStack")

## <a name="add-related-code-to-the-map"></a><a name="AddRelatedCode"></a> Agregar código relacionado al mapa
 Ahora ya tiene un mapa, ¿qué viene después? Si trabaja con Visual C# .NET o Visual Basic .NET, agregue elementos, como campos, propiedades y otros métodos, para hacer el seguimiento de lo que pasa en el código.

 Haga doble clic en un método para ver su definición de código, o bien use el menú contextual para el método. (Teclado: seleccione el método en el mapa y presione **F12**).

 ![Ir a la definición de código de un método en el mapa de código](../debugger/media/debuggermap-gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

 Agregue los elementos de los que desee realizar el seguimiento al mapa.

 ![Mostrar campos en un método en el mapa de código de la pila de llamadas](../debugger/media/debuggermap-showfields.png "DebuggerMap_ShowFields")

> [!NOTE]
> De forma predeterminada, al agregar elementos al mapa también se agregan nodos del grupo primario, como clase, espacio de nombres y ensamblado. Aunque esto es útil, puede mantener el mapa sencillo desactivando esta característica con el botón **incluir elementos primarios** de la barra de herramientas del mapa, o presionando **Ctrl** mientras agrega elementos.

 ![Campos relacionados con un método en el mapa de código de la pila de llamadas](../debugger/media/debuggermap-showedfields.png "DebuggerMap_ShowedFields")

 Aquí puede ver fácilmente los métodos que utilizan los mismos campos. Los elementos agregados más recientemente aparecen en verde.

 Continúe con la compilación del mapa para ver más código.

 ![Ver métodos que usan un campo: mapa de código de la pila de llamadas](../debugger/media/debuggermap-findallreferences.png "DebuggerMap_FindAllReferences")

 ![Métodos que usan un campo en el mapa de código de la pila de llamadas](../debugger/media/debuggermap-foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="find-bugs-using-the-map"></a><a name="FindBugs"></a> Buscar errores usando el mapa
 La visualización del código puede ayudarle a encontrar errores con mayor rapidez. Por ejemplo, suponga que está investigando un error en un programa de dibujo. Cuando dibuja una línea e intenta deshacerla, no sucede nada hasta que dibuja otra línea.

 Por tanto, establece los puntos de interrupción en los métodos  `clear`, `undo` y `Repaint`, inicia la depuración y compila un mapa como este:

 ![Agregar otra pila de llamadas al mapa de código](../debugger/media/debuggermap-addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Observe que todos los gestos de usuario en el mapa llaman a `Repaint`, salvo `undo`. Esto podría explicar por qué `undo` no funciona inmediatamente.

 Tras corregir el error y seguir ejecutando el programa, el mapa agrega la nueva llamada de `undo` a `Repaint`:

 ![Agregar llamada a un nuevo método a la pila de llamadas en el mapa de código](../debugger/media/debuggermap-addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="q--a"></a><a name="QA"></a> Preguntas y respuestas

- **No todas las llamadas aparecen en el mapa. ¿Por qué?**

   De forma predeterminada, en el mapa solo se muestra su código. Para ver el código externo, actívelo en la ventana **pila de llamadas** :

   ![Mostrar código externo mediante la ventana Pila de llamadas](../debugger/media/debuggermap-callstackmenu.png "DebuggerMap_CallStackMenu")

   o bien, desactive **habilitar solo mi código** en las opciones de depuración de Visual Studio:

   ![Mostrar código externo mediante el cuadro de diálogo Opciones](../debugger/media/debuggermap-debugoptions.png "DebuggerMap_DebugOptions")

- **¿Afecta el cambio del mapa al código?**

   Cambiar el mapa no afecta al código en forma alguna. No dude en cambiar el nombre, mover o quitar contenido del mapa.

- **¿Qué significa este mensaje: “El diagrama se puede basar en una versión anterior del código”?**

   El código podría haber cambiado después de la última actualización del mapa. Por ejemplo, una llamada en el mapa tal vez ya no exista en el código. Cierre el mensaje y, a continuación, intente volver a compilar la solución antes de actualizar el mapa de nuevo.

- **¿Cómo puedo controlar el diseño del mapa?**

   Abra el menú **diseño** en la barra de herramientas del mapa:

  - Cambie el diseño predeterminado.

  - Para dejar de reorganizar el mapa automáticamente, desactive la opción **diseñar automáticamente al depurar**.

  - Para reorganizar el mapa lo más bajo posible al agregar elementos, desactive el **diseño incremental**.

- **¿Es posible compartir el mapa con otros usuarios?**

   Puede exportar el mapa, enviarlo a otros usuarios si tiene Microsoft Outlook o guardarlo en la solución para protegerlo en el control de versiones de Team Foundation.

   ![Compartir el mapa de código de la pila de llamadas con otros usuarios](../debugger/media/debuggermap-sharewithothers.png "DebuggerMap_ShareWithOthers")

- **¿Cómo se detiene la agregación automática de nuevas pilas de llamadas al mapa?**

   Elija el ![botón &#45; Mostrar pila de llamadas en el mapa de código automáticamente](../debugger/media/debuggermap-automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") en la barra de herramientas del mapa. Para agregar manualmente la pila de llamadas actual al mapa, presione **Ctrl** + **Mayús** +  **`** .

   El mapa continuará resaltando las pilas de llamadas existentes mientras se está depurando.

- **¿Qué significan los iconos y las flechas de los elementos?**

   Para obtener más información sobre un elemento, mueva el puntero del mouse sobre él y examine la información sobre herramientas del elemento. También puede mirar la **leyenda** para saber lo que significa cada icono.

   ![¿Qué significan los iconos del mapa de código de la pila de llamadas?](../debugger/media/debuggermap-showlegend.png "DebuggerMap_ShowLegend")

  Vea: [asignar la pila de llamadas](#MapStack) • [hacer notas sobre el código](#MakeNotes) • [actualizar el mapa con la siguiente pila de llamadas](#UpdateMap) • [Agregar código relacionado al mapa](#AddRelatedCode) • [buscar errores mediante la asignación](#FindBugs)

## <a name="see-also"></a>Consulte también
 [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md) [usar mapas de código para depurar las aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md) [buscar posibles problemas mediante analizadores de mapa de código](../modeling/find-potential-problems-using-code-map-analyzers.md) [examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md)

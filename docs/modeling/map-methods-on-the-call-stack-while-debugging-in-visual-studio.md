---
title: Asignar métodos en la pila de llamadas durante la depuración
description: Obtenga información sobre cómo crear un mapa de código para hacer un seguimiento visual de la pila de llamadas durante la depuración. Además, aprenda que puede tomar notas en el mapa para realizar un seguimiento de lo que hace el código.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 08fa0ff028140ebad421dd43fdfa53cc36b77804
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387494"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Asignar métodos en la pila de llamadas durante la depuración en Visual Studio

Cree un mapa de código para hacer un seguimiento visual de la pila de llamadas durante la depuración. Puede hacer anotaciones en el mapa para llevar a cabo el seguimiento de lo que hace el código y poder concentrarse en encontrar errores.

 ![Depuración con pilas de llamadas en los mapas de código](../debugger/media/debuggermap_overview.png)

 Necesitará lo siguiente:

 ::: moniker range="vs-2017"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

::: moniker-end

::: moniker range=">=vs-2019"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/downloads)

::: moniker-end

- Código que puede depurar, como Visual C#, Visual Basic, C++, JavaScript o X++

  Vea:

- [Vídeo: Depuración visual con la integración del depurador de Mapa de código (Channel 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration)

- [Asignación de la pila de llamadas](#MapStack)

- [Tomar notas sobre el código](#MakeNotes)

- [Actualización del mapa con la siguiente pila de llamadas](#UpdateMap)

- [Adición de código relacionado al mapa](#AddRelatedCode)

- [Buscar errores mediante el mapa](#FindBugs)

- [PREGUNTAS Y RESPUESTAS](#QA)

  Para obtener más información sobre los comandos y las acciones que puede usar al trabajar con mapas de código, vea Examinar y [reorganizar mapas de código.](../modeling/browse-and-rearrange-code-maps.md)

## <a name="map-the-call-stack"></a><a name="MapStack"></a> Asignar la pila de llamadas

1. Inicie la depuración. (Teclado: **F5**)

2. Después de que la aplicación entre en modo de interrupción o de que entre en una función, elija **Mapa de código**. (Teclado: **Ctrl**  +  **Mayús**  +  **`** )

     ![Elegir Mapa de código para empezar a asignar la pila de llamadas](../debugger/media/debuggermap_choosecodemap.png)

     La pila de llamadas actual aparece en naranja en un nuevo mapa de código:

     ![Ver pila de llamadas en el mapa de código](../debugger/media/debuggermap_seeundocallstack.png)

     El mapa se actualiza automáticamente a la vez que continúa depurando. Consulte [Actualización del mapa con la siguiente pila de llamadas.](#UpdateMap)

## <a name="make-notes-about-the-code"></a><a name="MakeNotes"></a> Hacer notas sobre el código

 Agregue comentarios para realizar un seguimiento de lo que sucede en el código. Para agregar una nueva línea en un comentario, presione **Mayús + Devolver**.

 ![Agregar comentario a la pila de llamadas en el mapa de código](../debugger/media/debuggermap_addcomment.png)

## <a name="update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a> Actualizar el mapa con la siguiente pila de llamadas

 Ejecute la aplicación hasta el siguiente punto de interrupción o entre en una función. El mapa agrega una nueva pila de llamadas.

 ![Actualizar mapa de código con la siguiente pila de llamadas](../debugger/media/debuggermap_addclearcallstack.png)

## <a name="add-related-code-to-the-map"></a><a name="AddRelatedCode"></a> Agregar código relacionado al mapa

 Ahora tiene un mapa, ¿qué siguiente? Si está trabajando con C# o Visual Basic, agregue elementos, como campos, propiedades y otros métodos, para realizar un seguimiento de lo que sucede en el código.

 Haga doble clic en un método para ver su definición de código, o bien use el menú contextual para el método. (Teclado: seleccione el método en el mapa y presione **F12**)

 ![Ir a la definición de código de un método en el mapa de código](../debugger/media/debuggermap_gotocodedefinition.png)

 Agregue los elementos de los que desee realizar el seguimiento al mapa.

 ![Mostrar campos en un método en el mapa de código de la pila de llamadas](../debugger/media/debuggermap_showfields.png)

> [!NOTE]
> De forma predeterminada, al agregar elementos al mapa también se agregan nodos del grupo primario, como clase, espacio de nombres y ensamblado. Aunque esto es útil, puede mantener el mapa simple  desactivando esta característica mediante el botón Incluir elementos elementos principal de la barra de herramientas del mapa o presionando **CTRL** al agregar elementos.

 ![Campos relacionados con un método en el mapa de código de la pila de llamadas](../debugger/media/debuggermap_showedfields.png)

 Aquí puede ver fácilmente los métodos que utilizan los mismos campos. Los elementos agregados más recientemente aparecen en verde.

 Continúe con la compilación del mapa para ver más código.

 ![Ver métodos que usan un campo: mapa de código de la pila de llamadas](../debugger/media/debuggermap_findallreferences.png)

 ![Métodos que usan un campo en el mapa de código de la pila de llamadas](../debugger/media/debuggermap_foundallreferences.png)

## <a name="find-bugs-using-the-map"></a><a name="FindBugs"></a> Buscar errores usando el mapa

 La visualización del código puede ayudarle a encontrar errores con mayor rapidez. Por ejemplo, supongamos que está investigando un error en un programa de dibujo. Cuando dibuja una línea e intenta deshacerla, no sucede nada hasta que dibuja otra línea.

 Por tanto, establece los puntos de interrupción en los métodos  `clear`, `undo` y `Repaint`, inicia la depuración y compila un mapa como este:

 ![Agregar otra pila de llamadas al mapa de código](../debugger/media/debuggermap_addpaintobjectcallstack.png)

 Observe que todos los gestos de usuario en el mapa llaman a `Repaint`, salvo `undo`. Esto podría explicar por qué `undo` no funciona inmediatamente.

 Tras corregir el error y seguir ejecutando el programa, el mapa agrega la nueva llamada de `undo` a `Repaint`:

 ![Agregar llamada a un nuevo método a la pila de llamadas en el mapa de código](../debugger/media/debuggermap_addnewcallforrepaint.png)

## <a name="q--a"></a><a name="QA"></a> Preguntas y respuestas

- **No todas las llamadas aparecen en el mapa. ¿por qué?**

   De forma predeterminada, en el mapa solo se muestra su código. Para ver el código externo, encándalo en la ventana **Pila de** llamadas:

   ![Mostrar código externo mediante la ventana Pila de llamadas](../debugger/media/debuggermap_callstackmenu.png)

   o desactive Habilitar **Solo mi código** en las Visual Studio de depuración:

   ![Mostrar código externo mediante el cuadro de diálogo Opciones](../debugger/media/debuggermap_debugoptions.png)

- **¿Afecta el cambio del mapa al código?**

   Cambiar el mapa no afecta al código de ninguna manera. No dude en cambiar el nombre, mover o quitar contenido del mapa.

- **¿Qué significa este mensaje: "El diagrama puede basarse en una versión anterior del código"?**

   El código podría haber cambiado después de la última actualización del mapa. Por ejemplo, una llamada en el mapa tal vez ya no exista en el código. Cierre el mensaje y, a continuación, intente volver a compilar la solución antes de actualizar el mapa de nuevo.

- **Cómo controlar el diseño del mapa?**

   Abra el menú **Diseño** en la barra de herramientas del mapa:

  - Cambie el diseño predeterminado.

  - Para detener la reorganización automática del mapa, desactive **Diseño automático al depurar**.

  - Para reorganizar el mapa lo menos posible al agregar elementos, desactive **Diseño incremental.**

- **¿Es posible compartir el mapa con otros usuarios?**

   Puede exportar el mapa, enviarlo a otros usuarios si tiene Microsoft Outlook o guardarlo en la solución para que pueda comprobarlo en el control de código fuente.

   ![Compartir el mapa de código de la pila de llamadas con otros usuarios](../debugger/media/debuggermap_sharewithothers.png)

- **¿Cómo se detiene la agregación automática de nuevas pilas de llamadas al mapa?**

   Elija ![ Botón &#45; Mostrar pila de llamadas en el mapa de código automáticamente en la barra de herramientas del ](../debugger/media/debuggermap_automaticupdateicon.gif) mapa. Para agregar manualmente la pila de llamadas actual al mapa, presione **Ctrl** + **Mayús** +  **`** .

   El mapa seguirá resaltando las pilas de llamadas existentes en el mapa durante la depuración.

- **¿Qué significan los iconos y las flechas de los elementos?**

   Para obtener más información sobre un elemento, mueva el puntero del mouse sobre él y mire la información sobre herramientas del elemento. También puede ver la leyenda **para** aprender lo que significa cada icono.

   ![¿Qué significan los iconos del mapa de código de la pila de llamadas?](../debugger/media/debuggermap_showlegend.png)

  Vea:

- [Asignación de la pila de llamadas](#MapStack)

- [Tomar notas sobre el código](#MakeNotes)

- [Actualización del mapa con la siguiente pila de llamadas](#UpdateMap)

- [Adición de código relacionado al mapa](#AddRelatedCode)

- [Buscar errores mediante el mapa](#FindBugs)

## <a name="see-also"></a>Vea también

- [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)
- [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)
- [Buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md)

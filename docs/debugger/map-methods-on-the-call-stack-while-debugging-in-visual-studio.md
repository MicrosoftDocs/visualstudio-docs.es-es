---
title: Crear un mapa visual de la pila de llamadas | Microsoft Docs
ms.date: 11/26/2018
ms.topic: conceptual
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3de5a3f9e9c5b8f89a9c8917794247098ba12d06
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62846808"
---
# <a name="create-a-visual-map-of-the-call-stack-while-debugging-c-visual-basic-c-javascript"></a>Crear un mapa visual de la pila de llamadas durante la depuración (C#, Visual Basic, C++, JavaScript)

Cree un mapa de código para hacer un seguimiento visual de la pila de llamadas durante la depuración. Puede hacer anotaciones en el mapa para llevar a cabo el seguimiento de lo que hace el código y poder concentrarse en encontrar errores.

Para ver un tutorial, vea este vídeo: [Vídeo: Depurar visualmente con la integración del depurador del mapa de código (Channel 9)](http://go.microsoft.com/fwlink/?LinkId=293418)

Para obtener detalles de los comandos y acciones que puede utilizar con mapas de código, vea [examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md).

>[!IMPORTANT]
>Puede crear únicamente en los mapas de código [edition de Visual Studio Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).

Este es un vistazo rápido a un mapa de código:

 ![Depuración con pilas de llamadas en mapas de código](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")

## <a name="MapStack"></a> Asignar la pila de llamadas

1. En un Visual Studio Enterprise C#, Visual Basic, C++, o JavaScript del proyecto, iniciar la depuración seleccionando **depurar** > **Iniciar depuración** o presionando **F5** .

1. Después de la aplicación entra en modo de interrupción o entra en una función, seleccione **depurar** > **mapa de código**, o bien presione **Ctrl**+**MAYÚS** +**`**.

   La pila de llamadas actual aparece en naranja en un nuevo mapa de código:

   ![Vea la pila de llamadas en mapa de código](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

El código asignado automáticamente las actualizaciones al continuar la depuración. Cambiar el diseño o elementos de mapa no afecta al código de algún modo. No dude en cambiar el nombre, mover o quitar contenido del mapa.

Para obtener más información sobre un elemento, mantenga el mouse sobre él y examine la información sobre herramientas del elemento. También puede seleccionar **leyenda** en la barra de herramientas para obtener información sobre lo que significa cada icono.

![Leyenda del mapa de código](../debugger/media/debuggermap_showlegend.png "leyenda del mapa de código")

>[!NOTE]
>El mensaje **el diagrama se puede basar en una versión anterior del código** en la parte superior del código de asignación significa que el código podría haber cambiado después de que el mapa se actualizó por última vez. Por ejemplo, una llamada en el mapa tal vez ya no exista en el código. Cierre el mensaje y, a continuación, intente volver a compilar la solución antes de actualizar el mapa de nuevo.

## <a name="map-external-code"></a>Mapa de código externo

De forma predeterminada, en el mapa solo se muestra su código. Para ver código externo en el mapa:

- Haga clic en el **pila de llamadas** ventana y seleccione **mostrar código externo**:

  ![Mostrar código externo mediante la ventana Pila de llamadas](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")
- O bien, anule la selección de **habilitar solo mi código** en Visual Studio **herramientas** (o **depurar**) > **opciones**  >   **Depuración**:

  ![Mostrar código externo mediante el cuadro de diálogo Opciones](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")

## <a name="control-the-maps-layout"></a>Controlar el diseño del mapa

Cambiar el diseño del mapa no afecta al código de algún modo.

Para controlar el diseño del mapa, seleccione el **diseño** menú en la barra de herramientas del mapa.

En el **diseño** menú, puede:

- Cambie el diseño predeterminado.
- Que deje de reorganizarse el mapa automáticamente, anulando la selección de **diseñar automáticamente al depurar**.
- Reorganizar el mapa lo mínimo posible al agregar elementos, anulando la selección de **diseño Incremental**.

## <a name="MakeNotes"></a> Hacer notas sobre el código

Puede agregar comentarios para realizar un seguimiento de lo que sucede en el código.

Para agregar un comentario, haga clic en el mapa de código y seleccione **editar** > **nuevo comentario**, a continuación, escriba el comentario.

Para agregar una nueva línea en un comentario, presione **MAYÚS**+**ENTRAR**.

 ![Agregar comentario a la pila de llamadas en mapa de código](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")

## <a name="UpdateMap"></a> Actualizar el mapa con la siguiente pila de llamadas

Cuando ejecute la aplicación en el siguiente punto de interrupción o el paso en una función, el mapa agrega automáticamente nuevas pilas de llamadas.

![Actualizar el mapa de código con la siguiente pila de llamadas](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")

Para detener la asignación de agregar automáticamente nuevas pilas de llamadas, seleccione ![pila de llamadas Mostrar en mapa de código automáticamente](../debugger/media/debuggermap_automaticupdateicon.gif "pila de llamadas Mostrar en mapa de código automáticamente") en la barra de herramientas del mapa de código. La asignación continúa resaltar las pilas de llamadas existentes. Para agregar manualmente la pila de llamadas actual al mapa, presione **Ctrl**+**MAYÚS**+**`**.

## <a name="AddRelatedCode"></a> Agregar código relacionado al mapa

Ahora que tiene una asignación, en C# o Visual Basic, puede agregar elementos tales como campos, propiedades y otros métodos para realizar un seguimiento de lo que sucede en el código.

Para ir a la definición de un método en el código, haga doble clic en el método en el mapa, o selecciónelo y presione **F12**, o haga clic en él y seleccione **ir a definición**.

![Vaya a la definición de código para un método en el mapa de código](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

Para agregar elementos a los que desea realizar el seguimiento en el mapa, haga clic en un método y seleccione los elementos que desea realizar un seguimiento. Los elementos agregados más recientemente aparecen en verde.

![Campos relacionados con un método en el mapa de código de pila de llamadas](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")

>[!NOTE]
>De forma predeterminada, al agregar elementos al mapa también se agregan nodos del grupo primario, como clase, espacio de nombres y ensamblado. Puede activar esta característica y activar seleccionando el **incluir elementos primarios** situado en la barra de herramientas del mapa de código o presionando **Ctrl** mientras se agregan elementos.

![Mostrar campos en un método en el mapa de código de pila de llamadas](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")

Continúe con la compilación del mapa para ver más código.

 ![Vea los métodos que usan un campo: mapa de código de pila de llamadas](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")

 ![Los métodos que usan un campo en el mapa de código de pila de llamadas](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="FindBugs"></a> Buscar errores usando el mapa
 La visualización del código puede ayudarle a encontrar errores con mayor rapidez. Por ejemplo, suponga que está investigando un error en una aplicación de dibujo. Cuando dibuja una línea e intenta deshacerla, no sucede nada hasta que dibuja otra línea.

 Por tanto, establece los puntos de interrupción en los métodos  `clear`, `undo` y `Repaint`, inicia la depuración y compila un mapa como este:

 ![Agregar otra pila de llamadas al mapa de código](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Observe que todos los gestos de usuario en el mapa llaman a `Repaint`, salvo `undo`. Esto podría explicar por qué `undo` no funciona inmediatamente.

 Después de corregir el error y continuar la ejecución de la aplicación, el mapa agrega la nueva llamada de `undo` a `Repaint`:

 ![Agregar nueva pila de llamada a método en el mapa de código](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="share-the-map-with-others"></a>Compartir el mapa con otros usuarios

Puede exportar un mapa, enviarlo a otros usuarios con Microsoft Outlook, guárdelo en la solución y consultarla en el control de versiones.

Para compartir o guardar el mapa, utilice **compartir** en la barra de herramientas del mapa de código.

![Mapa de código de pila de llamadas de recurso compartido con otras personas](../debugger/media/debuggermap_sharewithothers.png "mapa de código de pila de llamadas de recurso compartido con otros usuarios")

## <a name="see-also"></a>Vea también
[Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)

[Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)

[Buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)

[Examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md)

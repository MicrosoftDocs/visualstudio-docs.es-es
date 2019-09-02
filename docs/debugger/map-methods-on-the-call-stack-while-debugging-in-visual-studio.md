---
title: Cree un mapa visual de la pila de llamadas | Microsoft Docs
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
ms.openlocfilehash: 62fb77590a20b0e31648cab10f310851fd65820e
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2019
ms.locfileid: "70179994"
---
# <a name="create-a-visual-map-of-the-call-stack-while-debugging-c-visual-basic-c-javascript"></a>Crear un mapa visual de la pila de llamadas durante la depuraciónC#( C++, Visual Basic,, JavaScript)

Cree un mapa de código para hacer un seguimiento visual de la pila de llamadas durante la depuración. Puede hacer anotaciones en el mapa para llevar a cabo el seguimiento de lo que hace el código y poder concentrarse en encontrar errores.

Para ver un tutorial, vea este vídeo: [Vídeo: Depurar visualmente con la integración del depurador del mapa de código (Channel 9)](http://go.microsoft.com/fwlink/?LinkId=293418)

Para más información sobre los comandos y las acciones que se pueden usar con los mapas de código, vea [examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md).

>[!IMPORTANT]
>Solo puede crear mapas de código en [Visual Studio Enterprise Edition](https://visualstudio.microsoft.com/downloads).

A continuación se muestra una vista rápida de un mapa de código:

 ![Depurar con pilas de llamadas en mapas de código](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")

## <a name="MapStack"></a> Asignar la pila de llamadas

1. En un proyecto C#de Visual Studio Enterprise, C++Visual Basic, o JavaScript, inicie la depuración seleccionando depurar > **iniciar** depuración o presionando **F5**.

1. Después de que la aplicación entre en modo de interrupción o entre en una > función, seleccione el**mapa de código**de depuración o presione **Ctrl**+**MAYÚS**+ **`** .

   La pila de llamadas actual aparece en naranja en un nuevo mapa de código:

   ![Vea pila de llamadas en el mapa de código](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

El mapa de código se actualiza automáticamente a medida que continúa con la depuración. Cambiar los elementos de mapa o el diseño no afecta al código de ninguna manera. No dude en cambiar el nombre, mover o quitar contenido del mapa.

Para obtener más información sobre un elemento, mantenga el mouse sobre él y mire la información sobre herramientas del elemento. También puede seleccionar **leyenda** en la barra de herramientas para obtener información sobre lo que significa cada icono.

![Leyenda de mapa de código](../debugger/media/debuggermap_showlegend.png "Leyenda de mapa de código")

>[!NOTE]
>El mensaje que **el diagrama puede estar basado en una versión anterior del código** en la parte superior del mapa de código significa que el código podría haber cambiado después de la última actualización del mapa. Por ejemplo, una llamada en el mapa tal vez ya no exista en el código. Cierre el mensaje y, a continuación, intente volver a compilar la solución antes de actualizar el mapa de nuevo.

## <a name="map-external-code"></a>Asignación de código externo

De forma predeterminada, en el mapa solo se muestra su código. Para ver el código externo en el mapa:

- Haga clic con el botón secundario en la ventana **pila de llamadas** y seleccione **Mostrar código externo**:

  ![Mostrar código externo mediante la ventana pila de llamadas](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")
- O bien, anule la selección de **Habilitar solo mi código** en Visual Studio **Tools** (o depurar) > **Opciones** > de depuración:

  ![Cuadro de diálogo Mostrar código externo mediante opciones](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")

## <a name="control-the-maps-layout"></a>Controlar el diseño del mapa

Cambiar el diseño del mapa no afecta al código de ninguna manera.

Para controlar el diseño del mapa, seleccione el menú **diseño** en la barra de herramientas del mapa.

En el menú **diseño** , puede:

- Cambie el diseño predeterminado.
- Detener la reorganización automática del mapa, anulando la selección del **diseño automático durante**la depuración.
- Reorganice el mapa lo más bajo posible al agregar elementos, anulando la selección del **diseño incremental**.

## <a name="MakeNotes"></a> Hacer notas sobre el código

Puede agregar comentarios para realizar un seguimiento de lo que ocurre en el código.

Para agregar un comentario, haga clic con el botón derecho en el mapa de código y seleccione **Editar** > **nuevo comentario**y, a continuación, escriba el comentario.

Para agregar una nueva línea a un comentario, presione **MAYÚS**+**entrar**.

 ![Agregar un comentario a la pila de llamadas en el mapa de código](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")

## <a name="UpdateMap"></a> Actualizar el mapa con la siguiente pila de llamadas

Al ejecutar la aplicación en el siguiente punto de interrupción o entrar en una función, el mapa agrega automáticamente nuevas pilas de llamadas.

![Actualizar mapa de código con la siguiente pila de llamadas](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")

Para que la asignación deje de agregar automáticamente nuevas pilas de llamadas, seleccione ![Mostrar pila de llamadas en mapa de código automáticamente](../debugger/media/debuggermap_automaticupdateicon.gif "Mostrar pila de llamadas en el mapa de código automáticamente") en la barra de herramientas del mapa de código. La asignación continúa resaltando las pilas de llamadas existentes. Para agregar manualmente la pila de llamadas actual al mapa, presione **Ctrl**+**MAYÚS**+ **`** .

## <a name="AddRelatedCode"></a> Agregar código relacionado al mapa

Ahora que tiene un mapa, en C# o Visual Basic, puede agregar elementos como campos, propiedades y otros métodos, para realizar un seguimiento de lo que sucede en el código.

Para ir a la definición de un método en el código, haga doble clic en el método en el mapa, selecciónelo y presione **F12**, o haga clic con el botón derecho en él y seleccione **ir a definición**.

![Ir a definición de código para un método en el mapa de código](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

Para agregar los elementos de los que desea realizar un seguimiento al mapa, haga clic con el botón secundario en un método y seleccione los elementos de los que desea realizar un seguimiento. Los elementos agregados más recientemente aparecen en verde.

![Campos relacionados con un método en el mapa de código de la pila de llamadas](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")

>[!NOTE]
>De forma predeterminada, al agregar elementos al mapa también se agregan nodos del grupo primario, como clase, espacio de nombres y ensamblado. Para activar y desactivar esta característica, seleccione el botón **incluir elementos primarios** en la barra de herramientas del mapa de código o presione **Ctrl** mientras agrega elementos.

![Mostrar los campos de un método en el mapa de código de la pila de llamadas](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")

Continúe con la compilación del mapa para ver más código.

 ![Vea los métodos que usan un campo: mapa de código de pila de llamadas](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")

 ![Métodos que usan un campo en el mapa de código de la pila de llamadas](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="FindBugs"></a> Buscar errores usando el mapa
 La visualización del código puede ayudarle a encontrar errores con mayor rapidez. Por ejemplo, supongamos que está investigando un error en una aplicación de dibujo. Cuando dibuja una línea e intenta deshacerla, no sucede nada hasta que dibuja otra línea.

 Por tanto, establece los puntos de interrupción en los métodos  `clear`, `undo` y `Repaint`, inicia la depuración y compila un mapa como este:

 ![Agregar otra pila de llamadas al mapa de código](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Observe que todos los gestos de usuario en el mapa llaman a `Repaint`, salvo `undo`. Esto podría explicar por qué `undo` no funciona inmediatamente.

 Después de corregir el error y seguir ejecutando la aplicación, la asignación agrega la nueva llamada de `undo` a `Repaint`:

 ![Agregar nueva llamada de método a la pila de llamadas en el mapa de código](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="share-the-map-with-others"></a>Compartir el mapa con otros usuarios

Puede exportar un mapa, enviarlo a otros usuarios con Microsoft Outlook, guardarlo en la solución y protegerlo en el control de versiones.

Para compartir o guardar el mapa, use **compartir** en la barra de herramientas del mapa de código.

![Compartir el mapa de código de la pila de llamadas con otros usuarios](../debugger/media/debuggermap_sharewithothers.png "Compartir el mapa de código de la pila de llamadas con otros usuarios")

## <a name="see-also"></a>Vea también
[Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)

[Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)

[Buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)

[Examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md)

---
title: Creación de un mapa visual de la pila de llamadas | Microsoft Docs
description: Cree un mapa de código para hacer un seguimiento visual de la pila de llamadas durante la depuración. Incluya anotaciones en el mapa para realizar un seguimiento de lo que hace el código y así poder centrarse en encontrar errores.
ms.custom: SEO-VS-2020
ms.date: 11/26/2018
ms.topic: how-to
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
ms.openlocfilehash: 965232f56fcd2bf0d459910e983fb10dcca7f96d
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903836"
---
# <a name="create-a-visual-map-of-the-call-stack-while-debugging-c-visual-basic-c-javascript"></a>Creación de un mapa visual de la pila de llamadas durante la depuración (C#, Visual Basic, C++, JavaScript)

Cree un mapa de código para hacer un seguimiento visual de la pila de llamadas durante la depuración. Puede hacer anotaciones en el mapa para llevar a cabo el seguimiento de lo que hace el código y poder concentrarse en encontrar errores.

Si quiere seguir un tutorial, vea este vídeo: [Vídeo: Depuración visual gracias a la integración del depurador del mapa de código (Channel 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration)

Para más información sobre los comandos y las acciones que puede usar al trabajar con mapas de código, vea [Examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md).

>[!IMPORTANT]
>Solo puede crear mapas de código en [Visual Studio Enterprise Edition](https://visualstudio.microsoft.com/downloads).

A continuación se muestra una vista rápida de un mapa de código:

 ![Depuración con pilas de llamadas en los mapas de código](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")

## <a name="map-the-call-stack"></a><a name="MapStack"></a> Asignar la pila de llamadas

1. En un proyecto de C#, Visual Basic, C++ o JavaScript en Visual Studio Enterprise, inicie la depuración seleccionando **Depurar** > **Iniciar depuración** o presionando **F5**.

1. Cuando la aplicación entra en modo de interrupción o se ejecuta una función paso a paso por instrucciones, seleccione **Depurar** > **Mapa de código**, o presione **Ctrl**+**Mayús**+ **`** .

   La pila de llamadas actual aparece en naranja en un nuevo mapa de código:

   ![Ver pila de llamadas en el mapa de código](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

El mapa de código se actualiza automáticamente a medida que continúa con la depuración. Cambiar los elementos o el diseño del mapa no afecta al código de ninguna manera. No dude en cambiar el nombre, mover o quitar contenido del mapa.

Para más información sobre un elemento, mantenga el puntero del mouse sobre él y examine su información sobre herramientas. También puede seleccionar **Leyenda** en la barra de herramientas para obtener información sobre lo que significa cada icono.

![Leyenda de mapa de código](../debugger/media/debuggermap_showlegend.png "Leyenda de mapa de código")

>[!NOTE]
>El mensaje **El diagrama se puede basar en una versión anterior del código** de la parte superior del mapa de código significa que el código podría haber cambiado después de la última actualización del mapa. Por ejemplo, una llamada en el mapa tal vez ya no exista en el código. Cierre el mensaje y, a continuación, intente volver a compilar la solución antes de actualizar el mapa de nuevo.

## <a name="map-external-code"></a>Código externo del mapa

De forma predeterminada, en el mapa solo se muestra su código. Para ver el código externo en el mapa:

- Haga clic con el botón derecho en la ventana **Pila de llamadas** y seleccione **Mostrar código externo**:

  ![Mostrar código externo mediante la ventana Pila de llamadas](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")
- O bien, anule la selección de **Habilitar Solo mi código** en **Herramientas** de Visual Studio (o **Depurar**) > **Opciones** > **Depuración**:

  ![Mostrar código externo mediante el cuadro de diálogo Opciones](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")

## <a name="control-the-maps-layout"></a>Control del diseño del mapa

Cambiar el diseño del mapa no afecta al código de ninguna manera.

Para controlar el diseño del mapa, seleccione el menú **Diseño** en la barra de herramientas del mapa.

En el menú **Diseño**, puede:

- Cambie el diseño predeterminado.
- Detener la reorganización automática del mapa anulando la selección de **Diseñar automáticamente al depurar**.
- Reorganizar el mapa lo menos posible al agregar elementos desactivando **Diseño incremental**.

## <a name="make-notes-about-the-code"></a><a name="MakeNotes"></a> Hacer notas sobre el código

Puede agregar comentarios para el hacer seguimiento de lo que pasa en el código.

Para agregar un comentario, haga clic con el botón derecho en el mapa de código, seleccione **Editar** > **Nuevo comentario** y escriba el comentario.

Para agregar una nueva línea a un comentario, presione **Mayús**+**Entrar**.

 ![Agregar comentario a la pila de llamadas en el mapa de código](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")

## <a name="update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a> Actualizar el mapa con la siguiente pila de llamadas

Al ejecutar la aplicación en el siguiente punto de interrupción o ejecutar una función paso a paso por instrucciones, el mapa agrega automáticamente nuevas pilas de llamadas.

![Actualizar mapa de código con la siguiente pila de llamadas](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")

Para que el mapa deje de agregar automáticamente nuevas pilas de llamadas, seleccione ![Mostrar automáticamente pila de llamadas del depurador en mapa de código](../debugger/media/debuggermap_automaticupdateicon.gif "Mostrar automáticamente pila de llamadas del depurador en mapa de código") en la barra de herramientas del mapa de código. El mapa continúa resaltando las pilas de llamadas existentes. Para agregar manualmente la pila de llamadas actual al mapa, presione **Ctrl**+**Mayús**+ **`** .

## <a name="add-related-code-to-the-map"></a><a name="AddRelatedCode"></a> Agregar código relacionado al mapa

Ahora que ya tiene un mapa, en C# o Visual Basic, puede agregar elementos, tales como campos, propiedades y otros métodos, para hacer el seguimiento de lo que pasa en el código.

Para ir a la definición de un método en el código, haga doble clic en el método en el mapa o selecciónelo y presione **F12**, o bien haga clic con el botón derecho en él y seleccione **Ir a definición**.

![Ir a la definición de código de un método en el mapa de código](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

Para agregar elementos cuyo seguimiento quiere realizar, haga clic con el botón derecho en un método y seleccione esos elementos. Los elementos agregados más recientemente aparecen en verde.

![Campos relacionados con un método en el mapa de código de la pila de llamadas](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")

>[!NOTE]
>De forma predeterminada, al agregar elementos al mapa también se agregan nodos del grupo primario, como clase, espacio de nombres y ensamblado. Para activar y desactivar esta característica, seleccione el botón **Incluir primarios** en la barra de herramientas del mapa de código o presione **Ctrl** mientras agrega elementos.

![Mostrar campos en un método en el mapa de código de la pila de llamadas](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")

Continúe con la compilación del mapa para ver más código.

 ![Ver métodos que usan un campo: mapa de código de la pila de llamadas](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")

 ![Métodos que usan un campo en el mapa de código de la pila de llamadas](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="find-bugs-using-the-map"></a><a name="FindBugs"></a> Buscar errores usando el mapa
 La visualización del código puede ayudarle a encontrar errores con mayor rapidez. Por ejemplo, suponga que está investigando un error en una aplicación de dibujo. Cuando dibuja una línea e intenta deshacerla, no sucede nada hasta que dibuja otra línea.

 Por tanto, establece los puntos de interrupción en los métodos  `clear`, `undo` y `Repaint`, inicia la depuración y compila un mapa como este:

 ![Agregar otra pila de llamadas al mapa de código](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Observe que todos los gestos de usuario en el mapa llaman a `Repaint`, salvo `undo`. Esto podría explicar por qué `undo` no funciona inmediatamente.

 Tras corregir el error y seguir ejecutando la aplicación, el mapa agrega la nueva llamada de `undo` a `Repaint`:

 ![Agregar llamada a un nuevo método a la pila de llamadas en el mapa de código](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="share-the-map-with-others"></a>Uso compartido del mapa con otros usuarios

Puede exportar un mapa, enviarlo a otros usuarios con Microsoft Outlook, guardarlo en la solución y protegerlo en el control de versiones.

Para compartir o guardar el mapa, use **Compartir** en la barra de herramientas del mapa de código.

![Compartir el mapa de código de la pila de llamadas con otros usuarios](../debugger/media/debuggermap_sharewithothers.png "Compartir el mapa de código de la pila de llamadas con otros usuarios")

## <a name="see-also"></a>Vea también
[Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)

[Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)

[Buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)

[Examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md)

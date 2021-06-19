---
title: Usar mapas de código para depurar aplicaciones
description: Aprenda a usar mapas de código para evitar perderse en bases de código grandes, código desconocido o código heredado.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, visualizing code
- Visual Studio Ultimate, navigating code visually
- Visual Studio Ultimate, understanding code
- Visual Studio Ultimate, mapping code relationships
- Visual Studio Ultimate, code maps
- mapping code relationships
- code maps
- mapping relationships in code
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b422c6c7857ca1baaa5bd1d8a7d6955e8b6751b3
ms.sourcegitcommit: c3713f284c4fe10b10996d5eb67077ddd8641424
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112375804"
---
# <a name="use-code-maps-to-debug-your-applications"></a>Usar mapas de código para depurar aplicaciones

[Los mapas de código Visual Studio](../modeling/map-dependencies-across-your-solutions.md) pueden ayudarle a evitar perderse en bases de código grandes, código desconocido o código heredado. Por ejemplo, al depurar, es posible que tenga que ver el código en muchos archivos y proyectos. Use mapas de código para navegar por fragmentos de código y entender las relaciones entre ellos. De este modo evitará tener que realizar un seguimiento mental de este código o dibujar un diagrama independiente. Así, cuando interrumpa su trabajo, los mapas de código le ayudarán a recordar el código en el que está trabajando.

![Asignación de &#45; asignar relaciones en el código](../modeling/media/codemapstoryboardpaint.png)

**Una flecha verde muestra la posición del cursor en el editor.**

Para obtener más información sobre los comandos y las acciones que puede usar al trabajar con mapas de código, vea [Examinar y reorganizar mapas de código.](../modeling/browse-and-rearrange-code-maps.md)

Obtenga más información sobre [la depuración en Visual Studio con la herramienta Depurador](../debugger/debugger-feature-tour.md).

> [!NOTE]
> Para crear y editar mapas de código, necesita Visual Studio Enterprise edición. En Visual Studio Community y Professional, puede abrir diagramas que se generaron en Enterprise Edition, pero no puede editarlos.

## <a name="understand-the-problem"></a>Entender el problema
 Supongamos que hay un error en un programa de dibujo en el que está trabajando. Para reproducir el error, abra la solución en Visual Studio presione **F5** para iniciar la depuración.

 Al dibujar una línea y elegir Deshacer mi último **trazo,** no ocurre nada hasta que dibuje la línea siguiente.

 ![Error de repro &#45; mapa de código](../modeling/media/codemapstoryboardpaint0.png)

 Por tanto, comienza la investigación buscando el método `Undo`. Lo encuentra en la clase `PaintCanvas`.

 ![Código de mapa &#45; buscar código](../modeling/media/codemapstoryboardpaint1.png)

## <a name="start-mapping-the-code"></a>Empezar a asignar el código
 Ahora comience la asignación del método `undo` y sus relaciones. Desde el editor de código, agrega el método `undo` y los campos a los que se hace referencia a un nuevo mapa de código. Cuando se crea un nuevo mapa, es posible que se tarde algo de tiempo en indizar el código. Esto ayuda a que se ejecuten más rápido las operaciones posteriores.

 ![Mapa de código &#45; mostrar el método y los campos relacionados](../modeling/media/codemapstoryboardpaint3.png)

> [!TIP]
> El resaltado verde muestra los últimos elementos agregados al mapa. La flecha verde muestra la posición del cursor en el código. Las flechas entre los elementos representan diferentes relaciones. Para más información sobre los elementos del mapa, pase el mouse sobre ellos y examine su información sobre herramientas.

 ![Mapa de código &#45; mostrar información sobre herramientas](../modeling/media/codemapstoryboardpaint4.png)

## <a name="navigate-and-examine-code-from-the-map"></a>Navegar y examinar código desde la asignación
 Para ver la definición de código de cada campo, haga doble clic en el campo en el mapa o seleccione el campo y **presione F12**. La flecha verde se desplaza entre los elementos del mapa. El cursor del editor de código también se desplaza automáticamente.

 ![Captura de pantalla de una ventana de mapa de código con el campo historial seleccionado y una ventana del editor de código donde se resaltan todas las instancias del historial.](../modeling/media/codemapstoryboardpaint5.png)

 ![Captura de pantalla de una ventana de mapa de código con el campo paintObjects seleccionado y una ventana del editor de código donde se resaltan todas las instancias de paintObjects.](../modeling/media/codemapstoryboardpaint5a.png)

> [!TIP]
> También puede mover la flecha verde en el mapa moviendo el cursor en el editor de código.

## <a name="understand-relationships-between-pieces-of-code"></a>Entender las relaciones entre los elementos de código
 Ahora desea saber qué otro código interactúa con los campos `history` y `paintObjects`. Puede agregar todos los métodos que hacen referencia a estos campos al mapa. Puede hacer esto desde el mapa o desde el editor de código.

 ![Mapa de código &#45; buscar todas las referencias](../modeling/media/codemapstoryboardpaint6.png)

 ![Abrir un mapa de código desde el editor de código](../modeling/media/codemapstoryboardpaint6a.png)

> [!NOTE]
> Si agrega elementos de un proyecto que se comparte entre varias aplicaciones, como Windows Phone o la Tienda Windows, dichos elementos aparecen siempre en el mapa con el proyecto de aplicación activo actualmente. Por lo tanto, si cambia el contexto a otro proyecto de aplicación, también cambia el contexto en el mapa para cualquier elemento recién agregado desde el proyecto compartido. Las operaciones que se realizan con un elemento en el mapa solo se aplican a los elementos que comparten el mismo contexto.

 Cambie el diseño para reorganizar el flujo de las relaciones y facilitar la lectura del mapa. También puede mover los elementos por el mapa arrastrándolos.

 ![Captura de pantalla de una ventana de mapa de código con el menú Diseño abierto y el comando Left to Rgiht (Izquierda a Rgiht) seleccionado.](../modeling/media/codemapstoryboardpaint7a.png)

> [!TIP]
> De forma predeterminada, **el diseño incremental** está activado. El mapa se reorganiza lo menos posible cuando se agregan nuevos elementos. Para reorganizar todo el mapa cada vez que agregue nuevos elementos, desactive **Diseño incremental**.

 ![Captura de pantalla de una ventana de mapa de código con las flechas relationshiop entre los campos que apuntan de izquierda a derecha.](../modeling/media/codemapstoryboardpaint7.png)

 Examinemos estos métodos. En el mapa, haga doble clic en **el método PaintCanvas** o seleccione este método y presione **F12**. Verá que este método crea `history` y `paintObjects` como listas vacías.

 ![Captura de pantalla de una ventana de mapa de código con el método PaintCanvas seleccionado y una imagen de fragmento de código que muestra el nombre del método PainCanvas resaltado.](../modeling/media/codemapstoryboardpaint8.png)

 Ahora repita los mismos pasos para examinar la definición del método `clear`. Verá que `clear` lleva a cabo algunas tareas con `paintObjects` e `history`. A continuación, llama al método `Repaint`.

 ![Captura de pantalla de una ventana de mapa de código con el método Clear seleccionado y una imagen de fragmento de código que muestra el código para el método Clear.](../modeling/media/codemapstoryboardpaint9.png)

 Ahora, examine la definición del método `addPaintObject`. También realiza algunas tareas con `history` y `paintObjects`. También llama a `Repaint`.

 ![Captura de pantalla de una ventana de mapa de código con el método addPaintObject seleccionado y una imagen de fragmento de código que muestra el código del método addPaintObject.](../modeling/media/codemapstoryboardpaint10.png)

## <a name="find-the-problem-by-examining-the-map"></a>Buscar el problema examinando la asignación
 Parece que todos los métodos que modifican `history` y `paintObjects` llaman a `Repaint`. Con todo, el método `undo` no llama a `Repaint`, aunque `undo` modifica los mismos campos. Por tanto, cree que puede corregir este problema mediante una llamada a `Repaint` desde `undo`.

 ![Asignación de código &#45; llamada de método que falta](../modeling/media/codemapstoryboardpaint11.png)

 Si no tuviese un mapa para encontrar la llamada que falta, posiblemente sería más difícil localizar este problema, sobre todo con código más complejo.

## <a name="share-your-discovery-and-next-steps"></a>Compartir la información y pasos siguientes
 Antes de que usted u otro usuario corrija este error, puede hacer anotaciones en el mapa acerca del problema y de cómo corregirlo.

 ![Asignación de &#45; elementos de marca y comentario para seguimiento](../modeling/media/codemapstoryboardpaint12.png)

 Por ejemplo, puede agregar comentarios al mapa y marcar los elementos con colores.

 ![Asignación de &#45; elementos marcados y comentados](../modeling/media/codemapstoryboardpaint12a.png)

 Si tiene Microsoft Outlook instalado, puede enviar el mapa a otras personas por correo electrónico. También puede exportar el mapa como imagen u otro formato.

 ![Asignación de &#45; compartir, exportar, correo electrónico](../modeling/media/codemapstoryboardpaint13.png)

## <a name="fix-the-problem-and-show-what-you-did"></a>Corregir el problema y mostrar lo que hizo
 Para corregir este error, agregue la llamada de `Repaint` a `undo`.

 ![Asignación de código &#45; agregar llamada de método que falta](../modeling/media/codemapstoryboardpaint14.png)

 Para confirmar la corrección, reinicie su sesión de depuración e intente reproducir el error. Ahora elegir **Deshacer mi último trazo** funciona según lo previsto y confirma que ha realizado la corrección correcta.

 ![Corrección de código &#45; mapa de código](../modeling/media/codemapstoryboardpaint15.png)

 Puede actualizar el mapa para mostrar la corrección que realizó.

 ![Mapa de código &#45; mapa de actualización con una llamada de método que falta](../modeling/media/codemapstoryboardpaint16.png)

 El mapa ahora muestra un vínculo entre **deshacer** y **volver a dibujar**.

 ![Mapa de código &#45; mapa actualizado con llamada al método](../modeling/media/codemapstoryboardpaint17.png)

> [!NOTE]
> Cuando actualice el mapa, puede que vea un mensaje que indica que se ha actualizado el índice de código utilizado para crear el mapa. Esto significa que alguien ha cambiado el código, lo que hace que el mapa no coincida con código actual. Esto no detiene su actualización del mapa, pero podría tener que volver a crearlo para confirmar que coincide con el código.

 Ya ha terminado con la investigación. Encontró y corrigió correctamente el problema asignando el código. También tiene un mapa que le ayuda a navegar por el código y a recordar lo que ha aprendido, y le muestra los pasos llevados a cabo para corregir el problema.

## <a name="see-also"></a>Vea también

- [Asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Visualizar el código](../modeling/visualize-code.md)

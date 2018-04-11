---
title: Usar mapas de código para depurar aplicaciones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: ab5d32c6a25eb9db21970ade0034aa1afd219a61
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/10/2018
---
# <a name="use-code-maps-to-debug-your-applications"></a>Usar mapas de código para depurar aplicaciones
Los mapas de código le ayudan a evitar bases de código de gran tamaño, código con el que no esté familiarizado o código heredado. Por ejemplo, al depurar, puede que tenga que buscar en varios proyectos y archivos. Use mapas de código para navegar por fragmentos de código y entender las relaciones entre ellos. De este modo evitará tener que realizar un seguimiento mental de este código o dibujar un diagrama independiente. Así, cuando interrumpa su trabajo, los mapas de código le ayudarán a recordar el código en el que está trabajando.  

 ![Mapa de código &#45; asignar relaciones en el código](../modeling/media/codemapstoryboardpaint.png "CodeMapStoryboardPaint")  

 **Una flecha verde muestra el cursor en el editor de**  

 Para obtener información detallada de los comandos y las acciones que puede utilizar cuando se trabaja con mapas de código, vea [examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md).  

## <a name="understand-the-problem"></a>Entender el problema  
 Supongamos que hay un error en un programa de dibujo en el que está trabajando. Para reproducir el error, abra la solución en Visual Studio y presione **F5** para iniciar la depuración.  

 Cuando dibuje una línea y elija **deshacer mi último trazo**, no ocurre nada hasta que se dibuje la línea siguiente.  

 ![Mapa de código &#45; : error de reproducción](../modeling/media/codemapstoryboardpaint0.png "CodeMapStoryboardPaint0")  

 Por tanto, comienza la investigación buscando el método `Undo`. Lo encuentra en la clase `PaintCanvas`.  

 ![Mapa de código &#45; Buscar código](../modeling/media/codemapstoryboardpaint1.png "CodeMapStoryboardPaint1")  

## <a name="start-mapping-the-code"></a>Empezar a asignar el código  
 Ahora comience la asignación del método `undo` y sus relaciones. Desde el editor de código, agrega el método `undo` y los campos a los que se hace referencia a un nuevo mapa de código. Cuando se crea un nuevo mapa, es posible que se tarde algo de tiempo en indizar el código. Esto ayuda a que se ejecuten más rápido las operaciones posteriores.  

 ![Mapa de código &#45; mostrar todos los campos relacionados y método](../modeling/media/codemapstoryboardpaint3.png "CodeMapStoryboardPaint3")  

> [!TIP]
>  El resaltado verde muestra los últimos elementos agregados al mapa. La flecha verde muestra la posición del cursor en el código. Las flechas entre los elementos representan diferentes relaciones. Para más información sobre los elementos del mapa, pase el mouse sobre ellos y examine su información sobre herramientas.  

 ![Mapa de código &#45; mostrar información sobre herramientas](../modeling/media/codemapstoryboardpaint4.png "CodeMapStoryboardPaint4")  

## <a name="navigate-and-examine-code-from-the-map"></a>Navegar y examinar código desde la asignación  
 Para ver la definición de código para cada campo, haga doble clic en el campo en el mapa o seleccione el campo y presione **F12**. La flecha verde se desplaza entre los elementos del mapa. El cursor del editor de código también se desplaza automáticamente.  

 ![Mapa de código &#45; examinar la definición de campo](../modeling/media/codemapstoryboardpaint5.png "CodeMapStoryboardPaint5")  

 ![Mapa de código &#45; examinar la definición de campo](../modeling/media/codemapstoryboardpaint5a.png "CodeMapStoryboardPaint5A")  

> [!TIP]
>  También puede mover la flecha verde en el mapa moviendo el cursor en el editor de código.  

## <a name="understand-relationships-between-pieces-of-code"></a>Entender las relaciones entre los elementos de código  
 Ahora desea saber qué otro código interactúa con los campos `history` y `paintObjects`. Puede agregar todos los métodos que hacen referencia a estos campos al mapa. Puede hacer esto desde el mapa o desde el editor de código.  

 ![Mapa de código &#45; buscar todas las referencias](../modeling/media/codemapstoryboardpaint6.png "CodeMapStoryboardPaint6")  

 ![Abrir un mapa de código desde el editor de código](../modeling/media/codemapstoryboardpaint6a.PNG "CodeMapStoryboardPaint6A")  

> [!NOTE]
>  Si agrega elementos de un proyecto que se comparte entre varias aplicaciones, como Windows Phone o la Tienda Windows, dichos elementos aparecen siempre en el mapa con el proyecto de aplicación activo actualmente. Por lo tanto, si cambia el contexto a otro proyecto de aplicación, también cambia el contexto en el mapa para cualquier elemento recién agregado desde el proyecto compartido. Las operaciones que se realizan con un elemento en el mapa solo se aplican a los elementos que comparten el mismo contexto.  

 Cambie el diseño para reorganizar el flujo de las relaciones y facilitar la lectura del mapa. También puede mover los elementos por el mapa arrastrándolos.  

 ![Mapa de código &#45; cambiar el diseño](../modeling/media/codemapstoryboardpaint7a.png "CodeMapStoryboardPaint7A")  

> [!TIP]
>  De forma predeterminada, **diseño Incremental** está activado. El mapa se reorganiza lo menos posible cuando se agregan nuevos elementos. Para reorganizar el mapa completo cada vez que agregue nuevos elementos, desactive la opción **diseño Incremental**.  

 ![Mapa de código &#45; cambiar el diseño](../modeling/media/codemapstoryboardpaint7.png "CodeMapStoryboardPaint7")  

 Examinemos estos métodos. En el mapa, haga doble clic en el **PaintCanvas** método, o seleccione este método y presione **F12**. Verá que este método crea `history` y `paintObjects` como listas vacías.  

 ![Mapa de código &#45; examinar la definición de método](../modeling/media/codemapstoryboardpaint8.png "CodeMapStoryboardPaint8")  

 Ahora repita los mismos pasos para examinar la definición del método `clear`. Verá que `clear` lleva a cabo algunas tareas con `paintObjects` e `history`. A continuación, llama al método `Repaint`.  

 ![Mapa de código &#45; examinar la definición de método](../modeling/media/codemapstoryboardpaint9.png "CodeMapStoryboardPaint9")  

 Ahora, examine la definición del método `addPaintObject`. También realiza algunas tareas con `history` y `paintObjects`. También llama a `Repaint`.  

 ![Mapa de código &#45; examinar la definición de método](../modeling/media/codemapstoryboardpaint10.png "CodeMapStoryboardPaint10")  

## <a name="find-the-problem-by-examining-the-map"></a>Buscar el problema examinando la asignación  
 Parece que todos los métodos que modifican `history` y `paintObjects` llaman a `Repaint`. Con todo, el método `undo` no llama a `Repaint`, aunque `undo` modifica los mismos campos. Por tanto, cree que puede corregir este problema mediante una llamada a `Repaint` desde `undo`.  

 ![Mapa de código &#45; buscar llamada a método que falta](../modeling/media/codemapstoryboardpaint11.png "CodeMapStoryboardPaint11")  

 Si no tuviese un mapa para encontrar la llamada que falta, posiblemente sería más difícil localizar este problema, sobre todo con código más complejo.  

## <a name="share-your-discovery-and-next-steps"></a>Compartir la información y pasos siguientes  
 Antes de que usted u otro usuario corrija este error, puede hacer anotaciones en el mapa acerca del problema y de cómo corregirlo.  

 ![Mapa de código &#45; comentar y marcar elementos para el seguimiento](../modeling/media/codemapstoryboardpaint12.png "CodeMapStoryboardPaint12")  

 Por ejemplo, puede agregar comentarios al mapa y marcar los elementos con colores.  

 ![Mapa de código &#45; comentado y elementos marcados](../modeling/media/codemapstoryboardpaint12a.png "CodeMapStoryboardPaint12A")  

 Si tiene Microsoft Outlook instalado, puede enviar el mapa a otras personas por correo electrónico. También puede exportar el mapa como imagen u otro formato.  

 ![Mapa de código &#45; recurso compartido, exportación, correo electrónico de](../modeling/media/codemapstoryboardpaint13.png "CodeMapStoryboardPaint13")  

## <a name="fix-the-problem-and-show-what-you-did"></a>Corregir el problema y mostrar lo que hizo  
 Para corregir este error, agregue la llamada de `Repaint` a `undo`.  

 ![Mapa de código &#45; agregar llamada a método que falta](../modeling/media/codemapstoryboardpaint14.png "CodeMapStoryboardPaint14")  

 Para confirmar la corrección, reinicie su sesión de depuración e intente reproducir el error. Ahora, si elige **deshacer mi último trazo** funciona como se esperaba y confirma que realizó la solución adecuada.  

 ![Mapa de código &#45; Confirmar corrección](../modeling/media/codemapstoryboardpaint15.png "CodeMapStoryboardPaint15")  

 Puede actualizar el mapa para mostrar la corrección que realizó.  

 ![Mapa de código &#45; actualizar el mapa con la llamada a método que falta](../modeling/media/codemapstoryboardpaint16.png "CodeMapStoryboardPaint16")  

 El mapa muestra ahora un vínculo entre **deshacer** y **volver a dibujar**.  

 ![Mapa de código &#45; el mapa actualizado con la llamada al método](../modeling/media/codemapstoryboardpaint17.png "CodeMapStoryboardPaint17")  

> [!NOTE]
>  Cuando actualice el mapa, puede que vea un mensaje que indica que se ha actualizado el índice de código utilizado para crear el mapa. Esto significa que alguien ha cambiado el código, lo que hace que el mapa no coincida con código actual. Esto no detiene su actualización del mapa, pero podría tener que volver a crearlo para confirmar que coincide con el código.  

 Ahora ha terminado con la investigación. Encontró y corrigió correctamente el problema asignando el código. También tiene un mapa que le ayuda a navegar por el código y a recordar lo que ha aprendido, y le muestra los pasos llevados a cabo para corregir el problema.  

## <a name="see-also"></a>Vea también  
 [Asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)   
 [Visualizar el código](../modeling/visualize-code.md)

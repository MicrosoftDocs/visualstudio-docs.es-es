---
title: "Usar mapas de c&#243;digo para depurar aplicaciones | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "mapas de código"
  - "asignación de relaciones de código"
  - "asignación de relaciones en el código"
  - "Visual Studio Ultimate, mapas de código"
  - "Visual Studio Ultimate, asignación de relaciones de código"
  - "Visual Studio Ultimate, navegar por el código visualmente"
  - "Visual Studio Ultimate, introducción al código"
  - "Visual Studio Ultimate, visualizar el código"
ms.assetid: 9fd0c9a2-d351-40c8-be88-0749788264bf
caps.latest.revision: 49
caps.handback.revision: 49
author: "alexhomer1"
ms.author: "ahomer"
manager: "douge"
---
# Usar mapas de c&#243;digo para depurar aplicaciones
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los mapas de código le ayudan a evitar bases de código de gran tamaño, código con el que no esté familiarizado o código heredado.  Por ejemplo, en la depuración, es posible que tenga que buscar en varios proyectos y archivos.  Use mapas de código para navegar por fragmentos de código y entender las relaciones entre ellos.  De este modo evitará tener que realizar un seguimiento mental de este código o dibujar un diagrama independiente.  Así, cuando interrumpa su trabajo, los mapas de código le ayudarán a recordar el código en el que está trabajando.  
  
 ![Mapa de código: Relaciones de mapa en el código](../modeling/media/codemapstoryboardpaint.png "CodeMapStoryboardPaint")  
  
 **Una flecha verde muestra la posición del cursor en el editor.**  
  
 Para obtener detalles de los comandos y las acciones que puede usar al trabajar con mapas de código, vea [Examinar y reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md).  
  
## Entender el problema  
 Supongamos que hay un error en un programa de dibujo en el que está trabajando.  Para reproducir el error, abra la solución en Visual Studio y presione **F5** para iniciar la depuración.  
  
 Cuando dibuje una línea y elija **Deshacer mi último trazo**, no sucederá nada hasta que se dibuje la línea siguiente.  
  
 ![Mapa de código: Error de reproducción](../modeling/media/codemapstoryboardpaint0.png "CodeMapStoryboardPaint0")  
  
 Por tanto, comienza la investigación buscando el método `Undo`.  Lo encuentra en la clase `PaintCanvas`.  
  
 ![Mapa de código: Buscar código](../modeling/media/codemapstoryboardpaint1.png "CodeMapStoryboardPaint1")  
  
## Empezar a asignar el código  
 Ahora comience la asignación del método `undo` y sus relaciones.  Desde el editor de código, agrega el método `undo` y los campos a los que se hace referencia a un nuevo mapa de código.  Cuando se crea un nuevo mapa, es posible que se tarde algo de tiempo en indizar el código.  Esto ayuda a que se ejecuten más rápido las operaciones posteriores.  
  
 ![Mapa de código: Mostrar el método y los campos relacionados](../modeling/media/codemapstoryboardpaint3.png "CodeMapStoryboardPaint3")  
  
> [!TIP]
>  El resaltado verde muestra los últimos elementos agregados al mapa.  La flecha verde muestra la posición del cursor en el código.  Las flechas entre los elementos representan diferentes relaciones.  Para más información sobre los elementos del mapa, pase el mouse sobre ellos y examine su información sobre herramientas.  
  
 ![Mapa de código: Mostrar informaciones sobre herramientas](../modeling/media/codemapstoryboardpaint4.png "CodeMapStoryboardPaint4")  
  
## Navegar y examinar código desde la asignación  
 Para consultar la definición de código de cada campo, haga doble clic en el campo del mapa o seleccione el campo y presione **F12**.  La flecha verde se desplaza entre los elementos del mapa.  El cursor del editor de código también se desplaza automáticamente.  
  
 ![Mapa de código: Examinar la definición de campo](../modeling/media/codemapstoryboardpaint5.png "CodeMapStoryboardPaint5")  
  
 ![Mapa de código: Examinar la definición de campo](../modeling/media/codemapstoryboardpaint5a.png "CodeMapStoryboardPaint5A")  
  
> [!TIP]
>  También puede mover la flecha verde en el mapa moviendo el cursor en el editor de código.  
  
## Entender las relaciones entre los elementos de código  
 Ahora desea saber qué otro código interactúa con los campos `history` y `paintObjects`.  Puede agregar todos los métodos que hacen referencia a estos campos al mapa.  Puede hacer esto desde el mapa o desde el editor de código.  
  
 ![Mapa de código: Buscar todas las referencias](../modeling/media/codemapstoryboardpaint6.png "CodeMapStoryboardPaint6")  
  
 ![Abrir un mapa de código desde el editor de código](../modeling/media/codemapstoryboardpaint6a.png "CodeMapStoryboardPaint6A")  
  
> [!NOTE]
>  Si agrega elementos de un proyecto que se comparte entre varias aplicaciones, como Windows Phone o la Tienda Windows, dichos elementos aparecen siempre en el mapa con el proyecto de aplicación activo actualmente.  Por lo tanto, si cambia el contexto a otro proyecto de aplicación, también cambia el contexto en el mapa para cualquier elemento recién agregado desde el proyecto compartido.  Las operaciones que se realizan con un elemento en el mapa solo se aplican a los elementos que comparten el mismo contexto.  
  
 Cambie el diseño para reorganizar el flujo de las relaciones y facilitar la lectura del mapa.  También puede mover los elementos por el mapa arrastrándolos.  
  
 ![Mapa de código: Cambiar el diseño](../modeling/media/codemapstoryboardpaint7a.png "CodeMapStoryboardPaint7A")  
  
> [!TIP]
>  De forma predeterminada, **Diseño incremental** está activado.  El mapa se reorganiza lo menos posible cuando se agregan nuevos elementos.  Para reorganizar el mapa completo cada vez que agregue nuevos elementos, desactive **Diseño incremental**.  
  
 ![Mapa de código: Cambiar el diseño](../modeling/media/codemapstoryboardpaint7.png "CodeMapStoryboardPaint7")  
  
 Examinemos estos métodos.  En el mapa, haga doble clic en el método **PaintCanvas** o seleccione este método y presione **F12**.  Verá que este método crea `history` y `paintObjects` como listas vacías.  
  
 ![Mapa de código: Examinar la definición de método](../modeling/media/codemapstoryboardpaint8.png "CodeMapStoryboardPaint8")  
  
 Ahora repita los mismos pasos para examinar la definición del método `clear`.  Verá que `clear` lleva a cabo algunas tareas con `paintObjects` e `history`.  A continuación, llama al método `Repaint`.  
  
 ![Mapa de código: Examinar la definición de método](../modeling/media/codemapstoryboardpaint9.png "CodeMapStoryboardPaint9")  
  
 Ahora, examine la definición del método `addPaintObject`.  También realiza algunas tareas con `history` y `paintObjects`.  También llama a `Repaint`.  
  
 ![Mapa de código: Examinar la definición de método](../modeling/media/codemapstoryboardpaint10.png "CodeMapStoryboardPaint10")  
  
## Buscar el problema examinando la asignación  
 Parece que todos los métodos que modifican `history` y `paintObjects` llaman a `Repaint`.  Con todo, el método `undo` no llama a `Repaint`, aunque `undo` modifica los mismos campos.  Por tanto, cree que puede corregir este problema mediante una llamada a `Repaint` desde `undo`.  
  
 ![Mapa de código: Buscar la llamada a método que falta](../modeling/media/codemapstoryboardpaint11.png "CodeMapStoryboardPaint11")  
  
 Si no tuviese un mapa para encontrar la llamada que falta, posiblemente sería más difícil localizar este problema, sobre todo con código más complejo.  
  
## Compartir la información y pasos siguientes  
 Antes de que usted u otro usuario corrija este error, puede hacer anotaciones en el mapa acerca del problema y de cómo corregirlo.  
  
 ![Mapa de código: Comentar y marcar elementos para el seguimiento](../modeling/media/codemapstoryboardpaint12.png "CodeMapStoryboardPaint12")  
  
 Por ejemplo, puede agregar comentarios al mapa y marcar los elementos con colores.  
  
 ![Mapa de código: Elementos comentados y marcados](../modeling/media/codemapstoryboardpaint12a.png "CodeMapStoryboardPaint12A")  
  
 Si tiene Microsoft Outlook instalado, puede enviar el mapa a otras personas por correo electrónico.  También puede exportar el mapa como imagen u otro formato.  
  
 ![Mapa de código: Compartir, exportar, enviar por correo](../modeling/media/codemapstoryboardpaint13.png "CodeMapStoryboardPaint13")  
  
## Corregir el problema y mostrar lo que hizo  
 Para corregir este error, agregue la llamada de `Repaint` a `undo`.  
  
 ![Mapa de código: Agregar la llamada a método que falta](../modeling/media/codemapstoryboardpaint14.png "CodeMapStoryboardPaint14")  
  
 Para confirmar la corrección, reinicie su sesión de depuración e intente reproducir el error.  Ahora, si elige **Deshacer mi último trazo** funciona como se esperaba y confirma que su corrección ha sido la adecuada.  
  
 ![Mapa de código: Confirmar la corrección del código](../modeling/media/codemapstoryboardpaint15.png "CodeMapStoryboardPaint15")  
  
 Puede actualizar el mapa para mostrar la corrección que realizó.  
  
 ![Mapa de código: Actualizar el mapa con la llamada a método que falta](../modeling/media/codemapstoryboardpaint16.png "CodeMapStoryboardPaint16")  
  
 El mapa muestra ahora un vínculo entre **deshacer** y **Volver a dibujar**.  
  
 ![Mapa de código: Mapa actualizado con la llamada a método](../modeling/media/codemapstoryboardpaint17.png "CodeMapStoryboardPaint17")  
  
> [!NOTE]
>  Cuando actualice el mapa, puede que vea un mensaje que indica que se ha actualizado el índice de código utilizado para crear el mapa.  Esto significa que alguien ha cambiado el código, lo que hace que el mapa no coincida con código actual.  Esto no detiene su actualización del mapa, pero podría tener que volver a crearlo para confirmar que coincide con el código.  
  
 Ahora ha terminado con la investigación.  Encontró y corrigió correctamente el problema asignando el código.  También tiene un mapa que le ayuda a navegar por el código y a recordar lo que ha aprendido, y le muestra los pasos llevados a cabo para corregir el problema.  
  
## Vea también  
 [Asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)   
 [Visualizar el código](../modeling/visualize-code.md)
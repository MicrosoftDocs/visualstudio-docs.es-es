---
title: Examinar y reorganizar mapas de código
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.dgmlgraph.layouthelp
- vs.progression.graphdocument
- vs.progression.dgmlgraph.message.notUlt.noexpandgroup
- vs.progression.colorsetpicker
- vs.progression.iconsetpicker
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code visualization [Visual Studio ALM]
- graph documents, browsing
- Visual Studio ALM, dependency graphs
- code visualization
- Visual Studio ALM, graph documents
- Visual Studio Ultimate, graph documents
- dependency graphs, browsing
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: cd9c431bdac6eb258084944bcff80c86e81796f0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042704"
---
# <a name="browse-and-rearrange-code-maps"></a>Examinar y reorganizar mapas de código

Reorganice los elementos en mapas de código para facilitar su lectura y mejorar su rendimiento.

Puede personalizar los mapas de código sin que ello afecte al código subyacente de una solución. Esto resulta útil si quiere centrarse en elementos de código clave o comunicar ideas sobre el código. Por ejemplo, para resaltar áreas interesantes, puede seleccionar elementos de código en el mapa y filtrarlos, cambiar el estilo de los elementos de código y los vínculos, ocultar o eliminar elementos de código y organizar los elementos de código mediante propiedades, categorías o grupos.

 **Requisitos**

-   Para crear mapas de código, es necesario tener Visual Studio Enterprise.

-   En Visual Studio Professional, puede ver mapas de código y realizar ediciones limitadas a los mapas de código.

##  <a name="ManageLargeGraphs"></a> Empezar a trabajar con mapas de código

Crear un mapa de código (consulte [asignar dependencias en sus soluciones](../modeling/map-dependencies-across-your-solutions.md) para obtener más detalles). Si no desea esperar el mapa termine de generar, haga clic en el **cancelar** vínculo en cualquier momento para detener el proceso de generación. Sin embargo, si lo hace, no podrá ver los detalles de todas las dependencias y vínculos.

Después de generar el mapa, siga primero estas sugerencias para revisar el código:

-   Observe los clústeres de dependencia naturales en el código. En la barra de herramientas del mapa, elija **diseño**, **clústeres rápidos**![botón clústeres rápidos en la barra de herramientas de gráfico](../modeling/media/quickclustersicon.gif). Consulte [cambiar el diseño del mapa](#Selecting).

     ![Gráfico de dependencias &#45; diseño clústeres rápidos](../modeling/media/dependencygraph_quickclusters.png)

-   Organice el mapa en áreas más pequeñas mediante la agrupación de los nodos relacionados. Contraiga esos grupos para ver solo las dependencias intergrupo, que aparecen automáticamente. Consulte [agrupar nodos](#OrganizeGroups).

-   Utilice los filtros para simplificar el mapa y centrarse en los tipos de nodos o vínculos que le interesen. Consulte [filtrar nodos y vínculos](#FilterNodes).

-   Obtenga el máximo rendimiento de los mapas grandes. Consulte [asignar dependencias en sus soluciones](../modeling/map-dependencies-across-your-solutions.md) para obtener más información. Por ejemplo, activar **Skip Build** por lo que Visual Studio no recompile la solución al actualizar los elementos del mapa de la barra de herramientas del mapa.

##  <a name="Selecting"></a> Cambiar el diseño del mapa

|**En**|**Siga estos pasos**|
|-|-|
|Organizar el flujo de dependencias de todo el mapa en una dirección concreta. Esto puede ayudarle a ver las capas de la arquitectura del código.|En la barra de herramientas del mapa, elija **diseño**y, a continuación:<br /><br /> -   **De arriba a abajo** ![botón gráfico de abajo arriba](../modeling/media/topbottomgraphbutton.gif)<br />-   **Orden descendente** ![inferior al botón del gráfico superior](../modeling/media/bottomtopgraphbutton.gif)<br />-   **De izquierda a derecha** ![deja al botón de diseño de la derecha](../modeling/media/leftrightgraphbutton.gif)<br />-   **De derecha a izquierda** ![directamente en el botón izquierdo del gráfico](../modeling/media/rightleftgraphbutton.gif)|
|Consultar los clústeres de dependencia naturales en el código con los nodos más dependientes en el centro de los clústeres y los nodos menos dependientes fuera de dichos clústeres.|En la barra de herramientas del mapa, elija **diseño**y, a continuación, **clústeres rápidos**![botón clústeres rápidos en la barra de herramientas de gráfico](../modeling/media/quickclustersicon.gif).|
|Seleccionar uno o más nodos en el mapa.|Haga clic en un nodo para seleccionarlo. Para seleccionar o anular la selección de varios nodos, mantenga **CTRL** mientras hace clic en.<br /><br /> Teclado: presione **ficha** o use las teclas de flecha para mover el rectángulo de foco punteado a un nodo y presione **espacio** para seleccionarlo. Presione **CTRL** + **espacio** realizar una selección múltiple o anule la selección de nodos.|
|Mover nodos específicos por el mapa.|Arrastre los nodos para moverlos. Para apartar otros nodos y vínculos apartan mientras arrastra nodos, mantenga presionada la **MAYÚS** clave.<br /><br /> Teclado: mantenga **CTRL** y presione las teclas de dirección.|
|Cambiar el diseño de un grupo independientemente del resto de nodos y grupos del mapa.|Seleccione un nodo y abra el menú contextual. Elija **diseño** y seleccione un estilo de diseño.<br /><br /> o bien<br /><br /> Seleccione un nodo y expándalo para mostrar los nodos secundarios. Haga clic en el título de nodo para mostrar la barra de herramientas emergente del grupo y abra el **cambiar el estilo de diseño del grupo**![gráfico de dependencias &#45; barra de herramientas del grupo &#45; diseño](../modeling/media/dependencygraph_grouptoolbar.gif) lista. Seleccione uno de los diseños de árbol, **clústeres rápidos**, o **vista de lista** (que organiza el contenido del grupo en una lista).<br /><br /> Consulte [agrupar nodos](#OrganizeGroups) para obtener más detalles.|
|Deshacer una acción en el mapa.|Presione **CTRL** + **Z** o usar Visual Studio **deshacer** comando.|

##  <a name="Explore"></a> Examinar el mapa

|**En**|**Siga estos pasos**|
|-|-|
|Examinar el mapa.|Arrastre el mapa en cualquier dirección con el mouse.<br /><br /> o bien<br /><br /> Mantenga **MAYÚS** y gire la rueda del mouse para desplazarse horizontalmente. Mantenga **MAYÚS** + **CTRL** y gire la rueda del mouse para desplazarse horizontalmente.|
|Acercar o alejar el mapa|Gire la rueda del mouse.<br /><br /> o bien<br /><br /> Use la **Zoom** lista desplegable en la barra de herramientas del mapa de código.<br /><br /> o bien<br /><br /> Utilice los métodos abreviados de teclado. Para acercar, presione **CTRL + MAYÚS +.** (punto). Para alejarla, presione **CTRL + MAYÚS +,** (coma).|
|Acercar en un área específica con el mouse.|Mantenga presionado el botón derecho del mouse mientras dibuja un rectángulo alrededor del área que le interesa.|
|Cambiar el tamaño del mapa y ajustarlo a la ventana.|Elija **Zoom para ajustar** desde el **Zoom** lista en la barra de herramientas del mapa de código.<br /><br /> o bien<br /><br /> Haga clic en el **ajustar al** icono ![icono de Zoom en la barra de herramientas del mapa](../modeling/media/almcodemapzoomicon.png) en la barra de herramientas del mapa de código. Teclado: presione **CTRL + 0** (cero).|
|Buscar un nodo en el mapa por su nombre. **Sugerencia:**  Esto solo funciona para los elementos del mapa. Para buscar elementos de la solución, pero no en el mapa, búsquelos en **el Explorador de soluciones**y después arrástrelos hasta el mapa. (Arrastre la selección, o en el **el Explorador de soluciones** barra de herramientas, haga clic en **mostrar en mapa de código**).|1.  Elija la **buscar** icono ![icono de búsqueda en la barra de herramientas del mapa](../modeling/media/almcodemapfindicon.png) en la barra de herramientas del mapa de código (teclado: presione **CTRL + F**) para mostrar el cuadro de búsqueda en la esquina superior derecha del mapa.<br />2.  Escriba el nombre del elemento y presione **devolver** o haga clic en el icono de "lupa". El primer elemento que coincide con la búsqueda aparece seleccionado en el mapa.<br />3.  Para personalizar la búsqueda, abra la lista desplegable y elija una opción de búsqueda. Las opciones son **Buscar siguiente**, **Buscar anterior**, y **seleccionar todo**. Después, haga clic en el botón correspondiente junto al cuadro de texto de búsqueda.<br />     ![Lista de opciones de búsqueda&#45;lista desplegable](../modeling/media/almcodemapssearchdropdown.png)<br />     Como alternativa, use el teclado: presione **F3** para seleccionar el siguiente nodo coincidente o **MAYÚS + F3** para seleccionar el nodo coincidente anterior.<br />4.  Para seleccionar una de las opciones que especifique cómo se deben gestionar los términos de búsqueda, haga clic en los iconos situados debajo del cuadro de texto de búsqueda.<br />     ![Opciones de coincidencia de búsqueda](../modeling/media/almcodemapssearchmatchicons.png)<br />     Las opciones son, de izquierda a derecha, coincidencia que distingue mayúsculas de minúsculas, solo palabras completas, uso de la sintaxis de expresiones regulares de .NET y expansión automática de grupos para mostrar las coincidencias con los elementos delimitados. **Importante:**  Se puede usar el cuadro de búsqueda para encontrar coincidencias en grupos contraídos solo si esos grupos se expandieron previamente. Para encontrar estas coincidencias y expandir los grupos primarios automáticamente, elija dicha opción en el cuadro de búsqueda.|
|Seleccionar los nodos no seleccionados.|Abra el menú contextual de los nodos seleccionados. Elija **seleccione**, **Invertir selección**.|
|Seleccionar nodos adicionales vinculados a los nodos seleccionados.|Abra el menú contextual de los nodos seleccionados. Elija **seleccione** y uno de los siguientes:<br /><br /> -Para seleccionar nodos adicionales vinculados directamente al nodo seleccionado, elija **dependencias entrantes**.<br />-Para seleccionar nodos adicionales vinculados directamente desde el nodo seleccionado, elija **dependencias salientes**.<br />-Para seleccionar nodos adicionales vinculados directamente hacia y desde el nodo seleccionado, elija **ambos**.<br />-Para seleccionar todos los nodos que se vinculan a y desde el nodo seleccionado, elija **subgráfico conectado**.<br />-Para seleccionar todos los elementos secundarios del nodo seleccionado, elija **hijos**.|

##  <a name="FilterNodes"></a> Filtrar nodos y vínculos

|**En**|**Siga estos pasos**|
|-|-|
|Mostrar u ocultar el panel Filtros.|Elija la **filtros** botón en la barra de herramientas del mapa de código. El **filtros** se muestra como una página con pestañas en el panel **el Explorador de soluciones**, de forma predeterminada.|
|Filtrar los tipos de nodos que se muestran en el mapa.|Active o desactive las casillas de verificación en la **elementos de código** lista en el panel filtros.|
|Filtrar los tipos de vínculos que se muestran en el mapa.|Active o desactive las casillas de verificación en la **relaciones** lista en el panel filtros.|
|Mostrar u ocultar los nodos de proyecto de prueba en el mapa.|Establecer o borrar el **activos de prueba** casilla de verificación en la **varios** lista en el panel filtros.|

Los iconos mostrados en el panel Leyenda del mapa reflejan la configuración establecida en la lista. Para mostrar u ocultar el panel leyenda, haga clic en el **leyenda** botón en la barra de herramientas del mapa de código.

##  <a name="Inspect"></a> Examinar nodos y vínculos

Los mapas de código muestran los siguientes tipos de vínculos:

-   Un vínculo individual representa una relación única entre dos nodos.

-   Un vínculo entre grupos representa una relación entre dos nodos de diferentes grupos.

-   Un vínculo agregado representa todas las relaciones que señalan la misma dirección entre dos grupos.

> [!TIP]
> De forma predeterminada, el mapa muestra los vínculos entre grupos solo para los nodos seleccionados. Para cambiar este comportamiento para mostrar u ocultar vínculos agregados entre grupos, haga clic en **diseño** en el código de barra de herramientas de mapa y elija **avanzadas**, a continuación, **mostrar todos los vínculos entre grupos** o **Ocultar todos los vínculos entre grupos**. Consulte [ocultar o mostrar nodos y vínculos](#HidingShowing) para obtener más detalles.

|**En**|**Siga estos pasos**|
|-|-|
|Ver más información sobre un nodo o un vínculo.|Mueva el puntero del mouse sobre el nodo o vínculo hasta que aparezca información sobre herramientas.<br /><br /> En la información sobre herramientas de un vínculo agregado se muestran las dependencias individuales que representa.<br /><br /> o bien<br /><br /> Abra el menú contextual del nodo o el vínculo. Elija **editar**, **propiedades**.|
|Mostrar u ocultar el contenido de un grupo.|-Para expandir un grupo, abra el menú contextual del nodo y elija **grupo**, **expandir**.<br />     o bien<br />     Mueva el puntero del mouse sobre el nodo hasta que aparezca el botón de contenido adicional (flecha hacia abajo). Haga clic en este botón para expandir el grupo. Teclado: para expandir o contraer el grupo seleccionado, presione el **PLUS** clave (**+**) o el **menos** clave (**-**).<br />-Para contraer un grupo, abra el menú contextual del nodo y elija **grupo**, **contraer**.<br />     o bien<br />     Mueva el puntero del mouse sobre un grupo hasta que aparezca el botón de contenido adicional (flecha hacia arriba). Haga clic en este botón para contraer el grupo.<br />-Para expandir todos los grupos, presione **CTRL** + **A** para seleccionar todos los nodos. Abra el menú contextual del mapa y elija **grupo**, **expandir**. **Nota:**      Este comando no está disponible si al expandir todos los grupos se producen problemas de memoria o se crea un mapa que no se puede usar. Se recomienda expandir el mapa solo al nivel de detalle que le interese.<br />-Para contraer todos los grupos, abra el menú contextual de un nodo o el mapa. Elija **grupo**, **Contraer todo**.|
|Ver la definición de código para un espacio de nombres, tipo o miembro.|Abra el menú contextual del nodo y elija **ir a definición**.<br /><br /> O bien<br /><br /> Haga doble clic en el nodo. Para los grupos expandidos, haga doble clic en el encabezado del grupo.<br /><br /> O bien<br /><br /> Seleccione el nodo y presione **F12**.<br /><br /> Por ejemplo:<br /><br /> -Para un espacio de nombres que contiene una clase, se abre el archivo de código para la clase para mostrar la definición de esa clase. En otros casos, el **resultados de la búsqueda de símbolos** ventana muestra una lista de archivos de código. **Nota:**      Al realizar esta tarea en un espacio de nombres de Visual Basic, no abra el archivo de código subyacente del espacio de nombres. Este problema también se produce al realizar esta tarea en un grupo de nodos seleccionados que incluyen un espacio de nombres de Visual Basic. Para evitar este problema, examine manualmente el archivo de código subyacente u omita el nodo del espacio de nombres de la selección.<br />-Para una clase o una clase parcial, se abre el archivo de código para esa clase para mostrar la definición de clase.<br />-Para un método, se abre el archivo de código de la clase primaria para mostrar la definición del método.|
|Examinar las dependencias y los elementos que participan en un vínculo agregado.|Seleccione los vínculos que le interesan y abra el menú contextual de la selección. Elija **mostrar vínculos de contribución** o **mostrar vínculos de contribución en el nuevo mapa de código**.<br /><br /> Visual Studio expande los grupos en ambos puntos de conexión del vínculo y muestra solo los elementos y dependencias que participan en el vínculo. **Nota:**  Cuando se examinan dependencias entre elementos en grupos parciales, podría observarse este comportamiento: <ul><li>Vínculos a elementos que no participan en el examen desaparecen del mapa, aunque esos vínculos todavía existan.</li><li>Suponga que examina un vínculo a un elemento en un grupo parcial y posteriormente examina otro vínculo al mismo elemento. Durante el segundo examen, el grupo parcial de destino muestra solo elementos del primer examen. Vínculos y elementos de destino que no participan en el primer examen pero participar en el segundo, no aparecen.</li></ul> Para ver los elementos de un grupo que faltan, elija **volver a obtener elementos secundarios**![volver a obtener elementos secundarios icono](../modeling/media/dependencygraph_deletednodesicon.png) (que indica que no todos los miembros de un grupo aparecen en el mapa). También puede intentar deshacer las acciones (teclado: presione **CTRL+Z**) y examinar las dependencias en un nuevo mapa.|
|Examinar las dependencias entre varios nodos de grupos diferentes.|Expanda los grupos de modo que pueda ver todos sus elementos secundarios. Seleccione todos los nodos que le interesen, incluidos sus elementos secundarios. En el mapa se muestran los vínculos entre grupos de los nodos seleccionados.<br /><br /> Para seleccionar todos los nodos de un grupo, mantenga presionada **MAYÚS** y el botón primario del mouse mientras dibuja un rectángulo alrededor de ese grupo. Para seleccionar todos los nodos en un mapa, presione **CTRL**+**A**. **Sugerencia:**  Para mostrar los vínculos entre grupos en todo momento, elija **diseño** en la barra de herramientas del mapa, **avanzadas**, **mostrar todos los vínculos entre grupos**.|
|Ver los elementos a los que un nodo o vínculo hace referencia.|Abra el menú contextual del nodo y elija **buscar todas las referencias**. **Nota:**  Esto solo se aplica cuando el atributo `Reference` se establece para el nodo o vínculo en el archivo .dgml del mapa. Para agregar referencias a elementos de los nodos o vínculos, consulte [Personalizar mapas de código mediante la edición de los archivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).|

##  <a name="HidingShowing"></a> Ocultar o mostrar nodos y vínculos

Al ocultar nodos, se evita que participen en algoritmos de diseño. De forma predeterminada, los vínculos entre grupos se ocultan. Los vínculos entre grupos son vínculos individuales que conectan nodos entre diferentes grupos. Cuando se contraen los grupos, el mapa agrega todos los vínculos entre grupos a los vínculos individuales que hay entre los grupos. Cuando se expande un grupo y se seleccionan los nodos que hay dentro de este, los vínculos entre grupos aparecen y muestran las dependencias que existen dentro de ese grupo.

> [!CAUTION]
> Antes de compartir un mapa creado en Visual Studio Enterprise con los usuarios de Visual Studio Professional, asegúrese de mostrar cualquier nodo o vínculo entre grupos que quiera que otros vean. De lo contrario, esos usuarios no podrán mostrar esos elementos.

### <a name="to-hide-or-show-nodes"></a>Para ocultar o mostrar nodos

|**En**|**Siga estos pasos**|
|-|-|
|Ocultar los nodos seleccionados.|1.  Seleccione los nodos que desea ocultar.<br />2.  Abra el menú contextual de los nodos seleccionados o del mapa. Elija **seleccione**, **ocultar seleccionada**.|
|Ocultar los nodos no seleccionados.|1.  Seleccione los nodos que quiere que permanezcan visibles.<br />2.  Abra el menú contextual de los nodos seleccionados o del mapa. Elija **seleccione**, **ocultar sin seleccionar**.|
|Mostrar los nodos ocultos.|-Para mostrar todos los nodos ocultos dentro de un grupo, primero asegúrese de que el grupo esté expandido. Abra el menú contextual y elija **seleccione**, **mostrar elementos secundarios**.<br />     o bien<br />     Haga clic en el **mostrar elementos secundarios**![Mostrar icono de elementos secundarios](../modeling/media/dependencygraph_filtericon_hiddennodes.gif) icono en la esquina superior izquierda del grupo (Esto solo está visible cuando hay nodos secundarios ocultos).<br />-Para mostrar todos los nodos ocultos, abra el menú contextual del mapa o un nodo y elija **seleccione**, **mostrar todo**.|

### <a name="to-hide-or-show-links"></a>Para ocultar o mostrar vínculos

|**En**|**En la barra de herramientas del mapa, elija el diseño, avanzada y, a continuación, elija**|
|-|-|
|Mostrar los vínculos entre grupos en todo momento.|**Mostrar todos los vínculos entre grupos**. De este modo, se ocultan los vínculos agregados entre grupos.|
|Ocultar los vínculos entre grupos en todo momento.|**Ocultar todos los vínculos entre grupos**|
|Mostrar solo los vínculos entre grupos de los nodos seleccionados.|**Mostrar vínculos entre grupos de los nodos seleccionados**|
|Ocultar todos los vínculos.|**Ocultar todos los vínculos**. Para volver a mostrar los vínculos, elija una de las opciones mencionadas anteriormente.|

##  <a name="OrganizeGroups"></a> Nodos de grupo

|**En**|**Siga estos pasos**|
|-|-|
|Mostrar los nodos contenedores como nodos de grupo o nodos de hoja.|Para mostrar los nodos contenedores como nodos de hoja: seleccione los nodos, abra el menú contextual de la selección y elija **grupo**, **convertir en hoja**.<br /><br /> Para mostrar los nodos contenedores como nodos de grupo: seleccione los nodos, abra el menú contextual de la selección y elija **grupo**, **convertir en grupo**.|
|Cambiar el diseño de un grupo.|Seleccione el grupo, abra el menú contextual, elija **diseño**y seleccione el estilo de diseño que desee.<br /><br /> o bien<br /><br /> 1.  Seleccione el grupo y asegúrese de que está expandido.<br />2.  Vuelva a hacer clic en el encabezado de grupo para que aparezca la barra de herramientas del grupo.<br />     ![Gráfico de dependencias &#45; barra de herramientas de grupo](../modeling/media/dependencygraph_group.png)<br />3.  Abra el **cambiar el estilo de diseño del grupo** lista ![gráfico de dependencias &#45; barra de herramientas del grupo &#45; diseño](../modeling/media/dependencygraph_grouptoolbar.gif) y elija el estilo de diseño que desee.<br /><br /> **Vista de lista** reorganiza los miembros del grupo en la lista. **Configuración predeterminada de gráfico** restablece el diseño del grupo en el diseño predeterminado del mapa. Para ver otras opciones, consulte [cambiar el diseño del mapa](#Selecting).|
|Agregar un nodo a un grupo.|Arrastre el nodo al grupo.<br /><br /> Mientras arrastra el nodo, Visual Studio muestra un indicador para señalar el movimiento del nodo.<br /><br /> También puede arrastrar nodos fuera de un grupo.|
|Agregar un nodo a un nodo sin grupo.|Arrastre el nodo hasta el nodo de destino. Puede convertir cualquier nodo de destino en un grupo mediante la adición de nodos.|
|Agrupar nodos seleccionados.|1.  Seleccione los nodos que desea agrupar. Aparece una barra de herramientas emergente por encima del último nodo seleccionado.<br />     ![Barra de herramientas de gráfico de dependencia](../modeling/media/depedencygraph_toolbar.png)<br />2.  En la barra de herramientas, elija el cuarto icono **agrupar los nodos seleccionados** (si el nodo está expandido tendrá cinco en lugar de cuatro iconos). Escriba el nombre del nuevo grupo y presione **devolver**.<br />     o bien<br />     Seleccione los nodos que quiere agrupar y abra el menú contextual de la selección. Elija **grupo**, **Agregar grupo primario**, escriba el nombre del nuevo grupo y presione **devolver**.<br /><br /> Puede cambiar el nombre de un grupo. Abra el menú contextual para el grupo y elija **editar**, **propiedades** para abrir la ventana Propiedades de Visual Studio. En el **etiqueta** propiedades, cambie el nombre del grupo según sea necesario.|
|Quitar grupos.|Seleccione el grupo o los grupos que desee quitar. Abra el menú contextual de la selección y elija **grupo**, **quitar grupo**.|
|Quitar los nodos del grupo primario.|Seleccione los nodos que desea mover. Abra el menú contextual de la selección y elija **grupo**, **quitar del elemento primario**. Esta acción quita los nodos hasta el grupo primario principal o fuera del grupo si no hay ningún grupo primario principal.<br /><br /> o bien<br /><br /> Seleccione los nodos y arrástrelos fuera del grupo.|

##  <a name="AddRemoveNodesLinks"></a> Agregar, quitar o cambiar el nombre de nodos, vínculos y comentarios

Puede mostrar más o menos elementos de un mapa con el fin de explorar en profundidad o simplificar el mapa. También puede cambiar el nombre de los elementos y agregar comentarios a los elementos.

> [!CAUTION]
> Antes de compartir un mapa creado mediante Visual Studio Enterprise con usuarios de Visual Professional, asegúrese de que los elementos de código que quiere que otros vean estén visibles en el mapa. De lo contrario, dichos usuarios no podrán recuperar los elementos de código eliminados.

### <a name="add-a-node-for-a-code-element"></a>Agregar un nodo para un elemento de código

|**En**|**Siga estos pasos**|
|-|-|
|Agregar un nuevo nodo genérico en la ubicación actual del puntero del mouse.|1.  Mueva el puntero del mouse al lugar en el mapa donde desea colocar el nuevo elemento de código y presione **insertar**.<br />     o bien<br />     Abra el menú contextual del mapa y elija **editar**, **agregar**, **nodo genérico**.<br />2.  Escriba el nombre del nuevo nodo y presione **devolver**.|
|Agregar un tipo específico de nodo de elemento de código en la ubicación actual del puntero del mouse.|1.  Mueva el puntero del mouse al lugar del mapa en el que quiere colocar el nuevo elemento de código y abra el menú contextual del mapa.<br />2.  Elija **editar**, **agregar**y seleccione el tipo de nodo que quiera.<br />3.  Escriba el nombre del nuevo nodo y presione **devolver**.|
|Agregar un tipo genérico o específico de nodo de elemento de código a un grupo.|1.  Seleccione el nodo de grupo y abra el menú contextual.<br />2.  Elija **editar**, **agregar**y seleccione el tipo de nodo que quiera.<br />3.  Escriba el nombre del nuevo nodo y presione **devolver**.|
|Agregar un nuevo nodo del mismo tipo que un nodo existente y que esté vinculado desde el mismo.|1.  Seleccione el elemento de código. Aparece una barra de herramientas emergente sobre él.<br />     ![Barra de herramientas de gráfico de dependencia](../modeling/media/depedencygraph_toolbar.png)<br />2.  En la barra de herramientas, elija el segundo icono **crear un nodo con la misma categoría que este nodo y agregar un nuevo vínculo a él**.<br />3.  Elija un lugar del mapa en el que colocar el nuevo elemento de código y haga clic en el botón primario del mouse.<br />4.  Escriba el nombre del nuevo nodo y presione **devolver**.|
|Agregar un nuevo nodo genérico que esté vinculado desde un elemento de código existente que tenga el foco.|1.  Con el teclado, presione **ficha** hasta que un vínculo desde el elemento de código tiene el foco (rectángulo punteado).<br />2.  Presione **Alt**+**insertar**.<br />3.  Escriba el nombre del nuevo nodo y presione **devolver**.|
|Agregar un nuevo nodo genérico que esté vinculado desde un elemento de código existente que tenga el foco.|1.  Con el teclado, presione **ficha** hasta que el elemento de código para vincular a tiene el foco (rectángulo punteado).<br />2.  Presione **Alt**+**MAYÚS**+**insertar**.<br />3.  Escriba el nombre del nuevo nodo y presione **devolver**.|

|**Para agregar elementos de código para**|**Siga estos pasos**|
|-|-|
|Elementos de código de la solución.|1.  Busque el elemento de código en **el Explorador de soluciones**. Use la **el Explorador de soluciones** cuadro de búsqueda o examinar la solución. **Sugerencia:**      Para buscar elementos de código que tienen dependencias en un tipo o miembro, abra el menú contextual para el tipo o miembro en **el Explorador de soluciones**. Elija la relación que le interese. **El Explorador de soluciones** muestra únicamente los elementos de código con las dependencias especificadas.<br />2.  Arrastre los elementos de código que le interesen a la superficie del mapa. También puede arrastrar elementos de código desde la Vista de clases o el Examinador de objetos.<br />     o bien<br />     En **el Explorador de soluciones**, seleccione los elementos de código que desea asignar. A continuación, en el **el Explorador de soluciones** barra de herramientas, haga clic en **mostrar en mapa de código**.<br /><br /> De forma predeterminada, la jerarquía de contenedores principales para los nuevos elementos de código se muestra en el mapa. Use la **incluir elementos primarios** botón en la barra de herramientas del mapa de código para cambiar este comportamiento. Al desactivarlo, solo se agrega al mapa el propio elemento de código. Para invertir este comportamiento para una sola arrastre y coloque la acción, mantenga presionada la **CTRL** mientras arrastra los elementos de código a la asignación de clave.<br /><br /> Visual Studio agrega elementos de código para los elementos de código de nivel superior en la selección. Para ver si un elemento de código contiene otros elementos de código, mueva el puntero del mouse sobre el elemento de código para que aparezca el botón de contenido adicional (flecha hacia abajo). Elija el botón de contenido adicional para expandir el elemento de código. Para expandir todos los elementos de código, presione **CTRL**+**A** para seleccionar todos los elementos, abra el menú contextual del mapa y elija **grupo**, **expandir** . Este comando no está disponible si el hecho de expandir todos los grupos generaría un mapa inusable o problemas de memoria insuficiente.|
|Elementos de código relacionados con elementos de código del mapa.|Haga clic en el **mostrar relacionados** situado en la barra de herramientas del mapa de código y elija el tipo de elementos relacionados que le interese.<br /><br /> o bien<br /><br /> Abra el menú contextual del elemento de código. Elija uno de los **mostrar...**  elementos del menú según el tipo de relación que le interese. Por ejemplo, puede ver los elementos a los que hace referencia el elemento actual, los elementos que hacen referencia al elemento actual, los tipos base y derivado para las clases, los llamadores de métodos y las clases, los nombres de espacios y los ensamblados.<br /><br /> Para obtener más información, consulte [en este tema](../modeling/map-dependencies-across-your-solutions.md).|
|Ensamblados .NET (.dll o .exe) o archivos binarios compilados.|Arrastre los ensamblados o archivos binarios desde fuera de Visual Studio a un mapa.<br /><br /> Solo puede arrastrar desde el Explorador de Windows o el Explorador de archivos si ejecuta tanto dichos exploradores como Visual Studio en el mismo nivel de permisos del Control de cuentas de usuario (UAC). Por ejemplo, si UAC está activado y está ejecutando Visual Studio como administrador, el Explorador de Windows o el Explorador de archivos bloquearán la operación de arrastre.|

###  <a name="AddNodes"></a>

#### <a name="add-a-link-between-existing-code-elements"></a>Para agregar un vínculo entre elementos de código existentes

1. Seleccione el elemento de código de origen. Aparece una barra de herramientas por encima del elemento de código.

    ![Barra de herramientas del gráfico de dependencia](../modeling/media/depedencygraph_toolbar.png)

2. En la barra de herramientas, elija el primer icono, **crear un nuevo vínculo desde este nodo a cualquier otro que se hace clic en siguiente**.

3. Seleccione el elemento de código de destino. Aparece un vínculo entre los dos elementos de código.

**O**

1. Seleccione el elemento de código de origen en el mapa.

2. Si ha instalado un mouse, mueva el puntero del mouse fuera de los límites del mapa.

3. Abra el menú contextual del elemento de código y elija **editar** > **agregar** > **vínculo genérico**.

4. Utilice el tabulador hasta el elemento de código de destino del vínculo y selecciónelo.

5. Presione **ENTRAR**.

###  <a name="AddComments"></a>

#### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Agregar un comentario a un nodo existente en el mapa

1.  Seleccione el elemento de código. Aparece una barra de herramientas sobre él.

     ![Barra de herramientas del gráfico de dependencia](../modeling/media/depedencygraph_toolbar.png)

2.  En la barra de herramientas, elija el tercer icono, **crear un nuevo nodo de comentario con un nuevo vínculo al nodo seleccionado**.

     \- o -

     Abra el menú contextual para el elemento de código y elija **editar** > **nuevo comentario**.

3.  Escriba sus comentarios. Para escribir en una nueva línea, presione **MAYÚS** + **ENTRAR**.

#### <a name="add-a-comment-to-the-map-itself"></a>Agregar un comentario al propio mapa

1.  Abra el menú contextual del mapa y elija **editar** > **nuevo comentario**.

2.  Escriba sus comentarios. Para escribir en una nueva línea, presione **MAYÚS** + **ENTRAR**.

###  <a name="RenameNodes"></a>

#### <a name="rename-a-code-element-or-link"></a>Cambiar el nombre de un elemento de código o vínculo

1.  Seleccione el elemento de código o el vínculo cuyo nombre quiere cambiar.

2.  Presione **F2**, o abra el menú contextual y elija **editar** > **cambiar el nombre**.

3.  Cuando el cuadro de edición aparece en el mapa, cambie el nombre del elemento de código o del vínculo.

**O**

1.  Abra el menú contextual y elija **editar** > **propiedades**.

2.  Editar el **etiqueta** propiedad en la ventana Propiedades de Visual Studio.

#### <a name="remove-a-code-element-or-link-from-the-map"></a>Quitar un elemento de código o vínculo del mapa

1.  Seleccione el elemento de código o vínculo y presione la **eliminar** clave.

     \- o -

     Abra el menú contextual para el elemento de código o vínculo y elija **editar** > **quitar**.

2.  Si el elemento o vínculo forma parte de un grupo, el **volver a obtener elementos secundarios** botón ![volver a obtener elementos secundarios icono](../modeling/media/dependencygraph_deletednodesicon.png) aparece dentro del grupo. Haga clic aquí para recuperar los elementos y vínculos que faltan.

-   Puede quitar los elementos de código y vínculos de un mapa sin que ello afecte al código subyacente. Al eliminarlos, sus definiciones se quitan del archivo DGML (.dgml).

-   Los mapas que se crean editando el DGML, agregando elementos de código sin definir o usando versiones anteriores de Visual Studio, no admiten esta funcionalidad.

#### <a name="flag-a-code-element-for-follow-up"></a>Marcar un elemento de código para su seguimiento

1.  Seleccione el elemento de código o el vínculo que quiera marcar para el seguimiento.

2.  Abra el menú contextual y elija **editar** > **marca de seguimiento**.

-   De forma predeterminada, el elemento de código adquiere un fondo de color rojo. Considere la posibilidad de [agregar un comentario](#AddComments) a él con la información de seguimiento adecuada.

-   Cambiar el color de fondo del elemento o borrar la marca de seguimiento eligiendo **editar** > **otros colores de marca**.

##  <a name="ChangeStyleCodeOrLink"></a> Cambiar el estilo de un elemento de código o vínculo

Puede cambiar los iconos de los elementos de código y los colores de los elementos de código y vínculos con el uso de iconos y colores predefinidos. Por ejemplo, puede elegir un color para resaltar los elementos de código y vínculos que tengan cierta categoría o propiedad. De este modo, podrá identificar áreas específicas del mapa y concentrarse en ellas. Puede especificar iconos personalizados y los colores editando el archivo del mapa .dgml; consulte [Personalizar mapas de código mediante la edición de los archivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Para aplicar un color o icono predefinido a los elementos de código o vínculos con cierta categoría o propiedad

1.  En la barra de herramientas del mapa, elija **leyenda**.

2.  En el **leyenda** cuadro, vea si la propiedad o categoría de elemento de código ya aparece en la lista.

3.  Si la lista no incluye la categoría o propiedad, elija **+** en el **leyenda** cuadro y luego elija **propiedad de nodo**, **categoría de nodo** , **Vincular propiedad**, o **vincular categoría**. Después, elija la propiedad o categoría. La categoría o propiedad aparece ahora en el **leyenda** cuadro.

    > [!NOTE]
    > Para crear y asignar una categoría o propiedad a un elemento de código, puede editar el archivo del mapa .dgml; consulte [Personalizar mapas de código mediante la edición de los archivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

4.  En el **leyenda** cuadro, haga clic en el icono situado junto a la categoría o propiedad agregada o que desee cambiar.

5.  Use la tabla siguiente para seleccionar el estilo que desea cambiar:

    |**Para cambiar el**|**Choose**|
    |-|-|
    |Color de fondo|**Fondo**|
    |Color del contorno|**Trazo**|
    |Color del texto (se muestra una letra "f" para mostrar el resultado)|**Foreground**|
    |Iconos|**Iconos**|

     El **selector de conjunto de colores** o **selector de conjunto de iconos** aparece el cuadro de diálogo para que seleccionar un color o icono.

6.  En el **selector de conjunto de colores** o **selector de conjunto de iconos** cuadro de diálogo, realice una de las siguientes acciones:

    |**Para aplicar un**|**Siga estos pasos**|
    |-|-|
    |Conjunto de colores o iconos|Abra el **seleccionar color** (o **icono**) **establecer** lista. Seleccione un conjunto de colores o de iconos.|
    |Color o icono específico|Abra la lista de valores de la categoría o propiedad. Seleccione un color o icono.|

    > [!NOTE]
    > Puede reorganizar, eliminar o desactivar temporalmente los estilos en el **leyenda** cuadro. Consulte [editar el cuadro leyenda](#ModifyLegend).

##  <a name="ModifyLegend"></a> Editar el cuadro leyenda

Puede reorganizar, eliminar o desactivar temporalmente los estilos en el **leyenda** cuadro:

1.  Abra el menú contextual para un estilo en el **leyenda** cuadro.

2.  Realice una de las tareas siguientes:

    |**En**|**Choose**|
    |-|-|
    |Desactivar el elemento de código|**deshabilitar**|
    |Eliminar el elemento de código|**Eliminar**|
    |Subir el estilo|**Mover hacia arriba**|
    |Bajar el elemento de código|**Mover hacia abajo**|

##  <a name="CopyLegend"></a> Copiar estilos de un mapa a otro

1.  Asegúrese de que el **leyenda** cuadro aparece en el mapa de origen. Si no está visible, en la barra de herramientas del mapa, haga clic en **leyenda**.

2.  Abra el menú contextual para el **leyenda** cuadro. Elija **copiar leyenda**.

3.  Pegue la leyenda en el mapa de destino.

##  <a name="MergeMaps"></a> Combinar mapas de código

Para combinar mapas, puede copiar y pegar elementos de código entre mapas. Si los identificadores de elemento de código coinciden, el pegado de elementos de código funciona como una operación de combinación. Para facilitar esta tarea, coloque todos los ensamblados o archivos binarios que quiere visualizar en la misma carpeta, de modo que la ruta de acceso completa de cada ensamblado o binario sea la misma para cada mapa que quiere combinar.

También puede arrastrar los ensamblados o archivos binarios al mismo mapa desde esa carpeta.

## <a name="see-also"></a>Vea también

- [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)
- [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)
- [Buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Personalizar mapas de código mediante la edición de los archivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [Referencia de Directed Graph Markup Language (DGML)](../modeling/directed-graph-markup-language-dgml-reference.md)

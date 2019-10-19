---
title: Examinar y reorganizar mapas de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
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
ms.assetid: 08f65f77-6ca7-4b25-b060-3f6c9f5847a4
caps.latest.revision: 91
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ecdfb91beb4d844216a9c961830af336e9de15a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672777"
---
# <a name="browse-and-rearrange-code-maps"></a>Examinar y reorganizar mapas de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Reorganice los elementos en mapas de código para facilitar su lectura y mejorar su rendimiento.

 Puede personalizar los mapas de código sin que ello afecte al código subyacente de una solución. Esto resulta útil si quiere centrarse en elementos de código clave o comunicar ideas sobre el código. Por ejemplo, para resaltar áreas interesantes, puede seleccionar elementos de código en el mapa y filtrarlos, cambiar el estilo de los elementos de código y los vínculos, ocultar o eliminar elementos de código y organizar los elementos de código mediante propiedades, categorías o grupos.

 **Requisitos**

- Para crear mapas de código, debe tener Visual Studio Enterprise.

- En Visual Studio Professional, puede ver mapas de código y realizar ediciones limitadas a los mapas de código.

## <a name="ManageLargeGraphs"></a>Introducción al uso de mapas de código
 Cree un mapa de código (consulte [asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md) para obtener más detalles). Si no desea esperar a que la asignación termine de generar, haga clic en el vínculo **Cancelar** en cualquier momento para detener el proceso de generación. Sin embargo, si lo hace, no podrá ver los detalles de todas las dependencias y vínculos.

 Después de generar el mapa, siga primero estas sugerencias para revisar el código:

- Observe los clústeres de dependencia naturales en el código. En la barra de herramientas del mapa, elija el botón **diseño** **, clústeres rápidos clústeres**![rápidos en la barra de herramientas del gráfico](../modeling/media/quickclustersicon.gif "QuickClustersIcon"). Vea [cambiar el diseño del mapa](#Selecting).

     ![Diseño de &#45; clústeres rápidos de gráfico de dependencias](../modeling/media/dependencygraph-quickclusters.png "DependencyGraph_QuickClusters")

- Organice el mapa en áreas más pequeñas mediante la agrupación de los nodos relacionados. Contraiga esos grupos para ver solo las dependencias intergrupo, que aparecen automáticamente. Vea [nodos de grupo](#OrganizeGroups).

- Utilice los filtros para simplificar el mapa y centrarse en los tipos de nodos o vínculos que le interesen. Vea [filtrar nodos y vínculos](#FilterNodes).

- Obtenga el máximo rendimiento de los mapas grandes. Consulte [asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md) para obtener más información. Por ejemplo, Active **omitir compilación** en la barra de herramientas del mapa para que Visual Studio no Recompile la solución al actualizar elementos en el mapa.

## <a name="Selecting"></a>Cambiar el diseño del mapa

|**En**|**Siga estos pasos**|
|------------|-----------------------------|
|Organizar el flujo de dependencias de todo el mapa en una dirección concreta. Esto puede ayudarle a ver las capas de la arquitectura del código.|En la barra de herramientas del mapa, elija **diseño**y, a continuación:<br /><br /> -    botón de la**parte superior a** la parte inferior del ![gráfico inferior](../modeling/media/topbottomgraphbutton.gif "TopBottomGraphButton")<br />-    botón de la parte**inferior** al superior del ![gráfico superior](../modeling/media/bottomtopgraphbutton.gif "BottomTopGraphButton")<br />-   **el botón de diseño de izquierda a** derecha ![a la derecha](../modeling/media/leftrightgraphbutton.gif "LeftRightGraphButton")<br />-   **derecha a izquierda** ![de derecha a izquierda botón](../modeling/media/rightleftgraphbutton.gif "RightLeftGraphButton")|
|Consultar los clústeres de dependencia naturales en el código con los nodos más dependientes en el centro de los clústeres y los nodos menos dependientes fuera de dichos clústeres.|En la barra de herramientas del mapa, elija **diseño**y **, a continuación, haga**clic en clústeres rápidos![botón clústeres rápidos en la barra de herramientas del gráfico](../modeling/media/quickclustersicon.gif "QuickClustersIcon").|
|Seleccionar uno o más nodos en el mapa.|Haga clic en un nodo para seleccionarlo. Para seleccionar o anular la selección de más de un nodo, mantenga presionada la **tecla Ctrl** mientras hace clic en él.<br /><br /> Teclado: Presione **Tab** o utilice las teclas de dirección para desplazar el rectángulo de foco de puntos a un nodo y presione la **barra espaciadora** para seleccionarlo. Presione **CTRL**  + **espacio** para seleccionar o anular la selección de los nodos.|
|Mover nodos específicos por el mapa.|Arrastre los nodos para moverlos. Para mover otros nodos y vínculos fuera del camino mientras arrastra nodos, mantenga presionada la tecla **MAYÚS** .<br /><br /> Teclado: mantenga presionada la **tecla Ctrl** y presione las teclas de dirección.|
|Cambiar el diseño de un grupo independientemente del resto de nodos y grupos del mapa.|Seleccione un nodo y abra el menú contextual. Elija **diseño** y seleccione un estilo de diseño.<br /><br /> O bien<br /><br /> Seleccione un nodo y expándalo para mostrar los nodos secundarios. Haga clic en la barra de herramientas emergente de título de nodo para mostrar grupo y abra la lista de diseño de la![barra &#45; de herramientas &#45; de grupo de gráfico de dependencias](../modeling/media/dependencygraph-grouptoolbar.gif "DependencyGraph_GroupToolbar") **de grupo**. Seleccione uno de los diseños de árbol, **clústeres rápidos**o **vista de lista** (que organiza el contenido del grupo en una lista).<br /><br /> Vea [nodos de grupo](#OrganizeGroups) para obtener más detalles.|
|Deshacer una acción en el mapa.|Presione **CTRL**  + **Z** o use el comando **Deshacer** de Visual Studio.|

## <a name="Explore"></a>Examinar el mapa

|**En**|**Siga estos pasos**|
|------------|-----------------------------|
|Examinar el mapa.|Arrastre el mapa en cualquier dirección con el mouse.<br /><br /> O bien<br /><br /> Mantenga presionada la **tecla Mayús** y gire la rueda del mouse para desplazarse horizontalmente. Mantenga presionada la tecla **mayús**  + **Ctrl** y gire la rueda del mouse para desplazarse horizontalmente.|
|Acercar o alejar el mapa|Gire la rueda del mouse.<br /><br /> O bien<br /><br /> Use la lista desplegable **zoom** en la barra de herramientas del mapa de código.<br /><br /> O bien<br /><br /> Utilice los métodos abreviados de teclado. Para acercar, presione **Ctrl + Mayús +.** (punto). Para alejar, presione **Ctrl + Mayús +,** (coma).|
|Acercar en un área específica con el mouse.|Mantenga presionado el botón derecho del mouse mientras dibuja un rectángulo alrededor del área que le interesa.|
|Cambiar el tamaño del mapa y ajustarlo a la ventana.|Elija **zoom para ajustarse** en la lista **zoom** de la barra de herramientas del mapa de código.<br /><br /> O bien<br /><br /> Haga clic en el icono zoom **para ajustar** icono ![de zoom en la barra de herramientas](../modeling/media/almcodemapzoomicon.png "ALMCodeMapZoomIcon") del mapa en la barra de herramientas del mapa de código. Teclado: Presione **Ctrl + 0** (cero).|
|Buscar un nodo en el mapa por su nombre. **Sugerencia:**  Esto solo funciona para los elementos del mapa. Para buscar elementos en la solución, pero no en el mapa, encontrarlos en **Explorador de soluciones**y, a continuación, arrástrelos al mapa. (Arrastre la selección o, en la barra de herramientas Explorador de soluciones, haga clic en **Mostrar en mapa de código**).|1. Elija el icono **Buscar** icono ![Buscar en la barra de herramientas de mapa](../modeling/media/almcodemapfindicon.png "ALMCodeMapFindIcon") de la barra de herramientas del mapa de código (teclado: Presione **Ctrl + F**) para mostrar el cuadro de búsqueda en la esquina superior derecha del mapa.<br />2. Escriba el nombre del elemento y presione **entrar** o haga clic en el icono del "ampliador". El primer elemento que coincide con la búsqueda aparece seleccionado en el mapa.<br />3. para personalizar la búsqueda, abra la lista desplegable y elija una opción de búsqueda. Las opciones son **siguiente**, **Buscar anterior**y **seleccionar todo**. Después, haga clic en el botón correspondiente junto al cuadro de texto de búsqueda.<br />     ![Lista desplegable&#45;de opciones de búsqueda](../modeling/media/almcodemapssearchdropdown.png "ALMCodeMapsSearchDropDown")<br />     También puede usar el teclado: Presione **F3** para seleccionar el siguiente nodo coincidente o **MAYÚS + F3** para seleccionar el nodo coincidente anterior.<br />4. Seleccione cualquiera de las opciones que especifican cómo se administran los términos de búsqueda; para ello, haga clic en los iconos situados debajo del cuadro de texto de búsqueda.<br />     ![Opciones de coincidencia de búsqueda](../modeling/media/almcodemapssearchmatchicons.png "ALMCodeMapsSearchMatchIcons")<br />     Las opciones son, de izquierda a derecha, coincidencia que distingue mayúsculas de minúsculas, solo palabras completas, uso de la sintaxis de expresiones regulares de .NET y expansión automática de grupos para mostrar las coincidencias con los elementos delimitados. **Importante:**  Puede usar el cuadro de búsqueda para buscar coincidencias en grupos contraídos solo si esos grupos se han expandido anteriormente. Para encontrar estas coincidencias y expandir los grupos primarios automáticamente, elija dicha opción en el cuadro de búsqueda.|
|Seleccionar los nodos no seleccionados.|Abra el menú contextual de los nodos seleccionados. Elija **seleccionar**, **invertir selección**.|
|Seleccionar nodos adicionales vinculados a los nodos seleccionados.|Abra el menú contextual de los nodos seleccionados. Elija **seleccionar** y uno de los siguientes:<br /><br /> -Para seleccionar nodos adicionales vinculados directamente al nodo seleccionado, elija **dependencias de entrada**.<br />-Para seleccionar nodos adicionales que se vinculan directamente desde el nodo seleccionado, elija **dependencias salientes**.<br />-Para seleccionar nodos adicionales vinculados directamente hacia y desde el nodo seleccionado, elija **ambos**.<br />-Para seleccionar todos los nodos vinculados y desde el nodo seleccionado, elija **subgráfico conectado**.<br />-Para seleccionar todos los elementos secundarios del nodo seleccionado, elija **secundarios**.|

## <a name="FilterNodes"></a>Filtrar nodos y vínculos

|**En**|**Siga estos pasos**|
|------------|-----------------------------|
|Mostrar u ocultar el panel Filtros.|Elija el botón **filtros** en la barra de herramientas del mapa de código. El panel Filtros se muestra como una página con pestañas en la ventana del Explorador de soluciones de forma predeterminada.|
|Filtrar los tipos de nodos que se muestran en el mapa.|Active o desactive las casillas de la lista **elementos de código** en el panel filtros.|
|Filtrar los tipos de vínculos que se muestran en el mapa.|Active o desactive las casillas de la lista **relaciones** en el panel filtros.|
|Mostrar u ocultar los nodos de proyecto de prueba en el mapa.|Establezca o desactive la casilla **activos de prueba** en la lista **varios** del panel filtros.|

 Los iconos mostrados en el panel Leyenda del mapa reflejan la configuración establecida en la lista. Para mostrar u ocultar el panel leyenda, haga clic en el botón **leyenda** de la barra de herramientas del mapa de código.

## <a name="Inspect"></a>Examinar nodos y vínculos
 Los mapas de código muestran los siguientes tipos de vínculos:

- Un vínculo individual representa una relación única entre dos nodos.

- Un vínculo entre grupos representa una relación entre dos nodos de diferentes grupos.

- Un vínculo agregado representa todas las relaciones que señalan la misma dirección entre dos grupos.

> [!TIP]
> De forma predeterminada, el mapa muestra los vínculos entre grupos solo para los nodos seleccionados. Para cambiar este comportamiento y mostrar u ocultar los vínculos agregados entre grupos, haga clic en **diseño** en la barra de herramientas del mapa de código y elija **Opciones avanzadas**y, a continuación, **Mostrar todos los vínculos entre grupos** u **ocultar todos los vínculos entre grupos**. Consulte [ocultar o mostrar nodos y vínculos](#HidingShowing) para obtener más detalles.

|**En**|**Siga estos pasos**|
|------------|-----------------------------|
|Ver más información sobre un nodo o un vínculo.|Mueva el puntero del mouse sobre el nodo o vínculo hasta que aparezca información sobre herramientas.<br /><br /> En la información sobre herramientas de un vínculo agregado se muestran las dependencias individuales que representa.<br /><br /> O bien<br /><br /> Abra el menú contextual del nodo o el vínculo. Elija **Editar**, **propiedades**.|
|Mostrar u ocultar el contenido de un grupo.|-Para expandir un grupo, abra el menú contextual del nodo y elija **Grupo**, **expandir**.<br />     O bien<br />     Mueva el puntero del mouse sobre el nodo hasta que aparezca el botón de contenido adicional (flecha hacia abajo). Haga clic en este botón para expandir el grupo. Teclado: para expandir o contraer el grupo seleccionado, presione la tecla **más** ( **+** ) o la tecla **menos** ( **-** ).<br />-Para contraer un grupo, abra el menú contextual del nodo y elija **Grupo**, **contraer**.<br />     O bien<br />     Mueva el puntero del mouse sobre un grupo hasta que aparezca el botón de contenido adicional (flecha hacia arriba). Haga clic en este botón para contraer el grupo.<br />-Para expandir todos los grupos, presione Ctrl ** +  a** para seleccionar todos los nodos. Abra el menú contextual del mapa y elija **Grupo**, **expandir**. **Nota:**      Este comando no está disponible si al expandir todos los grupos se genera una asignación inutilizable o problemas de memoria. Se recomienda expandir el mapa solo al nivel de detalle que le interese.<br />-Para contraer todos los grupos, abra el menú contextual de un nodo o del mapa. Elija **Grupo**, **contraer todo**.|
|Ver la definición de código para un espacio de nombres, tipo o miembro.|Abra el menú contextual del nodo y elija **ir a definición**.<br /><br /> o bien<br /><br /> Haga doble clic en el nodo. Para los grupos expandidos, haga doble clic en el encabezado del grupo.<br /><br /> o bien<br /><br /> Seleccione el nodo y presione **F12**.<br /><br /> Por ejemplo:<br /><br /> -Para un espacio de nombres que contiene una clase, se abre el archivo de código de la clase para mostrar la definición de esa clase. En otros casos, en la ventana Resultados de la **búsqueda de símbolos** se muestra una lista de archivos de código. **Nota:**      Al realizar esta tarea en un espacio de nombres de Visual Basic .NET, el archivo de código subyacente del espacio de nombres no se abre. Este problema también se produce cuando se efectúa esta tarea en un grupo de nodos seleccionados que incluyen un espacio de nombres de Visual Basic .NET. Para evitar este problema, examine manualmente el archivo de código subyacente u omita el nodo del espacio de nombres de la selección.<br />-Para una clase o una clase parcial, el archivo de código de esa clase se abre para mostrar la definición de clase.<br />-Para un método, se abre el archivo de código de la clase primaria para mostrar la definición del método.|
|Examinar las dependencias y los elementos que participan en un vínculo agregado.|Seleccione los vínculos que le interesan y abra el menú contextual de la selección. Elija **Mostrar vínculos de contribución** o **Mostrar vínculos de contribución en el nuevo mapa de código**.<br /><br /> Visual Studio expande los grupos en ambos extremos del vínculo y muestra solo los elementos y dependencias que participan en el vínculo. **Nota:**  Al examinar las dependencias entre los elementos de grupos parciales, es posible que vea este comportamiento: <ul><li>Los vínculos a los elementos que no participan en el examen desaparecen del mapa, aunque esos vínculos todavía existan.</li><li>Suponga que examina un vínculo a un elemento en un grupo parcial y posteriormente examina otro vínculo al mismo elemento. Durante el segundo examen, el grupo parcial de destino muestra solo elementos del primer examen. Los vínculos y los elementos de destino que no participaron en el primer examen, pero lo hacen en el segundo, no aparecen.</li></ul> Para ver los elementos que faltan de un grupo, elija volver a **obtener**el icono de elementos secundarios volver a![capturar](../modeling/media/dependencygraph-deletednodesicon.png "DependencyGraph_DeletedNodesIcon") secundarios (que indica que no todos los miembros de un grupo aparecen en el mapa). También puede intentar deshacer las acciones (teclado: Presione **Ctrl + Z**) y examinar las dependencias en un nuevo mapa.|
|Examinar las dependencias entre varios nodos de grupos diferentes.|Expanda los grupos de modo que pueda ver todos sus elementos secundarios. Seleccione todos los nodos que le interesen, incluidos sus elementos secundarios. En el mapa se muestran los vínculos entre grupos de los nodos seleccionados.<br /><br /> Para seleccionar todos los nodos de un grupo, mantenga presionada la **tecla Mayús** y el botón primario del mouse mientras dibuja un rectángulo alrededor de ese grupo. Para seleccionar todos los nodos de un mapa, presione **CTRL** +**a**. **Sugerencia:**  Para mostrar los vínculos entre grupos en todo momento, elija **diseño** en la barra de herramientas del mapa, **avanzado**, **Mostrar todos los vínculos entre grupos**.|
|Ver los elementos a los que un nodo o vínculo hace referencia.|Abra el menú contextual del nodo y elija **Buscar todas las referencias**. **Nota:**  Esto solo se aplica cuando se establece el atributo `Reference` para el nodo o vínculo en el archivo. DGML del mapa. Para agregar referencias a los elementos de los nodos o vínculos, vea [personalizar mapas de código mediante la edición de los archivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).|

## <a name="HidingShowing"></a>Ocultar o mostrar nodos y vínculos
 Al ocultar nodos, se evita que participen en algoritmos de diseño. De forma predeterminada, los vínculos entre grupos se ocultan. Los vínculos entre grupos son vínculos individuales que conectan nodos entre diferentes grupos. Cuando se contraen los grupos, el mapa agrega todos los vínculos entre grupos a los vínculos individuales que hay entre los grupos. Cuando se expande un grupo y se seleccionan los nodos que hay dentro de este, los vínculos entre grupos aparecen y muestran las dependencias que existen dentro de ese grupo.

> [!CAUTION]
> Antes de compartir un mapa creado en Visual Studio Enterprise con los usuarios de Visual Studio Professional, asegúrese de mostrar cualquier nodo o vínculo entre grupos que quiera que otros vean. De lo contrario, esos usuarios no podrán mostrar esos elementos.

### <a name="to-hide-or-show-nodes"></a>Para ocultar o mostrar nodos

|**En**|**Siga estos pasos**|
|------------|-----------------------------|
|Ocultar los nodos seleccionados.|1. Seleccione los nodos que desea ocultar.<br />2. Abra el menú contextual de los nodos seleccionados o del mapa. Elija **seleccionar**, **Ocultar selección**.|
|Ocultar los nodos no seleccionados.|1. Seleccione los nodos que desea que permanezcan visibles.<br />2. Abra el menú contextual de los nodos seleccionados o del mapa. Elija **seleccionar**, **ocultar no seleccionado**.|
|Mostrar los nodos ocultos.|-Para mostrar todos los nodos ocultos dentro de un grupo, asegúrese primero de que el grupo esté expandido. Abra el menú contextual y elija **seleccionar**y **Mostrar elementos secundarios**.<br />     O bien<br />     Haga clic en![el icono de mostrar los elementos secundarios](../modeling/media/dependencygraph-filtericon-hiddennodes.gif "DependencyGraph_FilterIcon_HiddenNodes ") IC **ocultar hijos**en la esquina superior izquierda del grupo (esto solo es visible cuando hay nodos secundarios ocultos).<br />-Para mostrar todos los nodos ocultos, abra el menú contextual para el mapa o un nodo y elija **seleccionar**, **Mostrar todo**.|

### <a name="to-hide-or-show-links"></a>Para ocultar o mostrar vínculos

|**En**|**En la barra de herramientas del mapa, elija diseño, opciones avanzadas y, a continuación, elija**|
|------------|----------------------------------------------------------------------|
|Mostrar los vínculos entre grupos en todo momento.|**Mostrar todos los vínculos entre grupos**. De este modo, se ocultan los vínculos agregados entre grupos.|
|Ocultar los vínculos entre grupos en todo momento.|**Ocultar todos los vínculos entre grupos**|
|Mostrar solo los vínculos entre grupos de los nodos seleccionados.|**Mostrar vínculos entre grupos en los nodos seleccionados**|
|Ocultar todos los vínculos.|**Ocultar todos los vínculos**. Para volver a mostrar los vínculos, elija una de las opciones mencionadas anteriormente.|

## <a name="OrganizeGroups"></a>Agrupar nodos

|**En**|**Siga estos pasos**|
|------------|-----------------------------|
|Mostrar los nodos contenedores como nodos de grupo o nodos de hoja.|Para mostrar los nodos contenedores como nodos hoja: seleccione los nodos, abra el menú contextual de la selección y elija **Grupo**, **convertir en hoja**.<br /><br /> Para mostrar los nodos contenedores como nodos de Grupo: seleccione los nodos, abra el menú contextual de la selección y elija **Grupo**, **convertir en grupo**.|
|Cambiar el diseño de un grupo.|Seleccione el grupo, abra el menú contextual, elija **diseño**y, a continuación, seleccione el estilo de diseño que desee.<br /><br /> O bien<br /><br /> 1. Seleccione el grupo y asegúrese de que está expandido.<br />2. Vuelva a hacer clic en el encabezado de grupo y aparecerá la barra de herramientas del grupo.<br />     ![Barra de &#45; herramientas de grupo de gráfico de dependencias](../modeling/media/dependencygraph-group.png "DependencyGraph_Group")<br />3. Abra el diseño de la barra **de herramientas** ![ &#45; &#45; ](../modeling/media/dependencygraph-grouptoolbar.gif "DependencyGraph_GroupToolbar") cambiar el estilo de diseño del grupo de gráfico de dependencias lista de grupos y elija el estilo de diseño que desee.<br /><br /> La **vista de lista** reorganiza los miembros del grupo en la lista. El **valor predeterminado del gráfico** restablece el diseño del grupo en el diseño predeterminado del mapa. Para ver otras opciones, consulte [cambiar el diseño del mapa](#Selecting).|
|Agregar un nodo a un grupo.|Arrastre el nodo al grupo.<br /><br /> Mientras arrastra el nodo, Visual Studio muestra un indicador para señalar el movimiento del nodo.<br /><br /> También puede arrastrar nodos fuera de un grupo.|
|Agregar un nodo a un nodo sin grupo.|Arrastre el nodo hasta el nodo de destino. Puede convertir cualquier nodo de destino en un grupo mediante la adición de nodos.|
|Agrupar nodos seleccionados.|1. Seleccione los nodos que desea agrupar. Aparece una barra de herramientas emergente por encima del último nodo seleccionado.<br />     ![Barra de herramientas de gráfico de dependencias](../modeling/media/depedencygraph-toolbar.png "DepedencyGraph_Toolbar")<br />2. en la barra de herramientas, elija el cuarto icono **agrupar los nodos seleccionados** (si el nodo está expandido, tendrá cinco iconos en lugar de cuatro). Escriba el nombre del nuevo grupo y presione **entrar**.<br />     O bien<br />     Seleccione los nodos que quiere agrupar y abra el menú contextual de la selección. Elija **Grupo**, **Agregar grupo primario**, escriba el nombre del nuevo grupo y presione **entrar**.<br /><br /> Puede cambiar el nombre de un grupo. Abra el menú contextual del grupo y elija **Editar**, **propiedades** para abrir el ventana Propiedades de Visual Studio. En la propiedad **Label** , cambie el nombre del grupo según sea necesario.|
|Quitar grupos.|Seleccione el grupo o los grupos que desee quitar. Abra el menú contextual de la selección y elija **Grupo**, **quitar grupo**.|
|Quitar los nodos del grupo primario.|Seleccione los nodos que desea mover. Abra el menú contextual de la selección y elija **Grupo**, **quitar del elemento primario**. Esta acción quita los nodos hasta el grupo primario principal o fuera del grupo si no hay ningún grupo primario principal.<br /><br /> O bien<br /><br /> Seleccione los nodos y arrástrelos fuera del grupo.|

## <a name="AddRemoveNodesLinks"></a>Agregar, quitar o cambiar el nombre de nodos, vínculos y comentarios
 Puede mostrar más o menos elementos de un mapa con el fin de explorar en profundidad o simplificar el mapa. También puede cambiar el nombre de los elementos y agregar comentarios a los elementos.

> [!CAUTION]
> Antes de compartir un mapa creado mediante Visual Studio Enterprise con usuarios de Visual Professional, asegúrese de que los elementos de código que quiere que otros vean estén visibles en el mapa. De lo contrario, dichos usuarios no podrán recuperar los elementos de código eliminados.

### <a name="add-a-node-for-a-code-element"></a>Agregar un nodo para un elemento de código

|**En**|**Siga estos pasos**|
|------------|-----------------------------|
|Agregar un nuevo nodo genérico en la ubicación actual del puntero del mouse.|1. Mueva el puntero del mouse al lugar del mapa en el que desea colocar el nuevo elemento de código y presione **Insertar**.<br />     O bien<br />     Abra el menú contextual del mapa y elija **Editar**, **Agregar**, **nodo genérico**.<br />2. Escriba el nombre del nuevo nodo y presione **entrar**.|
|Agregar un tipo específico de nodo de elemento de código en la ubicación actual del puntero del mouse.|1. Mueva el puntero del mouse al lugar del mapa en el que desea colocar el nuevo elemento de código y abra el menú contextual del mapa.<br />2. elija **Editar**, **Agregar**y seleccione el tipo de nodo que desee.<br />3. Escriba el nombre del nuevo nodo y presione **entrar**.|
|Agregar un tipo genérico o específico de nodo de elemento de código a un grupo.|1. Seleccione el nodo grupo y abra el menú contextual.<br />2. elija **Editar**, **Agregar**y seleccione el tipo de nodo que desee.<br />3. Escriba el nombre del nuevo nodo y presione **entrar**.|
|Agregar un nuevo nodo del mismo tipo que un nodo existente y que esté vinculado desde el mismo.|1. Seleccione el elemento de código. Aparece una barra de herramientas emergente sobre él.<br />     ![Barra de herramientas de gráfico de dependencias](../modeling/media/depedencygraph-toolbar.png "DepedencyGraph_Toolbar")<br />2. en la barra de herramientas, elija el segundo icono **crear un nodo con la misma categoría que este nodo y agregarle un nuevo vínculo**.<br />3. Elija un lugar en el mapa para colocar el nuevo elemento de código y haga clic en el botón primario del mouse.<br />4. Escriba el nombre del nuevo nodo y presione **entrar**.|
|Agregar un nuevo nodo genérico que esté vinculado desde un elemento de código existente que tenga el foco.|1. con el teclado, presione **Tab** hasta que el elemento de código que se va a vincular tenga el foco (rectángulo punteado).<br />2. Presione **Alt** +**Insertar**.<br />3. Escriba el nombre del nuevo nodo y presione **entrar**.|
|Agregar un nuevo nodo genérico que esté vinculado desde un elemento de código existente que tenga el foco.|1. con el teclado, presione **Tab** hasta que el elemento de código al que desea vincular tenga el foco (rectángulo punteado).<br />2. Presione **Alt** +**MAYÚS** +**Insertar**.<br />3. Escriba el nombre del nuevo nodo y presione **entrar**.|

|**Para agregar elementos de código para**|**Siga estos pasos**|
|----------------------------------|-----------------------------|
|Elementos de código de la solución.|1. Busque el elemento de código en **Explorador de soluciones**. Use el cuadro de búsqueda **Explorador de soluciones** o examine la solución. **Sugerencia:**      Para buscar elementos de código que tengan dependencias en un tipo o miembro, abra el menú contextual del tipo o miembro en **Explorador de soluciones**. Elija la relación que le interese. **Explorador de soluciones** muestra solo los elementos de código con las dependencias especificadas.<br />2. arrastre los elementos de código que le interesen a la superficie del mapa. También puede arrastrar elementos de código desde la Vista de clases o el Examinador de objetos.<br />     O bien<br />     En **Explorador de soluciones**, seleccione los elementos de código que desea asignar. A continuación, en la barra de herramientas **Explorador de soluciones** , haga clic en **Mostrar en mapa de código**.<br /><br /> De forma predeterminada, la jerarquía de contenedores principales para los nuevos elementos de código se muestra en el mapa. Use el botón **incluir elementos primarios** de la barra de herramientas del mapa de código para cambiar este comportamiento. Al desactivarlo, solo se agrega al mapa el propio elemento de código. Para invertir este comportamiento solo para una acción de arrastrar y colocar, mantenga presionada la tecla **Ctrl** mientras arrastra los elementos de código al mapa.<br /><br /> Visual Studio agrega elementos de código para los elementos de código de nivel superior en la selección. Para ver si un elemento de código contiene otros elementos de código, mueva el puntero del mouse sobre el elemento de código para que aparezca el botón de contenido adicional (flecha hacia abajo). Elija el botón de contenido adicional para expandir el elemento de código. Para expandir todos los elementos de código, presione **CTRL** **+ a** para seleccionar todos los elementos, abra el menú contextual del mapa y elija **Grupo**, **expandir**. Este comando no está disponible si el hecho de expandir todos los grupos generaría un mapa inusable o problemas de memoria insuficiente.|
|Elementos de código relacionados con elementos de código del mapa.|Haga clic en el botón **Mostrar relacionados** en la barra de herramientas del mapa de código y elija el tipo de elementos relacionados que le interesen.<br /><br /> O bien<br /><br /> Abra el menú contextual del elemento de código. Elija una **de las** elementos del menú en función del tipo de relación que le interese. Por ejemplo, puede ver los elementos a los que hace referencia el elemento actual, los elementos que hacen referencia al elemento actual, los tipos base y derivado para las clases, los llamadores de métodos y las clases, los nombres de espacios y los ensamblados.<br /><br /> Para obtener más información, consulte [este tema](../modeling/map-dependencies-across-your-solutions.md).|
|Ensamblados .NET (.dll o .exe) o archivos binarios compilados.|Arrastre los ensamblados o archivos binarios desde fuera de Visual Studio a un mapa.<br /><br /> Solo puede arrastrar desde el Explorador de Windows o el Explorador de archivos si ejecuta tanto dichos exploradores como Visual Studio en el mismo nivel de permisos del Control de cuentas de usuario (UAC). Por ejemplo, si UAC está activado y está ejecutando Visual Studio como administrador, el Explorador de Windows o el Explorador de archivos bloquearán la operación de arrastre.|

### <a name="AddNodes"></a>
##### <a name="add-a-link-between-existing-code-elements"></a>Para agregar un vínculo entre elementos de código existentes

1. Seleccione el elemento de código de origen. Aparece una barra de herramientas por encima del elemento de código.

    ![Barra de herramientas de gráfico de dependencias](../modeling/media/depedencygraph-toolbar.png "DepedencyGraph_Toolbar")

2. En la barra de herramientas, elija el primer icono, **crear nuevo vínculo desde este nodo a cada nodo en el que haga clic en siguiente**.

3. Seleccione el elemento de código de destino. Aparece un vínculo entre los dos elementos de código.

   \- o -

4. Seleccione el elemento de código de origen en el mapa.

5. Si ha instalado un mouse, mueva el puntero del mouse fuera de los límites del mapa.

6. Abra el menú contextual del elemento de código y elija **Editar**, **Agregar**, **vínculo genérico**.

7. Utilice el tabulador hasta el elemento de código de destino del vínculo y selecciónelo.

8. Presione **RETORNO**.

### <a name="AddComments"></a>
##### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Agregar un comentario a un nodo existente en el mapa

1. Seleccione el elemento de código. Aparece una barra de herramientas sobre él.

     ![Barra de herramientas de gráfico de dependencias](../modeling/media/depedencygraph-toolbar.png "DepedencyGraph_Toolbar")

2. En la barra de herramientas, elija el tercer icono, **cree un nuevo nodo de comentario con un nuevo vínculo al nodo seleccionado**.

     \- o -

     Abra el menú contextual del elemento de código y elija **Editar**, **nuevo comentario**.

3. Escriba sus comentarios. Para escribir en una nueva línea, presione **mayús**  + **retorno**.

##### <a name="add-a-comment-to-the-map-itself"></a>Agregar un comentario al propio mapa

1. Abra el menú contextual del mapa y elija **Editar**, **nuevo comentario**.

2. Escriba sus comentarios. Para escribir en una nueva línea, presione **mayús**  + **retorno**.

### <a name="RenameNodes"></a>
##### <a name="rename-a-code-element-or-link"></a>Cambiar el nombre de un elemento de código o vínculo

1. Seleccione el elemento de código o el vínculo cuyo nombre quiere cambiar.

2. Presione **F2**o abra el menú contextual y elija **Editar**, **cambiar nombre**.

3. Cuando el cuadro de edición aparece en el mapa, cambie el nombre del elemento de código o del vínculo.

     \- o -

4. Abra el menú contextual y elija **Editar**, **propiedades**.

5. Edite la propiedad **Label** en el ventana Propiedades de Visual Studio.

##### <a name="remove-a-code-element-or-link-from-the-map"></a>Quitar un elemento de código o vínculo del mapa

1. Seleccione el elemento de código o el vínculo y presione la tecla **Supr** .

     \- o -

     Abra el menú contextual del elemento de código o vínculo y elija **Editar**, **quitar**.

2. Si el elemento o el vínculo forma parte de un grupo, aparece el icono volver a capturar los elementos secundarios **del botón volver** a obtener elementos ![secundarios](../modeling/media/dependencygraph-deletednodesicon.png "DependencyGraph_DeletedNodesIcon") en el grupo. Haga clic aquí para recuperar los elementos y vínculos que faltan.

- Puede quitar los elementos de código y vínculos de un mapa sin que ello afecte al código subyacente. Al eliminarlos, sus definiciones se quitan del archivo DGML (.dgml).

- Los mapas que se crean editando el DGML, agregando elementos de código sin definir o usando versiones anteriores de Visual Studio, no admiten esta funcionalidad.

##### <a name="flag-a-code-element-for-follow-up"></a>Marcar un elemento de código para su seguimiento

1. Seleccione el elemento de código o el vínculo que quiera marcar para el seguimiento.

2. Abra el menú contextual y elija **Editar**, **marca para seguimiento**.

- De forma predeterminada, el elemento de código adquiere un fondo de color rojo. Considere la posibilidad de [agregarle un comentario](#AddComments) con la información de seguimiento adecuada.

- Cambiar el color de fondo del elemento o borrar la marca de seguimiento eligiendo **Editar**y **otros colores de marca**.

## <a name="ChangeStyleCodeOrLink"></a>Cambiar el estilo de un elemento de código o vínculo
 Puede cambiar los iconos de los elementos de código y los colores de los elementos de código y vínculos con el uso de iconos y colores predefinidos. Por ejemplo, puede elegir un color para resaltar los elementos de código y vínculos que tengan cierta categoría o propiedad. De este modo, podrá identificar áreas específicas del mapa y concentrarse en ellas. Puede especificar iconos y colores personalizados editando el archivo. DGML del mapa. vea [personalizar mapas de código mediante la edición de los archivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

#### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Para aplicar un color o icono predefinido a los elementos de código o vínculos con cierta categoría o propiedad

1. En la barra de herramientas del mapa, elija **leyenda**.

2. En el cuadro **leyenda** , vea si la categoría o propiedad del elemento de código ya aparece en la lista.

3. Si la lista no incluye la categoría o propiedad, elija **+** en el cuadro **leyenda** y, a continuación, elija **propiedad de nodo**, **categoría de nodo**, propiedad de **vínculo**o **categoría de vínculo**. Después, elija la propiedad o categoría. La categoría o propiedad aparece ahora en el cuadro **leyenda** .

    > [!NOTE]
    > Para crear y asignar una categoría o una propiedad a un elemento de código, puede editar el archivo. DGML del mapa. vea [personalizar mapas de código mediante la edición de los archivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

4. En el cuadro **leyenda** , haga clic en el icono situado junto a la categoría o propiedad que ha agregado o que desea cambiar.

5. Use la tabla siguiente para seleccionar el estilo que desea cambiar:

    |**Para cambiar el**|**Choose**|
    |-----------------------|----------------|
    |Color de fondo|**Fondo**|
    |Color del contorno|**Stroke**|
    |Color del texto (se muestra la letra “f” para mostrar el resultado)|**Planos**|
    |Iconos|**Iconos**|

     Aparece el cuadro de diálogo Selector de **conjunto de colores** o selector de **conjunto de iconos** para seleccionar un color o icono.

6. En el cuadro de diálogo **selector de conjunto de colores** o selector de conjunto de **iconos** , realice una de las acciones siguientes:

    |**Para aplicar un**|**Siga estos pasos**|
    |--------------------|-----------------------------|
    |Conjunto de colores o iconos|Abra la lista seleccionar **conjunto** de **colores** (o **icono**). Seleccione un conjunto de colores o de iconos.|
    |Color o icono específico|Abra la lista de valores de la categoría o propiedad. Seleccione un color o icono.|

    > [!NOTE]
    > Puede reorganizar, eliminar o desactivar temporalmente los estilos en el cuadro **leyenda** . Vea [editar el cuadro leyenda](#ModifyLegend).

## <a name="ModifyLegend"></a>Editar el cuadro leyenda
 Puede reorganizar, eliminar o desactivar temporalmente los estilos en el cuadro **leyenda** :

1. Abra el menú contextual de un estilo en el cuadro **leyenda** .

2. Realice una de las tareas siguientes:

    |**En**|**Choose**|
    |------------|----------------|
    |Desactivar el elemento de código|**Activa**|
    |Eliminar el elemento de código|**Eliminar**|
    |Subir el estilo|**Subir**|
    |Bajar el elemento de código|**Bajar**|

## <a name="CopyLegend"></a>Copiar estilos de un mapa a otro

1. Asegúrese de que el cuadro **leyenda** aparece en el mapa de origen. Si no está visible, en la barra de herramientas del mapa, haga clic en **leyenda**.

2. Abra el menú contextual del cuadro **leyenda** . Elija **copiar leyenda**.

3. Pegue la leyenda en el mapa de destino.

## <a name="MergeMaps"></a>Combinar mapas de código
 Para combinar mapas, puede copiar y pegar elementos de código entre mapas. Si los identificadores de elemento de código coinciden, el pegado de elementos de código funciona como una operación de combinación. Para facilitar esta tarea, coloque todos los ensamblados o archivos binarios que quiere visualizar en la misma carpeta, de modo que la ruta de acceso completa de cada ensamblado o binario sea la misma para cada mapa que quiere combinar.

 También puede arrastrar los ensamblados o archivos binarios al mismo mapa desde esa carpeta.

## <a name="see-also"></a>Vea también
 [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md) [usar mapas de código para depurar las aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md) [buscar posibles problemas mediante analizadores de mapa de código](../modeling/find-potential-problems-using-code-map-analyzers.md) [personalizar mapas de código mediante la edición de los archivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md) [Directed Graph Markup Language (DGML) referencia](../modeling/directed-graph-markup-language-dgml-reference.md) de
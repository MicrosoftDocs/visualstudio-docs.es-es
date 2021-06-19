---
title: Examinar y reorganizar mapas de código
description: Obtenga información sobre cómo puede reorganizar elementos en mapas de código para que sean más fáciles de leer y mejorar su rendimiento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 83132cfccd0af7244cf31f502669144eb3388bd8
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385557"
---
# <a name="browse-and-rearrange-code-maps"></a>Examinar y reorganizar mapas de código

Reorganice los elementos en mapas de código para facilitar su lectura y mejorar su rendimiento.

Puede personalizar los mapas de código sin que ello afecte al código subyacente de una solución. Esto resulta útil si quiere centrarse en elementos de código clave o comunicar ideas sobre el código. Por ejemplo, para resaltar áreas interesantes, puede seleccionar elementos de código en el mapa y filtrarlos, cambiar el estilo de los elementos de código y los vínculos, ocultar o eliminar elementos de código y organizar los elementos de código mediante propiedades, categorías o grupos.

 **Requisitos**

- Para crear mapas de código, debe tener Visual Studio Enterprise.

- En Visual Studio Professional, puede ver mapas de código y realizar ediciones limitadas a los mapas de código.

## <a name="get-started-working-with-code-maps"></a><a name="ManageLargeGraphs"></a> Introducción al trabajo con mapas de código

Cree un mapa de código (consulte [Asignación de dependencias en las soluciones para](../modeling/map-dependencies-across-your-solutions.md) obtener más detalles). Si no desea esperar a que el mapa termine  de generarse, haga clic en el vínculo Cancelar en cualquier momento para detener el proceso de generación. Sin embargo, si lo hace, no podrá ver los detalles de todas las dependencias y vínculos.

Después de generar el mapa, siga primero estas sugerencias para revisar el código:

- Observe los clústeres de dependencia naturales en el código. En la barra de herramientas del mapa, elija **el** botón Diseño , **Clústeres rápidos** ![ Clústeres rápidos en la barra de herramientas del gráfico ](../modeling/media/quickclustersicon.gif) . Vea [Cambiar el diseño del mapa.](#Selecting)

     ![Gráfico de dependencias &#45; diseño de clústeres rápidos](../modeling/media/dependencygraph_quickclusters.png)

- Organice el mapa en áreas más pequeñas mediante la agrupación de los nodos relacionados. Contraiga esos grupos para ver solo las dependencias intergrupo, que aparecen automáticamente. Vea [Agrupar nodos](#OrganizeGroups).

- Utilice los filtros para simplificar el mapa y centrarse en los tipos de nodos o vínculos que le interesen. Consulte [Filtrado de nodos y vínculos.](#FilterNodes)

- Obtenga el máximo rendimiento de los mapas grandes. Consulte [Asignación de dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md) para obtener más información. Por ejemplo, active **Omitir** compilación en la barra de herramientas del mapa para Visual Studio no recompile la solución al actualizar elementos en el mapa.

## <a name="change-the-map-layout"></a><a name="Selecting"></a> Cambio del diseño del mapa

|**To**|**Siga estos pasos**|
|-|-|
|Organizar el flujo de dependencias de todo el mapa en una dirección concreta. Esto puede ayudarle a ver las capas de la arquitectura del código.|En la barra de herramientas del mapa, elija **Diseño** y, a continuación:<br /><br /> -   **De arriba a abajo** ![ Botón de gráfico de arriba abajo](../modeling/media/topbottomgraphbutton.gif)<br />-   **De abajo a arriba** ![ Botón de gráfico de abajo a superior](../modeling/media/bottomtopgraphbutton.gif)<br />-   **De izquierda a derecha** ![ Botón de diseño de izquierda a derecha](../modeling/media/leftrightgraphbutton.gif)<br />-   **De derecha a izquierda** ![ Botón de gráfico de derecha a izquierda](../modeling/media/rightleftgraphbutton.gif)|
|Consultar los clústeres de dependencia naturales en el código con los nodos más dependientes en el centro de los clústeres y los nodos menos dependientes fuera de dichos clústeres.|En la barra de herramientas del mapa, elija **Diseño** y, a continuación, el botón **Clústeres rápidos** ![ de clústeres rápidos en la barra de herramientas del ](../modeling/media/quickclustersicon.gif) gráfico.|
|Seleccionar uno o más nodos en el mapa.|Haga clic en un nodo para seleccionarlo. Para seleccionar o anular la selección de más de un nodo, mantenga **presionada la tecla CTRL** al hacer clic.<br /><br /> Teclado: presione **TAB** o use las teclas de flecha para mover el rectángulo de foco de puntos a un nodo y **presione ESPACIO** para seleccionarlo. Presione **CTRL**  +  **ESPACIO para** seleccionar o anular la selección de nodos.|
|Mover nodos específicos por el mapa.|Arrastre los nodos para moverlos. Para sacar otros nodos y vínculos del camino mientras arrastra nodos, mantenga presionada la **tecla MAYÚS.**<br /><br /> Teclado: mantenga **presionada la tecla CTRL** y presione las teclas de dirección.|
|Cambiar el diseño de un grupo independientemente del resto de nodos y grupos del mapa.|Seleccione un nodo y abra el menú contextual. Elija **Diseño** y seleccione un estilo de diseño.<br /><br /> o bien<br /><br /> Seleccione un nodo y expándalo para mostrar los nodos secundarios. Haga clic en el título del nodo para mostrar la barra de herramientas emergente del grupo y abra la lista Cambiar el estilo de diseño del grupo Gráfico de dependencias &#45; barra de herramientas &#45; ![ ](../modeling/media/dependencygraph_grouptoolbar.gif) diseño. Seleccione uno de los diseños de árbol, **Clústeres rápidos** o Vista de lista **(que** organiza el contenido del grupo en una lista).<br /><br /> Consulte [Agrupar nodos para](#OrganizeGroups) obtener más detalles.|
|Deshacer una acción en el mapa.|Presione **CTRL**  +  **Z** o use el Visual Studio **Deshacer.**|

## <a name="browse-the-map"></a><a name="Explore"></a> Examinar el mapa

|**To**|**Siga estos pasos**|
|-|-|
|Examinar el mapa.|Arrastre el mapa en cualquier dirección con el mouse.<br /><br /> o bien<br /><br /> Mantenga **presionada la** tecla MAYÚS y gire la rueda del mouse para desplazarse horizontalmente. Mantenga   +  **presionada la tecla MAYÚS CTRL** y gire la rueda del mouse para desplazarse horizontalmente.|
|Acercar o alejar el mapa|Gire la rueda del mouse.<br /><br /> o bien<br /><br /> Use la **lista desplegable Zoom** en la barra de herramientas del mapa de código.<br /><br /> o bien<br /><br /> Utilice los métodos abreviados de teclado. Para acercar, presione **CTRL + MAYÚS + .** (punto). Para alejar, presione **CTRL + MAYÚS + ,** (coma).|
|Acercar en un área específica con el mouse.|Mantenga presionado el botón derecho del mouse mientras dibuja un rectángulo alrededor del área que le interesa.|
|Cambiar el tamaño del mapa y ajustarlo a la ventana.|Elija **Zoom para ajustar en** la lista Zoom **de** la barra de herramientas del mapa de código.<br /><br /> o bien<br /><br /> Haga clic en **el icono Zoom to fit** icon (Zoom para ajustar) icono zoom en la barra de herramientas del mapa de ![ ](../modeling/media/almcodemapzoomicon.png) código. Teclado: presione **CTRL + 0** (cero).|
|Buscar un nodo en el mapa por su nombre. **Sugerencia:**  Esto solo funciona para los elementos del mapa. Para buscar elementos en la solución, pero no en el mapa, encuéstrelos en Explorador de soluciones y, a continuación, arrástrelos al mapa. (Arrastre la selección o, en la barra de herramientas **Explorador de soluciones,** haga clic **en Mostrar en mapa de código**).|1. Elija  el icono Buscar icono Buscar en la barra de herramientas del mapa en la barra de herramientas del mapa de código ![ ](../modeling/media/almcodemapfindicon.png) (teclado: **presione CTRL + F**) para mostrar el cuadro de búsqueda en la esquina superior derecha del mapa.<br />2. Escriba el nombre del elemento y presione **Devolver** o haga clic en el icono "lupa". El primer elemento que coincide con la búsqueda aparece seleccionado en el mapa.<br />3. Para personalizar la búsqueda, abra la lista desplegable y elija una opción de búsqueda. Las opciones son **Buscar siguiente,** **Buscar anterior** y **Seleccionar todo.** Después, haga clic en el botón correspondiente junto al cuadro de texto de búsqueda.<br />     ![Lista desplegable de opciones&#45;búsqueda](../modeling/media/almcodemapssearchdropdown.png)<br />     Como alternativa, use el teclado: presione **F3** para seleccionar el siguiente nodo correspondiente o **MAYÚS + F3** para seleccionar el nodo de coincidencia anterior.<br />4. Seleccione cualquiera de las opciones que especifiquen cómo se controlan los términos de búsqueda haciendo clic en los iconos situados debajo del cuadro de texto de búsqueda.<br />     ![Opciones de coincidencia de búsqueda](../modeling/media/almcodemapssearchmatchicons.png)<br />     Las opciones son, de izquierda a derecha, coincidencia que distingue mayúsculas de minúsculas, solo palabras completas, uso de la sintaxis de expresiones regulares de .NET y expansión automática de grupos para mostrar las coincidencias con los elementos delimitados. **Importante:**  Puede usar el cuadro de búsqueda para buscar coincidencias en grupos contraídos solo si esos grupos se expandieron anteriormente. Para encontrar estas coincidencias y expandir los grupos primarios automáticamente, elija dicha opción en el cuadro de búsqueda.|
|Seleccionar los nodos no seleccionados.|Abra el menú contextual de los nodos seleccionados. Elija **Seleccionar**, **Invertir selección.**|
|Seleccionar nodos adicionales vinculados a los nodos seleccionados.|Abra el menú contextual de los nodos seleccionados. Elija **Seleccionar** y uno de estos:<br /><br /> - Para seleccionar nodos adicionales que se vinculan directamente al nodo seleccionado, elija **Dependencias entrantes.**<br />- Para seleccionar nodos adicionales que se vinculan directamente desde el nodo seleccionado, elija **Dependencias salientes.**<br />- Para seleccionar nodos adicionales que se vinculan directamente al nodo seleccionado y desde este, elija **Ambos.**<br />- Para seleccionar todos los nodos que se vinculan al nodo seleccionado y desde este, elija **Subgráfico conectado.**<br />- Para seleccionar todos los elementos secundarios del nodo seleccionado, elija **Elementos secundarios.**|

## <a name="filter-nodes-and-links"></a><a name="FilterNodes"></a> Filtrado de nodos y vínculos

|**To**|**Siga estos pasos**|
|-|-|
|Mostrar u ocultar el panel Filtros.|Elija el botón **Filtros de la** barra de herramientas del mapa de código. El **panel** Filtros se muestra como una página con pestañas **Explorador de soluciones**, de forma predeterminada.|
|Filtrar los tipos de nodos que se muestran en el mapa.|Establezca o desactive las casillas de la **lista Elementos de** código del panel Filtros.|
|Filtrar los tipos de vínculos que se muestran en el mapa.|Establezca o desactive las casillas de la **lista Relaciones** del panel Filtros.|
|Mostrar u ocultar los nodos de proyecto de prueba en el mapa.|Establezca o desactive la casilla **Probar recursos** en la **lista Varios** del panel Filtros.|

Los iconos mostrados en el panel Leyenda del mapa reflejan la configuración establecida en la lista. Para mostrar u ocultar el panel Leyenda, haga clic en el **botón Leyenda** de la barra de herramientas del mapa de código.

## <a name="examine-nodes-and-links"></a><a name="Inspect"></a> Examen de nodos y vínculos

Los mapas de código muestran los siguientes tipos de vínculos:

- Un vínculo individual representa una relación única entre dos nodos.

- Un vínculo entre grupos representa una relación entre dos nodos de diferentes grupos.

- Un vínculo agregado representa todas las relaciones que señalan la misma dirección entre dos grupos.

> [!TIP]
> De forma predeterminada, el mapa muestra los vínculos entre grupos solo para los nodos seleccionados. Para cambiar este comportamiento para mostrar u ocultar  vínculos agregados entre grupos,  haga clic en Diseño en la barra de herramientas del mapa de código y elija Avanzado **y,** a continuación, Mostrar todos los vínculos entre grupos u Ocultar todos los vínculos entre **grupos**. Consulte [Ocultar o mostrar nodos y vínculos para](#HidingShowing) obtener más detalles.

|**To**|**Siga estos pasos**|
|-|-|
|Ver más información sobre un nodo o un vínculo.|Mueva el puntero del mouse sobre el nodo o vínculo hasta que aparezca información sobre herramientas.<br /><br /> En la información sobre herramientas de un vínculo agregado se muestran las dependencias individuales que representa.<br /><br /> o bien<br /><br /> Abra el menú contextual del nodo o el vínculo. Elija **Editar**, **Propiedades**.|
|Mostrar u ocultar el contenido de un grupo.|- Para expandir un grupo, abra el menú contextual del nodo y elija **Grupo**, **Expandir.**<br />     o bien<br />     Mueva el puntero del mouse sobre el nodo hasta que aparezca el botón de contenido adicional (flecha hacia abajo). Haga clic en este botón para expandir el grupo. Teclado: para expandir o contraer el grupo seleccionado, presione la **tecla PLUS** ( ) o la **+** tecla **MENOS** ( **-** ).<br />- Para contraer un grupo, abra el menú contextual del nodo y elija **Grupo**, **Contraer**.<br />     o bien<br />     Mueva el puntero del mouse sobre un grupo hasta que aparezca el botón de contenido adicional (flecha hacia arriba). Haga clic en este botón para contraer el grupo.<br />- Para expandir todos los grupos, presione **CTRL**  +  **A** para seleccionar todos los nodos. Abra el menú contextual del mapa y elija **Agrupar,** **Expandir.** **Nota:**      Este comando no está disponible si la expansión de todos los grupos genera problemas de asignación o memoria inutilizables. Se recomienda expandir el mapa solo al nivel de detalle que le interese.<br />- Para contraer todos los grupos, abra el menú contextual de un nodo o del mapa. Elija **Grupo**, **Contraer todo.**|
|Ver la definición de código para un espacio de nombres, tipo o miembro.|Abra el menú contextual del nodo y elija **Ir a definición.**<br /><br /> O bien<br /><br /> Haga doble clic en el nodo. Para los grupos expandidos, haga doble clic en el encabezado del grupo.<br /><br /> O bien<br /><br /> Seleccione el nodo y presione **F12**.<br /><br /> Por ejemplo:<br /><br /> - Para un espacio de nombres que contiene una clase, se abre el archivo de código de la clase para mostrar la definición de esa clase. En otros casos, la **ventana Resultados de buscar** símbolos muestra una lista de archivos de código. **Nota:**      Al realizar esta tarea en un espacio de nombres Visual Basic, el archivo de código subyacente al espacio de nombres no se abre. Este problema también se produce cuando se realiza esta tarea en un grupo de nodos seleccionados que incluyen un espacio Visual Basic de nombres. Para evitar este problema, examine manualmente el archivo de código subyacente u omita el nodo del espacio de nombres de la selección.<br />- Para una clase o una clase parcial, se abre el archivo de código de esa clase para mostrar la definición de clase.<br />- Para un método, se abre el archivo de código de la clase primaria para mostrar la definición del método.|
|Examinar las dependencias y los elementos que participan en un vínculo agregado.|Seleccione los vínculos que le interesen y abra el menú contextual de la selección. Elija **Mostrar vínculos de contribución** o **Mostrar vínculos de contribución en el nuevo mapa de código.**<br /><br /> Visual Studio expande los grupos en ambos extremos del vínculo y muestra solo los elementos y dependencias que participan en el vínculo. **Nota:**  Al examinar las dependencias entre elementos de grupos parciales, es posible que vea este comportamiento: <ul><li>Los vínculos a elementos que no participan en el examen desaparecen del mapa, aunque esos vínculos siguen existiendo.</li><li>Suponga que examina un vínculo a un elemento en un grupo parcial y posteriormente examina otro vínculo al mismo elemento. Durante el segundo examen, el grupo parcial de destino muestra solo elementos del primer examen. Los vínculos y los elementos de destino que no participaron en el primer examen pero participaron en el segundo examen no aparecen.</li></ul> Para ver los elementos que faltan en un grupo, elija **Volver** a capturar los elementos secundarios icono de elementos secundarios (lo que indica que no todos los miembros de un grupo aparecen ![ en el ](../modeling/media/dependencygraph_deletednodesicon.png) mapa). También puede intentar deshacer las acciones (teclado: presione **CTRL+Z)** y examinar las dependencias en un nuevo mapa.|
|Examinar las dependencias entre varios nodos de grupos diferentes.|Expanda los grupos de modo que pueda ver todos sus elementos secundarios. Seleccione todos los nodos que le interesen, incluidos sus elementos secundarios. En el mapa se muestran los vínculos entre grupos de los nodos seleccionados.<br /><br /> Para seleccionar todos los nodos de un grupo, mantenga presionada la tecla **MAYÚS** y el botón izquierdo del mouse mientras dibuja un rectángulo alrededor de ese grupo. Para seleccionar todos los nodos de un mapa, presione **CTRL** + **A.** **Sugerencia:**  Para mostrar los vínculos entre  grupos en todo momento, elija Diseño en la barra de herramientas del **mapa,** Avanzado , Mostrar todos **los vínculos entre grupos**.|
|Ver los elementos a los que un nodo o vínculo hace referencia.|Abra el menú contextual del nodo y elija **Buscar todas las referencias.** **Nota:**  Esto solo se aplica cuando el atributo se establece para el nodo o vínculo en el `Reference` archivo .dgml del mapa. Para agregar referencias a elementos de nodos o vínculos, consulte [Personalización de mapas de código mediante la edición de los archivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).|

## <a name="hide-or-show-nodes-and-links"></a><a name="HidingShowing"></a> Ocultar o mostrar nodos y vínculos

Al ocultar nodos, se evita que participen en algoritmos de diseño. De forma predeterminada, los vínculos entre grupos se ocultan. Los vínculos entre grupos son vínculos individuales que conectan nodos entre diferentes grupos. Cuando se contraen los grupos, el mapa agrega todos los vínculos entre grupos a los vínculos individuales que hay entre los grupos. Cuando se expande un grupo y se seleccionan los nodos que hay dentro de este, los vínculos entre grupos aparecen y muestran las dependencias que existen dentro de ese grupo.

> [!CAUTION]
> Antes de compartir un mapa creado en Visual Studio Enterprise con los usuarios de Visual Studio Professional, asegúrese de mostrar cualquier nodo o vínculo entre grupos que quiera que otros vean. De lo contrario, esos usuarios no podrán mostrar esos elementos.

### <a name="to-hide-or-show-nodes"></a>Para ocultar o mostrar nodos

|**To**|**Siga estos pasos**|
|-|-|
|Ocultar los nodos seleccionados.|1. Seleccione los nodos que desea ocultar.<br />2. Abra el menú contextual de los nodos seleccionados o del mapa. Elija **Seleccionar**, **Ocultar seleccionado.**|
|Ocultar los nodos no seleccionados.|1. Seleccione los nodos que desea que permanezcan visibles.<br />2. Abra el menú contextual de los nodos seleccionados o del mapa. Elija **Seleccionar**, **Ocultar sin seleccionar.**|
|Mostrar los nodos ocultos.|- Para mostrar todos los nodos ocultos dentro de un grupo, primero asegúrese de que el grupo está expandido. Abra el menú contextual y elija **Seleccionar**, **Mostrar elementos secundarios.**<br />     o bien<br />     Haga clic **en el** icono Mostrar elementos secundarios Mostrar elementos secundarios en la esquina superior izquierda del grupo (esto solo es visible cuando hay nodos ![ secundarios ](../modeling/media/dependencygraph_filtericon_hiddennodes.gif) ocultos).<br />- Para mostrar todos los nodos ocultos, abra el menú contextual del mapa o un nodo y elija **Seleccionar**, **Mostrar todo**.|

### <a name="to-hide-or-show-links"></a>Para ocultar o mostrar vínculos

|**To**|**En la barra de herramientas del mapa, elija Diseño, Avanzado y, después, elija**|
|-|-|
|Mostrar los vínculos entre grupos en todo momento.|**Mostrar todos los vínculos entre grupos**. De este modo, se ocultan los vínculos agregados entre grupos.|
|Ocultar los vínculos entre grupos en todo momento.|**Ocultar todos los vínculos entre grupos**|
|Mostrar solo los vínculos entre grupos de los nodos seleccionados.|**Mostrar los vínculos entre grupos de los nodos seleccionados**|
|Ocultar todos los vínculos.|**Ocultar todos los vínculos**. Para volver a mostrar los vínculos, elija una de las opciones mencionadas anteriormente.|

## <a name="group-nodes"></a><a name="OrganizeGroups"></a> Nodos de grupo

|**To**|**Siga estos pasos**|
|-|-|
|Mostrar los nodos contenedores como nodos de grupo o nodos de hoja.|Para mostrar los nodos de contenedor como nodos hoja: seleccione los nodos, abra el menú contextual de la selección y elija **Agrupar**, **Convertir en hoja.**<br /><br /> Para mostrar los nodos de contenedor como nodos de grupo: seleccione los nodos, abra el menú contextual de la selección y elija **Grupo**, **Convertir en grupo.**|
|Cambiar el diseño de un grupo.|Seleccione el grupo, abra el menú contextual, elija **Diseño** y seleccione el estilo de diseño que desee.<br /><br /> o bien<br /><br /> 1. Seleccione el grupo y asegúrese de que está expandido.<br />2. Vuelva a hacer clic en el encabezado del grupo y aparecerá la barra de herramientas del grupo.<br />     ![Gráfico de dependencias &#45; barra de herramientas del grupo](../modeling/media/dependencygraph_group.png)<br />3. Abra  la barra de herramientas Cambiar el estilo de diseño de la lista de grupos Gráfico de dependencias &#45; grupo &#45; diseño y elija el estilo de ![ diseño que ](../modeling/media/dependencygraph_grouptoolbar.gif) desee.<br /><br /> **Vista de** lista reorganiza los miembros del grupo en una lista. **Graph Default restablece** el diseño del grupo al diseño predeterminado del mapa. Para otras opciones, vea [Cambiar el diseño del mapa.](#Selecting)|
|Agregar un nodo a un grupo.|Arrastre el nodo al grupo.<br /><br /> Mientras arrastra el nodo, Visual Studio muestra un indicador para señalar el movimiento del nodo.<br /><br /> También puede arrastrar nodos fuera de un grupo.|
|Agregar un nodo a un nodo sin grupo.|Arrastre el nodo hasta el nodo de destino. Puede convertir cualquier nodo de destino en un grupo mediante la adición de nodos.|
|Agrupar nodos seleccionados.|1. Seleccione los nodos que desea agrupar. Aparece una barra de herramientas emergente por encima del último nodo seleccionado.<br />     ![Barra de herramientas del gráfico de dependencia](../modeling/media/depedencygraph_toolbar.png)<br />2. En la barra de herramientas, elija el cuarto icono Agrupar los nodos seleccionados **(si** el nodo está expandido tendrá cinco en lugar de cuatro iconos). Escriba el nombre del nuevo grupo y presione **Devolver**.<br />     o bien<br />     Seleccione los nodos que quiere agrupar y abra el menú contextual de la selección. Elija **Grupo**, **Agregar grupo primario,** escriba el nombre del nuevo grupo y presione **Devolver**.<br /><br /> Puede cambiar el nombre de un grupo. Abra el menú contextual del grupo y elija **Editar**, **Propiedades** para abrir el Visual Studio ventana Propiedades. En la **propiedad Etiqueta,** cambie el nombre del grupo según sea necesario.|
|Quitar grupos.|Seleccione el grupo o los grupos que desee quitar. Abra el menú contextual de la selección y elija **Grupo**, **Quitar grupo.**|
|Quitar los nodos del grupo primario.|Seleccione los nodos que desea mover. Abra el menú contextual de la selección y elija **Agrupar**, **Quitar del elemento primario.** Esta acción quita los nodos hasta el grupo primario principal o fuera del grupo si no hay ningún grupo primario principal.<br /><br /> o bien<br /><br /> Seleccione los nodos y arrástrelos fuera del grupo.|

## <a name="add-remove-or-rename-nodes-links-and-comments"></a><a name="AddRemoveNodesLinks"></a> Agregar, quitar o cambiar el nombre de nodos, vínculos y comentarios

Puede mostrar más o menos elementos de un mapa con el fin de explorar en profundidad o simplificar el mapa. También puede cambiar el nombre de los elementos y agregar comentarios a los elementos.

> [!CAUTION]
> Antes de compartir un mapa creado mediante Visual Studio Enterprise con usuarios de Visual Professional, asegúrese de que los elementos de código que quiere que otros vean estén visibles en el mapa. De lo contrario, dichos usuarios no podrán recuperar los elementos de código eliminados.

### <a name="add-a-node-for-a-code-element"></a>Agregar un nodo para un elemento de código

|**To**|**Siga estos pasos**|
|-|-|
|Agregar un nuevo nodo genérico en la ubicación actual del puntero del mouse.|1. Mueva el puntero del mouse al lugar del mapa donde desea colocar el nuevo elemento de código y presione **Insertar**.<br />     o bien<br />     Abra el menú contextual del mapa y elija **Editar,** **Agregar,** **Nodo genérico.**<br />2. Escriba el nombre del nuevo nodo y presione **Devolver**.|
|Agregar un tipo específico de nodo de elemento de código en la ubicación actual del puntero del mouse.|1. Mueva el puntero del mouse al lugar del mapa donde desea colocar el nuevo elemento de código y abrir el menú contextual del mapa.<br />2. Elija **Editar,** **Agregar** y seleccione el tipo de nodo que desee.<br />3. Escriba el nombre del nuevo nodo y presione **Devolver**.|
|Agregar un tipo genérico o específico de nodo de elemento de código a un grupo.|1. Seleccione el nodo de grupo y abra el menú contextual.<br />2. Elija **Editar,** **Agregar** y seleccione el tipo de nodo que desee.<br />3. Escriba el nombre del nuevo nodo y presione **Devolver**.|
|Agregar un nuevo nodo del mismo tipo que un nodo existente y que esté vinculado desde el mismo.|1. Seleccione el elemento de código. Aparece una barra de herramientas emergente sobre él.<br />     ![Barra de herramientas del gráfico de dependencia](../modeling/media/depedencygraph_toolbar.png)<br />2. En la barra de herramientas, elija el segundo icono Crear un nodo con la misma categoría que este nodo y agregue **un nuevo vínculo a él.**<br />3. Elija un lugar en el mapa para colocar el nuevo elemento de código y haga clic en el botón izquierdo del mouse.<br />4. Escriba el nombre del nuevo nodo y presione **Devolver**.|
|Agregar un nuevo nodo genérico que esté vinculado desde un elemento de código existente que tenga el foco.|1. Con el teclado, presione **Tab** hasta que el elemento de código desde el que se vincula tenga el foco (rectángulo de puntos).<br />2. Presione **Alt** + **Insertar**.<br />3. Escriba el nombre del nuevo nodo y presione **Devolver**.|
|Agregar un nuevo nodo genérico que esté vinculado desde un elemento de código existente que tenga el foco.|1. Con el teclado, presione **Tab** hasta que el elemento de código al que se vincula tenga el foco (rectángulo de puntos).<br />2. Presione **Alt** + **Mayús** + **Insertar**.<br />3. Escriba el nombre del nuevo nodo y presione **Devolver**.|

|**Para agregar elementos de código para**|**Siga estos pasos**|
|-|-|
|Elementos de código de la solución.|1. Busque el elemento de código **en Explorador de soluciones**. Use el **Explorador de soluciones** de búsqueda o examine la solución. **Sugerencia:**      Para buscar elementos de código que tengan dependencias en un tipo o miembro, abra el menú contextual del tipo o del miembro de **Explorador de soluciones**. Elija la relación que le interese. **Explorador de soluciones** muestra solo los elementos de código con las dependencias especificadas.<br />2. Arrastre los elementos de código que le interesen a la superficie del mapa. También puede arrastrar elementos de código desde la Vista de clases o el Examinador de objetos.<br />     o bien<br />     En **Explorador de soluciones**, seleccione los elementos de código que desea asignar. A continuación, en la barra **Explorador de soluciones** de herramientas, haga clic **en Mostrar en mapa de código.**<br /><br /> De forma predeterminada, la jerarquía de contenedores principales para los nuevos elementos de código se muestra en el mapa. Use el botón **Incluir los padres** de la barra de herramientas del mapa de código para cambiar este comportamiento. Al desactivarlo, solo se agrega al mapa el propio elemento de código. Para invertir este comportamiento en una sola acción de arrastrar y colocar, mantenga presionada la tecla **CTRL** mientras arrastra los elementos de código al mapa.<br /><br /> Visual Studio agrega elementos de código para los elementos de código de nivel superior en la selección. Para ver si un elemento de código contiene otros elementos de código, mueva el puntero del mouse sobre el elemento de código para que aparezca el botón de contenido adicional (flecha hacia abajo). Elija el botón de contenido adicional para expandir el elemento de código. Para expandir todos los elementos de código, presione **CTRL** A para seleccionar todos los elementos, abra el menú contextual del mapa y +  **elija Agrupar**, **Expandir**. Este comando no está disponible si el hecho de expandir todos los grupos generaría un mapa inusable o problemas de memoria insuficiente.|
|Elementos de código relacionados con elementos de código del mapa.|Haga clic **en el botón Mostrar** relacionado de la barra de herramientas del mapa de código y elija el tipo de elementos relacionados que le interesen.<br /><br /> o bien<br /><br /> Abra el menú contextual del elemento de código. Elija uno de **los elementos Mostrar ...** del menú en función del tipo de relación que le interese. Por ejemplo, puede ver los elementos a los que hace referencia el elemento actual, los elementos que hacen referencia al elemento actual, los tipos base y derivado para las clases, los llamadores de métodos y las clases, los nombres de espacios y los ensamblados.<br /><br /> Para obtener más información, vea [este tema](../modeling/map-dependencies-across-your-solutions.md).|
|Ensamblados .NET (.dll o .exe) o archivos binarios compilados.|Arrastre los ensamblados o archivos binarios desde fuera de Visual Studio a un mapa.<br /><br /> Solo puede arrastrar desde el Explorador de Windows o el Explorador de archivos si ejecuta tanto dichos exploradores como Visual Studio en el mismo nivel de permisos del Control de cuentas de usuario (UAC). Por ejemplo, si UAC está activado y está ejecutando Visual Studio como administrador, el Explorador de Windows o el Explorador de archivos bloquearán la operación de arrastre.|

### <a name="AddNodes"></a>

#### <a name="add-a-link-between-existing-code-elements"></a>Para agregar un vínculo entre elementos de código existentes

1. Seleccione el elemento de código de origen. Aparece una barra de herramientas por encima del elemento de código.

    ![Barra de herramientas del gráfico de dependencia](../modeling/media/depedencygraph_toolbar.png)

2. En la barra de herramientas, elija el primer icono, Crear nuevo vínculo desde este nodo al que haga clic **en el siguiente nodo.**

3. Seleccione el elemento de código de destino. Aparece un vínculo entre los dos elementos de código.

**OR**

1. Seleccione el elemento de código de origen en el mapa.

2. Si ha instalado un mouse, mueva el puntero del mouse fuera de los límites del mapa.

3. Abra el menú contextual del elemento de código y elija **Editar**  >  **agregar**  >  **vínculo genérico.**

4. Utilice el tabulador hasta el elemento de código de destino del vínculo y selecciónelo.

5. Presione **ENTRAR**.

### <a name="AddComments"></a>

#### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Agregar un comentario a un nodo existente en el mapa

1. Seleccione el elemento de código. Aparece una barra de herramientas sobre él.

     ![Barra de herramientas del gráfico de dependencia](../modeling/media/depedencygraph_toolbar.png)

2. En la barra de herramientas, elija el tercer icono, Crear un nuevo nodo **de comentario con un nuevo vínculo al nodo seleccionado.**

     \- O bien

     Abra el menú contextual del elemento de código y elija **Editar**  >  **nuevo comentario.**

3. Escriba sus comentarios. Para escribir en una nueva línea, presione **Mayús**  +  **Entrar.**

#### <a name="add-a-comment-to-the-map-itself"></a>Agregar un comentario al propio mapa

1. Abra el menú contextual del mapa y elija **Editar**  >  **nuevo comentario.**

2. Escriba sus comentarios. Para escribir en una nueva línea, presione **Mayús**  +  **Entrar.**

### <a name="RenameNodes"></a>

#### <a name="rename-a-code-element-or-link"></a>Cambiar el nombre de un elemento de código o vínculo

1. Seleccione el elemento de código o el vínculo cuyo nombre quiere cambiar.

2. Presione **F2** o abra el menú contextual y elija **Editar cambiar**  >  **nombre.**

3. Cuando el cuadro de edición aparece en el mapa, cambie el nombre del elemento de código o del vínculo.

**OR**

1. Abra el menú contextual y elija **Editar**  >  **propiedades.**

2. Edite **la propiedad Label** en el Visual Studio ventana Propiedades.

#### <a name="remove-a-code-element-or-link-from-the-map"></a>Quitar un elemento de código o vínculo del mapa

1. Seleccione el elemento o vínculo de código y presione **la tecla** Eliminar.

     \- O bien

     Abra el menú contextual del elemento o vínculo de código y elija **Editar**  >  **Quitar.**

2. Si el elemento o vínculo forma  parte de un grupo, el botón Volver a captura de elementos secundarios aparece ![ dentro del ](../modeling/media/dependencygraph_deletednodesicon.png) grupo. Haga clic aquí para recuperar los elementos y vínculos que faltan.

- Puede quitar los elementos de código y vínculos de un mapa sin que ello afecte al código subyacente. Al eliminarlos, sus definiciones se quitan del archivo DGML (.dgml).

- Los mapas que se crean editando el DGML, agregando elementos de código sin definir o usando versiones anteriores de Visual Studio, no admiten esta funcionalidad.

#### <a name="flag-a-code-element-for-follow-up"></a>Marcar un elemento de código para su seguimiento

1. Seleccione el elemento de código o el vínculo que quiera marcar para el seguimiento.

2. Abra el menú contextual y elija **Editar**  >  **marca en Seguimiento.**

- De forma predeterminada, el elemento de código adquiere un fondo de color rojo. Considere [la posibilidad de agregarle](#AddComments) un comentario con la información de seguimiento adecuada.

- Cambie el color de fondo del elemento o desactive la marca de seguimiento eligiendo **Editar otros** colores  >  **de marca.**

## <a name="change-the-style-of-a-code-element-or-link"></a><a name="ChangeStyleCodeOrLink"></a> Cambiar el estilo de un elemento o vínculo de código

Puede cambiar los iconos de los elementos de código y los colores de los elementos de código y vínculos con el uso de iconos y colores predefinidos. Por ejemplo, puede elegir un color para resaltar los elementos de código y vínculos que tengan cierta categoría o propiedad. De este modo, podrá identificar áreas específicas del mapa y concentrarse en ellas. Puede especificar iconos y colores personalizados editando el archivo .dgml del mapa; consulte [Personalización de mapas de código mediante la edición de los archivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Para aplicar un color o icono predefinido a los elementos de código o vínculos con cierta categoría o propiedad

1. En la barra de herramientas del mapa, elija **Leyenda.**

2. En el **cuadro Leyenda** , vea si la propiedad o categoría de elemento de código ya aparece en la lista.

3. Si la lista no incluye la categoría o propiedad, elija en el cuadro Leyenda y, a continuación, elija Propiedad de nodo , Categoría de nodo, Propiedad de **+** vínculo o Categoría de **vínculo**.     Después, elija la propiedad o categoría. La categoría o propiedad aparece ahora en el **cuadro** Leyenda.

    > [!NOTE]
    > Para crear y asignar una categoría o una propiedad a un elemento de código, puede editar el archivo .dgml del mapa; consulte [Personalización de mapas de código mediante la edición de los archivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

4. En el **cuadro Leyenda** , haga clic en el icono situado junto a la categoría o propiedad que agregó o que desea cambiar.

5. Use la tabla siguiente para seleccionar el estilo que desea cambiar:

    |**Para cambiar el**|**Choose**|
    |-|-|
    |Color de fondo|**Información preliminar**|
    |Color del esquema|**Golpe**|
    |Color del texto (se muestra una letra "f" para mostrar el resultado)|**Primer plano**|
    |Icono|**Iconos**|

     Aparece **el cuadro de diálogo** **Selector** de conjunto de colores o Selector de conjunto de iconos para que seleccione un color o un icono.

6. En el **cuadro de diálogo Selector de conjunto** de colores o Selector de conjunto de iconos, realice una de las acciones siguientes: 

    |**Para aplicar a**|**Siga estos pasos**|
    |-|-|
    |Conjunto de colores o iconos|Abra la lista Seleccionar  conjunto de **colores** **(o icono).** Seleccione un conjunto de colores o de iconos.|
    |Color o icono específico|Abra la lista de valores de la categoría o propiedad. Seleccione un color o icono.|

    > [!NOTE]
    > Puede reorganizar, eliminar o desactivar temporalmente los estilos en el **cuadro** Leyenda. Vea [Editar el cuadro Leyenda](#ModifyLegend).

## <a name="edit-the-legend-box"></a><a name="ModifyLegend"></a> Edición del cuadro Leyenda

Puede reorganizar, eliminar o desactivar temporalmente estilos en el **cuadro Leyenda:**

1. Abra el menú contextual de un estilo en el **cuadro** Leyenda.

2. Realice una de las tareas siguientes:

    |**To**|**Choose**|
    |-|-|
    |Desactivar el elemento de código|**Deshabilitar**|
    |Eliminar el elemento de código|**Eliminar**|
    |Subir el estilo|**Subir**|
    |Bajar el elemento de código|**Bajar**|

## <a name="copy-styles-from-one-map-to-another"></a><a name="CopyLegend"></a> Copiar estilos de un mapa a otro

1. Asegúrese de que **el cuadro** Leyenda aparece en el mapa de origen. Si no está visible, en la barra de herramientas del mapa, haga clic en **Leyenda**.

2. Abra el menú contextual del cuadro **Leyenda.** Elija **Copiar leyenda.**

3. Pegue la leyenda en el mapa de destino.

## <a name="merge-code-maps"></a><a name="MergeMaps"></a> Mapas de código de combinación

Para combinar mapas, puede copiar y pegar elementos de código entre mapas. Si los identificadores de elemento de código coinciden, el pegado de elementos de código funciona como una operación de combinación. Para facilitar esta tarea, coloque todos los ensamblados o archivos binarios que quiere visualizar en la misma carpeta, de modo que la ruta de acceso completa de cada ensamblado o binario sea la misma para cada mapa que quiere combinar.

También puede arrastrar los ensamblados o archivos binarios al mismo mapa desde esa carpeta.

## <a name="see-also"></a>Vea también

- [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)
- [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)
- [Buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Personalizar mapas de código mediante la edición de los archivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [Referencia de Directed Graph Markup Language (DGML)](../modeling/directed-graph-markup-language-dgml-reference.md)

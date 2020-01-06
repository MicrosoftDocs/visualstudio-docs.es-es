---
title: Vista Gráfico del Diseñador de esquemas XML
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5881afde-3f24-4eb9-bff8-6cb3fc8aade7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb71196dfbaf371e66131bf1e4b22584d3dbf0c3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592872"
---
# <a name="graph-view"></a>Vista de gráfico

La vista Gráfico proporciona una representación gráfica de los nodos de esquema globales y de las relaciones entre ellos. Tenga en cuenta que la vista Gráfico no le permite modificar el diseño del conjunto de esquemas en la superficie de diseño. La vista Gráfico también incluye la barra de herramientas del Diseñador de esquemas XML y la barra de ruta de navegación.

La imagen siguiente muestra la vista Gráfico con seis nodos globales en su superficie de diseño.

![Vista Gráfico del Diseñador de esquemas XML](../xml-tools/media/xsddesigner_graphview.gif)

## <a name="design-surface"></a>Superficie de diseño

La superficie de diseño de la vista gráfico muestra el contenido del [área de trabajo del diseñador de esquemas XML](../xml-tools/xml-schema-designer-workspace.md). Si el área de trabajo contiene nodos globales del conjunto de esquemas, dichos nodos se muestran en la superficie de diseño de la vista Gráfico y se dibujan flechas entre los nodos que tienen relaciones.

Al hacer doble clic en un nodo de la vista de gráfico, se abrirá el editor XML.

Para eliminar los nodos seleccionados del área de trabajo, use la barra de herramientas del diseñador XSD o la tecla **suprimir** .

Si la superficie de diseño está en blanco, se muestran el editor XML, el **Explorador de esquemas XML**y la marca de agua. La *marca de agua* es una lista de vínculos a todas las vistas del diseñador xsd.

![Diseñador XSD; vista Gráfico](../xml-tools/media/xsdgraphviewwatermark.gif)

Si el conjunto de esquemas tiene errores, se muestra el texto siguiente al final de la lista: "Use la lista de errores para ver y corregir los errores en el conjunto de esquemas".

## <a name="breadcrumb-bar"></a>Barra de ruta de navegación

La barra de ruta de navegación situada en la parte inferior de la vista Gráfico muestra la ubicación del nodo seleccionado en el conjunto de esquemas. Si se han seleccionado varios elementos, la barra de ruta de navegación estará en blanco.

## <a name="context-right-click-menu"></a>Menú contextual (clic con el botón derecho)

En la tabla siguiente se describen las opciones disponibles para todos los nodos existentes en la superficie de diseño de la vista Gráfico.

|Opción|Descripción|
|-|-----------------|
|**Mostrar en el explorador de esquemas XML**|Coloca el foco en el Explorador de esquemas y resalta el nodo del conjunto de esquemas.|
|**Mostrar en la vista gráfico**|Cambia a la vista Gráfico (deshabilitado).|
|**Generar XML de ejemplo**|Disponible solo para los elementos globales. Genera un archivo XML de ejemplo para el elemento global.|
|**Borrar área de trabajo**|Borra el área de trabajo y la superficie de diseño.|
|**Quitar del área de trabajo**|Quita los nodos seleccionados del área de trabajo y de la superficie de diseño.|
|**Quitar todo excepto la selección del área de trabajo**|Quita los nodos que no están seleccionados del área de trabajo y de la superficie de diseño.|
|**Exportar diagrama como imagen**|Guarda la superficie de diseño en un archivo XPS.|
|**Seleccionar todo**|Selecciona todos los nodos de la superficie de diseño.|
|**Vista Código**|Abre el archivo que contiene el nodo seleccionado en el editor XML. El elemento seleccionado en el explorador de **esquemas XML** también se selecciona en el editor XML.|
|**Propiedades (ventana)**|Abre la ventana **propiedades** (si aún no está abierta). Esta ventana muestra información sobre el nodo.|

Además de las opciones comunes descritas anteriormente, el menú contextual para los elementos globales también tiene las opciones siguientes:

|Opción|Descripción|
|-|-----------------|
|**Agregar definición de tipo**|Agrega el tipo base al diagrama.|
|**Agregar todas las referencias**|Agrega todos los nodos que hacen referencia al elemento y dibuja flechas para indicar las relaciones entre ellos.|
|**Agregar miembros del grupo de sustitución**|Agrega todos los miembros del grupo de sustitución. Esta opción aparece en la vista si el elemento es el encabezado o un miembro de un grupo de sustitución.|
|**Generar XML de ejemplo**|Genera un archivo XML de ejemplo para el elemento global.|

Además de las opciones comunes descritas anteriormente, el menú contextual para los tipos simples y complejos globales también tiene las opciones siguientes:

|Opción|Descripción|
|-|-----------------|
|**Agregar tipo base**|Si el tipo seleccionado se deriva de un tipo global, agrega el tipo base del tipo seleccionado.|
|**Agregar todas las referencias**|Agrega todas las referencias del tipo seleccionado. Incluye elementos y atributos del tipo seleccionado, así como los tipos derivados de este.|
|**Agregar todos los tipos derivados**|Agrega todos los tipos derivados directa o indirectamente del tipo seleccionado.|
|**Agregar todos los antecesores**|Agrega todos los tipos primarios (base).|

Además de las opciones comunes descritas anteriormente, el menú contextual para los grupos globales y los grupos de atributos también tiene las opciones siguientes:

|Opción|Descripción|
|-|-----------------|
|**Agregar todas las referencias**|Agrega todos los nodos que hacen referencia al grupo y dibuja flechas para indicar las relaciones entre ellos.|
|**Agregar todos los miembros**|Agrega todos los miembros del grupo y dibuja flechas para indicar las relaciones entre ellos.|

Además de las opciones comunes descritas anteriormente, el menú contextual para los atributos globales también tiene las opciones siguientes:

|Opción|Descripción|
|-|-----------------|
|**Agregar todas las referencias**|Agrega todos los nodos que hacen referencia al grupo y dibuja flechas para indicar las relaciones entre ellos.|

## <a name="properties-window"></a>Propiedades (ventana)

Use el menú contextual (clic con el botón derecho) para abrir inicialmente la ventana **propiedades** . De forma predeterminada, la ventana **propiedades** aparece en la esquina inferior derecha de Visual Studio. Al hacer clic en un nodo que se representa en la vista modelo de contenido, las propiedades de ese nodo se mostrarán en la ventana **propiedades** .

## <a name="xsd-toolbar"></a>Barra de herramientas XSD

Cuando está activa la vista Gráfico, los botones siguientes de la barra de herramientas de XSD están habilitados.

![Barra de tareas del Diseñador de esquemas XSD](../xml-tools/media/xsdgraphviewtoolbar.gif)

|Opción|Descripción|
|-|-----------------|
|**Mostrar vista Inicio**|Cambia a la [vista Inicio](../xml-tools/start-view.md). Se puede tener acceso a esta vista mediante el método abreviado de teclado: **Ctrl**+**1**.|
|**Mostrar vista modelo de contenido**|Cambia a la [vista modelo de contenido](../xml-tools/content-model-view.md). Se puede tener acceso a esta vista mediante el método abreviado de teclado: **Ctrl**+**2**.|
|**Mostrar vista de gráfico**|Cambia a la [vista gráfico](../xml-tools/graph-view.md). Se puede tener acceso a esta vista mediante el método abreviado de teclado: **Ctrl**+**3**.|
|**Borrar área de trabajo**|Borra el área de trabajo y la superficie de diseño.|
|**Quitar del área de trabajo**|Quita los nodos seleccionados del área de trabajo y de la superficie de diseño.|
|**Quitar todo excepto la selección del área de trabajo**|Quita los nodos que no están seleccionados del área de trabajo y de la superficie de diseño. Esta opción está habilitada en las vistas Modelo de contenido y Gráfico.|
|**De izquierda a derecha**|Cambia el diseño de la vista Gráfico a una representación jerárquica de nodos mostrados de izquierda a derecha. Se puede tener acceso a esta opción mediante el método abreviado de teclado: **Alt**+**flecha derecha**.|
|**De derecha a izquierda**|Cambia el diseño de la vista Gráfico a una representación jerárquica de nodos mostrados de derecha a izquierda. Se puede tener acceso a esta opción mediante el método abreviado de teclado: **Alt**+**flecha izquierda**.|
|**De arriba abajo**|Cambia el diseño de la vista Gráfico a una representación jerárquica de nodos mostrados de arriba abajo. Se puede tener acceso a esta opción mediante el método abreviado de teclado: **Alt**+**flecha abajo**.|
|**De abajo arriba**|Cambia el diseño de la vista Gráfico a una representación jerárquica de nodos mostrados de abajo arriba. Se puede tener acceso a esta opción mediante el método abreviado de teclado: **Alt**+**flecha arriba**.|

## <a name="panscroll"></a>Panorámica/desplazamiento

Puede desplazar la superficie de diseño mediante las barras de desplazamiento o manteniendo presionada la tecla **Ctrl** mientras hace clic y arrastra el mouse. Cuando se obtiene una panorámica de la superficie de diseño usando el método de hacer clic y arrastrar, el cursor cambiará a cuatro flechas en cruz que señalan en cuatro direcciones.

## <a name="undoredo"></a>Deshacer/Rehacer

La función de deshacer/rehacer está habilitada en la vista Gráfico para las siguientes acciones:

- Agregar un nodo único arrastrándolo y colocándolo.

- Agregar varios nodos de la ventana de resultados de la búsqueda de las consultas del Explorador de esquemas o de la vista Inicio.

- Eliminar uno o varios nodos.

## <a name="zoom"></a>Zoom

El zoom está disponible en la esquina inferior derecha de la vista Gráfico.

El zoom se puede controlar de las maneras siguientes:

- Manteniendo presionada la tecla **Ctrl** y girando la rueda del mouse cuando el mouse se mantiene sobre la superficie de la vista del gráfico.

- Usando el control deslizante. El control deslizante muestra el nivel de zoom actual.

El control deslizante de zoom es opaco cuando se selecciona, se mantiene el mouse sobre él o se usa **Ctrl** con la rueda del mouse para hacer zoom; en el resto de los casos, es transparente.

## <a name="xml-editor-integration"></a>Integración del editor XML

Puede alternar entre la vista gráfico y el editor XML si hace clic en un nodo y usa el menú Ver contexto de código (clic con el botón derecho).

Si realiza cambios en el esquema establecido en el editor XML, los cambios se sincronizarán en la vista gráfico. Para obtener más información, vea [integración con el editor XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Vea también

- [Superficie de diseño](../xml-tools/xml-schema-designer-workspace.md)

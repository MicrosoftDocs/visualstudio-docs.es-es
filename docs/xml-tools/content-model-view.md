---
title: Vista Modelo de contenido del Diseñador de esquemas XML
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 67453571963ae22910842be0021e008632942de5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661528"
---
# <a name="content-model-view"></a>Vista Modelo de contenido

La vista Modelo de contenido proporciona una representación gráfica de los nodos de esquema globales y locales con sus componentes, incluidos los tipos simples y complejos, elementos, grupos de modelo, atributos y grupos de atributos. Los comentarios y las instrucciones de procesamiento XML no se pueden ver en el vista Modelo de contenido. La vista modelo de contenido contiene dos paneles: un panel de **área de trabajo** que contiene una lista de los nodos en el área de trabajo del [Diseñador de esquemas XML](../xml-tools/xml-schema-designer-workspace.md)y la superficie de diseño donde puede ver el modelo de contenido de los nodos de esquema seleccionados en el **área de trabajo** panel. La vista Modelo de contenido también incluye la barra de herramientas del Diseñador de esquemas XML y la barra de ruta de navegación.

En la siguiente imagen, el panel **área de trabajo** contiene seis nodos de esquema. El nodo `purchaseOrder` se selecciona en el panel **área de trabajo** y se muestra en la superficie de diseño.

![Vista Modelo de contenido del Diseñador de esquemas XML](../xml-tools/media/xsddesigner_contentmodelview.gif)

## <a name="workspace-panel"></a>Panel área de trabajo

Después de agregar nodos al área de trabajo, la lista de nodos aparecerá en el panel **área de trabajo** de la vista modelo de contenido. Al seleccionar los nodos en el panel **área de trabajo** , aparecen en la superficie de diseño de la vista modelo de contenido. Para eliminar nodos del área de trabajo, use la barra de herramientas del diseñador XSD, el menú contextual del panel del **área de trabajo** o la tecla **suprimir** .

Para obtener información sobre cómo agregar nodos, vea la sección "agregar nodos al área de trabajo" en el [área de trabajo del diseñador de esquemas XML](../xml-tools/xml-schema-designer-workspace.md).

## <a name="design-surface"></a>Superficie de diseño

Cuando se selecciona un nodo en el panel del **área de trabajo** , se agrega a la superficie de diseño de la vista modelo de contenido, donde puede ver los detalles del nodo.

El modelo de contenido de un nodo se representa con un árbol gráfico que puede expandirse, en el que los elementos y atributos aparecen como nodos del árbol. De forma predeterminada, solo se expande un nivel. Otra información, como los compositores, los nombres de tipo, los grupos y otros contenedores se coloca en una barra vertical (cuando se expande) junto con los elementos y atributos que encierran. Al hacer doble clic en una barra vertical, se vuelve horizontal y el árbol se contrae. Al hacer doble clic en una barra horizontal, se vuelve vertical y el árbol se expande. Al seleccionar la barra vertical, se seleccionan todos los nodos del contenedor. Los expansors aparecen a la derecha de un nodo si un elemento se puede expandir o contraer.

Si la superficie de diseño está en blanco, se muestran el editor XML, el **Explorador de esquemas XML**y la marca de agua. La *marca de agua* es una lista de vínculos a todas las vistas del diseñador xsd. Si el conjunto de esquemas tiene errores, se muestra el texto siguiente al final de la lista: "Use la lista de errores para ver y corregir los errores en el conjunto de esquemas".

## <a name="breadcrumb-bar"></a>Barra de ruta de navegación

La barra de ruta de navegación situada en la parte inferior de la vista Modelo de contenido muestra la ubicación del nodo seleccionado en el conjunto de esquemas.

## <a name="context-menus"></a>Menús contextuales

Al hacer clic con el botón secundario en un elemento en la superficie de diseño o en el panel **del área de trabajo** , aparece un menú contextual. En la siguiente tabla se describen las opciones que están disponibles para la superficie de diseño de la vista Modelo de contenido.

|Opción|Descripción|
|-|-----------------|
|**Mostrar en el explorador de esquemas XML**|Coloca el foco en el Explorador de esquemas y resalta el nodo del conjunto de esquemas.|
|**Mostrar en la vista gráfico**|Cambia a la vista Gráfico.|
|**Generar XML de ejemplo**|Disponible solo para los elementos globales. Genera un archivo XML de ejemplo para el elemento global.|
|**Mostrar documentación**|Muestra u oculta el contenido del nodo Anotación/Documentación.|
|**Exportar diagrama como imagen**|Guarda la superficie de diseño en un archivo XPS.|
|**Vista Código**|Abre el archivo que contiene el nodo seleccionado en el editor XML. El elemento seleccionado en el explorador de **esquemas XML** también se selecciona en el editor XML.|
|**Ventana Propiedades**|Abre la ventana **propiedades** (si aún no está abierta). Esta ventana muestra información sobre el nodo.|

En la tabla siguiente se describen las opciones disponibles para el panel **área de trabajo** .

|Opción|Descripción|
|-|-----------------|
|**Mostrar en el explorador de esquemas XML**|Coloca el foco en el Explorador de esquemas y resalta el nodo del conjunto de esquemas.|
|**Mostrar en la vista gráfico**|Cambia a la vista Gráfico.|
|**Borrar área de trabajo**|Borra el área de trabajo y la superficie de diseño.|
|**Quitar del área de trabajo**|Quita los nodos seleccionados del área de trabajo y de la superficie de diseño.|
|**Quitar todo excepto la selección del área de trabajo**|Quita los nodos que no están seleccionados del área de trabajo y de la superficie de diseño.|
|**Generar XML de ejemplo**|Disponible solo para los elementos globales. Genera un archivo XML de ejemplo para el elemento global.|
|**Seleccionar todo**|Selecciona todos los nodos del panel **área de trabajo** .|
|**Vista Código**|Abre el archivo que contiene el nodo seleccionado en el editor XML. El elemento seleccionado en el explorador de **esquemas XML** también se selecciona en el editor XML.|
|**Ventana Propiedades**|Abre la ventana **propiedades** (si aún no está abierta). Esta ventana muestra información sobre el nodo.|

## <a name="properties-window"></a>Propiedades (ventana)

Use el menú contextual para abrir inicialmente la ventana **propiedades** . De forma predeterminada, la ventana **propiedades** aparece en la esquina inferior derecha de Visual Studio. Al hacer clic en un nodo que se representa en la vista modelo de contenido, las propiedades de ese nodo se muestran en la ventana **propiedades** .

## <a name="xsd-designer-toolbar"></a>Barra de herramientas del diseñador XSD

Los siguientes botones de la barra de herramientas de Diseñador XSD están habilitados cuando está activa la vista Modelo de contenido.

![Barra de herramientas del Diseñador de esquemas XML](../xml-tools/media/xsdcontentmodelviewtoolbar.gif)

|Opción|Descripción|
|-|-----------------|
|**Mostrar vista Inicio**|Cambia a la [vista Inicio](../xml-tools/start-view.md). Se puede tener acceso a esta vista mediante el método abreviado de teclado: **Ctrl** +**1**.|
|**Mostrar vista modelo de contenido**|Cambia a la [vista modelo de contenido](../xml-tools/content-model-view.md). Se puede tener acceso a esta vista mediante el método abreviado de teclado: **Ctrl** +**2**.|
|**Mostrar vista de gráfico**|Cambia a la [vista gráfico](../xml-tools/graph-view.md). Se puede tener acceso a esta vista mediante el método abreviado de teclado: **Ctrl** +**3**.|
|**Borrar área de trabajo**|Borra el área de trabajo y la superficie de diseño.|
|**Quitar del área de trabajo**|Quita los nodos seleccionados del área de trabajo y de la superficie de diseño.|
|**Quitar todo excepto la selección del área de trabajo**|Quita los nodos que no están seleccionados del área de trabajo y de la superficie de diseño.|
|**Mostrar documentación**|Muestra u oculta el contenido del nodo Anotación/Documentación.|

## <a name="panscroll"></a>Panorámica/desplazamiento

Puede desplazar la superficie de diseño mediante las barras de desplazamiento o manteniendo presionada la tecla **Ctrl** mientras hace clic y arrastra el mouse. Al desplazar la superficie de diseño mediante hacer clic y arrastrar, el cursor cambia a cuatro flechas cruzadas que apuntan a cuatro direcciones.

## <a name="undoredo"></a>Deshacer/rehacer

La capacidad de deshacer/rehacer está habilitada en la vista Modelo de contenido para las siguientes acciones:

- Agregar un nodo único arrastrándolo y colocándolo.

- Agregar varios nodos desde la ventana de resultados de la búsqueda del Explorador de esquemas.

- Agregar nodos desde la vista Inicio.

- Eliminar uno o varios nodos.

## <a name="zoom"></a>Zoom

Zoom está disponible en la esquina inferior derecha de la vista modelo de contenido.

El zoom se puede controlar de las maneras siguientes:

- Manteniendo presionada la tecla **Ctrl** y girando la rueda del mouse cuando el mouse se mantiene sobre la superficie de la vista modelo de contenido.

- Usando el control deslizante. El control deslizante muestra el nivel de zoom actual.

El control deslizante de zoom es opaco cuando se selecciona, se mantiene el mouse sobre él o se usa **Ctrl** con la rueda del mouse para hacer zoom; en el resto de los casos, es transparente.

## <a name="xml-editor-integration"></a>Integración del editor XML

Puede alternar entre el **Diseñador XSD** y el editor XML mediante el menú contextual (contexto).

Si realiza cambios en el esquema establecido en el editor XML, los cambios se sincronizan en la vista modelo de contenido. Para obtener más información, vea [integración con el editor XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Vea también

- [Área de trabajo del Diseñador de esquemas XML](../xml-tools/xml-schema-designer-workspace.md)
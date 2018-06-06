---
title: Vista Modelo de contenido del Diseñador de esquemas XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d7f04c482149cbc063a3788dd6be44c643bae6a
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751798"
---
# <a name="content-model-view"></a>Vista Modelo de contenido

La vista Modelo de contenido proporciona una representación gráfica de los nodos de esquema globales y locales con sus componentes, incluidos los tipos simples y complejos, elementos, grupos de modelo, atributos y grupos de atributos. Los comentarios y las instrucciones de procesamiento XML no se pueden ver en el vista Modelo de contenido. La vista de modelo de contenido contiene dos paneles: un **área de trabajo** panel que contiene una lista de los nodos en el [área de trabajo de diseñador de esquemas XML](../xml-tools/xml-schema-designer-workspace.md)y la superficie de diseño donde puede ver el modelo de contenido del esquema nodos que están seleccionados en el **área de trabajo** panel. La vista Modelo de contenido también incluye la barra de herramientas del Diseñador de esquemas XML y la barra de ruta de navegación.

 En la siguiente imagen, el **área de trabajo** panel contiene seis nodos de esquema. El `purchaseOrder` nodo está seleccionado en el **área de trabajo** panel y se muestra en la superficie de diseño.

 ![Vista Modelo de contenido del Diseñador de esquemas XML](../xml-tools/media/xsddesigner_contentmodelview.gif)

## <a name="workspace-panel"></a>Panel área de trabajo

 Después de agregar nodos al área de trabajo, aparecerá la lista de nodos en el **área de trabajo** panel de la vista de modelo de contenido. Al seleccionar los nodos en el **área de trabajo** panel, que aparecen en la superficie de diseño de la vista modelo de contenido. Para eliminar nodos desde el área de trabajo, use la barra de herramientas del diseñador XSD, el **área de trabajo** menú contextual del panel, o la **eliminar** clave.

 Para obtener información acerca de cómo agregar nodos, vea la sección "Agregar nodos al área de trabajo" en [área de trabajo de diseñador de esquemas XML](../xml-tools/xml-schema-designer-workspace.md).

## <a name="design-surface"></a>Superficie de diseño

 Cuando se selecciona un nodo en el **área de trabajo** el panel, se agrega a la superficie de diseño de la vista modelo de contenido donde puede ver los detalles del nodo.

 El modelo de contenido de un nodo se representa con un árbol gráfico que puede expandirse, en el que los elementos y atributos aparecen como nodos del árbol. De forma predeterminada, solo se expande un nivel. Otra información, como los compositores, los nombres de tipo, los grupos y otros contenedores se coloca en una barra vertical (cuando se expande) junto con los elementos y atributos que encierran. Al hacer doble clic en una barra vertical, se vuelve horizontal y el árbol se contrae. Al hacer doble clic en una barra horizontal, se vuelve vertical y el árbol se expande. Al seleccionar la barra vertical, seleccionan todos los nodos en el contenedor. Los ampliadores aparecen a la derecha de un nodo si un elemento se puede expandir o contraer.

 Si la superficie de diseño está en blanco, el Editor XML, el **Explorador de esquemas XML**, y se muestran la marca de agua. El *marca de agua* es una lista de vínculos a todas las vistas del diseñador XSD. Si el conjunto de esquemas tiene errores, se muestra el texto siguiente al final de la lista: "Use la lista de errores para ver y corregir los errores en el conjunto de esquemas".

## <a name="breadcrumb-bar"></a>Barra de ruta de navegación

 La barra de ruta de navegación situada en la parte inferior de la vista Modelo de contenido muestra la ubicación del nodo seleccionado en el conjunto de esquemas.

## <a name="context-menus"></a>Menús contextuales

 Cuando hace doble clic en un elemento en la superficie de diseño o **área de trabajo** panel, aparece un menú contextual. En la siguiente tabla se describen las opciones que están disponibles para la superficie de diseño de la vista Modelo de contenido.

|Opción|Descripción|
|------------|-----------------|
|**Mostrar en Explorador de esquemas XML**|Coloca el foco en el Explorador de esquemas y resalta el nodo del conjunto de esquemas.|
|**Mostrar en vista de gráfico**|Cambia a la vista Gráfico.|
|**Generar XML de ejemplo**|Disponible solo para los elementos globales. Genera un archivo XML de ejemplo para el elemento global.|
|**Mostrar documentación**|Muestra u oculta el contenido del nodo Anotación/Documentación.|
|**Exportar diagrama como imagen**|Guarda la superficie de diseño en un archivo XPS.|
|**Ver código**|Abre el archivo que contiene el nodo seleccionado en el Editor XML. El elemento seleccionado en el **Explorador de esquemas XML** también está seleccionada en el Editor XML.|
|**Propiedades (ventana)**|Se abre la **propiedades** ventana (si no está ya abierto). Esta ventana muestra información sobre el nodo.|

 En la tabla siguiente se describe las opciones que están disponibles para la **área de trabajo** panel.

|Opción|Descripción|
|------------|-----------------|
|**Mostrar en Explorador de esquemas XML**|Coloca el foco en el Explorador de esquemas y resalta el nodo del conjunto de esquemas.|
|**Mostrar en vista de gráfico**|Cambia a la vista Gráfico.|
|**Borrar área de trabajo**|Borra el área de trabajo y la superficie de diseño.|
|**Quitar del área de trabajo**|Quita los nodos seleccionados del área de trabajo y de la superficie de diseño.|
|**Quitar todo salvo la selección de área de trabajo**|Quita los nodos que no están seleccionados del área de trabajo y de la superficie de diseño.|
|**Generar XML de ejemplo**|Disponible solo para los elementos globales. Genera un archivo XML de ejemplo para el elemento global.|
|**Seleccionar todo**|Selecciona todos los nodos en el **área de trabajo** panel.|
|**Ver código**|Abre el archivo que contiene el nodo seleccionado en el Editor XML. El elemento seleccionado en el **Explorador de esquemas XML** también está seleccionada en el Editor XML.|
|**Propiedades (ventana)**|Se abre la **propiedades** ventana (si no está ya abierto). Esta ventana muestra información sobre el nodo.|

## <a name="properties-window"></a>Propiedades (ventana)

 Use el menú contextual para abrir inicialmente la **propiedades** ventana. De forma predeterminada, el **propiedades** ventana aparece en la esquina inferior derecha de Visual Studio. Al hacer clic en un nodo que se presenta en la vista de modelo de contenido, las propiedades de ese nodo se muestran en la **propiedades** ventana.

## <a name="xsd-designer-toolbar"></a>Barra de herramientas del diseñador XSD

 Los siguientes botones de la barra de herramientas de Diseñador XSD están habilitados cuando está activa la vista Modelo de contenido.

 ![Barra de herramientas del Diseñador de esquemas XML](../xml-tools/media/xsdcontentmodelviewtoolbar.gif)

|Opción|Descripción|
|------------|-----------------|
|**Mostrar vista inicio**|Se activa en el [iniciar vista de](../xml-tools/start-view.md). Puede obtener acceso a esta vista usando el método abreviado de teclado: **Ctrl**+**1**.|
|**Mostrar vista modelo de contenido**|Se activa en el [vista del modelo de contenido](../xml-tools/content-model-view.md). Puede obtener acceso a esta vista usando el método abreviado de teclado: **Ctrl**+**2**.|
|**Mostrar vista Gráfico**|Se activa en el [vista gráfica](../xml-tools/graph-view.md). Puede obtener acceso a esta vista usando el método abreviado de teclado: **Ctrl**+**3**.|
|**Borrar área de trabajo**|Borra el área de trabajo y la superficie de diseño.|
|**Quitar del área de trabajo**|Quita los nodos seleccionados del área de trabajo y de la superficie de diseño.|
|**Quitar todo salvo la selección de área de trabajo**|Quita los nodos que no están seleccionados del área de trabajo y de la superficie de diseño.|
|**Mostrar documentación**|Muestra u oculta el contenido del nodo Anotación/Documentación.|

## <a name="panscroll"></a>Panorámica/desplazamiento

 Puede desplazar la superficie de diseño mediante el uso de las barras de desplazamiento o manteniendo presionada la **Ctrl** clave mientras hace clic y arrastre el mouse. Al aplicar una panorámica de la superficie de diseño con hacer clic y arrastrar, el cursor cambia a cuatro flechas cruzadas que señalan cuatro direcciones.

## <a name="undoredo"></a>Deshacer/rehacer

 La capacidad de deshacer/rehacer está habilitada en la vista Modelo de contenido para las siguientes acciones:

-   Agregar un nodo único arrastrándolo y colocándolo.

-   Agregar varios nodos desde la ventana de resultados de la búsqueda del Explorador de esquemas.

-   Agregar nodos desde la vista Inicio.

-   Eliminar uno o varios nodos.

## <a name="zoom"></a>Zoom

 Zoom está disponible en la esquina inferior derecha de la vista de modelo de contenido.

 El zoom se puede controlar de las maneras siguientes:

-   Manteniendo la **Ctrl** clave y girando el mouse wheel cuando se mantiene el mouse sobre la superficie de la vista modelo de contenido.

-   Usando el control deslizante. El control deslizante muestra el nivel de zoom actual.

El control deslizante del Zoom es opaco al seleccionarlo, mantenga el mouse sobre él o usar **Ctrl** con la rueda del mouse para hacer zoom; en el resto del tiempo, es transparente.

## <a name="xml-editor-integration"></a>Integración del editor XML

 Puede cambiar entre la **diseñador XSD** y el Editor XML mediante el menú contextual.

 Si realiza cambios en el esquema en el Editor de XML se sincronizan los cambios en la vista de modelo de contenido. Para obtener más información, consulte [integración con el editor XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Vea también

- [Área de trabajo del Diseñador de esquemas XML](../xml-tools/xml-schema-designer-workspace.md)
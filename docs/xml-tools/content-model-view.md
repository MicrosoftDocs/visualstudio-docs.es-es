---
title: Vista Modelo de contenido del Diseñador de esquemas XML
description: Obtenga información sobre la vista Modelo de contenido del diseñador de esquemas XAML que proporciona una representación gráfica de los nodos de esquema locales y globales, y sus componentes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05db6f02f2d00a5c0aca1ff91e15c61cf6bf8d4f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948601"
---
# <a name="content-model-view"></a>Vista Modelo de contenido

La vista Modelo de contenido proporciona una representación gráfica de los nodos de esquema globales y locales con sus componentes, incluidos los tipos simples y complejos, elementos, grupos de modelo, atributos y grupos de atributos. Los comentarios y las instrucciones de procesamiento XML no se pueden ver en el vista Modelo de contenido. La vista Modelo de contenido contiene dos paneles: un panel **Área de trabajo** que contiene una lista de los nodos del [Área de trabajo de Diseñador de esquemas XML](../xml-tools/xml-schema-designer-workspace.md) y la superficie de diseño donde puede ver el modelo de contenido de los nodos de esquema que están seleccionados en el panel **Área de trabajo**. La vista Modelo de contenido también incluye la barra de herramientas del Diseñador de esquemas XML y la barra de ruta de navegación.

En la siguiente imagen, el panel **Área de trabajo** contiene seis nodos de esquema. El nodo `purchaseOrder` está seleccionado en el panel **Área de trabajo** y se muestra en la superficie de diseño.

![Vista Modelo de contenido del Diseñador de esquemas XML](../xml-tools/media/xsddesigner_contentmodelview.gif)

## <a name="workspace-panel"></a>Panel Área de trabajo

Después de agregar los nodos al área de trabajo, la lista de nodos aparecerá en el panel **Área de trabajo** de la vista Modelo de contenido. Al seleccionar los nodos en el panel **Área de trabajo**, aparecen en la superficie de diseño de la vista Modelo de contenido. Para eliminar los nodos del área de trabajo, utilice la barra de herramientas de Diseñador XSD, el menú contextual del panel **Área de trabajo** o la tecla **Supr**.

Para obtener información sobre cómo agregar los nodos, vea la sección "Agregar nodos al área de trabajo" en [Área de trabajo del Diseñador de esquemas XML](../xml-tools/xml-schema-designer-workspace.md).

## <a name="design-surface"></a>Superficie de diseño

Cuando está seleccionado un nodo en el panel **Área de trabajo**, se agrega a la superficie de diseño de la vista Modelo de contenido, donde pueden verse los detalles del nodo.

El modelo de contenido de un nodo se representa con un árbol gráfico que puede expandirse, en el que los elementos y atributos aparecen como nodos del árbol. De forma predeterminada, solo se expande un nivel. Otra información, como los compositores, los nombres de tipo, los grupos y otros contenedores se coloca en una barra vertical (cuando se expande) junto con los elementos y atributos que encierran. Al hacer doble clic en una barra vertical, se vuelve horizontal y el árbol se contrae. Al hacer doble clic en una barra horizontal, se vuelve vertical y el árbol se expande. Al seleccionar la barra vertical, se seleccionan todos los nodos del contenedor. Los expansores aparecen a la derecha de un nodo si un elemento se puede expandir o contraer.

Si la superficie de diseño está en blanco, se mostrarán el editor XML, el **Explorador de esquemas XML** y la marca de agua. La *marca de agua* es una lista de vínculos a todas las vistas del Diseñador XSD. Si el conjunto de esquemas tiene errores, se muestra el texto siguiente al final de la lista: "Use la lista de errores para ver y corregir los errores en el conjunto de esquemas".

## <a name="breadcrumb-bar"></a>Barra de ruta de navegación

La barra de ruta de navegación situada en la parte inferior de la vista Modelo de contenido muestra la ubicación del nodo seleccionado en el conjunto de esquemas.

## <a name="context-menus"></a>Menús contextuales

Al hacer clic con el botón derecho en un elemento de la superficie de diseño o el panel **Área de trabajo**, aparece un menú contextual. En la siguiente tabla se describen las opciones que están disponibles para la superficie de diseño de la vista Modelo de contenido.

|Opción|Descripción|
|-|-----------------|
|**Mostrar en el Explorador de esquemas XML**|Coloca el foco en el Explorador de esquemas y resalta el nodo del conjunto de esquemas.|
|**Mostrar en la vista Gráfico**|Cambia a la vista Gráfico.|
|**Generar XML de ejemplo**|Disponible solo para los elementos globales. Genera un archivo XML de ejemplo para el elemento global.|
|**Mostrar documentación**|Muestra u oculta el contenido del nodo Anotación/Documentación.|
|**Exportar diagrama como imagen**|Guarda la superficie de diseño en un archivo XPS.|
|**Vista Código**|Abre el archivo que contiene el nodo seleccionado en el editor XML. El elemento que está seleccionado en el **Explorador de esquemas XML** también estará seleccionado en el editor XML.|
|**Propiedades (ventana)**|Abre la ventana **Propiedades** (si aún no está abierta). Esta ventana muestra información sobre el nodo.|

En la tabla siguiente se describen las opciones disponibles para el panel **Área de trabajo**.

|Opción|Descripción|
|-|-----------------|
|**Mostrar en el Explorador de esquemas XML**|Coloca el foco en el Explorador de esquemas y resalta el nodo del conjunto de esquemas.|
|**Mostrar en la vista Gráfico**|Cambia a la vista Gráfico.|
|**Borrar área de trabajo**|Borra el área de trabajo y la superficie de diseño.|
|**Quitar del área de trabajo**|Quita los nodos seleccionados del área de trabajo y de la superficie de diseño.|
|**Quitar todo salvo la selección del área de trabajo**|Quita los nodos que no están seleccionados del área de trabajo y de la superficie de diseño.|
|**Generar XML de ejemplo**|Disponible solo para los elementos globales. Genera un archivo XML de ejemplo para el elemento global.|
|**Seleccionar todo**|Selecciona todos los nodos del panel **Área de trabajo**.|
|**Vista Código**|Abre el archivo que contiene el nodo seleccionado en el editor XML. El elemento que está seleccionado en el **Explorador de esquemas XML** también estará seleccionado en el editor XML.|
|**Propiedades (ventana)**|Abre la ventana **Propiedades** (si aún no está abierta). Esta ventana muestra información sobre el nodo.|

## <a name="properties-window"></a>Propiedades (ventana)

Use el menú de clic con el botón derecho (contextual) para abrir inicialmente la ventana **Propiedades**. De forma predeterminada, la ventana **Propiedades** aparece en la esquina inferior derecha de Visual Studio. Al hacer clic en un nodo que se presenta en la vista Modelo de contenido, las propiedades de dicho nodo se muestran en la ventana **Propiedades**.

## <a name="xsd-designer-toolbar"></a>Barra de herramientas del diseñador XSD

Los siguientes botones de la barra de herramientas de Diseñador XSD están habilitados cuando está activa la vista Modelo de contenido.

![Barra de herramientas del Diseñador de esquemas XML](../xml-tools/media/xsdcontentmodelviewtoolbar.gif)

|Opción|Descripción|
|-|-----------------|
|**Mostrar vista Inicio**|Cambia a la [vista Inicio](../xml-tools/start-view.md). Se puede acceder a esta vista usando el método abreviado de teclado: **Ctrl**+**1**.|
|**Mostrar vista Modelo de contenido**|Cambia a la [vista Modelo de contenido](../xml-tools/content-model-view.md). Se puede acceder a esta vista usando el método abreviado de teclado: **Ctrl**+**2**.|
|**Mostrar vista Gráfico**|Cambia a la [vista Gráfico](../xml-tools/graph-view.md). Se puede acceder a esta vista usando el método abreviado de teclado: **Ctrl**+**3**.|
|**Borrar área de trabajo**|Borra el área de trabajo y la superficie de diseño.|
|**Quitar del área de trabajo**|Quita los nodos seleccionados del área de trabajo y de la superficie de diseño.|
|**Quitar todo salvo la selección del área de trabajo**|Quita los nodos que no están seleccionados del área de trabajo y de la superficie de diseño.|
|**Mostrar documentación**|Muestra u oculta el contenido del nodo Anotación/Documentación.|

## <a name="panscroll"></a>Panorámica/desplazamiento

Puede tener una panorámica de la superficie de diseño usando las barras de desplazamiento o manteniendo presionada la tecla **Ctrl** mientras hace clic y arrastra el mouse. Cuando se obtiene una panorámica de la superficie de diseño usando el método de hacer clic y arrastrar, el cursor cambia a cuatro flechas en cruz que señalan en cuatro direcciones.

## <a name="undoredo"></a>Deshacer/rehacer

La capacidad de deshacer/rehacer está habilitada en la vista Modelo de contenido para las siguientes acciones:

- Agregar un nodo único arrastrándolo y colocándolo.

- Agregar varios nodos desde la ventana de resultados de la búsqueda del Explorador de esquemas.

- Agregar nodos desde la vista Inicio.

- Eliminar uno o varios nodos.

## <a name="zoom"></a>Zoom

El zoom está disponible en la esquina inferior derecha de la vista Modelo de contenido.

El zoom se puede controlar de las maneras siguientes:

- Manteniendo presionada la tecla **Ctrl** y girando la rueda del mouse cuando este se mantiene sobre la superficie de la vista Modelo de contenido.

- Usando el control deslizante. El control deslizante muestra el nivel de zoom actual.

El control deslizante de zoom es opaco cuando se selecciona, al mantener el mouse sobre él o al usar **Ctrl** con la rueda del mouse para hacer zoom; en todos los demás casos, es transparente.

## <a name="xml-editor-integration"></a>Integración del editor XML

Puede alternar entre el **Diseñador XSD** y el editor XML utilizando el menú contextual.

Si realiza modificaciones en el conjunto de esquemas en el editor XML, dichas modificaciones se sincronizan en la vista Modelo de contenido. Para más información, consulte [Integración con el editor XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Vea también

- [Área de trabajo del Diseñador de esquemas XML](../xml-tools/xml-schema-designer-workspace.md)

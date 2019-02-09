---
title: Explorador de esquemas XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99ac977be83440bfd3e0b1436635bbeb9c39c0ec
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55915991"
---
# <a name="xml-schema-explorer"></a>Explorador de esquemas XML

El **Explorador de esquemas XML** está integrado con Microsoft Visual Studio y el Editor XML para permitirle trabajar con esquemas (XSD). Al abrir un archivo de esquema XML, el **del conjunto de esquemas** nodo aparece en el **Explorador de esquemas XML**. Todos los esquemas importados, incluidos o redefinidos para el archivo de destino, así como los archivos que se hace referencia mediante un `include` o `import` instrucción, también aparecen en la **Explorador de esquemas XML**.

 El **Explorador de esquemas XML** le permite hacer lo siguiente:

-   Obtener información general rápida del conjunto de esquemas.

-   Examinar y desplazarse por el árbol.

-   Realizar búsquedas específicas del esquema y de palabras clave. Para obtener más información, consulte [buscar el conjunto de esquemas](../xml-tools/searching-the-schema-set.md).

-   Agregar los resultados de búsqueda a la vista gráfico o modelo de contenido

-   Ordenar el árbol por documento, tipo o nombre. Para obtener más información, consulte [ordenación, filtrado y agrupación](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).

-   Abrir el Editor XML y saltar a las ubicaciones de código del archivo XSD. Para obtener más información, consulte [integración con el Editor XML](../xml-tools/integration-with-xml-editor.md).

-   Generar XML de ejemplo para elementos globales.

El **Explorador de esquemas XML** proporciona una vista jerárquica del esquema que se establecen a través de una vista de árbol. El **Explorador de esquemas XML** también proporciona búsqueda, filtrado, navegación y ordenación. Para tener acceso a la **Explorador de esquemas XML**, realice una de las siguientes acciones:

-   Si se encuentra en la [vista inicio](../xml-tools/start-view.md), haga clic en el **Explorador de esquemas XML** vínculo.

-   Si se encuentra en la [vista gráfico](../xml-tools/graph-view.md) o [vista modelo de contenido](../xml-tools/content-model-view.md) y tiene nodos en el área de trabajo, use el menú contextual (clic derecho) para seleccionar el **Explorador de esquemas XML**.

-   También puede seleccionar la **Explorador de esquemas XML** desde el **vista** menú.

-   Puede tener acceso a la **Explorador de esquemas XML** desde un *.vb* archivo que tiene un literal XML de Visual Basic asociado con un *.xsd* archivo. Para ver el esquema establecido el **Explorador de esquemas XML**, haga clic en un nodo XML en un literal XML o una importación de espacio de nombres XML y seleccione el **mostrar en el Explorador de esquema** comando. Para obtener más información, consulte [literales integración de XML con el Explorador de esquemas XML](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).

## <a name="tree-view"></a>Vista de árbol
 El **Explorador de esquemas XML** información del conjunto de esquemas de muestra previamente compilado en una estructura de árbol. La estructura de árbol está organizada de la forma siguiente:

-   En la parte superior está el nodo del conjunto de esquemas.

-   El segundo nivel contiene los espacios de nombres.

-   El tercer nivel contiene los archivos.

-   El cuarto nivel contiene los nodos globales. Esto puede incluir elementos, grupos, tipos complejos, tipos simples, atributos, grupos de atributos e instrucciones `include`, `import` y `redefine`.

A continuación se muestra un ejemplo de estructura de árbol:

![Explorador de esquemas XML](../xml-tools/media/xmlschemaexplorer.gif)

## <a name="selection-and-activation"></a>Selección y activación
 Para resaltar y seleccionar un nodo, haga clic una vez en el Explorador de esquemas.

 Para activar un nodo, haga doble clic en él o presione **ENTRAR** cuando se selecciona el nodo.

-   Al activar un nodo, se abre el archivo en el que está definido (si no está abierto ya) y se selecciona el nodo en dicho archivo.

-   Al activar un nodo de archivo, se abre el archivo seleccionado (si no está abierto ya) y se resalta el nodo del `<schema>`.

-   Al activar un nodo de espacio de nombres o de conjunto de esquemas no se realiza ninguna acción.

## <a name="drag-and-drop-nodes"></a>Arrastre y coloque nodos
 Puede arrastrar y colocar nodos globales, de archivo y de espacio de nombres en una vista del Diseñador XSD. Si la vista actual es el [vista inicio](../xml-tools/start-view.md), arrastre un nodo en la vista se abrirá el [vista gráfico](../xml-tools/graph-view.md). Si la vista actual es el [vista modelo de contenido](../xml-tools/content-model-view.md) o vista de gráfico, la vista no cambiará al colocar un nodo sobre ella.

 Al colocar los archivos en la vista se agregarán todos los nodos globales en el archivo para el [área de trabajo de diseñador XSD](../xml-tools/xml-schema-designer-workspace.md). Al colocar los espacios de nombres en la vista, se agregarán al área de trabajo todos los nodos globales del espacio de nombres. El área de trabajo la comparten todas las vistas.

 No es posible arrastrar y colocar nodos locales ni importaciones.

## <a name="see-also"></a>Vea también

- [Cómo: Agregar nodos al área de trabajo desde el Explorador de esquemas XML](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)
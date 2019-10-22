---
title: 'Cómo: agregar nodos al área de trabajo desde el explorador de esquemas XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e0c8fe9d5ba8c096a03de7a9df85945f4aeb4a0a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656344"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Cómo: Agregar nodos al área de trabajo desde el Explorador de esquemas XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se explica cómo agregar nodos al [área de trabajo del diseñador de esquemas XML](../xml-tools/xml-schema-designer-workspace.md) desde el explorador de esquemas XML. Eso puede lograrse arrastrando y colocando nodos desde el Explorador de esquemas XML hasta una vista del Diseñador XSD o usando el menú contextual del Explorador de esquemas XML. También puede agregar los nodos que se resaltan como resultado de una búsqueda realizada por el Explorador de esquemas XML. Para obtener más información, consulte [Cómo: agregar nodos de resultados de búsqueda del conjunto de esquemas al área de trabajo](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> Solo se pueden agregar nodos globales al [área de trabajo del diseñador de esquemas XML](../xml-tools/xml-schema-designer-workspace.md).

### <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Para agregar nodos mediante el menú contextual del Explorador de esquemas XML

1. Siga los pasos descritos en [Cómo: crear y editar un archivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Haga clic con el botón secundario del mouse en el nodo `PurchaseOrderType` en el Explorador XSD. Seleccione **Mostrar en la vista gráfico**.

     El nodo `purchaseOrderType` aparece en la superficie de diseño de la vista Gráfico.

### <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Para arrastrar y colocar un nodo en una vista

1. Haga clic con el botón secundario del mouse en el nodo `PurchaseOrderType` de la vista Gráfico. Seleccione **Mostrar en el explorador de esquemas XML**.

     El nodo se resalta en el Explorador de esquemas XML.

2. Haga clic con el botón secundario en el nodo `PurchaseOrderType` en el explorador de esquemas XML y seleccione **Mostrar todas las referencias**.

     Se resalta el nodo `purchaseOrder`.

3. Arrastre el nodo `purchaseOrder` hasta la vista Gráfico.

     Los nodos `purchaseOrder` y `PurchaseOrderType` aparecen uno al lado del otro en la superficie de diseño de la vista Gráfico. Dado que los dos nodos están relacionados (el elemento `purchaseOrder` es del tipo `PurchaseOrderType`), se dibuja una flecha entre ellos.

### <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Para agregar nodos usando la capacidad de búsqueda del Explorador de esquemas

1. Escriba "purchaseOrder" en el cuadro de texto buscar de la barra de herramientas del [Explorador XML](../xml-tools/xml-schema-explorer.md) y haga clic en el botón Buscar.

     ![Búsqueda de palabras clave del explorador de esquema XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

     Los resultados de la búsqueda se resaltan en el Explorador de esquemas XML y se marcan en la barra de desplazamiento vertical.

2. Agregue los resultados de la búsqueda al área de trabajo haciendo clic en el botón **agregar nodos resaltados al área de trabajo** en el panel de resultados de resumen.

     ![Resultado de búsqueda del explorador de esquemas XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

     Los nodos `purchaseOrder` y `PurchaseOrderType` aparecen junto a los demás en la superficie de diseño de la [vista gráfico](../xml-tools/graph-view.md). Dado que los dos nodos están relacionados (el elemento `purchaseOrder` es del tipo `PurchaseOrderType`), se dibuja una flecha entre ellos.

## <a name="see-also"></a>Vea también
 [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md)

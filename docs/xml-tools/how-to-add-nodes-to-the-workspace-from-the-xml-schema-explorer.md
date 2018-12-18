---
title: 'Cómo: Agregar nodos al área de trabajo desde el Explorador de esquemas XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e1f5821d3a4207d89eb62b9344cff967c73b536
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752058"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Cómo: agregar nodos al área de trabajo desde el Explorador de esquemas XML

Este tema explica cómo agregar nodos a la [área de trabajo del Diseñador de esquemas XML](../xml-tools/xml-schema-designer-workspace.md) desde el **Explorador de esquemas XML**. Esto puede lograrse arrastrando y colocando nodos desde el **Explorador de esquemas XML** en una vista de diseñador XSD, o mediante el uso de la **del explorador de esquemas XML** menú contextual. También puede agregar nodos que se resaltan como resultado de una búsqueda realizada por el **Explorador de esquemas XML**. Para obtener más información, consulte [Cómo: agregar nodos de resultados de búsqueda de conjunto de esquema para el área de trabajo](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> Solo los nodos globales se pueden agregar a la [área de trabajo del Diseñador de esquemas XML](../xml-tools/xml-schema-designer-workspace.md).

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Para agregar nodos mediante el menú contextual de explorador de XML

1.  Siga los pasos de [Cómo: crear y editar un archivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Haga clic con el botón secundario en el `PurchaseOrderType` nodo en el Explorador de XSD. Seleccione **mostrar en vista de gráfico**.

     El nodo `purchaseOrderType` aparece en la superficie de diseño de la vista Gráfico.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Para arrastrar y colocar un nodo en una vista

1.  Haga doble clic en el `PurchaseOrderType` nodo en la vista gráfico. Seleccione **mostrar en Explorador de esquemas XML**.

     El nodo se resalta en el **Explorador de esquemas XML**.

2.  Haga clic con el botón secundario en el `PurchaseOrderType` nodo en el **Explorador de esquemas XML** y seleccione **mostrar todas las referencias**.

     Se resalta el nodo `purchaseOrder`.

3.  Arrastre el nodo `purchaseOrder` hasta la vista Gráfico.

     Los nodos `purchaseOrder` y `PurchaseOrderType` aparecen uno al lado del otro en la superficie de diseño de la vista Gráfico. Dado que los dos nodos están relacionados (el elemento `purchaseOrder` es del tipo `PurchaseOrderType`), se dibuja una flecha entre ellos.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Para agregar nodos usando la capacidad de búsqueda del Explorador de esquemas

1.  Escriba "purchaseOrder" en el cuadro de texto de búsqueda de la [explorador XML](../xml-tools/xml-schema-explorer.md) barra de herramientas y haga clic en el botón de búsqueda.

     ![Búsqueda de palabras clave en el Explorador de esquemas XML](../xml-tools/media/schemaexplorersearch.gif)

     Los resultados de búsqueda se resaltan en el **Explorador de esquemas XML** y se marcan en la barra de desplazamiento vertical.

2.  Agregar los resultados de búsqueda al área de trabajo haciendo clic en el **agregar nodos resaltados al área de trabajo** botón en el panel de resultados de resumen.

     ![Resultado de búsqueda en el Explorador de esquemas XML](../xml-tools/media/schemaexplorersearchresult.gif)

     El `purchaseOrder` nodo y `PurchaseOrderType` nodo aparece junto a la otra en la superficie de diseño de la [vista gráfico](../xml-tools/graph-view.md). Dado que los dos nodos están relacionados (el elemento `purchaseOrder` es del tipo `PurchaseOrderType`), se dibuja una flecha entre ellos.

## <a name="see-also"></a>Vea también

- [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md)
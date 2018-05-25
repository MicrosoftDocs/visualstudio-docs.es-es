---
title: Agregar nodos de resultados de búsqueda XML esquemas conjunto al área de trabajo
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f6629aef7549a78f7cfdb73bb6d7ee0be3ac7412
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Cómo: agregar nodos de resultados de búsqueda de conjunto de esquema para el área de trabajo

Este tema explica cómo agregar nodos que están resaltados en el **Explorador de esquemas XML** como resultado de una búsqueda de palabra clave en el área de trabajo.

> [!NOTE]
> Solo los nodos globales se pueden agregar a la [área de trabajo](../xml-tools/xml-schema-designer-workspace.md).


 En este ejemplo se utiliza el ejemplo [esquema de pedido de compra](../xml-tools/sample-xsd-file-purchase-order-schema.md).

## <a name="to-add-schema-set-result-nodes"></a>Para agregar nodos de resultados del conjunto de esquemas

1.  Siga los pasos de [Cómo: crear y editar un archivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Escriba "purchaseOrder" en el cuadro de texto de búsqueda de la [explorador XML](../xml-tools/xml-schema-explorer.md) barra de herramientas y haga clic en el botón de búsqueda.

     ![Búsqueda de palabra clave de explorador de esquemas XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

     Los resultados de búsqueda se resaltan en el **Explorador de esquemas XML** y se marcan en la barra de desplazamiento vertical.

3.  Agregar los resultados de búsqueda al área de trabajo haciendo clic en el **agregar nodos resaltados al área de trabajo** botón en el panel de resultados de resumen.

     ![Resultado de búsqueda del explorador de esquemas XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

     El `purchaseOrder` nodo y `PurchaseOrderType` nodo aparece junto a la otra en la superficie de diseño de la [vista gráfico](../xml-tools/graph-view.md). Dado que los dos nodos están relacionados (el elemento `purchaseOrder` es del tipo `PurchaseOrderType`), se dibuja una flecha entre ellos.
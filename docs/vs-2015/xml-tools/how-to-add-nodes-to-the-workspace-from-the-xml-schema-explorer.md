---
title: Procedimiento Agregar nodos al área de trabajo desde el Explorador de esquemas XML | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1fef367b36a683111369b656c8c1ba5a285fe6df
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63417464"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Procedimiento Agregar nodos al área de trabajo desde el Explorador de esquemas XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se explica cómo agregar nodos a la [área de trabajo del Diseñador de esquemas XML](../xml-tools/xml-schema-designer-workspace.md) desde el Explorador de esquemas XML. Eso puede lograrse arrastrando y colocando nodos desde el Explorador de esquemas XML hasta una vista del Diseñador XSD o usando el menú contextual del Explorador de esquemas XML. También puede agregar los nodos que se resaltan como resultado de una búsqueda realizada por el Explorador de esquemas XML. Para obtener más información, vea [Cómo: Agregar nodos de resultados de búsqueda de conjunto de esquemas al área de trabajo](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).  
  
> [!NOTE]
> Solo los nodos globales se pueden agregar a la [área de trabajo del Diseñador de esquemas de XML](../xml-tools/xml-schema-designer-workspace.md).  
  
### <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Para agregar nodos mediante el menú contextual del Explorador de esquemas XML  
  
1. Siga los pasos de [Cómo: Crear y editar un archivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2. Haga clic con el botón secundario del mouse en el nodo `PurchaseOrderType` en el Explorador XSD. Seleccione **mostrar en vista de gráfico**.  
  
     El nodo `purchaseOrderType` aparece en la superficie de diseño de la vista Gráfico.  
  
### <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Para arrastrar y colocar un nodo en una vista  
  
1. Haga clic con el botón secundario del mouse en el nodo `PurchaseOrderType` de la vista Gráfico. Seleccione **mostrar en Explorador de esquemas XML**.  
  
     El nodo se resalta en el Explorador de esquemas XML.  
  
2. Haga clic con el botón derecho en el `PurchaseOrderType` nodo en el Explorador de esquemas XML y seleccione **mostrar todas las referencias**.  
  
     Se resalta el nodo `purchaseOrder`.  
  
3. Arrastre el nodo `purchaseOrder` hasta la vista Gráfico.  
  
     Los nodos `purchaseOrder` y `PurchaseOrderType` aparecen uno al lado del otro en la superficie de diseño de la vista Gráfico. Dado que los dos nodos están relacionados (el elemento `purchaseOrder` es del tipo `PurchaseOrderType`), se dibuja una flecha entre ellos.  
  
### <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Para agregar nodos usando la capacidad de búsqueda del Explorador de esquemas  
  
1. Escriba "purchaseOrder" en el cuadro de texto de búsqueda de la [explorador XML](../xml-tools/xml-schema-explorer.md) barra de herramientas y haga clic en el botón de búsqueda.  
  
     ![Búsqueda de palabra clave de explorador de esquemas XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     Los resultados de la búsqueda se resaltan en el Explorador de esquemas XML y se marcan en la barra de desplazamiento vertical.  
  
2. Agregar los resultados de búsqueda al área de trabajo, haga clic en el **agregar nodos resaltados al área de trabajo** botón en el panel de resultados de resumen.  
  
     ![Resultado de búsqueda de explorador de esquema XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     El `purchaseOrder` nodo y el `PurchaseOrderType` nodo aparecen junto a la otra en la superficie de diseño de la [vista gráfico](../xml-tools/graph-view.md). Dado que los dos nodos están relacionados (el elemento `purchaseOrder` es del tipo `PurchaseOrderType`), se dibuja una flecha entre ellos.  
  
## <a name="see-also"></a>Vea también  
 [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md)

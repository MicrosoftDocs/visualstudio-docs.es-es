---
title: Incorporación de nodos al área de trabajo desde el Explorador de esquemas XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2049b8da1caa4e0af0afc52aec6e75f499d85b8b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592820"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Procedimiento Adición de nodos al área de trabajo desde el Explorador de esquemas XML

En este tema se explica cómo agregar nodos al [área de trabajo del Diseñador de esquemas XML](../xml-tools/xml-schema-designer-workspace.md) desde el **Explorador de esquemas XML**. Eso puede lograrse arrastrando y colocando nodos desde el **Explorador de esquemas XML** hasta una vista del Diseñador XSD o usando el menú contextual del **Explorador de esquemas XML**. También puede agregar los nodos que se resaltan como resultado de una búsqueda realizada por el **Explorador de esquemas XML**. Para obtener más información, vea [Cómo: Incorporación de nodos de resultados de búsqueda del conjunto de esquemas al área de trabajo](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> Solo se pueden agregar nodos globales al [espacio de trabajo del Diseñador de esquemas XML](../xml-tools/xml-schema-designer-workspace.md).

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Para agregar nodos mediante el menú contextual del Explorador de esquemas XML

1. Siga los pasos que se describen en [Procedimientos: Creación y edición de un archivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Haga clic con el botón derecho del mouse en el nodo `PurchaseOrderType` en el Explorador XSD. Seleccione **Mostrar en la vista Gráfico**.

     El nodo `purchaseOrderType` aparece en la superficie de diseño de la vista Gráfico.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Para arrastrar y colocar un nodo en una vista

1. Haga clic con el botón derecho del mouse en el nodo `PurchaseOrderType` de la vista Gráfico. Seleccione **Mostrar en el Explorador de esquemas XML**.

     El nodo se resalta en el **Explorador de esquemas XML**.

2. Haga clic con el botón derecho del mouse en el nodo `PurchaseOrderType` en el **Explorador de esquemas XML** y seleccione **Mostrar todas las referencias**.

     Se resalta el nodo `purchaseOrder`.

3. Arrastre el nodo `purchaseOrder` hasta la vista Gráfico.

     Los nodos `purchaseOrder` y `PurchaseOrderType` aparecen uno al lado del otro en la superficie de diseño de la vista Gráfico. Dado que los dos nodos están relacionados (el elemento `purchaseOrder` es del tipo `PurchaseOrderType`), se dibuja una flecha entre ellos.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Para agregar nodos usando la capacidad de búsqueda del Explorador de esquemas

1. Escriba "purchaseOrder" en el cuadro de texto de búsqueda de la barra de herramientas del [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md) y haga clic en el botón de búsqueda.

     ![Búsqueda de palabras clave en el Explorador de esquemas XML](../xml-tools/media/schemaexplorersearch.gif)

     Los resultados de la búsqueda se resaltan en el **Explorador de esquemas XML** y se marcan en la barra de desplazamiento vertical.

2. Agregue los resultados de la búsqueda al área de trabajo; para ello, haga clic en el botón **Agregar nodos resaltados al área de trabajo** en el panel de resumen de resultados.

     ![Resultado de búsqueda en el Explorador de esquemas XML](../xml-tools/media/schemaexplorersearchresult.gif)

     Los nodos `purchaseOrder` y `PurchaseOrderType` aparecen uno al lado del otro en la superficie de diseño de la [Vista de gráfico](../xml-tools/graph-view.md). Dado que los dos nodos están relacionados (el elemento `purchaseOrder` es del tipo `PurchaseOrderType`), se dibuja una flecha entre ellos.

## <a name="see-also"></a>Vea también

- [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md)

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
ms.openlocfilehash: 04e74057bd059c82010678b7de571ff180e7fbfe
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751915"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Cómo: agregar nodos de resultados de búsqueda de conjunto de esquema para el área de trabajo

Este tema explica cómo agregar nodos que están resaltados en el **Explorador de esquemas XML** como resultado de una búsqueda de palabra clave en el área de trabajo.

> [!NOTE]
> Solo los nodos globales se pueden agregar a la [área de trabajo](../xml-tools/xml-schema-designer-workspace.md).


 En este ejemplo se utiliza el ejemplo [esquema de pedido de compra](../xml-tools/sample-xsd-file-purchase-order-schema.md).

## <a name="to-add-schema-set-result-nodes"></a>Para agregar nodos de resultados del conjunto de esquemas

1.  Siga los pasos de [Cómo: crear y editar un archivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Escriba "purchaseOrder" en el cuadro de texto de búsqueda de la [explorador XML](../xml-tools/xml-schema-explorer.md) barra de herramientas y haga clic en el botón de búsqueda.

     ![Búsqueda de palabras clave en el Explorador de esquemas XML](../xml-tools/media/schemaexplorersearch.gif)

     Los resultados de búsqueda se resaltan en el **Explorador de esquemas XML** y se marcan en la barra de desplazamiento vertical.

3.  Agregar los resultados de búsqueda al área de trabajo haciendo clic en el **agregar nodos resaltados al área de trabajo** botón en el panel de resultados de resumen.

     ![Resultado de búsqueda en el Explorador de esquemas XML](../xml-tools/media/schemaexplorersearchresult.gif)

     El `purchaseOrder` nodo y `PurchaseOrderType` nodo aparece junto a la otra en la superficie de diseño de la [vista gráfico](../xml-tools/graph-view.md). Dado que los dos nodos están relacionados (el elemento `purchaseOrder` es del tipo `PurchaseOrderType`), se dibuja una flecha entre ellos.
---
title: Agregar nodos de resultados de búsqueda del conjunto de esquemas XML al área de trabajo
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7cb8e66292a1cdb393401d180bd8b9f8691dc8f0
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913933"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Filtrar Agregar nodos de resultados de búsqueda de conjunto de esquemas al área de trabajo

En este tema se explica cómo agregar nodos que están resaltados en la **Explorador de esquemas XML** como resultado de una búsqueda de palabra clave en el área de trabajo.

> [!NOTE]
> Solo los nodos globales se pueden agregar a la [área de trabajo](../xml-tools/xml-schema-designer-workspace.md).


 En este ejemplo se utiliza el ejemplo [esquema de pedido de compra](../xml-tools/sample-xsd-file-purchase-order-schema.md).

## <a name="to-add-schema-set-result-nodes"></a>Para agregar nodos de resultados del conjunto de esquemas

1.  Siga los pasos de [Cómo: Crear y editar un archivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Escriba "purchaseOrder" en el cuadro de texto de búsqueda de la [explorador XML](../xml-tools/xml-schema-explorer.md) barra de herramientas y haga clic en el botón de búsqueda.

     ![Búsqueda de palabras clave en el Explorador de esquemas XML](../xml-tools/media/schemaexplorersearch.gif)

     Los resultados de búsqueda se resaltan en la **Explorador de esquemas XML** y marcan en la barra de desplazamiento vertical.

3.  Agregar los resultados de búsqueda al área de trabajo, haga clic en el **agregar nodos resaltados al área de trabajo** botón en el panel de resultados de resumen.

     ![Resultado de búsqueda en el Explorador de esquemas XML](../xml-tools/media/schemaexplorersearchresult.gif)

     El `purchaseOrder` nodo y el `PurchaseOrderType` nodo aparecen junto a la otra en la superficie de diseño de la [vista gráfico](../xml-tools/graph-view.md). Dado que los dos nodos están relacionados (el elemento `purchaseOrder` es del tipo `PurchaseOrderType`), se dibuja una flecha entre ellos.
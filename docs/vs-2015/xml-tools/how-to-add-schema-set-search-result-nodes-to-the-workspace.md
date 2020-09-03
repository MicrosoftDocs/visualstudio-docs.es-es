---
title: 'Cómo: agregar nodos de resultados de búsqueda del conjunto de esquemas al área de trabajo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b34be331ad3ec67e2c3bd8d9ecc500cd256b1b09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666549"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Cómo: Agregar nodos de resultados de búsqueda del conjunto de esquemas al área de trabajo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se explica cómo agregar nodos que están resaltados en el Explorador de esquemas XML como el resultado de una búsqueda de palabras claves en el área de trabajo.

> [!NOTE]
> Solo se pueden agregar nodos globales al [espacio de trabajo](../xml-tools/xml-schema-designer-workspace.md).

 En este ejemplo se usa el [esquema del pedido de compra](../xml-tools/sample-xsd-file-purchase-order-schema.md)de ejemplo.

### <a name="to-add-schema-set-result-nodes"></a>Para agregar nodos de resultados del conjunto de esquemas

1. Siga los pasos descritos en [Cómo: crear y editar un archivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Escriba "purchaseOrder" en el cuadro de texto de búsqueda de la barra de herramientas del [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md) y haga clic en el botón de búsqueda.

     ![Búsqueda de palabras clave en el Explorador de esquemas XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

     Los resultados de la búsqueda se resaltan en el Explorador de esquemas XML y se marcan en la barra de desplazamiento vertical.

3. Agregue los resultados de la búsqueda al área de trabajo; para ello, haga clic en el botón **Agregar nodos resaltados al área de trabajo** en el panel de resumen de resultados.

     ![Resultado de búsqueda en el Explorador de esquemas XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

     Los nodos `purchaseOrder` y `PurchaseOrderType` aparecen uno al lado del otro en la superficie de diseño de la [Vista de gráfico](../xml-tools/graph-view.md). Dado que los dos nodos están relacionados (el elemento `purchaseOrder` es del tipo `PurchaseOrderType`), se dibuja una flecha entre ellos.

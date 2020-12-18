---
title: Adición de nodos de resultados de búsqueda del conjunto de esquemas
description: Descubra cómo agregar nodos que están resaltados en el Explorador de esquemas XML como el resultado de una búsqueda de palabra clave en el área de trabajo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cffced7a0b680932a1f2b17bd1261e160563462c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996284"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Procedimiento Adición de nodos de resultados de búsqueda del conjunto de esquemas al área de trabajo

En este tema se explica cómo agregar nodos que están resaltados en el **Explorador de esquemas XML** como el resultado de una búsqueda de palabras claves en el área de trabajo.

> [!NOTE]
> Solo se pueden agregar nodos globales al [espacio de trabajo](../xml-tools/xml-schema-designer-workspace.md).

En este ejemplo se utiliza el ejemplo [Esquema de pedido de compra](../xml-tools/sample-xsd-file-purchase-order-schema.md).

## <a name="to-add-schema-set-result-nodes"></a>Para agregar nodos de resultados del conjunto de esquemas

1. Siga los pasos que se describen en [Procedimientos: Creación y edición de un archivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Escriba "purchaseOrder" en el cuadro de texto de búsqueda de la barra de herramientas del [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md) y haga clic en el botón de búsqueda.

     ![Búsqueda de palabras clave en el Explorador de esquemas XML](../xml-tools/media/schemaexplorersearch.gif)

     Los resultados de la búsqueda se resaltan en el **Explorador de esquemas XML** y se marcan en la barra de desplazamiento vertical.

3. Agregue los resultados de la búsqueda al área de trabajo; para ello, haga clic en el botón **Agregar nodos resaltados al área de trabajo** en el panel de resumen de resultados.

     ![Resultado de búsqueda en el Explorador de esquemas XML](../xml-tools/media/schemaexplorersearchresult.gif)

     Los nodos `purchaseOrder` y `PurchaseOrderType` aparecen uno al lado del otro en la superficie de diseño de la [Vista de gráfico](../xml-tools/graph-view.md). Dado que los dos nodos están relacionados (el elemento `purchaseOrder` es del tipo `PurchaseOrderType`), se dibuja una flecha entre ellos.

---
title: 'Cómo: agregar nodos de resultados de búsqueda de conjunto de esquemas al área de trabajo | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 75f254a8f64c3750a3c89e10016a0520d3760847
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210371"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Cómo: Agregar nodos de resultados de búsqueda del conjunto de esquemas al área de trabajo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
En este tema se explica cómo agregar nodos que están resaltados en el Explorador de esquemas XML como el resultado de una búsqueda de palabras claves en el área de trabajo.  
  
> [!NOTE]
>  Solo los nodos globales se pueden agregar a la [área de trabajo](../xml-tools/xml-schema-designer-workspace.md).  
  
 En este ejemplo se utiliza el ejemplo [esquema de pedido de compra](../xml-tools/sample-xsd-file-purchase-order-schema.md).  
  
### <a name="to-add-schema-set-result-nodes"></a>Para agregar nodos de resultados del conjunto de esquemas  
  
1.  Siga los pasos de [Cómo: crear y editar un archivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  Escriba "purchaseOrder" en el cuadro de texto de búsqueda de la [explorador XML](../xml-tools/xml-schema-explorer.md) barra de herramientas y haga clic en el botón de búsqueda.  
  
     ![Búsqueda de palabra clave de explorador de esquemas XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     Los resultados de la búsqueda se resaltan en el Explorador de esquemas XML y se marcan en la barra de desplazamiento vertical.  
  
3.  Agregar los resultados de búsqueda al área de trabajo, haga clic en el **agregar nodos resaltados al área de trabajo** botón en el panel de resultados de resumen.  
  
     ![Resultado de búsqueda de explorador de esquema XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     El `purchaseOrder` nodo y el `PurchaseOrderType` nodo aparecen junto a la otra en la superficie de diseño de la [vista gráfico](../xml-tools/graph-view.md). Dado que los dos nodos están relacionados (el elemento `purchaseOrder` es del tipo `PurchaseOrderType`), se dibuja una flecha entre ellos.




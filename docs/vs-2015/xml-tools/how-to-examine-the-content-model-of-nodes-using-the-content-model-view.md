---
title: 'Cómo: examinar el modelo de contenido de los nodos mediante la vista de modelo de contenido | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 25e47eed752a78caebcbae66a527cc847ac7d8f7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566135"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Cómo: Examinar el Modelo de contenido de los nodos mediante la vista de Modelo de contenido
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: examinar el contenido modelo de nodos con la vista de modelo de contenido](https://docs.microsoft.com/visualstudio/xml-tools/how-to-examine-the-content-model-of-nodes-using-the-content-model-view).  
  
  
En este tema se describe cómo explorar los nodos mediante el [vista modelo de contenido](../xml-tools/content-model-view.md).  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Para crear un nuevo archivo XSD y mostrar el elemento raíz en el vista Modelo de contenido  
  
1.  Cree un nuevo archivo de esquema XML.  
  
2.  Haga clic en **Use el Editor XML para ver y editar el archivo de esquema XML subyacente** en la vista inicio.  
  
3.  Copie el código de ejemplo de esquema XML de [esquema XML de ejemplo: esquema de pedido de compra](../xml-tools/sample-xsd-file-purchase-order-schema.md) y péguelo para reemplazar el código que se ha agregado el nuevo archivo XSD de forma predeterminada.  
  
4.  Seleccione el `purchaseOrder` elemento en el Explorador de esquema haciendo clic con el `purchaseOrder` elemento en el Editor XML y seleccionando **mostrar en explorador XML**.  
  
5.  Haga clic en el `purchaseOrder` en el Explorador de XML y seleccione **mostrar en vista de modelo de contenido**.  
  
     La vista Modelo de contenido muestra el elemento `purchaseOrder` en la superficie de diseño.  
  
6.  Expanda los nodos `shipTo`, `billTo` y `items` haciendo doble clic en cada nodo o haciendo clic en la flecha doble situada a la derecha de cada nodo.  
  
     Los nodos del elemento `purchaseOrder` se expanden y puede ver el modelo de contenido del elemento.  
  
7.  Haga clic en cualquier nodo situado debajo del elemento `purchaseOrder` y busque en la barra de ruta de navegación dónde se encuentra el nodo seleccionado dentro del conjunto de esquemas.  
  
8.  Haga clic en el **Mostrar documentación** botón en la barra de herramientas de XSD para ver la documentación. También puede hacer clic con el botón secundario en la superficie de diseño para ver la documentación.  
  
9. Haga clic el `purchaseOrder` nodo y seleccione **generar XML de ejemplo** para ver el documento de instancia XML.




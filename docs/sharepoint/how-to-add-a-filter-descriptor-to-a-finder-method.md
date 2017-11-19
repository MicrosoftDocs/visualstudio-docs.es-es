---
title: "Cómo: agregar un Descriptor de filtro a un método de buscador | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
ms.assetid: 228a6190-8cb8-4182-b6d9-d4c656f4a164
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 37aff0510af501b75aafe190fc412a0d4b9fd625
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Cómo: Agregar un descriptor de filtro para un método Finder
  Descriptores de filtro permiten a los consumidores del modelo pasar valores a métodos antes de ejecutarlos. Para obtener más información, consulte [diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Un escenario común es que los usuarios de SharePoint van a recuperar las instancias de un tipo de contenido externo que cumplen algunos criterios. Puede admitir este escenario agregando un descriptor de filtro a un método Finder.  
  
### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Para agregar un descriptor de filtro a un método Finder  
  
1.  En el **detalles del método de BDC** ventana, expanda el nodo de un método Finder, expanda el **parámetros** nodo y, a continuación, agregue un parámetro de entrada. Para obtener más información, consulte [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md).  
  
2.  En el **detalles del método** ventana, elija el descriptor de tipo del parámetro.  
  
3.  En la barra de menús, elija **vista**, **ventana propiedades**.  
  
4.  En el **propiedades** ventana, establezca el **nombre de tipo** propiedad a un tipo de datos que es adecuado para el filtro.  
  
     Por ejemplo, un filtro podría utilizar una fecha de pedido para limitar el número de pedidos de venta devueltos por el método. Para admitir ese filtro, el **nombre de tipo** propiedad del descriptor de tipo debe establecerse en **System.DateTime**.  
  
5.  En el **detalles del método** ventana, expanda la **descriptores de filtro** nodo.  
  
6.  En **agregar un Descriptor de filtro** elija **crear Descriptor de filtro**.  
  
     Un nuevo descriptor de filtro aparece debajo del **descriptores de filtro** nodo.  
  
7.  En la barra de menús, elija **vista**, **ventana propiedades**.  
  
8.  En el **propiedades** ventana, elija la **tipo** propiedad.  
  
9. En la lista que aparece para el **tipo** propiedad, elija el modelo de filtrado que desee.  
  
     Por ejemplo, para crear un filtro que utiliza una fecha de pedido para limitar el número de pedidos de venta devueltos en un método Finder, elija **comparación**. Un filtro de comparación garantiza que un método finder devuelve solo las instancias que cumplen una condición específica. Para obtener más información acerca de cada modelo de filtrado, consulte [tipos de filtros admitidos por la BDC](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
10. En el **propiedades** ventana, elija la **Associated Type Descriptors** propiedad.  
  
11. En la lista que aparece para el **Associated Type Descriptors** propiedad, elija el descriptor de tipo que creó anteriormente en este procedimiento. Esto está relacionado con el filtro para el parámetro de entrada del método de buscador.  
  
12. Agregue código al método Finder que devuelve los datos. Puede usar el parámetro de entrada como condición en una consulta select.  
  
     En el ejemplo siguiente se devuelve los pedidos de ventas que tienen la fecha de pedido especificado.  
  
    > [!NOTE]  
    >  Sustituya el valor de la `ServerName` campo con el nombre del servidor.  
  
     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Cómo: agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Cómo: definir el Descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Integrar Datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  
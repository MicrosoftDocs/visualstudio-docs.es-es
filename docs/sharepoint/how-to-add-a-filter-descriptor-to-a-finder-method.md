---
title: 'Cómo: agregar un Descriptor de filtro a un método de buscador | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 63374f4d96c86ea3eafbd4c6fa3fbe3d1f5a5899
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755604"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Cómo: agregar un descriptor de filtro a un método Finder
  Descriptores de filtro permiten a los consumidores del modelo pasar valores a los métodos antes de ejecutarlos. Para obtener más información, consulte [diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Un escenario común es que los usuarios de SharePoint va a recuperar las instancias de un tipo de contenido externo que coincidan con ciertos criterios. Puede admitir este escenario mediante la adición de un descriptor de filtro a un método de buscador.  
  
### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Para agregar un descriptor de filtro a un método Finder  
  
1.  En el **detalles del método de BDC** ventana, expanda el nodo de un método Finder, expanda el **parámetros** nodo y, a continuación, agregue un parámetro de entrada. Para obtener más información, consulte [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md).  
  
2.  En el **detalles del método** ventana, elija el descriptor de tipo del parámetro.  
  
3.  En la barra de menús, elija **vista** > **ventana propiedades**.  
  
4.  En el **propiedades** ventana, establezca el **nombre de tipo** propiedad a un tipo de datos que es adecuado para el filtro.  
  
     Por ejemplo, un filtro podría usar una fecha de pedido para limitar el número de pedidos de venta devueltos por el método. Para admitir ese filtro, el **nombre de tipo** debe establecerse la propiedad de descriptor de tipos **System.DateTime**.  
  
5.  En el **detalles del método** ventana, expanda el **descriptores de filtro** nodo.  
  
6.  En **agregar un Descriptor de filtro** elija **crear Descriptor de filtro**.  
  
     Un nuevo descriptor de filtro aparece debajo del **descriptores de filtro** nodo.  
  
7.  En la barra de menús, elija **vista** > **ventana propiedades**.  
  
8.  En el **propiedades** ventana, elija el **tipo** propiedad.  
  
9. En la lista que aparece para la **tipo** propiedad, elija el modelo de filtrado que desee.  
  
     Por ejemplo, para crear un filtro que use una fecha de pedido para limitar el número de pedidos de venta devueltos en un método Finder, elija **comparación**. Un filtro de comparación garantiza que un método finder devuelve solo las instancias que cumplen una condición específica. Para obtener más información acerca de cada modelo de filtrado, consulte [tipos de filtros compatibles con el BDC](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
10. En el **propiedades** ventana, elija el **descriptores de tipo asociados** propiedad.  
  
11. En la lista que aparece para la **descriptores de tipo asociados** propiedad, elija el descriptor de tipos que creó anteriormente en este procedimiento. Esto se relaciona con el filtro para el parámetro de entrada del método de buscador.  
  
12. Agregue código al método Finder que devuelve datos. Puede usar el parámetro de entrada como una condición en una consulta select.  
  
     El ejemplo siguiente devuelve los pedidos de ventas que tienen la fecha de orden especificado.  
  
    > [!NOTE]  
    >  Reemplace el valor de la `ServerName` campo con el nombre del servidor.  
  
     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]  
  
## <a name="see-also"></a>Vea también
 [Cómo: agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Cómo: agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Cómo: definir el descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Integrar datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  

---
title: 'Cómo: agregar un descriptor de filtro a un método Finder | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f9dd853142d970cd14de20f4782accb3ce3e17eb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986252"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Cómo: agregar un descriptor de filtro a un método Finder
  Los descriptores de filtro permiten a los consumidores del modelo pasar valores a los métodos antes de que se ejecuten. Para obtener más información, vea [diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).

 Un escenario común es que los usuarios de SharePoint quieran recuperar instancias de un tipo de contenido externo que coincidan con algunos criterios. Puede admitir este escenario si agrega un descriptor de filtro a un método Finder.

### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Para agregar un descriptor de filtro a un método Finder

1. En la ventana **detalles del método de BDC** , expanda el nodo de un método Finder, expanda el nodo **parámetros** y, a continuación, agregue un parámetro de entrada. Para obtener más información, vea [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md).

2. En la ventana **detalles del método** , elija el descriptor de tipo del parámetro.

3. En la barra de menús, elija **ver** > **ventana Propiedades**.

4. En la ventana **propiedades** , establezca la propiedad **nombre de tipo** en un tipo de datos adecuado para el filtro.

     Por ejemplo, un filtro podría usar una fecha de pedido para limitar el número de pedidos de venta devueltos por el método. Para admitir ese filtro, la propiedad **nombre de tipo** del descriptor de tipo debe establecerse en **System. DateTime**.

5. En la ventana **detalles del método** , expanda el nodo **descriptores de filtro** .

6. En **Agregar una lista de descriptores de filtro** , elija **crear descriptor de filtro**.

     Aparece un nuevo descriptor de filtro debajo del nodo **descriptores de filtro** .

7. En la barra de menús, elija **ver** > **ventana Propiedades**.

8. En la ventana **propiedades** , elija la propiedad **tipo** .

9. En la lista que aparece para la propiedad **Type** , elija el patrón de filtrado que desee.

     Por ejemplo, para crear un filtro que use una fecha de pedido para limitar el número de pedidos de venta devueltos en un método de buscador, elija **comparación**. Un filtro de comparación garantiza que un método Finder solo devuelva instancias que cumplan una condición específica. Para obtener más información acerca de cada patrón de filtrado, consulte [tipos de filtros admitidos por el BDC](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14)).

10. En la ventana **propiedades** , elija la propiedad **descriptores de tipo asociados** .

11. En la lista que aparece para la propiedad **descriptores de tipos asociados** , elija el descriptor de tipos que creó anteriormente en este procedimiento. Esto relaciona el filtro con el parámetro de entrada del método Finder.

12. Agregue código al método Finder que devuelve datos. Puede usar el parámetro de entrada como una condición en una consulta Select.

     En el ejemplo siguiente se devuelven pedidos de ventas que tienen la fecha de pedido especificada.

    > [!NOTE]
    > Reemplace el valor del campo `ServerName` por el nombre del servidor.

     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]

## <a name="see-also"></a>Vea también
- [Cómo: agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Cómo: agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Cómo: definir el descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Integrar datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)

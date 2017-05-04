---
title: "C&#243;mo: Agregar un descriptor de filtro para un m&#233;todo Finder | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [desarrollo de SharePoint en Visual Studio], agregar un filtro"
  - "BDC [desarrollo de SharePoint en Visual Studio], descriptores de filtro"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], agregar un filtro"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], descriptores de filtro"
ms.assetid: 228a6190-8cb8-4182-b6d9-d4c656f4a164
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# C&#243;mo: Agregar un descriptor de filtro para un m&#233;todo Finder
  Los descriptores de filtro permiten a los consumidores del modelo pasar valores a los métodos antes de que se ejecuten.  Para obtener más información, vea [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Es muy habitual que los usuarios de SharePoint deseen recuperar las instancias de un tipo de contenido externo que coincidan con ciertos criterios.  Puede admitir este escenario agregando un descriptor de filtro a un método Finder.  
  
### Para agregar un descriptor de filtro a un método Finder  
  
1.  En la ventana **Detalles del método de BDC**, expanda el nodo de un método Finder, expanda el nodo **Parámetros** y, a continuación, agregue un parámetro de entrada.  Para obtener más información, vea [Cómo: Agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md).  
  
2.  En la ventana de **Detalles del método** , elija el descriptor de parámetro.  
  
3.  En la barra de menús, elija **Ver** y después elija **Ventana Propiedades**.  
  
4.  En la ventana **Propiedades**, establezca la propiedad **Type Name** en un tipo de datos que sea adecuado para el filtro.  
  
     Un filtro puede usar, por ejemplo, una fecha de pedido para limitar el número de pedidos de venta devueltos por el método.  Para admitir ese filtro, la propiedad **Type Name** del descriptor de tipo debe estar establecida en **System.DateTime**.  
  
5.  En la ventana **Detalles del método**, expanda el nodo **Descriptores de filtro**.  
  
6.  En la lista de **Agregar un descriptor de filtro** , elija **Crear descriptor de filtro**.  
  
     Bajo el nodo **Descriptores de filtro**, aparece un nuevo descriptor de filtro.  
  
7.  En la barra de menús, elija **Ver** y después elija **Ventana Propiedades**.  
  
8.  En la ventana de **Propiedades** , elija la propiedad de **Tipo** .  
  
9. En la lista que aparece en la propiedad de **Tipo** , elija el modelo de filtrado que desee.  
  
     Por ejemplo, para crear un filtro que utiliza una fecha de pedido para limitar el número de pedidos devueltos en un método Finder, elija **Comparación**.  Un filtro de comparación garantiza que un método finder devuelve únicamente instancias que satisfacen una condición específica.  Para obtener más información sobre cada modelo de filtrado, vea [Tipos de filtros que admite el BDC](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
10. En la ventana de **Propiedades** , elija la propiedad de **Descriptores de tipo asociados** .  
  
11. En la lista que aparece en la propiedad de **Descriptores de tipo asociados** , elija el descriptor que creó anteriormente en este procedimiento.  De este modo, relacionará el filtro con el parámetro de entrada del método Finder.  
  
12. Agregue el código al método Finder que devuelve los datos.  Puede usar el parámetro de entrada como condición en una consulta de selección \(SELECT\).  
  
     En el siguiente ejemplo se devuelven pedidos de ventas que tienen la fecha de pedido especificada.  
  
    > [!NOTE]  
    >  Reemplace el valor del campo `ServerName` con el nombre del servidor.  
  
     [!code-csharp[SP_BDC#11](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderservice.vb#11)]  
  
## Vea también  
 [Cómo: Agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Cómo: Agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Cómo: Agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Integrar Datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  
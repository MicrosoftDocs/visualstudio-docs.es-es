---
title: "Los objetos que va a agregar al dise&#241;ador usan una conexi&#243;n de datos diferente a la que est&#225; usando el dise&#241;ador | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Los objetos que va a agregar al dise&#241;ador usan una conexi&#243;n de datos diferente a la que est&#225; usando el dise&#241;ador
Los objetos que va a agregar al diseñador usan una conexión de datos diferente a la que está usando el diseñador.¿Desea reemplazar la conexión que usa el diseñador?  
  
 Al agregar elementos al [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\), todos los elementos usan una conexión de datos compartida.\(La superficie de diseño representa la clase <xref:System.Data.Linq.DataContext>, que usa una sola conexión para todos los objetos en la superficie.\) Si agrega al diseñador un objeto que usa una conexión de datos distinta de la conexión de datos que usa actualmente el diseñador, aparece este mensaje.Para resolver este error, puede optar por mantener la conexión existente.Si elige esta opción, no se agregará el objeto seleccionado.Asimismo, puede optar por agregar el objeto y restablecer la conexión de <xref:System.Data.Linq.DataContext> en la nueva conexión.  
  
> [!NOTE]
>  Si hace clic en **Sí**, todas las clases de entidad en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] se asignarán a la nueva conexión.  
  
### Para reemplazar la conexión existente con la conexión que usa el objeto seleccionado  
  
-   Haga clic en **Sí**.  
  
     El objeto seleccionado se agrega al [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] y DataContext.Connection se establece en la nueva conexión.  
  
### Para continuar usando la conexión existente y cancelar la adición del objeto seleccionado  
  
-   Haga clic en **No**.  
  
     Se cancela la acción.DataContext.Connection se mantiene establecido en la conexión existente.  
  
## Vea también  
 [Object Relational Designer](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ a SQL](../Topic/LINQ%20to%20SQL.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)
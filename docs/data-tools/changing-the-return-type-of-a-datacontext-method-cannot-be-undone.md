---
title: "El cambio del tipo devuelto de un m&#233;todo DataContext no se puede deshacer | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# El cambio del tipo devuelto de un m&#233;todo DataContext no se puede deshacer
El cambio del tipo devuelto de un método DataContext no se puede deshacer.Para volver al tipo generado automáticamente, debe arrastrar de nuevo el elemento desde el Explorador de servidores\/Explorador de bases de datos hasta Object Relational Designer.¿Está seguro de que desea cambiar el tipo devuelto?  
  
 El tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> difiere según la ubicación donde se coloque el elemento en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Si se coloca un elemento directamente en una clase de entidad existente, se crea un método de <xref:System.Data.Linq.DataContext> que tiene el tipo de valor devuelto de la clase de entidad.Si se coloca un elemento en un área vacía del [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], se crea un método de <xref:System.Data.Linq.DataContext> que devuelve un tipo generado automáticamente.Se puede cambiar el tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> después de agregarlo al panel de métodos.Para examinar o cambiar el tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext>, selecciónelo y haga clic en la propiedad **Tipo devuelto** en la ventana **Propiedades**.  
  
### Para cambiar el tipo de valor devuelto de un método de DataContext  
  
-   Haga clic en **Sí**.  
  
### Para salir del cuadro de mensaje sin modificar el tipo de valor devuelto  
  
-   Haga clic en **No**.  
  
### Para revertir al tipo de valor devuelto original después de cambiar el tipo de valor devuelto  
  
1.  Seleccione el método de <xref:System.Data.Linq.DataContext> en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] y elimínelo.  
  
2.  Busque el elemento en el **Explorador de servidores\/Explorador de bases de datos** y arrástrelo hasta el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Se crea un método de <xref:System.Data.Linq.DataContext> con el tipo de valor devuelto predeterminado original.  
  
## Vea también  
 [Object Relational Designer](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Métodos DataContext \(Object Relational Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Cómo: Crear métodos DataContext asignados funciones y procedimientos almacenados \(Object Relational Designer\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [LINQ a SQL](../Topic/LINQ%20to%20SQL.md)
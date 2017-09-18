---
title: "No se puede eliminar la clase seleccionada porque se usa como tipo devuelto de uno o varios m&#233;todos DataContext | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# No se puede eliminar la clase seleccionada porque se usa como tipo devuelto de uno o varios m&#233;todos DataContext
El tipo de valor devuelto de uno o varios métodos de <xref:System.Data.Linq.DataContext> es la clase de entidad seleccionada.Cuando se elimina una clase de entidad que se usa como tipo de valor devuelto para un método de <xref:System.Data.Linq.DataContext>, se pueden producir errores en la compilación del proyecto.Para eliminar la clase de entidad seleccionada, identifique los métodos de <xref:System.Data.Linq.DataContext> que la usan y establezca sus tipos de valor devuelto en otra clase de entidad.  
  
 Para revertir los tipos de valor devuelto de los métodos de <xref:System.Data.Linq.DataContext> a sus tipos originales generados automáticamente, primero elimine el método de <xref:System.Data.Linq.DataContext> del panel de métodos y, a continuación, arrastre el objeto desde el **Explorador de servidores**\/**Explorador de bases de datos** hasta Object Relational Designer.  
  
### Para corregir este error  
  
1.  Para identificar los métodos de <xref:System.Data.Linq.DataContext> que usan la clase de entidad como tipo de valor devuelto, seleccione un método de <xref:System.Data.Linq.DataContext> en el panel de métodos y examine la propiedad **Tipo devuelto** en la ventana **Propiedades**.  
  
2.  Establezca **Tipo devuelto** en otra clase de entidad o elimine el método de <xref:System.Data.Linq.DataContext> del panel de métodos.  
  
## Vea también  
 [Información general sobre Object Relational Designer](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Tutorial: Crear clases de LINQ to SQL \(Object Relational Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Métodos DataContext \(Object Relational Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Cómo: Cambiar el tipo devuelto de un método DataContext \(Object Relational Designer\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)
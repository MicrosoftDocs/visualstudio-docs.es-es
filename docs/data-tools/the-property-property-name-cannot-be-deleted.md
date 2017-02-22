---
title: "No se puede eliminar la propiedad &lt;nombre de propiedad&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# No se puede eliminar la propiedad &lt;nombre de propiedad&gt;
No se puede eliminar la propiedad \<nombre de propiedad\> porque se está usando como propiedad Discriminator para la herencia entre las clases \<nombre de clase\> y \<nombre de clase\>  
  
 La propiedad seleccionada está establecida como propiedad **Discriminator** para la herencia entre las clases indicadas en el mensaje de error.Las propiedades no se pueden eliminar si participan en la configuración de la herencia entre clases de datos.  
  
 Establezca la propiedad **Discriminator** en otra propiedad de la clase de datos para que se pueda eliminar correctamente la propiedad deseada.  
  
### Para corregir este error  
  
1.  En Object Relational Designer, seleccione la línea de herencia que conecta las clases de datos indicadas en el mensaje de error.  
  
2.  Establezca la propiedad **Discriminator** en otra propiedad.  
  
3.  Intente de nuevo eliminar la propiedad.  
  
## Vea también  
 [Cómo: Configurar herencia usando Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)   
 [Herencia de clases de datos \(Object Relational Designer\)](../data-tools/data-class-inheritance-o-r-designer.md)   
 [Tutorial: Crear clases de LINQ to SQL usando la herencia de tabla única \(Object Relational Designer\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
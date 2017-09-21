---
title: "No se puede eliminar la propiedad &lt;nombre de propiedad&gt; porque participa en la asociaci&#243;n &lt;nombre de asociaci&#243;n&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# No se puede eliminar la propiedad &lt;nombre de propiedad&gt; porque participa en la asociaci&#243;n &lt;nombre de asociaci&#243;n&gt;
La propiedad seleccionada está establecida como **propiedad de asociación** para la asociación entre las clases indicadas en el mensaje de error.Las propiedades no se pueden eliminar si participan en una asociación entre clases de datos.  
  
 Establezca la **propiedad de asociación** en otra propiedad de la clase de datos para que se pueda eliminar correctamente la propiedad deseada.  
  
### Para corregir este error  
  
1.  En Object Relational Designer, seleccione la línea de asociación que conecta las clases de datos indicadas en el mensaje de error.  
  
2.  Haga doble clic en la línea para abrir el cuadro de diálogo **Editor de asociaciones**.  
  
3.  Quite la propiedad de **Propiedades de la asociación**.  
  
4.  Intente de nuevo eliminar la propiedad.  
  
## Vea también  
 [Información general sobre Object Relational Designer](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Cómo: Crear una asociación \(relación\) entre las clases de LINQ to SQL \(Object Relational Designer\)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Tutorial: Crear clases de LINQ to SQL \(Object Relational Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ a SQL](../Topic/LINQ%20to%20SQL.md)
---
title: "C&#243;mo: Cambiar el tipo devuelto de un m&#233;todo DataContext (Object Relational Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Cambiar el tipo devuelto de un m&#233;todo DataContext (Object Relational Designer)
El tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> \(creado a partir de un procedimiento almacenado o una función\) difiere según la ubicación donde se coloque el procedimiento almacenado o la función en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Si se coloca un elemento directamente en una clase de entidad existente, se crea un método de <xref:System.Data.Linq.DataContext> que tiene el tipo de valor devuelto de la clase de entidad \(si el esquema de los datos devueltos por el procedimiento almacenado o la función coincide con la forma de la clase de entidad\).Si se coloca un elemento en un área vacía del [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], se crea un método de <xref:System.Data.Linq.DataContext> que devuelve un tipo generado automáticamente.Se puede cambiar el tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> después de agregarlo al panel de métodos.Para examinar o cambiar el tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext>, selecciónelo y haga clic en la propiedad **Tipo devuelto** en la ventana **Propiedades**.  
  
> [!NOTE]
>  Mediante la ventana **Propiedades**, no se pueden revertir los métodos de <xref:System.Data.Linq.DataContext> cuyo tipo de valor devuelto está establecido en una clase de entidad para que devuelvan el tipo generado automáticamente.Para revertir un método de <xref:System.Data.Linq.DataContext> de modo que devuelva un tipo generado automáticamente, debe arrastrar de nuevo el objeto de base de datos original hasta Object Relational Designer.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Para cambiar el tipo de valor devuelto de un método de DataContext del tipo generado automáticamente a una clase de entidad  
  
1.  Seleccione el método de <xref:System.Data.Linq.DataContext> en el panel de métodos.  
  
2.  Seleccione **Tipo devuelto** en la ventana **Propiedades** y, a continuación, seleccione una clase de entidad disponible en la lista **Tipo devuelto**.Si la clase de entidad que desea no está en la lista, agréguela o créela en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] para que se incluya en la lista.  
  
3.  Guarde el archivo .dbml.  
  
### Para volver a cambiar el tipo de valor devuelto de un método de DataContext de una clase de entidad al tipo generado automáticamente  
  
1.  Seleccione el método de <xref:System.Data.Linq.DataContext> en el panel de métodos y elimínelo.  
  
2.  Arrastre el objeto de base de datos del **Explorador de servidores**\/**Explorador de bases de datos** hasta un área vacía de Object Relational Designer.  
  
3.  Guarde el archivo .dbml.  
  
## Vea también  
 [Object Relational Designer](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ a SQL](../Topic/LINQ%20to%20SQL.md)   
 [Métodos DataContext \(Object Relational Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Cómo: Crear métodos DataContext asignados funciones y procedimientos almacenados \(Object Relational Designer\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
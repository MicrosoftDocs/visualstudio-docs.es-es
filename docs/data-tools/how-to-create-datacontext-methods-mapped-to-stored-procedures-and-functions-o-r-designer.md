---
title: "C&#243;mo: Crear m&#233;todos DataContext asignados funciones y procedimientos almacenados (Object Relational Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Crear m&#233;todos DataContext asignados funciones y procedimientos almacenados (Object Relational Designer)
Los procedimientos almacenados y funciones se pueden agregar al [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] como métodos de <xref:System.Data.Linq.DataContext>.Al llamar al método y pasar los parámetros necesarios se ejecuta el procedimiento almacenado o la función en la base de datos y se devuelven los datos en el tipo de valor devuelto del método de <xref:System.Data.Linq.DataContext>.Para obtener información detallada sobre los métodos de <xref:System.Data.Linq.DataContext>, vea [Métodos DataContext \(Object Relational Designer\)](../data-tools/datacontext-methods-o-r-designer.md).  
  
> [!NOTE]
>  Los procedimientos almacenados también se pueden usar para invalidar el comportamiento predeterminado de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] en tiempo de ejecución para las inserciones, actualizaciones y eliminaciones cuando se guardan los cambios de las clases de entidad en una base de datos.Para obtener más información, consulte [Cómo: Asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones \(Object Relational Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## Crear métodos de DataContext  
 Puede crear los métodos de <xref:System.Data.Linq.DataContext> arrastrando procedimientos almacenados o funciones desde el **Explorador de servidores\/Explorador de bases de datos** hasta el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
> [!NOTE]
>  El tipo de valor devuelto del método de <xref:System.Data.Linq.DataContext> generado difiere según la ubicación donde se coloque el procedimiento almacenado o la función en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Si se coloca un elemento directamente en una clase de entidad existente, se crea un método de <xref:System.Data.Linq.DataContext> con el tipo de valor devuelto de la clase de entidad.Si se coloca un elemento en un área vacía del [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], se crea un método de <xref:System.Data.Linq.DataContext> que devuelve un tipo generado automáticamente.Se puede cambiar el tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> después de agregarlo al panel de métodos.Para examinar o cambiar el tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext>, selecciónelo y fíjese en la propiedad **Tipo devuelto** en la ventana **Propiedades**.Para obtener más información, consulte [Cómo: Cambiar el tipo devuelto de un método DataContext \(Object Relational Designer\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Para crear métodos de DataContext que devuelvan tipos generados automáticamente  
  
1.  En el **Explorador de servidores**\/**Explorador de bases de datos**, expanda el nodo **Procedimientos almacenados** de la base de datos con la que está trabajando.  
  
2.  Busque el procedimiento almacenado que desee y arrástrelo hasta un área vacía del [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     El método de <xref:System.Data.Linq.DataContext> se crea con un tipo de valor devuelto generado automáticamente y aparece en el panel **Métodos**.  
  
#### Para crear métodos de DataContext con el tipo de valor devuelto de una clase de entidad  
  
1.  En el **Explorador de servidores**\/**Explorador de bases de datos**, expanda el nodo **Procedimientos almacenados** de la base de datos con la que está trabajando.  
  
2.  Busque el procedimiento almacenado que desee y arrástrelo hasta una clase de entidad existente en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     El método de <xref:System.Data.Linq.DataContext> se crea con el tipo de valor devuelto de la clase de entidad seleccionada y aparece en el panel **Métodos**.  
  
> [!NOTE]
>  Para obtener información sobre cómo cambiar el tipo de valor devuelto de los métodos de <xref:System.Data.Linq.DataContext> existentes, vea [Cómo: Cambiar el tipo devuelto de un método DataContext \(Object Relational Designer\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
## Vea también  
 [Object Relational Designer](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Métodos DataContext \(Object Relational Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Tutorial: Crear clases de LINQ to SQL \(Object Relational Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ a SQL](../Topic/LINQ%20to%20SQL.md)   
 [Introducción a LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [Cómo: Escribir consultas con LINQ en C\#](../Topic/How%20to:%20Write%20LINQ%20Queries%20in%20C%23.md)
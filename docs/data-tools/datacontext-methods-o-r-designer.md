---
title: "M&#233;todos DataContext (Object Relational Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 5
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# M&#233;todos DataContext (Object Relational Designer)
Los métodos de <xref:System.Data.Linq.DataContext> \(en el contexto del [Object Relational Designer](../data-tools/linq-to-sql-tools-in-visual-studio2.md)\) son métodos de la clase <xref:System.Data.Linq.DataContext> que ejecutan procedimientos almacenados y funciones en una base de datos.  
  
 La clase <xref:System.Data.Linq.DataContext> es una clase de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] que actúa como una vía entre una base de datos de SQL Server y las clases de entidad de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] asignadas a esa base de datos.La clase <xref:System.Data.Linq.DataContext> contiene la información de la cadena de conexión y los métodos para realizar la conexión a una base de datos y manipular los datos de la base de datos. De forma predeterminada, la clase <xref:System.Data.Linq.DataContext> contiene varios métodos a los que se puede llamar, como el método <xref:System.Data.Linq.DataContext.SubmitChanges%2A> que envía los datos actualizados de las clases de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] a la base de datos.También se pueden crear métodos adicionales de <xref:System.Data.Linq.DataContext> que se asignan a los procedimientos almacenados y funciones.Es decir, al llamar a estos métodos personalizados, se ejecutará el procedimiento almacenado o la función en la base de datos a la que está asignado el método de <xref:System.Data.Linq.DataContext>.Se pueden agregar métodos nuevos a la clase <xref:System.Data.Linq.DataContext> de la misma forma que se agregarían métodos para extender cualquier clase.Sin embargo, en las explicaciones sobre los métodos de <xref:System.Data.Linq.DataContext> en el contexto del [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], se abordan los métodos de <xref:System.Data.Linq.DataContext> que se asignan a los procedimientos almacenados y funciones.  
  
> [!NOTE]
>  En [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)], los procedimientos almacenados y funciones se administran de la misma manera, ya que ambos se asignan a las clases de entidad usando el mismo atributo <xref:System.Data.Linq.StoredProcedureAttribute>.En el contexto de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)], los métodos de <xref:System.Data.Linq.DataContext> que se asignan a los procedimientos almacenados son los mismos que los que se asignan a las funciones.  
  
## Panel de métodos  
 Los métodos de <xref:System.Data.Linq.DataContext> que se asignan a los procedimientos almacenados y funciones se muestran en el panel de métodos del [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].El panel de métodos es el situado junto al panel **Entidades** \(la principal superficie de diseño\).El panel de métodos muestra todos los métodos de <xref:System.Data.Linq.DataContext> creados mediante el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].De forma predeterminada, el panel de métodos está vacío; arrastre los procedimientos almacenados o funciones desde el **Explorador de servidores**\/**Explorador de bases de datos** hasta el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] para crear métodos de <xref:System.Data.Linq.DataContext> y rellenar el panel de métodos.Para obtener más información, consulte [Cómo: Crear métodos DataContext asignados funciones y procedimientos almacenados \(Object Relational Designer\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).  
  
> [!NOTE]
>  Para abrir y cerrar el panel de métodos, haga clic con el botón secundario del mouse en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] y, a continuación, haga clic en **Ocultar panel Métodos** o **Mostrar panel Métodos**, o bien, use el método abreviado de teclado CTRL\+1.  
  
## Dos tipos de métodos de DataContext  
 Los métodos de DataContext son los que se asignan a los procedimientos almacenados y funciones de la base de datos.Puede crear y agregar métodos DataContext en el panel de métodos de [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Hay dos tipos distintos de métodos de <xref:System.Data.Linq.DataContext>: los que devuelven uno o varios conjuntos de resultados y los que no:  
  
-   Métodos de <xref:System.Data.Linq.DataContext> que devuelven uno o varios conjuntos de resultados:  
  
     Cree este tipo de método de <xref:System.Data.Linq.DataContext> cuando la aplicación solamente necesite ejecutar los procedimientos almacenados y funciones en la base de datos y devolver los resultados.Para obtener más información, vea [Cómo: Crear métodos DataContext asignados funciones y procedimientos almacenados \(Object Relational Designer\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), <xref:System.Data.Linq.ISingleResult%271> e <xref:System.Data.Linq.IMultipleResults>.  
  
-   Métodos de <xref:System.Data.Linq.DataContext> que no devuelven conjuntos de resultados, como Inserts, Updates y Deletes para una clase de entidad concreta.  
  
     Cree este tipo de método de <xref:System.Data.Linq.DataContext> cuando la aplicación tenga que ejecutar los procedimientos almacenados en lugar de usar el comportamiento predeterminado de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] para guardar los datos modificados entre una clase de entidad y la base de datos.Para obtener más información, consulte [Cómo: Asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones \(Object Relational Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## Tipos de valor devuelto de los métodos de DataContext  
 Al arrastrar los procedimientos almacenados y funciones desde el **Explorador de servidores**\/**Explorador de bases de datos** hasta el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], el tipo de valor devuelto del método generado de <xref:System.Data.Linq.DataContext> difiere según la ubicación donde se coloque el elemento.Al colocar directamente los elementos en una clase de entidad existente, se crea un método de <xref:System.Data.Linq.DataContext> con el tipo de valor devuelto de la clase de entidad; al colocar los elementos en un área vacía \(en cualquiera de los dos paneles\) del [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], se crea un método de <xref:System.Data.Linq.DataContext> que devuelve un tipo generado automáticamente.El tipo generado automáticamente coincide con el nombre del procedimiento almacenado o de la función y sus propiedades se asignan a los campos devueltos por el procedimiento almacenado o la función.  
  
> [!NOTE]
>  Se puede cambiar el tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> después de agregarlo al panel de métodos.Para examinar o cambiar el tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext>, selecciónelo y fíjese en la propiedad **Tipo devuelto** en la ventana **Propiedades**.Para obtener más información, consulte [Cómo: Cambiar el tipo devuelto de un método DataContext \(Object Relational Designer\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 Los objetos que se arrastran desde la base de datos a la superficie de Object Relational Designer reciben automáticamente un nombre basado en el nombre de los objetos de la base de datos.Si arrastra el mismo objeto más de una vez, se anexa un número al final del nuevo nombre para diferenciar los nombres.Cuando los nombres de objetos de la base de datos contienen espacios o caracteres no admitidos en Visual Basic o C\#, el espacio o el carácter no válido se sustituye por un carácter de subrayado.  
  
## Vea también  
 [Object Relational Designer](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ a SQL](../Topic/LINQ%20to%20SQL.md)   
 [Procedimientos almacenados](../Topic/Stored%20Procedures.md)   
 [Cómo: Crear métodos DataContext asignados funciones y procedimientos almacenados \(Object Relational Designer\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [Cómo: Asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones \(Object Relational Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Tutorial: Personalizar el comportamiento de inserción, actualización y eliminación de las clases de entidad](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [Tutorial: Crear clases de LINQ to SQL \(Object Relational Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)
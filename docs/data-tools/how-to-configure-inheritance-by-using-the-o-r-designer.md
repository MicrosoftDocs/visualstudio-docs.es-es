---
title: "C&#243;mo: Configurar herencia usando Object Relational Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: 4
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Configurar herencia usando Object Relational Designer
[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) admite el concepto de la herencia de tabla única normalmente implementada en los sistemas relacionales. En la herencia de tabla única, hay una sola tabla de base de datos que contiene campos tanto para la información de elementos primarios como para la información de elementos secundarios.En el caso de datos relacionales, una columna discriminadora contiene el valor que determina la clase a la que pertenece un registro cualquiera.  
  
 Por ejemplo, consideremos una tabla Persons que contiene todas las personas que trabajan en una compañía.Algunas personas son los empleados y otras son los directores.La tabla Persons contiene una columna denominada `EmployeeType` que tiene el valor 1 para los directores y el valor 2 para los empleados; ésta es la columna discriminadora.En este escenario, puede crear una subclase de empleados y rellenar la clase únicamente con los registros cuyo `EmployeeType` tiene el valor 2.Puede eliminar también columnas que no se aplican desde cada una de las clases.  
  
 La creación de un modelo de objetos que use la herencia \(y que corresponda a datos relacionales\) puede resultar un poco confusa.En el procedimiento siguiente se describen los pasos necesarios para configurar la herencia con Object Relational Designer.Puede resultar difícil seguir estos pasos genéricos sin hacer referencia a una tabla y columnas ya existentes, por lo que se ha proporcionado un tutorial con datos.Para obtener instrucciones paso a paso detalladas sobre cómo configurar la herencia mediante el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], vea [Tutorial: Crear clases de LINQ to SQL usando la herencia de tabla única \(Object Relational Designer\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).  
  
### Para crear clases de datos heredadas  
  
1.  Abra el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] agregando un elemento de **Clases de LINQ to SQL** a un proyecto existente de Visual Basic o de C\#.  
  
2.  Arrastre la tabla que desee usar como clase base hasta el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
3.  Arrastre una segunda copia de la tabla hasta el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] y cambie su nombre.Ésta es la clase derivada o subclase.  
  
4.  Haga clic en **Herencia** en la pestaña **Object Relational Designer** del **Cuadro de herramientas**y, a continuación, haga clic en la subclase \(la tabla cuyo nombre cambió\) y conéctela a la clase base.  
  
    > [!NOTE]
    >  Haga clic en el elemento **Herencia** del **Cuadro de herramientas** y suelte el botón del mouse, haga clic en la segunda copia de la clase creada en el paso 3 y haga clic en la primera clase creada en el paso 2.La flecha en la línea de herencia apuntará a la primera clase.  
  
5.  En cada clase, elimine las propiedades de objeto que no desee que aparezcan y que no se utilicen para asociaciones.Recibirá un error si intenta eliminar las propiedades de objeto utilizadas para las asociaciones: [No se puede eliminar la propiedad \<nombre de propiedad\> porque participa en la asociación \<nombre de asociación\>](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).  
  
    > [!NOTE]
    >  Dado que una clase derivada hereda las propiedades definidas en su clase base, no se pueden definir las mismas columnas en cada clase.\(Las columnas se implementan como propiedades.\) Puede habilitar la creación de columnas en la clase derivada estableciendo el Modificador de herencia de la propiedad en la clase base.Para obtener más información, consulte [NOT IN BUILD: Overriding Properties and Methods](http://msdn.microsoft.com/es-es/2167e8f5-1225-4b13-9ebd-02591ba90213).  
  
6.  Seleccione la línea de herencia en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
7.  En la ventana **Propiedades**, establezca la propiedad **Discriminator** en el nombre de columna que se usa para distinguir los registros en las clases.  
  
8.  Establezca la propiedad **Valor de discriminador de clase derivada** en el valor de la base de datos que designa el registro como tipo heredado.\(Éste es el valor que está almacenado en la columna discriminadora y que se usa para designar la clase heredada\).  
  
9. Establezca la propiedad **Valor de discriminador de clase base** en el valor que designa el registro como tipo base.\(Éste es el valor que está almacenado en la columna discriminadora y que se usa para designar la clase base\).  
  
10. De manera opcional, también puede establecer la propiedad **Predeterminado de herencia** para designar un tipo en una jerarquía de herencia que se va a usar cuando se carguen filas que no coinciden con ningún código de herencia definido.Es decir, si un registro tiene un valor en su columna discriminadora que no coincide con el valor de las propiedades **Valor de discriminador de clase derivada** o **Valor de discriminador de clase base**, el registro se cargará en el tipo designado como **Predeterminado de herencia**.  
  
## Vea también  
 [Información general sobre Object Relational Designer](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Tutorial: Crear clases de LINQ to SQL \(Object Relational Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [PAVE What's New for Data Application Development in Visual Studio 2012](http://msdn.microsoft.com/es-es/3d50d68f-5f44-4915-842f-6d42fce793f1)   
 [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [LINQ a SQL](../Topic/LINQ%20to%20SQL.md)   
 [Tutorial: Crear clases de LINQ to SQL usando la herencia de tabla única \(Object Relational Designer\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [NOT IN BUILD: Inheritance in Visual Basic](http://msdn.microsoft.com/es-es/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [Herencia](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
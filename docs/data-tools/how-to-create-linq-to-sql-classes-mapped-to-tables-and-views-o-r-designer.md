---
title: "C&#243;mo: Crear clases de LINQ to SQL asignadas a tablas y vistas (Object Relational Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Crear clases de LINQ to SQL asignadas a tablas y vistas (Object Relational Designer)
Las clases de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] asignadas a las tablas y vistas de base de datos se denominan *clases de entidad*. La clase de entidad se asigna a un registro, mientras que las propiedades individuales de una clase de entidad se asignan a las columnas individuales que forman un registro.Puede crear clases de entidad basadas en tablas o vistas de base de datos arrastrando las tablas o vistas desde el **Explorador de servidores**\/**Explorador de bases de datos** hasta el [Object Relational Designer](../data-tools/linq-to-sql-tools-in-visual-studio2.md).El [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] genera las clases y aplica los atributos concretos de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] para habilitar la funcionalidad de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] \(funciones de edición y comunicación de datos de <xref:System.Data.Linq.DataContext>\).Para obtener información detallada sobre las clases de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)], vea [Modelo de objetos de LINQ to SQL](../Topic/The%20LINQ%20to%20SQL%20Object%20Model.md).  
  
> [!NOTE]
>  El [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] es un asignador relacional de objetos simple porque admite únicamente relaciones de asignación 1:1.Es decir, una clase de entidad únicamente puede tener una relación de asignación 1:1 con una tabla o vista de base de datos.No se admiten asignaciones complejas, como la asignación de una clase de entidad a varias tablas.Sin embargo, se puede asignar una clase de entidad a una vista que combina varias tablas relacionadas.  
  
## Crear clases de LINQ to SQL asignadas a tablas o vistas de base de datos  
 Al arrastrar tablas o vistas desde el **Explorador de servidores**\/**Explorador de bases de datos** hasta el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], se crean clases de entidad además de los métodos de <xref:System.Data.Linq.DataContext> que se usan para realizar actualizaciones.  
  
 De forma predeterminada, el motor en tiempo de ejecución de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] crea la lógica para volver a guardar en la base de datos los cambios de una clase de entidad actualizable.Esta lógica se basa en el esquema de la tabla \(las definiciones de columna e información de la clave principal\).Si no desea este comportamiento, puede configurar una clase de entidad para que se usen los procedimientos almacenados para realizar inserciones, actualizaciones y eliminaciones en lugar del comportamiento predeterminado del motor en tiempo de ejecución [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].Para obtener más información, vea [Cómo: Asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones \(Object Relational Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Para crear clases de LINQ to SQL asignadas a tablas o vistas de base de datos  
  
1.  En **Servidor**\/**Explorador de bases de datos**, expanda **Tablas** o **Vistas** y busque la tabla o vista de base de datos que desee usar en la aplicación.  
  
2.  Arrastre la tabla o vista hasta el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Se crea una clase de entidad, que aparece en la superficie de diseño.La clase de entidad tiene propiedades que se asignan a las columnas en la tabla o vista seleccionada.  
  
## Crear un origen de datos de objeto y mostrar los datos en un formulario  
 Después de crear las clases de entidad mediante el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], puede crear un origen de datos de objeto y rellenar la [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md) con las clases de entidad.  
  
#### Para crear un origen de datos de objeto basándose en las clases de entidad de LINQ to SQL  
  
1.  Para compilar el proyecto, en el menú **Compilar**, haga clic en **Compilar solución**.  
  
2.  En el menú **Datos**, haga clic en **Mostrar orígenes de datos**.  
  
3.  En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos**.  
  
4.  Haga clic en **Objeto** en la página **Elegir un tipo de origen de datos** y, a continuación, haga clic en **Siguiente**.  
  
5.  Expanda los nodos y, a continuación, busque y seleccione la clase.  
  
    > [!NOTE]
    >  Si la clase **Customer** no está disponible, cierre el asistente, compile el proyecto y vuelva a ejecutar el asistente.  
  
6.  Haga clic en **Finalizar** para crear el origen de datos y agregar la clase de entidad **Customer** a la ventana **Orígenes de datos**.  
  
7.  Arrastre los elementos desde la ventana **Orígenes de datos** a un formulario.  
  
## Vea también  
 [Object Relational Designer](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Tutorial: Crear clases de LINQ to SQL \(Object Relational Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Métodos DataContext \(Object Relational Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Cómo: Crear métodos DataContext asignados funciones y procedimientos almacenados \(Object Relational Designer\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [Modelo de objetos de LINQ to SQL](../Topic/The%20LINQ%20to%20SQL%20Object%20Model.md)   
 [Cómo: Agregar validación a clases de entidad](../data-tools/how-to-add-validation-to-entity-classes.md)   
 [Tutorial: Personalizar el comportamiento de inserción, actualización y eliminación de las clases de entidad](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [Tutorial: Agregar validación a clases de entidad](../Topic/Walkthrough:%20Adding%20Validation%20to%20Entity%20Classes.md)   
 [Cómo: Crear una asociación \(relación\) entre las clases de LINQ to SQL \(Object Relational Designer\)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)
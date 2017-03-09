---
title: "LINQ to SQL Tools en Visual Studio2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# LINQ to SQL Tools en Visual Studio
LINQ to SQL fue la primera tecnología de asignación objeto-relacional publicada por Microsoft. Funciona bien en escenarios básicos y se sigue admitiendo en Visual Studio, pero ya no está en desarrollo activo. Usar LINQ to SQL al mantenimiento de una aplicación heredada que ya está usando o en aplicaciones sencillas que utilizan SQL Server y no requieren la asignación de varias tabla. En general, aplicaciones nuevas deben usar Entity Framework cuando se necesita una capa mapeador relacional de objetos.  
  
 En Visual Studio, crea clases LINQ to SQL que representan tablas SQL utilizando la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 El [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] tiene dos áreas distintas en su superficie de diseño: el panel de entidades de la izquierda y el panel de métodos a la derecha. El panel de entidades es la superficie de diseño principal que muestra las clases de entidad, asociaciones y jerarquías de herencia. El panel de métodos es la superficie de diseño que muestra la <xref:System.Data.Linq.DataContext> métodos que se asignan a los procedimientos almacenados y funciones.  
  
 El [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]) proporciona una superficie de diseño visual para crear [LINQ to SQL](../Topic/LINQ%20to%20SQL.md) clases de entidad y asociaciones (relaciones) que se basan en los objetos de una base de datos. Es decir, el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] se usa para crear un modelo de objetos en una aplicación que se asigna a los objetos de una base de datos. También genera fuertemente tipados <xref:System.Data.Linq.DataContext> que se utiliza para enviar y recibir datos entre las clases de entidad y la base de datos. El [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] también proporciona funcionalidad para asignar procedimientos almacenados y funciones a <xref:System.Data.Linq.DataContext> métodos para devolver datos y rellenar las clases de entidad. Por último, el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] permite diseñar relaciones de herencia entre las clases de entidad.  
  
## <a name="opening-the-or-designer"></a>Abrir Object Relational Designer  
 Para agregar un LINQ al modelo de entity SQL a su proyecto, elija **proyecto &#124; Agregar nuevo elemento** y, a continuación, elija  **clases LINQ to SQL** en la lista de elementos de proyecto:  
  
 ![Clases de LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png "raddata LINQ to SQL Classes")  
  
 Visual Studio crea un archivo .dbml y lo agrega a la solución. Este es el archivo de asignación de XML y sus archivos de código relacionados.  
  
 ![Clases LINQ to SQL en el Explorador de soluciones](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata LINQ to SQL classes in Solution Explorer")  
  
 Al seleccionar el archivo .dbml, Visual Studio muestra la superficie del Diseñador de Object Relational que le permite crear visualmente el modelo. La ilustración siguiente muestra el diseñador después de las tablas de Northwind Customers y Orders que se han arrastrado desde el Explorador de servidores. Tenga en cuenta la relación entre las tablas.  
  
 ![Diseñador LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png "raddata LINQ to SQL Designer")  
  
> [!IMPORTANT]
>  El [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] es un asignador relacional de objetos simple porque admite únicamente relaciones de asignación 1:1. Es decir, una clase de entidad únicamente puede tener una relación de asignación 1:1 con una tabla o vista de base de datos. No se admiten asignaciones complejas, como la asignación de una clase de entidad a una tabla combinada, utilizar Entity Framework para la asignación compleja. Además, el diseñador es un generador de código unidireccional. Esto significa que solo se reflejan en el archivo de código los cambios que se realizan en la superficie del diseñador. Los cambios realizados manualmente en el archivo de código no se reflejan en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Cualquier cambio que se realice manualmente en el archivo de código se sobrescribe cuando se guarda el diseñador y se vuelve a generar el código. Para obtener información acerca de cómo agregar código de usuario y extender las clases generadas por el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], vea [Cómo: ampliar código generado por el Object Relational Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).  
  
## <a name="creating-and-configuring-the-datacontext"></a>Crear y configurar DataContext  
 Después de agregar un **clases LINQ to SQL** elemento a un proyecto y abrir el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], la superficie de diseño vacía representa un <xref:System.Data.Linq.DataContext> listo para su configuración. el <xref:System.Data.Linq.DataContext> está configurado con información de conexión proporcionada por el primer elemento que se arrastra hasta la superficie de diseño... Por lo tanto, la <xref:System.Data.Linq.DataContext> está configurado con información de conexión desde el primer elemento que se coloca en la superficie de diseño. Para obtener más información acerca de la <xref:System.Data.Linq.DataContext> vea clase [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Crear clases de entidad que se asignan a tablas y vistas de base de datos  
 Puede crear clases de entidad asignadas a tablas y vistas arrastrando tablas de base de datos y vistas de **Server Explorer**/**Database Explorer** hasta la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Como se indica en la sección anterior del <xref:System.Data.Linq.DataContext> está configurado con información de conexión proporcionada por el primer elemento que se arrastra hasta la superficie de diseño. Si se agrega un elemento subsiguiente que use otra conexión a la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], puede cambiar la conexión para el <xref:System.Data.Linq.DataContext>. Para obtener más información, vea [Cómo: crear clases de LINQ to SQL asignadas a tablas y vistas (Object Relational Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Crear métodos de DataContext que llamen a procedimientos almacenados y funciones  
 Puede crear <xref:System.Data.Linq.DataContext> métodos que llamen (estén asignados) procedimientos almacenados y funciones arrastrándolos desde **Explorador de servidores**/**Database Explorer** hasta la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Procedimientos almacenados y funciones se agregan a la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] como métodos de la <xref:System.Data.Linq.DataContext>.  
  
> [!NOTE]
>  Al arrastrar los procedimientos almacenados y funciones de **Server Explorer**/**Database Explorer** en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], el tipo devuelto de generado <xref:System.Data.Linq.DataContext> método difiere dependiendo de dónde se coloca el elemento. Para obtener más información, consulte [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configurar DataContext de modo que se usen los procedimientos almacenados para guardar los datos entre las clases de entidad y una base de datos  
 Como se indicó anteriormente, puede crear <xref:System.Data.Linq.DataContext> métodos que llaman a procedimientos almacenados y funciones. Además, también puede asignar los procedimientos almacenados que se pueden usar para el comportamiento predeterminado del motor en tiempo de ejecución [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] en materia de inserciones, actualizaciones y eliminaciones. Para obtener más información, vea [Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="inheritance-and-the-or-designer"></a>Herencia y Object Relational Designer  
 Al igual que otros objetos, las clases de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] pueden usar la herencia y derivarse de otras clases. En una base de datos, las relaciones de herencia se crean de varias maneras. El [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] admite el concepto de la herencia de tabla única normalmente implementada en los sistemas relacionales. Para obtener más información, vea [Cómo: configurar la herencia utilizando Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).  
  
## <a name="linq-to-sql-queries"></a>Consultas de LINQ to SQL  
 Las clases de entidad creadas por el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] están diseñados para su uso con [LINQ (Language-Integrated Query)](../Topic/LINQ%20\(Language-Integrated%20Query\).md). Para obtener más información, vea [Cómo: consultar información](../Topic/How%20to:%20Query%20for%20Information.md).  
  
## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Separar la clase DataContext generada y el código de clase de entidad en espacios de nombres distintos  
 El [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] proporciona el **el espacio de nombres de contexto** y **el espacio de nombres de entidad** Propiedades en el <xref:System.Data.Linq.DataContext>. Estas propiedades determinan qué espacio de nombres del <xref:System.Data.Linq.DataContext> y se genera el código de clase de entidad en. De forma predeterminada, estas propiedades están vacías y <xref:System.Data.Linq.DataContext> y clases de entidad se generan en el espacio de nombres de la aplicación. Para generar el código en un espacio de nombres distinto del espacio de nombres de la aplicación, escriba un valor en el **el espacio de nombres de contexto** o **el espacio de nombres de entidad** Propiedades.  
  
## <a name="in-this-section"></a>En esta sección  
 [Métodos de DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)  
 Explica qué <xref:System.Data.Linq.DataContext> métodos son y cómo crearlos.  
  
 [Herencia de clases de datos (Object Relational Designer)](../data-tools/data-class-inheritance-o-r-designer.md)  
 Describe el concepto de herencia de tabla única y cómo se implementa en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 [Cómo: crear LINQ to SQL classes asignadas a tablas y vistas (Object Relational Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)  
 Describe cómo crear clases de entidad asignadas a tablas y vistas de una base de datos.  
  
 [Cómo: crear una asociación (relación) entre clases LINQ to SQL (Object Relational Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)  
 Describe cómo crear una relación entre las clases de entidad de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].  
  
 [Cómo: crear métodos DataContext asignados a procedimientos almacenados y funciones (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)  
 Describe cómo crear <xref:System.Data.Linq.DataContext> métodos que ejecutan procedimientos almacenados o funciones cuando se les llama.  
  
 [Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
 Describe cómo configurar un <xref:System.Data.Linq.DataContext> volver a usar procedimientos almacenados al guardar los datos de entidad a una base de datos de clases.  
  
 [Cómo: cambiar el tipo de valor devuelto de un método DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)  
 Describe cómo establecer el tipo de valor devuelto de un <xref:System.Data.Linq.DataContext> método sea el tipo de una clase de entidad o un tipo generado automáticamente por el Object Relational Designer.  
  
 [Cómo: agregar validación a las clases de entidad](../data-tools/how-to-add-validation-to-entity-classes.md)  
 Describe cómo generar métodos parciales que permitan agregar código durante los cambios de propiedad y las actualizaciones de las clases de entidad.  
  
 [Cómo: activar y desactivar (Object Relational Designer) pluralización](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md)  
 Describe cómo activar y desactivar el cambio de nombre automático de las clases que se agregan al [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 [Cómo: configurar la herencia utilizando Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)  
 Describe cómo configurar las clases de entidad usando la herencia de tabla única con el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 [Cómo: ampliar código generado por el Object Relational Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md)  
 Describe cómo y dónde se debe agregar código para que no se sobrescriba cuando los cambios en los objetos de Object Relational Designer vuelvan a generar el código.  
  
 [Tutorial: Crear clases LINQ to SQL mediante la herencia de tabla única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)  
 Proporciona instrucciones paso a paso para configurar las clases de entidad usando la herencia de tabla única con el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 [Tutorial: Personalizar la inserción, actualización y eliminación de comportamiento de las clases de entidad](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
 Proporciona instrucciones paso a paso para configurar un <xref:System.Data.Linq.DataContext> volver a usar procedimientos almacenados al guardar los datos de entidad a una base de datos de clases.  
  
## <a name="reference-content"></a>Contenido de referencia  
 <xref:System.Linq>  
  
 <xref:System.Data.Linq>  
  
## <a name="see-also"></a>Vea también  
 [Herramientas de datos de Visual Studio para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)   
 [Preguntas más frecuentes](../Topic/Frequently%20Asked%20Questions.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Acceso a datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
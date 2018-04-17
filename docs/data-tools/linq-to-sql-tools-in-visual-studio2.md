---
title: Introducción a Visual Studio Object Relational Designer | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 09fe5a8cbec1ba1ab5a45abda4c88864e25a1751
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>LINQ to SQL herramientas en Visual Studio
LINQ to SQL era la primera tecnología de asignación objeto-relacional publicada por Microsoft. Funciona bien en escenarios básicos y continúa siendo compatible con Visual Studio, pero es ya no está en desarrollo activo. Usar LINQ to SQL al mantener una aplicación heredada que ya está utilizando, o en aplicaciones sencillas que use SQL Server y no requieren la asignación de varias tabla. En general, aplicaciones nuevas deben usar Entity Framework cuando se requiere un nivel de asignador relacional de objetos.  
  
En Visual Studio, crear LINQ a las clases SQL que representan tablas SQL mediante el uso de Object Relational Designer (Object Relational Designer).  
  
El [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] tiene dos áreas distintas en la superficie de diseño: el panel de entidades de la izquierda y el panel de métodos a la derecha. El panel de entidades es la superficie de diseño principal que muestra las clases de entidad, asociaciones y jerarquías de herencia. El panel de métodos es la superficie de diseño que muestra la <xref:System.Data.Linq.DataContext> métodos que están asignados a procedimientos almacenados y funciones.  
  
El [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] proporciona una superficie de diseño visual para crear [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) las clases de entidad y asociaciones (relaciones) que se basan en los objetos de una base de datos. Es decir, el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] se usa para crear un modelo de objetos en una aplicación que se asigna a los objetos de una base de datos. También genera una clase <xref:System.Data.Linq.DataContext> fuertemente tipada que se usa para enviar y recibir datos entre las clases de entidad y la base de datos. El [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] también proporciona la funcionalidad para asignar los procedimientos almacenados y funciones a los métodos de <xref:System.Data.Linq.DataContext> con el fin de devolver datos y rellenar las clases de entidad. Por último, el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] permite diseñar relaciones de herencia entre las clases de entidad.  
  
## <a name="opening-the-or-designer"></a>Abrir Object Relational Designer  
 Para agregar un LINQ al modelo de entity SQL al proyecto, elija **proyecto**, **Agregar nuevo elemento** y, a continuación, elija **clases LINQ to SQL** en la lista de elementos de proyecto:  
  
 ![Clases LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png "raddata clases LINQ to SQL")  
  
 Visual Studio crea un archivo .dbml y lo agrega a la solución. Este es el archivo de asignación de XML y sus archivos de código relacionados.  
  
 ![Clases de LINQ to SQL en el Explorador de soluciones](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata de LINQ to SQL clases en el Explorador de soluciones")  
  
 Cuando se selecciona el archivo .dbml, Visual Studio muestra la superficie del Diseñador de Object Relational que le permite crear visualmente el modelo. En la siguiente ilustración muestra el diseñador después de las tablas de Northwind Customers y Orders que se han arrastrado desde el Explorador de servidores. Tenga en cuenta la relación entre las tablas.  
  
 ![Diseñador LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png "raddata diseñador LINQ to SQL")  
  
> [!IMPORTANT]
>  El [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] es un asignador relacional de objetos simple porque admite únicamente relaciones de asignación 1:1. Es decir, una clase de entidad únicamente puede tener una relación de asignación 1:1 con una tabla o vista de base de datos. No se admiten asignaciones complejas, como la asignación de una clase de entidad para una tabla combinada, utilizar Entity Framework para la asignación compleja. Además, el diseñador es un generador de código unidireccional. Esto significa que solo se reflejan en el archivo de código los cambios que se realizan en la superficie del diseñador. Los cambios realizados manualmente en el archivo de código no se reflejan en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Cualquier cambio que se realice manualmente en el archivo de código se sobrescribe cuando se guarda el diseñador y se vuelve a generar el código. Para obtener información acerca de cómo agregar código de usuario y extender las clases generadas por el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], consulte [Cómo: ampliar código generado por el Object Relational Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).  
  
## <a name="creating-and-configuring-the-datacontext"></a>Crear y configurar DataContext  
 Después de agregar un **clases LINQ to SQL** elemento a un proyecto y abra el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], la superficie de diseño vacía representa vacío <xref:System.Data.Linq.DataContext> listo para configurarlo. el <xref:System.Data.Linq.DataContext> está configurado con información de conexión proporcionada por el primer elemento que se arrastra hasta la superficie de diseño... Por lo tanto, el <xref:System.Data.Linq.DataContext> se configura con información de conexión desde el primer elemento que se coloca en la superficie de diseño. Para obtener más información sobre la <xref:System.Data.Linq.DataContext> , vea clase [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Crear clases de entidad que se asignan a tablas y vistas de base de datos  
 Puede crear las clases de entidad asignadas a tablas y vistas arrastrando tablas de base de datos y vistas de **Explorador de servidores**/**el Explorador de base de datos** en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Tal como se ha indicado en la sección anterior, el <xref:System.Data.Linq.DataContext> se configura con la información de conexión proporcionada por el primer elemento que se arrastra hasta la superficie de diseño. Si se agrega al [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] un elemento subsiguiente que use otra conexión, se puede cambiar la conexión para <xref:System.Data.Linq.DataContext>. Para obtener más información, consulte [Cómo: crear clases de LINQ to SQL asignadas a tablas y vistas (Object Relational Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Crear métodos de DataContext que llamen a procedimientos almacenados y funciones  
 Puede crear <xref:System.Data.Linq.DataContext> métodos que llaman (estén asignados) los procedimientos almacenados y funciones arrastrándolos desde **Explorador de servidores**/**el Explorador de base de datos** en la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Los procedimientos almacenados y funciones se agregan al [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] como métodos de <xref:System.Data.Linq.DataContext>.  
  
> [!NOTE]
>  Al arrastrar los procedimientos almacenados y funciones de **Explorador de servidores**/**el Explorador de base de datos** en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], el tipo de valor devuelto de generado <xref:System.Data.Linq.DataContext> difiere del método Dependiendo de dónde colocar el elemento. Para obtener más información, consulte [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configurar DataContext de modo que se usen los procedimientos almacenados para guardar los datos entre las clases de entidad y una base de datos  
 Como se ha indicado anteriormente, puede crear métodos de <xref:System.Data.Linq.DataContext> que llamen a los procedimientos almacenados y funciones. Además, también puede asignar los procedimientos almacenados que se pueden usar para el comportamiento predeterminado del motor en tiempo de ejecución [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] en materia de inserciones, actualizaciones y eliminaciones. Para obtener más información, consulte [Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="inheritance-and-the-or-designer"></a>Herencia y Object Relational Designer  
 Al igual que otros objetos, las clases de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] pueden usar la herencia y derivarse de otras clases. En una base de datos, las relaciones de herencia se crean de varias maneras. El [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] admite el concepto de la herencia de tabla única normalmente implementada en los sistemas relacionales. Para obtener más información, consulte [Cómo: configurar la herencia utilizando Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).  
  
## <a name="linq-to-sql-queries"></a>Consultas de LINQ to SQL  
 Las clases de entidad creadas por la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] están diseñados para su uso con [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/). Para obtener más información, consulte [Cómo: consultar información](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).  
  
## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Separar la clase DataContext generada y el código de clase de entidad en espacios de nombres distintos  
 El [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] proporciona el **contexto Namespace** y **entidad Namespace** propiedades en el <xref:System.Data.Linq.DataContext>. Estas propiedades determinan en qué espacio de nombres se generan la clase <xref:System.Data.Linq.DataContext> y el código de clase de entidad. De forma predeterminada, estas propiedades están vacías y las clases de entidad y <xref:System.Data.Linq.DataContext> se generan en el espacio de nombres de la aplicación. Para compilar el código en un espacio de nombres distinto del espacio de nombres de la aplicación, escriba un valor en el **contexto Namespace** o **entidad Namespace** propiedades.
  
## <a name="reference-content"></a>Contenido de referencia
<xref:System.Linq>  
<xref:System.Data.Linq>  
  
## <a name="see-also"></a>Vea también
[LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)    
[(.NET Framework) de preguntas más frecuentes](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions) 
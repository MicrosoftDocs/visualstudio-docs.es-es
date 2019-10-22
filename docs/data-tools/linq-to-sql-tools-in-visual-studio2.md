---
title: Introducción al Object Relational Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c02dbc42d629385671403de7131b27a449313591
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648292"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Herramientas de LINQ to SQL en Visual Studio

LINQ to SQL era la primera tecnología de asignación relacional de objetos lanzada por Microsoft. Funciona bien en escenarios básicos y sigue siendo compatible con Visual Studio, pero ya no está en desarrollo activo. Use LINQ to SQL al mantener una aplicación heredada que ya la esté usando, o en aplicaciones sencillas que utilicen SQL Server y no requieran asignación de varias tablas. En general, las aplicaciones nuevas deben usar el Entity Framework cuando se requiere una capa de asignador relacional de objetos.

En Visual Studio, se crean LINQ to SQL clases que representan tablas SQL mediante el **Object Relational Designer** (Object Relational**Designer**).

**Object Relational Designer** tiene dos áreas distintas en su superficie de diseño: el panel entidades de la izquierda y el panel métodos de la derecha. El panel de entidades es la superficie de diseño principal que muestra las clases de entidad, asociaciones y jerarquías de herencia. El panel de métodos es la superficie de diseño que muestra los métodos <xref:System.Data.Linq.DataContext> que están asignados a procedimientos almacenados y funciones.

**Object Relational Designer** proporciona una superficie de diseño visual para crear [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) clases de entidad y asociaciones (relaciones) basadas en objetos de una base de datos. En otras palabras, Object Relational **Designer** crea un modelo de objetos en una aplicación que se asigna a los objetos de una base de datos. También genera un <xref:System.Data.Linq.DataContext> fuertemente tipado que envía y recibe datos entre las clases de entidad y la base de datos. **Object Relational Designer** también proporciona funcionalidad para asignar procedimientos almacenados y funciones a métodos <xref:System.Data.Linq.DataContext> para devolver datos y rellenar clases de entidad. Por último, el **Object Relational Designer** proporciona la capacidad de diseñar las relaciones de herencia entre las clases de entidad.

## <a name="open-the-or-designer"></a>Apertura de Object Relational Designer

Para agregar un LINQ to SQL modelo de entidad al proyecto, elija **proyecto**  > **Agregar nuevo elemento**y, a continuación, seleccione **clases de LINQ to SQL** de la lista de elementos de proyecto:

![Clases LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio crea un archivo *. dbml* y lo agrega a la solución. Este es el archivo de asignación XML y sus archivos de código relacionados.

![LINQ to SQL clases en Explorador de soluciones](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

Al seleccionar el archivo *. dbml* , Visual Studio muestra la superficie del **Diseñador de o/R** que le permite crear visualmente el modelo. En la ilustración siguiente se muestra el diseñador una vez que se han arrastrado las tablas `Customers` y `Orders` de Northwind desde **Explorador de servidores**. Observe la relación entre las tablas.

![Diseñador LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> Object Relational **Designer** es un asignador relacional de objetos simple porque admite solo relaciones de asignación 1:1. Es decir, una clase de entidad únicamente puede tener una relación de asignación 1:1 con una tabla o vista de base de datos. No se admite la asignación compleja, como la asignación de una clase de entidad a una tabla combinada. Use el Entity Framework para la asignación compleja. Además, el diseñador es un generador de código unidireccional. Esto significa que solo se reflejan en el archivo de código los cambios que se realizan en la superficie del diseñador. Los cambios manuales en el archivo de código no se reflejan en Object Relational **Designer**. Cualquier cambio que se realice manualmente en el archivo de código se sobrescribe cuando se guarda el diseñador y se vuelve a generar el código. Para obtener información acerca de cómo agregar código de usuario y extender las clases generadas por el **Object Relational Designer**, vea [Cómo: Ampliar el código generado por Object Relational Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="create-and-configure-the-datacontext"></a>Crear y configurar DataContext

Después de agregar un elemento de **clases de LINQ to SQL** a un proyecto y abrir Object Relational **Designer**, la superficie de diseño vacía representa un <xref:System.Data.Linq.DataContext> vacío listo para configurarlo. El elemento <xref:System.Data.Linq.DataContext> se configura con la información de conexión proporcionada por el primer elemento que se arrastra hasta la superficie de diseño. Por consiguiente, <xref:System.Data.Linq.DataContext> se configura usando la información de conexión del primer elemento que se coloca sobre la superficie de diseño. Para obtener más información sobre la clase <xref:System.Data.Linq.DataContext>, vea [métodos DataContext (Object](../data-tools/datacontext-methods-o-r-designer.md)Relational Designer).

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>Crear clases de entidad que se asignan a tablas y vistas de base de datos

Puede crear clases de entidad asignadas a tablas y vistas arrastrando tablas y vistas de base de datos desde **Explorador de servidores** o **Explorador de bases de datos** a **Object Relational Designer**. Tal como se ha indicado en la sección anterior, el <xref:System.Data.Linq.DataContext> se configura con la información de conexión proporcionada por el primer elemento que se arrastra hasta la superficie de diseño. Si se agrega un elemento subsiguiente que usa una conexión diferente a Object Relational **Designer**, puede cambiar la conexión para el <xref:System.Data.Linq.DataContext>. Para obtener más información, vea [Cómo: crear clases de LINQ to SQL asignadas a tablas y vistas (Object](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)Relational Designer).

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>Crear métodos de DataContext que llamen a procedimientos almacenados y funciones

Puede crear métodos de <xref:System.Data.Linq.DataContext> que llamen a (están asignados a) procedimientos almacenados y funciones arrastrándolos desde **Explorador de servidores** o **Explorador de bases de datos** hasta **Object**Relational Designer. Los procedimientos almacenados y las funciones se agregan a Object Relational **Designer** como métodos de la <xref:System.Data.Linq.DataContext>.

> [!NOTE]
> Al arrastrar procedimientos almacenados y funciones desde **Explorador de servidores** o **Explorador de bases de datos** a Object Relational **Designer**, el tipo de valor devuelto del método <xref:System.Data.Linq.DataContext> generado varía en función de dónde se coloque el elemento. Para obtener más información, vea [métodos DataContext (Object](../data-tools/datacontext-methods-o-r-designer.md)Relational Designer).

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configurar un DataContext para usar procedimientos almacenados para guardar datos entre las clases de entidad y una base de datos

Como se ha indicado anteriormente, puede crear métodos de <xref:System.Data.Linq.DataContext> que llamen a los procedimientos almacenados y funciones. Además, también puede asignar procedimientos almacenados que se utilizan para el comportamiento predeterminado de tiempo de ejecución de LINQ to SQL, que realiza inserciones, actualizaciones y eliminaciones. Para obtener más información, vea [Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)Relational Designer).

## <a name="inheritance-and-the-or-designer"></a>Herencia y Object Relational Designer

Al igual que otros objetos, las clases de LINQ to SQL pueden utilizar la herencia y derivarse de otras clases. En una base de datos, las relaciones de herencia se crean de varias maneras. Object Relational **Designer** admite el concepto de herencia de tabla única, ya que se suele implementar en sistemas relacionales. Para obtener más información, consulte [Cómo: configurar la herencia mediante Object](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)Relational Designer.

## <a name="linq-to-sql-queries"></a>Consultas de LINQ to SQL

Las clases de entidad creadas por el Object Relational **Designer** están diseñadas para su uso con [Language-Integrated Query (LINQ)](/dotnet/csharp/linq/). Para obtener más información, consulte [Cómo: consultar información](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Separar el código de clase de entidad y DataContext generado en diferentes espacios de nombres

**Object Relational Designer** proporciona las propiedades espacio de nombres del **contexto** y espacio de nombres de la **entidad** en el <xref:System.Data.Linq.DataContext>. Estas propiedades determinan en qué espacio de nombres se generan la clase <xref:System.Data.Linq.DataContext> y el código de clase de entidad. De forma predeterminada, estas propiedades están vacías y las clases de entidad y <xref:System.Data.Linq.DataContext> se generan en el espacio de nombres de la aplicación. Para generar el código en un espacio de nombres distinto del espacio de nombres de la aplicación, especifique un valor para las propiedades **Espacio de nombres del contexto** o **Espacio de nombres de la entidad**.

## <a name="reference-content"></a>Contenido de referencia

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>Vea también

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Preguntas más frecuentes (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)
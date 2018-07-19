---
title: Información general de Visual Studio Object Relational Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7c7abaa95c3b7c8f5ab78b4d58f383243b176f7a
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089417"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>LINQ to SQL tools en Visual Studio

LINQ to SQL era la primera tecnología de asignación relacional de objetos publicada por Microsoft. Funciona bien en escenarios básicos y sigue siendo compatible con Visual Studio, pero ya no está en desarrollo activo. Usar LINQ to SQL al mantener una aplicación heredada que ya está usando, o en aplicaciones sencillas que usan SQL Server y no requieren la asignación de varias tabla. En general, aplicaciones nuevas deben utilizar Entity Framework cuando se requiere un nivel de asignador relacional de objetos.

En Visual Studio, cree LINQ a las clases SQL que representan las tablas SQL mediante el uso de la **Object Relational Designer** (**Object Relational Designer**).

El **Object Relational Designer** tiene dos áreas distintas en su superficie de diseño: el panel entidades de la izquierda y el panel de métodos de la derecha. El panel de entidades es la superficie de diseño principal que muestra las clases de entidad, asociaciones y jerarquías de herencia. El panel de métodos es la superficie de diseño que muestra la <xref:System.Data.Linq.DataContext> métodos que están asignados a procedimientos almacenados y funciones.

El **Object Relational Designer** proporciona una superficie de diseño visual para crear [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) clases de entidad y asociaciones (relaciones) que se basan en los objetos de una base de datos. En otras palabras, el **Object Relational Designer** crea un modelo de objetos en una aplicación que se asigna a los objetos en una base de datos. También genera fuertemente tipadas <xref:System.Data.Linq.DataContext> que envía y recibe datos entre las clases de entidad y la base de datos. El **Object Relational Designer** también proporciona funcionalidad para asignar procedimientos almacenados y funciones a <xref:System.Data.Linq.DataContext> métodos para devolver datos y rellenar las clases de entidad. Por último, el **Object Relational Designer** permite diseñar relaciones de herencia entre clases de entidad.

## <a name="open-the-or-designer"></a>Abra el Object Relational designer

Para agregar un LINQ al modelo de entity SQL al proyecto, elija **proyecto** > **Agregar nuevo elemento**y, a continuación, seleccione **clases LINQ to SQL** en la lista de elementos de proyecto:

![Clases LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio crea un *.dbml* de archivo y lo agrega a la solución. Este es el archivo de asignación XML y sus archivos de código relacionados.

![Clases LINQ to SQL en el Explorador de soluciones](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

Cuando se selecciona el *.dbml* de archivos, Visual Studio muestra el **Object Relational Designer** superficie que le permite crear visualmente el modelo. La siguiente ilustración muestra el diseñador después de Northwind `Customers` y `Orders` tablas que se han arrastrado desde **Explorador de servidores**. Tenga en cuenta la relación entre las tablas.

![Diseñador LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> El **Object Relational Designer** es un asignador relacional de objetos simple porque admite únicamente relaciones de asignación 1:1. Es decir, una clase de entidad únicamente puede tener una relación de asignación 1:1 con una tabla o vista de base de datos. No se admiten asignaciones complejas, como la asignación de una clase de entidad a una tabla combinada, utilizar Entity Framework para la asignación compleja. Además, el diseñador es un generador de código unidireccional. Esto significa que solo se reflejan en el archivo de código los cambios que se realizan en la superficie del diseñador. No se reflejan los cambios manuales en el archivo de código en el **Object Relational Designer**. Cualquier cambio que se realice manualmente en el archivo de código se sobrescribe cuando se guarda el diseñador y se vuelve a generar el código. Para obtener información acerca de cómo agregar código de usuario y extender las clases generadas por el **Object Relational Designer**, consulte [Cómo: ampliar código generado por el Object Relational Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="create-and-configure-the-datacontext"></a>Crear y configurar DataContext

Después de agregar un **clases LINQ to SQL** elemento a un proyecto y abrir el **Object Relational Designer**, la superficie de diseño vacía representa un <xref:System.Data.Linq.DataContext> listo para su configuración. el <xref:System.Data.Linq.DataContext> se configura con la información de conexión proporcionada por el primer elemento que se arrastra hasta la superficie de diseño. Por lo tanto, el <xref:System.Data.Linq.DataContext> se configura con la información de conexión desde el primer elemento que se coloca en la superficie de diseño. Para obtener más información sobre la <xref:System.Data.Linq.DataContext> , vea clase [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>Crear clases de entidad que se asignan a tablas de base de datos y vistas

Puede crear clases de entidad asignadas a tablas y vistas arrastrando tablas de base de datos y vistas de **Explorador de servidores** o **Database Explorer** hasta la **Object Relational Designer**. Como se indica en la sección anterior, el <xref:System.Data.Linq.DataContext> se configura con la información de conexión proporcionada por el primer elemento que se arrastra hasta la superficie de diseño. Si se agrega un elemento subsiguiente que use otra conexión a la **Object Relational Designer**, puede cambiar la conexión para el <xref:System.Data.Linq.DataContext>. Para obtener más información, consulte [Cómo: crear clases de LINQ to SQL asignadas a tablas y vistas (Object Relational Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>Crear métodos de DataContext que llamen a procedimientos almacenados y funciones

Puede crear <xref:System.Data.Linq.DataContext> métodos que llaman (estén asignados) procedimientos almacenados y funciones arrastrándolos desde **Explorador de servidores** o **Database Explorer** hasta la **Object Relational Designer** . Procedimientos almacenados y funciones se agregan a la **Object Relational Designer** como métodos de la <xref:System.Data.Linq.DataContext>.

> [!NOTE]
> Cuando arrastre los procedimientos almacenados y funciones de **Explorador de servidores** o **Database Explorer** hasta la **Object Relational Designer**, el tipo de valor devuelto de generado <xref:System.Data.Linq.DataContext> método difiere según donde se coloque el elemento. Para obtener más información, consulte [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configurar DataContext de modo que utilice procedimientos almacenados para guardar los datos entre las clases de entidad y una base de datos

Como se ha indicado anteriormente, puede crear métodos de <xref:System.Data.Linq.DataContext> que llamen a los procedimientos almacenados y funciones. Además, también puede asignar procedimientos almacenados que se usan para el valor predeterminado LINQ al comportamiento en tiempo de ejecución de SQL, que realiza inserciones, actualizaciones y eliminaciones. Para obtener más información, consulte [Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Herencia y Object Relational designer

Al igual que otros objetos, clases LINQ to SQL puede usar la herencia y derivarse de otras clases. En una base de datos, las relaciones de herencia se crean de varias maneras. El **Object Relational Designer** admite el concepto de herencia de tabla única normalmente implementada en los sistemas relacionales. Para obtener más información, consulte [Cómo: configurar la herencia mediante Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>Consultas LINQ to SQL

Las clases de entidad creadas por el **Object Relational Designer** están diseñados para su uso con [Language-Integrated query (LINQ)](/dotnet/csharp/linq/). Para obtener más información, consulte [Cómo: consultar información](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Separar el código de clase DataContext y entidad generado en diferentes espacios de nombres

El **Object Relational Designer** proporciona el **contexto Namespace** y **Namespace Entity** propiedades en el <xref:System.Data.Linq.DataContext>. Estas propiedades determinan en qué espacio de nombres se generan la clase <xref:System.Data.Linq.DataContext> y el código de clase de entidad. De forma predeterminada, estas propiedades están vacías y las clases de entidad y <xref:System.Data.Linq.DataContext> se generan en el espacio de nombres de la aplicación. Para generar el código en un espacio de nombres distinto del espacio de nombres de la aplicación, escriba un valor en el **contexto Namespace** o **Namespace Entity** propiedades.

## <a name="reference-content"></a>Contenido de referencia

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>Vea también

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Preguntas más frecuentes (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)
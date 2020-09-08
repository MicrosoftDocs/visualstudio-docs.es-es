---
title: Introducción a Object Relational Designer de LINQ to SQL
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 55f6fa2ad9eda2d701563d1fa99c76f5cd5c7c1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282012"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Herramientas de LINQ to SQL en Visual Studio

LINQ to SQL fue la primera tecnología de asignación relacional de objetos publicada por Microsoft. Funciona bien en escenarios básicos y todavía se admite en Visual Studio, pero ya no está en desarrollo activo. Use LINQ to SQL al mantener una aplicación heredada en la que ya se use, o bien en aplicaciones sencillas que utilicen SQL Server y no requieran asignación de varias tablas. En general, las aplicaciones nuevas deben usar Entity Framework cuando se necesite una capa de asignador relacional de objetos.

## <a name="install-the-linq-to-sql-tools"></a>Instalación de las herramientas de LINQ to SQL

En Visual Studio, para crear clases de LINQ to SQL que representan tablas SQL se usa **Object Relational Designer** (**O/R Designer**). Object Relational Designer es la interfaz de usuario para editar archivos .dbml. Para la edición de archivos .dbml con una superficie de diseñador se necesitan las herramientas de LINQ to SQL que no se instalan de forma predeterminada como parte de las cargas de trabajo de Visual Studio.

Para instalar las herramientas de LINQ to SQL, inicie el instalador de Visual Studio, elija **Modificar**, seleccione la pestaña **Componentes individuales** y después **Herramientas de LINQ to SQL** en la categoría **Herramientas de código**.

## <a name="what-is-the-or-designer"></a>Definición de Object Relational Designer

**Object Relational Designer** tiene dos áreas distintas en su superficie de diseño: el panel de entidades (a la izquierda) y el panel de métodos (a la derecha). El panel de entidades es la superficie de diseño principal que muestra las clases de entidad, asociaciones y jerarquías de herencia. El panel de métodos es la superficie de diseño que muestra los métodos <xref:System.Data.Linq.DataContext> que están asignados a procedimientos almacenados y funciones.

**Object Relational Designer** proporciona una superficie de diseño visual para crear clases de entidad y asociaciones (relaciones) de [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) basadas en los objetos de una base de datos. Es decir, **Object Relational Designer** se usa para crear un modelo de objetos en una aplicación que se asigna a los objetos de una base de datos. También genera una clase <xref:System.Data.Linq.DataContext> fuertemente tipada que envía y recibe datos entre las clases de entidad y la base de datos. **Object Relational Designer** también proporciona funcionalidad para asignar procedimientos almacenados y funciones a los métodos de <xref:System.Data.Linq.DataContext> con el fin de devolver datos y rellenar las clases de entidad. Por último, **Object Relational Designer** permite diseñar relaciones de herencia entre las clases de entidad.

## <a name="open-the-or-designer"></a>Apertura de Object Relational Designer

Para agregar un modelo de entidad de LINQ to SQL al proyecto, elija **Proyecto** > **Agregar nuevo elemento** y, después, seleccione **Clases de LINQ to SQL** en la lista de elementos de proyecto:

![Clases LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio crea un archivo *.dbml* y lo agrega a la solución. Es el archivo de asignación XML y sus archivos de código relacionados.

![Clases de LINQ to SQL en el Explorador de soluciones](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

Al seleccionar el archivo *.dbml*, Visual Studio muestra la superficie de **Object Relational Designer** que le permite crear visualmente el modelo. En la ilustración siguiente se muestra el diseñador una vez que se han arrastrado las tablas `Customers` y `Orders` de Northwind desde el **Explorador de servidores**. Observe la relación entre las tablas.

![Diseñador LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> **Object Relational Designer** es un asignador relacional de objetos simple porque solo admite relaciones de asignación 1:1. Es decir, una clase de entidad únicamente puede tener una relación de asignación 1:1 con una tabla o vista de base de datos. No se admiten asignaciones complejas como la de una clase de entidad a una tabla combinada; para ello, use Entity Framework. Además, el diseñador es un generador de código unidireccional. Esto significa que solo se reflejan en el archivo de código los cambios que se realizan en la superficie del diseñador. Los cambios realizados manualmente en el archivo de código no se reflejan en **Object Relational Designer**. Cualquier cambio que se realice manualmente en el archivo de código se sobrescribe cuando se guarda el diseñador y se vuelve a generar el código. Para obtener información acerca de cómo agregar código de usuario y extender las clases generadas por el **Object Relational Designer**, vea [Cómo: Ampliar el código generado por Object Relational Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="create-and-configure-the-datacontext"></a>Creación y configuración del objeto DataContext

Después de agregar un elemento de **Clases de LINQ to SQL** a un proyecto y abrir **Object Relational Designer**, la superficie de diseño vacía representa un objeto <xref:System.Data.Linq.DataContext> vacío listo para su configuración. El elemento <xref:System.Data.Linq.DataContext> se configura con la información de conexión proporcionada por el primer elemento que se arrastra hasta la superficie de diseño. Por consiguiente, <xref:System.Data.Linq.DataContext> se configura usando la información de conexión del primer elemento que se coloca sobre la superficie de diseño. Para obtener más información sobre la clase <xref:System.Data.Linq.DataContext>, vea [Métodos de DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>Creación de clases de entidad que se asignan a tablas y vistas de base de datos

Puede crear clases de entidad asignadas a tablas y vistas si arrastra tablas y vistas de base de datos desde el **Explorador de servidores** o el **Explorador de bases de datos** hasta **Object Relational Designer**. Tal como se ha indicado en la sección anterior, el <xref:System.Data.Linq.DataContext> se configura con la información de conexión proporcionada por el primer elemento que se arrastra hasta la superficie de diseño. Si se agrega a **Object Relational Designer** un elemento posterior que use otra conexión, puede cambiar la conexión para <xref:System.Data.Linq.DataContext>. Para obtener más información, vea [Cómo: Creación de clases de LINQ to SQL asignadas a tablas y vistas (Object Relational Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>Creación de métodos de DataContext que llamen a procedimientos almacenados y funciones

Puede crear métodos de <xref:System.Data.Linq.DataContext> que llamen (estén asignados) a procedimientos almacenados y funciones si los arrastra desde el **Explorador de servidores** o el **Explorador de bases de datos** hasta **Object Relational Designer**. Los procedimientos almacenados y las funciones se agregan a **Object Relational Designer** como métodos de <xref:System.Data.Linq.DataContext>.

> [!NOTE]
> Al arrastrar procedimientos almacenados y funciones desde el **Explorador de servidores** o el **Explorador de bases de datos** hasta **Object Relational Designer**, el tipo de valor devuelto del método generado de <xref:System.Data.Linq.DataContext> difiere según la ubicación donde se coloque el elemento. Para obtener más información, vea [Métodos de DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configuración de un objeto DataContext a fin de usar procedimientos almacenados para guardar datos entre clases de entidad y una base de datos

Como se ha indicado anteriormente, puede crear métodos de <xref:System.Data.Linq.DataContext> que llamen a los procedimientos almacenados y funciones. Además, también puede asignar los procedimientos almacenados que se usan para el comportamiento predeterminado en tiempo de ejecución de LINQ to SQL, que realiza inserciones, actualizaciones y eliminaciones. Para obtener más información, vea [Cómo: Asignación de procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Herencia y Object Relational Designer

Al igual que otros objetos, las clases de LINQ to SQL pueden usar la herencia y derivarse de otras clases. En una base de datos, las relaciones de herencia se crean de varias maneras. **Object Relational Designer** admite el concepto de herencia de tabla única que normalmente se implementa en sistemas relacionales. Para obtener más información, vea [Cómo: configurar herencia mediante Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>Consultas de LINQ to SQL

Las clases de entidad creadas por **Object Relational Designer** están diseñadas para su uso con [Language Integrated Query (LINQ)](/dotnet/csharp/linq/). Para obtener más información, vea [Cómo: para consultar información](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Separación del objeto DataContext generado y el código de clase de entidad en espacios de nombres distintos

**Object Relational Designer** proporciona las propiedades **Espacio de nombres del contexto** y **Espacio de nombres de la entidad** de <xref:System.Data.Linq.DataContext>. Estas propiedades determinan en qué espacio de nombres se generan la clase <xref:System.Data.Linq.DataContext> y el código de clase de entidad. De forma predeterminada, estas propiedades están vacías y las clases de entidad y <xref:System.Data.Linq.DataContext> se generan en el espacio de nombres de la aplicación. Para generar el código en un espacio de nombres distinto del espacio de nombres de la aplicación, especifique un valor para las propiedades **Espacio de nombres del contexto** o **Espacio de nombres de la entidad**.

## <a name="reference-content"></a>Contenido de referencia

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>Vea también

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Preguntas más frecuentes (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)

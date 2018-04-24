---
title: Introducción a Visual Studio Object Relational Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c1d065a31c8c15ac26b7ded368499846cb9f0645
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>LINQ to SQL de las herramientas en Visual Studio

LINQ to SQL era la primera tecnología de asignación objeto-relacional publicada por Microsoft. Funciona bien en escenarios básicos y continúa siendo compatible con Visual Studio, pero es ya no está en desarrollo activo. Usar LINQ to SQL al mantener una aplicación heredada que ya está utilizando, o en aplicaciones sencillas que use SQL Server y no requieren la asignación de varias tabla. En general, aplicaciones nuevas deben usar Entity Framework cuando se requiere un nivel de asignador relacional de objetos.

En Visual Studio, crear LINQ a las clases SQL que representan tablas SQL mediante el uso de Object Relational Designer (Object Relational Designer).

Object Relational Designer tiene dos áreas distintas en la superficie de diseño: el panel de entidades de la izquierda y el panel de métodos a la derecha. El panel de entidades es la superficie de diseño principal que muestra las clases de entidad, asociaciones y jerarquías de herencia. El panel de métodos es la superficie de diseño que muestra la <xref:System.Data.Linq.DataContext> métodos que están asignados a procedimientos almacenados y funciones.

Object Relational Designer proporciona una superficie de diseño visual para crear [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) las clases de entidad y asociaciones (relaciones) que se basan en los objetos de una base de datos. En otras palabras, el Object Relational Designer se utiliza para crear un modelo de objetos en una aplicación que se asigna a los objetos en una base de datos. También genera una clase <xref:System.Data.Linq.DataContext> fuertemente tipada que se usa para enviar y recibir datos entre las clases de entidad y la base de datos. Object Relational Designer también proporciona funcionalidad para asignar procedimientos almacenados y funciones a <xref:System.Data.Linq.DataContext> métodos para devolver datos y rellenar las clases de entidad. Por último, el Object Relational Designer permite diseñar relaciones de herencia entre las clases de entidad.

## <a name="open-the-or-designer"></a>Abrir Object Relational designer

Para agregar un LINQ al modelo de entity SQL al proyecto, elija **proyecto** > **Agregar nuevo elemento**y, a continuación, seleccione **clases LINQ to SQL** en la lista de elementos de proyecto:

![Clases LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio crea un archivo .dbml y lo agrega a la solución. Este es el archivo de asignación de XML y sus archivos de código relacionados.

![Clases LINQ to SQL en el Explorador de soluciones](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

Cuando se selecciona el archivo .dbml, Visual Studio muestra la superficie del Diseñador de Object Relational que le permite crear visualmente el modelo. En la siguiente ilustración muestra el diseñador después de las tablas de Northwind Customers y Orders que se han arrastrado desde el Explorador de servidores. Tenga en cuenta la relación entre las tablas.

![Diseñador LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> Object Relational Designer es un asignador relacional de objetos simple porque admite únicamente relaciones de asignación 1:1. Es decir, una clase de entidad únicamente puede tener una relación de asignación 1:1 con una tabla o vista de base de datos. No se admiten asignaciones complejas, como la asignación de una clase de entidad para una tabla combinada, utilizar Entity Framework para la asignación compleja. Además, el diseñador es un generador de código unidireccional. Esto significa que solo se reflejan en el archivo de código los cambios que se realizan en la superficie del diseñador. Los cambios manuales en el archivo de código no se reflejan en el Object Relational Designer. Cualquier cambio que se realice manualmente en el archivo de código se sobrescribe cuando se guarda el diseñador y se vuelve a generar el código. Para obtener información acerca de cómo agregar código de usuario y extender las clases generadas por el Object Relational Designer, vea [Cómo: ampliar código generado por el Object Relational Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="create-and-configure-the-datacontext"></a>Crear y configurar DataContext

Después de agregar un **clases LINQ to SQL** elemento a un proyecto y abre el Object Relational Designer, la superficie de diseño vacía representa vacío <xref:System.Data.Linq.DataContext> listo para configurarlo. el <xref:System.Data.Linq.DataContext> está configurado con información de conexión proporcionada por el primer elemento que se arrastra hasta la superficie de diseño... Por lo tanto, el <xref:System.Data.Linq.DataContext> se configura con información de conexión desde el primer elemento que se coloca en la superficie de diseño. Para obtener más información sobre la <xref:System.Data.Linq.DataContext> , vea clase [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>Crear clases de entidad que se asignan a las tablas de base de datos y vistas

Puede crear las clases de entidad asignadas a tablas y vistas arrastrando tablas de base de datos y vistas de **Explorador de servidores**/**el Explorador de base de datos** en Object Relational Designer. Tal como se ha indicado en la sección anterior, el <xref:System.Data.Linq.DataContext> se configura con la información de conexión proporcionada por el primer elemento que se arrastra hasta la superficie de diseño. Si se agrega un elemento subsiguiente que use otra conexión a Object Relational Designer, puede cambiar la conexión para el <xref:System.Data.Linq.DataContext>. Para obtener más información, consulte [Cómo: crear clases de LINQ to SQL asignadas a tablas y vistas (Object Relational Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>Crear métodos de DataContext que llamen a los procedimientos almacenados y funciones

Puede crear <xref:System.Data.Linq.DataContext> métodos que llaman (estén asignados) los procedimientos almacenados y funciones arrastrándolos desde **Explorador de servidores**/**el Explorador de base de datos** en Object Relational Designer. Procedimientos almacenados y funciones se agregan a Object Relational Designer como métodos de la <xref:System.Data.Linq.DataContext>.

> [!NOTE]
> Al arrastrar los procedimientos almacenados y funciones de **Explorador de servidores**/**el Explorador de base de datos** en Object Relational Designer, el tipo de valor devuelto de generado <xref:System.Data.Linq.DataContext> difiere del método Dependiendo de dónde colocar el elemento. Para obtener más información, consulte [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configurar DataContext de modo que utilice los procedimientos almacenados para guardar datos entre las clases de entidad y una base de datos

Como se ha indicado anteriormente, puede crear métodos de <xref:System.Data.Linq.DataContext> que llamen a los procedimientos almacenados y funciones. Además, también puede asignar procedimientos almacenados que pueden utilizarse para el comportamiento predeterminado del LINQ to SQL en tiempo de ejecución que realiza inserciones, actualizaciones y eliminaciones. Para obtener más información, consulte [Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Herencia y Object Relational designer

Al igual que otros objetos, clases LINQ to SQL puede usar la herencia y derivarse de otras clases. En una base de datos, las relaciones de herencia se crean de varias maneras. Object Relational Designer admite el concepto de herencia de tabla única normalmente implementada en los sistemas relacionales. Para obtener más información, consulte [Cómo: configurar la herencia utilizando Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>Consultas LINQ to SQL

Las clases de entidad creadas por el Object Relational Designer están diseñadas para su uso con [Language-Integrated Query (LINQ)](/dotnet/csharp/linq/). Para obtener más información, consulte [Cómo: consultar información](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Separar el código de clase DataContext y entidad generado en diferentes espacios de nombres

Object Relational Designer proporciona la **contexto Namespace** y **entidad Namespace** propiedades en el <xref:System.Data.Linq.DataContext>. Estas propiedades determinan en qué espacio de nombres se generan la clase <xref:System.Data.Linq.DataContext> y el código de clase de entidad. De forma predeterminada, estas propiedades están vacías y las clases de entidad y <xref:System.Data.Linq.DataContext> se generan en el espacio de nombres de la aplicación. Para compilar el código en un espacio de nombres distinto del espacio de nombres de la aplicación, escriba un valor en el **contexto Namespace** o **entidad Namespace** propiedades.

## <a name="reference-content"></a>Contenido de referencia

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>Vea también

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [(.NET Framework) de preguntas más frecuentes](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)
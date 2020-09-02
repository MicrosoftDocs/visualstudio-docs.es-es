---
title: Herramientas de LINQ to SQL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 470cfabd54fa5f2b92001a635477c60d45fac538
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651516"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Herramientas de LINQ to SQL en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

LINQ to SQL era la primera tecnología de asignación relacional de objetos lanzada por Microsoft. Funciona bien en escenarios básicos y sigue siendo compatible con Visual Studio, pero ya no está en desarrollo activo. Use LINQ to SQL al mantener una aplicación heredada que ya la esté usando o en aplicaciones sencillas que utilicen SQL Server y no requieran asignación de varias tablas. En general, las aplicaciones nuevas deben usar el Entity Framework cuando se requiere una capa de asignador relacional de objetos.

 En Visual Studio, se crean LINQ to SQL clases que representan tablas SQL mediante el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Tiene dos áreas distintas en su superficie de diseño: el panel entidades de la izquierda y el panel métodos a la derecha. El panel de entidades es la superficie de diseño principal que muestra las clases de entidad, asociaciones y jerarquías de herencia. El panel de métodos es la superficie de diseño que muestra los métodos <xref:System.Data.Linq.DataContext> que están asignados a procedimientos almacenados y funciones.

 [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)]( [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ) Proporciona una superficie de diseño visual para crear [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) clases de entidad y asociaciones (relaciones) basadas en objetos de una base de datos. Es decir, el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] se usa para crear un modelo de objetos en una aplicación que se asigna a los objetos de una base de datos. También genera una clase <xref:System.Data.Linq.DataContext> fuertemente tipada que se usa para enviar y recibir datos entre las clases de entidad y la base de datos. El [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] también proporciona la funcionalidad para asignar los procedimientos almacenados y funciones a los métodos de <xref:System.Data.Linq.DataContext> con el fin de devolver datos y rellenar las clases de entidad. Por último, el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] permite diseñar relaciones de herencia entre las clases de entidad.

## <a name="opening-the-or-designer"></a>Abrir Object Relational Designer
 Para agregar un LINQ to SQL modelo de entidad al proyecto, elija **proyecto &#124; agregar nuevo elemento** y, a continuación, elija  **clases de LINQ to SQL** de la lista de elementos de proyecto:

 ![Clases de LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png "Clases de LINQ to SQL de raddata")

 Visual Studio crea un archivo. dbml y lo agrega a la solución. Este es el archivo de asignación XML y sus archivos de código relacionados.

 ![LINQ to SQL clases en Explorador de soluciones](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata LINQ to SQL clases en Explorador de soluciones")

 Al seleccionar el archivo. dbml, Visual Studio muestra la superficie del diseñador de O/R que le permite crear visualmente el modelo. En la ilustración siguiente se muestra el diseñador una vez que se han arrastrado las tablas Customers y Orders de Northwind desde Explorador de servidores. Observe la relación entre las tablas.

 ![Diseñador LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png "raddata diseñador de LINQ to SQL")

> [!IMPORTANT]
> [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Es un asignador relacional de objetos simple porque solo admite relaciones de asignación de 1:1. Es decir, una clase de entidad únicamente puede tener una relación de asignación 1:1 con una tabla o vista de base de datos. No se admite la asignación compleja, como la asignación de una clase de entidad a una tabla combinada. Use el Entity Framework para la asignación compleja. Además, el diseñador es un generador de código unidireccional. Esto significa que solo se reflejan en el archivo de código los cambios que se realizan en la superficie del diseñador. Los cambios realizados manualmente en el archivo de código no se reflejan en el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Cualquier cambio que se realice manualmente en el archivo de código se sobrescribe cuando se guarda el diseñador y se vuelve a generar el código. Para obtener información sobre cómo agregar código de usuario y extender las clases generadas por [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , vea [Cómo: extender el código generado por el Object](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md)Relational Designer.

## <a name="creating-and-configuring-the-datacontext"></a>Crear y configurar DataContext
 Después de agregar un elemento de **clases de LINQ to SQL** a un proyecto y abrir el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , la superficie de diseño vacía representa un vacío <xref:System.Data.Linq.DataContext> listo para configurarlo. <xref:System.Data.Linq.DataContext>se configura con la información de conexión proporcionada por el primer elemento que se arrastra hasta la superficie de diseño. Por consiguiente, <xref:System.Data.Linq.DataContext> se configura usando la información de conexión del primer elemento que se coloca sobre la superficie de diseño. Para obtener más información sobre la <xref:System.Data.Linq.DataContext> clase, vea [métodos DataContext (Object](../data-tools/datacontext-methods-o-r-designer.md)Relational Designer).

## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Crear clases de entidad que se asignan a tablas y vistas de base de datos
 Puede crear clases de entidad asignadas a tablas y vistas arrastrando tablas y vistas de base de datos desde **Explorador de servidores** / **Explorador de bases de datos** al [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Tal como se ha indicado en la sección anterior, el <xref:System.Data.Linq.DataContext> se configura con la información de conexión proporcionada por el primer elemento que se arrastra hasta la superficie de diseño. Si se agrega al [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] un elemento subsiguiente que use otra conexión, se puede cambiar la conexión para <xref:System.Data.Linq.DataContext>. Para obtener más información, vea [Cómo: crear clases de LINQ to SQL asignadas a tablas y vistas (Object](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)Relational Designer).

## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Crear métodos de DataContext que llamen a procedimientos almacenados y funciones
 Puede crear <xref:System.Data.Linq.DataContext> métodos que llamen a (se asignan a) procedimientos almacenados y funciones arrastrándolos desde **Explorador de servidores** / **Explorador de bases de datos** hasta el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Los procedimientos almacenados y funciones se agregan al [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] como métodos de <xref:System.Data.Linq.DataContext>.

> [!NOTE]
> Al arrastrar procedimientos almacenados y funciones desde **Explorador de servidores** / **Explorador de bases de datos** al [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , el tipo de valor devuelto del <xref:System.Data.Linq.DataContext> método generado varía en función de dónde se coloque el elemento. Para obtener más información, vea [métodos DataContext (Object](../data-tools/datacontext-methods-o-r-designer.md)Relational Designer).

## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configurar DataContext de modo que se usen los procedimientos almacenados para guardar los datos entre las clases de entidad y una base de datos
 Como se ha indicado anteriormente, puede crear métodos de <xref:System.Data.Linq.DataContext> que llamen a los procedimientos almacenados y funciones. Además, también puede asignar los procedimientos almacenados que se pueden usar para el comportamiento predeterminado del motor en tiempo de ejecución [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] en materia de inserciones, actualizaciones y eliminaciones. Para obtener más información, vea [Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)Relational Designer).

## <a name="inheritance-and-the-or-designer"></a>Herencia y Object Relational Designer
 Al igual que otros objetos, las clases de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] pueden usar la herencia y derivarse de otras clases. En una base de datos, las relaciones de herencia se crean de varias maneras. El [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] admite el concepto de la herencia de tabla única normalmente implementada en los sistemas relacionales. Para obtener más información, consulte [Cómo: configurar la herencia mediante Object](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)Relational Designer.

## <a name="linq-to-sql-queries"></a>Consultas de LINQ to SQL
 Las clases de entidad creadas por [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] están diseñadas para su uso con [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d). Para obtener más información, consulte [Cómo: consultar información](https://msdn.microsoft.com/library/e538d288-2070-40ca-9da6-4fbc68cd6ad0).

## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Separar la clase DataContext generada y el código de clase de entidad en espacios de nombres distintos
 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Proporciona las propiedades **espacio** de nombres del contexto y **espacio de nombres** de la entidad en <xref:System.Data.Linq.DataContext> . Estas propiedades determinan en qué espacio de nombres se generan la clase <xref:System.Data.Linq.DataContext> y el código de clase de entidad. De forma predeterminada, estas propiedades están vacías y las clases de entidad y <xref:System.Data.Linq.DataContext> se generan en el espacio de nombres de la aplicación. Para generar el código en un espacio de nombres distinto del espacio de nombres de la aplicación, especifique un valor para las propiedades **Espacio de nombres del contexto** o **Espacio de nombres de la entidad**.

## <a name="in-this-section"></a>En esta sección
 [DataContext (métodos) (Object](../data-tools/datacontext-methods-o-r-designer.md) Relational Designer) Explica qué <xref:System.Data.Linq.DataContext> son los métodos y cómo crearlos.

 [Herencia de clases de datos (Object](../data-tools/data-class-inheritance-o-r-designer.md) Relational Designer) Describe el concepto de herencia de tabla única y cómo se implementa en [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [Cómo: crear clases de LINQ to SQL asignadas a tablas y vistas (Object](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md) Relational Designer) Describe cómo crear clases de entidad asignadas a tablas y vistas en una base de datos.

 [Cómo: crear una asociación (relación) entre LINQ to SQL clases (Object](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) Relational Designer) Describe cómo crear una relación entre [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] las clases de entidad.

 [Cómo: crear métodos DataContext asignados a funciones y procedimientos almacenados (Object](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) Relational Designer) Describe cómo crear <xref:System.Data.Linq.DataContext> métodos que ejecutan procedimientos almacenados o funciones cuando se les llama.

 [Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) Relational Designer) Describe cómo configurar un <xref:System.Data.Linq.DataContext> para utilizar procedimientos almacenados al guardar datos de las clases de entidad de nuevo en una base de datos de.

 [Cómo: cambiar el tipo de valor devuelto de un método DataContext (Object](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md) Relational Designer) Describe cómo establecer el tipo de valor devuelto de un <xref:System.Data.Linq.DataContext> método para que sea el tipo de una clase de entidad o un tipo generado automáticamente creado por Object Relational Designer.

 [Cómo: agregar validación a clases de entidad](../data-tools/how-to-add-validation-to-entity-classes.md) Describe cómo generar métodos parciales que permiten agregar código durante los cambios de propiedad y las actualizaciones de la clase de entidad.

 [Cómo: activar y desactivar la pluralización (Object](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md) Relational Designer) Describe cómo activar y desactivar el cambio de nombre automático de las clases que se agregan a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [Cómo: configurar la herencia mediante Object](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) Relational Designer Describe cómo configurar las clases de entidad mediante la herencia de tabla única con el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [Cómo: extender el código generado por Object](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md) Relational Designer Describe cómo y dónde agregar código que no se sobrescribirá cuando los cambios en los objetos en el diseñador de O/R vuelvan a generar el código.

 [Tutorial: crear clases de LINQ to SQL mediante la herencia de tabla única (Object](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) Relational Designer) Proporciona instrucciones paso a paso para configurar las clases de entidad mediante la herencia de tabla única con el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [Tutorial: personalizar el comportamiento de inserción, actualización y eliminación de las clases de entidad](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) Proporciona instrucciones paso a paso para configurar un <xref:System.Data.Linq.DataContext> para utilizar procedimientos almacenados al guardar datos de las clases de entidad de nuevo en una base de datos de.

## <a name="reference-content"></a>Contenido de referencia
 <xref:System.Linq>

 <xref:System.Data.Linq>

## <a name="see-also"></a>Consulte también
 [Preguntas más frecuentes sobre](https://msdn.microsoft.com/library/252ed666-0679-4eea-b71b-2f14117ef443) [Visual Studio Data tools para .net](../data-tools/visual-studio-data-tools-for-dotnet.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [acceder a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)

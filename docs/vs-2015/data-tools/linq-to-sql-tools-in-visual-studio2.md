---
title: Herramientas LINQ to SQL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d7dcb33add9726a341c1b4b92c032be7c289c2d2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987516"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>LINQ to SQL Tools en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


LINQ to SQL era la primera tecnología de asignación relacional de objetos publicada por Microsoft. Funciona bien en escenarios básicos y sigue siendo compatible con Visual Studio, pero ya no está en desarrollo activo. Usar LINQ to SQL al mantener una aplicación heredada que ya está usando, o en aplicaciones sencillas que usan SQL Server y no requieren la asignación de varias tabla. En general, aplicaciones nuevas deben utilizar Entity Framework cuando se requiere un nivel de asignador relacional de objetos.

 En Visual Studio, cree LINQ a las clases SQL que representan las tablas SQL mediante el uso de la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 El [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] tiene dos áreas distintas en su superficie de diseño: el panel entidades de la izquierda y el panel de métodos de la derecha. El panel de entidades es la superficie de diseño principal que muestra las clases de entidad, asociaciones y jerarquías de herencia. El panel de métodos es la superficie de diseño que muestra los métodos <xref:System.Data.Linq.DataContext> que están asignados a procedimientos almacenados y funciones.

 El [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) proporciona una superficie de diseño visual para crear [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) clases de entidad y asociaciones (relaciones) que se basan en los objetos de una base de datos. Es decir, el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] se usa para crear un modelo de objetos en una aplicación que se asigna a los objetos de una base de datos. También genera una clase <xref:System.Data.Linq.DataContext> fuertemente tipada que se usa para enviar y recibir datos entre las clases de entidad y la base de datos. El [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] también proporciona la funcionalidad para asignar los procedimientos almacenados y funciones a los métodos de <xref:System.Data.Linq.DataContext> con el fin de devolver datos y rellenar las clases de entidad. Por último, el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] permite diseñar relaciones de herencia entre las clases de entidad.

## <a name="opening-the-or-designer"></a>Abrir Object Relational Designer
 Para agregar un LINQ al modelo de entity SQL al proyecto, elija **proyecto &#124; Agregar nuevo elemento** y, a continuación, elija **clases LINQ to SQL** en la lista de elementos de proyecto:

 ![Clases LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png "raddata clases LINQ to SQL")

 Visual Studio crea un archivo .dbml y lo agrega a la solución. Este es el archivo de asignación XML y sus archivos de código relacionados.

 ![Las clases de LINQ to SQL en el Explorador de soluciones](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata de LINQ to SQL clases en el Explorador de soluciones")

 Al seleccionar el archivo .dbml, Visual Studio muestra la superficie del diseñador Relational que le permite crear visualmente el modelo. La siguiente ilustración muestra el diseñador después de las tablas de Northwind Customers y Orders se ha arrastrado desde el Explorador de servidores. Tenga en cuenta la relación entre las tablas.

 ![Diseñador LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png "raddata diseñador LINQ to SQL")

> [!IMPORTANT]
>  El [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] es un asignador relacional de objetos simple porque admite únicamente relaciones de asignación 1:1. Es decir, una clase de entidad únicamente puede tener una relación de asignación 1:1 con una tabla o vista de base de datos. No se admiten asignaciones complejas, como la asignación de una clase de entidad a una tabla combinada, utilizar Entity Framework para la asignación compleja. Además, el diseñador es un generador de código unidireccional. Esto significa que solo se reflejan en el archivo de código los cambios que se realizan en la superficie del diseñador. Los cambios realizados manualmente en el archivo de código no se reflejan en el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Cualquier cambio que se realice manualmente en el archivo de código se sobrescribe cuando se guarda el diseñador y se vuelve a generar el código. Para obtener información acerca de cómo agregar código de usuario y extender las clases generadas por el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], vea [Cómo: Ampliar código generado por el Object Relational Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="creating-and-configuring-the-datacontext"></a>Crear y configurar DataContext
 Después de agregar un **clases LINQ to SQL** elemento a un proyecto y abrir el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], la superficie de diseño vacía representa un <xref:System.Data.Linq.DataContext> listo para su configuración. el <xref:System.Data.Linq.DataContext> se configura con la información de conexión proporcionada por el primer elemento que se arrastra hasta la superficie de diseño... Por consiguiente, <xref:System.Data.Linq.DataContext> se configura usando la información de conexión del primer elemento que se coloca sobre la superficie de diseño. Para obtener más información sobre la <xref:System.Data.Linq.DataContext> , vea clase [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Crear clases de entidad que se asignan a tablas y vistas de base de datos
 Puede crear clases de entidad asignadas a tablas y vistas arrastrando tablas de base de datos y vistas de **Explorador de servidores**/**Database Explorer** hasta el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Tal como se ha indicado en la sección anterior, el <xref:System.Data.Linq.DataContext> se configura con la información de conexión proporcionada por el primer elemento que se arrastra hasta la superficie de diseño. Si se agrega al [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] un elemento subsiguiente que use otra conexión, se puede cambiar la conexión para <xref:System.Data.Linq.DataContext>. Para obtener más información, vea [Cómo: Creación de clases de LINQ to SQL asignadas a tablas y vistas (Object Relational Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Crear métodos de DataContext que llamen a procedimientos almacenados y funciones
 Puede crear <xref:System.Data.Linq.DataContext> métodos que llaman (estén asignados) los procedimientos almacenados y funciones arrastrándolos desde **Explorador de servidores**/**Database Explorer** hasta el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Los procedimientos almacenados y funciones se agregan al [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] como métodos de <xref:System.Data.Linq.DataContext>.

> [!NOTE]
>  Cuando arrastre los procedimientos almacenados y funciones de **Explorador de servidores**/**Database Explorer** hasta la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], el tipo de valor devuelto de generado <xref:System.Data.Linq.DataContext> difiere del método Dependiendo de dónde colocar el elemento. Para obtener más información, consulte [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configurar DataContext de modo que se usen los procedimientos almacenados para guardar los datos entre las clases de entidad y una base de datos
 Como se ha indicado anteriormente, puede crear métodos de <xref:System.Data.Linq.DataContext> que llamen a los procedimientos almacenados y funciones. Además, también puede asignar los procedimientos almacenados que se pueden usar para el comportamiento predeterminado del motor en tiempo de ejecución [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] en materia de inserciones, actualizaciones y eliminaciones. Para obtener más información, vea [Cómo: Asignación de procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Herencia y Object Relational Designer
 Al igual que otros objetos, las clases de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] pueden usar la herencia y derivarse de otras clases. En una base de datos, las relaciones de herencia se crean de varias maneras. El [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] admite el concepto de la herencia de tabla única normalmente implementada en los sistemas relacionales. Para obtener más información, vea [Cómo: configurar herencia mediante Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>Consultas de LINQ to SQL
 Las clases de entidad creadas por el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] están diseñados para su uso con [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d). Para obtener más información, vea [Cómo: Consultar información](http://msdn.microsoft.com/library/e538d288-2070-40ca-9da6-4fbc68cd6ad0).

## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Separar la clase DataContext generada y el código de clase de entidad en espacios de nombres distintos
 El [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] proporciona el **contexto Namespace** y **Namespace Entity** propiedades en el <xref:System.Data.Linq.DataContext>. Estas propiedades determinan en qué espacio de nombres se generan la clase <xref:System.Data.Linq.DataContext> y el código de clase de entidad. De forma predeterminada, estas propiedades están vacías y las clases de entidad y <xref:System.Data.Linq.DataContext> se generan en el espacio de nombres de la aplicación. Para generar el código en un espacio de nombres distinto del espacio de nombres de la aplicación, especifique un valor para las propiedades **Espacio de nombres del contexto** o **Espacio de nombres de la entidad**.

## <a name="in-this-section"></a>En esta sección
 [Métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md) explica qué <xref:System.Data.Linq.DataContext> métodos son y cómo crearlos.

 [(Object Relational Designer) de la herencia de clases de datos](../data-tools/data-class-inheritance-o-r-designer.md) describe el concepto de herencia de tabla única y cómo se implementa en el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Cómo: Creación de LINQ to SQL asignadas a tablas y vistas (Object Relational Designer) que las clases](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md) se describe cómo crear clases de entidad que se asignan a tablas y vistas de una base de datos.

 [Cómo: Crear una asociación (relación) entre clases LINQ to SQL (Object Relational Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) se describe cómo crear una relación entre [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] clases de entidad.

 [Cómo: Crear métodos DataContext asignados a procedimientos almacenados y funciones (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) se describe cómo crear <xref:System.Data.Linq.DataContext> métodos que se ejecutan procedimientos almacenados o funciones cuando se les llama.

 [Cómo: Asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) se describe cómo configurar un <xref:System.Data.Linq.DataContext> para volver a usar los procedimientos almacenados al guardar los datos de entidad clases a una base de datos.

 [Cómo: Cambiar el tipo de valor devuelto de un método DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md) se describe cómo establecer el tipo de valor devuelto de un <xref:System.Data.Linq.DataContext> método sea el tipo de una clase de entidad o un tipo generado automáticamente, creado por el Object Relational Designer.

 [Cómo: Agregar validación a clases de entidad](../data-tools/how-to-add-validation-to-entity-classes.md) se describe cómo generar métodos parciales que permiten la adición de código durante los cambios de propiedad y actualizaciones de la clase de entidad.

 [Cómo: Activar y desactivar (Object Relational Designer) la pluralización](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md) se describe cómo activar y desactivar el cambio de nombre automático de las clases que se agregan a la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Cómo: Configurar la herencia mediante Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) se describe cómo configurar las clases de entidad con herencia de tabla única con el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Cómo: Ampliar el código generado por Object Relational Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md) describe cómo y dónde agregar código que no se sobrescribirá cuando los cambios realizados en objetos en el Object Relational Designer, vuelva a generar código.

 [Tutorial: Crear clases LINQ to SQL mediante el uso de la herencia de tabla única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) proporciona instrucciones paso a paso para configurar las clases de entidad con herencia de tabla única con el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Tutorial: Personalización de la inserción, actualización y eliminación de comportamiento de las clases de entidad](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) proporciona instrucciones paso a paso para configurar un <xref:System.Data.Linq.DataContext> para volver a usar los procedimientos almacenados al guardar los datos de entidad clases a una base de datos.

## <a name="reference-content"></a>Contenido de referencia
 <xref:System.Linq>

 <xref:System.Data.Linq>

## <a name="see-also"></a>Vea también
 [Visual Studio data tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) [preguntas más frecuentes](http://msdn.microsoft.com/library/252ed666-0679-4eea-b71b-2f14117ef443) [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [acceso a datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)

---
title: Asignación de clases de LINQ to SQL a tablas o vistas (Object Relational Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 2b34212ddad2bc5d69778f973d5975655431a829
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253014"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Procedimiento Creación de clases de LINQ to SQL asignadas a tablas y vistas (Object Relational Designer)

Las clases de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] asignadas a las tablas y vistas de base de datos se denominan *clases de entidad*. La clase de entidad se asigna a un registro, mientras que las propiedades individuales de una clase de entidad se asignan a las columnas individuales que forman un registro. Cree clases de entidad basadas en tablas o vistas de base de datos arrastrando las tablas o vistas desde **Explorador de servidores** o **Explorador de bases de datos** en las [herramientas de LINQ to SQL de Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). El **Object Relational Designer** genera las clases y aplica los [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] atributos específicos para [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] habilitar la funcionalidad (las capacidades de comunicación y edición <xref:System.Data.Linq.DataContext>de datos de). Para obtener información detallada [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] sobre las clases, vea [el LINQ to SQL modelo de objetos](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).

> [!NOTE]
> Object Relational **Designer** es un asignador relacional de objetos simple porque admite solo relaciones de asignación 1:1. Es decir, una clase de entidad únicamente puede tener una relación de asignación 1:1 con una tabla o vista de base de datos. No se admiten asignaciones complejas, como la asignación de una clase de entidad a varias tablas. Sin embargo, se puede asignar una clase de entidad a una vista que combina varias tablas relacionadas.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Crear clases de LINQ to SQL asignadas a tablas o vistas de base de datos

Al arrastrar tablas o vistas desde **Explorador de servidores** o **Explorador de bases de datos** a Object Relational **Designer,** se crean clases de entidad además <xref:System.Data.Linq.DataContext> de los métodos que se usan para realizar actualizaciones.

De forma predeterminada, el motor en tiempo de ejecución de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] crea la lógica para volver a guardar en la base de datos los cambios de una clase de entidad actualizable. Esta lógica se basa en el esquema de la tabla (las definiciones de columna e información de la clave principal). Si no desea este comportamiento, puede configurar una clase de entidad para que use procedimientos almacenados para realizar inserciones, actualizaciones y eliminaciones en lugar de usar el comportamiento predeterminado [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] en tiempo de ejecución. Para obtener más información, vea [Cómo: Asignación de procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Para crear clases de LINQ to SQL asignadas a tablas o vistas de base de datos

1. En **Servidor** o en **Explorador de bases de datos**, expanda **Tablas** o **Vistas** y busque la tabla o vista de base de datos que desee usar en la aplicación.

2. Arrastre la tabla o vista a Object Relational **Designer**.

     Se crea una clase de entidad, que aparece en la superficie de diseño. La clase de entidad tiene propiedades que se asignan a las columnas en la tabla o vista seleccionada.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Crear un origen de datos de objeto y mostrar los datos en un formulario

Después de crear las clases de entidad mediante Object Relational **Designer**, puede crear un origen de datos de objeto y rellenar la [ventana orígenes de datos](add-new-data-sources.md#data-sources-window) con las clases de entidad.

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Para crear un origen de datos de objeto basándose en las clases de entidad de LINQ to SQL

1. Para compilar el proyecto, en el menú **Compilar**, haga clic en **Compilar solución**.

2. Para abrir la ventana **orígenes de datos** , en el menú **datos** , haga clic en **Mostrar orígenes de datos**.

3. En la ventana **Orígenes de datos** , seleccione **Agregar nuevo origen de datos**.

4. Haga clic en **Objeto** en la página **Elegir un tipo de origen de datos** y después haga clic en **Siguiente**.

5. Expanda los nodos y, a continuación, busque y seleccione la clase.

    > [!NOTE]
    > Si la clase **Customer** no está disponible, cierre el asistente, compile el proyecto y vuelva a ejecutar el asistente.

6. Haga clic en **Finalizar** para crear el origen de datos y agregar la clase de entidad **Customer** a la ventana **Orígenes de datos**.

7. Arrastre los elementos desde la ventana **Orígenes de datos** a un formulario.

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)
- [Tutorial: Crear clases de LINQ to SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [DataContext methods (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md) (Métodos DataContext [Object Relational Designer])
- [Cómo: Crear métodos DataContext asignados a funciones y procedimientos almacenados (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [The LINQ to SQL object model](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model) (Modelo de objetos de LINQ to SQL)
- [Tutorial: Personalizar el comportamiento de inserción, actualización y eliminación de clases de entidad](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Cómo: Crear una asociación (relación) entre clases de LINQ to SQL (Object Relational Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)

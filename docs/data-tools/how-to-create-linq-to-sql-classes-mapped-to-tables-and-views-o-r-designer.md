---
title: 'Cómo: crear LINQ clases to SQL asignadas a tablas y vistas (Object Relational Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 11fb4265047387e30327bbbe17c9babf1f23ec61
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089330"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Cómo: crear LINQ clases to SQL asignadas a tablas y vistas (Object Relational Designer)
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] las clases que se asignan a tablas de base de datos y vistas se denominan *las clases de entidad*. La clase de entidad se asigna a un registro, mientras que las propiedades individuales de una clase de entidad se asignan a las columnas individuales que forman un registro. Crear clases de entidad que se basan en las tablas de base de datos o vistas arrastrando tablas o vistas desde **Explorador de servidores** o **Database Explorer** hasta la [de LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). El **Object Relational Designer** genera las clases y aplica las específicas [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] atributos para habilitar [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] funcionalidad (la comunicación de datos y editar las capacidades de la <xref:System.Data.Linq.DataContext>). Para obtener información detallada sobre [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] las clases, consulte [el modelo LINQ to SQL objeto](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).

> [!NOTE]
>  El **Object Relational Designer** es un asignador relacional de objetos simple porque admite únicamente relaciones de asignación 1:1. Es decir, una clase de entidad únicamente puede tener una relación de asignación 1:1 con una tabla o vista de base de datos. No se admiten asignaciones complejas, como la asignación de una clase de entidad a varias tablas. Sin embargo, se puede asignar una clase de entidad a una vista que combina varias tablas relacionadas.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Creación de LINQ a las clases SQL que se asignan a tablas de base de datos o vistas
 Al arrastrar tablas o vistas desde **Explorador de servidores** o **Database Explorer** hasta la **Object Relational Designer** crea clases de entidad además el <xref:System.Data.Linq.DataContext> métodos que se usan para realizar actualizaciones.

 De forma predeterminada, el motor en tiempo de ejecución de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] crea la lógica para volver a guardar en la base de datos los cambios de una clase de entidad actualizable. Esta lógica se basa en el esquema de la tabla (las definiciones de columna e información de la clave principal). Si no desea este comportamiento, puede configurar una clase de entidad para usar los procedimientos almacenados para realizar inserciones, actualizaciones y eliminaciones en lugar de usar el valor predeterminado [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] comportamiento en tiempo de ejecución. Para obtener más información, consulte [Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Para crear clases de LINQ to SQL asignadas a tablas o vistas de base de datos

1.  En **Server** o **Database Explorer**, expanda **tablas** o **vistas** y busque la tabla de base de datos o ver que va a utilizar en su aplicación.

2.  Arrastre la tabla o vista hasta el **Object Relational Designer**.

     Se crea una clase de entidad, que aparece en la superficie de diseño. La clase de entidad tiene propiedades que se asignan a las columnas en la tabla o vista seleccionada.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Crear un origen de datos de objeto y mostrar los datos en un formulario
 Después de crear las clases de entidad mediante el uso de la **Object Relational Designer**, puede crear un origen de datos de objeto y rellenar el [ventana Orígenes de datos](add-new-data-sources.md) con las clases de entidad.

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Para crear un origen de datos de objeto basándose en las clases de entidad de LINQ to SQL

1.  En el **compilar** menú, haga clic en **compilar solución** para compilar el proyecto.

2.  En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.

3.  En la ventana **Orígenes de datos** , seleccione **Agregar nuevo origen de datos**.

4.  Haga clic en **objeto** en el **elegir un tipo de origen de datos** página y, a continuación, haga clic en **siguiente**.

5.  Expanda los nodos y, a continuación, busque y seleccione la clase.

    > [!NOTE]
    >  Si el **cliente** clase no está disponible, cancele el asistente, compile el proyecto y vuelva a ejecutar el asistente.

6.  Haga clic en **finalizar** para crear el origen de datos y agregar el **cliente** clase de entidad para el **orígenes de datos** ventana.

7.  Arrastre elementos desde el **orígenes de datos** ventana en un formulario.

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Tutorial: Creación de LINQ a las clases SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Cómo: crear métodos DataContext asignados a procedimientos almacenados y funciones (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [El LINQ al modelo de objetos SQL](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [Tutorial: Personalizar el comportamiento de inserción, actualización y eliminación de las clases de entidad](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Cómo: crear una asociación (relación) entre clases LINQ to SQL (Object Relational Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)
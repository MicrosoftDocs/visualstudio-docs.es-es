---
title: Filtrar Creación de LINQ to SQL asignadas a tablas y vistas (Object Relational Designer) que las clases | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c2be46e61438c555fc7ee7d523b3ff9b758c0a15
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996808"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Filtrar Creación de clases de LINQ to SQL asignadas a tablas y vistas (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Clases LINQ to SQL que se asignan a tablas de base de datos y vistas se denominan *las clases de entidad*. La clase de entidad se asigna a un registro, mientras que las propiedades individuales de una clase de entidad se asignan a las columnas individuales que forman un registro. Crear clases de entidad que se basan en las tablas de base de datos o vistas arrastrando tablas o vistas desde **Explorador de servidores**/**Database Explorer** hasta la [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). El [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] genera las clases y aplica las específicas [! LINQ para atributos de SQL para habilitar [! LINQ a la funcionalidad SQL (la comunicación de datos y editar las capacidades de la <xref:System.Data.Linq.DataContext>). Para obtener información detallada acerca de [! Clases LINQ to SQL, vea [el modelo LINQ to SQL objeto](http://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810).

> [!NOTE]
> El [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] es un asignador relacional de objetos simple porque admite únicamente relaciones de asignación 1:1. Es decir, una clase de entidad únicamente puede tener una relación de asignación 1:1 con una tabla o vista de base de datos. No se admiten asignaciones complejas, como la asignación de una clase de entidad a varias tablas. Sin embargo, se puede asignar una clase de entidad a una vista que combina varias tablas relacionadas.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Crear clases de LINQ to SQL asignadas a tablas o vistas de base de datos
 Al arrastrar tablas o vistas desde **Explorador de servidores**/**Database Explorer** hasta la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] crea clases de entidad además el <xref:System.Data.Linq.DataContext> métodos que se usan para realizar actualizaciones.

 De forma predeterminada, el [! LINQ to SQL en tiempo de ejecución crea lógica para guardar los cambios en la base de datos de una clase de entidad actualizable. Esta lógica se basa en el esquema de la tabla (las definiciones de columna e información de la clave principal). Si no desea este comportamiento, puede configurar una clase de entidad para usar los procedimientos almacenados para realizar inserciones, actualizaciones y eliminaciones en lugar de usar el valor predeterminado [! LINQ al comportamiento en tiempo de ejecución SQL. Para obtener más información, vea [Cómo: Asignación de procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Para crear clases de LINQ to SQL asignadas a tablas o vistas de base de datos

1.  En **Server**/**Database Explorer**, expanda **tablas** o **vistas** y busque la tabla de base de datos o vista que desea Para usar en la aplicación.

2.  Arrastre la tabla o vista hasta el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Se crea una clase de entidad, que aparece en la superficie de diseño. La clase de entidad tiene propiedades que se asignan a las columnas en la tabla o vista seleccionada.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Crear un origen de datos de objeto y mostrar los datos en un formulario
 Después de crear las clases de entidad mediante el uso de la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], puede crear un origen de datos de objeto y rellenar el [ventana Orígenes de datos](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) con las clases de entidad.

#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Para crear un origen de datos de objeto basándose en las clases de entidad de LINQ to SQL

1.  Para compilar el proyecto, en el menú **Compilar**, haga clic en **Compilar solución**.

2.  En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.

3.  En la ventana **Orígenes de datos** , seleccione **Agregar nuevo origen de datos**.

4.  Haga clic en **Objeto** en la página **Elegir un tipo de origen de datos** y después haga clic en **Siguiente**.

5.  Expanda los nodos y, a continuación, busque y seleccione la clase.

    > [!NOTE]
    > Si la clase **Customer** no está disponible, cierre el asistente, compile el proyecto y vuelva a ejecutar el asistente.

6.  Haga clic en **Finalizar** para crear el origen de datos y agregar la clase de entidad **Customer** a la ventana **Orígenes de datos**.

7.  Arrastre los elementos desde la ventana **Orígenes de datos** a un formulario.

## <a name="see-also"></a>Vea también

- [Herramientas LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Tutorial: Crear clases LINQ to SQL (Object Relational Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
- [Métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Cómo: Crear métodos DataContext asignados a funciones y procedimientos almacenados (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Modelo de objetos de LINQ to SQL](http://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810)
- [Tutorial: Personalizar el comportamiento de inserción, actualización y eliminación de clases de entidad](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Tutorial: Agregar validación a clases de entidad](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
- [Cómo: Crear una asociación (relación) entre clases de LINQ to SQL (Object Relational Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)
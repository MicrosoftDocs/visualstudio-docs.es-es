---
title: 'Cómo: crear clases de LINQ to SQL asignadas a tablas y vistas (Object Relational Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7a63e81abcae508487afa40d0778c0f9e9b9caf4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665927"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Cómo: Crear clases de LINQ to SQL asignadas a tablas y vistas (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
LINQ to SQL clases asignadas a tablas y vistas de base de datos se denominan *clases de entidad*. La clase de entidad se asigna a un registro, mientras que las propiedades individuales de una clase de entidad se asignan a las columnas individuales que forman un registro. Cree clases de entidad basadas en tablas o vistas de base de datos arrastrando las tablas o vistas desde **Explorador de servidores** /**Explorador de bases de datos** hasta las [herramientas de LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). El [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] genera las clases y aplica el [! LINQ to SQL atributos para habilitar [! LINQ to SQL funcionalidad (la comunicación de datos y las capacidades de edición de la <xref:System.Data.Linq.DataContext>). Para obtener información detallada acerca de [! LINQ to SQL clases, vea [el modelo de objetos de LINQ to SQL](https://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810).

> [!NOTE]
> El [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] es un asignador relacional de objetos simple porque solo admite relaciones de asignación de 1:1. Es decir, una clase de entidad únicamente puede tener una relación de asignación 1:1 con una tabla o vista de base de datos. No se admiten asignaciones complejas, como la asignación de una clase de entidad a varias tablas. Sin embargo, se puede asignar una clase de entidad a una vista que combina varias tablas relacionadas.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Crear clases de LINQ to SQL asignadas a tablas o vistas de base de datos
 Arrastrar tablas o vistas desde **Explorador de servidores** /**Explorador de bases de datos** hasta el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] crea clases de entidad además de los métodos <xref:System.Data.Linq.DataContext> que se usan para realizar actualizaciones.

 De forma predeterminada, el [! LINQ to SQL Runtime crea una lógica para guardar los cambios de una clase de entidad actualizable en la base de datos. Esta lógica se basa en el esquema de la tabla (las definiciones de columna e información de la clave principal). Si no desea este comportamiento, puede configurar una clase de entidad para que use procedimientos almacenados para realizar inserciones, actualizaciones y eliminaciones en lugar de usar el valor predeterminado [! LINQ to SQL comportamiento en tiempo de ejecución. Para obtener más información, vea [Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)Relational Designer).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Para crear clases de LINQ to SQL asignadas a tablas o vistas de base de datos

1. En **servidor** /**Explorador de bases de datos**, expanda **tablas** o **vistas** y busque la tabla o vista de base de datos que desea usar en la aplicación.

2. Arrastre la tabla o vista hasta el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Se crea una clase de entidad, que aparece en la superficie de diseño. La clase de entidad tiene propiedades que se asignan a las columnas en la tabla o vista seleccionada.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Crear un origen de datos de objeto y mostrar los datos en un formulario
 Después de crear las clases de entidad mediante el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], puede crear un origen de datos de objeto y rellenar la [ventana orígenes de datos](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) con las clases de entidad.

#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Para crear un origen de datos de objeto basándose en las clases de entidad de LINQ to SQL

1. Para compilar el proyecto, en el menú **Compilar**, haga clic en **Compilar solución**.

2. En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.

3. En la ventana **Orígenes de datos** , seleccione **Agregar nuevo origen de datos**.

4. Haga clic en **Objeto** en la página **Elegir un tipo de origen de datos** y después haga clic en **Siguiente**.

5. Expanda los nodos y, a continuación, busque y seleccione la clase.

    > [!NOTE]
    > Si la clase **Customer** no está disponible, cierre el asistente, compile el proyecto y vuelva a ejecutar el asistente.

6. Haga clic en **Finalizar** para crear el origen de datos y agregar la clase de entidad **Customer** a la ventana **Orígenes de datos**.

7. Arrastre los elementos desde la ventana **Orígenes de datos** a un formulario.

## <a name="see-also"></a>Vea también

- [Herramientas LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Tutorial: crear clases de LINQ to SQL (Object Relational Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
- [Métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Cómo: Crear métodos DataContext asignados a funciones y procedimientos almacenados (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Modelo de objetos de LINQ to SQL](https://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810)
- [Tutorial: Personalizar el comportamiento de inserción, actualización y eliminación de las clases de entidad](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Tutorial: agregar validación a clases de entidad](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
- [Cómo: Crear una asociación (relación) entre clases de LINQ to SQL (Object Relational Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)
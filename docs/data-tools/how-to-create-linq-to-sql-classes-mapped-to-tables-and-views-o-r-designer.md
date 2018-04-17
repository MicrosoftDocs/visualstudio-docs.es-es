---
title: 'Cómo: crear LINQ a las clases SQL asignadas a tablas y vistas (Object Relational Designer) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: cc3c70ca70170de630dc28a10ff5d1352a610bfb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Cómo: crear LINQ a las clases SQL asignadas a tablas y vistas (Object Relational Designer)
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] las clases que se asignan a tablas de base de datos y vistas se denominan *las clases de entidad*. La clase de entidad se asigna a un registro, mientras que las propiedades individuales de una clase de entidad se asignan a las columnas individuales que forman un registro. Crear clases de entidad que se basan en tablas de base de datos o vistas arrastrando tablas o vistas desde **Explorador de servidores**/**el Explorador de base de datos** en el [LINQ a las herramientas de SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). El [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] genera las clases y aplica específico del [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] atributos para habilitar [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] funcionalidad (la comunicación de datos y editar las capacidades de la <xref:System.Data.Linq.DataContext>). Para obtener información detallada acerca de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] clases, vea el artículo [el modelo de LINQ to SQL objeto](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).  
  
> [!NOTE]
>  El [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] es un asignador relacional de objetos simple porque admite únicamente relaciones de asignación 1:1. Es decir, una clase de entidad únicamente puede tener una relación de asignación 1:1 con una tabla o vista de base de datos. No se admiten asignaciones complejas, como la asignación de una clase de entidad a varias tablas. Sin embargo, se puede asignar una clase de entidad a una vista que combina varias tablas relacionadas.  
  
## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Crear clases de LINQ to SQL asignadas a tablas o vistas de base de datos  
 Arrastrar tablas o vistas de **Explorador de servidores**/**el Explorador de base de datos** en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] crea las clases de entidad además el <xref:System.Data.Linq.DataContext> métodos que se utilizan para realizar actualizaciones.  
  
 De forma predeterminada, el motor en tiempo de ejecución de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] crea la lógica para volver a guardar en la base de datos los cambios de una clase de entidad actualizable. Esta lógica se basa en el esquema de la tabla (las definiciones de columna e información de la clave principal). Si no desea este comportamiento, puede configurar una clase de entidad para que se usen los procedimientos almacenados para realizar inserciones, actualizaciones y eliminaciones en lugar del comportamiento predeterminado del motor en tiempo de ejecución [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]. Para obtener más información, consulte [Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Para crear clases de LINQ to SQL asignadas a tablas o vistas de base de datos  
  
1.  En **Server**/**el Explorador de base de datos**, expanda **tablas** o **vistas** y busque la tabla de base de datos o vista que desea Para utilizar en la aplicación.  
  
2.  Arrastre la tabla o vista hasta el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Se crea una clase de entidad, que aparece en la superficie de diseño. La clase de entidad tiene propiedades que se asignan a las columnas en la tabla o vista seleccionada.  
  
## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Crear un origen de datos de objeto y mostrar los datos en un formulario  
 Después de crear las clases de entidad mediante el uso de la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], puede crear un origen de datos de objeto y rellenar el [ventana Orígenes de datos](add-new-data-sources.md) con las clases de entidad.  
  
#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Para crear un origen de datos de objeto basándose en las clases de entidad de LINQ to SQL  
  
1.  En el **generar** menú, haga clic en **generar solución** para compilar el proyecto.  
  
2.  En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.  
  
3.  En la ventana **Orígenes de datos** , seleccione **Agregar nuevo origen de datos**.  
  
4.  Haga clic en **objeto** en el **elegir un tipo de origen de datos** página y, a continuación, haga clic en **siguiente**.  
  
5.  Expanda los nodos y, a continuación, busque y seleccione la clase.  
  
    > [!NOTE]
    >  Si el **cliente** clase no está disponible, cancele el asistente, compile el proyecto y vuelva a ejecutar el asistente.  
  
6.  Haga clic en **finalizar** para crear el origen de datos y agregar el **cliente** clase de entidad para el **orígenes de datos** ventana.  
  
7.  Arrastrar elementos desde la **orígenes de datos** ventana a un formulario.  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Tutorial: Crear clases LINQ to SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [Métodos de DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Cómo: crear métodos DataContext asignados a procedimientos almacenados y funciones (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [El modelo de LINQ to SQL objeto](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)   
 [Tutorial: Personalizar la instrucción insert, update y delete de comportamiento de las clases de entidad](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
  [Cómo: crear una asociación (relación) entre clases LINQ to SQL (Object Relational Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)
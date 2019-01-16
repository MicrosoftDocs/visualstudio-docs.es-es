---
title: Procedimiento Crear métodos DataContext asignados a funciones y procedimientos almacenados (Object Relational Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: bda01cec76629bd69d0e3773d99da0b34773f4ff
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868519"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Procedimiento Crear métodos DataContext asignados a funciones y procedimientos almacenados (Object Relational Designer)

Puede agregar procedimientos almacenados y funciones para el **Object Relational Designer** como <xref:System.Data.Linq.DataContext> métodos. Al llamar al método y pasar los parámetros necesarios se ejecuta el procedimiento almacenado o la función en la base de datos y se devuelven los datos en el tipo de valor devuelto del método <xref:System.Data.Linq.DataContext>. Para obtener información detallada sobre <xref:System.Data.Linq.DataContext> métodos, vea [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> También puede usar los procedimientos almacenados para invalidar el valor predeterminado [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] comportamiento en tiempo de ejecución que realiza inserciones, actualizaciones y eliminaciones cuando los cambios se guardan las clases de entidad en una base de datos. Para obtener más información, vea [Cómo: Asignación de procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="create-datacontext-methods"></a>Crear métodos DataContext

Puede crear <xref:System.Data.Linq.DataContext> métodos arrastrando procedimientos almacenan o funciones desde <strong>Explorador de servidores o ** Database Explorer</strong> hasta la **Object Relational Designer**.

> [!NOTE]
> El tipo de valor devuelto de generado <xref:System.Data.Linq.DataContext> método difiere dependiendo de dónde se coloque el procedimiento almacenado o la función en el **Object Relational Designer**. Si se coloca un elemento directamente en una clase de entidad existente, se crea un método de <xref:System.Data.Linq.DataContext> con el tipo de valor devuelto de la clase de entidad. Quitar elementos hasta un área vacía de la **Object Relational Designer** crea un <xref:System.Data.Linq.DataContext> método que devuelve un tipo generado automáticamente. Se puede cambiar el tipo de valor devuelto de un método <xref:System.Data.Linq.DataContext> después de agregarlo al panel **Métodos**. Para examinar o cambiar el tipo de valor devuelto de un método <xref:System.Data.Linq.DataContext>, selecciónelo y fíjese en la propiedad **Tipo devuelto** en la ventana **Propiedades**. Para obtener más información, vea [Cómo: Cambio del tipo de valor devuelto de un método DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Para crear métodos de DataContext que devuelvan tipos generados automáticamente

1.  En **Explorador de servidores** o **Database Explorer**, expanda el **Stored Procedures** nodo de la base de datos con el que está trabajando.

2.  Busque el procedimiento almacenado que desee y arrástrelo hasta un área vacía de la **Object Relational Designer**.

     El método <xref:System.Data.Linq.DataContext> se crea con un tipo de valor devuelto generado automáticamente y aparece en el panel **Métodos**.

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Para crear métodos de DataContext con el tipo de valor devuelto de una clase de entidad

1.  En **Explorador de servidores** o **Database Explorer**, expanda el **Stored Procedures** nodo de la base de datos con el que está trabajando.

2.  Busque el procedimiento almacenado que desee y arrástrelo hasta una clase de entidad existente en el **Object Relational Designer**.

     El método <xref:System.Data.Linq.DataContext> se crea con el tipo de valor devuelto de la clase de entidad seleccionada y aparece en el panel **Métodos**.

> [!NOTE]
> Para obtener información acerca de cómo cambiar el tipo de valor devuelto de existente <xref:System.Data.Linq.DataContext> métodos, vea [Cómo: Cambiar el tipo de valor devuelto de un método DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)
- [DataContext methods (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md) (Métodos DataContext [Object Relational Designer])
- [Tutorial: Creación de LINQ a las clases SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Introducción a LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [LINQ en C#](/dotnet/csharp/linq/linq-in-csharp)
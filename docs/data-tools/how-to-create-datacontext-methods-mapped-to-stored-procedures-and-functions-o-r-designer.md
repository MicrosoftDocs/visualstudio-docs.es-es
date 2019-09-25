---
title: Asignación de métodos de DataContext a procedimientos almacenados y funciones (Object Relational Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4c3769634bfbeb98fcc31e5c074177d950248292
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252904"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Procedimiento Crear métodos DataContext asignados a funciones y procedimientos almacenados (Object Relational Designer)

Puede Agregar procedimientos almacenados y funciones a Object Relational **Designer** como <xref:System.Data.Linq.DataContext> métodos. Al llamar al método y pasar los parámetros necesarios se ejecuta el procedimiento almacenado o la función en la base de datos y se devuelven los datos en el tipo de valor devuelto del método <xref:System.Data.Linq.DataContext>. Para obtener información detallada <xref:System.Data.Linq.DataContext> sobre los métodos, vea [método DataContext (Object](../data-tools/datacontext-methods-o-r-designer.md)Relational Designer).

> [!NOTE]
> También puede utilizar procedimientos almacenados para invalidar el comportamiento [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] predeterminado en tiempo de ejecución que realiza inserciones, actualizaciones y eliminaciones cuando se guardan los cambios de las clases de entidad en una base de datos. Para obtener más información, vea [Cómo: Asignación de procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="create-datacontext-methods"></a>Crear métodos DataContext

Puede crear <xref:System.Data.Linq.DataContext> métodos arrastrando procedimientos almacenados o funciones desde <strong>Explorador de servidores o * * explorador de bases de datos</strong> a Object Relational **Designer**.

> [!NOTE]
> El tipo de valor devuelto <xref:System.Data.Linq.DataContext> del método generado varía en función de dónde se coloque el procedimiento almacenado o la función en Object Relational **Designer**. Si se coloca un elemento directamente en una clase de entidad existente, se crea un método de <xref:System.Data.Linq.DataContext> con el tipo de valor devuelto de la clase de entidad. Al colocar elementos en un área vacía de **Object** Relational Designer, <xref:System.Data.Linq.DataContext> se crea un método que devuelve un tipo generado automáticamente. Se puede cambiar el tipo de valor devuelto de un método <xref:System.Data.Linq.DataContext> después de agregarlo al panel **Métodos**. Para examinar o cambiar el tipo de valor devuelto de un método <xref:System.Data.Linq.DataContext>, selecciónelo y fíjese en la propiedad **Tipo devuelto** en la ventana **Propiedades**. Para obtener más información, vea [Cómo: Cambio del tipo de valor devuelto de un método DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Para crear métodos de DataContext que devuelvan tipos generados automáticamente

1. En **Explorador de servidores** o **Explorador de bases de datos**, expanda el nodo **procedimientos almacenados** de la base de datos con la que está trabajando.

2. Busque el procedimiento almacenado deseado y arrástrelo hasta un área vacía de Object Relational **Designer**.

     El método <xref:System.Data.Linq.DataContext> se crea con un tipo de valor devuelto generado automáticamente y aparece en el panel **Métodos**.

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Para crear métodos de DataContext con el tipo de valor devuelto de una clase de entidad

1. En **Explorador de servidores** o **Explorador de bases de datos**, expanda el nodo **procedimientos almacenados** de la base de datos con la que está trabajando.

2. Busque el procedimiento almacenado deseado y arrástrelo hasta una clase de entidad existente en Object Relational **Designer**.

     El método <xref:System.Data.Linq.DataContext> se crea con el tipo de valor devuelto de la clase de entidad seleccionada y aparece en el panel **Métodos**.

> [!NOTE]
> Para obtener información acerca de cómo cambiar el tipo <xref:System.Data.Linq.DataContext> de valor devuelto de los métodos existentes, consulte [How to: Cambio del tipo de valor devuelto de un método DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)
- [DataContext methods (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md) (Métodos DataContext [Object Relational Designer])
- [Tutorial: Crear clases de LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Introducción a LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [LINQ en C#](/dotnet/csharp/linq/linq-in-csharp)

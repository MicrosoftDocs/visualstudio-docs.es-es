---
title: 'Cómo: crear métodos DataContext asignados a procedimientos almacenados y funciones (Object Relational Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 53829ffaeab44eb758b1850f5619de43db31e589
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089690"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Cómo: crear métodos DataContext asignados a procedimientos almacenados y funciones (Object Relational Designer)
Puede agregar procedimientos almacenados y funciones para el **Object Relational Designer** como <xref:System.Data.Linq.DataContext> métodos. Una llamada al método y pasar los parámetros necesarios se ejecuta el procedimiento almacenado o función en la base de datos y devuelve los datos en el tipo de valor devuelto de la <xref:System.Data.Linq.DataContext> método. Para obtener información detallada sobre <xref:System.Data.Linq.DataContext> métodos, vea [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
>  También puede usar los procedimientos almacenados para invalidar el valor predeterminado [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] comportamiento en tiempo de ejecución que realiza inserciones, actualizaciones y eliminaciones cuando los cambios se guardan las clases de entidad en una base de datos. Para obtener más información, consulte [Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="create-datacontext-methods"></a>Crear métodos DataContext
 Puede crear <xref:System.Data.Linq.DataContext> métodos arrastrando procedimientos almacenan o funciones de ** explorador de servidores o **Database Explorer** hasta la **Object Relational Designer**.

> [!NOTE]
>  El tipo de valor devuelto de generado <xref:System.Data.Linq.DataContext> método difiere dependiendo de dónde se coloque el procedimiento almacenado o la función en el **Object Relational Designer**. Si se coloca un elemento directamente en una clase de entidad existente, se crea un método de <xref:System.Data.Linq.DataContext> con el tipo de valor devuelto de la clase de entidad. Quitar elementos hasta un área vacía de la **Object Relational Designer** crea un <xref:System.Data.Linq.DataContext> método que devuelve un tipo generado automáticamente. Puede cambiar el tipo de valor devuelto de un <xref:System.Data.Linq.DataContext> método después de agregarlo a la **métodos** panel. Para examinar o cambiar el tipo de valor devuelto de un <xref:System.Data.Linq.DataContext> método, selecciónelo y fíjese la **Return Type** propiedad en el **propiedades** ventana. Para obtener más información, consulte [Cómo: cambiar el tipo de valor devuelto de un método DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Para crear métodos de DataContext que devuelvan tipos generados automáticamente

1.  En **Explorador de servidores** o **Database Explorer**, expanda el **Stored Procedures** nodo de la base de datos con el que está trabajando.

2.  Busque el procedimiento almacenado que desee y arrástrelo hasta un área vacía de la **Object Relational Designer**.

     El <xref:System.Data.Linq.DataContext> método se crea con un tipo de valor devuelto generado automáticamente y aparece en el **métodos** panel.

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Para crear métodos de DataContext con el tipo de valor devuelto de una clase de entidad

1.  En **Explorador de servidores** o **Database Explorer**, expanda el **Stored Procedures** nodo de la base de datos con el que está trabajando.

2.  Busque el procedimiento almacenado que desee y arrástrelo hasta una clase de entidad existente en el **Object Relational Designer**.

     El <xref:System.Data.Linq.DataContext> método se crea con el tipo de valor devuelto de la clase de entidad seleccionada y aparece en el **métodos** panel.

> [!NOTE]
>  Para obtener información acerca de cómo cambiar el tipo de valor devuelto de existente <xref:System.Data.Linq.DataContext> métodos, vea [Cómo: cambiar el tipo de valor devuelto de un método DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Tutorial: Creación de LINQ a las clases SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Introducción a LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [LINQ en C#](/dotnet/csharp/linq/linq-in-csharp)
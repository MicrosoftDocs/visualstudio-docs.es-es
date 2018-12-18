---
title: 'Cómo: cambiar el tipo de valor devuelto de un método DataContext (Object Relational Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5c67d6dea4c64e858acdab25ecc4a6cede6bf262
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089362"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Cómo: cambiar el tipo de valor devuelto de un método DataContext (Object Relational Designer)
El tipo de valor devuelto de un <xref:System.Data.Linq.DataContext> método (creado a partir de un procedimiento almacenado o función) difiere dependiendo de dónde se coloque el procedimiento almacenado o la función en el **Object Relational Designer**. Si se coloca un elemento directamente en una clase de entidad existente, se crea un método de <xref:System.Data.Linq.DataContext> que tiene el tipo de valor devuelto de la clase de entidad (si el esquema de los datos devueltos por el procedimiento almacenado o la función coincide con la forma de la clase de entidad). Si coloca un elemento en un área vacía de la **Object Relational Designer**, un <xref:System.Data.Linq.DataContext> se crea el método que devuelve un tipo generado automáticamente. Se puede cambiar el tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> después de agregarlo al panel de métodos. Para examinar o cambiar el tipo de valor devuelto de un <xref:System.Data.Linq.DataContext> método, selecciónelo y haga clic en el **Return Type** propiedad en el **propiedades** ventana.

> [!NOTE]
>  No se puede revertir <xref:System.Data.Linq.DataContext> los métodos que tienen un tipo de valor devuelto se establece en una clase de entidad para devolver el tipo generado automáticamente mediante el **propiedades** ventana. Para revertir un <xref:System.Data.Linq.DataContext> método devuelva un tipo generado automáticamente, debe arrastrar el objeto de base de datos original en el **Object Relational Designer** nuevo.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Para cambiar el tipo de valor devuelto de un método de DataContext del tipo generado automáticamente a una clase de entidad

1.  Seleccione el método de <xref:System.Data.Linq.DataContext> en el panel de métodos.

2.  Seleccione **Return Type** en el **propiedades** clase de ventana y, a continuación, seleccione una entidad disponible en el **Return Type** lista. Si la clase de entidad deseada no está en la lista, agréguelo a o créela en el **Object Relational Designer** para agregarlo a la lista.

3.  Guardar el *.dbml* archivo.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Para volver a cambiar el tipo de valor devuelto de un método de DataContext de una clase de entidad al tipo generado automáticamente

1.  Seleccione el <xref:System.Data.Linq.DataContext> método en el **métodos** panel y elimínelo.

2.  Arrastre el objeto de base de datos desde **Explorador de servidores** o **Database Explorer** en un área vacía de la **Object Relational Designer**.

3.  Guardar el *.dbml* archivo.

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Cómo: crear métodos DataContext asignados a procedimientos almacenados y funciones (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
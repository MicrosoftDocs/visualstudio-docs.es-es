---
title: Cambiar el tipo de valor devuelto del método DataContext
description: Saber cómo cambiar el tipo de valor devuelto de un método DataContext cuando se coloca un procedimiento almacenado o una función en el Object Relational Designer (Object Relational Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 4226be60f91fb1b9d55e279be2a697861c3f9566
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858805"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Procedimiento para cambiar el tipo de valor devuelto de un método DataContext (Object Relational Designer)
El tipo de valor devuelto de un <xref:System.Data.Linq.DataContext> método (creado basándose en un procedimiento almacenado o una función) difiere en función de dónde se coloque el procedimiento almacenado o la función en Object Relational **Designer**. Si se coloca un elemento directamente en una clase de entidad existente, se crea un método de <xref:System.Data.Linq.DataContext> que tiene el tipo de valor devuelto de la clase de entidad (si el esquema de los datos devueltos por el procedimiento almacenado o la función coincide con la forma de la clase de entidad). Si coloca un elemento en un área vacía de Object Relational **Designer**, <xref:System.Data.Linq.DataContext> se crea un método que devuelve un tipo generado automáticamente. Se puede cambiar el tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> después de agregarlo al panel de métodos. Para examinar o cambiar el tipo de valor devuelto de un método <xref:System.Data.Linq.DataContext>, selecciónelo y haga clic en la propiedad **Tipo devuelto** en la ventana **Propiedades**.

> [!NOTE]
> Mediante la ventana **Propiedades**, no se pueden revertir los métodos de <xref:System.Data.Linq.DataContext> cuyo tipo de valor devuelto está establecido en una clase de entidad para que devuelvan el tipo generado automáticamente. Para revertir un <xref:System.Data.Linq.DataContext> método para que devuelva un tipo generado automáticamente, debe arrastrar de nuevo el objeto original de la base de datos al Object Relational **Designer** .

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Para cambiar el tipo de valor devuelto de un método de DataContext del tipo generado automáticamente a una clase de entidad

1. Seleccione el método de <xref:System.Data.Linq.DataContext> en el panel de métodos.

2. Seleccione **Tipo devuelto** en la ventana **Propiedades** y después seleccione una clase de entidad disponible en la lista **Tipo devuelto**. Si la clase de entidad deseada no está en la lista, agréguela a o créela en Object Relational **Designer** para agregarla a la lista.

3. Guarde el archivo *.dbml*.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Para volver a cambiar el tipo de valor devuelto de un método de DataContext de una clase de entidad al tipo generado automáticamente

1. Seleccione el <xref:System.Data.Linq.DataContext> método en el panel **métodos** y elimínelo.

2. Arrastre el objeto Database desde **Explorador de servidores** o **Explorador de bases de datos** a un área vacía de Object Relational **Designer**.

3. Guarde el archivo *.dbml*.

## <a name="see-also"></a>Vea también

- [Herramientas de LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext (métodos) (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Cómo: Crear métodos DataContext asignados a funciones y procedimientos almacenados (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)

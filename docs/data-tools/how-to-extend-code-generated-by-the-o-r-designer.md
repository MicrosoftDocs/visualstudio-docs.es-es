---
title: Procedimiento Ampliar el código generado por Object Relational Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 41704ad1f43dadee1efd16102281173215bad4e0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53933789"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Procedimiento Ampliar el código generado por Object Relational Designer
Código generado por el **Object Relational Designer** se vuelve a generar cuando se realizan cambios en las clases de entidad y otros objetos en la superficie del diseñador. Debido a esta regeneración del código, cualquier código que se agregue al código generado se suele sobrescribir cuando el diseñador vuelve a generar el código. El **Object Relational Designer** proporciona la capacidad de generar archivos de clase parcial en la que puede agregar código que no se sobrescribe. Un ejemplo de cómo agregar su propio código para el código generado por el **Object Relational Designer** es agregar la validación de datos a LINQ a las clases SQL (entity). Para obtener más información, vea [Cómo: Agregar validación a clases de entidad](../data-tools/how-to-add-validation-to-entity-classes.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>Agregar código a una clase de entidad

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Para crear una clase parcial y agregar código a una clase de entidad

1.  Abra o cree un nuevo archivo LINQ to SQL Classes (**.dbml** archivo) en el **Object Relational Designer**. (Haga doble clic en el **.dbml** archivo **el Explorador de soluciones** o **Database Explorer**.)

2.  En **Object Relational Designer**, haga clic con el botón derecho del mouse en la clase para la que desee agregar validación y, a continuación, haga clic en **Ver código**.

     El Editor de código se abre con una clase parcial para la clase de entidad seleccionada.

3.  Agregue código a la declaración de clase parcial para la clase de entidad.

## <a name="add-code-to-a-datacontext"></a>Agregue código a una clase DataContext

### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Para crear una clase parcial y agregar código a una clase DataContext

1.  Abra o cree un nuevo archivo LINQ to SQL Classes (**.dbml** archivo) en el **Object Relational Designer**. (Haga doble clic en el **.dbml** archivo **el Explorador de soluciones** o **Database Explorer**.)

2.  En el **Object Relational Designer**, haga clic en un área vacía en el diseñador y, a continuación, haga clic en **ver código**.

     El Editor de código se abre con una clase parcial de DataContext.

3.  Agregue código a la declaración de clase parcial para DataContext.

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)
- [Tutorial: Creación de LINQ a las clases SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
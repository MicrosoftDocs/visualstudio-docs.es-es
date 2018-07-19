---
title: 'Cómo: ampliar código generado por el Object Relational Designer'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9da4dca31043104c58122c2eed7aa55ae44ef07e
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089794"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Cómo: ampliar código generado por el Object Relational Designer
Código generado por el **Object Relational Designer** se vuelve a generar cuando se realizan cambios en las clases de entidad y otros objetos en la superficie del diseñador. Debido a esta regeneración del código, cualquier código que se agregue al código generado se suele sobrescribir cuando el diseñador vuelve a generar el código. El **Object Relational Designer** proporciona la capacidad de generar archivos de clase parcial en la que puede agregar código que no se sobrescribe. Un ejemplo de cómo agregar su propio código para el código generado por el **Object Relational Designer** es agregar la validación de datos a LINQ a las clases SQL (entity). Para obtener más información, consulte [Cómo: agregar validación a clases de entidad](../data-tools/how-to-add-validation-to-entity-classes.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>Agregar código a una clase de entidad

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Para crear una clase parcial y agregar código a una clase de entidad

1.  Abra o cree un nuevo archivo LINQ to SQL Classes (**.dbml** archivo) en el **Object Relational Designer**. (Haga doble clic en el **.dbml** archivo **el Explorador de soluciones** o **Database Explorer**.)

2.  En el **Object Relational Designer**, haga clic en la clase para el que desea agregar la validación y, a continuación, haga clic en **ver código**.

     El Editor de código se abre con una clase parcial para la clase de entidad seleccionada.

3.  Agregue código a la declaración de clase parcial para la clase de entidad.

## <a name="add-code-to-a-datacontext"></a>Agregue código a una clase DataContext

### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Para crear una clase parcial y agregar código a una clase DataContext

1.  Abra o cree un nuevo archivo LINQ to SQL Classes (**.dbml** archivo) en el **Object Relational Designer**. (Haga doble clic en el **.dbml** archivo **el Explorador de soluciones** o **Database Explorer**.)

2.  En el **Object Relational Designer**, haga clic en un área vacía en el diseñador y, a continuación, haga clic en **ver código**.

     El Editor de código se abre con una clase parcial de DataContext.

3.  Agregue código a la declaración de clase parcial para DataContext.

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Tutorial: Creación de LINQ a las clases SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
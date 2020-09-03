---
title: Procedimiento para ampliar el código generado con O-R Designer
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b4c0ac8cff82250169171e1d842e64a34a4523ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282116"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Procedimiento para ampliar el código generado con Object Relational Designer
El código generado por **Object** Relational Designer se vuelve a generar cuando se realizan cambios en las clases de entidad y otros objetos en la superficie del diseñador. Debido a esta regeneración del código, cualquier código que se agregue al código generado se suele sobrescribir cuando el diseñador vuelve a generar el código. Object Relational **Designer** proporciona la capacidad de generar archivos de clase parcial en los que se puede agregar código que no se sobrescribe. Un ejemplo de cómo agregar su propio código al código generado por Object Relational **Designer** es agregar la validación de datos a clases LINQ to SQL (entidad). Para obtener más información, consulte [Cómo: agregar validación a clases de entidad](../data-tools/how-to-add-validation-to-entity-classes.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>Agregar código a una clase de entidad

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Para crear una clase parcial y agregar código a una clase de entidad

1. Abra o cree un nuevo archivo de clases de LINQ to SQL (archivo **. dbml** ) en Object Relational **Designer**. (Haga doble clic en el archivo **. dbml** en **Explorador de soluciones** o **Explorador de bases de datos**).

2. En **Object Relational Designer**, haga clic con el botón derecho del mouse en la clase para la que desee agregar validación y, a continuación, haga clic en **Ver código**.

     El Editor de código se abre con una clase parcial para la clase de entidad seleccionada.

3. Agregue código a la declaración de clase parcial para la clase de entidad.

## <a name="add-code-to-a-datacontext"></a>Agregar código a un DataContext

### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Para crear una clase parcial y agregar código a una clase DataContext

1. Abra o cree un nuevo archivo de clases de LINQ to SQL (archivo **. dbml** ) en Object Relational **Designer**. (Haga doble clic en el archivo **. dbml** en **Explorador de soluciones** o **Explorador de bases de datos**).

2. En Object Relational **Designer**, haga clic con el botón secundario en un área vacía del diseñador y, a continuación, haga clic en **Ver código**.

     El Editor de código se abre con una clase parcial de DataContext.

3. Agregue código a la declaración de clase parcial para DataContext.

## <a name="see-also"></a>Vea también

- [Herramientas de LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Walkthrough: Creating LINQ to SQL classes (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md) (Tutorial: Crear clases de LINQ to SQL [Object Relational Designer])
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)

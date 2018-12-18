---
title: 'Cómo: configurar la herencia utilizando el Object Relational Designer'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: bb0be89627f5e7e95d7d45ebfb938bca3e4a982b
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089269"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Cómo: configurar la herencia mediante Object Relational Designer
El **Object Relational Designer** (**Object Relational Designer**) admite el concepto de herencia de tabla única normalmente implementada en los sistemas relacionales. En la herencia de tabla única, hay una sola tabla de base de datos que contiene campos tanto para la información de elementos primarios como para la información de elementos secundarios. En el caso de datos relacionales, una columna discriminadora contiene el valor que determina la clase a la que pertenece un registro cualquiera.

Por ejemplo, considere un `Persons` tabla que contiene todos los usuarios trabajan en una compañía. Algunas personas son los empleados y otras son los directores. El `Persons` tabla contiene una columna denominada `EmployeeType` que tiene un valor de 1 para directores y el valor de 2 para empleados; ésta es la columna discriminadora. En este escenario, puede crear una subclase de empleados y rellenar la clase únicamente con los registros cuyo `EmployeeType` tiene el valor 2. Puede eliminar también columnas que no se aplican desde cada una de las clases.

La creación de un modelo de objetos que use la herencia (y que corresponda a datos relacionales) puede resultar un poco confusa. El procedimiento siguiente describe los pasos necesarios para configurar la herencia con la **Object Relational Designer**. Estos pasos genéricos sin hacer referencia a una tabla existente y de columnas pueden resultar difícil, por lo que se proporciona un tutorial que utiliza los datos. Para obtener instrucciones paso a paso para configurar la herencia mediante el uso de la **Object Relational Designer**, consulte [Tutorial: creación de LINQ to SQL clases mediante la herencia de tabla única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

## <a name="to-create-inherited-data-classes"></a>Para crear clases de datos heredadas

1.  Abra el **Object Relational Designer** agregando un **clases LINQ to SQL** elemento a un proyecto existente de Visual Basic o C#.

2.  Arrastre la tabla que desea utilizar como clase base hasta el **Object Relational Designer**.

3.  Arrastre una segunda copia de la tabla hasta la **Object Relational Designer** y cambie su nombre. Ésta es la clase derivada o subclase.

4.  Haga clic en **herencia** en el **Object Relational Designer** pestaña de la **cuadro de herramientas**y, a continuación, haga clic en la subclase (la tabla ha cambiado el nombre) y conectarlo a la clase base.

    > [!NOTE]
    >  Haga clic en el **herencia** de elemento en el **cuadro de herramientas** y suelte el botón del mouse, haga clic en la segunda copia de la clase que creó en el paso 3 y, a continuación, haga clic en la primera clase que creó en el paso 2. La flecha situada en la línea de herencia apunta a la primera clase.

5.  En cada clase, elimine las propiedades de objeto que no desee que aparezcan y que no se utilicen para asociaciones. Recibe un error si intenta eliminar las propiedades del objeto utilizadas para las asociaciones: [la propiedad \<nombre de propiedad > no se puede eliminar porque participa en la asociación \<nombre de asociación >](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    >  Dado que una clase derivada hereda las propiedades definidas en su clase base, no se pueden definir las mismas columnas en cada clase. (Las columnas se implementan como propiedades.) Puede habilitar la creación de columnas de la clase derivada estableciendo el modificador de herencia de la propiedad en la clase base. Para obtener más información, consulte [Fundamentos de la herencia (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics).

6.  Seleccione la línea de herencia en el **Object Relational Designer**.

7.  En el **propiedades** ventana, establezca el **propiedad Discriminator** al nombre de columna que distingue los registros en las clases.

8.  Establecer el **Derived Class Discriminator Value** propiedad al valor de la base de datos que designa el registro como tipo heredado. (Esto es el valor que se almacena en la columna discriminadora y que se usa para designar la clase heredada).

9. Establecer el **Base Class Discriminator Value** en el valor que designa el registro como tipo base. (Esto es el valor que se almacena en la columna discriminadora y que se usa para designar la clase base).

10. Si lo desea, también puede establecer el **predeterminado de herencia** propiedad para designar un tipo en una jerarquía de herencia que se usa al cargar las filas que no coinciden con cualquier código de herencia definido. En otras palabras, si un registro tiene un valor en su columna discriminadora que no coincide con el valor de la **Derived Class Discriminator Value** o **Base Class Discriminator Value** propiedades, el registro carga en el tipo designado como el **predeterminado de herencia**.

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Tutorial: Creación de LINQ a las clases SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Tutorial: Creación de LINQ a las clases SQL mediante la herencia de tabla única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Fundamentos de la herencia (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Herencia](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
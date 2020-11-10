---
title: Configurar la herencia mediante Object Relational Designer
description: Obtenga información sobre cómo configurar la herencia mediante el Object Relational Designer (Object Relational Designer), que admite la herencia de tabla única. Clases de datos heredadas creadas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4bc36bca3cc5bd13b3dcfad5ebed66eca7eeb019
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436338"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Procedimiento para configurar la herencia mediante Object Relational Designer
El **Object Relational Designer** ( **Object** Relational Designer) admite el concepto de herencia de tabla única, ya que se suele implementar en sistemas relacionales. En la herencia de tabla única, hay una sola tabla de base de datos que contiene campos tanto para la información de elementos primarios como para la información de elementos secundarios. En el caso de datos relacionales, una columna discriminadora contiene el valor que determina la clase a la que pertenece un registro cualquiera.

Por ejemplo, considere una `Persons` tabla que contiene todos los empleados de una empresa. Algunas personas son los empleados y otras son los directores. La `Persons` tabla contiene una columna denominada `EmployeeType` que tiene un valor de 1 para los administradores y un valor de 2 para los empleados; esta es la columna discriminadora. En este escenario, puede crear una subclase de empleados y rellenar la clase únicamente con los registros cuyo `EmployeeType` tiene el valor 2. Puede eliminar también columnas que no se aplican desde cada una de las clases.

La creación de un modelo de objetos que use la herencia (y que corresponda a datos relacionales) puede resultar un poco confusa. En el procedimiento siguiente se describen los pasos necesarios para configurar la herencia con **Object** Relational Designer. Los siguientes pasos genéricos sin hacer referencia a una tabla y columnas existentes pueden resultar difíciles, por lo que se proporciona un tutorial que usa datos. Para obtener instrucciones paso a paso para configurar la herencia mediante el uso de la **Object Relational Designer** , consulte [Tutorial: creación de LINQ to SQL clases mediante la herencia de tabla única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

## <a name="to-create-inherited-data-classes"></a>Para crear clases de datos heredadas

1. Abra **o/R Designer** agregando un elemento de **clases de LINQ to SQL** a un proyecto de Visual Basic o C# existente.

2. Arrastre la tabla que desea usar como clase base a Object Relational **Designer**.

3. Arrastre una segunda copia de la tabla hasta Object Relational **Designer** y cambie su nombre. Ésta es la clase derivada o subclase.

4. Haga clic en **Herencia** en la pestaña **Object Relational Designer** del **Cuadro de herramientas** y, a continuación, haga clic en la subclase (la tabla cuyo nombre ha cambiado) y conéctela a la clase base.

    > [!NOTE]
    > Haga clic en el elemento **Herencia** del **Cuadro de herramientas** y suelte el botón del mouse, haga clic en la segunda copia de la clase creada en el paso 3 y haga clic en la primera clase creada en el paso 2. La flecha en la línea de herencia apunta a la primera clase.

5. En cada clase, elimine las propiedades de objeto que no desee que aparezcan y que no se utilicen para asociaciones. Recibirá un error si intenta eliminar las propiedades de objeto utilizadas para las asociaciones: [ \<property name> no se puede eliminar la propiedad porque participa en la Asociación \<association name> ](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    > Dado que una clase derivada hereda las propiedades definidas en su clase base, no se pueden definir las mismas columnas en cada clase. (Las columnas se implementan como propiedades). Puede habilitar la creación de columnas en la clase derivada estableciendo el modificador de herencia en la propiedad de la clase base. Para obtener más información, vea [conceptos básicos de herencia (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics).

6. Seleccione la línea de herencia en el Object Relational **Designer**.

7. En la ventana **propiedades** , establezca la **propiedad Discriminator** en el nombre de columna que distingue los registros de las clases.

8. Establezca la propiedad **Valor de discriminador de clase derivada** en el valor de la base de datos que designa el registro como tipo heredado. (Este es el valor que se almacena en la columna discriminadora y se usa para designar la clase heredada).

9. Establezca la propiedad **Valor de discriminador de clase base** en el valor que designa el registro como tipo base. (Este es el valor que se almacena en la columna discriminadora y se usa para designar la clase base).

10. De manera opcional, también puede establecer la propiedad **Predeterminado de herencia** para designar un tipo en una jerarquía de herencia que se va a usar cuando se carguen filas que no coinciden con ningún código de herencia definido. En otras palabras, si un registro tiene un valor en su columna discriminadora que no coincide con el valor de las propiedades valor de **discriminador de clase derivada** o **valor de discriminador de clase base** , el registro se carga en el tipo designado como **predeterminado de herencia**.

## <a name="see-also"></a>Consulte también

- [Herramientas de LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Walkthrough: Creating LINQ to SQL classes (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md) (Tutorial: Crear clases de LINQ to SQL [Object Relational Designer])
- [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Tutorial: crear clases de LINQ to SQL mediante la herencia de tabla única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Conceptos básicos de la herencia (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Herencia](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)

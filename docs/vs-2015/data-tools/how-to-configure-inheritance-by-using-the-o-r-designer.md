---
title: 'Cómo: configurar la herencia mediante Object Relational Designer | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f8c08546fdf96c755b3adb80021ab7269509739
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654704"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Procedimiento para configurar la herencia mediante Object Relational Designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) admite el concepto de la herencia de tabla única normalmente implementada en los sistemas relacionales. En la herencia de tabla única, hay una sola tabla de base de datos que contiene campos tanto para la información de elementos primarios como para la información de elementos secundarios. En el caso de datos relacionales, una columna discriminadora contiene el valor que determina la clase a la que pertenece un registro cualquiera.

 Por ejemplo, consideremos una tabla Persons que contiene todas las personas que trabajan en una compañía. Algunas personas son los empleados y otras son los directores. La tabla Persons contiene una columna denominada `EmployeeType` que tiene el valor 1 para los directores y el valor 2 para los empleados; ésta es la columna discriminadora. En este escenario, puede crear una subclase de empleados y rellenar la clase únicamente con los registros cuyo `EmployeeType` tiene el valor 2. Puede eliminar también columnas que no se aplican desde cada una de las clases.

 La creación de un modelo de objetos que use la herencia (y que corresponda a datos relacionales) puede resultar un poco confusa. En el procedimiento siguiente se describen los pasos necesarios para configurar la herencia con Object Relational Designer. Puede resultar difícil seguir estos pasos genéricos sin hacer referencia a una tabla y columnas ya existentes, por lo que se ha proporcionado un tutorial con datos. Para obtener instrucciones detalladas paso a paso para configurar la herencia mediante el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , vea [Tutorial: crear LINQ to SQL clases mediante la herencia de tabla única (o/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

### <a name="to-create-inherited-data-classes"></a>Para crear clases de datos heredadas

1. Abra el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] agregando un elemento de **clases LINQ to SQL** a un proyecto de Visual Basic o C# existente.

2. Arrastre la tabla que desee usar como clase base hasta el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

3. Arrastre una segunda copia de la tabla hasta el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] y cambie su nombre. Ésta es la clase derivada o subclase.

4. Haga clic en **Herencia** en la pestaña **Object Relational Designer** del **Cuadro de herramientas** y, a continuación, haga clic en la subclase (la tabla cuyo nombre ha cambiado) y conéctela a la clase base.

    > [!NOTE]
    > Haga clic en el elemento **Herencia** del **Cuadro de herramientas** y suelte el botón del mouse, haga clic en la segunda copia de la clase creada en el paso 3 y haga clic en la primera clase creada en el paso 2. La flecha en la línea de herencia apuntará a la primera clase.

5. En cada clase, elimine las propiedades de objeto que no desee que aparezcan y que no se utilicen para asociaciones. Recibirá un error si intenta eliminar las propiedades de objeto utilizadas para las asociaciones: [no se \<property name> puede eliminar la propiedad porque participa en la Asociación \<association name> ](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    > Dado que una clase derivada hereda las propiedades definidas en su clase base, no se pueden definir las mismas columnas en cada clase. (Las columnas se implementan como propiedades). Puede habilitar la creación de columnas en la clase derivada estableciendo el modificador de herencia en la propiedad de la clase base. Para obtener más información, vea [no está en la compilación: invalidar propiedades y métodos](https://msdn.microsoft.com/2167e8f5-1225-4b13-9ebd-02591ba90213).

6. Seleccione la línea de herencia en el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

7. En la ventana **propiedades** , establezca la **propiedad Discriminator** en el nombre de columna que se usa para distinguir los registros de las clases.

8. Establezca la propiedad **Valor de discriminador de clase derivada** en el valor de la base de datos que designa el registro como tipo heredado. (Éste es el valor que está almacenado en la columna discriminadora y que se usa para designar la clase heredada).

9. Establezca la propiedad **Valor de discriminador de clase base** en el valor que designa el registro como tipo base. (Éste es el valor que está almacenado en la columna discriminadora y que se usa para designar la clase base).

10. De manera opcional, también puede establecer la propiedad **Predeterminado de herencia** para designar un tipo en una jerarquía de herencia que se va a usar cuando se carguen filas que no coinciden con ningún código de herencia definido. En otras palabras, si un registro tiene un valor en su columna discriminadora que no coincide con el valor de las propiedades valor de **discriminador de clase derivada** o **valor de discriminador de clase base** , el registro se cargará en el tipo designado como **predeterminado de herencia**.

## <a name="see-also"></a>Consulte también
 [LINQ to SQL herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [Tutorial: crear clases de LINQ to SQL (Object Relational Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [desarrollar novedades para el desarrollo de aplicaciones de datos en Visual Studio 2012](https://msdn.microsoft.com/3d50d68f-5f44-4915-842f-6d42fce793f1) [acceder a los datos en visual studio](../data-tools/accessing-data-in-visual-studio.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [Tutorial: crear clases de LINQ to SQL con la herencia de tabla única (o/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) [no está en la compilación: herencia en Visual Basic](https://msdn.microsoft.com/e5e6e240-ed31-4657-820c-079b7c79313c) [herencia](https://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)

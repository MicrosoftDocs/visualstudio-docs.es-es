---
title: Procedimiento Crear un tipo que acepta valores NULL en el Diseñador de clases
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5be8b553dfead4b8c05f29bbd18c16fcef847130
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592235"
---
# <a name="how-to-create-a-nullable-type-in-class-designer"></a>Procedimiento Crear un tipo que acepta valores NULL en el Diseñador de clases

Determinados tipos de valor no siempre tienen (o necesitan) un valor definido. Esto es habitual en las bases de datos, donde es posible que algunos campos no tengan asignado ningún valor. Por ejemplo, se podría asignar un valor nulo a un campo de base de datos para indicar que aún no se le ha asignado ningún valor.

Un *tipo que acepta valores NULL* es un tipo de valor que se amplía para que acepte el intervalo normal de valores para ese tipo y además un valor nulo. Por ejemplo, a un valor NULL de `Int32`, también conocido como Nullable\<Int32>, se le puede asignar cualquier valor comprendido entre -2147483648 y 2147483647, o se le puede asignar un valor nulo. A un valor Nullable\<bool> se le pueden asignar los valores `True`, `False` o nulo (ningún valor).

Los tipos que aceptan valores NULL son instancias de la estructura <xref:System.Nullable%601>. Cada instancia de un tipo que acepta valores NULL tiene dos propiedades públicas de solo lectura, `HasValue` y `Value`:

- `HasValue` es de tipo `bool` e indica si la variable contiene un valor definido. `True` significa que la variable contiene un valor que no es nulo. Puede probar un valor definido mediante una instrucción como `if (x.HasValue)` o `if (y != null)`.

- `Value` es del mismo tipo que el tipo subyacente. Si `HasValue` es `True`, `Value` contiene un valor significativo. Si `HasValue` es `False`, al acceder a `Value` se producirá una excepción de operación no válida.

De forma predeterminada, cuando se declara una variable como un tipo que acepta valores NULL, no tiene ningún valor definido (`HasValue` es `False`) más que el valor predeterminado de su tipo de valor subyacente.

El Diseñador de clases muestra un tipo que acepta valores NULL al igual que muestra su tipo subyacente.

Para más información sobre los tipos que aceptan valores NULL en C#, vea [Tipos que aceptan valores NULL](/dotnet/csharp/programming-guide/nullable-types/index). Para más información sobre los tipos que aceptan valores NULL en Visual Basic, vea [Tipos que admiten valores null](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types).

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>Para agregar un tipo que acepta valores NULL mediante el Diseñador de clases

1. En el diagrama de clases, expanda una clase existente o cree una nueva.

2. Para agregar una clase al proyecto, en el menú **Diagrama de clases**, haga clic en **Agregar** > **Agregar clase**.

3. Para expandir la forma de clase, en el menú **Diagrama de clases**, haga clic en **Expandir**.

4. Seleccione la forma de clase. En el menú **Diagrama de clases**, haga clic en **Agregar** > **Campo**. Un nuevo campo con el nombre predeterminado **Campo** aparecerá en la forma de clase y también en la ventana **Detalles de clase**.

5. En la columna **Nombre** de la ventana **Detalles de clase** (o en la propia forma de clase), cambie el nombre del nuevo campo por un nombre válido y significativo.

6. En la columna **Tipo** de la ventana **Detalles de clase**, declare el tipo como un tipo que acepta valores NULL al especificar lo siguiente:

    - `int?` (Visual C#)
    - `Nullable(Of Integer)` (Visual Basic)

## <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>Para agregar un tipo que acepta valores NULL mediante el Editor de código

1. Agregue una clase al proyecto. Seleccione el nodo de proyecto en el **Explorador de soluciones** y, en el menú **Proyecto**, haga clic en **Agregar clase**.

2. En el archivo .cs o .vb de la nueva clase, agregue uno o más tipos que aceptan valores NULL en la nueva clase para la declaración de clase.

    ```csharp
    // Declare a nullable type in Visual C#:
    class Test
    {
       int? building_number = 5;
    }
    ```

    ```vb
    ' Declare a nullable type in Visual Basic:
    Class Test
       Dim buildingNumber As Nullable(Of Integer) = 5
    End Class
    ```

3. En Vista de clases, arrastre el icono de la nueva clase a la superficie de diseño Diseñador de clases. Aparece una forma de clase en el diagrama de clases.

4. Expanda los detalles de la forma de clase y mueva el puntero del mouse sobre los miembros de la clase. La información sobre herramientas muestra la declaración de cada miembro.

5. Haga clic con el botón derecho en la forma de clase y haga clic en **Detalles de clase**. Puede ver o modificar las propiedades del nuevo tipo en la ventana **Detalles de clase**.

## <a name="see-also"></a>Vea también

- <xref:System.Nullable%601>
- [Tipos que aceptan valores NULL](/dotnet/csharp/programming-guide/nullable-types/index)
- [Utilizar tipos que aceptan valores NULL](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)
- [Cómo: Identificar tipos que aceptan valores NULL](/dotnet/csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type)
- [Tipos de valor que aceptan valores NULL](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)

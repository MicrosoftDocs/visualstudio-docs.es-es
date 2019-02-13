---
title: Procedimiento Crear un tipo que acepta valores null (Diseñador de clases) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 683e9e6fdd6108ade3a991ce5280a2f8024fe496
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834922"
---
# <a name="how-to-create-a-nullable-type-class-designer"></a>Cómo: Crear un tipo que acepta valores NULL (Diseñador de clases)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Determinados tipos de valor no siempre tienen (o necesitan) un valor definido. Esto es habitual en las bases de datos, donde es posible que algunos campos no tengan asignado ningún valor. Por ejemplo, se podría asignar un valor nulo a un campo de base de datos para indicar que aún no se le ha asignado ningún valor.  
  
 Un *tipo que acepta valores NULL* es un tipo de valor que se amplía para que acepte el intervalo normal de valores para ese tipo y además un valor nulo. Por ejemplo, a un valor NULL de `Int32`, también conocido como Nullable\<Int32>, se le puede asignar cualquier valor comprendido entre -2147483648 y 2147483647, o se le puede asignar un valor nulo. A un valor Nullable\<bool> se le pueden asignar los valores `True`, `False` o nulo (ningún valor).  
  
 Los tipos que aceptan valores NULL son instancias de la estructura <xref:System.Nullable%601>. Cada instancia de un tipo que acepta valores NULL tiene dos propiedades públicas de solo lectura, `HasValue` y `Value`:  
  
- `HasValue` es de tipo `bool` e indica si la variable contiene un valor definido. `True` significa que la variable contiene un valor que no es nulo. Puede probar un valor definido mediante una instrucción como `if (x.HasValue)` o `if (y != null)`.  
  
- `Value` es del mismo tipo que el tipo subyacente. Si `HasValue` es `True`, `Value` contiene un valor significativo. Si `HasValue` es `False`, al acceder a `Value` se producirá una excepción de operación no válida.  
  
  De forma predeterminada, cuando se declara una variable como un tipo que acepta valores NULL, no tiene ningún valor definido (`HasValue` es `False`) más que el valor predeterminado de su tipo de valor subyacente.  
  
  El Diseñador de clases muestra un tipo que acepta valores NULL al igual que muestra su tipo subyacente.  
  
  Para más información sobre los tipos que aceptan valores NULL en Visual C#, vea [Tipos que aceptan valores NULL](http://msdn.microsoft.com/library/e473cb01-28ca-42be-9cea-f717055d72c6). Para más información sobre los tipos que aceptan valores NULL en Visual Basic, vea [Tipos que admiten valores null](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6).  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>Para agregar un tipo que acepta valores NULL mediante el Diseñador de clases  
  
1.  En el Diagrama de clases, expanda una clase existente o cree una nueva clase.  
  
2.  Para agregar una clase al proyecto, en el menú **Diagrama de clases**, haga clic en **Agregar** y luego en **Agregar clase**.  
  
3.  Para expandir la forma de clase, en el menú **Diagrama de clases**, haga clic en **Expandir**.  
  
4.  Seleccione la forma de clase. En el menú **Diagrama de clases**, haga clic en **Agregar** y luego en **Campo**. Un nuevo campo con el nombre predeterminado **Campo** aparecerá en la forma de clase y también en la ventana **Detalles de clase**.  
  
5.  En la columna **Nombre** de la ventana **Detalles de clase** (o en la propia forma de clase), cambie el nombre del nuevo campo por un nombre válido y significativo.  
  
6.  En la columna **Tipo** de la ventana **Detalles de clase**, declare el tipo como un tipo que acepta valores NULL, como se muestra en el código siguiente:  
  
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
  
### <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>Para agregar un tipo que acepta valores NULL mediante el Editor de código  
  
1.  Agregue una clase al proyecto. Seleccione el nodo de proyecto en el **Explorador de soluciones** y, en el menú **Proyecto**, haga clic en **Agregar clase**.  
  
2.  En el archivo .cs o .vb de la nueva clase, agregue uno o más tipos que aceptan valores NULL en la nueva clase para la declaración de clase.  
  
3.  En Vista de clases, arrastre el icono de la nueva clase a la superficie de diseño Diseñador de clases. Aparece una forma de clase en el diagrama de clases.  
  
4.  Expanda los detalles de la forma de clase y mueva el puntero del mouse sobre los miembros de la clase. La información sobre herramientas muestra la declaración de cada miembro.  
  
5.  Haga clic con el botón derecho en la forma de clase y haga clic en **Detalles de clase**. Puede ver o modificar las propiedades del nuevo tipo en la ventana **Detalles de clase**.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Nullable%601>   
 [Tipos que aceptan valores NULL](http://msdn.microsoft.com/library/e473cb01-28ca-42be-9cea-f717055d72c6)   
 [Utilizar tipos que aceptan valores NULL](http://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28)   
 [Cómo: Identificar tipos que aceptan valores NULL](http://msdn.microsoft.com/library/d4b67ee2-66e8-40c1-ae9d-545d32c71387)   
 [Tipos de valor que aceptan valores NULL](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6)

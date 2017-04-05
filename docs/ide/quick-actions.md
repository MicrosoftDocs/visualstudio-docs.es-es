---
title: "Acciones rápidas | Microsoft Docs"
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: e173fb7d-c5bd-4568-ba0f-aa61913b3244
author: BrianPeek
ms.author: brpeek
manager: ghogen
dev_langs:
- CSharp
- VB
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 46846db26bee30841e6cb35913d533b512d01ba0
ms.openlocfilehash: 226e51ace56d51945cc380aaaf3450ae7dacf8e4
ms.lasthandoff: 03/27/2017

---
# <a name="quick-actions"></a>Acciones rápidas

Las [acciones rápidas](refactoring-code-generation-quick-actions.md#quick-actions) le permiten refactorizar, generar o modificar el código de otra manera fácilmente con una sola acción.  Aunque hay muchas acciones rápidas que se aplican específicamente a C# o a Visual Basic, también hay algunas que se aplican a los proyectos de C# y Visual Basic.  Se pueden aplicar mediante el icono de bombilla ![icono de bombilla pequeño](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") o mediante **Ctrl + .** cuando el cursor esté en la línea de código adecuada.

Verá una bombilla si hay una flecha en zigzag de color rojo y Visual Studio tiene una sugerencia para corregir el problema. Por ejemplo, si tiene un error que se indica mediante una flecha en zigzag de color rojo, aparecerá una bombilla cuando haya disponibles correcciones para ese error. Para cualquier lenguaje, un tercero puede proporcionar diagnósticos y sugerencias, por ejemplo, como parte de un SDK, y las bombillas de Visual Studio se encenderán siguiendo esas reglas.  

### <a name="to-see-a-light-bulb"></a>Para ver una bombilla  

1. En muchos casos, las bombillas aparecen espontáneamente cuando se desplaza el mouse sobre el punto de error, o en el margen izquierdo del editor cuando se coloca el cursor de inserción en una línea que tiene un error en ella. Cuando vea una flecha zigzagueante de color rojo, puede mover el puntero por encima para mostrar la bombilla. También puede hacer que una bombilla aparezca usando el ratón o el teclado para ir a algún sitio de la línea donde existe el problema.  

2. Pulse **Ctrl + .** en cualquier sitio de una línea para invocar a la bombilla e ir directamente a la lista de posibles correcciones.  

   ![Bombilla con el desplazamiento del mouse](../ide/media/vs2015_lightbulb_hover.png "VS2017_LightBulb_Hover")  

### <a name="to-see-potential-fixes"></a>Para ver posibles correcciones  
Haga clic en la flecha hacia abajo o en el vínculo Mostrar posibles correcciones para mostrar la lista de acciones rápidas que la bombilla puede llevar a cabo.  

![Bombilla expandida](../ide/media/vs2015_lightbulb_hover_expanded.png "VS2017_LightBulb_hover_expanded")

## <a name="common-quick-actions"></a>Acciones rápidas comunes
Estas son algunas de las acciones rápidas comunes que se aplican a código de C# y de Visual Basic.

### <a name="add-missing-casesdefault-caseboth"></a>Agregar casos que faltan, un caso predeterminado o ambos
Al crear una instrucción `switch` en C# o una instrucción `Select Case` en Visual Basic, puede usar una acción de código para agregar automáticamente los elementos de casos que faltan, una instrucción de caso predeterminado o ambos.  Para instrucción vacía como la siguiente:

```CSharp
enum MyEnum
{
    Item1,
    Item2,
    Item3
}

...

MyEnum myEnum = MyEnum.Item1;

switch(myEnum)
{
}
```

```VB
Enum MyEnum
    Item1
    Item2
    Item3
End Enum

...

Dim myEnum as MyEnum = MyEnum.Item1

Select Case myEnum
End Select
```

Si usa la acción rápida **Agregar ambos** para rellenar los casos que faltan y un caso predeterminado, creará lo siguiente:

```CSharp
switch(myEnum)
{
    case MyEnum.Item1:
        break;
    case MyEnum.Item2:
        break;
    case MyEnum.Item3:
        break;
    default:
        break;    
}
```

```VB
Select Case myEnum
    Case MyEnum.Item1
        Exit Select
    Case MyEnum.Item2
        Exit Select
    Case Else
        Exit Select
End Select
```

### <a name="correct-misspelled-type"></a>Corregir un tipo mal escrito
Si se equivoca al escribir un tipo en Visual Studio, esta acción rápida lo corregirá automáticamente.  Verá estos elementos en el menú de bombilla como **"Cambiar '*tipo mal escrito*' a '*tipo correcto*'"**.  Por ejemplo:

```CSharp
// Before
private viod MyMethod()
{
}

// Change 'viod' to 'void'

// After
private void MyMethod()
{
}
```

```VB
' Before
Function MyFunction as Intger
End Function

' Change 'Intger' to 'Integer'

' After
Function MyFunction as Integer
End Function
```

### <a name="remove-unnecessary-cast"></a>Quitar conversión innecesaria
Si convierte un tipo a otro que no requiere una conversión, el elemento de acción rápida **Quitar conversión innecesaria** quitará la conversión del código.

```CSharp
// before
int number = (int)3;

// Remove Unnecessary Cast

// after
int number = 3;
```

```VB
' Before
Dim number as Integer = CType(3, Integer)

' Remove Unnecessary Cast

' After
Dim number as Integer = 3
```

### <a name="replace-method-with-property--replace-property-with-method"></a>Reemplazar método con propiedad / Reemplazar propiedad con método
Estas acciones rápidas convertirán un método en una propiedad o viceversa.  En el ejemplo siguiente se muestra el cambio de un método a una propiedad.  Para ver el caso contrario, basta con que invierta las secciones *Before* y *After*.

```CSharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

```VB
Dim MyValue As Integer

' Before
Function GetMyValue() As Integer
    Return MyValue
End Function

' Replace 'GetMyValue' with property

' After
ReadOnly Property MyValue As Integer
    Get
        Return MyValue
    End Get
End Property
```

### <a name="make-method-synchronous"></a>Convertir un método en sincrónico
Cuando se usa la palabra clave `async`/`Async` en un método, se espera que en algún lugar dentro de ese método también se use la palabra clave `await`/`Await`.  Pero si este no es el caso, aparecerá una acción rápida que le permitirá convertir el método en sincrónico si elimina la palabra clave `async`/`Async` y cambia el tipo de valor devuelto.  Use la opción **Convertir el método en sincrónico** del menú Acciones rápidas.

```CSharp
// Before
async Task<int> MyAsyncMethod()
{
    return 3;
}

// Make method synchronous

// After
int MyAsyncMethod()
{
    return 3;
}
```

```VB
' Before
Async Function MyAsyncMethod() As Task(Of Integer)
    Return 3
End Function

' Make method synchronous

' After
Function MyAsyncMethod() As Integer
    Return 3
End Function
```

### <a name="make-method-asynchronous"></a>Convertir un método en asincrónico
Cuando se usa la palabra clave `await`/`Await` dentro de un método, se espera que el propio método esté marcado con la palabra clave `async`/`Async`.  Pero si este no es el caso, aparecerá una acción rápida que le permitirá convertir el método en asincrónico.  Use la opción **Make method/Function asynchronous** (Convertir el método/función en asincrónico) del menú Acciones rápidas.

```CSharp
// Before
int MyAsyncMethod()
{
    return await Task.Run(...);
}

// Make method synchronous

// After
async Task<int> MyAsyncMethod()
{
    return await Task.Run(...);
}
```

```VB
' Before
Function MyAsyncMethod() as Integer
    Return  Await Task.Run(...)
End Function

' Make method synchronous

' After
Async Function MyAsyncMethod() As Task(Of Integer)
    Return Await Task.Run(...)
End Function
```

### <a name="remove-unnecesary-usingsimports"></a>Quitar instrucciones Using o Import innecesarias
La acción rápida **Eliminar instrucciones Using innecesarias/Quitar instrucciones Import innecesarias** quitará todas las instrucciones `using` y `Import` sin usar del archivo actual.  Cuando se selecciona este elemento, las importaciones de espacios de nombres sin usar se quitarán inmediatamente.

### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Agregar instrucciones Using o Import para tipos en ensamblados de referencia, paquetes NuGet u otros tipos de la solución
Si usa tipos ubicados en otros proyectos de la solución, la acción rápida se mostrará automáticamente, pero deberá habilitar los demás en la pestaña **Herramientas > Opciones > C#** o **Básico > Avanzadas**:  

* Sugerir instrucciones Using o Import para tipos de ensamblados de referencia
* Sugerir instrucciones Using o Import para tipos de paquetes NuGet

Cuando está habilitado, si usa un tipo de un espacio de nombres que actualmente no se importa pero que existe en un ensamblado de referencia o un paquete NuGet, se creará la instrucción Using o Import.

```CSharp
// Before
Debug.WriteLine("Hello");

// using System.Diagnostics;

// After
using System.Diagnostics;

Debug.WriteLine("Hello");
```

```VB
' Before
Debug.WriteLine("Hello")

' Imports System.Diagnostics

// After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

### <a name="convert-to-interpolated-string"></a>Convertir en una cadena interpolada
Las [cadenas interpoladas](/dotnet/articles/csharp/language-reference/keywords/interpolated-strings) son una forma sencilla de expresar cadenas con variables insertadas, similar al método **[String.Format](https://msdn.microsoft.com/library/system.string.format(v=vs.110).aspx)**.  Esta acción rápida reconoce los casos en los que las cadenas están concatenadas o usan **String.Format** y cambia el uso a una cadena interpolada.

```CSharp
// Before
int num = 3;
string s = string.Format("My string with {0} in the middle", num);

// Convert to interpolated string

// After
int num = 3;
string s = $"My string with {num} in the middle";
```

```VB
' Before
Dim num as Integer = 3
Dim s as String = String.Format("My string with {0} in the middle", num)

' Convert to interpolated string

' After
Dim num as Integer = 3
Dim s As String = $"My string with {num} in the middle"
```

# <a name="see-also"></a>Vea también
* [Estilos de código y acciones rápidas](code-styles-and-quick-actions.md)

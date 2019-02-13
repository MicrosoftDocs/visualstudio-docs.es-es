---
title: Acciones rápidas comunes
ms.date: 03/28/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f6f8872fa9acb2ca79010a87168c629dcbc3ac6e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55932942"
---
# <a name="common-quick-actions"></a>Acciones rápidas comunes

Las secciones de este tema presentan algunas de las **acciones rápidas** comunes que se aplican a código de C# y de Visual Basic. Estas acciones son *correcciones del código* para el diagnóstico de compilador o [analizadores de .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md) integrados en Visual Studio.

## <a name="actions-that-fix-errors"></a>Acciones que corrigen errores

Las acciones rápidas de esta sección corrigen errores en el código que provocarían que se produjera un error en la compilación. Si hay acciones rápidas disponibles para corregir un error en una línea de código, el icono que se muestra en el margen o debajo del subrayado ondulado rojo es una bombilla con una “x” roja en ella.

![Menú e icono de error de las acciones rápidas](media/error-light-bulb-with-code.png)

### <a name="correct-misspelled-symbol-or-keyword"></a>Corrección de símbolos o palabras clave mal escritos

Si se equivoca al escribir un tipo o una palabra clave en Visual Studio, esta acción rápida lo corrige automáticamente. Verá estos elementos en el menú de bombilla como **"Cambiar '*palabra mal escrita*' a '*palabra correcta*'**. Por ejemplo:

```csharp
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

```vb
' Before
Function MyFunction as Intger
End Function

' Change 'Intger' to 'Integer'

' After
Function MyFunction as Integer
End Function
```

| Identificador del error: | Lenguajes aplicables | Versión compatible |
| ------- | -------------------- | ---------------- |
| CS0103, BC30002 | C# y Visual Basic | Visual Studio 2015 Update 2 |

### <a name="resolve-git-merge-conflict"></a>Resolver conflictos de fusión mediante combinación de GIT

Estas acciones rápidas permiten resolver conflictos de fusión mediante combinación de GIT al "adoptar un cambio" que elimina los marcadores y el código en conflicto.

```csharp
// Before
private void MyMethod()
{
    if (false)
    {

    }
}

// Take changes from 'HEAD'

// After
private void MyMethod()
{
    if (true)
    {

    }
}
```

| Identificador del error: | Lenguajes aplicables | Versión compatible |
| ------- | -------------------- | ---------------- |
| CS8300, BC37284 | C# y Visual Basic | Visual Studio 2017 versión 15.3 |

## <a name="actions-that-remove-unnecessary-code"></a>Acciones que quitan código innecesario

### <a name="remove-unnecessary-usingsimports"></a>Quitar instrucciones Using o Import innecesarias

La acción rápida **Eliminar instrucciones Using innecesarias/Quitar instrucciones Import innecesarias** quita todas las instrucciones `using` y `Import` sin usar del archivo actual. Cuando se seleccione este elemento, las importaciones de espacios de nombres sin usar se quitarán.

| Lenguajes aplicables | Versión compatible |
| -------------------- | ---------------- |
| C# y Visual Basic | Visual Studio 2015 RTW |

### <a name="remove-unnecessary-cast"></a>Quitar conversión innecesaria

Si convierte un tipo a otro que no requiere una conversión, el elemento de acción rápida **Quitar conversión innecesaria** quitará la conversión innecesaria.

```csharp
// before
int number = (int)3;

// Remove Unnecessary Cast

// after
int number = 3;
```

```vb
' Before
Dim number as Integer = CType(3, Integer)

' Remove Unnecessary Cast

' After
Dim number as Integer = 3
```

| Id. de diagnóstico | Lenguajes aplicables | Versión compatible |
| ------- | -------------------- | ---------------- |
| IDE0004 | C# y Visual Basic | Visual Studio 2015 RTW |

### <a name="remove-unused-variables"></a>Quitar variables no usadas

Esta acción rápida permite quitar variables que se han declarado pero que nunca se han usado en el código.

```csharp
// Before
public MyMethod()
{
    var unused = 8;
    var used = 1;
    return DoStuff(used);
}

// Remove unused variables

// After
public MyMethod()
{
    var used = 1;
    return DoStuff(used);
}
```

| Id. de diagnóstico | Lenguajes aplicables | Versión compatible |
| ------- | -------------------- | ---------------- |
| CS0219, BC42024 | C# y Visual Basic | Visual Studio 2017 versión 15.3 |

### <a name="remove-type-from-default-value-expression"></a>Quitar el tipo de la expresión de valor predeterminado

Esta acción rápida quita el tipo de valor de una expresión de valor predeterminado y usa el [literal default](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference) cuando el compilador puede deducir el tipo de la expresión.

```csharp
// Before
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }

// Simplify default expression

// After
void DoWork(CancellationToken cancellationToken = default) { ... }
```

| Id. de diagnóstico | Lenguajes aplicables | Versión compatible |
| ------- | -------------------- | ---------------- |
| IDE0034 | C# 7.1+ | Visual Studio 2017 versión 15.3 |

## <a name="actions-that-add-missing-code"></a>Acciones que agregan código que falta

### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Agregar instrucciones Using o Import para tipos en ensamblados de referencia, paquetes NuGet u otros tipos de la solución

Si usa tipos ubicados en otros proyectos de la solución, la acción rápida se mostrará automáticamente, pero deberá habilitar los demás en la pestaña **Herramientas > Opciones > C#** o **Básico > Avanzadas**:

- Sugerir instrucciones Using o Import para tipos de ensamblados de referencia
- Sugerir instrucciones Using o Import para tipos de paquetes NuGet

Cuando está habilitado, si usa un tipo de un espacio de nombres que actualmente no se importa pero que existe en un ensamblado de referencia o un paquete NuGet, se creará la instrucción Using o Import.

```csharp
// Before
Debug.WriteLine("Hello");

// using System.Diagnostics;

// After
using System.Diagnostics;

Debug.WriteLine("Hello");
```

```vb
' Before
Debug.WriteLine("Hello")

' Imports System.Diagnostics

// After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

| Id. de diagnóstico | Lenguajes aplicables | Versión compatible |
| ------- | -------------------- | ---------------- |
| CS0103, BC30451 | C# y Visual Basic| Visual Studio 2015 Update 2 |

### <a name="add-missing-casesdefault-caseboth"></a>Agregar casos que faltan, un caso predeterminado o ambos

Al crear una instrucción `switch` en C# o una instrucción `Select Case` en Visual Basic, puede usar una acción de código para agregar automáticamente los elementos de casos que faltan, una instrucción de caso predeterminado o ambos.

Tenga en cuenta la enumeración siguiente y vacíe la instrucción `switch` o `Select Case`:

```csharp
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

```vb
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

Con la acción rápida **Agregar ambos** se completan los casos omitidos y se agrega un caso predeterminado:

```csharp
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

```vb
Select Case myEnum
    Case MyEnum.Item1
        Exit Select
    Case MyEnum.Item2
        Exit Select
    Case Else
        Exit Select
End Select
```

| Id. de diagnóstico | Lenguajes aplicables | Versión compatible |
| ------- | -------------------- | ---------------- |
| IDE0010 | C# y Visual Basic| Visual Studio 2017 versión 15.3 |

### <a name="add-null-checks-for-parameters"></a>Agregar comprobaciones de parámetros nulos

Esta acción rápida permite agregar una comprobación en el código para saber si un parámetro es nulo.

```csharp
// Before
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty) // cursor inside myProperty
    {
        MyProperty = myProperty;
    }
}

// Add null check

// After
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty)
    {
        MyProperty = myProperty ?? throw new ArgumentNullException(nameof(myProperty));
    }
}
```

| Lenguajes aplicables | Versión compatible |
| -------------------- | ---------------- |
| C# y Visual Basic| Visual Studio 2017 versión 15.3 |

### <a name="add-argument-name"></a>Agregar nombre de argumento

```csharp
// Before
var date = new DateTime(1997, 7, 8);

// Include argument name 'year' (include trailing arguments)

// After
var date = new DateTime(year: 1997, month: 7, day: 8);
```

| Lenguajes aplicables | Versión compatible |
| -------------------- | ---------------- |
| C# y Visual Basic| Visual Studio 2017 versión 15.3 |

### <a name="add-braces"></a>Agregar llaves

Las acción rápida Agregar llaves encapsula llaves alrededor de instrucciones `if` de una sola línea.

```csharp
// Before
if (true)
    return "hello,world";

// Add braces

// After
if (true)
{
    return "hello,world";
}
```

| Id. de diagnóstico | Lenguajes aplicables | Versión compatible |
| ------- | -------------------- | ---------------- |
| IDE0011 | C# | Visual Studio 2017 RTW |

### <a name="add-and-order-modifiers"></a>Agregar y ordenar modificadores

Estas acciones rápidas ayudan a organizar los modificadores permitiendo ordenar los modificadores de accesibilidad existentes y agregar los que faltan.

```csharp
// Before
enum Color
{
    Red, White, Blue
}

// Add accessibility modifiers

// After
internal enum Color
{
    Red, White, Blue
}
```

```csharp
// Before
static private int thisFieldIsPublic;

// Order modifiers

// After
private static int thisFieldIsPublic;
```

| Id. de diagnóstico | Lenguajes aplicables | Versión compatible |
| ------- | -------------------- | ---------------- |
| IDE0036 | C# y Visual Basic| Versión 15.5 de Visual Studio 2017 |
| IDE0040 | C# y Visual Basic| Versión 15.5 de Visual Studio 2017 |

## <a name="code-transformations"></a>Transformaciones de código

### <a name="convert-if-construct-to-switch"></a>Convertir la construcción "if" en "switch"

Esta acción rápida permite convertir una construcción **if-then-else** en una construcción **switch**.

```csharp
// Before
if (obj is string s)
{
  Console.WriteLine("obj is a string: " + s);
}

else if (obj is int i && i > 10)
{
  Console.WriteLine("obj is an int greater than 10");
}

// Convert to switch

// After
switch (obj)
{
  case string s:
    Console.WriteLine("Obj is a string: " + s);
    break;
  case int i when i > 10:
    Console.WriteLine("obj is an int greater than 10");
    break;
}
```

```vb
' Before
If TypeOf obj Is String s Then
    Console.WriteLine("obj is a string: " + s)
Else If TypeOf obj Is Integer i And i > 10 Then
    Console.WriteLine("obj is an int greater than 10")
End If

' Convert to switch

' After
Select Case obj
  Case String s
    Console.WriteLine("Obj is a string: " + s)
    Exit Sub
  Case Integer i when i > 10
    Console.WriteLine("obj is an int greater than 10")
    Exit Sub
End Select
```

| Lenguajes aplicables | Versión compatible |
| -------------------- | ---------------- |
| C# y Visual Basic| Visual Studio 2017 versión 15.3 |

### <a name="convert-to-interpolated-string"></a>Convertir en una cadena interpolada

Las [cadenas interpoladas](/dotnet/csharp/language-reference/keywords/interpolated-strings) son una forma sencilla de expresar cadenas con variables insertadas, similar al método **[String.Format](/dotnet/api/system.string.format#overloads)**.  Esta acción rápida reconoce los casos en los que las cadenas están concatenadas o usan **String.Format** y cambia el uso a una cadena interpolada.

```csharp
// Before
int num = 3;
string s = string.Format("My string with {0} in the middle", num);

// Convert to interpolated string

// After
int num = 3;
string s = $"My string with {num} in the middle";
```

```vb
' Before
Dim num as Integer = 3
Dim s as String = String.Format("My string with {0} in the middle", num)

' Convert to interpolated string

' After
Dim num as Integer = 3
Dim s As String = $"My string with {num} in the middle"
```

| Lenguajes aplicables | Versión compatible |
| -------------------- | ---------------- |
| C# 6.0+ y Visual Basic 14+ | Visual Studio 2017 RTW |

### <a name="use-object-initializers"></a>Usar inicializadores de objeto

Esta acción rápida permite usar [inicializadores de objeto](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) en lugar de invocar el constructor y tener líneas adicionales de instrucciones de asignación.

```csharp
// Before
var c = new Customer();
c.Age = 21;

// Object initialization can be simplified

// After
var c = new Customer() { Age = 21 };
```

```vb
' Before
Dim c = New Customer()
c.Age = 21

' Object initialization can be simplified

' After
Dim c = New Customer() With {.Age = 21}
```

| Id. de diagnóstico | Lenguajes aplicables | Versión compatible |
| ------- | -------------------- | ---------------- |
| IDE0017 | C# y Visual Basic | Visual Studio 2017 RTW |

### <a name="use-collection-initializers"></a>Usar inicializadores de colección

Esta acción rápida permite usar [inicializadores de colección](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) en lugar de varias llamadas al método `Add` de la clase.

```csharp
// Before
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);

// Collection initialization can be simplified

// After
var list = new List<int> { 1, 2, 3 };
```

```vb
' Before
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)

' Collection initialization can be simplified

' After
Dim list = New List(Of Integer) From {1, 2, 3}
```

| Id. de diagnóstico | Lenguajes aplicables | Versión compatible |
| ------- | -------------------- | ---------------- |
| IDE0028 | C# y Visual Basic | Visual Studio 2017 RTW |

### <a name="convert-auto-property-to-full-property"></a>Convertir propiedad automática en propiedad completa

Esta acción rápida permite convertir una propiedad automática en una propiedad completa y viceversa.

```csharp
// Before
private int MyProperty { get; set; }

// Convert to full property

// After
private int MyProperty
{
    get { return _myProperty; }
    set { _myProperty = value; }
}
```

```vb
' Before
Public Property Name As String

' Convert to full property

' After
Private _Name As String

Public Property Name As String
    Get
        Return _Name
    End Get
    Set
        _Name = Value
    End Set
End Property
```

| Lenguajes aplicables | Versión compatible |
| -------------------- | ---------------- |
| C# y Visual Basic | Versión 15.5 de Visual Studio 2017 |

### <a name="convert-block-body-to-expression-bodied-member"></a>Convertir cuerpo de bloques en miembro con forma de expresión

Esta acción rápida permite convertir cuerpos de bloques en miembros con forma de expresión para métodos, constructores, operadores, propiedades, indizadores y descriptores de acceso.

```csharp
//Before
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get { return _myProperty; }
        set
        {
            _myProperty = value;
        }
    }

    public MyClass4(int myProperty)
    {
        MyProperty = myProperty;
    }

    public void PrintProperty()
    {
        Console.WriteLine(MyProperty);
    }
}

// Use expression body for accessors/constructors/methods

// After
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get => _myProperty;
        set => _myProperty = value;
    }

    public MyClass4(int myProperty) => MyProperty = myProperty;

    public void PrintProperty() => Console.WriteLine(MyProperty);
}
```

| Id. de diagnóstico | Lenguajes aplicables | Versión compatible |
| ------- | -------------------- | ---------------- |
| IDE0021-27 | C# 6.0+ | Visual Studio 2017 RTW |

### <a name="convert-anonymous-function-to-local-function"></a>Convertir función anónima en función local

Esta acción rápida convierte funciones anónimas en funciones locales.

```csharp
// Before
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};

// Use local function

// After
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}
```

### <a name="convert-referenceequals-to-is-null"></a>Convertir "ReferenceEquals" en "es null"

| Id. de diagnóstico | Lenguajes aplicables | Versión compatible |
| ------- | -------------------- | ---------------- |
| IDE0041 | C# 7.0+ | Versión 15.5 de Visual Studio 2017 |

Esta acción rápida sugiere el uso de la [coincidencia de patrones](/dotnet/csharp/pattern-matching) en lugar del patrón de codificación ```ReferenceEquals```, siempre que sea posible.

```csharp
// Before
var value = "someString";
if (object.ReferenceEquals(value, null))
{
    return;
}

// Use 'is null' check

// After
var value = "someString";
if (value is null)
{
    return;
}
```

| Id. de diagnóstico | Lenguajes aplicables | Versión compatible |
| ------- | -------------------- | ---------------- |
| IDE0039 | C# 7.0+ | Versión 15.5 de Visual Studio 2017 |

### <a name="introduce-pattern-matching"></a>Introducir la coincidencia de patrones

Esta acción rápida sugiere el uso de la [coincidencia de patrones](/dotnet/csharp/pattern-matching) con conversiones y comprobaciones de valores NULL en C#.

```csharp
// Before
if (o is int)
{
    var i = (int)o;
    ...
}

// Use pattern matching

// After
if (o is int i)
{
    ...
}
```

```csharp
// Before
var s = o as string;
if (s != null)
{
    ...
}

// Use pattern matching

// After
if (o is string s)
{
    ...
}
```

| Id. de diagnóstico | Lenguajes aplicables | Versión compatible |
| ------- | -------------------- | ---------------- |
| IDE0020 | C# 7.0+ | Visual Studio 2017 RTW |
| IDE0019 | C# 7.0+ | Visual Studio 2017 RTW |

### <a name="change-base-for-numeric-literals"></a>Cambiar base de literales numéricos

Esta acción rápida le permite convertir un literal numérico de un sistema numérico base a otro. Por ejemplo, puede cambiar un número a hexadecimal o a formato binario.

```csharp
// Before
int countdown = 2097152;

// Convert to hex

// After
int countdown = 0x200000;
```

```vb
' Before
Dim countdown As Integer = 2097152

' Convert to hex

' After
Dim countdown As Integer = &H200000
```

| Lenguajes aplicables | Versión compatible |
| ------- | -------------------- | ---------------- |
| C# 7.0+ y Visual Basic 14+ | Visual Studio 2017 versión 15.3 |

### <a name="insert-digit-separators-into-literals"></a>Insertar separadores de dígitos en literales

Esta acción rápida le permite agregar caracteres separadores en valores literales.

```csharp
// Before
int countdown = 1000000;

// Separate thousands

// After
int countdown = 1_000_000;
```

```vb
' Before
Dim countdown As Integer = 1000000

' Separate thousands

' After
Dim countdown As Integer = 1_000_000
```

| Lenguajes aplicables | Versión compatible |
| ------- | -------------------- | ---------------- |
| C# 7.0+ y Visual Basic 14+ | Visual Studio 2017 versión 15.3 |

### <a name="use-explicit-tuple-names"></a>Usar nombres de tupla explícitos

Esta acción rápida identifica las áreas donde se puede usar el nombre de tupla explícito en lugar de Elemento1, Elemento2, etc.

```csharp
// Before
(string name, int age) customer = GetCustomer();
var name = customer.Item1;

// Use explicit tuple name

// After
(string name, int age) customer = GetCustomer();
var name = customer.name;
```

```vb
' Before
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1

' Use explicit tuple name

' After
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name
```

| Id. de diagnóstico | Lenguajes aplicables | Versión compatible |
| ------- | -------------------- | ---------------- |
| IDE0033 | C# 7.0+ y Visual Basic 15+ | Visual Studio 2017 RTW |

### <a name="use-inferred-names"></a>Usar nombres deducidos

Esta acción rápida indica si el código se puede simplificar para usar nombres de miembros inferidos en tipos anónimos, o bien nombres de elementos inferidos en tuplas.

```csharp
// Before
var anon = new { age = age, name = name };

// Use inferred member name

// After
var anon = new { age, name };
```

```csharp
// Before
var tuple = (age: age, name: name);

// Use inferred tuple element name

// After
var tuple = (age, name);
```

| Id. de diagnóstico | Lenguajes aplicables | Versión compatible |
| ------- | -------------------- | ---------------- |
| IDE0037 | C# | Visual Studio 2017 v. 15.5 |
| IDE0037 | C# 7.1+ | Visual Studio 2017 v. 15.5 |

### <a name="deconstruct-tuple-declaration"></a>Deconstruir la declaración de tupla

Esta acción rápida permite deconstruir las declaraciones de variable de tupla.

```csharp
// Before
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");

//Deconstruct variable declaration

// After
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");
```

| Id. de diagnóstico | Lenguajes aplicables | Versión compatible |
| ------- | -------------------- | ---------------- |
| IDE0042 | C# 7.0+ | Visual Studio 2017 v. 15.5 |

### <a name="make-method-synchronous"></a>Convertir un método en sincrónico

Cuando se usa la palabra clave `async` o `Async` en un método, se espera que dentro de ese método también se use la palabra clave `await` o `Await`. En caso contrario, aparecerá una acción rápida para convertir el método en sincrónico si elimina la palabra clave `async` o `Async` y cambia el tipo de valor devuelto. Use la opción **Convertir el método en sincrónico** del menú Acciones rápidas.

```csharp
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

```vb
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

| Identificador del error: | Lenguajes aplicables | Versión compatible |
| ------- | -------------------- | ---------------- |
| CS1998, BC42356 | C# y Visual Basic | Visual Studio 2015 Update 2 |

### <a name="make-method-asynchronous"></a>Convertir un método en asincrónico

Cuando se usa la palabra clave `await` o `Await` dentro de un método, se espera que el método esté marcado con la palabra clave `async` o `Async`. En caso contrario, aparece una acción rápida para convertir el método en asincrónico. Use la opción **Make method/Function asynchronous** (Convertir el método/función en asincrónico) del menú Acciones rápidas.

```csharp
// Before
int MyAsyncMethod()
{
    return await Task.Run(...);
}

// Make method asynchronous

// After
async Task<int> MyAsyncMethod()
{
    return await Task.Run(...);
}
```

```vb
' Before
Function MyAsyncMethod() as Integer
    Return  Await Task.Run(...)
End Function

' Make method asynchronous

' After
Async Function MyAsyncMethod() As Task(Of Integer)
    Return Await Task.Run(...)
End Function
```

| Identificador del error: | Lenguajes aplicables | Versión compatible |
| ------- | -------------------- | ---------------- |
| CS4032, BC37057 | C# y Visual Basic | Visual Studio 2017 |

## <a name="see-also"></a>Vea también

- [Acciones rápidas](../ide/quick-actions.md)

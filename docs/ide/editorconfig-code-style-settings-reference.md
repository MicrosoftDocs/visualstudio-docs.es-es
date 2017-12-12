---
title: "Configuración de la convención de codificación de .NET para EditorConfig | Microsoft Docs"
ms.custom: 
ms.date: 10/13/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
helpviewer_keywords: editor
ms.assetid: 
caps.latest.revision: "1"
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.technology: vs-ide-general
ms.openlocfilehash: f59065777de938c07a88d722cabdba82d6b19c02
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>Configuración de la convención de codificación de .NET para EditorConfig
Puede definir y mantener un estilo de código coherente en el código base con el uso de un archivo [EditorConfig](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options). EditorConfig incluye varias propiedades de formato básicas, como `indent_style` e `indent_size`. En Visual Studio, las convenciones de codificación de .NET también se pueden configurar mediante un archivo EditorConfig. Los archivos EditorConfig permiten habilitar o deshabilitar las convenciones de codificación individuales de .NET y configurar el grado en el que quiere que se aplique la convención mediante un nivel de gravedad. Para más información sobre cómo usar EditorConfig para aplicar la coherencia en el código base, lea [Crear opciones de configuración del editor personalizadas y portátiles](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options). Para ver un ejemplo, eche un vistazo al [archivo .editorconfig de la plataforma del compilador de .NET](https://github.com/dotnet/roslyn/blob/master/.editorconfig).  

Hay tres categorías de convención de codificación de .NET admitidas:  
- [Convenciones de lenguaje](#language-conventions)  
   Reglas relativas al lenguaje C# o Visual Basic. Por ejemplo, puede especificar reglas sobre el uso de `var` o tipos explícitos en la definición de variables o la preferencia por miembros con forma de expresión.  
- [Convenciones de formato](#formatting-conventions)  
   Reglas sobre el diseño y la estructura del código para que sea más fácil de leer. Por ejemplo, puede especificar reglas sobre las llaves Allman o preferir espacios en los bloques de control.  
- [Convenciones de nomenclatura](#naming-conventions)  
   Reglas relacionadas con los nombres de los elementos de código. Por ejemplo, puede especificar que los métodos `async` deben terminar en "Async".  

## <a name="language-conventions"></a>Convenciones de lenguaje  
Las reglas para las convenciones de lenguaje tienen el formato siguiente:  

`options_name = false|true : none|suggestion|warning|error`  

Para cada regla de convención de lenguaje, debe especificar **true** (se prefiere este estilo) o **false** (no se prefiere este estilo), y la **gravedad**. La gravedad especifica el nivel de cumplimiento para ese estilo.  

En la tabla siguiente se enumeran los valores de gravedad posibles y sus efectos:  

Gravedad | Efecto
:------- | ------
Ninguna o silenciosa | No mostrar nada al usuario cuando se infringe esta regla. Pero las características de generación de código generarán código con este estilo.  
suggestion | Cuando se infringe esta regla de estilo, se muestra al usuario como una sugerencia. Las sugerencias aparecen como tres puntos de color gris en los dos primeros caracteres.  
warning | Cuando se infringe esta regla de estilo, se muestra una advertencia del compilador.  
error | Cuando se infringe esta regla de estilo, se muestra un error del compilador.  

En la lista siguiente se muestran las reglas de convención de lenguaje permitidas:  

- Configuración del estilo de código de .NET
    - [Los calificadores "This." y "Me."](#this_and_me)
        - dotnet\_style\_qualification\_for_field
        - dotnet\_style\_qualification\_for_property
        - dotnet\_style\_qualification\_for_method
        - dotnet\_style\_qualification\_for_event
    - [Palabras clave del lenguaje en lugar de nombres de tipos de marco para referencias de tipo](#language_keywords)
        - dotnet\_style\_predefined\_type\_for\_locals\_parameters_members
        - dotnet\_style\_predefined\_type\_for\_member_access
    - [Preferencias de nivel de expresión](#expression_level)
        - dotnet\_style\_object_initializer
        - dotnet\_style\_collection_initializer
        - dotnet\_style\_explicit\_tuple_names
        - dotnet\_style\_coalesce_expression
        - dotnet\_style\_null_propagation
- Configuración del estilo de código de C#
    - [Tipos implícitos y explícitos](#var)
        - csharp\_style\_var\_for\_built\_in_types
        - csharp\_style\_var\_when\_type\_is_apparent
        - csharp\_style\_var_elsewhere
    - [Miembros con forma de expresión](#expression_bodied_members)
        - csharp\_style\_expression\_bodied_methods
        - csharp\_style\_expression\_bodied_constructors
        - csharp\_style\_expression\_bodied_operators
        - csharp\_style\_expression\_bodied_properties
        - csharp\_style\_expression\_bodied_indexers
        - csharp\_style\_expression\_bodied_accessors
    - [Coincidencia de patrones](#pattern_matching)
        - csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check
        - csharp\_style\_pattern\_matching\_over\_as\_with\_null_check
    - [Declaraciones de variables insertadas](#inlined_variable_declarations)
        - csharp\_style\_inlined\_variable_declaration
    - [Preferencias de nivel de expresión](#expression_level_csharp)
        - csharp\_prefer\_simple\_default_expression
    - [Preferencias de la comprobación de "NULL"](#null_checking)
        - csharp\_style\_throw_expression
        - csharp\_style\_conditional\_delegate_call
    - [Preferencias de bloques de código](#code_block)
        - csharp\_prefer_braces

### <a name="net-code-style-settings"></a>Configuración del estilo de código de .NET  
Las reglas de estilo de esta sección son aplicables a C# y Visual Basic. Para ver ejemplos de código en el lenguaje de programación preferido, elíjalo en el menú desplegable **Lenguaje** en la esquina superior derecha de la ventana del explorador.  

#### <a name="this_and_me">Los calificadores "This." y "Me."</a>
Esta regla de estilo (los identificadores de regla IDE0003 e IDE0009) se puede aplicar a campos, propiedades, métodos o eventos. Un valor **true** significa que prefiere que el símbolo de código esté precedido por `this.` en C# o `Me.` en Visual Basic. Un valor **false** significa que prefiere que el elemento de código _no_ esté precedido por `this.` o `Me.`.  

En esta tabla se muestran los nombres de las reglas, los lenguajes de programación aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:  

| Nombre de regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión compatible |
| ----------- | -------------------- | ----------------------| ----------------  |
| dotnet_style_qualification_for_field | C# y Visual Basic | false:none | Visual Studio 2017 RTW |
| dotnet_style_qualification_for_property | C# y Visual Basic | false:none | Visual Studio 2017 RTW |
| dotnet_style_qualification_for_method | C# y Visual Basic | false:none | Visual Studio 2017 RTW |
| dotnet_style_qualification_for_event | C# y Visual Basic | false:none | Visual Studio 2017 RTW |   

**dotnet\_style\_qualification\_for_field**  
Cuando esta regla se establece en **true**, se prefiere que los campos estén precedidos por `this.` en C# o `Me.` en Visual Basic.  
Cuando esta regla se establece en **false**, se prefiere que los campos _no_ estén precedidos por `this.` o `Me.`.  

Ejemplos de código:  

```csharp
// dotnet_style_qualification_for_field = true
this.capacity = 0;

// dotnet_style_qualification_for_field = false
capacity = 0;
```
```vb
' dotnet_style_qualification_for_field = true
Me.capacity = 0

' dotnet_style_qualification_for_field = false
capacity = 0
```  

**dotnet\_style\_qualification\_for_property**  
Cuando esta regla se establece en **true**, se prefiere que las propiedades estén precedidas de `this.` en C# o `Me.` en Visual Basic.  
Cuando esta regla se establece en **false**, se prefiere que las propiedades _no_ estén precedidas de `this.` o `Me.`.  

Ejemplos de código:  

```csharp
// dotnet_style_qualification_for_property = true
this.ID = 0;

// dotnet_style_qualification_for_property = false
ID = 0;
```
```vb
' dotnet_style_qualification_for_property = true
Me.ID = 0

' dotnet_style_qualification_for_property = false
ID = 0
```  

**dotnet\_style\_qualification\_for_method**  
Cuando esta regla se establece en **true**, se prefiere que los métodos estén precedidos de `this.` en C# o `Me.` en Visual Basic.  
Cuando esta regla se establece en **false**, se prefiere que los métodos _no_ estén precedidos de `this.` o `Me.`.  

Ejemplos de código:  

```csharp
// dotnet_style_qualification_for_method = true
this.Display();

// dotnet_style_qualification_for_method = false
Display();
```
```vb
' dotnet_style_qualification_for_method = true
Me.Display()

' dotnet_style_qualification_for_method = false
Display()
```  

**dotnet\_style\_qualification\_for_event**  
Cuando esta regla se establece en **true**, se prefiere que los eventos estén precedidos de `this.` en C# o `Me.` en Visual Basic.  
Cuando esta regla se establece en **false**, se prefiere que los eventos _no_ estén precedidos de `this.` o `Me.`.  

Ejemplos de código:  

```csharp
// dotnet_style_qualification_for_event = true
this.Elapsed += Handler;

// dotnet_style_qualification_for_event = false
Elapsed += Handler;
```
```vb
' dotnet_style_qualification_for_event = true
AddHandler Me.Elapsed, AddressOf Handler

' dotnet_style_qualification_for_event = false
AddHandler Elapsed, AddressOf Handler
```  

Estas reglas podrían aparecer en un archivo .editorconfig como sigue:  

```
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="language_keywords">Palabras clave del lenguaje en lugar de nombres de tipos de marco para referencias de tipo</a>
Esta regla de estilo se puede aplicar a variables locales, parámetros de métodos y miembros de clases, o bien como una regla independiente para escribir expresiones de acceso a miembros. Un valor **true** significa que se prefiere la palabra clave del lenguaje (como `int` o `Integer`) en lugar del nombre de tipo (por ejemplo, `Int32`) para los tipos que tienen una palabra clave para representarlos. Un valor **false** significa que se prefiere el nombre de tipo en lugar de la palabra clave del lenguaje.  

En la tabla siguiente se muestran los nombres e identificadores de las reglas, los lenguajes de programación aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:  

| Nombre de regla | Identificador de la regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión compatible |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| dotnet_style_predefined_type_for_locals_parameters_members | IDE0012 e IDE0014 | C# y Visual Basic | true:none | Visual Studio 2017 RTW |
| dotnet_style_predefined_type_for_member_access | IDE0013 e IDE0015 | C# y Visual Basic | true:none | Visual Studio 2017 RTW |  

**dotnet\_style\_predefined\_type\_for\_locals\_parameters_members**  
Cuando esta regla se establece en **true**, se prefiere la palabra clave del lenguaje para las variables locales, parámetros de métodos y miembros de clases, en lugar del nombre de tipo, para los tipos que tienen una palabra clave para representarlos.  
Cuando esta regla se establece en **false**, se prefiere el nombre de tipo para las variables locales, parámetros de métodos y miembros de clases, en lugar de la palabra clave del lenguaje.  

Ejemplos de código:  

```csharp
// dotnet_style_predefined_type_for_locals_parameters_members = true
private int _member;

// dotnet_style_predefined_type_for_locals_parameters_members = false
private Int32 _member;
```
```vb
' dotnet_style_predefined_type_for_locals_parameters_members = true
Private _member As Integer

' dotnet_style_predefined_type_for_locals_parameters_members = false
Private _member As Int32
``` 

**dotnet\_style\_predefined\_type\_for\_member_access**   
Cuando esta regla se establece en **true**, se prefiere la palabra clave del lenguaje para las expresiones de acceso a miembros, en lugar del nombre de tipo, para los tipos que tienen una palabra clave para representarlos.  
Cuando esta regla se establece en **false**, se prefiere el nombre de tipo para las expresiones de acceso a miembros, en lugar de la palabra clave del lenguaje.  

Ejemplos de código:  

```csharp
// dotnet_style_predefined_type_for_member_access = true
var local = int.MaxValue;

// dotnet_style_predefined_type_for_member_access = false
var local = Int32.MaxValue;
```
```vb
' dotnet_style_predefined_type_for_member_access = true
Dim local = Integer.MaxValue

' dotnet_style_predefined_type_for_member_access = false
Dim local = Int32.MaxValue
```  

Estas reglas podrían aparecer en un archivo .editorconfig como sigue:  

```
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
``` 

#### <a name="expression_level">Preferencias de nivel de expresión</a>  
Las reglas de estilo de esta sección definen las preferencias de nivel de expresión, incluido el uso de inicializadores de objeto, inicializadores de colección, nombres de tupla explícitos, expresiones de fusión NULL frente a operadores ternarios y el operador condicional NULL.  

En la tabla siguiente se muestran los nombres e identificadores de las reglas, los lenguajes de programación aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:  

| Nombre de regla | Identificador de la regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión compatible |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| dotnet_style_object_initializer | IDE0017 | C# y Visual Basic | true:suggestion | Visual Studio 2017 RTW |
| dotnet_style_collection_initializer | IDE0028 | C# y Visual Basic | true:suggestion | Visual Studio 2017 RTW |
| dotnet_style_explicit_tuple_names | IDE0033 | C# 7.0+ y Visual Basic 15+ | true:suggestion | Visual Studio 2017 RTW |
| dotnet_style_coalesce_expression | IDE0029 | C# y Visual Basic | true:suggestion | Visual Studio 2017 RTW |
| dotnet_style_null_propagation | IDE0031 | C# 6.0+ y Visual Basic 14+ | true:suggestion | Visual Studio 2017 RTW | 

**dotnet\_style\_object_initializer**  
Cuando esta regla se establece en **true**, se prefiere inicializar los objetos con inicializadores de objeto siempre que sea posible.  
Cuando esta regla se establece en **false**, se prefiere *no* inicializar los objetos con inicializadores de objeto.  

Ejemplos de código:  

```csharp
// dotnet_style_object_initializer = true
var c = new Customer() { Age = 21 };

// dotnet_style_object_initializer = false
var c = new Customer();
c.Age = 21;
```
```vb
' dotnet_style_object_initializer = true
Dim c = New Customer() With {.Age = 21}

' dotnet_style_object_initializer = false
Dim c = New Customer()
c.Age = 21
```

**dotnet\_style\_collection_initializer**  
Cuando esta regla se establece en **true**, se prefiere inicializar las colecciones con inicializadores de colección siempre que sea posible.  
Cuando esta regla se establece en **false**, se prefiere *no* inicializar las colecciones con inicializadores de colección.

Ejemplos de código:

```csharp
// dotnet_style_collection_initializer = true
var list = new List<int> { 1, 2, 3 };

// dotnet_style_collection_initializer = false
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);
```
```vb
' dotnet_style_collection_initializer = true
Dim list = New List(Of Integer) From {1, 2, 3}

' dotnet_style_collection_initializer = false
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)
```  

**dotnet\_style\_explicit\_tuple_names**  
Cuando esta regla se establece en **true**, se prefieren los nombres de tupla a las propiedades ItemX.  
Cuando esta regla se establece en **false**, se prefieren las propiedades ItemX a los nombres de tupla.  

Ejemplos de código:  

```csharp
// dotnet_style_explicit_tuple_names = true
(string name, int age) customer = GetCustomer();
var name = customer.name;

// dotnet_style_explicit_tuple_names = false
(string name, int age) customer = GetCustomer();
var name = customer.Item1;
```
```vb
 ' dotnet_style_explicit_tuple_names = true
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name

' dotnet_style_explicit_tuple_names = false
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1
```

**dotnet\_style\_coalesce_expression**  
Cuando esta regla se establece en **true**, se prefieren expresiones de fusión nulas a la comprobación del operador ternario.  
Cuando esta regla se establece en **false**, se prefiere la comprobación del operador ternario a las expresiones de fusión nulas.

Ejemplos de código:  

```csharp
// dotnet_style_coalesce_expression = true
var v = x ?? y;

// dotnet_style_coalesce_expression = false
var v = x != null ? x : y; // or
var v = x == null ? y : x;
```
```vb
' dotnet_style_coalesce_expression = true
Dim v = If(x, y)

' dotnet_style_coalesce_expression = false
Dim v = If(x Is Nothing, y, x) ' or
Dim v = If(x IsNot Nothing, x, y)
```

**dotnet\_style\_null_propagation**  
Cuando esta regla se establece en **true**, se prefiere usar el operador condicional NULL siempre que sea posible.  
Cuando esta regla se establece en **false**, se prefiere usar la comprobación de NULL ternario siempre que sea posible.  

Ejemplos de código:  

```csharp
// dotnet_style_null_propagation = true
var v = o?.ToString();

// dotnet_style_null_propagation = false
var v = o == null ? null : o.ToString(); // or
var v = o != null ? o.String() : null;
```
```vb
' dotnet_style_null_propagation = true
Dim v = o?.ToString()

' dotnet_style_null_propagation = false
Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or
Dim v = If(o IsNot Nothing, o.ToString(), Nothing)
```  

Estas reglas podrían aparecer en un archivo .editorconfig como sigue:  

```
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
``` 

### <a name="c-code-style-settings"></a>Configuración del estilo de código de C#  
Las reglas de estilo de esta sección solo son aplicables a C#.  

#### <a name="var">Tipos implícitos y explícitos</a>
Las reglas de estilo de esta sección (los identificadores de regla IDE0007 e IDE0008) hacen referencia al uso de la palabra clave [var](/dotnet/csharp/language-reference/keywords/var) frente a un tipo explícito en una declaración de variable. Esta regla se puede aplicar por separado a los tipos integrados, cuando el tipo es aparente, y en otros lugares.  

En esta tabla se muestran los nombres de las reglas, los lenguajes de programación aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:  

| Nombre de regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión compatible |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_style_var_for_built_in_types | C# | true:none | Visual Studio 2017 RTW |
| csharp_style_var_when_type_is_apparent | C# | true:none | Visual Studio 2017 RTW |
| csharp_style_var_elsewhere | C# | true:none | Visual Studio 2017 RTW |

**csharp\_style\_var\_for\_built\_in_types**  
Cuando esta regla se establece en **true**, se prefiere usar `var` para declarar variables con tipos de sistema integrados como `int`.  
Cuando esta regla se establece en **false** se prefiere el tipo explícito sobre `var` para declarar variables con tipos de sistema integrados como `int`.

Ejemplos de código:  

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

**csharp\_style\_var\_when\_type\_is_apparent**  
Cuando esta regla se establece en **true**, se prefiere `var` cuando el tipo ya se menciona en el lado derecho de una expresión de declaración.  
Cuando esta regla se establece en **false**, se prefiere el tipo explícito a `var` cuando el tipo ya se menciona en el lado derecho de una expresión de declaración.  

Ejemplos de código:  

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

**csharp\_style\_var_elsewhere**  
Cuando esta regla se establece en **true**, se prefiere `var` a un tipo explícito en todos los casos, a menos que se reemplace por otra regla de estilo de código.  
Cuando esta regla se establece en **false**, se prefiere el tipo explícito a `var` en todos los casos, a menos que se reemplace por otra regla de estilo de código.  

Ejemplos de código:  

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

Archivo .editorconfig de ejemplo:  

```
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
``` 

#### <a name="expression_bodied_members">Miembros con forma de expresión</a>
Las reglas de estilo de esta sección hacen referencia al uso de [miembros con forma de expresión](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members) cuando la lógica consta de una sola expresión. Esta regla se puede aplicar a métodos, constructores, operadores, propiedades, indizadores y descriptores de acceso.  

En la tabla siguiente se muestran los nombres e identificadores de las reglas, las versiones del lenguaje aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:  

| Nombre de regla | Identificador de la regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión compatible |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_style_expression_bodied_methods | IDE0022 | C# 6.0+ | false:none | Visual Studio 2017 RTW |
| csharp_style_expression_bodied_constructors | IDE0021 | C# 7.0+ | false:none | Visual Studio 2017 RTW |
| csharp_style_expression_bodied_operators | IDE0023 e IDE0024 | C# 7.0+ | false:none | Visual Studio 2017 RTW |
| csharp_style_expression_bodied_properties | IDE0025 | C# 7.0+ | true:none | Visual Studio 2017 RTW |
| csharp_style_expression_bodied_indexers | IDE0026 | C# 7.0+ | true:none | Visual Studio 2017 RTW |
| csharp_style_expression_bodied_accessors | IDE0027 | C# 7.0+ | true:none | Visual Studio 2017 RTW |  

**csharp\_style\_expression\_bodied_methods**  
Cuando esta regla se establece en **true**, se prefieren miembros con forma de expresión para los métodos.  
Cuando esta regla se establece en **false**, no se prefieren los miembros con forma de expresión para los métodos.  

Ejemplos de código:  

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```  

**csharp\_style\_expression\_bodied_constructors**  
Cuando esta regla se establece en **true**, se prefieren los miembros con forma de expresión para los constructores.  
Cuando esta regla se establece en **false**, no se prefieren los miembros con forma de expresión para los constructores.  

Ejemplos de código:  

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```  

**csharp\_style\_expression\_bodied_operators**  
Cuando esta regla se establece en **true**, se prefieren los miembros con forma de expresión para los operadores.  
Cuando esta regla se establece en **false**, no se prefieren los miembros con forma de expresión para los operadores.  

Ejemplos de código:  

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```  

**csharp\_style\_expression\_bodied_properties**  
Cuando esta regla se establece en **true**, se prefieren los miembros con forma de expresión para las propiedades.  
Cuando esta regla se establece en **false**, no se prefieren los miembros con forma de expresión para las propiedades.  

Ejemplos de código:  

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```  

**csharp\_style\_expression\_bodied_indexers**  
Cuando esta regla se establece en **true**, se prefieren los miembros con forma de expresión para los indizadores.  
Cuando esta regla se establece en **false**, no se prefieren los miembros con forma de expresión para los indizadores.  

Ejemplos de código:  

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _value[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```  

**csharp\_style\_expression\_bodied_accessors**  
Cuando esta regla se establece en **true**, se prefieren los miembros con forma de expresión para los descriptores de acceso.  
Cuando esta regla se establece en **false**, no se prefieren los miembros con forma de expresión para los descriptores de acceso.  

Ejemplos de código:  

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```  

Archivo .editorconfig de ejemplo:  

```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
csharp_style_expression_bodied_constructors = false:none
csharp_style_expression_bodied_operators = false:none
csharp_style_expression_bodied_properties = true:none
csharp_style_expression_bodied_indexers = false:none
csharp_style_expression_bodied_accessors = false:none
```  

#### <a name="pattern_matching">Coincidencia de patrones</a>
Las reglas de estilo de esta sección hacen referencia al uso de la [coincidencia de patrones](/dotnet/csharp/pattern-matching) en C#.  

En la tabla siguiente se muestran los nombres e identificadores de las reglas, las versiones del lenguaje aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:  

| Nombre de regla | Identificador de la regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión compatible |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_style_pattern_matching_over_is_with_cast_check | IDE0020 | C# 7.0+ | true:suggestion | Visual Studio 2017 RTW |
| csharp_style_pattern_matching_over_as_with_null_check | IDE0019 | C# 7.0+ | true:suggestion | Visual Studio 2017 RTW |

**csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check**  
Cuando esta regla se establece en **true**, se prefiere la coincidencia de patrones en lugar de expresiones `is` con conversiones de tipos.  
Cuando esta regla se establece en **false**, se prefieren las expresiones `is` con conversiones de tipos en lugar de la coincidencia de patrones.  

Ejemplos de código:  

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

**csharp\_style\_pattern\_matching\_over\_as\_with\_null_check**  
Cuando esta regla se establece en **true**, se prefiere la coincidencia de patrones en lugar de las expresiones `as` con comprobaciones de valores NULL para determinar si algo es de un tipo determinado.  
Cuando esta regla se establece en **false**, se prefieren las expresiones `as` con comprobaciones de valores NULL en lugar de la coincidencia de patrones para determinar si algo es de un tipo determinado.  

Ejemplos de código:  

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

Archivo .editorconfig de ejemplo:  

```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="inlined_variable_declarations">Declaraciones de variables insertadas</a>
Esta regla de estilo se aplica a si las variables `out` se declaran como alineadas o no. A partir de C# 7, puede [declarar una variable de salida en la lista de argumentos de la llamada al método](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument), en lugar de en una declaración de variable independiente.  

En la tabla siguiente se muestran el nombre e identificador de la regla, las versiones del lenguaje aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:  

| Nombre de regla | Identificador de la regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión compatible |
| --------- | -------- | -------------------- | ----------------------| ----------------  |
| csharp_style_inlined_variable_declaration | IDE0018 | C# 7.0+ | true:suggestion | Visual Studio 2017 RTW |

**csharp\_style\_inlined\_variable_declaration**  
Cuando esta regla se establece en **true**, se prefiere que las variables `out` se declaren como alineadas en la lista de argumentos de una llamada de método, siempre que sea posible.  
Cuando esta regla se establece en **false**, se prefiere que las variables `out` se declaren antes de la llamada de método.  

Ejemplos de código:  

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = fale
int i;
if (int.TryParse(value, out i) {...}
```

Archivo .editorconfig de ejemplo:  

```
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

#### <a name="expression_level_csharp">Preferencias de nivel de expresión</a>
Esta regla de estilo se aplica al uso del [literal `default` para las expresiones de valor predeterminado](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference) cuando el compilador puede deducir el tipo de la expresión.  

En la tabla siguiente se muestran el nombre e identificador de la regla, las versiones del lenguaje aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:  

| Nombre de regla | Identificador de la regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión compatible |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_prefer_simple_default_expression | IDE0034 | C# 7.1+ | true:suggestion | Visual Studio 2017 v. 15.3 |

**csharp\_prefer\_simple\_default_expression**  
Cuando esta regla se establece en **true**, se prefiere `default` a `default(T)`.  
Cuando esta regla se establece en **false**, se prefiere `default(T)` a `default`.  

Ejemplos de código:  

```csharp 
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

Archivo .editorconfig de ejemplo:  

```
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
``` 

#### <a name="null_checking">Preferencias de la comprobación de "NULL"</a>
Estas reglas de estilo están relacionadas con la sintaxis de la comprobación de `null`, incluido el uso de expresiones `throw` o instrucciones `throw`, y si se realiza una comprobación de NULL o se usa el operador de incorporación condicional (`?.`) al invocar una [expresión lambda](/dotnet/csharp/lambda-expressions).  

En la tabla siguiente se muestran los nombres e identificadores de las reglas, las versiones del lenguaje aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:  

| Nombre de regla | Identificador de la regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión compatible |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_style_throw_expression | IDE0016 | C# 7.0+ | true:suggestion | Visual Studio 2017 RTW |
| csharp_style_conditional_delegate_call | IDE0041 | C# 6.0+ | true:suggestion | Visual Studio 2017 RTW |

**csharp\_style\_throw_expression**  
Cuando esta regla se establece en **true**, se prefiere el uso de expresiones `throw` en lugar de instrucciones `throw`.  
Cuando esta regla se establece en **false**, se prefiere el uso de expresiones `throw` en lugar de instrucciones `throw`.  

Ejemplos de código:  

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

**csharp\_style\_conditional\_delegate_call**   
Cuando esta regla se establece en **true**, es preferible usar el operador de incorporación condicional (`?.`) al invocar una expresión lambda, en lugar de realizar una comprobación de NULL.  
Cuando esta regla se establece en **false**, se prefiere realizar una comprobación de NULL antes de invocar una expresión lambda, en lugar de usar el operador de incorporación condicional (`?.`).  

Ejemplos de código:  

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

Archivo .editorconfig de ejemplo:  

```
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestions:
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="code_block">Preferencias de bloques de código</a>
Esta regla de estilo se refiere al uso de llaves `{ }` para delimitar los bloques de código.  

En la tabla siguiente se muestran el nombre e identificador de la regla, las versiones del lenguaje aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:  

| Nombre de regla | Identificador de la regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión compatible |
| --------- | ------- | -------------------- | ----------------------| ----------------  |
| csharp_prefer_braces | IDE0011 | C# | true:none | Visual Studio 2017 v. 15.3 |

**csharp\_prefer\_braces**   
Cuando esta regla se establece en **true**, se prefieren las llaves incluso para una línea de código.  
Cuando esta regla se establece en **false**, se prefiere que no se usen llaves, si está permitido.  

Ejemplos de código:  

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

Archivo .editorconfig de ejemplo:  

```
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:none
```

## <a name="formatting-conventions"></a>Convenciones de formato
La mayoría de las reglas de convenciones de formato tienen el formato siguiente:  

`rule_name = false|true`  

Se especifica **true** (se prefiere este estilo) o **false** (no se prefiere este estilo). No se especifica un nivel de gravedad. Para algunas reglas, en lugar de true o false, se especifican otros valores para describir cuándo y dónde se va a aplicar la regla.  

En la lista siguiente se muestran las reglas de convención de formato disponibles en Visual Studio:  

- Configuración de formato de .NET
    - [Organización de instrucciones Using](#usings)
        - dotnet_sort_system_directives_first
- Configuración de formato de C#
    - [Opciones de nueva línea](#newline)
        - csharp_new_line_before_open_brace
        - csharp_new_line_before_else
        - csharp_new_line_before_catch
        - csharp_new_line_before_finally
        - csharp_new_line_before_members_in_object_initializers
        - csharp_new_line_before_members_in_anonymous_types
        - csharp_new_line_between_query_expression_clauses
    - [Opciones de sangría](#indent)
        - csharp_indent_case_contents
        - csharp_indent_switch_labels
        - csharp_indent_labels
    - [Opciones de espaciado](#spacing)
        - csharp_space_after_cast
        - csharp_space_after_keywords_in_control_flow_statements
        - csharp_space_between_method_declaration_parameter_list_parentheses
        - csharp_space_between_method_call_parameter_list_parentheses
        - csharp_space_between_parentheses
    - [Opciones de ajuste](#wrapping)
        - csharp_preserve_single_line_statements
        - csharp_preserve_single_line_blocks

### <a name="net-formatting-settings"></a>Configuración de formato de .NET
Las reglas de formato de esta sección son aplicables a C# y Visual Basic.  

#### <a name="usings">Organización de instrucciones Using</a>
Esta regla de formato se refiere a la ubicación de directivas using con System.*, con respecto a otras directivas using.  

En la tabla siguiente se muestra el nombre de la regla, los lenguajes aplicables, el valor predeterminado y la primera versión compatible de Visual Studio:  

| Nombre de regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión compatible |
| ----------- | -------------------- | ----------------------| ----------------  |
| dotnet_sort_system_directives_first |  C# y Visual Basic | true | Visual Studio 2017 v. 15.3  |

**dotnet\_sort\_system\_directives_first**  
Cuando esta regla se establece en **true**, las directivas using System.* se ordenan alfabéticamente y se colocan delante de otras directivas using.  
Cuando esta regla se establece en **false**, las directivas using System.* no se colocan delante de otras directivas using.  

Ejemplos de código:  

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

Archivo .editorconfig de ejemplo:  

```
# .NET formatting settings:
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
``` 

### <a name="csharp_formatting">Configuración de formato de C#</a>  
Las reglas de formato de esta sección se aplican únicamente al código de C#.  

#### <a name="newline">Opciones de nueva línea</a>  
Estas reglas de formato se refieren al uso de nuevas líneas para dar formato al código.  

En la tabla siguiente se muestran los nombres de las reglas de "nueva línea", los lenguajes aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:  

| Nombre de regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión compatible |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_new_line_before_open_brace |  C# | todo | Visual Studio 2017 v. 15.3  |
| csharp_new_line_before_else |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_new_line_before_catch |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_new_line_before_finally |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_new_line_before_members_in_object_initializers |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_new_line_before_members_in_anonymous_types |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_new_line_between_query_expression_clauses |  C# | true | Visual Studio 2017 v. 15.3  |

**csharp\_new\_line\_before\_open_brace**  
Esta regla se refiere a si se debe colocar una llave de apertura `{` en la misma línea que el código anterior, o en una línea nueva. Para esta regla, no se especifica **true** ni **false**. En su lugar, se especifica **all**, **none** o uno o varios elementos de código como **methods** o **properties**, para definir cuándo se debe aplicar esta regla. La lista completa de los valores permitidos se muestra en la tabla siguiente:  

| Valor | Descripción 
| ------------- |:-------------|
| descriptores de acceso, métodos_anónimos, tipos_anónimos, bloques_control, eventos, indexadores, lambdas, funciones_locales, métodos, colección_objetos, propiedades, tipos.<br>(Si hay varios tipos, sepárelos con comas ","). | Es obligatorio que las llaves estén en una línea nueva para los elementos de código especificados (también conocido como estilo "Allman") |
| todo | Es obligatorio que las llaves estén en una nueva línea para todas las expresiones (estilo "Allman") |
| ninguna | Es obligatorio que las llaves estén en una nueva línea para todas las expresiones ("K&R") |

Ejemplos de código:  

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod() 
{
    if (...) 
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

**csharp\_new\_line\_before_else**  
Cuando esta regla se establece en **true**, las instrucciones `else` se colocan en una línea nueva.  
Cuando esta regla se establece en **false**, las instrucciones `else` se colocan en la misma línea.  

Ejemplos de código:  

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

**csharp\_new\_line\_before_catch**    
Cuando esta regla se establece en **true**, las instrucciones `catch` se colocan en una línea nueva.  
Cuando esta regla se establece en **false**, las instrucciones `catch` se colocan en la misma línea.  

Ejemplos de código:  

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

**csharp\_new\_line\_before_finally**      
Cuando esta regla se establece en **true**, es obligatorio que las instrucciones `finally` estén en una nueva línea después de la llave de cierre.  
Cuando esta regla se establece en **false**, es obligatorio que las instrucciones `finally` estén en la misma línea que la llave de cierre.  

Ejemplos de código:  

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

**csharp\_new\_line\_before\_members\_in\_object_initializers**       
Cuando esta regla se establece en **true**, es obligatorio que los miembros de inicializadores de objeto estén en líneas independientes.  
Cuando esta regla se establece en **false**, es obligatorio que los miembros de inicializadores de objeto estén en la misma línea.  

Ejemplos de código:  

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

**csharp\_new\_line\_before\_members\_in\_anonymous_types**       
Cuando esta regla se establece en **true**, es obligatorio que los miembros de tipos anónimos estén en líneas independientes.  
Cuando esta regla se establece en **false**, es obligatorio que los miembros de tipos anónimos estén en la misma línea.  

Ejemplos de código:  

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

**csharp_new_line_between_query_expression_clauses**       
Cuando esta regla se establece en **true**, es obligatorio que los elementos de cláusulas de expresión de consulta estén en líneas independientes.  
Cuando esta regla se establece en **false**, es obligatorio que los elementos de cláusulas de expresión de consulta estén en la misma línea.  

Ejemplos de código:  

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

Archivo .editorconfig de ejemplo:  

```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
``` 

#### <a name="indent">Opciones de sangría</a>  
Estas reglas de formato se refieren al uso de la sangría para dar formato al código.  

En la tabla siguiente se muestran los nombres de las reglas, los lenguajes aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:  

| Nombre de regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión compatible |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_indent_case_contents |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_indent_switch_labels |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_indent_labels |  C# | no_change | Visual Studio 2017 v. 15.3  |

**csharp\_indent\_case_contents**  
Cuando esta regla se establece en **true**, se aplica sangría al contenido de los casos `switch`.  
Cuando esta regla se establece en **false**, no se aplica sangría al contenido de los casos `switch`.  

Ejemplos de código:  

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**csharp\_indent\_switch_labels**  
Cuando esta regla se establece en **true**, se aplica sangría a las etiquetas `switch`.  
Cuando esta regla se establece en **false**, no se aplica sangría a las etiquetas `switch`.  

Ejemplos de código:  

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**csharp\_indent_labels**  
Esta regla no acepta un valor **true** o **false**; en su lugar, acepta un valor de la tabla siguiente:  

| Valor | Descripción |
| ----- |:----------- |
| flush_left | Las etiquetas se colocan en la primera columna de la izquierda |
| one_less_than_current | Las etiquetas se colocan una sangría menos que el contexto actual. |
| no_change | Las etiquetas se colocan en la misma sangría que el contexto actual. |

Ejemplos de código:  

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...) 
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...) 
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...) 
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

Archivo .editorconfig de ejemplo:  

```
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
``` 

#### <a name="spacing">Opciones de espaciado</a>  
Estas reglas de formato se refieren al uso de caracteres de espacio para dar formato al código.  

En la tabla siguiente se muestran los nombres de las reglas, los lenguajes aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:  

| Nombre de regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión compatible |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_space_after_cast |  C# | False | Visual Studio 2017 v. 15.3  |
| csharp_space_after_keywords_in_control_flow_statements |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_space_between_method_declaration_parameter_list_parentheses |  C# | False | Visual Studio 2017 v. 15.3  |
| csharp_space_between_method_call_parameter_list_parentheses |  C# | False | Visual Studio 2017 v. 15.3  |
| csharp_space_between_parentheses |  C# | False | Visual Studio 2017 v. 15.3  |

**csharp\_space\_after_cast**  
Cuando esta regla se establece en **true**, se requiere un espacio entre una conversión y el valor.  
Cuando esta regla se establece en **false**, _no_ se requiere un espacio entre la conversión y el valor.  

Ejemplos de código:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

**csharp_space_after_keywords_in_control_flow_statements**  
Cuando esta regla se establece en **true**, se requiere un espacio después de una palabra clave en una instrucción de flujo de control como un bucle `for`.  
Cuando esta regla se establece en **false**, _no_ se requiere un espacio después de una palabra clave en una instrucción de flujo de control como un bucle `for`.  

Ejemplos de código:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

**csharp_space_between_method_declaration_parameter_list_parentheses**  
Cuando esta regla se establece en **true**, se coloca un carácter de espacio después del paréntesis de apertura y antes del paréntesis de cierre de una lista de parámetros de declaración de método.  
Cuando esta regla se establece en **false**, no se colocan caracteres de espacio después del paréntesis de apertura y antes del paréntesis de cierre de una lista de parámetros de declaración de método.  

Ejemplos de código:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

**csharp_space_between_method_call_parameter_list_parentheses**  
Cuando esta regla se establece en **true**, se coloca un carácter de espacio después del paréntesis de apertura y antes del paréntesis de cierre de una llamada de método.  
Cuando esta regla se establece en **false**, no se colocan caracteres de espacio después del paréntesis de apertura y antes del paréntesis de cierre de una llamada de método.  

Ejemplos de código:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

**csharp_space_between_parentheses**  
Esta regla no acepta un valor **true** o **false**; en su lugar, acepta un valor de la tabla siguiente:  

| Valor | Descripción |
| ----- |:------------|
| control_flow_statements | Se inserta un espacio entre los paréntesis de instrucciones de flujo de control. |
| expresiones | Se inserta un espacio entre los paréntesis de expresiones. |
| type_casts | Se inserta un espacio entre los paréntesis de las conversiones de tipos. |

Ejemplos de código:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for( int i;i<x;i++ ) { ... }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3);

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

Archivo .editorconfig de ejemplo:  

```
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_parentheses = control_flow_statements, type_casts
``` 

#### <a name="wrapping">Opciones de ajuste</a>
Estas reglas de formato se refieren al uso de líneas individuales frente a líneas separadas para las instrucciones y bloques de código.  

En la tabla siguiente se muestran los nombres de las reglas, los lenguajes aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:  

| Nombre de regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión compatible |
| ----------- | -------------------- | ----------------------| ----------------  |
| csharp_preserve_single_line_statements |  C# | true | Visual Studio 2017 v. 15.3  |
| csharp_preserve_single_line_blocks |  C# | true | Visual Studio 2017 v. 15.3  |

**csharp_preserve_single_line_statements**   
Cuando esta regla se establece en **true**, las instrucciones y declaraciones de miembros se dejan en la misma línea.  
Cuando esta regla se establece en **false**, las instrucciones y declaraciones de miembros se dejan en líneas diferentes.  

Ejemplos de código:  

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0; 
string name = "John";
```

**csharp_preserve_single_line_blocks**  
Cuando esta regla se establece en **true**, el bloque de código se deja en una sola línea.  
Cuando esta regla se establece en **false**, el bloque de código se deja en líneas separadas.  

Ejemplos de código:  

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{ 
    get; set;
}
```

Archivo .editorconfig de ejemplo:  

```
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

## <a name="naming-conventions"></a>Convenciones de nomenclatura  
Las convenciones de nomenclatura están relacionadas con los nombres de elementos de código como clases, propiedades y métodos. Por ejemplo, puede especificar que los métodos asincrónicos deben terminar en "Async". Las convenciones de nomenclatura deben ordenarse de la más específica a la menos específica. La primera regla encontrada que se puede aplicar es la única que se aplica.  

Para cada regla de convención de nomenclatura, identificada por **namingRuleTitle**, debe especificar los **símbolos** a los que se aplica, un **estilo** de nomenclatura y una **gravedad**:  
  
`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`  
`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`  
`dotnet_naming_rule.<namingRuleTitle>.severity = none|suggestion|warning|error`  

### <a name="symbols"></a>Símbolos
Identifique un grupo de símbolos a los que aplicar una regla de nomenclatura con esta propiedad: `dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`. Especifique el tipo de símbolos, los modificadores y niveles de accesibilidad que se incluyen en el grupo con las propiedades siguientes:  

| Propiedad | Valores posibles |
| ------------- |:-------------:|
| dotnet\_naming\_symbols.\<symbolTitle\>.applicable\_kinds | *, class, struct, interface, enum, property, method, field, event, namespace, delegate, type_parameter |
| dotnet\_naming\_symbols.\<symbolTitle\>.applicable_accessibilities | *, public, internal (C#), friend (Visual Basic), private, protected, protected\_internal (C#), protected\_friend (Visual Basic) |
| dotnet\_naming\_symbols.\<symbolTitle\>.required\_modifiers | abstract (C#), must_inherit (Visual Basic), async, const, readonly, static (C#), shared (Visual Basic) |  

### <a name="style"></a>Estilo
Identifique el estilo de nomenclatura para aplicar a un grupo de símbolos con esta propiedad: `dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`.  

Especifique el estilo de nomenclatura mediante una o más de las propiedades siguientes:  

|  Propiedad | Valores posibles |
| ------------- |:-------------:|
| dotnet_naming_style.\<styleTitle\>.required_prefix | Caracteres requeridos que deben aparecer al inicio del identificador. |  
| dotnet_naming_style.\<styleTitle\>.required_suffix | Caracteres requeridos que deben aparecer al final del identificador. |  
| dotnet_naming_style.\<styleTitle\>.word_separator | Carácter requerido entre las palabras en el identificador. | 
| dotnet_naming_style.\<styleTitle\>.capitalization | pascal_case, camel_case, first_word_upper, all_upper, all_lower |

> [!NOTE]
> Debe especificar un estilo de mayúsculas y minúsculas como parte del estilo de nomenclatura; en caso contrario, el estilo de nomenclatura se ignorará.  

#### <a name="severity"></a>Gravedad
Identifique el nivel de gravedad de una regla de nomenclatura con esta propiedad: `dotnet_naming_rule.<namingRuleTitle>.severity`.  

En la tabla siguiente se muestran las opciones de valor de gravedad:  

Gravedad | Efecto
------------ | -------------
Ninguna o silenciosa | Cuando no se sigue este estilo, no se muestra nada al usuario, pero las características de generación de código generan el código nuevo en este estilo.  
suggestion | Cuando este estilo no se sigue, se muestra al usuario como una sugerencia (puntos subyacentes en los dos primeros caracteres). No tiene ningún efecto en tiempo de compilación.  
warning | Cuando este estilo no se sigue, se muestra una advertencia del compilador.  
error | Cuando este estilo no se sigue, se muestra un error del compilador.   

### <a name="example-editorconfig-file-with-naming-conventions"></a>Archivo de ejemplo .editorconfig con convenciones de nomenclatura
```
# Dotnet Naming Conventions
[*.{cs,vb}] 
dotnet_naming_rule.async_methods_end_in_async.symbols  = any_async_methods
dotnet_naming_rule.async_methods_end_in_async.style    = end_in_async
dotnet_naming_rule.async_methods_end_in_async.severity = suggestion

dotnet_naming_symbols.any_async_methods.applicable_kinds           = method
dotnet_naming_symbols.any_async_methods.applicable_accessibilities = *
dotnet_naming_symbols.any_async_methods.required_modifiers         = async

dotnet_naming_style.end_in_async.required_suffix = Async
dotnet_naming_style.end_in_async.capitalization  = pascal_case
``` 

## <a name="see-also"></a>Vea también
[Acciones rápidas](../ide/quick-actions.md)  
[Crear opciones del editor personalizadas y portátiles](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options)  
[Archivo .editorconfig de la plataforma de compilación .NET](https://github.com/dotnet/roslyn/blob/master/.editorconfig)  

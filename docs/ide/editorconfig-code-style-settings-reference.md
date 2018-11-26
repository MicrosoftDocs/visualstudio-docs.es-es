---
title: Configuración de la convención de codificación de .NET para EditorConfig
ms.date: 06/14/2018
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- coding conventions [EditorConfig]
- EditorConfig coding conventions
- language code style rules [EditorConfig]
- formatting conventions [EditorConfig]
author: kuhlenh
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a54a3d6b967e7652c25e24922d7bd3b49141cc17
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769753"
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>Configuración de la convención de codificación de .NET para EditorConfig

En Visual Studio 2017, se puede definir y mantener un estilo de código coherente en el código base con el uso de un archivo [EditorConfig](../ide/create-portable-custom-editor-options.md). EditorConfig incluye varias propiedades de formato básicas, como `indent_style` e `indent_size`. En Visual Studio, las convenciones de codificación de .NET también se pueden configurar mediante un archivo EditorConfig. Los archivos EditorConfig permiten habilitar o deshabilitar las convenciones de codificación individuales de .NET y configurar el grado en el que quiere que se aplique la convención mediante un nivel de gravedad. Para más información sobre cómo usar EditorConfig para aplicar la coherencia en el código base, lea [Crear opciones de configuración del editor personalizadas y portátiles](../ide/create-portable-custom-editor-options.md).

En la parte final de este artículo encontrará un [archivo .editorconfig de ejemplo](#example-editorconfig-file).

## <a name="convention-categories"></a>Categorías de convención

Hay tres categorías de convención de codificación de .NET admitidas:

- [Estilos de código de idioma](#language-code-styles)

   Reglas relativas al lenguaje C# o Visual Basic. Por ejemplo, puede especificar reglas sobre el uso de `var` o tipos explícitos en la definición de variables o la preferencia por miembros con forma de expresión.

- [Convenciones de formato](#formatting-conventions)

   Reglas sobre el diseño y la estructura del código para que sea más fácil de leer. Por ejemplo, puede especificar reglas sobre las llaves Allman o preferir espacios en los bloques de control.

- [Convenciones de nomenclatura](../ide/editorconfig-naming-conventions.md)

   Reglas relacionadas con los nombres de los elementos de código. Por ejemplo, puede especificar que los métodos `async` deben terminar en "Async".

## <a name="language-code-styles"></a>Estilos de código de idioma

Las reglas para los estilos de código de idioma tienen el siguiente formato:

`options_name = false|true : none|silent|suggestion|warning|error`

Para cada estilo de código de idioma, debe especificar **true** (se prefiere este estilo) o **false** (no se prefiere este estilo), y la **gravedad**. La gravedad especifica el nivel de cumplimiento para ese estilo.

En la tabla siguiente se enumeran los valores de gravedad posibles y sus efectos:

Gravedad | Efecto
:------- | ------
`none` | No mostrar nada al usuario cuando se infringe esta regla. Pero las características de generación de código generan código con este estilo. Las reglas con gravedad `none` nunca aparecen en el menú **Acciones rápidas y refactorizaciones**. En la mayoría de casos, el valor se considera "deshabilitado" o "omitido".
`silent` (también `refactoring` en Visual Studio 2017 versión 15.8) | No mostrar nada al usuario cuando se infringe esta regla. Pero las características de generación de código generan código con este estilo. Las reglas con gravedad `silent` participan en la limpieza y, además, aparecen en el menú **Acciones rápidas y refactorizaciones**.
`suggestion` | Cuando se infringe esta regla de estilo, se muestra al usuario como una sugerencia. Las sugerencias aparecen como tres puntos de color gris en los dos primeros caracteres.
`warning` | Cuando se infringe esta regla de estilo, se muestra una advertencia del compilador.
`error` | Cuando se infringe esta regla de estilo, se muestra un error del compilador.

En la siguiente lista se muestra la configuración de estilo de código de idioma permitida:

- Configuración del estilo de código de .NET
    - [Los calificadores "This." y "Me."](#this_and_me)
        - dotnet\_style\_qualification\_for_field
        - dotnet\_style\_qualification\_for_property
        - dotnet\_style\_qualification\_for_method
        - dotnet\_style\_qualification\_for_event
    - [Palabras clave del lenguaje en lugar de nombres de tipos de marco para referencias de tipo](#language_keywords)
        - dotnet\_style\_predefined\_type\_for\_locals\_parameters_members
        - dotnet\_style\_predefined\_type\_for\_member_access
    - [Preferencias de modificadores](#normalize_modifiers)
        - dotnet\_style\_require\_accessibility_modifiers
        - csharp\_preferred\_modifier_order
        - visual\_basic\_preferred\_modifier_order
        - dotnet\_style\_readonly\_field
    - [Preferencias de paréntesis](#parentheses)
        - dotnet\_style\_parentheses\_in\_arithmetic\_binary\_operators
        - dotnet\_style\_parentheses\_in\_other\_binary\_operators
        - dotnet\_style\_parentheses\_in\_other\_operators
        - dotnet\_style\_parentheses\_in\_relational\_binary\_operators
    - [Preferencias de nivel de expresión](#expression_level)
        - dotnet\_style\_object_initializer
        - dotnet\_style\_collection_initializer
        - dotnet\_style\_explicit\_tuple_names
        - dotnet\_style\_prefer\_inferred\_tuple_names
        - dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names
        - dotnet\_style\_prefer\_auto\_properties
        - dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method
        - dotnet\_style\_prefer\_conditional\_expression\_over\_assignment
        - dotnet\_style\_prefer\_conditional\_expression\_over\_return
    - [Preferencias de la comprobación de "NULL"](#null_checking)
        - dotnet\_style\_coalesce_expression
        - dotnet\_style\_null_propagation
- Configuración del estilo de código de C#
    - [Tipos implícitos y explícitos](#implicit-and-explicit-types)
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
        - csharp\_style\_deconstructed\_variable_declaration
        - csharp\_style\_pattern\_local\_over\_anonymous_function
    - [Preferencias de la comprobación de "NULL"](#null_checking_csharp)
        - csharp\_style\_throw_expression
        - csharp\_style\_conditional\_delegate_call
    - [Preferencias de bloques de código](#code_block)
        - csharp\_prefer_braces

### <a name="net-code-style-settings"></a>Configuración del estilo de código de .NET

Las reglas de estilo de esta sección son aplicables a C# y Visual Basic. Para ver ejemplos de código en el lenguaje de programación preferido, elíjalo en el menú desplegable **Lenguaje** en la esquina superior derecha de la ventana del explorador.

#### Calificadores <a name="this_and_me"></a>"This." y "Me."

Esta regla de estilo (los identificadores de regla IDE0003 e IDE0009) se puede aplicar a campos, propiedades, métodos o eventos. Un valor **true** significa que prefiere que el símbolo de código esté precedido por `this.` en C# o `Me.` en Visual Basic. Un valor **false** significa que prefiere que el elemento de código _no_ esté precedido por `this.` o `Me.`.

En esta tabla se muestran los nombres de las reglas, los lenguajes de programación aplicables y los valores predeterminados:

| Nombre de regla | Lenguajes aplicables | Valor predeterminado de Visual Studio |
| ----------- | -------------------- | ----------------------|
| dotnet_style_qualification_for_field | C# y Visual Basic | false:none |
| dotnet_style_qualification_for_property | C# y Visual Basic | false:none |
| dotnet_style_qualification_for_method | C# y Visual Basic | false:none |
| dotnet_style_qualification_for_event | C# y Visual Basic | false:none |

**dotnet\_style\_qualification\_for_field**

- Cuando esta regla se establece en **true**, se prefiere que los campos estén precedidos por `this.` en C# o `Me.` en Visual Basic.
- Cuando esta regla se establece en **false**, se prefiere que los campos _no_ estén precedidos por `this.` o `Me.`.

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

- Cuando esta regla se establece en **true**, se prefiere que las propiedades estén precedidas de `this.` en C# o `Me.` en Visual Basic.
- Cuando esta regla se establece en **false**, se prefiere que las propiedades _no_ estén precedidas de `this.` o `Me.`.

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

- Cuando esta regla se establece en **true**, se prefiere que los métodos estén precedidos de `this.` en C# o `Me.` en Visual Basic.
- Cuando esta regla se establece en **false**, se prefiere que los métodos _no_ estén precedidos de `this.` o `Me.`.

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

- Cuando esta regla se establece en **true**, se prefiere que los eventos estén precedidos de `this.` en C# o `Me.` en Visual Basic.
- Cuando esta regla se establece en **false**, se prefiere que los eventos _no_ estén precedidos de `this.` o `Me.`.

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

Estas reglas podrían aparecer en un archivo *.editorconfig* como sigue:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="language_keywords"></a>Palabras clave del lenguaje en lugar de nombres de tipos de marco para referencias de tipo

Esta regla de estilo se puede aplicar a variables locales, parámetros de métodos y miembros de clases, o bien como una regla independiente para escribir expresiones de acceso a miembros. Un valor **true** significa que se prefiere la palabra clave del lenguaje (por ejemplo, `int` o `Integer`) en lugar del nombre de tipo (por ejemplo, `Int32`) para los tipos que tienen una palabra clave para representarlos. Un valor **false** significa que se prefiere el nombre de tipo en lugar de la palabra clave del lenguaje.

En esta tabla se muestran los nombres de las reglas, los identificadores de reglas, los lenguajes de programación aplicables y los valores predeterminados:

| Nombre de regla | Identificador de la regla | Lenguajes aplicables | Valor predeterminado de Visual Studio |
| --------- | ------- | -------------------- | ----------------------|
| dotnet_style_predefined_type_for_locals_parameters_members | IDE0012 e IDE0014 | C# y Visual Basic | true:none |
| dotnet_style_predefined_type_for_member_access | IDE0013 e IDE0015 | C# y Visual Basic | true:none |

**dotnet\_style\_predefined\_type\_for\_locals\_parameters_members**

- Cuando esta regla se establece en **true**, se prefiere la palabra clave del lenguaje para las variables locales, parámetros de métodos y miembros de clases, en lugar del nombre de tipo, para los tipos que tienen una palabra clave para representarlos.
- Cuando esta regla se establece en **false**, se prefiere el nombre de tipo para las variables locales, parámetros de métodos y miembros de clases, en lugar de la palabra clave del lenguaje.

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

- Cuando esta regla se establece en **true**, se prefiere la palabra clave del lenguaje para las expresiones de acceso a miembros, en lugar del nombre de tipo, para los tipos que tienen una palabra clave para representarlos.
- Cuando esta regla se establece en **false**, se prefiere el nombre de tipo para las expresiones de acceso a miembros, en lugar de la palabra clave del lenguaje.

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

Estas reglas podrían aparecer en un archivo *.editorconfig* como sigue:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="normalize_modifiers"></a>Preferencias de modificadores

Las reglas de estilo de esta sección hacen referencia a las preferencias de modificadores, incluida la necesidad de modificadores de accesibilidad, la especificación del criterio de ordenación deseado de los modificadores y la necesidad del modificador de solo lectura.

En la tabla siguiente se muestran los nombres e identificadores de las reglas, los lenguajes de programación aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:

| Nombre de regla | Identificador de la regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión de Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| dotnet_style_require_accessibility_modifiers | IDE0040 | C# y Visual Basic | for_non_interface_members:none | 15.5 |
| csharp_preferred_modifier_order | IDE0036 | C# | public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:none | 15.5 |
| visual_basic_preferred_modifier_order | IDE0036 | Visual Basic | Partial, Default, Private, Protected, Public, Friend, NotOverridable, Overridable, MustOverride, Overloads, Overrides, MustInherit, NotInheritable, Static, Shared, Shadows, ReadOnly, WriteOnly, Dim, Const,WithEvents, Widening, Narrowing, Custom, Async:none | 15.5 |
| dotnet_style_readonly_field | IDE0044 | C# y Visual Basic | true:suggestion | 15.7 |

**dotnet\_style\_require\_accessibility_modifiers**

Esta regla no acepta un valor **true** o **false**; en su lugar, acepta un valor de la tabla siguiente:

| Valor | Descripción |
| ----- |:----------- |
| always | Prefiere que los modificadores de accesibilidad se especifiquen. |
| for\_non\_interface_members | Prefiere que los modificadores de accesibilidad se declaren, excepto para los miembros de la interfaz pública. Esto equivale a **always** y se ha agregado para las pruebas futuras si C# agrega métodos de interfaz predeterminados. |
| never | No se prefiere que se especifiquen los modificadores de accesibilidad |

Ejemplos de código:

```csharp
// dotnet_style_require_accessibility_modifiers = always
// dotnet_style_require_accessibility_modifiers = for_non_interface_members
class MyClass
{
    private const string thisFieldIsConst = "constant";
}

// dotnet_style_require_accessibility_modifiers = never
class MyClass
{
    const string thisFieldIsConst = "constant";
}
```

**csharp_preferred_modifier_order**

- Cuando esta regla esté establecida en una lista de modificadores, prefiere el orden especificado.
- Cuando esta regla se omite del archivo, no se prefiere un orden de modificador.

Ejemplos de código:

```csharp
// csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async
class MyClass
{
    private static readonly int _daysInYear = 365;
}
```

**visual_basic_preferred_modifier_order**

- Cuando esta regla esté establecida en una lista de modificadores, prefiere el orden especificado.
- Cuando esta regla se omite del archivo, no se prefiere un orden de modificador.

Ejemplos de código:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

**dotnet_style_readonly_field**

- Cuando esta regla se establece en **true**, es preferible marcar los campos con `readonly` (C#) o `ReadOnly` (Visual Basic) si solo se van a asignar en línea, o dentro de un constructor.
- Cuando esta regla se establece en **false**, no se especifica ninguna preferencia sobre si los campos se deben marcar con `readonly` (C#) o `ReadOnly` (Visual Basic).

Ejemplos de código:

```csharp
// dotnet_style_readonly_field = true
class MyClass
{
    private readonly int _daysInYear = 365;
}
```

```vb
' dotnet_style_readonly_field = true
Public Class MyClass
    Private ReadOnly daysInYear As Int = 365
End Class
```

Estas reglas podrían aparecer en un archivo *.editorconfig* como sigue:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_require_accessibility_modifiers = always:suggestion
dotnet_style_readonly_field = true:warning

# CSharp code style settings:
[*.cs]
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Visual Basic code style settings:
[*.vb]
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

#### <a name="parentheses"></a>Preferencias de paréntesis

Las reglas de estilo de esta sección se refieren a las preferencias de paréntesis, e incluyen el uso de paréntesis para operadores de aritmética, relacionales y otros operadores binarios.

En la tabla siguiente se muestran los nombres e identificadores de las reglas, los lenguajes de programación aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:

| Nombre de regla | Identificador de la regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión de Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_parentheses_in_arithmetic_binary_operators | IDE0047 | C# y Visual Basic | always_for_clarity:none | 15.8 |
| dotnet_style_parentheses_in_relational_binary_operators | IDE0047 | C# y Visual Basic | always_for_clarity:none | 15.8 |
| dotnet_style_parentheses_in_other_binary_operators | IDE0047 | C# y Visual Basic | always_for_clarity:none | 15.8 |
| dotnet_style_parentheses_in_other_operators | IDE0047 | C# y Visual Basic | never_if_unnecessary:none | 15.8 |

**dotnet\_style\_parentheses\_in\_arithmetic\_binary_operators**

- Cuando esta regla se establece en **always_for_clarity**, se prefieren paréntesis para clarificar la prioridad del operador aritmético (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`).
- Cuando esta regla se establece en **never_if_unnecessary**, se prefiere no tener paréntesis cuando la prioridad del operador aritmético (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) es obvia.

Ejemplos de código:

```csharp
// dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
var v = a + (b * c);

// dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
var v = a + b * c;
```

```vb
' dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
Dim v = a + (b * c)

' dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
Dim v = a + b * c
```

**dotnet\_style\_parentheses\_in\_relational\_binary_operators**

- Cuando esta regla se establece en **always_for_clarity**, se prefieren paréntesis para clarificar la prioridad del operador aritmético (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`).
- Cuando esta regla se establece en **never_if_unnecessary**, se prefiere no tener paréntesis cuando la prioridad del operador aritmético (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) es obvia.

Ejemplos de código:

```csharp
// dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
var v = (a < b) == (c > d);

// dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
var v = a < b == c > d;
```

```vb
' dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
Dim v = (a < b) = (c > d)

' dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
Dim v = a < b = c > d
```

**dotnet\_style\_parentheses\_in\_other\_binary_operators**

- Cuando esta regla se establece en **always_for_clarity**, se prefieren paréntesis para clarificar la prioridad de otro operador binario (`&&`, `||`, `??`).
- Cuando esta regla se establece en **never_if_unnecessary**, se prefiere no tener paréntesis cuando la prioridad de otro operador binario (`&&`, `||`, `??`) es obvia.

Ejemplos de código:

```csharp
// dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
var v = a || (b && c);

// dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
var v = a || b && c;
```

```vb
' dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
Dim v = a OrElse (b AndAlso c)

' dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
Dim v = a OrElse b AndAlso c
```

**dotnet\_style\_parentheses\_in\_other_operators**

- Cuando esta regla se establece en **always_for_clarity**, se prefieren paréntesis para clarificar la prioridad del operador.
- Cuando esta regla se establece en **never_if_unnecessary**, se prefiere no tener paréntesis cuando la prioridad del operador es obvia.

Ejemplos de código:

```csharp
// dotnet_style_parentheses_in_other_operators = always_for_clarity
var v = (a.b).Length;

// dotnet_style_parentheses_in_other_operators = never_if_unnecessary
var v = a.b.Length;
```

```vb
' dotnet_style_parentheses_in_other_operators = always_for_clarity
Dim v = (a.b).Length

' dotnet_style_parentheses_in_other_operators = never_if_unnecessary
Dim v = a.b.Length
```

Estas reglas podrían aparecer en un archivo *.editorconfig* como sigue:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:none
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:none
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:none
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:none
```

#### <a name="expression_level"></a>Preferencias de nivel de expresión

Las reglas de estilo de esta sección definen las preferencias de nivel de expresión, incluido el uso de inicializadores de objeto, de inicializadores de colección, de nombres de tupla explícitos o inferidos y de tipos anónimos inferidos.

En la tabla siguiente se muestran los nombres e identificadores de las reglas, los lenguajes de programación aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:

| Nombre de regla | Identificador de la regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión de Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_object_initializer | IDE0017 | C# y Visual Basic | true:suggestion | Primera versión |
| dotnet_style_collection_initializer | IDE0028 | C# y Visual Basic | true:suggestion | Primera versión |
| dotnet_style_explicit_tuple_names | IDE0033 | C# 7.0+ y Visual Basic 15+ | true:suggestion | Primera versión |
| dotnet_style_prefer_inferred_tuple_names | IDE0037 | C# 7.1+ y Visual Basic 15+ | true:suggestion | 15,6 |
| dotnet_style_prefer_inferred_anonymous_type_member_names | IDE0037 | C# y Visual Basic | true:suggestion | 15,6 |
| dotnet_style_prefer_auto_properties | IDE0032 | C# y Visual Basic | true:none | 15.7 |
| dotnet_style_prefer_is_null_check_over_reference_equality_method | IDE0041 | C# y Visual Basic | true:suggestion | 15.7 |
| dotnet_style_prefer_conditional_expression_over_assignment | IDE0045 | C# y Visual Basic | true:none | 15.8 |
| dotnet_style_prefer_conditional_expression_over_return | IDE0046 | C# y Visual Basic | true:none | 15.8 |

**dotnet\_style\_object_initializer**

- Cuando esta regla se establece en **true**, se prefiere inicializar los objetos con inicializadores de objeto siempre que sea posible.
- Cuando esta regla se establece en **false**, se prefiere *no* inicializar los objetos con inicializadores de objeto.

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

- Cuando esta regla se establece en **true**, se prefiere inicializar las colecciones con inicializadores de colección siempre que sea posible.
- Cuando esta regla se establece en **false**, se prefiere *no* inicializar las colecciones con inicializadores de colección.

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

- Cuando esta regla se establece en **true**, se prefieren los nombres de tupla a las propiedades ItemX.
- Cuando esta regla se establece en **false**, se prefieren las propiedades ItemX a los nombres de tupla.

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

**dotnet\_style\_prefer\_inferred\_tuple_names**

- Cuando esta regla se establece en **true**, se prefieren nombres de elementos de tupla deducidos.
- Cuando esta regla se establece en **false**, se prefieren nombres de elementos de tupla explícitos.

Ejemplos de código:

```csharp
// dotnet_style_prefer_inferred_tuple_names = true
var tuple = (age, name);

// dotnet_style_prefer_inferred_tuple_names = false
var tuple = (age: age, name: name);
```

```vb
' dotnet_style_prefer_inferred_tuple_names = true
Dim tuple = (name, age)

' dotnet_style_prefer_inferred_tuple_names = false
Dim tuple = (name:=name, age:=age)
```

**dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names**

- Cuando esta regla se establece en **true**, se prefieren nombres de miembros de tipo anónimo deducidos.
- Cuando esta regla se establece en **false**, se prefieren nombres de miembros de tipo anónimo explícitos.

Ejemplos de código:

```csharp
// dotnet_style_prefer_inferred_anonymous_type_member_names = true
var anon = new { age, name };

// dotnet_style_prefer_inferred_anonymous_type_member_names = false
var anon = new { age = age, name = name };
```

```vb
' dotnet_style_prefer_inferred_anonymous_type_member_names = true
Dim anon = New With {name, age}

' dotnet_style_prefer_inferred_anonymous_type_member_names = false
Dim anon = New With {.name = name, .age = age}
```

**dotnet\_style\_prefer\_auto\_properties**

- Cuando esta regla se establece en **true**, se prefieren propiedades automáticas antes que campos de respaldo privados.
- Cuando esta regla se establece en **false**, se prefieren propiedades con campos de respaldo privados antes que propiedades automáticas.

Ejemplos de código:

```csharp
// dotnet_style_prefer_auto_properties = true
private int Age { get; }

// dotnet_style_prefer_auto_properties = false
private int age;

public int Age
{
    get
    {
        return age;
    }
}
```

```vb
' dotnet_style_prefer_auto_properties = true
Public ReadOnly Property Age As Integer

' dotnet_style_prefer_auto_properties = false
Private _age As Integer

Public ReadOnly Property Age As Integer
    Get
        return _age
    End Get
End Property
```

**dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method**

- Cuando esta regla se establece en **true**, se prefiere usar una comprobación de valores null con coincidencia de patrones antes que object.ReferenceEquals.
- Cuando esta regla se establece en **false**, se prefiere el valor object.ReferenceEquals antes que una comprobación de valores null con coincidencia de patrones.

Ejemplos de código:

```csharp
// dotnet_style_prefer_is_null_check_over_reference_equality_method = true
if (value is null)
    return;

// dotnet_style_prefer_is_null_check_over_reference_equality_method = false
if (object.ReferenceEquals(value, null))
    return;
```

```vb
' dotnet_style_prefer_is_null_check_over_reference_equality_method = true
If value Is Nothing
    Return
End If

' dotnet_style_prefer_is_null_check_over_reference_equality_method = false
If Object.ReferenceEquals(value, Nothing)
    Return
End If
```



**dotnet\_style\_prefer\_conditional\_expression\_over_assignment**

- Cuando esta regla se establece en **true**, se prefieren asignaciones con un condicional ternario en lugar de una instrucción if-else.
- Cuando esta regla se establece en **false**, se prefieren asignaciones con una instrucción if-else en lugar de un condicional ternario.

Ejemplos de código:

```csharp
// dotnet_style_prefer_conditional_expression_over_assignment = true
string s = expr ? "hello" : "world";

// dotnet_style_prefer_conditional_expression_over_assignment = false
string s;
if (expr)
{
    s = "hello";
}
else
{
    s = "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_assignment = true
Dim s As String = If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_assignment = false
Dim s As String
If expr Then
    s = "hello"
Else
    s = "world"
End If
```

**dotnet\_style\_prefer\_conditional\_expression\_over_return**

- Cuando esta regla se establece en **true**, se prefiere que las instrucciones de devolución utilicen un condicional ternario en lugar de una instrucción if-else.
- Cuando esta regla se establece en **false**, se prefiere que las instrucciones de devolución utilicen una instrucción if-else en lugar de un condicional ternario.

Ejemplos de código:

```csharp
// dotnet_style_prefer_conditional_expression_over_return = true
return expr ? "hello" : "world"

// dotnet_style_prefer_conditional_expression_over_return = false
if (expr)
{
    return "hello";
}
else
{
    return "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_return = true
Return If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_return = false
If expr Then
    Return "hello"
Else
    Return "world"
End If
```

Estas reglas podrían aparecer en un archivo *.editorconfig* como sigue:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:none
dotnet_style_prefer_conditional_expression_over_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_return = true:suggestion
```

#### <a name="null_checking"></a>Preferencias de la comprobación de NULL

Las reglas de estilo de esta sección tienen que ver con el uso de las preferencias de la comprobación de NULL.

En la tabla siguiente se muestran los nombres e identificadores de las reglas, los lenguajes de programación aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:

| Nombre de regla | Identificador de la regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión de Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_coalesce_expression | IDE0029 | C# y Visual Basic | true:suggestion | Primera versión |
| dotnet_style_null_propagation | IDE0031 | C# 6.0+ y Visual Basic 14+ | true:suggestion | Primera versión |

**dotnet\_style\_coalesce_expression**

- Cuando esta regla se establece en **true**, se prefieren expresiones de fusión nulas a la comprobación del operador ternario.
- Cuando esta regla se establece en **false**, se prefiere la comprobación del operador ternario a las expresiones de fusión nulas.

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

- Cuando esta regla se establece en **true**, se prefiere usar el operador condicional NULL siempre que sea posible.
- Cuando esta regla se establece en **false**, se prefiere usar la comprobación de NULL ternario siempre que sea posible.

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

Estas reglas podrían aparecer en un archivo *.editorconfig* como sigue:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
```

### <a name="c-code-style-settings"></a>Configuración del estilo de código de C#

Las reglas de estilo de esta sección solo son aplicables a C#.

#### <a name="implicit-and-explicit-types"></a>Tipos implícitos y explícitos

Las reglas de estilo de esta sección (los identificadores de regla IDE0007 e IDE0008) hacen referencia al uso de la palabra clave [var](/dotnet/csharp/language-reference/keywords/var) frente a un tipo explícito en una declaración de variable. Esta regla se puede aplicar por separado a los tipos integrados, cuando el tipo es aparente, y en otros lugares.

En esta tabla se muestran los nombres de las reglas, los lenguajes de programación aplicables y los valores predeterminados:

| Nombre de regla | Lenguajes aplicables | Valor predeterminado de Visual Studio |
| ----------- | -------------------- | ----------------------|
| csharp_style_var_for_built_in_types | C# | true:none |
| csharp_style_var_when_type_is_apparent | C# | true:none |
| csharp_style_var_elsewhere | C# | true:none |

**csharp\_style\_var\_for\_built\_in_types**

- Cuando esta regla se establece en **true**, se prefiere usar `var` para declarar variables con tipos de sistema integrados como `int`.
- Cuando esta regla se establece en **false** se prefiere el tipo explícito sobre `var` para declarar variables con tipos de sistema integrados como `int`.

Ejemplos de código:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

**csharp\_style\_var\_when\_type\_is_apparent**

- Cuando esta regla se establece en **true**, se prefiere `var` cuando el tipo ya se menciona en el lado derecho de una expresión de declaración.
- Cuando esta regla se establece en **false**, se prefiere el tipo explícito a `var` cuando el tipo ya se menciona en el lado derecho de una expresión de declaración.

Ejemplos de código:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

**csharp\_style\_var_elsewhere**

- Cuando esta regla se establece en **true**, se prefiere `var` a un tipo explícito en todos los casos, a menos que se reemplace por otra regla de estilo de código.
- Cuando esta regla se establece en **false**, se prefiere el tipo explícito a `var` en todos los casos, a menos que se reemplace por otra regla de estilo de código.

Ejemplos de código:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

Ejemplo del archivo *.editorconfig*:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="expression_bodied_members"></a>Miembros con forma de expresión

Las reglas de estilo de esta sección hacen referencia al uso de [miembros con forma de expresión](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members) cuando la lógica consta de una sola expresión. Esta regla se puede aplicar a métodos, constructores, operadores, propiedades, indizadores y descriptores de acceso.

En la tabla siguiente se muestran los nombres e identificadores de las reglas, las versiones del lenguaje aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:

| Nombre de regla | Identificador de la regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión de Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_style_expression_bodied_methods | IDE0022 | C# 6.0+ | false:none | 15.3 |
| csharp_style_expression_bodied_constructors | IDE0021 | C# 7.0+ | false:none | 15.3 |
| csharp_style_expression_bodied_operators | IDE0023 e IDE0024 | C# 7.0+ | false:none | 15.3 |
| csharp_style_expression_bodied_properties | IDE0025 | C# 7.0+ | true:none | 15.3 |
| csharp_style_expression_bodied_indexers | IDE0026 | C# 7.0+ | true:none | 15.3 |
| csharp_style_expression_bodied_accessors | IDE0027 | C# 7.0+ | true:none | 15.3 |

**csharp\_style\_expression\_bodied_methods**

Esta regla acepta valores de la tabla siguiente:

| Valor | Descripción |
| ----- |:----------- |
| true | Prefiere miembros con forma de expresión para los métodos |
| when_on_single_line | Prefiere miembros con forma de expresión para los métodos cuando sean una sola línea |
| False | Prefiere cuerpos de bloque para los métodos |

Ejemplos de código:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

**csharp\_style\_expression\_bodied_constructors**

Esta regla acepta valores de la tabla siguiente:

| Valor | Descripción |
| ----- |:----------- |
| true | Prefiere miembros con forma de expresión para los constructores |
| when_on_single_line | Prefiere miembros con forma de expresión para los constructores cuando sean una sola línea |
| False | Prefiere cuerpos de bloque para los constructores |

Ejemplos de código:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

**csharp\_style\_expression\_bodied_operators**

Esta regla acepta valores de la tabla siguiente:

| Valor | Descripción |
| ----- |:----------- |
| true | Prefiere miembros con forma de expresión para los operadores |
| when_on_single_line | Prefiere miembros con forma de expresión para los operadores cuando sean una sola línea |
| False | Prefiere cuerpos de bloque para los operadores |

Ejemplos de código:

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

**csharp\_style\_expression\_bodied_properties**

Esta regla acepta valores de la tabla siguiente:

| Valor | Descripción |
| ----- |:----------- |
| true | Prefiere miembros con forma de expresión para las propiedades |
| when_on_single_line | Prefiere miembros con forma de expresión para las propiedades cuando sean una sola línea |
| False | Prefiere cuerpos de bloque para las propiedades |

Ejemplos de código:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

**csharp\_style\_expression\_bodied_indexers**

Esta regla acepta valores de la tabla siguiente:

| Valor | Descripción |
| ----- |:----------- |
| true | Prefiere miembros con forma de expresión para los indexadores |
| when_on_single_line | Prefiere miembros con forma de expresión para los indexadores cuando sean una sola línea |
| False | Prefiere cuerpos de bloque para los indexadores |

Ejemplos de código:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

**csharp\_style\_expression\_bodied_accessors**

Esta regla acepta valores de la tabla siguiente:

| Valor | Descripción |
| ----- |:----------- |
| true | Prefiere miembros con forma de expresión para los descriptores de acceso |
| when_on_single_line | Prefiere miembros con forma de expresión para los descriptores de acceso cuando sean una sola línea |
| False | Prefiere cuerpos de bloque para los descriptores de acceso |

Ejemplos de código:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

Ejemplo del archivo *.editorconfig*:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
csharp_style_expression_bodied_constructors = false:none
csharp_style_expression_bodied_operators = false:none
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
```

#### <a name="pattern_matching"></a>Coincidencia de patrones

Las reglas de estilo de esta sección hacen referencia al uso de la [coincidencia de patrones](/dotnet/csharp/pattern-matching) en C#.

En esta tabla se muestran los nombres de las reglas, los identificadores de reglas, las versiones de lenguaje aplicables y los valores predeterminados:

| Nombre de regla | Identificador de la regla | Lenguajes aplicables | Valor predeterminado de Visual Studio |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_pattern_matching_over_is_with_cast_check | IDE0020 | C# 7.0+ | true:suggestion |
| csharp_style_pattern_matching_over_as_with_null_check | IDE0019 | C# 7.0+ | true:suggestion |

**csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check**

- Cuando esta regla se establece en **true**, se prefiere la coincidencia de patrones en lugar de expresiones `is` con conversiones de tipos.
- Cuando esta regla se establece en **false**, se prefieren las expresiones `is` con conversiones de tipos en lugar de la coincidencia de patrones.

Ejemplos de código:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

**csharp\_style\_pattern\_matching\_over\_as\_with\_null_check**

- Cuando esta regla se establece en **true**, se prefiere la coincidencia de patrones en lugar de las expresiones `as` con comprobaciones de valores NULL para determinar si algo es de un tipo determinado.
- Cuando esta regla se establece en **false**, se prefieren las expresiones `as` con comprobaciones de valores NULL en lugar de la coincidencia de patrones para determinar si algo es de un tipo determinado.

Ejemplos de código:

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

Ejemplo del archivo *.editorconfig*:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="inlined_variable_declarations"></a>Declaraciones de variables insertadas

Esta regla de estilo se aplica a si las variables `out` se declaran como alineadas o no. A partir de C# 7, puede [declarar una variable de salida en la lista de argumentos de la llamada al método](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument), en lugar de en una declaración de variable independiente.

En esta tabla se muestran los nombres de las reglas, el identificador de reglas, las versiones de lenguaje aplicables y los valores predeterminados:

| Nombre de regla | Identificador de la regla | Lenguajes aplicables | Valor predeterminado de Visual Studio |
| --------- | -------- | -------------------- | ----------------------|
| csharp_style_inlined_variable_declaration | IDE0018 | C# 7.0+ | true:suggestion |

**csharp\_style\_inlined\_variable_declaration**

- Cuando esta regla se establece en **true**, se prefiere que las variables `out` se declaren como alineadas en la lista de argumentos de una llamada de método, siempre que sea posible.
- Cuando esta regla se establece en **false**, se prefiere que las variables `out` se declaren antes de la llamada de método.

Ejemplos de código:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

Ejemplo del archivo *.editorconfig*:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

#### <a name="expression_level_csharp"></a>Preferencias de nivel de expresión

Las reglas de estilo de esta sección hacen referencia a las preferencias de nivel de expresión, incluido el uso de [expresiones predeterminadas](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference), variables deconstruidas y funciones locales sobre funciones anónimas.

En la tabla siguiente se muestran el nombre e identificador de la regla, las versiones del lenguaje aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:

| Nombre de regla | Identificador de la regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión de Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_prefer_simple_default_expression | IDE0034 | C# 7.1+ | true:suggestion | 15.3 |
| csharp_style_deconstructed_variable_declaration | IDE0042 | C# 7.0+ | true:suggestion | 15.5 |
| csharp_style_pattern_local_over_anonymous_function | IDE0039 | C# 7.0+ | true:suggestion | 15.5 |

**csharp\_prefer\_simple\_default_expression**

Esta regla de estilo se aplica al uso del [literal `default` para las expresiones de valor predeterminado](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference) cuando el compilador puede deducir el tipo de la expresión.

- Cuando esta regla se establece en **true**, se prefiere `default` a `default(T)`.
- Cuando esta regla se establece en **false**, se prefiere `default(T)` a `default`.

Ejemplos de código:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

**csharp\_style\_deconstructed\_variable_declaration**

- Cuando esta regla está establecida en **true**, prefiere la declaración de variable deconstruida.
- Cuando esta regla está establecida **false**, no se prefiere la deconstrucción en las declaraciones de variable.

Ejemplos de código:

```csharp
// csharp_style_deconstructed_variable_declaration = true
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");

// csharp_style_deconstructed_variable_declaration = false
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");
```

**csharp\_style\_pattern\_local\_over\_anonymous_function**

- Cuando esta regla está establecida en **true**, prefiere las funciones locales sobre las funciones anónimas.
- Cuando esta regla está establecida en **false**, prefiere las funciones anónimas sobre las funciones locales.

Ejemplos de código:

```csharp
// csharp_style_pattern_local_over_anonymous_function = true
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}

// csharp_style_pattern_local_over_anonymous_function = false
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};
```

Ejemplo del archivo *.editorconfig*:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
```

#### <a name="null_checking_csharp"></a>Preferencias de la comprobación de "NULL"

Estas reglas de estilo están relacionadas con la sintaxis de la comprobación de `null`, incluido el uso de expresiones `throw` o instrucciones `throw`, y si se realiza una comprobación de NULL o se usa el operador de incorporación condicional (`?.`) al invocar una [expresión lambda](/dotnet/csharp/lambda-expressions).

En esta tabla se muestran los nombres de las reglas, los identificadores de reglas, las versiones de lenguaje aplicables y los valores predeterminados:

| Nombre de regla | Identificador de la regla | Lenguajes aplicables | Valor predeterminado de Visual Studio |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_throw_expression | IDE0016 | C# 7.0+ | true:suggestion |
| csharp_style_conditional_delegate_call | IDE0041 | C# 6.0+ | true:suggestion |

**csharp\_style\_throw_expression**

- Cuando esta regla se establece en **true**, se prefiere el uso de expresiones `throw` en lugar de instrucciones `throw`.
- Cuando esta regla se establece en **false**, se prefiere el uso de expresiones `throw` en lugar de instrucciones `throw`.

Ejemplos de código:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

**csharp\_style\_conditional\_delegate_call**

- Cuando esta regla se establece en **true**, es preferible usar el operador de incorporación condicional (`?.`) al invocar una expresión lambda, en lugar de realizar una comprobación de NULL.
- Cuando esta regla se establece en **false**, se prefiere realizar una comprobación de NULL antes de invocar una expresión lambda, en lugar de usar el operador de incorporación condicional (`?.`).

Ejemplos de código:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

Ejemplo del archivo *.editorconfig*:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="code_block"></a>Preferencias de bloques de código

Esta regla de estilo se refiere al uso de llaves `{ }` para delimitar los bloques de código.

En la tabla siguiente se muestran el nombre e identificador de la regla, las versiones del lenguaje aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:

| Nombre de regla | Identificador de la regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión de Visual Studio 2017 |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_prefer_braces | IDE0011 | C# | true:none | 15.3 |

**csharp\_prefer\_braces**

- Cuando esta regla se establece en **true**, se prefieren las llaves incluso para una línea de código.
- Cuando esta regla se establece en **false**, se prefiere que no se usen llaves, si está permitido.

Ejemplos de código:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

Ejemplo del archivo *.editorconfig*:

```EditorConfig
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
        - csharp_space_before_colon_in_inheritance_clause
        - csharp_space_after_colon_in_inheritance_clause
        - csharp_space_around_binary_operators
        - csharp_space_between_method_declaration_empty_parameter_list_parentheses
        - csharp_space_between_method_call_name_and_opening_parenthesis
        - csharp_space_between_method_call_empty_parameter_list_parentheses
    - [Opciones de ajuste](#wrapping)
        - csharp_preserve_single_line_statements
        - csharp_preserve_single_line_blocks

### <a name="net-formatting-settings"></a>Configuración de formato de .NET

Las reglas de formato de esta sección son aplicables a C# y Visual Basic.

#### <a name="usings"></a>Organización de instrucciones Using

Esta regla de formato se refiere a la ubicación de directivas using con System.*, con respecto a otras directivas using.

En la tabla siguiente se muestra el nombre de la regla, los lenguajes aplicables, el valor predeterminado y la primera versión compatible de Visual Studio:

| Nombre de regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión de Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ---------------- |
| dotnet_sort_system_directives_first | C# y Visual Basic | true | 15.3 |

**dotnet\_sort\_system\_directives_first**

- Cuando esta regla se establece en **true**, las directivas using System.* se ordenan alfabéticamente y se colocan delante de otras directivas using.
- Cuando esta regla se establece en **false**, las directivas using System.* no se colocan delante de otras directivas using.

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

Ejemplo del archivo *.editorconfig*:

```EditorConfig
# .NET formatting settings:
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
```

### <a name="c-formatting-settings"></a>Configuración de formato de C#

Las reglas de formato de esta sección se aplican únicamente al código de C#.

#### <a name="newline"></a>Opciones de nueva línea

Estas reglas de formato se refieren al uso de nuevas líneas para dar formato al código.

En la tabla siguiente se muestran los nombres de las reglas de "nueva línea", los lenguajes aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:

| Nombre de regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión de Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_new_line_before_open_brace | C# | todo | 15.3 |
| csharp_new_line_before_else | C# | true | 15.3 |
| csharp_new_line_before_catch | C# | true | 15.3 |
| csharp_new_line_before_finally | C# | true | 15.3 |
| csharp_new_line_before_members_in_object_initializers | C# | true | 15.3 |
| csharp_new_line_before_members_in_anonymous_types | C# | true | 15.3 |
| csharp_new_line_between_query_expression_clauses | C# | true | 15.3 |

**csharp\_new\_line\_before\_open_brace**

Esta regla se refiere a si se debe colocar una llave de apertura `{` en la misma línea que el código anterior, o en una línea nueva. Para esta regla, no se especifica **true** ni **false**. En su lugar, se especifica **all**, **none** o uno o varios elementos de código como **methods** o **properties**, para definir cuándo se debe aplicar esta regla. La lista completa de los valores permitidos se muestra en la tabla siguiente:

| Valor | Descripción
| ------------- |:-------------|
| descriptores de acceso, métodos_anónimos, tipos_anónimos, bloques_control, eventos, indexadores, lambdas, funciones_locales, métodos, inicializadores_matriz_colección_objetos, propiedades, tipos.<br>(Si hay varios tipos, sepárelos con comas ","). | Es obligatorio que las llaves estén en una línea nueva para los elementos de código especificados (también conocido como estilo "Allman") |
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

- Cuando esta regla se establece en **true**, las instrucciones `else` se colocan en una línea nueva.
- Cuando esta regla se establece en **false**, las instrucciones `else` se colocan en la misma línea.

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

- Cuando esta regla se establece en **true**, las instrucciones `catch` se colocan en una línea nueva.
- Cuando esta regla se establece en **false**, las instrucciones `catch` se colocan en la misma línea.

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

- Cuando esta regla se establece en **true**, es obligatorio que las instrucciones `finally` estén en una nueva línea después de la llave de cierre.
- Cuando esta regla se establece en **false**, es obligatorio que las instrucciones `finally` estén en la misma línea que la llave de cierre.

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

- Cuando esta regla se establece en **true**, es obligatorio que los miembros de inicializadores de objeto estén en líneas independientes.
- Cuando esta regla se establece en **false**, es obligatorio que los miembros de inicializadores de objeto estén en la misma línea.

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

- Cuando esta regla se establece en **true**, es obligatorio que los miembros de tipos anónimos estén en líneas independientes.
- Cuando esta regla se establece en **false**, es obligatorio que los miembros de tipos anónimos estén en la misma línea.

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

- Cuando esta regla se establece en **true**, es obligatorio que los elementos de cláusulas de expresión de consulta estén en líneas independientes.
- Cuando esta regla se establece en **false**, es obligatorio que los elementos de cláusulas de expresión de consulta estén en la misma línea.

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

Ejemplo del archivo *.editorconfig*:

```EditorConfig
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

#### <a name="indent"></a>Opciones de sangría

Estas reglas de formato se refieren al uso de la sangría para dar formato al código.

En la tabla siguiente se muestran los nombres de las reglas, los lenguajes aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:

| Nombre de regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión de Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_indent_case_contents | C# | true | 15.3 |
| csharp_indent_switch_labels | C# | true | 15.3 |
| csharp_indent_labels | C# | no_change | 15.3 |

**csharp\_indent\_case_contents**

- Cuando esta regla se establece en **true**, se aplica sangría al contenido de los casos `switch`.
- Cuando esta regla se establece en **false**, no se aplica sangría al contenido de los casos `switch`.

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

- Cuando esta regla se establece en **true**, se aplica sangría a las etiquetas `switch`.
- Cuando esta regla se establece en **false**, no se aplica sangría a las etiquetas `switch`.

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

Ejemplo del archivo *.editorconfig*:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
```

#### <a name="spacing"></a>Opciones de espaciado

Estas reglas de formato se refieren al uso de caracteres de espacio para dar formato al código.

En la tabla siguiente se muestran los nombres de las reglas, los lenguajes aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:

| Nombre de regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión de Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_space_after_cast | C# | False | 15.3 |
| csharp_space_after_keywords_in_control_flow_statements | C# | true | 15.3 |
| csharp_space_between_method_declaration_parameter_list_parentheses | C# | False | 15.3 |
| csharp_space_between_method_call_parameter_list_parentheses | C# | False | 15.3 |
| csharp_space_between_parentheses | C# | False | 15.3 |
| csharp_space_before_colon_in_inheritance_clause | C# | true | 15.7 |
| csharp_space_after_colon_in_inheritance_clause | C# | true | 15.7 |
| csharp_space_around_binary_operators | C# | before_and_after | 15.7 |
| csharp_space_between_method_declaration_empty_parameter_list_parentheses | C# | False | 15.7 |
| csharp_space_between_method_call_name_and_opening_parenthesis | C# | False | 15.7 |
| csharp_space_between_method_call_empty_parameter_list_parentheses | C# | False | 15.7 |

**csharp\_space\_after_cast**

- Cuando esta regla se establece en **true**, se requiere un espacio entre una conversión y el valor.
- Cuando esta regla se establece en **false**, _no_ se requiere un espacio entre la conversión y el valor.

Ejemplos de código:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

**csharp_space_after_keywords_in_control_flow_statements**

- Cuando esta regla se establece en **true**, se requiere un espacio después de una palabra clave en una instrucción de flujo de control como un bucle `for`.
- Cuando esta regla se establece en **false**, _no_ se requiere un espacio después de una palabra clave en una instrucción de flujo de control como un bucle `for`.

Ejemplos de código:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

**csharp_space_between_method_declaration_parameter_list_parentheses**

- Cuando esta regla se establece en **true**, se coloca un carácter de espacio después del paréntesis de apertura y antes del paréntesis de cierre de una lista de parámetros de declaración de método.
- Cuando esta regla se establece en **false**, no se colocan caracteres de espacio después del paréntesis de apertura y antes del paréntesis de cierre de una lista de parámetros de declaración de método.

Ejemplos de código:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

**csharp_space_between_method_call_parameter_list_parentheses**

- Cuando esta regla se establece en **true**, se coloca un carácter de espacio después del paréntesis de apertura y antes del paréntesis de cierre de una llamada de método.
- Cuando esta regla se establece en **false**, no se colocan caracteres de espacio después del paréntesis de apertura y antes del paréntesis de cierre de una llamada de método.

Ejemplos de código:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

**csharp_space_between_parentheses**

Esta regla acepta uno o más valores de la siguiente tabla:

| Valor | Descripción |
| ----- |:------------|
| control_flow_statements | Se inserta un espacio entre los paréntesis de instrucciones de flujo de control. |
| expresiones | Se inserta un espacio entre los paréntesis de expresiones. |
| type_casts | Se inserta un espacio entre los paréntesis de las conversiones de tipos. |

Si esta regla se omite o si se usa un valor distinto de `control_flow_statements`, `expressions` o `type_casts`, la configuración no se aplicará.

Ejemplos de código:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

**csharp\_space\_before\_colon\_in\_inheritance_clause**

- Cuando esta regla se establece en **true**, hay que introducir un espacio antes de los dos puntos para las bases o interfaces en las declaraciones de tipos.
- Cuando esta regla se establece en **false**, _no_ hay que introducir ningún espacio antes de los dos puntos para las bases o interfaces en las declaraciones de tipos.

Ejemplos de código:

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

**csharp\_space\_after\_colon\_in\_inheritance_clause**

- Cuando esta regla se establece en **true**, hay que introducir un espacio después de los dos puntos para las bases o interfaces en las declaraciones de tipos.
- Cuando esta regla se establece en **false**, _no_ hay que introducir ningún espacio después de los dos puntos para las bases o interfaces en las declaraciones de tipos.

Ejemplos de código:

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

**csharp\_space\_around\_binary_operators**

Esta regla acepta un valor de la tabla siguiente:

| Valor | Descripción |
| ----- |:------------|
| before_and_after | Insertar espacio delante y detrás del operador binario |
| ninguna | Quitar espacios delante y detrás del operador binario |
| omitir | Omitir espacios alrededor de operadores binarios |

Si esta regla se omite o si se usa un valor distinto de `before_and_after`, `none` o `ignore`, la configuración no se aplicará.

Ejemplos de código:

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

**csharp_space_between_method_declaration_empty_parameter_list_parentheses**

- Si esta regla se establece en **true**, inserte un espacio dentro de los paréntesis de una lista de parámetros correspondiente a una declaración de método.
- Si esta regla se establece en **false**, quite el espacio dentro de los paréntesis de una lista de parámetros correspondiente a una declaración de método.

Ejemplos de código:

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

**csharp_space_between_method_call_name_and_opening_parenthesis**

- Si esta regla se establece en **true**, inserte un espacio entre el nombre de la llamada de método y el paréntesis de apertura.
- Si esta regla se establece en **false**, quite el espacio entre el nombre de la llamada de método y el paréntesis de apertura.

Ejemplos de código:

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

**csharp_space_between_method_call_empty_parameter_list_parentheses**

- Si esta regla se establece en **true**, inserte un espacio entre los paréntesis vacíos de la lista de argumentos.
- Si esta regla se establece en **false**, quite el espacio entre los paréntesis vacíos de la lista de argumentos.

Ejemplos de código:

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

Ejemplo del archivo *.editorconfig*:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
```

#### <a name="wrapping"></a>Opciones de ajuste

Estas reglas de formato se refieren al uso de líneas individuales frente a líneas separadas para las instrucciones y bloques de código.

En la tabla siguiente se muestran los nombres de las reglas, los lenguajes aplicables, los valores predeterminados y la primera versión compatible de Visual Studio:

| Nombre de regla | Lenguajes aplicables | Valor predeterminado de Visual Studio | Versión de Visual Studio 2017 |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_preserve_single_line_statements | C# | true | 15.3 |
| csharp_preserve_single_line_blocks | C# | true | 15.3 |

**csharp_preserve_single_line_statements**

- Cuando esta regla se establece en **true**, las instrucciones y declaraciones de miembros se dejan en la misma línea.
- Cuando esta regla se establece en **false**, las instrucciones y declaraciones de miembros se dejan en líneas diferentes.

Ejemplos de código:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

**csharp_preserve_single_line_blocks**

- Cuando esta regla se establece en **true**, el bloque de código se deja en una sola línea.
- Cuando esta regla se establece en **false**, el bloque de código se deja en líneas separadas.

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

Ejemplo del archivo *.editorconfig*:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

## <a name="example-editorconfig-file"></a>Ejemplo del archivo EditorConfig

Para poder empezar, aquí tiene un archivo *.editorconfig* de ejemplo con las opciones predeterminadas:

```EditorConfig
###############################
# Core EditorConfig Options   #
###############################

root = true

# All files
[*]
indent_style = space

# Code files
[*.{cs,csx,vb,vbx}]
indent_size = 4
insert_final_newline = true
charset = utf-8-bom

###############################
# .NET Coding Conventions     #
###############################

[*.{cs,vb}]
# Organize usings
dotnet_sort_system_directives_first = true

# this. preferences
dotnet_style_qualification_for_field = false:none
dotnet_style_qualification_for_property = false:none
dotnet_style_qualification_for_method = false:none
dotnet_style_qualification_for_event = false:none

# Language keywords vs BCL types preferences
dotnet_style_predefined_type_for_locals_parameters_members = true:none
dotnet_style_predefined_type_for_member_access = true:none

# Parentheses preferences
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent

# Modifier preferences
dotnet_style_require_accessibility_modifiers = for_non_interface_members:none
dotnet_style_readonly_field = true:suggestion

# Expression-level preferences
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:silent
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:silent
dotnet_style_prefer_conditional_expression_over_return = true:silent

###############################
# Naming Conventions          #
###############################

# Style Definitions
dotnet_naming_style.pascal_case_style.capitalization             = pascal_case

# Use PascalCase for constant fields
dotnet_naming_rule.constant_fields_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.constant_fields_should_be_pascal_case.symbols  = constant_fields
dotnet_naming_rule.constant_fields_should_be_pascal_case.style    = pascal_case_style
dotnet_naming_symbols.constant_fields.applicable_kinds            = field
dotnet_naming_symbols.constant_fields.applicable_accessibilities  = *
dotnet_naming_symbols.constant_fields.required_modifiers          = const

###############################
# C# Code Style Rules         #
###############################

[*.cs]
# var preferences
csharp_style_var_for_built_in_types = true:none
csharp_style_var_when_type_is_apparent = true:none
csharp_style_var_elsewhere = true:none

# Expression-bodied members
csharp_style_expression_bodied_methods = false:none
csharp_style_expression_bodied_constructors = false:none
csharp_style_expression_bodied_operators = false:none
csharp_style_expression_bodied_properties = true:none
csharp_style_expression_bodied_indexers = true:none
csharp_style_expression_bodied_accessors = true:none

# Pattern-matching preferences
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion

# Null-checking preferences
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = true:suggestion

# Modifier preferences
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Expression-level preferences
csharp_prefer_braces = true:none
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_style_inlined_variable_declaration = true:suggestion

###############################
# C# Formatting Rules         #
###############################

# New line preferences
csharp_new_line_before_open_brace = all
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true

# Indentation preferences
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left

# Space preferences
csharp_space_after_cast = false
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_call_parameter_list_parentheses = false
csharp_space_between_method_declaration_parameter_list_parentheses = false
csharp_space_between_parentheses = false
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false

# Wrapping preferences
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true

##################################
# Visual Basic Code Style Rules  #
##################################

[*.vb]
# Modifier preferences
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

## <a name="see-also"></a>Vea también

- [Acciones rápidas](../ide/quick-actions.md)
- [Convenciones de nomenclatura de .NET para EditorConfig](../ide/editorconfig-naming-conventions.md)
- [Crear opciones del editor personalizadas y portátiles](../ide/create-portable-custom-editor-options.md)
- [Archivo .editorconfig de la plataforma de compilación .NET](https://github.com/dotnet/roslyn/blob/master/.editorconfig)

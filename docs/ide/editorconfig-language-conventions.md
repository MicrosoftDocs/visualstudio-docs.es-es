---
title: Convenciones de lenguaje de .NET para EditorConfig
ms.date: 09/23/2019
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- language code style rules [EditorConfig]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 471932f6a097879da194dc6bb4f18807f2323397
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "79306864"
---
# <a name="language-conventions"></a>Convenciones de lenguaje

Las convenciones de lenguaje de EditorConfig en Visual Studio se dividen en dos categorías: las que se aplican a Visual Basic y C# y las que son específicas de C#. Las convenciones de lenguaje afectan al modo en que se usan diversos aspectos de un lenguaje de programación, por ejemplo, los modificadores y los paréntesis.

> [!TIP]
> - Para ver los ejemplos de código en el lenguaje de programación preferido, elíjalo con el selector de lenguajes en la esquina superior derecha de la ventana del explorador.
>
>   ![Control de selector de lenguaje de codificación](media/code-language-picker.png)
>
> - Use los vínculos de **este artículo** para ir a las diferentes secciones de la página.

## <a name="rule-format"></a>Formato de regla

Las reglas para las convenciones de lenguaje tienen el formato siguiente:

`option_name = value:severity`

Para cada convención de lenguaje, especifique un valor que define si se prefiere el estilo o cuándo. Muchas reglas aceptan un valor de `true` (se prefiere este estilo) o `false` (no se prefiere este estilo). Otras reglas aceptan valores como `when_on_single_line` o `never`. La segunda parte de la regla especifica la [gravedad](#severity-levels).

::: moniker range=">=vs-2019"

> [!NOTE]
> Dado que los analizadores aplican las convenciones del lenguaje, también puede establecer su gravedad mediante la sintaxis de configuración predeterminada para los analizadores. La sintaxis adopta la forma `dotnet_diagnostic.<rule ID>.severity = <severity>`, por ejemplo, `dotnet_diagnostic.IDE0040.severity = silent`. Para obtener más información, vea [Establecer la gravedad de la regla en un archivo EditorConfig](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file).

::: moniker-end

## <a name="severity-levels"></a>Niveles de gravedad

La gravedad de la convención de lenguaje especifica el nivel en el que se va a aplicar ese estilo. En la tabla siguiente se enumeran los valores de gravedad posibles y sus efectos:

Gravedad | Efecto
:------- | ------
`error` | Cuando se infringe esta regla de estilo, se muestra un error del compilador.
`warning` | Cuando se infringe esta regla de estilo, se muestra una advertencia del compilador.
`suggestion` | Cuando se infringe esta regla de estilo, se muestra al usuario como una sugerencia. Las sugerencias aparecen como tres puntos de color gris en los dos primeros caracteres.
`silent` | No mostrar nada al usuario cuando se infringe esta regla. Pero las características de generación de código generan código con este estilo. Las reglas con gravedad `silent` participan en la limpieza y aparecen en el menú **Acciones rápidas y refactorizaciones**.
`none` | No mostrar nada al usuario cuando se infringe esta regla. Pero las características de generación de código generan código con este estilo. Las reglas con gravedad `none` nunca aparecen en el menú **Acciones rápidas y refactorizaciones**. En la mayoría de casos, el valor se considera "deshabilitado" o "omitido".

::: moniker range=">=vs-2019"

## <a name="automatically-configure-code-styles"></a>Configuración automática de estilos de código

A partir de Visual Studio 2019 16.3, puede configurar reglas de estilo de código desde el menú de bombilla [Acciones rápidas](quick-actions.md) después de que se produzca una infracción de estilo.

Para cambiar la convención de estilo de código:

1. Mantenga el mouse sobre la línea ondulada en el editor y abra el menú de bombilla que aparece. Elija **Configurar o suprimir incidencias** > **Configurar \<Id. de regla> Estilo de código**.

   ![Configuración del estilo de código desde el menú de bombilla en Visual Studio](media/vs-2019/configure-code-style.png)

2. Desde allí, elija una de las opciones de estilo de código.

   ![Configuración del estilo de código](media/vs-2019/configure-code-style-setting.png)

   Visual Studio agrega o modifica la opción de configuración en el archivo EditorConfig, tal como se muestra en el cuadro de vista previa.

Para cambiar la gravedad de la infracción del estilo de código, siga los mismos pasos, pero elija **Configurar \<Id. de regla> gravedad**, en lugar de **Configurar \<Id. de regla > Estilo de código**. Para obtener más información, consulte [Configuración automática de la gravedad de la regla](../code-quality/use-roslyn-analyzers.md#automatically-configure-rule-severity).

::: moniker-end

## <a name="net-code-style-settings"></a>Configuración del estilo de código de .NET

Las reglas de estilo de esta sección son aplicables a C# y Visual Basic.

- [Los calificadores "This." y "Me."](#this-and-me)
  - dotnet\_style\_qualification\_for_field
  - dotnet\_style\_qualification\_for_property
  - dotnet\_style\_qualification\_for_method
  - dotnet\_style\_qualification\_for_event
- [Palabras clave del lenguaje en lugar de nombres de tipos de marco para referencias de tipo](#language-keywords)
  - dotnet\_style\_predefined\_type\_for\_locals\_parameters_members
  - dotnet\_style\_predefined\_type\_for\_member_access
- [Preferencias de modificadores](#normalize-modifiers)
  - dotnet\_style\_require\_accessibility_modifiers
  - csharp\_preferred\_modifier_order
  - visual\_basic\_preferred\_modifier_order
  - dotnet\_style\_readonly\_field
- [Preferencias de paréntesis](#parentheses-preferences)
  - dotnet\_style\_parentheses\_in\_arithmetic\_binary\_operators
  - dotnet\_style\_parentheses\_in\_other\_binary\_operators
  - dotnet\_style\_parentheses\_in\_other\_operators
  - dotnet\_style\_parentheses\_in\_relational\_binary\_operators
- [Preferencias de nivel de expresión](#expression-level-preferences)
  - dotnet\_style\_object_initializer
  - dotnet\_style\_collection_initializer
  - dotnet\_style\_explicit\_tuple_names
  - dotnet\_style\_prefer\_inferred\_tuple_names
  - dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names
  - dotnet\_style\_prefer\_auto\_properties
  - dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method
  - dotnet\_style\_prefer\_conditional\_expression\_over\_assignment
  - dotnet\_style\_prefer\_conditional\_expression\_over\_return
  - dotnet\_style\_prefer\_compound\_assignment
- [Preferencias de la comprobación de "NULL"](#null-checking-preferences)
  - dotnet\_style\_coalesce_expression
  - dotnet\_style\_null_propagation

### <a name="this-and-me"></a>"This." y "Me."

Esta regla de estilo se puede aplicar a campos, propiedades, métodos o eventos. Un valor **true** significa que prefiere que el símbolo de código esté precedido por `this.` en C# o `Me.` en Visual Basic. Un valor **false** significa que prefiere que el elemento de código _no_ esté precedido por `this.` o `Me.`.

Estas reglas podrían aparecer en un archivo *.editorconfig* como sigue:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="dotnet_style_qualification_for_field"></a>dotnet\_style\_qualification\_for_field

|||
|-|-|
| **Nombre de regla** | dotnet_style_qualification_for_field |
| **Identificador de la regla** | IDE0003 e IDE0009 |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Valores** | `true`: se prefiere que los campos estén precedidos por `this.` en C# o `Me.` en Visual Basic.<br /><br />`false`: se prefiere que los campos _no_ estén precedidos por `this.` o `Me.`. |
| **Valor predeterminado de Visual Studio** | `false:silent` |

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

#### <a name="dotnet_style_qualification_for_property"></a>dotnet\_style\_qualification\_for_property

|||
|-|-|
| **Nombre de regla** | dotnet_style_qualification_for_property |
| **Identificador de la regla** | IDE0003 e IDE0009 |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Valores** | `true`: se prefiere que las propiedades estén precedidas por `this.` en C# o `Me.` en Visual Basic.<br /><br />`false`: se prefiere que las propiedades _no_ estén precedidas por `this.` o `Me.`. |
| **Valor predeterminado de Visual Studio** | `false:silent` |

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

#### <a name="dotnet_style_qualification_for_method"></a>dotnet\_style\_qualification\_for_method

|||
|-|-|
| **Nombre de regla** | dotnet_style_qualification_for_method |
| **Identificador de la regla** | IDE0003 e IDE0009 |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Valores** | `true`: se prefiere que los métodos estén precedidos por `this.` en C# o `Me.` en Visual Basic.<br /><br />`false`: se prefiere que los métodos _no_ estén precedidos por `this.` o `Me.`. |
| **Valor predeterminado de Visual Studio** | `false:silent` |

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

#### <a name="dotnet_style_qualification_for_event"></a>dotnet\_style\_qualification\_for_event

|||
|-|-|
| **Nombre de regla** | dotnet_style_qualification_for_event |
| **Identificador de la regla** | IDE0003 e IDE0009 |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Valores** | `true`: se prefiere que los eventos estén precedidos por `this.` en C# o `Me.` en Visual Basic.<br /><br />`false`: se prefiere que los eventos _no_ estén precedidos por `this.` o `Me.`. |
| **Valor predeterminado de Visual Studio** | `false:silent` |

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

### <a name="language-keywords"></a>Palabras clave del lenguaje en lugar de nombres de tipos de marco para referencias de tipo

Esta regla de estilo se puede aplicar a variables locales, parámetros de métodos y miembros de clases, o bien como una regla independiente para escribir expresiones de acceso a miembros. Un valor **true** significa que se prefiere la palabra clave del lenguaje (por ejemplo, `int` o `Integer`) en lugar del nombre de tipo (por ejemplo, `Int32`) para los tipos que tienen una palabra clave para representarlos. Un valor **false** significa que se prefiere el nombre de tipo en lugar de la palabra clave del lenguaje.

Estas reglas podrían aparecer en un archivo *.editorconfig* como sigue:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="dotnet_style_predefined_type_for_locals_parameters_members"></a>dotnet\_style\_predefined\_type\_for\_locals\_parameters_members

|||
|-|-|
| **Nombre de regla** | dotnet_style_predefined_type_for_locals_parameters_members |
| **Identificador de la regla** | IDE0012 e IDE0014 |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Valores** | `true`: se prefiere la palabra clave del lenguaje para las variables locales, parámetros de métodos y miembros de clases, en lugar del nombre de tipo, para los tipos que tienen una palabra clave para representarlos.<br /><br />`false`: se prefiere el nombre de tipo para las variables locales, parámetros de métodos y miembros de clases, en lugar de la palabra clave del lenguaje. |
| **Valor predeterminado de Visual Studio** | `true:silent` |

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

#### <a name="dotnet_style_predefined_type_for_member_access"></a>dotnet\_style\_predefined\_type\_for\_member_access

|||
|-|-|
| **Nombre de regla** | dotnet_style_predefined_type_for_member_access |
| **Identificador de la regla** | IDE0013 e IDE0015 |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Valores** | `true`: se prefiere la palabra clave del lenguaje para las expresiones de acceso a miembros, en lugar del nombre de tipo, para los tipos que tienen una palabra clave para representarlos.<br /><br />`false`: se prefiere el nombre de tipo para las expresiones de acceso a miembros, en lugar de la palabra clave del lenguaje. |
| **Valor predeterminado de Visual Studio** | `true:silent` |

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

### <a name="normalize-modifiers"></a>Preferencias de modificadores

Las reglas de estilo de esta sección hacen referencia a las preferencias de modificadores, incluida la necesidad de modificadores de accesibilidad, la especificación del criterio de ordenación deseado de los modificadores y la necesidad del modificador de solo lectura.

Estas reglas podrían aparecer en un archivo *.editorconfig* como sigue:

```ini
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

#### <a name="dotnet_style_require_accessibility_modifiers"></a>dotnet\_style\_require\_accessibility_modifiers

|||
|-|-|
| **Nombre de regla** | dotnet_style_require_accessibility_modifiers |
| **Identificador de la regla** | IDE0040 |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Valores** | `always`: se prefiere que los modificadores de accesibilidad se especifiquen.<br /><br />`for_non_interface_members`: se prefiere que los modificadores de accesibilidad se declaren, excepto para los miembros de la interfaz pública. (Esto equivale a **always** y se ha agregado para las pruebas futuras si C# agrega métodos de interfaz predeterminados).<br /><br />`never`: no se prefiere que se especifiquen los modificadores de accesibilidad.<br /><br />`omit_if_default`: se prefiere que se especifiquen los modificadores de accesibilidad, excepto si se trata del modificador predeterminado. |
| **Valor predeterminado de Visual Studio** | `for_non_interface_members:silent` |
| **Versión introducida** | Versión 15.5 de Visual Studio 2017 |

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

#### <a name="csharp_preferred_modifier_order"></a>csharp_preferred_modifier_order

|||
|-|-|
| **Nombre de regla** | csharp_preferred_modifier_order |
| **Identificador de la regla** | IDE0036 |
| **Lenguajes aplicables** | C# |
| **Valores** | Uno o más C# modificadores, como `public`, `private`, y `protected` |
| **Valor predeterminado de Visual Studio** | `public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:silent` |
| **Versión introducida** | Versión 15.5 de Visual Studio 2017 |

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

#### <a name="visual_basic_preferred_modifier_order"></a>visual_basic_preferred_modifier_order

|||
|-|-|
| **Nombre de regla** | visual_basic_preferred_modifier_order |
| **Identificador de la regla** | IDE0036 |
| **Lenguajes aplicables** | Visual Basic |
| **Valores** | Uno o varios modificadores de Visual Basic, como `Partial`, `Private` y `Public` |
| **Valor predeterminado de Visual Studio** | `Partial, Default, Private, Protected, Public, Friend, NotOverridable, Overridable, MustOverride, Overloads, Overrides, MustInherit, NotInheritable, Static, Shared, Shadows, ReadOnly, WriteOnly, Dim, Const,WithEvents, Widening, Narrowing, Custom, Async:silent` |
| **Versión introducida** | Versión 15.5 de Visual Studio 2017 |

- Cuando esta regla esté establecida en una lista de modificadores, prefiere el orden especificado.
- Cuando esta regla se omite del archivo, no se prefiere un orden de modificador.

Ejemplos de código:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

#### <a name="dotnet_style_readonly_field"></a>dotnet_style_readonly_field

|||
|-|-|
| **Nombre de regla** | dotnet_style_readonly_field |
| **Identificador de la regla** | IDE0044 |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Valores** | `true`: se prefiere que los campos se marquen con `readonly` (C#) o `ReadOnly` (Visual Basic) si solo se van a asignar en línea, o dentro de un constructor.<br /><br />`false`: no se especifica ninguna preferencia sobre si los campos se deben marcar con `readonly` (C#) o `ReadOnly` (Visual Basic). |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |
| **Versión introducida** | Visual Studio 2017 versión 15.7 |

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

### <a name="parentheses-preferences"></a>Preferencias de paréntesis

Las reglas de estilo de esta sección se refieren a las preferencias de paréntesis, e incluyen el uso de paréntesis para operadores de aritmética, relacionales y otros operadores binarios.

Estas reglas podrían aparecer en un archivo *.editorconfig* como sigue:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
```

#### <a name="dotnet_style_parentheses_in_arithmetic_binary_operators"></a>dotnet\_style\_parentheses\_in\_arithmetic\_binary_operators

|||
|-|-|
| **Nombre de regla** | dotnet_style_parentheses_in_arithmetic_binary_operators |
| **Identificador de la regla** | IDE0047 |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Valores** | `always_for_clarity`: se prefieren los paréntesis para clarificar la prioridad del operador aritmético (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`).<br /><br />`never_if_unnecessary`: se prefiere no tener paréntesis cuando la prioridad del operador aritmético (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) es obvia. |
| **Valor predeterminado de Visual Studio** | `always_for_clarity:silent` |
| **Versión introducida** | Visual Studio 2017, versión 15.8 |

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

#### <a name="dotnet_style_parentheses_in_relational_binary_operators"></a>dotnet\_style\_parentheses\_in\_relational\_binary_operators

|||
|-|-|
| **Nombre de regla** | dotnet_style_parentheses_in_relational_binary_operators |
| **Identificador de la regla** | IDE0047 |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Valores** | `always_for_clarity`: se prefieren los paréntesis para clarificar la prioridad del operador relacional (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`).<br /><br />`never_if_unnecessary`: se prefiere no tener paréntesis cuando la prioridad del operador relacional (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) es obvia. |
| **Valor predeterminado de Visual Studio** | `always_for_clarity:silent` |
| **Versión introducida** | Visual Studio 2017, versión 15.8 |

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

#### <a name="dotnet_style_parentheses_in_other_binary_operators"></a>dotnet\_style\_parentheses\_in\_other\_binary_operators

|||
|-|-|
| **Nombre de regla** | dotnet_style_parentheses_in_other_binary_operators |
| **Identificador de la regla** | IDE0047 |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Valores** | `always_for_clarity`: se prefieren los paréntesis para clarificar la prioridad de otro operador binario (`&&`, `||`, `??`).<br /><br />`never_if_unnecessary`: se prefiere no tener paréntesis cuando la prioridad del operador binario (`&&`, `||`, `??`) es obvia. |
| **Valor predeterminado de Visual Studio** | `always_for_clarity:silent` |
| **Versión introducida** | Visual Studio 2017, versión 15.8 |

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

#### <a name="dotnet_style_parentheses_in_other_operators"></a>dotnet\_style\_parentheses\_in\_other_operators

|||
|-|-|
| **Nombre de regla** | dotnet_style_parentheses_in_other_operators |
| **Identificador de la regla** | IDE0047 |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Valores** | `always_for_clarity`: se prefieren los paréntesis para clarificar la prioridad del operador.<br /><br />`never_if_unnecessary`: se prefiere no tener paréntesis cuando la prioridad del operador aritmético es obvia. |
| **Valor predeterminado de Visual Studio** | `never_if_unnecessary:silent` |
| **Versión introducida** | Visual Studio 2017, versión 15.8 |

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

### <a name="expression-level-preferences"></a>Preferencias de nivel de expresión

Las reglas de estilo de esta sección definen las preferencias de nivel de expresión, incluido el uso de inicializadores de objeto, de inicializadores de colección, de nombres de tupla explícitos o inferidos y de tipos anónimos inferidos.

Estas reglas podrían aparecer en un archivo *.editorconfig* como sigue:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_return = true:suggestion
dotnet_style_prefer_compound_assignment = true:suggestion
```

#### <a name="dotnet_style_object_initializer"></a>dotnet\_style\_object_initializer

|||
|-|-|
| **Nombre de regla** | dotnet_style_object_initializer |
| **Identificador de la regla** | IDE0017 |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Valores** | `true`: se prefiere que los objetos se inicialicen con inicializadores de objeto siempre que sea posible.<br /><br />`false`: se prefiere que los objetos *no* se inicialicen con inicializadores de objeto. |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |

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

#### <a name="dotnet_style_collection_initializer"></a>dotnet\_style\_collection_initializer

|||
|-|-|
| **Nombre de regla** | dotnet_style_collection_initializer |
| **Identificador de la regla** | IDE0028 |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Valores** | `true`: se prefiere que las colecciones se inicialicen con inicializadores de colección siempre que sea posible.<br /><br />`false`: se prefiere que las colecciones *no* se inicialicen con inicializadores de colección. |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |

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

#### <a name="dotnet_style_explicit_tuple_names"></a>dotnet\_style\_explicit\_tuple_names

|||
|-|-|
| **Nombre de regla** | dotnet_style_explicit_tuple_names |
| **Identificador de la regla** | IDE0033 |
| **Lenguajes aplicables** | C# 7.0+ y Visual Basic 15+ |
| **Valores** | `true`: se prefieren los nombres de tupla a propiedades ItemX.<br /><br />`false`: se prefieren las propiedades ItemX a nombres de tupla. |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |

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

#### <a name="dotnet_style_prefer_inferred_tuple_names"></a>dotnet\_style\_prefer\_inferred\_tuple_names

|||
|-|-|
| **Nombre de regla** | dotnet_style_prefer_inferred_tuple_names |
| **Identificador de la regla** | IDE0037 |
| **Lenguajes aplicables** | C# 7.1+ y Visual Basic 15+ |
| **Valores** | `true`: se prefieren los nombres de elementos de tupla inferidos.<br /><br />`false`: se prefieren los nombres de elementos de tupla explícitos. |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |
| **Versión introducida** | Visual Studio 2017, versión 15.6 |

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

#### <a name="dotnet_style_prefer_inferred_anonymous_type_member_names"></a>dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names

|||
|-|-|
| **Nombre de regla** | dotnet_style_prefer_inferred_anonymous_type_member_names |
| **Identificador de la regla** | IDE0037 |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Valores** | `true`: se prefieren nombres de miembros de tipo anónimo inferidos.<br /><br />`false`: se prefieren nombres de miembros de tipo anónimo explícitos. |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |
| **Versión introducida** | Visual Studio 2017, versión 15.6 |

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

#### <a name="dotnet_style_prefer_auto_properties"></a>dotnet\_style\_prefer\_auto\_properties

|||
|-|-|
| **Nombre de regla** | dotnet_style_prefer_auto_properties |
| **Identificador de la regla** | IDE0032 |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Valores** | `true`: se prefieren propiedades automáticas antes que campos de respaldo privados.<br /><br />`false`: se prefieren propiedades con campos de respaldo privados antes que propiedades automáticas. |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |
| **Versión introducida** | Visual Studio 2017 versión 15.7 |

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

#### <a name="dotnet_style_prefer_is_null_check_over_reference_equality_method"></a>dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method

|||
|-|-|
| **Nombre de regla** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **Identificador de la regla** | IDE0041 |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Valores** | `true`: se prefiere usar una comprobación de NULL con coincidencia de patrones antes que `object.ReferenceEquals`.<br /><br />`false`: se prefiere `object.ReferenceEquals` en lugar de una comprobación de NULL con coincidencia de patrones. |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |
| **Versión introducida** | Visual Studio 2017 versión 15.7 |

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

#### <a name="dotnet_style_prefer_conditional_expression_over_assignment"></a>dotnet\_style\_prefer\_conditional\_expression\_over_assignment

|||
|-|-|
| **Nombre de regla** | dotnet_style_prefer_conditional_expression_over_assignment |
| **Identificador de la regla** | IDE0045 |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Valores** | `true`: se prefieren asignaciones con un condicional ternario en lugar de una instrucción if-else.<br /><br />`false`: se prefieren asignaciones con una instrucción if-else en lugar de un condicional ternario. |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |
| **Versión introducida** | Visual Studio 2017, versión 15.8 |

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

#### <a name="dotnet_style_prefer_conditional_expression_over_return"></a>dotnet\_style\_prefer\_conditional\_expression\_over_return

|||
|-|-|
| **Nombre de regla** | dotnet_style_prefer_conditional_expression_over_return |
| **Identificador de la regla** | IDE0046 |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Valores** | `true`: se prefiere que las instrucciones de devolución utilicen un condicional ternario en lugar de una instrucción if-else.<br /><br />`false`: se prefiere que las instrucciones de devolución utilicen una instrucción if-else en lugar de un condicional ternario. |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |
| **Versión introducida** | Visual Studio 2017, versión 15.8 |

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

#### <a name="dotnet_style_prefer_compound_assignment"></a>dotnet\_style\_prefer\_compound\_assignment

|||
|-|-|
| **Nombre de regla** | dotnet_style_prefer_compound_assignment |
| **Identificador de la regla** | IDE0054 |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Valores** | `true`: se prefieren expresiones de [asignación compuesta](/dotnet/csharp/language-reference/operators/assignment-operator#compound-assignment)<br /><br />`false`: no se prefieren expresiones de asignación compuesta |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |

Ejemplos de código:

```csharp
// dotnet_style_prefer_compound_assignment = true
x += 1;

// dotnet_style_prefer_compound_assignment = false
x = x + 1;
```

```vb
' dotnet_style_prefer_compound_assignment = true
x += 1

' dotnet_style_prefer_compound_assignment = false
x = x + 1
```

### <a name="null-checking-preferences"></a>Preferencias de la comprobación de NULL

Las reglas de estilo de esta sección tienen que ver con el uso de las preferencias de la comprobación de NULL.

Estas reglas podrían aparecer en un archivo *.editorconfig* como sigue:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
```

#### <a name="dotnet_style_coalesce_expression"></a>dotnet\_style\_coalesce_expression

|||
|-|-|
| **Nombre de regla** | dotnet_style_coalesce_expression |
| **Identificador de la regla** | IDE0029 |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Valores** | `true`: se prefiere la expresión de fusión NULL a la comprobación del operador ternario.<br /><br />`false`: Se prefiere la comprobación del operador ternario a la expresión de fusión NULL. |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |

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

#### <a name="dotnet_style_null_propagation"></a>dotnet\_style\_null_propagation

|||
|-|-|
| **Nombre de regla** | dotnet_style_null_propagation |
| **Identificador de la regla** | IDE0031 |
| **Lenguajes aplicables** | C# 6.0+ y Visual Basic 14+ |
| **Valores** | `true`: Se prefiere usar el operador condicional NULL siempre que sea posible.<br /><br />`false`: Se prefiere usar la comprobación NULL ternaria siempre que sea posible. |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |

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

## <a name="net-code-quality-settings"></a>Configuración de la calidad del código .NET

Las reglas de calidad de esta sección se aplican al código de C# y Visual Basic. Se usan para configurar analizadores de código integrados en el entorno de desarrollo integrado (IDE) de Visual Studio. Para obtener información sobre cómo configurar analizadores de FxCop con un archivo EditorConfig, vea [Configurar los analizadores de FxCop](../code-quality/configure-fxcop-analyzers.md).

- [Preferencias de parámetros](#parameter-preferences)
  - dotnet\_code\_quality\_unused\_parameters

### <a name="parameter-preferences"></a>Preferencias de parámetros

Las reglas de calidad de esta sección se refieren a parámetros de método.

Estas reglas podrían aparecer en un archivo *.editorconfig* como sigue:

```ini
# CSharp and Visual Basic code quality settings:
[*.{cs,vb}]
dotnet_code_quality_unused_parameters = all:suggestion
```

#### <a name="dotnet_code_quality_unused_parameters"></a>dotnet\_code\_quality\_unused\_parameters

|||
|-|-|
| **Nombre de regla** | dotnet_code_quality_unused_parameters |
| **Identificador de la regla** | IDE0060 |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Valores** | `all`: se marcan métodos con cualquier accesibilidad que contengan parámetros no usados<br /><br />`non_public`: solo se marcan métodos no públicos que contengan parámetros no usados |
| **Valor predeterminado de Visual Studio** | `all:suggestion` |

Ejemplos de código:

```csharp
// dotnet_code_quality_unused_parameters = all:suggestion
public int GetNum() { return 1; }

// dotnet_code_quality_unused_parameters = non_public:suggestion
public int GetNum(int arg1) { return 1; }
```

```vb
' dotnet_code_quality_unused_parameters = all:suggestion
Public Function GetNum()
    Return 1
End Function

' dotnet_code_quality_unused_parameters = non_public:suggestion
Public Function GetNum(arg1 As Integer)
    Return 1
End Function
```

## <a name="c-code-style-settings"></a>Configuración del estilo de código de C#

Las reglas de estilo de esta sección solo son aplicables a C#.

- [Tipos implícitos y explícitos](#implicit-and-explicit-types)
  - csharp\_style\_var\_for\_built\_in_types
  - csharp\_style\_var\_when\_type\_is_apparent
  - csharp\_style\_var_elsewhere
- [Miembros con forma de expresión](#expression-bodied-members)
  - csharp\_style\_expression\_bodied_methods
  - csharp\_style\_expression\_bodied_constructors
  - csharp\_style\_expression\_bodied_operators
  - csharp\_style\_expression\_bodied_properties
  - csharp\_style\_expression\_bodied_indexers
  - csharp\_style\_expression\_bodied_accessors
  - csharp\_style\_expression\_bodied_lambdas
  - csharp\_style\_expression\_bodied\_local_functions
- [Coincidencia de patrones](#pattern-matching)
  - csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check
  - csharp\_style\_pattern\_matching\_over\_as\_with\_null_check
- [Declaraciones de variables insertadas](#inlined-variable-declarations)
  - csharp\_style\_inlined\_variable_declaration
- [Preferencias de nivel de expresión](#c-expression-level-preferences)
  - csharp\_prefer\_simple\_default_expression
- [Preferencias de la comprobación de "NULL"](#c-null-checking-preferences)
  - csharp\_style\_throw_expression
  - csharp\_style\_conditional\_delegate_call
- [Preferencias de bloques de código](#code-block-preferences)
  - csharp\_prefer_braces
- [Preferencias de valores no usados](#unused-value-preferences)
  - csharp\_style\_unused\_value\_expression\_statement_preference
  - csharp\_style\_unused\_value\_assignment_preference
- [Preferencias de índices y rangos](#index-and-range-preferences)
  - csharp\_style\_prefer\_index_operator
  - csharp\_style\_prefer\_range_operator
- [Preferencias varias](#miscellaneous-preferences)
  - csharp\_style\_deconstructed\_variable_declaration
  - csharp\_style\_pattern\_local\_over\_anonymous_function
  - csharp\_using\_directive\_placement
  - csharp\_prefer\_static\_local_function
  - csharp\_prefer\_simple\_using_statement
  - csharp\_style\_prefer\_switch_expression

### <a name="implicit-and-explicit-types"></a>Tipos implícitos y explícitos

Las reglas de estilo de esta sección hacen referencia al uso de la palabra clave [var](/dotnet/csharp/language-reference/keywords/var) frente a un tipo explícito en una declaración de variable. Esta regla se puede aplicar por separado a los tipos integrados, cuando el tipo es aparente, y en otros lugares.

Ejemplo del archivo *.editorconfig*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="csharp_style_var_for_built_in_types"></a>csharp\_style\_var\_for\_built\_in_types

|||
|-|-|
| **Nombre de regla** | csharp_style_var_for_built_in_types |
| **Identificador de la regla** | IDE0007 e IDE0008 |
| **Lenguajes aplicables** | C#  |
| **Valores** | `true`: se prefiere usar `var` para declarar variables con tipos de sistema integrados como `int`.<br /><br />`false`: se prefiere el tipo explícito sobre `var` para declarar variables con tipos de sistema integrados como `int`. |
| **Valor predeterminado de Visual Studio** | `true:silent` |

Ejemplos de código:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

#### <a name="csharp_style_var_when_type_is_apparent"></a>csharp\_style\_var\_when\_type\_is_apparent

|||
|-|-|
| **Nombre de regla** | csharp_style_var_when_type_is_apparent |
| **Identificador de la regla** | IDE0007 e IDE0008 |
| **Lenguajes aplicables** | C#  |
| **Valores** | `true`: se prefiere `var` cuando el tipo ya se ha mencionado en el lateral derecho de una expresión de declaración.<br /><br />`false`: se prefiere el tipo explícito en vez de `var` cuando el tipo ya se ha mencionado en el lateral derecho de una expresión de declaración. |
| **Valor predeterminado de Visual Studio** | `true:silent` |

Ejemplos de código:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

#### <a name="csharp_style_var_elsewhere"></a>csharp\_style\_var_elsewhere

|||
|-|-|
| **Nombre de regla** | csharp_style_var_elsewhere |
| **Identificador de la regla** | IDE0007 e IDE0008 |
| **Lenguajes aplicables** | C#  |
| **Valores** | `true`: se prefiere `var` a un tipo explícito en todos los casos, a menos que se reemplace por otra regla de estilo de código.<br /><br />`false`: se prefiere el tipo explícito en vez de `var` en todos los casos, a no ser que otra regla de estilo de código lo reemplace. |
| **Valor predeterminado de Visual Studio** | `true:silent` |

Ejemplos de código:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

### <a name="expression-bodied-members"></a>Miembros con forma de expresión

Las reglas de estilo de esta sección hacen referencia al uso de [miembros con forma de expresión](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members) cuando la lógica consta de una sola expresión. Esta regla se puede aplicar a métodos, constructores, operadores, propiedades, indizadores y descriptores de acceso.

Ejemplo del archivo *.editorconfig*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
csharp_style_expression_bodied_lambdas = true:silent
csharp_style_expression_bodied_local_functions = false:silent
```

#### <a name="csharp_style_expression_bodied_methods"></a>csharp\_style\_expression\_bodied_methods

|||
|-|-|
| **Nombre de regla** | csharp_style_expression_bodied_methods |
| **Identificador de la regla** | IDE0022 |
| **Lenguajes aplicables** | C# 6.0+  |
| **Valores** | `true`: se prefieren cuerpos de expresión para los métodos<br /><br />`when_on_single_line`: se prefieren cuerpos de expresión para los métodos cuando van a ser una sola línea<br /><br />`false`: se prefieren cuerpos de bloque para los métodos. |
| **Valor predeterminado de Visual Studio** | `false:silent` |

Ejemplos de código:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

#### <a name="csharp_style_expression_bodied_constructors"></a>csharp\_style\_expression\_bodied_constructors

|||
|-|-|
| **Nombre de regla** | csharp_style_expression_bodied_constructors |
| **Identificador de la regla** | IDE0021 |
| **Lenguajes aplicables** | C# 7.0+ |
| **Valores** | `true`: se prefieren cuerpos de expresión para los constructores<br /><br />`when_on_single_line`: se prefieren cuerpos de expresión para los constructores cuando van a ser una sola línea<br /><br />`false`: se prefieren cuerpos de bloque para los constructores. |
| **Valor predeterminado de Visual Studio** | `false:silent` |

Ejemplos de código:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

#### <a name="csharp_style_expression_bodied_operators"></a>csharp\_style\_expression\_bodied_operators

|||
|-|-|
| **Nombre de regla** | csharp_style_expression_bodied_operators |
| **Identificador de la regla** | IDE0023 e IDE0024 |
| **Lenguajes aplicables** | C# 7.0+ |
| **Valores** | `true`: se prefieren cuerpos de expresión para los operadores<br /><br />`when_on_single_line`: se prefieren cuerpos de expresión para los operadores cuando van a ser una sola línea<br /><br />`false`: se prefieren cuerpos de bloque para los operadores. |
| **Valor predeterminado de Visual Studio** | `false:silent` |

Ejemplos de código:

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

#### <a name="csharp_style_expression_bodied_properties"></a>csharp\_style\_expression\_bodied_properties

|||
|-|-|
| **Nombre de regla** | csharp_style_expression_bodied_properties |
| **Identificador de la regla** | IDE0025 |
| **Lenguajes aplicables** | C# 7.0+ |
| **Valores** | `true`: se prefieren cuerpos de expresión para las propiedades<br /><br />`when_on_single_line`: se prefieren cuerpos de expresión para las propiedades cuando van a ser una sola línea<br /><br />`false`: se prefieren cuerpos de bloque para las propiedades. |
| **Valor predeterminado de Visual Studio** | `true:silent` |

Ejemplos de código:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

#### <a name="csharp_style_expression_bodied_indexers"></a>csharp\_style\_expression\_bodied_indexers

|||
|-|-|
| **Nombre de regla** | csharp_style_expression_bodied_indexers |
| **Identificador de la regla** | IDE0026 |
| **Lenguajes aplicables** | C# 7.0+ |
| **Valores** | `true`: se prefieren cuerpos de expresión para los indizadores<br /><br />`when_on_single_line`: se prefieren cuerpos de expresión para los indizadores cuando van a ser una sola línea<br /><br />`false`: se prefieren cuerpos de bloque para los indexadores. |
| **Valor predeterminado de Visual Studio** | `true:silent` |

Ejemplos de código:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

#### <a name="csharp_style_expression_bodied_accessors"></a>csharp\_style\_expression\_bodied_accessors

|||
|-|-|
| **Nombre de regla** | csharp_style_expression_bodied_accessors |
| **Identificador de la regla** | IDE0027 |
| **Lenguajes aplicables** | C# 7.0+ |
| **Valores** | `true`: se prefieren cuerpos de expresión para los descriptores de acceso<br /><br />`when_on_single_line`: se prefieren cuerpos de expresión para los descriptores de acceso cuando van a ser una sola línea<br /><br />`false`: se prefieren cuerpos de bloque para los descriptores de acceso. |
| **Valor predeterminado de Visual Studio** | `true:silent` |

Ejemplos de código:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

#### <a name="csharp_style_expression_bodied_lambdas"></a>csharp\_style\_expression\_bodied_lambdas

|||
|-|-|
| **Nombre de regla** | csharp_style_expression_bodied_lambdas |
| **Identificador de la regla** | IDE0053 |
| **Valores** | `true`: se prefieren cuerpos de expresión para las expresiones lambda<br /><br />`when_on_single_line`: se prefieren cuerpos de expresión para las expresiones lambda cuando van a ser una sola línea<br /><br />`false`: se prefieren cuerpos de bloque para las expresiones lambda |
| **Valor predeterminado de Visual Studio** | `true:silent` |

Ejemplos de código:

```csharp
// csharp_style_expression_bodied_lambdas = true
Func<int, int> square = x => x * x;

// csharp_style_expression_bodied_lambdas = false
Func<int, int> square = x => { return x * x; };
```

#### <a name="csharp_style_expression_bodied_local_functions"></a>csharp\_style\_expression\_bodied\_local_functions

A partir de C# 7.0, C# admite [funciones locales](/dotnet/csharp/programming-guide/classes-and-structs/local-functions). Las funciones locales son métodos privados de un tipo que están anidados en otro miembro.

|||
|-|-|
| **Nombre de regla** | csharp_style_expression_bodied_local_functions |
| **Identificador de la regla** | IDE0061 |
| **Lenguajes aplicables** | C# 7.0+ |
| **Valores** | `true`: se prefieren cuerpos de expresión para las funciones locales<br /><br />`when_on_single_line`: se prefieren cuerpos de expresión para las funciones locales cuando van a ser una sola línea<br /><br />`false`: se prefieren cuerpos de bloque para las funciones locales |
| **Valor predeterminado de Visual Studio** | `false:silent` |

Ejemplos de código:

```csharp
// csharp_style_expression_bodied_local_functions = true
void M()
{
    Hello();
    void Hello() => Console.WriteLine("Hello");
}

// csharp_style_expression_bodied_local_functions = false
void M()
{
    Hello();
    void Hello()
    {
        Console.WriteLine("Hello");
    }
}
```

### <a name="pattern-matching"></a>Detección de patrones

Las reglas de estilo de esta sección hacen referencia al uso de la [coincidencia de patrones](/dotnet/csharp/pattern-matching) en C#.

Ejemplo del archivo *.editorconfig*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="csharp_style_pattern_matching_over_is_with_cast_check"></a>csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check

|||
|-|-|
| **Nombre de regla** | csharp_style_pattern_matching_over_is_with_cast_check |
| **Identificador de la regla** | IDE0020 |
| **Lenguajes aplicables** | C# 7.0+ |
| **Valores** | `true`: se prefieren la coincidencia de patrones en lugar de expresiones `is` con conversiones de tipo.<br /><br />`false`: se prefieren expresiones `is` con conversiones de tipo en lugar de la coincidencia de patrones. |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |

Ejemplos de código:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

#### <a name="csharp_style_pattern_matching_over_as_with_null_check"></a>csharp\_style\_pattern\_matching\_over\_as\_with\_null_check

|||
|-|-|
| **Nombre de regla** | csharp_style_pattern_matching_over_as_with_null_check |
| **Identificador de la regla** | IDE0019 |
| **Lenguajes aplicables** | C# 7.0+ |
| **Valores** | `true`: se prefiere la coincidencia de patrones en lugar de expresiones `as` con comprobaciones NULL para determinar si algo es de un tipo determinado.<br /><br />`false`: se prefieren expresiones `as` con comprobaciones NULL en lugar de la coincidencia de patrones para determinar si algo es de un tipo determinado. |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |

Ejemplos de código:

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

### <a name="inlined-variable-declarations"></a>Declaraciones de variables insertadas

Esta regla de estilo se aplica a si las variables `out` se declaran como alineadas o no. A partir de C# 7, puede [declarar una variable de salida en la lista de argumentos de la llamada al método](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument), en lugar de en una declaración de variable independiente.

#### <a name="csharp_style_inlined_variable_declaration"></a>csharp\_style\_inlined\_variable_declaration

|||
|-|-|
| **Nombre de regla** | csharp_style_inlined_variable_declaration |
| **Identificador de la regla** | IDE0018 |
| **Lenguajes aplicables** | C# 7.0+ |
| **Valores** | `true`: se prefiere que las variables `out` se declaren como alineadas en la lista de argumentos de una llamada de método, siempre que sea posible.<br /><br />`false`: se prefiere que las variables `out` se declaren antes de la llamada al método. |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |

Ejemplos de código:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

Ejemplo del archivo *.editorconfig*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

### <a name="c-expression-level-preferences"></a>Preferencias de nivel de expresión de C#

Las reglas de estilo de esta sección se refieren a las preferencias de nivel de expresión.

Ejemplo del archivo *.editorconfig*:

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
```

#### <a name="csharp_prefer_simple_default_expression"></a>csharp\_prefer\_simple\_default_expression

Esta regla de estilo se aplica al uso del [literal `default` para las expresiones de valor predeterminado](/dotnet/csharp/language-reference/operators/default#default-literal) cuando el compilador puede deducir el tipo de la expresión.

|||
|-|-|
| **Nombre de regla** | csharp_prefer_simple_default_expression |
| **Identificador de la regla** | IDE0034 |
| **Lenguajes aplicables** | C# 7.1+  |
| **Valores** | `true`: se prefiere `default` sobre `default(T)`.<br /><br />`false`: se prefiere `default(T)` sobre `default`. |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |

Ejemplos de código:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

### <a name="c-null-checking-preferences"></a>Preferencias de comprobación de NULL de C#

Estas reglas de estilo están relacionadas con la sintaxis de la comprobación de `null`, incluido el uso de expresiones `throw` o instrucciones `throw`, y si se realiza una comprobación de NULL o se usa el operador de incorporación condicional (`?.`) al invocar una [expresión lambda](/dotnet/csharp/lambda-expressions).

Ejemplo del archivo *.editorconfig*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="csharp_style_throw_expression"></a>csharp\_style\_throw_expression

|||
|-|-|
| **Nombre de regla** | csharp_style_throw_expression |
| **Identificador de la regla** | IDE0016 |
| **Lenguajes aplicables** | C# 7.0+ |
| **Valores** | `true`: se prefiere el uso de expresiones `throw` en lugar de instrucciones `throw`.<br /><br />`false`: se prefiere el uso de instrucciones `throw` en lugar de expresiones `throw`. |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |

Ejemplos de código:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

#### <a name="csharp_style_conditional_delegate_call"></a>csharp\_style\_conditional\_delegate_call

|||
|-|-|
| **Nombre de regla** | csharp_style_conditional_delegate_call |
| **Identificador de la regla** | IDE0041 |
| **Lenguajes aplicables** | C# 6.0+  |
| **Valores** | `true`: se prefiere usar el operador de incorporación condicional (`?.`) al invocar una expresión lambda, en lugar de realizar una comprobación de NULL.<br /><br />`false`: se prefiere realizar una comprobación de NULL antes de invocar una expresión lambda en lugar de usar el operador de fusión condicional (`?.`). |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |

Ejemplos de código:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

### <a name="code-block-preferences"></a>Preferencias de bloques de código

Esta regla de estilo se refiere al uso de llaves `{ }` para delimitar los bloques de código.

Ejemplo del archivo *.editorconfig*:

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:silent
```

#### <a name="csharp_prefer_braces"></a>csharp\_prefer\_braces

|||
|-|-|
| **Nombre de regla** | csharp_prefer_braces |
| **Identificador de la regla** | IDE0011 |
| **Lenguajes aplicables** | C# |
| **Valores** | `true`: se prefieren las llaves incluso para una línea de código.<br /><br />`false`: no se prefieren las llaves aunque estén permitidas.<br /><br />`when_multiline`: se prefieren las llaves en varias líneas. |
| **Valor predeterminado de Visual Studio** | `true:silent` |

Ejemplos de código:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

### <a name="unused-value-preferences"></a>Preferencias de valores no usados

Estas reglas de estilo se refieren a expresiones no usadas y asignaciones de valores.

Ejemplo del archivo *.editorconfig*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_unused_value_expression_statement_preference = discard_variable:silent
csharp_style_unused_value_assignment_preference = discard_variable:suggestion
```

#### <a name="csharp_style_unused_value_expression_statement_preference"></a>csharp_style_unused_value_expression_statement_preference

|||
|-|-|
| **Nombre de regla** | csharp_style_unused_value_expression_statement_preference |
| **Identificador de la regla** | IDE0058 |
| **Lenguajes aplicables** | C# |
| **Valores** | `discard_variable`: se prefiere asignar una expresión no usada a un [descarte](/dotnet/csharp/discards) <br /><br />`unused_local_variable`: se prefiere asignar una expresión no usada a una variable local |
| **Valor predeterminado de Visual Studio** | `discard_variable:silent` |

Ejemplos de código:

```csharp
// Original code:
System.Convert.ToInt32("35");

// After code fix for IDE0058:

// csharp_style_unused_value_expression_statement_preference = discard_variable
_ = System.Convert.ToInt32("35");

// csharp_style_unused_value_expression_statement_preference = unused_local_variable
var unused = Convert.ToInt32("35");
```

#### <a name="csharp_style_unused_value_assignment_preference"></a>csharp_style_unused_value_assignment_preference

|||
|-|-|
| **Nombre de regla** | csharp_style_unused_value_assignment_preference |
| **Identificador de la regla** | IDE0059 |
| **Lenguajes aplicables** | C# |
| **Valores** | `discard_variable`: se prefiere usar un [descarte](/dotnet/csharp/discards) al asignar un valor que no se usa<br /><br />`unused_local_variable`: se prefiere usar una variable local al asignar un valor que no se usa |
| **Valor predeterminado de Visual Studio** | `discard_variable:suggestion` |

Ejemplos de código:

```csharp
// csharp_style_unused_value_assignment_preference = discard_variable
int GetCount(Dictionary<string, int> wordCount, string searchWord)
{
    _ = wordCount.TryGetValue(searchWord, out var count);
    return count;
}

// csharp_style_unused_value_assignment_preference = unused_local_variable
int GetCount(Dictionary<string, int> wordCount, string searchWord)
{
    var unused = wordCount.TryGetValue(searchWord, out var count);
    return count;
}
```

### <a name="index-and-range-preferences"></a>Preferencias de índices y rangos

Estas reglas de estilo se refieren al uso de operadores de índice y rango, que están disponibles en C# 8.0 y versiones posteriores.

Ejemplo del archivo *.editorconfig*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_prefer_index_operator = true:suggestion
csharp_style_prefer_range_operator = true:suggestion
```

#### <a name="csharp_style_prefer_index_operator"></a>csharp\_style\_prefer\_index_operator

|||
|-|-|
| **Nombre de regla** | csharp_style_prefer_index_operator |
| **Identificador de la regla** | IDE0056 |
| **Lenguajes aplicables** | C# 8.0+ |
| **Valores** | `true`: se prefiere usar el operador `^` al calcular un índice del final de una colección<br /><br />`false`: no se prefiere usar el operador `^` al calcular un índice del final de una colección |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |

Ejemplos de código:

```csharp
// csharp_style_prefer_index_operator = true
string[] names = { "Archimedes", "Pythagoras", "Euclid" };
var index = names[^1];

// csharp_style_prefer_index_operator = false
string[] names = { "Archimedes", "Pythagoras", "Euclid" };
var index = names[names.Length - 1];
```

#### <a name="csharp_style_prefer_range_operator"></a>csharp\_style\_prefer\_range_operator

|||
|-|-|
| **Nombre de regla** | csharp_style_prefer_range_operator |
| **Identificador de la regla** | IDE0057 |
| **Lenguajes aplicables** | C# 8.0+ |
| **Valores** | `true`: se prefiere usar el operador de rango `..` al extraer un "segmento" de una colección<br /><br />`false`: no se prefiere usar el operador de rango `..` al extraer un "segmento" de una colección |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |

Ejemplos de código:

```csharp
// csharp_style_prefer_range_operator = true
string sentence = "the quick brown fox";
var sub = sentence[0..^4];

// csharp_style_prefer_range_operator = false
string sentence = "the quick brown fox";
var sub = sentence.Substring(0, sentence.Length - 4);
```

### <a name="miscellaneous-preferences"></a>Preferencias varias

Esta sección contiene reglas de estilo varias.

Ejemplo del archivo *.editorconfig*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_using_directive_placement = outside_namespace:silent
csharp_prefer_static_local_function = true:suggestion
csharp_prefer_simple_using_statement = true:suggestion
csharp_style_prefer_switch_expression = true:suggestion
```

#### <a name="csharp_style_deconstructed_variable_declaration"></a>csharp\_style\_deconstructed\_variable_declaration

|||
|-|-|
| **Nombre de regla** | csharp_style_deconstructed_variable_declaration |
| **Identificador de la regla** | IDE0042 |
| **Lenguajes aplicables** | C# 7.0+ |
| **Valores** | `true`: se prefiere la declaración de variable deconstruida.<br /><br />`false`: no se prefiere la deconstrucción de las declaraciones de variable. |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |

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

#### <a name="csharp_style_pattern_local_over_anonymous_function"></a>csharp\_style\_pattern\_local\_over\_anonymous_function

A partir de C# 7.0, C# admite [funciones locales](/dotnet/csharp/programming-guide/classes-and-structs/local-functions). Las funciones locales son métodos privados de un tipo que están anidados en otro miembro.

|||
|-|-|
| **Nombre de regla** | csharp_style_pattern_local_over_anonymous_function |
| **Identificador de la regla** | IDE0039 |
| **Lenguajes aplicables** | C# 7.0+ |
| **Valores** | `true`: se prefieren las funciones locales sobre las funciones anónimas.<br /><br />`false`: se prefieren las funciones anónimas sobre las funciones locales. |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |

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

#### <a name="csharp_using_directive_placement"></a>csharp\_using\_directive_placement

|||
|-|-|
| **Nombre de regla** | csharp_using_directive_placement |
| **Identificador de la regla** | IDE0065 |
| **Lenguajes aplicables** | C# |
| **Valores** | `outside_namespace`: se prefiere colocar las directivas `using` fuera del espacio de nombres<br /><br />`inside_namespace`: se prefiere colocar las directivas `using` dentro del espacio de nombres |
| **Valor predeterminado de Visual Studio** | `outside_namespace:silent` |

Ejemplos de código:

```csharp
// csharp_using_directive_placement = outside_namespace
using System;

namespace Conventions
{
    ...
}

// csharp_using_directive_placement = inside_namespace
namespace Conventions
{
    using System;
    ...
}
```

#### <a name="csharp_prefer_static_local_function"></a>csharp\_prefer\_static\_local_function

|||
|-|-|
| **Nombre de regla** | csharp_prefer_static_local_function |
| **Identificador de la regla** | IDE0062 |
| **Lenguajes aplicables** | C# 8.0+ |
| **Valores** | `true`: se prefiere marcar las funciones locales como `static`<br /><br />`false`: no se prefiere marcar las funciones locales como `static` |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |

Ejemplos de código:

```csharp
// csharp_prefer_static_local_function = true
void M()
{
    Hello();
    static void Hello()
    {
        Console.WriteLine("Hello");
    }
}

// csharp_prefer_static_local_function = false
void M()
{
    Hello();
    void Hello()
    {
        Console.WriteLine("Hello");
    }
}
```

#### <a name="csharp_prefer_simple_using_statement"></a>csharp\_prefer\_simple\_using_statement

|||
|-|-|
| **Nombre de regla** | csharp_prefer_simple_using_statement |
| **Identificador de la regla** | IDE0063 |
| **Lenguajes aplicables** | C# 8.0+ |
| **Valores** | `true`: se prefiere usar una instrucción `using`*simple*<br /><br />`false`: no se prefiere usar una instrucción `using`*simple* |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |

Ejemplos de código:

```csharp
// csharp_prefer_simple_using_statement = true
using var a = b;

// csharp_prefer_simple_using_statement = false
using (var a = b) { }
```

#### <a name="csharp_style_prefer_switch_expression"></a>csharp\_style\_prefer\_switch_expression

|||
|-|-|
| **Nombre de regla** | csharp_style_prefer_switch_expression |
| **Identificador de la regla** | IDE0066 |
| **Lenguajes aplicables** | C# 8.0+ |
| **Valores** | `true`: prefiera usar una expresión `switch` (introducida con C# 8.0)<br /><br />`false`: prefiera usar una [instrucción switch](/dotnet/csharp/language-reference/keywords/switch) |
| **Valor predeterminado de Visual Studio** | `true:suggestion` |
| **Versión introducida** | Visual Studio 2019, versión 16.2 |

Ejemplos de código:

```csharp
// csharp_style_prefer_switch_expression = true
return x switch
{
    1 => 1 * 1,
    2 => 2 * 2,
    _ => 0,
};

// csharp_style_prefer_switch_expression = false
switch (x)
{
    case 1:
        return 1 * 1;
    case 2:
        return 2 * 2;
    default:
        return 0;
}
```

## <a name="see-also"></a>Vea también

- [Convenciones de formato](editorconfig-formatting-conventions.md)
- [Convenciones de nomenclatura](editorconfig-naming-conventions.md)
- [Configuración de la convención de codificación de .NET para EditorConfig](editorconfig-code-style-settings-reference.md)

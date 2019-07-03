---
title: Convenciones de formato de .NET para EditorConfig
ms.date: 06/17/2019
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- formatting conventions [EditorConfig]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 340d8ca7f7b578ae952c0b5024cd6962f20a0dff
ms.sourcegitcommit: b468d71052a1b8a697f477ab23a3644de139f1e9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2019
ms.locfileid: "67262798"
---
# <a name="formatting-conventions"></a>Convenciones de formato

Las convenciones de formato para EditorConfig en Visual Studio se dividen en dos categorías:

- [Configuración de formato de .NET](#net-formatting-settings)

- [Configuración de formato de C#](#c-formatting-settings)

## <a name="rule-format"></a>Formato de regla

Las reglas de convenciones de formato tienen el formato siguiente:

`rule_name = value`

Para muchas reglas, especificará `true` (se prefiere este estilo) o `false` (no se prefiere este estilo) para `value`. Para otras reglas, especifique un valor como `flush_left` o `before_and_after` para describir cuándo y dónde aplicar la regla. No se especifica un nivel de gravedad.

## <a name="net-formatting-settings"></a>Configuración de formato de .NET

Las reglas de formato de esta sección se aplican a C# y al código de Visual Basic.

- [Organización de instrucciones Using](#organize-using-directives)
   - dotnet_sort_system_directives_first
   - dotnet_separate_import_directive_groups

### <a name="organize-using-directives"></a>Organización de directivas using

Estas reglas de formato se refieren a la ordenación y la visualización de directivas `using` y de instrucciones `Imports`.

Ejemplo del archivo *.editorconfig*:

```ini
# .NET formatting settings
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnetsortsystemdirectivesfirst"></a>dotnet\_sort\_system\_directives_first

|||
|-|-|
| **Nombre de la regla** | dotnet_sort_system_directives_first |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Versión introducida** | Visual Studio 2017 versión 15.3 |
| **Valores** | `true`: se ordenan alfabéticamente las directivas System.* `using` del sistema y se colocan antes de cualquier otra directiva using.<br /><br />`false`: no se colocan las directivas System.* `using` antes que otras directivas `using`. |
| **Valor predeterminado de Visual Studio** | `true` |

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

#### <a name="dotnetseparateimportdirectivegroups"></a>dotnet\_separate\_import\_directive\_groups

|||
|-|-|
| **Nombre de la regla** | dotnet_separate_import_directive_groups |
| **Lenguajes aplicables** | C# y Visual Basic |
| **Versión introducida** | Versión 15.5 de Visual Studio 2017 |
| **Valores** | `true`: coloque una línea en blanco entre grupos de directivas `using`.<br /><br />`false`: no coloque una línea en blanco entre grupos de directivas `using`. |
| **Valor predeterminado de Visual Studio** | `false` |

Ejemplos de código:

```csharp
// dotnet_separate_import_directive_groups = true
using System.Collections.Generic;
using System.Threading.Tasks;

using Octokit;

// dotnet_separate_import_directive_groups = false
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;
```

## <a name="c-formatting-settings"></a>Configuración de formato de C#

Las reglas de formato de esta sección se aplican únicamente al código de C#.

- [Opciones de nueva línea](#new-line-options)
   - csharp_new_line_before_open_brace
   - csharp_new_line_before_else
   - csharp_new_line_before_catch
   - csharp_new_line_before_finally
   - csharp_new_line_before_members_in_object_initializers
   - csharp_new_line_before_members_in_anonymous_types
   - csharp_new_line_between_query_expression_clauses
- [Opciones de sangría](#indentation-options)
   - csharp_indent_case_contents
   - csharp_indent_switch_labels
   - csharp_indent_labels
- [Opciones de espaciado](#spacing-options)
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
   - csharp_space_after_comma
   - csharp_space_after_dot
- [Opciones de encapsulado](#wrap-options)
   - csharp_preserve_single_line_statements
   - csharp_preserve_single_line_blocks

### <a name="new-line-options"></a>Opciones de nueva línea

Estas reglas de formato se refieren al uso de nuevas líneas para dar formato al código.

Ejemplo del archivo *.editorconfig*:

```ini
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

#### <a name="csharpnewlinebeforeopenbrace"></a>csharp\_new\_line\_before\_open_brace

Esta regla se refiere a si se debe colocar una llave de apertura `{` en la misma línea que el código anterior, o en una línea nueva. Para esta regla, se especifica **all**, **none** o uno o varios elementos de código como **methods** o **properties** para definir cuándo se debe aplicar esta regla. Para especificar varios elementos de código, sepárelos con una coma (,).

|||
|-|-|
| **Nombre de la regla** | csharp_new_line_before_open_brace |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.3 |
| **Valores** | `all`: se requiere que las llaves estén en una nueva línea para todas las expresiones (estilo "Allman").<br /><br />`none`: se requiere que las llaves estén en una nueva línea para todas las expresiones ("K&R").<br /><br />`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, `properties`, `types`: se requiere que las llaves estén en una línea nueva para el elemento de código especificado (estilo "Allman"). |
| **Valor predeterminado de Visual Studio** | `all` |

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

#### <a name="csharpnewlinebeforeelse"></a>csharp\_new\_line\_before_else

|||
|-|-|
| **Nombre de la regla** | csharp_new_line_before_else |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.3 |
| **Valores** | `true`: las instrucciones `else` se colocan en una nueva línea.<br /><br />`false`: las instrucciones `else` se colocan en la misma línea. |
| **Valor predeterminado de Visual Studio** | `true` |

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

#### <a name="csharpnewlinebeforecatch"></a>csharp\_new\_line\_before_catch

|||
|-|-|
| **Nombre de la regla** | csharp_new_line_before_catch |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.3 |
| **Valores** | `true`: las instrucciones `catch` se colocan en una nueva línea.<br /><br />`false`: las instrucciones `catch` se colocan en la misma línea. |
| **Valor predeterminado de Visual Studio** | `true` |

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

#### <a name="csharpnewlinebeforefinally"></a>csharp\_new\_line\_before_finally

|||
|-|-|
| **Nombre de la regla** | csharp_new_line_before_finally |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.3 |
| **Valores** | `true`: se requiere que las instrucciones `finally` estén en una nueva línea después de la llave de cierre.<br /><br />`false`: se requiere que las instrucciones `finally` estén en la misma línea que la llave de cierre. |
| **Valor predeterminado de Visual Studio** | `true` |

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

#### <a name="csharpnewlinebeforemembersinobjectinitializers"></a>csharp\_new\_line\_before\_members\_in\_object_initializers

|||
|-|-|
| **Nombre de la regla** | csharp_new_line_before_members_in_object_initializers |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.3 |
| **Valores** | `true`: se requiere que los miembros de inicializadores de objeto estén en líneas independientes.<br /><br />`false`: se requiere que los miembros de inicializadores de objeto estén en la misma línea. |
| **Valor predeterminado de Visual Studio** | `true` |

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

#### <a name="csharpnewlinebeforemembersinanonymoustypes"></a>csharp\_new\_line\_before\_members\_in\_anonymous_types

|||
|-|-|
| **Nombre de la regla** | csharp_new_line_before_members_in_anonymous_types |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.3 |
| **Valores** | `true`: se requiere que los miembros de tipos anónimos estén en líneas independientes.<br /><br />`false`: se requiere que los miembros de tipos anónimos estén en la misma línea. |
| **Valor predeterminado de Visual Studio** | `true` |

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

#### <a name="csharpnewlinebetweenqueryexpressionclauses"></a>csharp_new_line_between_query_expression_clauses

|||
|-|-|
| **Nombre de la regla** | csharp_new_line_between_query_expression_clauses |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.3 |
| **Valores** | `true`: se requiere que los elementos de las cláusulas de la expresión de consulta estén en líneas independientes.<br /><br />`false`: se requiere que los elementos de las cláusulas de la expresión de consulta estén en la misma línea. |
| **Valor predeterminado de Visual Studio** | `true` |

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

### <a name="indentation-options"></a>Opciones de sangría

Estas reglas de formato se refieren al uso de la sangría para dar formato al código.

Ejemplo del archivo *.editorconfig*:

```ini
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
```

#### <a name="csharpindentcasecontents"></a>csharp\_indent\_case_contents

|||
|-|-|
| **Nombre de la regla** | csharp_indent_case_contents |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.3 |
| **Valores** | `true`: aplicar sangría al contenido del caso `switch`.<br /><br />`false`: no aplicar sangría al contenido del caso `switch`. |
| **Valor predeterminado de Visual Studio** | `true` |

- Cuando esta regla se establece en **true**, i.
- Cuando esta regla se establece en **false**, d.

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

#### <a name="csharpindentswitchlabels"></a>csharp\_indent\_switch_labels

|||
|-|-|
| **Nombre de la regla** | csharp_indent_switch_labels |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.3 |
| **Valores** | `true`: aplicar sangría a etiquetas `switch`.<br /><br />`false`: no aplicar sangría a etiquetas `switch`. |
| **Valor predeterminado de Visual Studio** | `true` |

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

#### <a name="csharpindentlabels"></a>csharp\_indent_labels

|||
|-|-|
| **Nombre de la regla** | csharp_indent_labels |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.3 |
| **Valores** | `flush_left`: las etiquetas se colocan en la primera columna de la izquierda.<br /><br />`one_less_than_current`: las etiquetas se colocan una sangría menos que el contexto actual.<br /><br />`no_change`: las etiquetas se colocan en la misma sangría que el contexto actual. |
| **Valor predeterminado de Visual Studio** | `no_change` |

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

### <a name="spacing-options"></a>Opciones de espaciado

Estas reglas de formato se refieren al uso de caracteres de espacio para dar formato al código.

Ejemplo del archivo *.editorconfig*:

```ini
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
csharp_space_after_comma = true
csharp_space_after_dot = false
```

#### <a name="csharpspaceaftercast"></a>csharp\_space\_after_cast

|||
|-|-|
| **Nombre de la regla** | csharp_space_after_cast |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.3 |
| **Valores** | `true`: se requiere un espacio entre una conversión y el valor.<br /><br />`false`: _no_ se requiere ningún espacio entre una conversión y el valor. |
| **Valor predeterminado de Visual Studio** | `false` |

Ejemplos de código:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharpspaceafterkeywordsincontrolflowstatements"></a>csharp_space_after_keywords_in_control_flow_statements

|||
|-|-|
| **Nombre de la regla** | csharp_space_after_keywords_in_control_flow_statements |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.3 |
| **Valores** | `true`: se requiere un espacio después de una palabra clave en una instrucción de flujo de control como un bucle `for`.<br /><br />`false`: _no_ se requiere un espacio después de una palabra clave en una instrucción de flujo de control como un bucle `for`. |
| **Valor predeterminado de Visual Studio** | `true` |

Ejemplos de código:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharpspacebetweenmethoddeclarationparameterlistparentheses"></a>csharp_space_between_method_declaration_parameter_list_parentheses

|||
|-|-|
| **Nombre de la regla** | csharp_space_between_method_declaration_parameter_list_parentheses |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.3 |
| **Valores** | `true`: se coloca un carácter de espacio después del paréntesis de apertura y antes del paréntesis de cierre de una lista de parámetros de declaración de método.<br /><br />`false`: no se colocan caracteres de espacio después del paréntesis de apertura y antes del paréntesis de cierre de una lista de parámetros de declaración de método. |
| **Valor predeterminado de Visual Studio** | `false` |

Ejemplos de código:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharpspacebetweenmethodcallparameterlistparentheses"></a>csharp_space_between_method_call_parameter_list_parentheses

|||
|-|-|
| **Nombre de la regla** | csharp_space_between_method_call_parameter_list_parentheses |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.3 |
| **Valores** | `true`: se coloca un carácter de espacio después del paréntesis de apertura y antes del paréntesis de cierre de una llamada de método.<br /><br />`false`: no se colocan caracteres de espacio después del paréntesis de apertura y antes del paréntesis de cierre de una llamada de método. |
| **Valor predeterminado de Visual Studio** | `false` |

Ejemplos de código:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharpspacebetweenparentheses"></a>csharp_space_between_parentheses

|||
|-|-|
| **Nombre de la regla** | csharp_space_between_parentheses |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.3 |
| **Valores** | `control_flow_statements`: se inserta un espacio entre los paréntesis de instrucciones de flujo de control.<br /><br />`expressions`: se inserta un espacio entre los paréntesis de expresiones.<br /><br />`type_casts`: se inserta un espacio entre los paréntesis de las conversiones de tipos. |
| **Valor predeterminado de Visual Studio** | `false` |

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

#### <a name="csharpspacebeforecolonininheritanceclause"></a>csharp\_space\_before\_colon\_in\_inheritance_clause

|||
|-|-|
| **Nombre de la regla** | csharp_space_before_colon_in_inheritance_clause |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.7 |
| **Valores** | `true`: se requiere un espacio antes de los dos puntos para las bases o interfaces en las declaraciones de tipos.<br /><br />`false`: _no_ se requiere ningún espacio antes de los dos puntos para las bases o interfaces en las declaraciones de tipos. |
| **Valor predeterminado de Visual Studio** | `true` |

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

#### <a name="csharpspaceaftercolonininheritanceclause"></a>csharp\_space\_after\_colon\_in\_inheritance_clause

|||
|-|-|
| **Nombre de la regla** | csharp_space_after_colon_in_inheritance_clause |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.7 |
| **Valores** | `true`: se requiere un espacio después de los dos puntos para las bases o interfaces en las declaraciones de tipos.<br /><br />`false`: _no_ se requiere ningún espacio después de los dos puntos para las bases o interfaces en las declaraciones de tipos. |
| **Valor predeterminado de Visual Studio** | `true` |

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

#### <a name="csharpspacearoundbinaryoperators"></a>csharp\_space\_around\_binary_operators

|||
|-|-|
| **Nombre de la regla** | csharp_space_around_binary_operators |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.7 |
| **Valores** | `before_and_after`: se inserta un espacio delante y detrás del operador binario.<br /><br />`none`: se quitan los espacios delante y detrás del operador binario.<br /><br />`ignore`: se omiten los espacios alrededor de operadores binarios, |
| **Valor predeterminado de Visual Studio** | `before_and_after` |

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

#### <a name="csharpspacebetweenmethoddeclarationemptyparameterlistparentheses"></a>csharp_space_between_method_declaration_empty_parameter_list_parentheses

|||
|-|-|
| **Nombre de la regla** | csharp_space_between_method_declaration_empty_parameter_list_parentheses |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.7 |
| **Valores** | `true`: se inserta un espacio dentro de los paréntesis de una lista de parámetros correspondiente a una declaración de método.<br /><br />`false`: se quita el espacio dentro de los paréntesis de una lista de parámetros correspondiente a una declaración de método. |
| **Valor predeterminado de Visual Studio** | `false` |

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

#### <a name="csharpspacebetweenmethodcallnameandopeningparenthesis"></a>csharp_space_between_method_call_name_and_opening_parenthesis

|||
|-|-|
| **Nombre de la regla** | csharp_space_between_method_call_name_and_opening_parenthesis |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.7 |
| **Valores** | `true`: se inserta un espacio entre el nombre de la llamada de método y el paréntesis de apertura.<br /><br />`false`: se quita un espacio entre el nombre de la llamada de método y el paréntesis de apertura. |
| **Valor predeterminado de Visual Studio** | `false` |

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

#### <a name="csharpspacebetweenmethodcallemptyparameterlistparentheses"></a>csharp_space_between_method_call_empty_parameter_list_parentheses

|||
|-|-|
| **Nombre de la regla** | csharp_space_between_method_call_empty_parameter_list_parentheses |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.7 |
| **Valores** | `true`: se inserta un espacio entre paréntesis vacíos de la lista de argumentos.<br /><br />`false`: se quita un espacio entre paréntesis vacíos de la lista de argumentos. |
| **Valor predeterminado de Visual Studio** | `false` |

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

#### <a name="csharpspaceaftercomma"></a>csharp_space_after_comma

|||
|-|-|
| **Nombre de la regla** | csharp_space_after_comma |
| **Lenguajes aplicables** | C# |
| **Valores** | `true`: se inserta un espacio tras una coma.<br /><br />`false`: se quita un espacio después de una coma. |
| **Valor predeterminado de Visual Studio** | `true` |

Ejemplos de código:

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharpspaceafterdot"></a>csharp_space_after_dot

|||
|-|-|
| **Nombre de la regla** | csharp_space_after_dot |
| **Lenguajes aplicables** | C# |
| **Valores** | `true`: se inserta un espacio después de un punto.<br /><br />`false`: se quita un espacio después de un punto. |
| **Valor predeterminado de Visual Studio** | `false` |

Ejemplos de código:

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

### <a name="wrap-options"></a>Opciones de encapsulado

Estas reglas de formato se refieren al uso de líneas individuales frente a líneas separadas para las instrucciones y bloques de código.

Ejemplo del archivo *.editorconfig*:

```ini
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharppreservesinglelinestatements"></a>csharp_preserve_single_line_statements

|||
|-|-|
| **Nombre de la regla** | csharp_preserve_single_line_statements |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.3 |
| **Valores** | `true`: se dejan las instrucciones y declaraciones de miembros en la misma línea.<br /><br />`false`: se dejan las instrucciones y declaraciones de miembros en líneas diferentes. |
| **Valor predeterminado de Visual Studio** | `true` |

Ejemplos de código:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharppreservesinglelineblocks"></a>csharp_preserve_single_line_blocks

|||
|-|-|
| **Nombre de la regla** | csharp_preserve_single_line_blocks |
| **Lenguajes aplicables** | C# |
| **Versión introducida** | Visual Studio 2017 versión 15.3 |
| **Valores** | `true`: se deja el bloque de código en una sola línea.<br /><br />`false`: se deja el bloque de código en líneas independientes. |
| **Valor predeterminado de Visual Studio** | `true` |

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

## <a name="see-also"></a>Vea también

- [Convenciones de lenguaje](editorconfig-language-conventions.md)
- [Convenciones de nomenclatura](editorconfig-naming-conventions.md)
- [Configuración de la convención de codificación de .NET para EditorConfig](editorconfig-code-style-settings-reference.md)
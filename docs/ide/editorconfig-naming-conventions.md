---
title: Convenciones de nomenclatura .NET para archivos EditorConfig
ms.date: 08/07/2019
ms.topic: reference
helpviewer_keywords:
- naming conventions [EditorConfig]
- EditorConfig naming conventions
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ff6c9885bd01a94cc36046faf71067e1fe9c17b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650911"
---
# <a name="net-naming-conventions-for-editorconfig"></a>Convenciones de nomenclatura .NET para EditorConfig

Las convenciones de nomenclatura están relacionadas con los nombres de elementos de código como clases, propiedades y métodos. Por ejemplo, puede especificar que los miembros públicos deben escribirse en mayúsculas, o que los métodos asincrónicos deben terminar en "Async". Puede aplicar estas reglas si las especifica en un [archivo .editorconfig](../ide/create-portable-custom-editor-options.md). Las infracciones de reglas de nomenclatura aparecen en la **lista de errores** o como una sugerencia debajo del nombre, según la gravedad que elija para la regla. No es necesario compilar el proyecto para ver las infracciones.

Para cada convención de nomenclatura, debe especificar los símbolos a los que se aplica, un estilo de nomenclatura y una gravedad de aplicación de la convención, con las propiedades que se describen a continuación. El orden de las propiedades no es importante.

Para comenzar, elija un título para la regla de nomenclatura que va a usar en cada una de las propiedades que se necesitan para describir completamente la regla. Por ejemplo, `public_members_must_be_capitalized` es un buen nombre descriptivo para una regla de nomenclatura. En esta página se hará referencia al título que elija como **<namingRuleTitle\>** en las secciones siguientes.

## <a name="symbols"></a>Símbolos

En primer lugar, identifique un grupo de símbolos al que aplicar la regla de nomenclatura. Esta propiedad tiene el formato siguiente:

`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`

Asigne un nombre al grupo de símbolos reemplazando el valor **<títuloDelSímbolo\>** con un título descriptivo, por ejemplo `public_symbols`. Usará el valor **<títuloDelSímbolo\>** en los tres nombres de propiedad que describen los símbolos a los que se aplica la regla (tipos de símbolos, niveles de accesibilidad y modificadores).

### <a name="kinds-of-symbols"></a>Tipos de símbolos

Para describir el tipo de símbolos a los que se aplica la regla de nomenclatura, especifique una propiedad con el formato siguiente:

`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = <values>`

En la lista siguiente se muestran los valores permitidos y puede especificar varios valores si los separa con una coma.

- \* (use este valor para especificar todos los símbolos)
- namespace
- clase
- struct
- interfaz
- enum
- propiedad
- método
- campo
- evento
- delegado
- parámetro
- type_parameter
- locales
- local_function

### <a name="accessibility-levels-of-symbols"></a>Niveles de accesibilidad de símbolos

Para describir los niveles de accesibilidad de los símbolos a los que quiere aplicar la regla de nomenclatura, especifique un nombre de propiedad con el formato siguiente:

`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = <values>`

En la lista siguiente se muestran los valores permitidos y puede especificar varios valores si los separa con una coma.

- \* (use este valor para especificar todos los niveles de accesibilidad)
- public
- internal o friend
- private
- protected
- protected\_internal o protected_friend
- private\_protected
- locales

   El nivel de accesibilidad `local` se aplica a los símbolos definidos dentro de un método. Es útil para definir las convenciones de nomenclatura de los símbolos cuya accesibilidad no puede especificarse en el código. Por ejemplo, si especifica `applicable_accessibilities = local` en una convención de nomenclatura para las constantes (`required_modifiers = const`), la regla se aplica únicamente a las constantes definidas dentro de un método y no a las definidas en un tipo.

   ```csharp
   class TypeName
   {
     // Constant defined in a type.
     const int X = 3;

     void Method()
     {
       // Constant defined in a method with "local" accessibility.
       const int Y = 4;
     }
   }
   ```

### <a name="symbol-modifiers-optional"></a>Modificadores de símbolo (opcionales)

Para describir los modificadores de los símbolos a los que quiere aplicar la regla de nomenclatura, especifique un nombre de propiedad con el formato siguiente:

`dotnet_naming_symbols.<symbolTitle>.required_modifiers = <values>`

En la lista siguiente se muestran los valores permitidos (separe los distintos valores con una coma):

- `abstract` o `must_inherit`
- `async`
- `const`
- `readonly`
- `static` o `shared`

   > [!NOTE]
   > Si tiene una regla de nomenclatura para los símbolos `static` o `shared`, también se aplica a símbolos `const` porque son implícitamente estáticos. Si no desea que la regla de nomenclatura `static` se aplique a símbolos `const`, cree una regla de nomenclatura independiente para los símbolos `const`.

Una regla de nomenclatura coincide con las firmas que tienen *todos* los modificadores especificados en `required_modifiers`. Si se omite esta propiedad, se usa el valor predeterminado de una lista vacía, es decir, no se necesitan modificadores específicos para una coincidencia. Esto significa que los modificadores de un símbolo no influyen positiva o negativamente en la aplicación de esta regla.

> [!TIP]
> No se especifica un valor de `*` para `required_modifiers`. En su lugar, simplemente omita por completo la propiedad `required_modifiers` y la regla de nomenclatura se aplicará a todo tipo de modificador.

## <a name="style"></a>Estilo

Ahora que ha identificado el grupo de símbolos al que aplicar la regla de nomenclatura, puede describir el estilo de nomenclatura. Un estilo puede ser que el nombre tenga un prefijo o sufijo determinado, o bien que palabras individuales del nombre se separen con un carácter determinado. También puede especificar un estilo de uso de mayúsculas. La propiedad de estilo tiene el formato siguiente:

`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`

Asigne un nombre al estilo reemplazando el valor **<títuloDelEstilo\>** por un título descriptivo, por ejemplo `first_word_upper_case_style`. Usará el valor **<títuloDelEstilo\>** en los nombres de propiedades que describen el estilo de nomenclatura (prefijo, sufijo, carácter separador de palabras y uso de mayúsculas). Use una o varias de estas propiedades para describir el estilo.

### <a name="require-a-prefix"></a>Requerir un prefijo

Para especificar que los nombres de símbolo deben empezar con determinados caracteres, use esta propiedad:

`dotnet_naming_style.<styleTitle>.required_prefix = <prefix>`

### <a name="require-a-suffix"></a>Requerir un sufijo

Para especificar que los nombres de símbolo deben terminar con determinados caracteres, use esta propiedad:

`dotnet_naming_style.<styleTitle>.required_suffix = <suffix>`

### <a name="require-a-certain-word-separator"></a>Requerir un separador de palabras determinado

Para especificar que las palabras individuales en los nombres de símbolo deben separarse con un carácter determinado, use esta propiedad:

`dotnet_naming_style.<styleTitle>.word_separator = <separator character>`

### <a name="require-a-capitalization-style"></a>Requerir un estilo de uso de mayúsculas

Para especificar un estilo de uso de mayúsculas determinado para los nombres de símbolo, use esta propiedad:

`dotnet_naming_style.<styleTitle>.capitalization = <value>`

Los valores permitidos para esta propiedad son:

- pascal_case
- camel_case
- first\_word_upper
- all\_upper
- all_lower

> [!NOTE]
> Debe especificar un estilo de uso de mayúsculas como parte del estilo de nomenclatura; en caso contrario, es posible que el estilo de nomenclatura se ignore.

## <a name="severity"></a>Gravedad

Para describir la gravedad de una infracción de la regla de nomenclatura, especifique una propiedad con el formato siguiente:

`dotnet_naming_rule.<namingRuleTitle>.severity = <value>`

En la tabla siguiente se muestran los valores de gravedad permitidos y lo que significan:

Gravedad | Efecto
------------ | -------------
ninguna | La regla se suprime por completo.
refactoring o silent | Cuando no se sigue este estilo, no se muestra nada al usuario, pero el código generado automáticamente sigue este estilo.
suggestion | Cuando no se sigue este estilo, se muestra al usuario como una sugerencia (como puntos debajo de los dos primeros caracteres). No tiene ningún efecto en tiempo de compilación.
warning | Cuando no se sigue este estilo, se muestra una advertencia del compilador en la **lista de errores**.
error | Cuando no se sigue este estilo, se muestra un error del compilador en la **lista de errores**.

> [!NOTE]
> No tiene que volver a compilar el proyecto para ver las infracciones de reglas de nomenclatura. Aparecen mientras se modifica el código, ya sea en la **lista de errores** o como una sugerencia.

## <a name="rule-order"></a>Orden de las reglas

::: moniker range="vs-2017"

Las convenciones de nomenclatura deben ordenarse de la más específica a la menos específica en el archivo EditorConfig. La primera regla encontrada que se puede aplicar es la única que se aplica. Sin embargo, si hay varias *propiedades* de regla con el mismo nombre, la prioridad la tiene la última propiedad encontrada con ese nombre. Para más información, consulte [Prioridad y jerarquía de los archivos](create-portable-custom-editor-options.md#file-hierarchy-and-precedence).

::: moniker-end

::: moniker range=">=vs-2019"

A partir de la versión 16.2 de Visual Studio 2019, no importa el orden en el que se definan las reglas de nomenclatura de un archivo EditorConfig. Por el contrario, Visual Studio ordena las reglas de nomenclatura automáticamente según la definición de las propias reglas. La [extensión de servicio de lenguaje de EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) puede analizar un archivo EditorConfig y notificar los casos en los que el orden de las reglas del archivo es diferente al que va a usar el compilador en tiempo de ejecución.

Si usa una versión anterior de Visual Studio, las convenciones de nomenclatura deben ordenarse de la más a la menos específica en el archivo EditorConfig. La primera regla encontrada que se puede aplicar es la única que se aplica. Sin embargo, si hay varias *propiedades* de regla con el mismo nombre, la prioridad la tiene la última propiedad encontrada con ese nombre. Para más información, consulte [Prioridad y jerarquía de los archivos](create-portable-custom-editor-options.md#file-hierarchy-and-precedence).

::: moniker-end

## <a name="default-naming-styles"></a>Estilos de nomenclatura predeterminados

Si no especifica ninguna regla de nomenclatura personalizada, Visual Studio usa los siguientes estilos predeterminados:

- Para clases, estructuras, enumeraciones, propiedades y eventos con accesibilidad `public`, `private`, `internal`, `protected` o `protected_internal`, el estilo de nomenclatura predeterminado es Pascal Case.

- Para interfaces con accesibilidad `public`, `private`, `internal`, `protected` o `protected_internal`, el estilo de nomenclatura predeterminado es Pascal Case con el prefijo necesario **l**.

## <a name="example"></a>Ejemplo

El archivo *.editorconfig* siguiente contiene una convención de nomenclatura que especifica que las propiedades, los métodos, los campos, los eventos y los delegados públicos deben escribirse en mayúsculas. Tenga en cuenta que esta convención de nomenclatura especifica varios tipos de símbolo a los que aplicar la regla, con una coma para separar los valores.

```ini
# Public members must be capitalized (public_members_must_be_capitalized)
[*.{cs,vb}]
dotnet_naming_rule.public_members_must_be_capitalized.symbols   = public_symbols
dotnet_naming_symbols.public_symbols.applicable_kinds           = property,method,field,event,delegate
dotnet_naming_symbols.public_symbols.applicable_accessibilities = public
dotnet_naming_symbols.public_symbols.required_modifiers         = readonly

dotnet_naming_rule.public_members_must_be_capitalized.style    = first_word_upper_case_style
dotnet_naming_style.first_word_upper_case_style.capitalization = first_word_upper

dotnet_naming_rule.public_members_must_be_capitalized.severity = suggestion
```

En la captura de pantalla siguiente se muestra el efecto de esta convención de nomenclatura en el editor. Se han nombrado dos variables públicas sin usar mayúscula en la primera letra. Una es `const` y la otra es `readonly`. Puesto que la regla de nomenclatura solo se aplica a símbolos `readonly`, solo la variable `readonly` muestra una sugerencia de regla de nomenclatura.

![Sugerencia de regla de nomenclatura](media/editorconfig-naming-rule-suggestion.png)

Ahora se va a cambiar la gravedad de la infracción a `warning`:

```ini
dotnet_naming_rule.public_members_must_be_capitalized.severity = warning
```

Si cierra y vuelve a abrir el archivo de código, en lugar de ver la sugerencia debajo de la infracción de nombre, verá una línea ondulada de color verde y una advertencia en la lista de errores:

![Advertencia de regla de nomenclatura](media/editorconfig-naming-rule-warning.png)

## <a name="see-also"></a>Vea también

- [Convenciones de lenguaje](editorconfig-language-conventions.md)
- [Convenciones de formato](editorconfig-formatting-conventions.md)
- [Roslyn naming conventions](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63) (Convenciones de nomenclatura de Roslyn)
- [Crear opciones del editor personalizadas y portátiles](../ide/create-portable-custom-editor-options.md)
- [Configuración de la convención de codificación de .NET para EditorConfig](editorconfig-code-style-settings-reference.md)

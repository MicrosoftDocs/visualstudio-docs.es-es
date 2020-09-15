---
title: Configurar analizadores de calidad de código de .NET mediante editorconfig
ms.date: 09/01/2020
ms.topic: conceptual
helpviewer_keywords:
- .NET analyzers
- FxCop analyzers, configuring
- code quality
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 4016699e6329bf6b1755b49cae0986770699fabe
ms.sourcegitcommit: d77da260d79471ab139973c51d65b04e0f80fe2e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2020
ms.locfileid: "90560767"
---
# <a name="configure-net-code-quality-analyzers-with-editorconfig"></a>Configurar analizadores de calidad de código de .NET con EditorConfig

A partir de .NET 5,0, los analizadores de calidad de código ([ `CAxxxx` reglas](code-analysis-for-managed-code-warnings.md)) se incluyen con el [SDK de .net](/dotnet/fundamentals/productivity/code-analysis.md/#code-quality-analysis). Cada analizador de calidad de código se puede refinar para que se aplique a las partes del código base mediante opciones configurables. Cada opción se especifica agregando un par clave-valor a un archivo [EditorConfig](https://editorconfig.org) . Un archivo de configuración puede ser específico de un archivo, proyecto, solución o todo el repositorio.

> [!TIP]
> Agregue un archivo. editorconfig al proyecto haciendo clic con el botón derecho en el proyecto en **Explorador de soluciones** y seleccionando **Agregar**  >  **nuevo elemento**. En la ventana **Agregar nuevo elemento** , escriba **editorconfig** en el cuadro de búsqueda. Seleccione la plantilla **archivo editorconfig (valor predeterminado)** y elija **Agregar**.
>
> ![Agregar archivo EditorConfig al proyecto en Visual Studio](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Para obtener información sobre la configuración de la gravedad de una regla (por ejemplo, si es un error o una advertencia), vea [establecer la gravedad de la regla en un archivo EditorConfig](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). O bien, puede elegir uno de los [conjuntos de reglas o los archivos EditorConfig](analyzer-rule-sets.md) integrados para habilitar o deshabilitar rápidamente una categoría de reglas.

::: moniker-end

En el resto de este artículo se describe la sintaxis general de las opciones que delimitan dónde se aplican los analizadores de calidad de código de .NET.

## <a name="option-scopes"></a>Ámbitos de opción

Cada opción de refinamiento se puede configurar para todas las reglas, para una categoría de reglas (por ejemplo, seguridad o diseño) o para una regla específica.

### <a name="all-rules"></a>Todas las reglas

La sintaxis para configurar una opción para *todas* las reglas es la siguiente:

|Sintaxis|Ejemplo|
|-|-|
| dotnet_code_quality.OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Categoría de reglas

La sintaxis para configurar una opción para una *categoría* de reglas (como nombre, diseño o rendimiento) es la siguiente:

|Sintaxis|Ejemplo|
|-|-|
| dotnet_code_quality.RuleCategory.OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Regla específica

La sintaxis para configurar una opción para una regla *específica* es la siguiente:

|Sintaxis|Ejemplo|
|-|-|
| dotnet_code_quality. . Nombredeopción = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="options-for-net-code-quality-analyzers"></a>Opciones para los analizadores de calidad de código de .NET

Puede especificar opciones en un [archivo EditorConfig](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project). Por ejemplo, puede especificar las siguientes opciones.

> [!TIP]
> Para ver la lista completa de las opciones disponibles, consulte este [archivo Configuration.MD del analizador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md). Este es un ejemplo de cómo se documenta una opción en el archivo *Configuration.MD del analizador* :
>
> Nombre de la opción: `sufficient_IterationCount_for_weak_KDF_algorithm`\
> Valores de opción: valores enteros \
> Valor predeterminado: específico de cada regla configurable (' 100000 ' de forma predeterminada para la mayoría de las reglas) \
> Ejemplo: `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

### <a name="api_surface"></a>api_surface

| Descripción | Valores permitidos | Valor predeterminado | Reglas configurables |
| - | - | - | - |
| Qué parte de la superficie de API se va a analizar | `public`<br/>`internal` o `friend`<br/>`private`<br/>`all`<br/><br/>Separar varios valores con una coma (,) | `public` | [CA1000](ca1000.md) [CA1003](ca1003.md) [CA1008](ca1008.md) [CA1010](ca1010.md)<br/>[CA1012](ca1012.md) [CA1024](ca1024.md) [CA1027](ca1027.md) [CA1028](ca1028.md)<br/>[CA1030](ca1030.md) [CA1036](ca1036.md) [CA1040](ca1040.md) [CA1041](ca1041.md)<br/>[CA1043](ca1043.md) [CA1044](ca1044.md) [CA1051](ca1051.md) [CA1052](ca1052.md)<br/>[CA1054](ca1054.md) [CA1055](ca1055.md) [CA1056](ca1056.md) [CA1058](ca1058.md)<br/>[CA1063](ca1063.md) [CA1708](ca1708.md) [CA1710](ca1710.md) [CA1711](ca1711.md)<br/>[CA1714](ca1714.md) [CA1715](ca1715.md) [CA1716](ca1716.md) [CA1717](ca1717.md)<br/>[CA1720](ca1720.md) [CA1721](ca1721.md) [CA1725](ca1725.md) [CA1801](ca1801.md)<br/>[CA1802](ca1802.md) [CA1815](ca1815.md) [CA1819](ca1819.md) [CA2217](ca2217.md)<br/>[CA2225](ca2225.md) [CA2226](ca2226.md) [CA2231](ca2231.md) [CA2234](ca2234.md)<br/>|

### <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Descripción | Valores permitidos | Valor predeterminado | Reglas configurables |
| - | - | - | - |
| Si se omiten los métodos asincrónicos que no devuelven un valor | `true`<br/>`false` | `false` | [CA2007](ca2007.md) |

> [!NOTE]
> En la versión 2.6.3 y versiones anteriores del paquete de analizador, esta opción se denominaba `skip_async_void_methods` .

### <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Descripción | Valores permitidos | Valor predeterminado | Reglas configurables |
| - | - | - | - |
| Si se van a excluir de la regla [los parámetros de tipo](/dotnet/csharp/programming-guide/generics/generic-type-parameters) de un solo carácter, por ejemplo, `S` en `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715.md) |

> [!NOTE]
> En la versión 2.6.3 y versiones anteriores del paquete de analizador, esta opción se denominaba `allow_single_letter_type_parameters` .

### <a name="output_kind"></a>output_kind

| Descripción | Valores permitidos | Valor predeterminado | Reglas configurables |
| - | - | - | - |
| Especifica que debe analizarse el código de un proyecto que genera este tipo de ensamblado. | Uno o más campos de la <xref:Microsoft.CodeAnalysis.OutputKind> enumeración<br/><br/>Separar varios valores con una coma (,) | Todos los tipos de salida | [CA2007](ca2007.md) |

### <a name="required_modifiers"></a>required_modifiers

| Descripción | Valores permitidos | Valor predeterminado | Reglas configurables |
| - | - | - | - |
| Especifica los modificadores necesarios para las API que se deben analizar. | Uno o más valores de la siguiente tabla de modificadores permitidos<br/><br/>Separar varios valores con una coma (,) | Depende de cada regla | [CA1802](ca1802.md) |

| Modificador permitido | Resumen |
| --- | --- |
| `none` | No hay ningún requisito modificador |
| `static` o `Shared` | Se debe declarar como ' Static ' (' Shared ' en Visual Basic) |
| `const` | Se debe declarar como ' const ' |
| `readonly` | Se debe declarar como ' readonly ' |
| `abstract` | Se debe declarar como ' Abstract ' |
| `virtual` | Se debe declarar como ' virtual ' |
| `override` | Se debe declarar como ' override ' |
| `sealed` | Se debe declarar como ' Sealed ' |
| `extern` | Se debe declarar como ' extern ' |
| `async` | Se debe declarar como ' Async ' |

### <a name="exclude_extension_method_this_parameter"></a>exclude_extension_method_this_parameter

| Descripción | Valores permitidos | Valor predeterminado | Reglas configurables |
| - | - | - | - |
| Indica si se omitirá el análisis del `this` parámetro de los métodos de extensión | `true`<br/>`false` | `false` | [CA1062](ca1062.md) |

### <a name="null_check_validation_methods"></a>null_check_validation_methods

| Descripción | Valores permitidos | Valor predeterminado | Reglas configurables |
| - | - | - | - |
| Los nombres de métodos de validación de comprobación null que validan los argumentos pasados al método no son NULL | Formatos de nombre de método permitidos (separados por `|` ):<br/> -Solo nombre del método (incluye todos los métodos con el nombre, sin tener en cuenta el tipo o espacio de nombres contenedor)<br/> -Nombres completos en el [formato de identificador de documentación](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)del símbolo, con un `M:` prefijo opcional | None | [CA1062](ca1062.md) |

### <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| Descripción | Valores permitidos | Valor predeterminado | Reglas configurables |
| - | - | - | - |
| Nombres de métodos de formato de cadena adicionales | Formatos de nombre de método permitidos (separados por `|` ):<br/> -Solo nombre del método (incluye todos los métodos con el nombre, sin tener en cuenta el tipo o espacio de nombres contenedor)<br/> -Nombres completos en el [formato de identificador de documentación](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)del símbolo, con un `M:` prefijo opcional | None | [CA2241](ca2241.md) |

### <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| Descripción | Valores permitidos | Valor predeterminado | Reglas configurables |
| - | - | - | - |
| Nombres de tipos, de modo que el tipo y todos sus tipos derivados se excluyen para el análisis | Formatos de nombre de símbolos permitidos (separados por `|` ):<br/> -Solo nombre de tipo (incluye todos los tipos con el nombre, independientemente del tipo o espacio de nombres contenedor)<br/> -Nombres completos en el [formato de identificador de documentación](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)del símbolo, con un `T:` prefijo opcional | None | [CA1303](ca1303.md) |

### <a name="excluded_symbol_names"></a>excluded_symbol_names

| Descripción | Valores permitidos | Valor predeterminado | Reglas configurables |
| - | - | - | - |
| Nombres de los símbolos que se excluyen para el análisis | Formatos de nombre de símbolos permitidos (separados por `|` ):<br/> -Solo nombre de símbolo (incluye todos los símbolos con el nombre, independientemente del tipo o espacio de nombres contenedor)<br/> -Nombres completos en el [formato de ID](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format). de documentación del símbolo. Cada nombre de símbolo requiere un prefijo de tipo de símbolo, como el prefijo "M:" para los métodos, el prefijo "T:" para los tipos, el prefijo "N:" para los espacios de nombres, etc.<br/> - `.ctor` para constructores y `.cctor` para constructores estáticos | None | [CA1062](ca1062.md) [CA1303](ca1303.md) [CA2000](ca2000.md) [CA2100](ca2100.md) [CA2301](ca2301.md) [CA2302](ca2302.md)<br/>[CA2311](ca2311.md) [CA2312](ca2312.md) [CA2321](ca2321.md) [CA2322](ca2322.md) [CA2327](ca2327.md) [CA2328](ca2328.md)<br/>[CA2329](ca2329.md) [CA2330](ca2330.md) [CA3001](ca3001.md) [CA3002](ca3002.md) [CA3003](ca3003.md) [CA3004](ca3004.md)<br/>[CA3005](ca3005.md) [CA3006](ca3006.md) [CA3007](ca3007.md) [CA3008](ca3008.md) [CA3009](ca3009.md) [CA3010](ca3010.md)<br/>[CA3011](ca3011.md) [CA3012](ca3012.md) [CA5361](ca5361.md) CA5376 CA5377 [CA5378](ca5378.md)<br/>[CA5380](ca5380.md) [CA5381](ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](ca5389.md) CA5390 |

### <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| Descripción | Valores permitidos | Valor predeterminado | Reglas configurables |
| - | - | - | - |
| Nombres de los símbolos que no se permiten en el contexto del análisis | Formatos de nombre de símbolos permitidos (separados por `|` ):<br/> -Solo nombre de símbolo (incluye todos los símbolos con el nombre, independientemente del tipo o espacio de nombres contenedor)<br/> -Nombres completos en el [formato de ID](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format). de documentación del símbolo. Cada nombre de símbolo requiere un prefijo de tipo de símbolo, como el prefijo "M:" para los métodos, el prefijo "T:" para los tipos, el prefijo "N:" para los espacios de nombres, etc.<br/> - `.ctor` para constructores y `.cctor` para constructores estáticos | None | [CA1031](ca1031.md) |

## <a name="enable-a-category-of-rules"></a>Habilitar una categoría de reglas

Los paquetes de analizador pueden incluir archivos de conjunto de [reglas](using-rule-sets-to-group-code-analysis-rules.md) y/o [EditorConfig](use-roslyn-analyzers.md#configure-severity-levels) predefinidos que facilitan y agilizan la habilitación de una categoría de reglas, como reglas de seguridad o de diseño. El paquete del analizador de NuGet [Microsoft. CodeAnalysis. NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) incluye tanto archivos EditorConfig como conjuntos de reglas. Al habilitar una categoría específica de reglas, puede identificar problemas de destino y condiciones específicas.

> [!NOTE]
> La habilitación de las reglas del analizador y el establecimiento de su gravedad mediante un archivo EditorConfig se admite a partir de la versión 16,3 de Visual Studio 2019.

El paquete NuGet de NetAnalyzers incluye los conjuntos de reglas y los archivos EditorConfig predefinidos para las siguientes categorías de reglas:

- Todas las reglas
- Flujo de datos
- Diseño
- Documentación
- Globalización
- Interoperabilidad
- Capacidad de mantenimiento
- Nomenclatura
- Rendimiento
- Trasladado desde FxCop
- Confiabilidad
- Seguridad
- Uso

Cada una de esas categorías de reglas tiene un EditorConfig o un archivo de conjunto de reglas para:

- Habilitar todas las reglas de la categoría (y deshabilitar todas las demás reglas)
- Usar la gravedad predeterminada de cada regla y habilitarla de forma predeterminada (y deshabilitar todas las demás reglas)

> [!TIP]
> La categoría "todas las reglas" tiene un EditorConfig adicional o un archivo de conjunto de reglas para deshabilitar todas las reglas. Use este archivo para deshacerse rápidamente de cualquier error o advertencia del analizador en un proyecto.

> [!TIP]
> Si va a migrar desde el análisis de "FxCop" heredado al análisis de código basado en .NET Compiler Platform, los archivos de conjunto de reglas y EditorConfig permiten seguir usando configuraciones de reglas similares a [las que usó anteriormente](rule-set-reference.md).

## <a name="predefined-editorconfig-files"></a>Archivos EditorConfig predefinidos

Los archivos EditorConfig predefinidos para el paquete Microsoft. CodeAnalysis. NetAnalyzers Analyzer se encuentran en el directorio *% userprofile% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \editorconfig* . Por ejemplo, el archivo EditorConfig para habilitar todas las reglas de seguridad se encuentra en *% userprofile% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \editorconfig\SecurityRulesEnabled \\ . EditorConfig*.

Copie el archivo. editorconfig elegido en el directorio raíz del proyecto.

## <a name="predefined-rule-sets"></a>Conjunto de reglas predefinidas

Los archivos de conjunto de reglas predefinidos para el paquete Microsoft. CodeAnalysis. NetAnalyzers Analyzer se encuentran en el directorio *% userprofile% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \rulesets* . Por ejemplo, el archivo de conjunto de reglas para habilitar todas las reglas de seguridad se encuentra en *% userprofile% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \rulesets\SecurityRulesEnabled.ruleset*.

Copie uno o más conjuntos de reglas y péguelos en el directorio que contiene el proyecto de Visual Studio o directamente en **Explorador de soluciones**.

También puede [personalizar un conjunto de reglas predefinidas según](how-to-create-a-custom-rule-set.md) sus preferencias. Por ejemplo, puede cambiar la gravedad de una o varias reglas para que las infracciones aparezcan como errores o advertencias en el **lista de errores**.


## <a name="see-also"></a>Consulte también

- [Configuración del analizador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Convenciones de código de .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)

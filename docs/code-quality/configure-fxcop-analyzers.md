---
title: Configurar analizadores de calidad de código de .NET mediante editorconfig
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- .NET analyzers
- FxCop analyzers, configuring
- code quality
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fbd30859c5ee3dbbea80c6d88d68c0211da62c88
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2020
ms.locfileid: "88706586"
---
# <a name="configure-net-code-quality-analyzers"></a>Configurar analizadores de calidad de código de .NET

Para determinados analizadores de calidad de código de .NET (aquellos cuyos identificadores de regla comienzan con `CA` ), puede refinar qué partes del código base deben aplicarse a través de [las opciones configurables](fxcop-analyzer-options.md). Cada opción se especifica agregando un par clave-valor a un archivo [EditorConfig](https://editorconfig.org) . Un archivo de configuración puede ser específico de un archivo, proyecto, solución o todo el repositorio.

> [!TIP]
> Agregue un archivo. editorconfig al proyecto; para ello, haga clic con el botón derecho en el proyecto en **Explorador de soluciones** y seleccione **Agregar**  >  **nuevo elemento**. En la ventana **Agregar nuevo elemento** , escriba **editorconfig** en el cuadro de búsqueda. Seleccione la plantilla **archivo editorconfig (valor predeterminado)** y elija **Agregar**.
>
> ![Agregar archivo editorconfig al proyecto en Visual Studio](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Para obtener información sobre la configuración de la gravedad de una regla (por ejemplo, si es un error o una advertencia), vea [establecer la gravedad de la regla en un archivo EditorConfig](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). O bien, puede elegir uno de los [conjuntos de reglas o los archivos EditorConfig](analyzer-rule-sets.md) integrados para habilitar o deshabilitar rápidamente una categoría de reglas.

::: moniker-end

En el resto de este artículo se describe la sintaxis general de las [opciones que delimitan](fxcop-analyzer-options.md) dónde se aplican los analizadores de calidad de código de .net.

## <a name="option-scopes"></a>Ámbitos de opción

Cada opción de refinamiento puede configurarse para todas las reglas, para una categoría de reglas (por ejemplo, nomenclatura o diseño) o para una regla específica.

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

## <a name="enabling-editorconfig-based-configuration"></a>Habilitar la configuración basada en Editorconfig

La configuración del analizador basado en EditorConfig se puede habilitar para los siguientes ámbitos:

- Documentos específicos
- Carpetas específicas
- Proyectos específicos
- Soluciones específicas
- Repositorio completo

Para habilitar la configuración, agregue un archivo *. editorconfig* con las opciones del directorio correspondiente. Este archivo también puede contener entradas de configuración de gravedad de diagnóstico basadas en EditorConfig. Obtenga más información [aquí](use-roslyn-analyzers.md#rule-severity).

## <a name="see-also"></a>Consulte también

- [Opciones de ámbito de reglas para los analizadores de calidad de código de .NET](fxcop-analyzer-options.md)
- [Configuración del analizador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Convenciones de código de .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)

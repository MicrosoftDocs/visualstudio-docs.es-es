---
title: Configurar analizadores de FxCop mediante editorconfig
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1d2c4f6b44daf83b3fd013167ec24e82c45ce2e8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649699"
---
# <a name="configure-fxcop-analyzers"></a>Configurar analizadores FxCop

El [paquete de analizadores de FxCop](install-fxcop-analyzers.md) consta de las reglas de "FxCop" más importantes del análisis heredado convertidas en analizadores de código basados en .net Compiler Platform. En el caso de ciertas reglas de FxCop, puede restringir qué partes del código base deben aplicarse a través de [las opciones configurables](fxcop-analyzer-options.md). Cada opción se especifica agregando un par clave-valor a un archivo [EditorConfig](https://editorconfig.org) . Un archivo de configuración puede ser [específico de un proyecto](#per-project-configuration) o puede [compartirse](#shared-configuration) entre dos o más proyectos.

> [!TIP]
> Agregue un archivo. editorconfig al proyecto haciendo clic con el botón derecho en el proyecto en **Explorador de soluciones** y seleccionando **Agregar**  > **nuevo elemento**. En la ventana **Agregar nuevo elemento** , escriba **editorconfig** en el cuadro de búsqueda. Seleccione la plantilla **archivo editorconfig (valor predeterminado)** y elija **Agregar**.
>
> ![Agregar archivo editorconfig al proyecto en Visual Studio](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Para obtener información sobre la configuración de la gravedad de una regla (por ejemplo, si es un error o una advertencia), vea [establecer la gravedad de la regla en un archivo EditorConfig](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). O bien, puede elegir uno de los [conjuntos de reglas o los archivos EditorConfig](analyzer-rule-sets.md) integrados para habilitar o deshabilitar rápidamente una categoría de reglas.

::: moniker-end

En el resto de este artículo se describe la sintaxis general de las [opciones que refinan](fxcop-analyzer-options.md) dónde se aplican las reglas de FxCop.

> [!NOTE]
> No se pueden configurar reglas FxCop heredadas mediante un archivo EditorConfig. Para obtener información sobre las diferencias entre el análisis heredado y los analizadores de FxCop, consulte [p + f sobre analizadores de FxCop](fxcop-analyzers-faq.md).

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

## <a name="per-project-configuration"></a>Configuración por proyecto

Para habilitar la configuración de analizador basada en EditorConfig para un proyecto específico, agregue un archivo *. EditorConfig* al directorio raíz del proyecto.

Actualmente no hay compatibilidad jerárquica con los archivos. editorconfig "combinados" que existen en distintos niveles de directorio, por ejemplo, el nivel de solución y de proyecto.

## <a name="shared-configuration"></a>Configuración compartida

Puede compartir un archivo. editorconfig para la configuración del analizador de FxCop entre dos o más proyectos, pero requiere algunos pasos adicionales.

1. Guarde el archivo *. editorconfig* en una ubicación común.

2. Cree un archivo *. props* con el siguiente contenido:

   ```xml
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <PropertyGroup>
       <SkipDefaultEditorConfigAsAdditionalFile>true</SkipDefaultEditorConfigAsAdditionalFile>
     </PropertyGroup>
     <ItemGroup Condition="Exists('<your path>\.editorconfig')" >
       <AdditionalFiles Include="<your path>\.editorconfig" />
     </ItemGroup>
   </Project>
   ```

3. Agregue una línea al archivo *. csproj* o *. vbproj* para importar el archivo *. props* que creó en el paso anterior. Esta línea se debe colocar delante de cualquier línea que importe los archivos FxCop Analyzer *. props* . Por ejemplo, si el archivo. props se denomina *editorconfig. props*:

   ```xml
   ...
   <Import Project="..\..\editorconfig.props" Condition="Exists('..\..\editorconfig.props')" />
   <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
   ...
   ```

4. Vuelva a cargar el proyecto.

> [!NOTE]
> La ubicación compartida arbitraria del archivo EditorConfig que se describe aquí solo se aplica a la configuración del ámbito de ciertas reglas del analizador de FxCop. Para otras opciones, como la gravedad de la regla, la configuración general del editor y el estilo de código, el archivo EditorConfig se debe colocar siempre en la carpeta del proyecto o en una carpeta principal.

## <a name="see-also"></a>Vea también

- [Opciones de ámbito de reglas para los analizadores de FxCop](fxcop-analyzer-options.md)
- [Configuración del analizador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Analizadores de FxCop](install-fxcop-analyzers.md)
- [Convenciones de código de .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)

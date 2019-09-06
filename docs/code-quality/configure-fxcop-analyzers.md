---
title: Configurar analizadores de FxCop mediante editorconfig
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 68c175a55c9e60e870a5466a831aaae50d62dced
ms.sourcegitcommit: 9c07ae6fb18204ea080c8248994a683fa12e5c82
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2019
ms.locfileid: "70293448"
---
# <a name="configure-fxcop-analyzers"></a>Configurar analizadores FxCop

Los [analizadores de FxCop](install-fxcop-analyzers.md) se componen de las reglas de "FxCop" más importantes del análisis heredado, que se convierten en analizadores de código basados en .net Compiler Platform. Puede configurar los analizadores de código FxCop de dos maneras:

- Con un [conjunto de reglas](#fxcop-analyzer-rule-sets), que le permite habilitar o deshabilitar la regla y establecer la gravedad de las infracciones de reglas individuales.

- A partir de la versión 2.6.3 del paquete de NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) , a través de un [archivo. editorconfig](#editorconfig-file). Las [Opciones configurables](fxcop-analyzer-options.md) permiten restringir qué partes del código base se van a analizar.

> [!TIP]
> Para obtener información sobre las diferencias entre el análisis heredado y los analizadores de FxCop, consulte [p + f sobre analizadores de FxCop](fxcop-analyzers-faq.md).

## <a name="fxcop-analyzer-rule-sets"></a>Conjuntos de reglas del analizador de FxCop

Una manera de configurar los analizadores de FxCop es mediante un *conjunto de reglas*Xml. Un conjunto de reglas es una agrupación de reglas de análisis de código que identifican problemas de destino y condiciones específicas. Los conjuntos de reglas permiten habilitar o deshabilitar la regla y establecer la gravedad de las infracciones de reglas individuales.

El paquete de NuGet del analizador de FxCop incluye conjuntos de reglas predefinidos para las siguientes categorías de reglas:

- diseño
- en línea
- mantenimiento
- asignar nombre
- rendimiento
- confiabilidad
- seguridad
- uso

Para obtener más información, vea [conjuntos de reglas para los analizadores de código](analyzer-rule-sets.md).

## <a name="editorconfig-file"></a>Archivo EditorConfig

Puede configurar las reglas del analizador de FxCop agregando pares clave-valor a un archivo [. editorconfig](https://editorconfig.org) . Un archivo de configuración puede ser [específico de un proyecto](#per-project-configuration) o puede [compartirse](#shared-configuration) entre dos o más proyectos.

> [!NOTE]
> No se pueden configurar reglas FxCop heredadas mediante un archivo. editorconfig.

### <a name="per-project-configuration"></a>Configuración por proyecto

Para habilitar la configuración de analizador basada en. editorconfig para un proyecto específico, agregue un archivo *. editorconfig* al directorio raíz del proyecto.

> [!TIP]
> Puede Agregar un archivo. editorconfig al proyecto haciendo clic con el botón derecho en el proyecto en **Explorador de soluciones** y seleccionando **Agregar** > **nuevo elemento**. En la ventana **Agregar nuevo elemento** , escriba **editorconfig** en el cuadro de búsqueda. Seleccione la plantilla **archivo editorconfig (valor predeterminado)** y elija **Agregar**.
>
> ![Agregar elemento editorconfig al proyecto en Visual Studio](media/add-editorconfig-file.png)

Actualmente no hay compatibilidad jerárquica con los archivos. editorconfig "combinados" que existen en distintos niveles de directorio, por ejemplo, el nivel de solución y de proyecto.

### <a name="shared-configuration"></a>Configuración compartida

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
> La ubicación compartida arbitraria del archivo EditorConfig que se describe aquí solo se aplica a la configuración de analizadores de FxCop. Para otras opciones, como la sangría y el estilo de código, el archivo EditorConfig siempre debe colocarse en la carpeta del proyecto o en una carpeta principal.

## <a name="option-scopes"></a>Ámbitos de opción

Cada opción se puede configurar para todas las reglas, para una categoría de reglas (por ejemplo, nomenclatura o diseño) o para una regla concreta.

### <a name="all-rules"></a>Todas las reglas

La sintaxis para configurar una opción para todas las reglas es la siguiente:

|Sintaxis|Ejemplo|
|-|-|
| dotnet_code_quality.OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Categoría de reglas

La sintaxis para configurar una opción para una *categoría* de reglas (como nombre, diseño o rendimiento) es la siguiente:

|Sintaxis|Ejemplo|
|-|-|
| dotnet_code_quality.RuleCategory.OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Regla específica

La sintaxis para configurar una opción para una regla específica es la siguiente:

|Sintaxis|Ejemplo|
|-|-|
| dotnet_code_quality. . Nombredeopción = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="see-also"></a>Vea también

- [Configuración del analizador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Analizadores de FxCop](install-fxcop-analyzers.md)
- [Convenciones de código de .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)

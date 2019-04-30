---
title: Configurar los analizadores de FxCop con editorconfig
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ac751b7ec130b6bfbb18752c02b491b6c342f172
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816938"
---
# <a name="configure-fxcop-analyzers"></a>Configurar los analizadores de FxCop

El [analizadores de FxCop](install-fxcop-analyzers.md) constan de las reglas de "FxCop" más importante del análisis de código estático, puede convertida en analizadores de Roslyn. Puede configurar los analizadores de código de FxCop de dos maneras:

- Con un [conjunto de reglas](#fxcop-analyzer-rule-sets), que le permite habilitar o deshabilitar la regla y establecer la gravedad de las infracciones de reglas individuales.

- A partir de la versión 2.6.3 de la [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) de paquetes de NuGet, mediante un [archivo .editorconfig](#editorconfig-file). El [opciones configurables](fxcop-analyzer-options.md) permiten restringir qué partes de la base de código para analizar.

> [!TIP]
> Para obtener información sobre las diferencias entre el análisis de código estático de FxCop y analizadores de FxCop, consulte [preguntas más frecuentes sobre los analizadores de FxCop](fxcop-analyzers-faq.md).

## <a name="fxcop-analyzer-rule-sets"></a>Conjuntos de reglas del analizador de FxCop

Una manera de configurar los analizadores de FxCop es mediante el uso de un documento XML *conjunto de reglas*. Un conjunto de reglas es una agrupación de reglas de análisis de código que identifican problemas concretos y condiciones específicas. Conjuntos de reglas le permiten habilitar o deshabilitar la regla y establecer la gravedad de las infracciones de reglas individuales.

El paquete de NuGet de analizadores de FxCop incluye conjuntos de reglas predefinidas para las siguientes categorías de regla:

- diseño
- en línea
- mantenimiento
- asignar nombre
- rendimiento
- confiabilidad
- seguridad
- uso

Para obtener más información, consulte [conjuntos de reglas para los analizadores de Roslyn](analyzer-rule-sets.md).

## <a name="editorconfig-file"></a>Archivo EditorConfig

Puede configurar reglas del analizador mediante la adición de pares clave-valor a un [.editorconfig](https://editorconfig.org) archivo. Puede ser un archivo de configuración [específico a un proyecto](#per-project-configuration) o puede ser [compartido](#shared-configuration) entre dos o más proyectos.

### <a name="per-project-configuration"></a>Configuración por proyecto

Para habilitar la configuración del analizador basado en .editorconfig para un proyecto específico, agregue un *.editorconfig* archivo al directorio raíz del proyecto.

> [!TIP]
> Puede agregar un archivo .editorconfig al proyecto con el botón secundario en el proyecto en **el Explorador de soluciones** y seleccionando **agregar** > **nuevo elemento**. En el **Agregar nuevo elemento** ventana, escriba **editorconfig** en el cuadro de búsqueda. Seleccione el **(valor predeterminado) del archivo editorconfig** plantilla y elija **agregar**.
>
> ![Agregar elemento de editorconfig al proyecto en Visual Studio](media/add-editorconfig-file.png)

Actualmente no hay ninguna compatibilidad jerárquica para "combinar".editorconfig archivos que existen en los niveles de otro directorio, por ejemplo, el nivel de solución y proyecto.

### <a name="shared-configuration"></a>Configuración compartida

Puede compartir un archivo .editorconfig para la configuración del analizador entre dos o más proyectos, pero requiere algunos pasos adicionales.

1. Guardar el *.editorconfig* en una ubicación común.

2. Crear un *.props* archivo con el siguiente contenido:

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

3. Agregue una línea a su *.csproj* o *.vbproj* archivo para importar el *.props* archivo que creó en el paso anterior. Esta línea debe colocarse antes de todas las líneas que importación el analizador de FxCop *.props* archivos. Por ejemplo, si su archivo .props se denomina *editorconfig.props*:

   ```xml
   ...
   <Import Project="..\..\editorconfig.props" Condition="Exists('..\..\editorconfig.props')" />
   <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
   ...
   ```

4. Vuelva a cargar el proyecto.

> [!NOTE]
> No se puede configurar reglas heredadas de FxCop (análisis de código estático FxCop) mediante el uso de un archivo .editorconfig.

## <a name="option-scopes"></a>Ámbitos de opción

Cada opción se puede configurar para todas las reglas, para una categoría de reglas (por ejemplo, el diseño o nomenclatura) o para una regla específica.

### <a name="all-rules"></a>Todas las reglas

La sintaxis para configurar una opción para todas las reglas es como sigue:

|Sintaxis|Ejemplo|
|-|-|
| dotnet_code_quality.OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Categoría de reglas

La sintaxis para configurar una opción para un *categoría* de reglas (por ejemplo, convenciones de nomenclatura, diseño o rendimiento) es como sigue:

|Sintaxis|Ejemplo|
|-|-|
| dotnet_code_quality.RuleCategory.OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Regla específica

La sintaxis para configurar una opción para una regla concreta es como sigue:

|Sintaxis|Ejemplo|
|-|-|
| dotnet_code_quality.RuleId.OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="see-also"></a>Vea también

- [Configuración del analizador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Analizadores de FxCop](install-fxcop-analyzers.md)

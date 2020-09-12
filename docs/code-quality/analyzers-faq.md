---
title: EditorConfig frente a analizadores
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9408e8615e2a3591a5e93f569546b6161fe40e4c
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037255"
---
# <a name="code-analysis-faq"></a>Preguntas más frecuentes sobre análisis de código

Esta página contiene respuestas a algunas preguntas frecuentes sobre el análisis de código basado en .NET Compiler Platform en Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Análisis de código frente a EditorConfig

**P**: ¿debo usar el análisis de código o EditorConfig para comprobar el estilo de código?

**R: el**análisis de código y los archivos EditorConfig funcionan en mano. Al definir estilos de código [en un archivo EditorConfig](../ide/editorconfig-code-style-settings-reference.md) o en la página de [Opciones editor de texto](../ide/code-styles-and-code-cleanup.md) , en realidad está configurando los analizadores de código integrados en Visual Studio. Los archivos EditorConfig se pueden usar para habilitar o deshabilitar las reglas del analizador y también para configurar paquetes del analizador de NuGet.

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig frente a conjuntos de reglas

**P**: ¿debo configurar mis analizadores mediante un conjunto de reglas o un archivo EditorConfig?

**R**: los conjuntos de reglas y los archivos EditorConfig pueden coexistir y se pueden usar para configurar los analizadores. Tanto los archivos EditorConfig como los conjuntos de reglas permiten habilitar y deshabilitar reglas y establecer su gravedad.

Sin embargo, los archivos EditorConfig ofrecen maneras adicionales de configurar reglas también:

- En el caso de los analizadores de calidad de código de .NET, los archivos EditorConfig permiten [definir los tipos de código que se van a analizar](fxcop-analyzer-options.md).
- En el caso de los analizadores de estilo de código .NET integrados en Visual Studio, los archivos EditorConfig permiten [definir los estilos de código preferidos](../ide/editorconfig-code-style-settings-reference.md) para un código base.

Además de los conjuntos de reglas y los archivos EditorConfig, algunos analizadores se configuran mediante el uso de archivos de texto marcados como [archivos adicionales](../ide/build-actions.md#build-action-values) para los compiladores de C# y VB.

> [!NOTE]
> - Los archivos EditorConfig solo se pueden usar para habilitar reglas y establecer su gravedad en Visual Studio 2019, versión 16,3 y versiones posteriores.
> - Los archivos EditorConfig no se pueden usar para configurar el análisis heredado, mientras que los conjuntos de reglas pueden.

## <a name="code-analysis-in-ci-builds"></a>Análisis de código en compilaciones de CI

**P**: ¿funciona el análisis de código basado en .net Compiler Platform en compilaciones de integración continua (CI)?

**R.** : Sí. En el caso de los analizadores que se instalan desde un paquete NuGet, esas reglas se [aplican en el momento](roslyn-analyzers-overview.md#build-errors)de la compilación, incluso durante una compilación de CI. Los analizadores utilizados en las compilaciones de elementos de configuración respetan la configuración de reglas de ambos conjuntos de reglas y archivos EditorConfig. Actualmente, los analizadores de código que están integrados en Visual Studio no están disponibles como un paquete NuGet, por lo que estas reglas no se pueden aplicar en una compilación de CI.

## <a name="ide-analyzers-versus-stylecop"></a>Analizadores de IDE frente a StyleCop

**P**: ¿Cuál es la diferencia entre los analizadores de código del IDE de Visual Studio y los analizadores de StyleCop?

**R**: el IDE de Visual Studio incluye analizadores integrados que buscan problemas de estilo de código y calidad. Estas reglas le ayudan a usar las nuevas características del lenguaje a medida que se introducen y mejoran el mantenimiento del código. Los analizadores de IDE se actualizan continuamente con cada versión de Visual Studio.

Los [analizadores de StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) son analizadores de terceros instalados como un paquete NuGet que comprueban la coherencia de estilo en el código. En general, las reglas de StyleCop permiten establecer preferencias personales para un código base sin recomendar un estilo sobre otro.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analizadores de código frente al análisis heredado

**P**: ¿Cuál es la diferencia entre el análisis heredado y el análisis de código basado en .net Compiler Platform?

**R**: el análisis de código basado en .net Compiler Platform analiza el código fuente en tiempo real y durante la compilación, mientras que el análisis heredado analiza los archivos binarios una vez completada la compilación. Para obtener más información, vea [análisis basado en .net Compiler Platform frente al análisis heredado](../code-quality/fxcop-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers).

## <a name="treat-warnings-as-errors"></a>Tratar advertencias como errores

**P**: mi proyecto usa la opción de compilación para tratar las advertencias como errores. Después de migrar del análisis heredado al análisis de código fuente, todas las advertencias de análisis de código aparecen ahora como errores. ¿Cómo puedo evitarlo?

**R**: para evitar que las advertencias de análisis de código se traten como errores, siga estos pasos:

  1. Cree un archivo. props con el siguiente contenido:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Agregue una línea al archivo de proyecto. csproj o. vbproj para importar el archivo. props que creó en el paso anterior. Esta línea se debe colocar delante de cualquier línea que importe los archivos FxCop Analyzer. props. Por ejemplo, si el archivo. props se denomina CodeAnalysis. props:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="code-analysis-solution-property-page"></a>Página de propiedades solución de análisis de código

**P**: ¿Dónde está la página de propiedades análisis de código para la solución?

**R**: la página de propiedades análisis de código en el nivel de solución se quitó en favor del grupo de propiedades compartidas más confiables. Para administrar el análisis de código en el nivel de proyecto, la página de propiedades análisis de código sigue estando disponible. (En el caso de los proyectos administrados, también se recomienda migrar de conjuntos de reglas a EditorConfig para la configuración de la regla).  Para compartir conjuntos de archivos entre varios proyectos de una solución o un repositorio, se recomienda definir un grupo de propiedades con la propiedad CodeAnalysisRuleSet en un archivo de propiedades compartidas/destinos o directorio. props/Directory. targets. Si no tiene ninguna propiedad o destino común que se importen todos los proyectos, considere la posibilidad de [Agregar un grupo de propiedades de este tipo a un directorio. props o un directorio. targets en un directorio de soluciones de nivel superior, que se importa automáticamente en todos los archivos de proyecto definidos en el directorio o en sus](../msbuild/customize-your-build.md)subdirectorios.

## <a name="see-also"></a>Consulte también

- [Información general de los analizadores](roslyn-analyzers-overview.md)
- [Configuración de la convención de codificación de .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
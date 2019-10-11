---
title: EditorConfig frente a analizadores
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5aec8c26a827a39abdfeacfc0e3d6dea4a62db43
ms.sourcegitcommit: 7825d4163e52d724e59f6c0da209af5fbef673f7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71999979"
---
# <a name="code-analysis-faq"></a>Preguntas más frecuentes sobre análisis de código

Esta página contiene respuestas a algunas preguntas frecuentes sobre el análisis de código basado en .NET Compiler Platform en Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Análisis de código frente a EditorConfig

**P**: ¿Debo usar el análisis de código o EditorConfig para comprobar el estilo de código?

**R**: Los archivos de análisis de código y EditorConfig funcionan a la mano. Al definir estilos de código [en un archivo EditorConfig](../ide/editorconfig-code-style-settings-reference.md) o en la página de [Opciones editor de texto](../ide/code-styles-and-code-cleanup.md) , en realidad está configurando los analizadores de código integrados en Visual Studio. Los archivos EditorConfig también se pueden usar para configurar algunos paquetes del analizador de NuGet, como los [analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig frente a conjuntos de reglas

**P**: ¿Debo configurar mis analizadores mediante un conjunto de reglas o un archivo EditorConfig?

**R**: Los conjuntos de reglas y los archivos EditorConfig pueden coexistir y se pueden usar para configurar los analizadores. Los [conjuntos de reglas](analyzer-rule-sets.md) permiten habilitar y deshabilitar reglas y establecer su gravedad. Los archivos EditorConfig ofrecen otras maneras de configurar reglas. En el caso de los analizadores de FxCop, los archivos EditorConfig permiten [definir los tipos de código que se van a analizar](fxcop-analyzer-options.md). En el caso de los analizadores de estilo de código integrados en Visual Studio, los archivos EditorConfig permiten [definir los estilos de código preferidos](../ide/editorconfig-code-style-settings-reference.md) para un código base.

Además de los conjuntos de reglas y los archivos EditorConfig, algunos analizadores se configuran mediante el uso de archivos de texto marcados como [archivos adicionales](../ide/build-actions.md#build-action-values) para los C# compiladores de y VB.

> [!NOTE]
> Los archivos EditorConfig no se pueden usar para configurar el análisis heredado, mientras que los conjuntos de reglas pueden.

## <a name="code-analysis-in-ci-builds"></a>Análisis de código en compilaciones de CI

**P**: ¿Funciona el análisis de código basado en .NET Compiler Platform en compilaciones de integración continua (CI)?

**R**: Sí. En el caso de los analizadores que se instalan desde un paquete NuGet, esas reglas se [aplican en el momento](roslyn-analyzers-overview.md#build-errors)de la compilación, incluso durante una compilación de CI. Los analizadores usados en las compilaciones de elementos de configuración respetan la configuración de reglas de ambos [conjuntos de reglas](analyzer-rule-sets.md) y [archivos. editorconfig](configure-fxcop-analyzers.md). Actualmente, los analizadores de código que están integrados en Visual Studio no están disponibles como un paquete NuGet, por lo que estas reglas no se pueden aplicar en una compilación de CI.

## <a name="ide-analyzers-versus-stylecop"></a>Analizadores de IDE frente a StyleCop

**P**: ¿Cuál es la diferencia entre los analizadores de código del IDE de Visual Studio y los analizadores de StyleCop?

**R**: El IDE de Visual Studio incluye analizadores integrados que buscan problemas de estilo de código y calidad. Estas reglas le ayudan a usar las nuevas características del lenguaje a medida que se introducen y mejoran el mantenimiento del código. Los analizadores de IDE se actualizan continuamente con cada versión de Visual Studio.

Los [analizadores de StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) son analizadores de terceros instalados como un paquete NuGet que comprueban la coherencia de estilo en el código. En general, las reglas de StyleCop permiten establecer preferencias personales para un código base sin recomendar un estilo sobre otro.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analizadores de código frente al análisis heredado

**P**: ¿Cuál es la diferencia entre el análisis heredado y el análisis de código basado en .NET Compiler Platform?

**R**: el análisis de código basado en .net Compiler Platform analiza el código fuente en tiempo real y durante la compilación, mientras que el análisis heredado analiza los archivos binarios una vez completada la compilación. Para obtener más información, consulte preguntas más frecuentes sobre [el análisis basado en .net Compiler Platform frente al análisis heredado](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) y los [analizadores de FxCop](fxcop-analyzers-faq.md).

## <a name="treat-warnings-as-errors"></a>Tratar advertencias como errores

**P**: Mi proyecto utiliza la opción de compilación para tratar las advertencias como errores. Después de migrar del análisis heredado al análisis de código fuente, todas las advertencias de análisis de código aparecen ahora como errores. ¿Cómo puedo evitarlo?

**R**: Para evitar que las advertencias de análisis de código se traten como errores, siga estos pasos:

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

## <a name="see-also"></a>Vea también

- [Información general de los analizadores](roslyn-analyzers-overview.md)
- [Configuración de la convención de codificación de .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)

---
title: EditorConfig frente a analizadores
ms.date: 03/11/2019
description: Obtenga información .NET Compiler Platform análisis de código basado en Visual Studio. Vea respuestas a preguntas sobre archivos EditorConfig, conjuntos de reglas y otros temas.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6d67471027f36d0e22c055f4306ce2137d972463
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800460"
---
# <a name="code-analysis-faq"></a>Preguntas más frecuentes sobre análisis de código

Esta página contiene respuestas a algunas de las preguntas más frecuentes sobre el .NET Compiler Platform de código basado en Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Análisis de código frente a EditorConfig

**P:**¿Debo usar el análisis de código o EditorConfig para comprobar el estilo de código?

**A:** Los archivos De análisis de código y EditorConfig funcionan de forma manual. Al definir estilos de código en un archivo [EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options) o en la página Opciones del [editor](../ide/code-styles-and-code-cleanup.md) de texto, realmente está configurando los analizadores de código integrados en Visual Studio. Los archivos EditorConfig se pueden usar para habilitar o deshabilitar las reglas del analizador, así como para configurar paquetes del analizador de NuGet.

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig frente a conjuntos de reglas

**P:**¿Debo configurar mis analizadores mediante un conjunto de reglas o un archivo EditorConfig?

**:** los conjuntos de reglas y los archivos EditorConfig pueden coexistir y se pueden usar para configurar analizadores. Tanto los archivos EditorConfig como los conjuntos de reglas permiten habilitar y deshabilitar reglas y establecer su gravedad.

Sin embargo, los archivos EditorConfig también ofrecen maneras adicionales de configurar reglas:

- Para los analizadores de calidad de código de .NET, los archivos EditorConfig permiten [definir qué tipos de código se van a analizar.](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
- Para los analizadores de estilo de código de .NET integrados [](/dotnet/fundamentals/code-analysis/code-style-rule-options) en Visual Studio, los archivos EditorConfig permiten definir los estilos de código preferidos para un código base.

Además de los conjuntos de reglas y los archivos EditorConfig, algunos [](../ide/build-actions.md#build-action-values) analizadores se configuran mediante el uso de archivos de texto marcados como archivos adicionales para los compiladores de C# y VB.

> [!NOTE]
> - Los archivos EditorConfig solo se pueden usar para habilitar reglas y establecer su gravedad en Visual Studio versión 16.3 y posteriores de 2019.
> - Los archivos EditorConfig no se pueden usar para configurar el análisis heredado, mientras que los conjuntos de reglas sí.

## <a name="code-analysis-in-ci-builds"></a>Análisis de código en compilaciones de CI

**P:**¿Funciona .NET Compiler Platform análisis de código basado en aplicaciones en compilaciones de integración continua (CI)?

**R.** : Sí. En el caso de los analizadores que se [](roslyn-analyzers-overview.md#build-errors)instalan desde un paquete NuGet, esas reglas se aplican en tiempo de compilación, incluso durante una compilación de CI. Los analizadores que se usan en las compilaciones de CI respetan la configuración de reglas de los conjuntos de reglas y los archivos EditorConfig. Actualmente, los analizadores de código integrados en Visual Studio no están disponibles como un paquete NuGet, por lo que estas reglas no se pueden aplicar en una compilación de CI.

## <a name="ide-analyzers-versus-stylecop"></a>Analizadores de IDE frente a StyleCop

**P:**¿Cuál es la diferencia entre los analizadores de código Visual Studio IDE y los analizadores stylecop?

**Un**: el IDE Visual Studio integrados que buscan problemas de calidad y estilo de código. Estas reglas le ayudan a usar nuevas características de lenguaje a medida que se introducen y mejoran la capacidad de mantenimiento del código. Los analizadores de IDE se actualizan continuamente con cada Visual Studio versión.

[Los analizadores de StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) son analizadores de terceros instalados como un paquete NuGet que comprueban la coherencia del estilo en el código. En general, las reglas stylecop permiten establecer preferencias personales para una base de código sin recomendar un estilo sobre otro.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analizadores de código frente a análisis heredado

**P:**¿Cuál es la diferencia entre el análisis heredado y el .NET Compiler Platform basado en código?

**A**: .NET Compiler Platform análisis de código basado en datos analiza el código fuente en tiempo real y durante la compilación, mientras que el análisis heredado analiza los archivos binarios una vez completada la compilación. Para obtener más información, vea .NET Compiler Platform análisis basado en [datos en comparación con el análisis heredado.](../code-quality/net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)

## <a name="fxcop-analyzers-versus-net-analyzers"></a>Analizadores de FxCop frente a analizadores de .NET

**P:**¿Cuál es la diferencia entre los analizadores de FxCop y los analizadores de .NET?

**R:** Tanto los analizadores de FxCop como los analizadores de .NET se refieren a las implementaciones .NET Compiler Platform analizadores ("Roslyn") de las reglas de ca de FxCop. Antes de Visual Studio 2019 16.8 y .NET 5.0, estos analizadores se suministran como `Microsoft.CodeAnalysis.FxCopAnalyzers` [paquete NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). A partir Visual Studio 2019 16.8 y .NET 5.0, estos analizadores se incluyen con el [SDK de .NET.](/dotnet/fundamentals/code-analysis/overview) También están disponibles como paquete `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) Considere la [posibilidad de migrar de analizadores de FxCop a analizadores de .NET.](migrate-from-fxcop-analyzers-to-net-analyzers.md)

## <a name="treat-warnings-as-errors"></a>Tratar advertencias como errores

**P:** Mi proyecto usa la opción de compilación para tratar las advertencias como errores. Después de migrar del análisis heredado al análisis de código fuente, todas las advertencias de análisis de código ahora aparecen como errores. ¿Cómo puedo evitarlo?

**R:** Para evitar que las advertencias de análisis de código se traten como errores, siga estos pasos:

  1. Cree un archivo .props con el siguiente contenido:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Agregue una línea al archivo de proyecto .csproj o .vbproj para importar el archivo .props que creó en el paso anterior. Esta línea debe colocarse antes que cualquier línea que importe los archivos .props del analizador. Por ejemplo, si el archivo .props se denomina codeanalysis.props:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.NetAnalyzers.5.0.0\build\Microsoft.CodeAnalysis.NetAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.NetAnalyzers.5.0.0\build\Microsoft.CodeAnalysis.NetAnalyzers.props')" />
     ...
     ```

## <a name="code-analysis-solution-property-page"></a>Página de propiedades de la solución de análisis de código

**P:**¿Dónde está la Code Analysis de propiedades de la solución?

**A**: la Code Analysis de propiedades en el nivel de solución se quitó en favor del grupo de propiedades compartidas más confiable. Para administrar Code Analysis en el nivel de proyecto, la Code Analysis de propiedades sigue estando disponible. (En el caso de los proyectos administrados, también se recomienda migrar desde conjuntos de reglas a EditorConfig para la configuración de reglas).  Para compartir conjuntos de reglas entre varios o todos los proyectos de una solución o un repositorio, se recomienda definir un grupo de propiedades con la propiedad [CodeAnalysisRuleSet](../code-quality/using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) en un archivo props/targets compartido o en un archivo *Directory.props/Directory.targets.* Si no tiene ninguna propiedad o destino común que importen todos los proyectos, considere la posibilidad de agregar este tipo de grupo de propiedades a un archivo [Directory.props o Directory.targets](../msbuild/customize-your-build.md) en un directorio de solución de nivel superior, que se importa automáticamente en todos los archivos de proyecto definidos en el directorio o en sus subdirectorios.

## <a name="see-also"></a>Consulte también

- [Introducción a los analizadores](roslyn-analyzers-overview.md)
- [Configuración de la convención de codificación de .NET para EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options)
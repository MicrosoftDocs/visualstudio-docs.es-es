---
title: EditorConfig frente a analizadores
ms.date: 03/11/2019
description: Obtenga información sobre el análisis de código basado en .NET Compiler Platform en Visual Studio. Vea las respuestas a preguntas acerca de los archivos EditorConfig, los conjuntos de reglas y otros temas.
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
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99843753"
---
# <a name="code-analysis-faq"></a>Preguntas más frecuentes sobre análisis de código

Esta página contiene respuestas a algunas preguntas frecuentes sobre el análisis de código basado en .NET Compiler Platform en Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Análisis de código frente a EditorConfig

**P**: ¿debo usar el análisis de código o EditorConfig para comprobar el estilo de código?

**R: el** análisis de código y los archivos EditorConfig funcionan en mano. Al definir estilos de código [en un archivo EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options) o en la página de [Opciones editor de texto](../ide/code-styles-and-code-cleanup.md) , en realidad está configurando los analizadores de código integrados en Visual Studio. Los archivos EditorConfig se pueden usar para habilitar o deshabilitar las reglas del analizador y también para configurar paquetes del analizador de NuGet.

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig frente a conjuntos de reglas

**P**: ¿debo configurar mis analizadores mediante un conjunto de reglas o un archivo EditorConfig?

**R**: los conjuntos de reglas y los archivos EditorConfig pueden coexistir y se pueden usar para configurar los analizadores. Tanto los archivos EditorConfig como los conjuntos de reglas permiten habilitar y deshabilitar reglas y establecer su gravedad.

Sin embargo, los archivos EditorConfig ofrecen maneras adicionales de configurar reglas también:

- En el caso de los analizadores de calidad de código de .NET, los archivos EditorConfig permiten [definir los tipos de código que se van a analizar](/dotnet/fundamentals/code-analysis/code-quality-rule-options).
- En el caso de los analizadores de estilo de código .NET integrados en Visual Studio, los archivos EditorConfig permiten [definir los estilos de código preferidos](/dotnet/fundamentals/code-analysis/code-style-rule-options) para un código base.

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

**R**: el análisis de código basado en .net Compiler Platform analiza el código fuente en tiempo real y durante la compilación, mientras que el análisis heredado analiza los archivos binarios una vez completada la compilación. Para obtener más información, vea [análisis basado en .net Compiler Platform frente al análisis heredado](../code-quality/net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers).

## <a name="fxcop-analyzers-versus-net-analyzers"></a>Analizadores de FxCop frente a analizadores de .NET

**P**: ¿Cuál es la diferencia entre los analizadores de FxCop y los analizadores de .net?

**R**: los analizadores de FxCop y los analizadores de .net hacen referencia a las implementaciones de analizador de .net Compiler Platform ("Roslyn") de las reglas de CA de FxCop. Antes de Visual Studio 2019 16,8 y .NET 5,0, estos analizadores se distribuyen como `Microsoft.CodeAnalysis.FxCopAnalyzers` [paquete NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). A partir de Visual Studio 2019 16,8 y .NET 5,0, estos analizadores se [incluyen con el SDK de .net](/dotnet/fundamentals/code-analysis/overview). También están disponibles como `Microsoft.CodeAnalysis.NetAnalyzers` [paquete NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Considere la posibilidad [de migrar de los analizadores de FxCop a los analizadores de .net](migrate-from-fxcop-analyzers-to-net-analyzers.md).

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

  2. Agregue una línea al archivo de proyecto. csproj o. vbproj para importar el archivo. props que creó en el paso anterior. Esta línea se debe colocar delante de cualquier línea que importe los archivos Analyzer. props. Por ejemplo, si el archivo. props se denomina CodeAnalysis. props:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.NetAnalyzers.5.0.0\build\Microsoft.CodeAnalysis.NetAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.NetAnalyzers.5.0.0\build\Microsoft.CodeAnalysis.NetAnalyzers.props')" />
     ...
     ```

## <a name="code-analysis-solution-property-page"></a>Página de propiedades solución de análisis de código

**P**: ¿Dónde está la página de propiedades análisis de código para la solución?

**R**: la página de propiedades análisis de código en el nivel de solución se quitó en favor del grupo de propiedades compartidas más confiables. Para administrar el análisis de código en el nivel de proyecto, la página de propiedades análisis de código sigue estando disponible. (En el caso de los proyectos administrados, también se recomienda migrar de conjuntos de reglas a EditorConfig para la configuración de la regla).  Para compartir conjuntos de archivos entre varios proyectos de una solución o un repositorio, se recomienda definir un grupo de propiedades con la propiedad [CodeAnalysisRuleSet](../code-quality/using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) en un archivo de propiedades compartidas/destinos o *directorio. props/Directory. targets* . Si no tiene ninguna de estas propiedades o destinos comunes que importen todos los proyectos, considere la posibilidad de agregar un grupo de propiedades de este tipo a un [directorio. props o un archivo Directory. targets](../msbuild/customize-your-build.md) en un directorio de soluciones de nivel superior, que se importa automáticamente en todos los archivos de proyecto definidos en el directorio o en sus subdirectorios.

## <a name="see-also"></a>Vea también

- [Información general de los analizadores](roslyn-analyzers-overview.md)
- [Configuración de la convención de codificación de .NET para EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options)
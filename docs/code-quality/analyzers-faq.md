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
ms.openlocfilehash: 56b0c0defe5593c9dc0e2111ef5984a5c51eaf55
ms.sourcegitcommit: a7f781d5a089e6aab6b073a07f3d4d2967af8aa6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81760136"
---
# <a name="code-analysis-faq"></a>Preguntas frecuentes sobre el análisis de código

Esta página contiene respuestas a algunas preguntas frecuentes sobre el análisis de código basado en .NET Compiler Platform en Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Análisis de código frente a EditorConfig

**P:**¿Debo usar el análisis de código o EditorConfig para comprobar el estilo de código?

**R**: El análisis de código y los archivos EditorConfig funcionan mano a mano. Al definir estilos de código [en un archivo EditorConfig](../ide/editorconfig-code-style-settings-reference.md) o en la página Opciones del editor de [texto,](../ide/code-styles-and-code-cleanup.md) en realidad está configurando los analizadores de código integrados en Visual Studio. Los archivos EditorConfig se pueden usar para habilitar o deshabilitar las reglas del analizador y también para configurar algunos paquetes de analizador NuGet, como los [analizadores FxCop.](configure-fxcop-analyzers.md)

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig versus conjuntos de reglas

**P:**¿Debo configurar mis analizadores mediante un conjunto de reglas o un archivo EditorConfig?

**R**: Los conjuntos de reglas y los archivos EditorConfig pueden coexistir y ambos se pueden utilizar para configurar analizadores. Tanto los archivos EditorConfig como los conjuntos de reglas le permiten habilitar y deshabilitar reglas y establecer su gravedad.

Sin embargo, los archivos EditorConfig también ofrecen formas adicionales de configurar reglas:

- Para los analizadores FxCop, los archivos EditorConfig permiten [definir qué tipos de código analizar.](fxcop-analyzer-options.md)
- Para los analizadores de estilo de código integrados en Visual Studio, los archivos EditorConfig permiten [definir los estilos](../ide/editorconfig-code-style-settings-reference.md) de código preferidos para un código base.

Además de los conjuntos de reglas y los archivos EditorConfig, algunos analizadores se configuran mediante el uso de archivos de texto marcados como [archivos adicionales](../ide/build-actions.md#build-action-values) para los compiladores de C- y VB.

> [!NOTE]
> - Los archivos EditorConfig solo se pueden usar para habilitar reglas y establecer su gravedad en Visual Studio 2019 versión 16.3 y versiones posteriores.
> - Los archivos EditorConfig no se pueden utilizar para configurar el análisis heredado, mientras que los conjuntos de reglas pueden hacerlo.

## <a name="code-analysis-in-ci-builds"></a>Análisis de código en compilaciones de CI

**P:**¿Funciona el análisis de código basado en .NET Compiler Platform en compilaciones de integración continua (CI)?

**R.** : Sí. Para los analizadores que se instalan desde un paquete NuGet, esas reglas se aplican en tiempo de [compilación,](roslyn-analyzers-overview.md#build-errors)incluso durante una compilación de CI. Los analizadores utilizados en las compilaciones de CI respetan la configuración de reglas de los conjuntos de reglas y los archivos EditorConfig. Actualmente, los analizadores de código integrados en Visual Studio no están disponibles como un paquete NuGet, por lo que estas reglas no son aplicables en una compilación de CI.

## <a name="ide-analyzers-versus-stylecop"></a>Analizadores IDE frente a StyleCop

**P:**¿Cuál es la diferencia entre los analizadores de código IDE de Visual Studio y los analizadores StyleCop?

**R:** El IDE de Visual Studio incluye analizadores integrados que buscan problemas de calidad y estilo de código. Estas reglas le ayudan a usar nuevas características de idioma a medida que se introducen y mejorar la capacidad de mantenimiento del código. Los analizadores IDE se actualizan continuamente con cada versión de Visual Studio.

Los [analizadores StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) son analizadores de terceros instalados como un paquete NuGet que comprueban la coherencia de estilo en el código. En general, las reglas de StyleCop le permiten establecer preferencias personales para una base de código sin recomendar un estilo sobre otro.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analizadores de código frente al análisis heredado

**P:**¿Cuál es la diferencia entre el análisis heredado y el análisis de código basado en .NET Compiler Platform?

**R**: El análisis de código basado en .NET Compiler Platform analiza el código fuente en tiempo real y durante la compilación, mientras que el análisis heredado analiza los archivos binarios una vez completada la compilación. Para obtener más información, consulte [Análisis basado en .NET Compiler Platform frente a análisis heredadoy](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) Preguntas frecuentes sobre [analizadores FxCop](fxcop-analyzers-faq.md).

## <a name="treat-warnings-as-errors"></a>Tratar advertencias como errores

**P:** Mi proyecto utiliza la opción de compilación para tratar las advertencias como errores. Después de migrar del análisis heredado al análisis de código fuente, todas las advertencias de análisis de código ahora aparecen como errores. ¿Cómo puedo evitarlo?

**R**: Para evitar que las advertencias de análisis de código se traten como errores, siga estos pasos:

  1. Cree un archivo .props con el siguiente contenido:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Agregue una línea al archivo de proyecto .csproj o .vbproj para importar el archivo .props que creó en el paso anterior. Esta línea debe colocarse antes de cualquier línea que importe los archivos .props del analizador FxCop. Por ejemplo, si el archivo .props se denomina codeanalysis.props:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="code-analysis-solution-property-page"></a>Página de propiedades de la solución de análisis de código

**P:**¿Dónde está la página de propiedades Análisis de código de la solución?

**R:** La página de propiedades Análisis de código en el nivel de solución se eliminó en favor del grupo de propiedades compartidas más confiable. Para administrar el análisis de código en el nivel de proyecto, la página de propiedades Análisis de código sigue estando disponible. (Para proyectos administrados, también se recomienda migrar de conjuntos de reglas a EditorConfig para la configuración de reglas.)  Para compartir conjuntos de reglas en varios/todos los proyectos de una solución o un repositorio, se recomienda definir un grupo de propiedades con la propiedad CodeAnalysisRuleSet en un archivo de accesorios/destinos compartido o un archivo Directory.props/Directory.targets. Si no tiene ningún objetivo o objetivos comunes que importen todos los proyectos, debe considerar la posibilidad de agregar un grupo de propiedades de este [tipo a un Directory.props o un Directory.targets en un directorio de solución de nivel superior, que se importa automáticamente en todos los archivos de proyecto definidos en el directorio o sus subdirectorios.](https://docs.microsoft.com/visualstudio/msbuild/customize-your-build?directorybuildprops-and-directorybuildtargets)

## <a name="see-also"></a>Vea también

- [Visión general de los analizadores](roslyn-analyzers-overview.md)
- [Configuración de la convención de codificación de .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)

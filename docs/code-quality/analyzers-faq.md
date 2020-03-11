---
title: Archivo .editorconfig frente a los analizadores
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 680d52ff04553d399b6abeb53919d8aafd4fa792
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408829"
---
# <a name="code-analysis-faq"></a>Preguntas frecuentes sobre análisis de código

Esta página contiene respuestas a algunas preguntas frecuentes sobre el análisis de código basado en .NET Compiler Platform en Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Análisis de código frente .editorconfig

**P.** : ¿Qué hay que usar para comprobar el estilo del código: análisis de código o .editorconfig?

**R**: Los archivos de análisis de código y .editorconfig funcionan a la par. Al definir estilos de código [en un archivo .editorconfig](../ide/editorconfig-code-style-settings-reference.md) o en la página [Opciones](../ide/code-styles-and-code-cleanup.md) del editor de texto, realmente lo que se está haciendo es configurar los analizadores de código integrados en Visual Studio. Los archivos .editorconfig se pueden usar para habilitar o deshabilitar reglas del analizador y, también, para configurar algunos paquetes de analizador de NuGet, como los [analizadores FxCop](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>Archivo .editorconfig frente a conjuntos de reglas

**P.** : ¿Hay que configurar los analizadores con un conjunto de reglas o con un archivo .editorconfig?

**R**: Los conjuntos de reglas y los archivos .editorconfig pueden coexistir y ambos se pueden usar para configurar analizadores. Tanto los archivos .editorconfig como los conjuntos de reglas permiten habilitar y deshabilitar reglas y establecer su gravedad.

Pero los archivos .editorconfig ofrecen otras maneras de configurar reglas también:

- En los analizadores FxCop, los archivos .editorconfig permiten [definir qué tipos de código analizar](fxcop-analyzer-options.md).
- En los analizadores de estilo de código integrados en Visual Studio, los archivos .editorconfig permiten [definir los estilos de código preferidos](../ide/editorconfig-code-style-settings-reference.md) de un código base.

Aparte de los conjuntos de reglas y los archivos .editorconfig, algunos analizadores se configuran usando archivos de texto marcados como [archivos adicionales](../ide/build-actions.md#build-action-values) en los compiladores de C# y Visual Basic.

> [!NOTE]
> - En Visual Studio 2019 versión 16.3 y versiones posteriores, los archivos .editorconfig solo se pueden usar para habilitar reglas y establecer su gravedad .
> - Los archivos .editorconfig no se pueden usar para configurar análisis heredados, mientras que los conjuntos de reglas sí.

## <a name="code-analysis-in-ci-builds"></a>Análisis de código en compilaciones de CI

**P.** : ¿El análisis de código basado en .NET Compiler Platform funciona en compilaciones de integración continua (CI)?

**R**: Sí. En los analizadores que se instalan desde un paquete NuGet, estas reglas se [aplican en el momento de la compilación](roslyn-analyzers-overview.md#build-errors), incluso durante una compilación de CI. Los analizadores utilizados en las compilaciones de integración continua respetan la configuración de reglas tanto de los conjuntos de reglas como de los archivos .editorconfig. Actualmente, los analizadores de código integrados en Visual Studio no están disponibles como paquete NuGet, por lo que estas reglas no se pueden aplicar en una compilación de integración continua.

## <a name="ide-analyzers-versus-stylecop"></a>Analizadores de IDE frente a StyleCop

**P.** : ¿Cuál es la diferencia entre los analizadores de código del IDE de Visual Studio y los analizadores StyleCop?

**R**: El IDE de Visual Studio incluye analizadores integrados que buscan problemas tanto de estilo como de calidad del código. Estas reglas sirven para usar las nuevas características del lenguaje a medida que se van incorporando y mejoran el mantenimiento del código. Los analizadores de IDE se actualizan continuamente con cada versión de Visual Studio.

Los [analizadores StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) son analizadores de terceros que se instalan como un paquete NuGet y que comprueban la coherencia de estilo en el código. En general, las reglas de StyleCop permiten establecer las preferencias personales de un código base sin recomendar un estilo sobre otro.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analizadores de código frente a análisis heredado

**P.** : ¿Cuál es la diferencia entre el análisis heredado y el análisis de código basado en .NET Compiler Platform?

**R**: El análisis de código basado en .NET Compiler Platform analiza el código fuente en tiempo real y durante la compilación, mientras que el análisis heredado analiza los archivos binarios una vez completada la compilación. Para más información, vea [Análisis basados en .NET Compiler Platform frente a análisis heredados](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) y [Preguntas frecuentes sobre analizadores FxCop](fxcop-analyzers-faq.md).

## <a name="treat-warnings-as-errors"></a>Tratar advertencias como errores

**P.** : En mi proyecto se usa la opción de compilación para tratar las advertencias como errores. Tras migrar de análisis heredado a análisis de código fuente, ahora todas las advertencias del análisis de código aparecen como errores. ¿Cómo puedo evitar esto?

**R**: Haga lo siguiente para evitar que las advertencias del análisis de código se traten como errores:

  1. Cree un archivo .props con el siguiente contenido:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Agregue una línea al archivo de proyecto .csproj o .vbproj para importar el archivo .props que creó en el paso anterior. Esta línea debe colocarse antes de cualquier línea que importe archivos .props del analizador FxCop. Por ejemplo, si el archivo .props se llama codeanalysis.props:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="see-also"></a>Vea también

- [Información general de los analizadores](roslyn-analyzers-overview.md)
- [Configuración de la convención de codificación de .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)

---
title: Análisis de código de FxCop (análisis binario) y analizadores de .NET (análisis de código fuente)
ms.date: 09/06/2018
description: Comprenda la diferencia entre fxcop heredado (análisis binario) y analizadores de .NET (análisis de origen) en Visual Studio. Vea respuestas a preguntas sobre cómo usar estos analizadores.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 951e9b951f1d90077fe29506e9c288fb19f2d5ff
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800459"
---
# <a name="frequently-asked-questions-about-legacy-fxcop-and-net-analyzers"></a>Preguntas más frecuentes sobre los analizadores heredados de FxCop y .NET

Puede resultar un poco confuso comprender las diferencias entre fxcop heredado (análisis binario) y analizadores de .NET (análisis de origen). Este artículo pretende abordar algunas de las preguntas que pudiera tener.

## <a name="whats-the-difference-between-legacy-fxcop-and-net-analyzers"></a>¿Cuál es la diferencia entre los analizadores de FxCop y .NET heredados?

El FxCop heredado ejecuta un análisis posterior a la compilación en un ensamblado compilado. Se ejecuta como un archivo ejecutable independiente denominado **FxCopCmd.exe**. FxCopCmd.exe carga el ensamblado compilado, ejecuta el análisis de código y después informa de los resultados (o *diagnósticos*).

Los analizadores de .NET se basan en .NET Compiler Platform ("Roslyn"). Puede [habilitarlos desde el SDK de .NET o](install-net-analyzers.md) instalarlos como un paquete NuGet al que hace referencia el proyecto o la solución. Los analizadores ejecutan análisis basados en código fuente durante la ejecución del compilador. Los analizadores se hospedan dentro  del proceso del compilador, ya seacsc.exeo **vbc.exe**, y ejecutan el análisis cuando se compila el proyecto. Se notifican los resultados del analizador junto con los del compilador.

## <a name="whats-the-difference-between-fxcop-analyzers-and-net-analyzers"></a>¿Cuál es la diferencia entre los analizadores de FxCop y los analizadores de .NET?

Tanto los analizadores de FxCop como los analizadores de .NET se refieren a las implementaciones .NET Compiler Platform analizadores ("Roslyn") de las reglas de ca de FxCop. Antes de Visual Studio 2019 16.8 y .NET 5.0, estos analizadores se suministran como paquete `Microsoft.CodeAnalysis.FxCopAnalyzers` [NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). A partir Visual Studio 2019 16.8 y .NET 5.0, estos analizadores se incluyen con el [SDK de .NET.](/dotnet/fundamentals/code-analysis/overview) También están disponibles como paquete `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) Considere la [posibilidad de migrar de analizadores de FxCop a analizadores de .NET.](migrate-from-fxcop-analyzers-to-net-analyzers.md)

## <a name="does-the-run-code-analysis-command-run-net-analyzers"></a>¿El comando Ejecutar Code Analysis ejecuta analizadores de .NET?

Antes de Visual Studio versión 2019 16.5, al seleccionar **Analizar** ejecución Code Analysis , ejecuta  >  el análisis heredado. A Visual Studio 2019 16.5, la opción de menú Ejecutar **Code Analysis** ejecuta analizadores basados en Roslyn para el proyecto o la solución seleccionados. Si ha instalado analizadores de .NET, también se ejecutarían. Para obtener más información, [vea Cómo: Ejecutar Code Analysis manualmente para código administrado.](how-to-run-code-analysis-manually-for-managed-code.md)

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>¿La propiedad de proyecto de msbuild RunCodeAnalysis ejecuta los analizadores?

No. La propiedad **RunCodeAnalysis** en un archivo de proyecto (por ejemplo, *.csproj*) solo se usa para ejecutar FxCop heredado. Ejecuta una tarea de msbuild posterior a la compilación que invoca **FxCopCmd.exe**.

## <a name="so-how-do-i-run-net-analyzers-then"></a>Entonces, ¿cómo se ejecutan los analizadores de .NET?

Para ejecutar analizadores de .NET, primero debe habilitarlos desde el [SDK de .NET o instalarlos como un paquete NuGet](install-net-analyzers.md). Después, compile el proyecto o solución en Visual Studio o con msbuild. Las advertencias y errores que generan los analizadores de Roslyn aparecerán en la lista **de errores** o en la ventana de comandos.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-net-analyzers-nuget-package"></a>Aparece la advertencia CA0507 incluso después de instalar el paquete NuGet de analizadores de .NET

Si ha instalado analizadores de .NET pero sigue recibiendo la advertencia CA0507 **""Ejecutar Code Analysis"** ha quedado en desuso en favor de los analizadores de FxCop, que se ejecutan durante la compilación", es posible que tenga que establecer la propiedad **RunCodeAnalysis** msbuild en el archivo del proyecto [en](../ide/solutions-and-projects-in-visual-studio.md#project-file) **false.** De lo contrario, el análisis heredado se ejecutará después de cada compilación.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-net-analyzers"></a>¿Qué reglas se han portado a los analizadores de .NET?

Para obtener información sobre qué reglas de análisis heredadas se han portado a analizadores de .NET, vea Estado del [puerto de regla de Fxcop.](fxcop-rule-port-status.md)

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Las advertencias de análisis de código se tratan como errores

Si el proyecto usa la opción de compilación para tratar las advertencias como errores, las advertencias del analizador pueden aparecer como errores. Para evitar que las advertencias de análisis de código se traten como errores, siga los pasos descritos en Preguntas más frecuentes [sobre análisis de código](../code-quality/analyzers-faq.md#treat-warnings-as-errors).

## <a name="see-also"></a>Consulte también

- [Introducción a los analizadores de .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Migración a los analizadores de .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Instalación de los analizadores de .NET](install-net-analyzers.md)

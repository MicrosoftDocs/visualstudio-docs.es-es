---
title: Análisis de código FxCop (análisis binario) y analizadores de .NET (análisis de código fuente)
ms.date: 09/06/2018
description: Comprenda la diferencia entre FxCop (análisis binario) y analizadores de .NET (análisis de código fuente) heredados en Visual Studio. Vea las respuestas a preguntas sobre cómo usar estos analizadores.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d581ef60ebfe9ff5aeceae4c16ee4294eae5d850
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112195"
---
# <a name="frequently-asked-questions-about-legacy-fxcop-and-net-analyzers"></a>Preguntas más frecuentes sobre los analizadores de FxCop y .NET heredados

Puede ser un poco confuso comprender las diferencias entre FxCop heredado (análisis binario) y analizadores de .NET (análisis de código fuente). Este artículo pretende abordar algunas de las preguntas que pudiera tener.

## <a name="whats-the-difference-between-legacy-fxcop-and-net-analyzers"></a>¿Cuál es la diferencia entre los analizadores de FxCop y .NET heredados?

El FxCop heredado ejecuta un análisis posterior a la compilación en un ensamblado compilado. Se ejecuta como un archivo ejecutable independiente denominado **FxCopCmd.exe**. FxCopCmd.exe carga el ensamblado compilado, ejecuta el análisis de código y después informa de los resultados (o *diagnósticos*).

Los analizadores de .NET se basan en el .NET Compiler Platform ("Roslyn"). Se [habilitan desde el SDK de .net o se instalan como un paquete NuGet](install-net-analyzers.md) al que hace referencia el proyecto o la solución. Los analizadores ejecutan el análisis basado en código fuente durante la ejecución del compilador. Los analizadores se hospedan en el proceso del compilador, ya sea **csc.exe** o **vbc.exe** y ejecutar el análisis cuando se compila el proyecto. Se notifican los resultados del analizador junto con los del compilador.

## <a name="whats-the-difference-between-fxcop-analyzers-and-net-analyzers"></a>¿Cuál es la diferencia entre los analizadores de FxCop y los analizadores de .NET?

Tanto los analizadores de FxCop como los analizadores de .NET hacen referencia a las implementaciones de analizador de .NET Compiler Platform ("Roslyn") de las reglas de CA de FxCop. Antes de Visual Studio 2019 16,8 y .NET 5,0, estos analizadores se distribuyen como `Microsoft.CodeAnalysis.FxCopAnalyzers` [paquete NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). A partir de Visual Studio 2019 16,8 y .NET 5,0, estos analizadores se [incluyen con el SDK de .net](/dotnet/fundamentals/code-analysis/overview). También están disponibles como `Microsoft.CodeAnalysis.NetAnalyzers` [paquete NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Considere la posibilidad [de migrar de los analizadores de FxCop a los analizadores de .net](migrate-from-fxcop-analyzers-to-net-analyzers.md).

## <a name="does-the-run-code-analysis-command-run-net-analyzers"></a>¿Ejecuta el comando ejecutar análisis de código los analizadores de .NET?

Antes de la versión 2019 16,5 de Visual Studio, al seleccionar **analizar**  >  **Ejecutar Análisis de código**, se ejecuta el análisis heredado. Al iniciar Visual Studio 2019 16,5, la opción de menú **Ejecutar Análisis de código** ejecuta analizadores basados en Roslyn para el proyecto o la solución seleccionados. Si ha instalado analizadores de .NET, también se ejecutarán. Para obtener más información, vea [Cómo: ejecutar análisis de código manualmente para código administrado](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>¿La propiedad de proyecto de msbuild RunCodeAnalysis ejecuta los analizadores?

No. La propiedad **RunCodeAnalysis** en un archivo de proyecto (por ejemplo, *.csproj*) solo se usa para ejecutar FxCop heredado. Ejecuta una tarea de msbuild posterior a la compilación que invoca **FxCopCmd.exe**.

## <a name="so-how-do-i-run-net-analyzers-then"></a>¿Cómo se ejecutan los analizadores de .NET?

Para ejecutar analizadores de .NET, [habilítelo en primer lugar desde el SDK de .net o instálelos como un paquete NuGet](install-net-analyzers.md). Después, compile el proyecto o solución en Visual Studio o con msbuild. Las advertencias y los errores que generan los analizadores Roslyn aparecerán en el **lista de errores** o en la ventana de comandos.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-net-analyzers-nuget-package"></a>Obtengo la advertencia CA0507 incluso después de instalar el paquete NuGet analizadores de .NET

Si ha instalado analizadores de .NET pero sigue recibiendo ADVERTENCIA CA0507 **"" ejecutar análisis de código "está en desuso en favor de los analizadores de FxCop, que se ejecutan durante la compilación"**, puede que tenga que establecer la propiedad **RunCodeAnalysis** de MSBuild en el [archivo de proyecto](../ide/solutions-and-projects-in-visual-studio.md#project-file) en **false**. De lo contrario, el análisis heredado se ejecutará después de cada compilación.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-net-analyzers"></a>¿Qué reglas se han trasladado a analizadores de .NET?

Para obtener información sobre qué reglas de análisis heredado se han trasladado a analizadores de .NET, consulte estado del puerto de la [regla de FxCop](fxcop-rule-port-status.md).

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Las advertencias de análisis de código se tratan como errores

Si el proyecto utiliza la opción de compilación para tratar las advertencias como errores, las advertencias del analizador pueden aparecer como errores. Para evitar que las advertencias de análisis de código se traten como errores, siga los pasos descritos en las [preguntas más frecuentes sobre análisis de código](../code-quality/analyzers-faq.md#treat-warnings-as-errors).

## <a name="see-also"></a>Consulta también

- [Introducción a los analizadores de .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Migrar a analizadores de .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Instalar analizadores de .NET](install-net-analyzers.md)

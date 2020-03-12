---
title: Análisis de código de FxCop y analizadores de FxCop
ms.date: 09/06/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d8e1df93fa9e865bb9b9136b9d0a0e07f1a485ea
ms.sourcegitcommit: 514f0f7d1a61d292c7dbc80ec73a36bda960d6ce
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/09/2020
ms.locfileid: "78937515"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Preguntas más frecuentes acerca de FxCop y analizadores de FxCop

Puede ser un poco confuso comprender las diferencias entre el FxCop heredado y los analizadores de FxCop. Este artículo pretende abordar algunas de las preguntas que pudiera tener.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>¿Cuál es la diferencia entre FxCop heredados y los analizadores de FxCop?

El FxCop heredado ejecuta un análisis posterior a la compilación en un ensamblado compilado. Se ejecuta como un archivo ejecutable independiente denominado **FxCopCmd.exe**. FxCopCmd.exe carga el ensamblado compilado, ejecuta el análisis de código y después informa de los resultados (o *diagnósticos*).

Los analizadores de FxCop se basan en .NET Compiler Platform (“Roslyn”). Se [instalan como un paquete NuGet](install-fxcop-analyzers.md#nuget-package) que hace referencia al proyecto o solución. Los analizadores de FxCop ejecutan análisis basados en código fuente durante la ejecución del compilador. Los analizadores de FxCop se hospedan dentro del proceso del compilador, ya sea **csc.exe** o **vbc.exe**, y ejecutan el análisis cuando se compila el proyecto. Se notifican los resultados del analizador junto con los del compilador.

> [!NOTE]
> También puede [instalar analizadores de FxCop como una extensión de Visual Studio](install-fxcop-analyzers.md#vsix). En este caso, los analizadores se ejecutan cuando escribe en el editor de código, pero no se ejecutan en el tiempo de compilación. Si desea ejecutar analizadores de FxCop como parte de la integración continua (CI), instálelos como un paquete NuGet en su lugar.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>¿El comando Ejecutar análisis de código ejecuta los analizadores de FxCop?

No. Al seleccionar **analizar** > **ejecutar el análisis de código**, se ejecuta el análisis heredado. **Ejecutar análisis de código** no tiene ningún efecto en los analizadores basados en Roslyn, incluidos los analizadores de FxCop basados en Roslyn.

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>¿La propiedad de proyecto de msbuild RunCodeAnalysis ejecuta los analizadores?

No. La propiedad **RunCodeAnalysis** en un archivo de proyecto (por ejemplo, *.csproj*) solo se usa para ejecutar FxCop heredado. Ejecuta una tarea de msbuild posterior a la compilación que invoca **FxCopCmd.exe**. Esto equivale a seleccionar **Analizar** > **Ejecutar análisis de código** en Visual Studio.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>¿En ese caso, cómo puedo ejecutar analizadores de FxCop?

Para ejecutar los analizadores de FxCop, primero [instale el paquete NuGet](install-fxcop-analyzers.md) para ellos. Después, compile el proyecto o solución en Visual Studio o con msbuild. Las advertencias y errores que generan los analizadores de FxCop aparecerán en la **Lista de errores** o la ventana de comandos.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>Aparece una advertencia CA0507 incluso después de instalar el paquete de NuGet de los analizadores de FxCop

Si ha instalado analizadores FxCop pero sigue recibiendo ADVERTENCIA CA0507 **"" ejecutar análisis de código "está en desuso en favor de los analizadores de FxCop, que se ejecutan durante la compilación"** , puede que tenga que establecer la propiedad **RunCodeAnalysis** de MSBuild en el [archivo de proyecto](../ide/solutions-and-projects-in-visual-studio.md#project-file) en **false**. De lo contrario, el análisis heredado se ejecutará después de cada compilación.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-fxcop-analyzers"></a>¿Qué reglas se han trasladado a los analizadores de FxCop?

Para obtener información sobre qué reglas de análisis heredado se han trasladado a los [analizadores de FxCop](install-fxcop-analyzers.md), consulte estado del puerto de la [regla de FxCop](fxcop-rule-port-status.md).

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Las advertencias de análisis de código se tratan como errores

Si el proyecto utiliza la opción de compilación para tratar las advertencias como errores, las advertencias del analizador de FxCop pueden aparecer como errores. Para evitar que las advertencias de análisis de código se traten como errores, siga los pasos descritos en las [preguntas más frecuentes sobre análisis de código](../code-quality/analyzers-faq.md#treat-warnings-as-errors).

## <a name="see-also"></a>Consulte también

- [Introducción a los analizadores de .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Migrar a analizadores de FxCop](migrate-from-legacy-analysis-to-fxcop-analyzers.md)
- [Instalar analizadores de FxCop](install-fxcop-analyzers.md)

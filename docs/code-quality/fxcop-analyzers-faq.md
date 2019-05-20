---
title: Análisis de código de FxCop y analizadores de FxCop
ms.date: 09/06/2018
ms.topic: overview
helpviewer_keywords:
- code analysis FAQ
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ab7816e7e1472101f0e84c05a4975f19e3902e27
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65613557"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Preguntas más frecuentes acerca de FxCop y analizadores de FxCop

Puede ser un poco confuso comprender las diferencias entre el FxCop heredado y los analizadores de FxCop. Este artículo pretende abordar algunas de las preguntas que pudiera tener.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>¿Cuál es la diferencia entre FxCop heredados y los analizadores de FxCop?

El FxCop heredado ejecuta un análisis posterior a la compilación en un ensamblado compilado. Se ejecuta como un archivo ejecutable independiente denominado **FxCopCmd.exe**. FxCopCmd.exe carga el ensamblado compilado, ejecuta el análisis de código y después informa de los resultados (o *diagnósticos*).

Los analizadores de FxCop se basan en .NET Compiler Platform (“Roslyn”). Se [instalan como un paquete NuGet](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) que hace referencia al proyecto o solución. Los analizadores de FxCop ejecutan análisis basados en código fuente durante la ejecución del compilador. Los analizadores de FxCop se hospedan dentro del proceso del compilador, ya sea **csc.exe** o **vbc.exe**, y ejecutan el análisis cuando se compila el proyecto. Se notifican los resultados del analizador junto con los del compilador.

> [!NOTE]
> También puede [instalar analizadores de FxCop como una extensión de Visual Studio](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix). En este caso, los analizadores se ejecutan cuando escribe en el editor de código, pero no se ejecutan en el tiempo de compilación. Si desea ejecutar analizadores de FxCop como parte de la integración continua (CI), instálelos como un paquete NuGet en su lugar.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>¿El comando Ejecutar análisis de código ejecuta los analizadores de FxCop?

No. Al seleccionar **Analizar** > **Ejecutar análisis de código**, se ejecuta el análisis de código estático o el FxCop heredado. **Ejecutar análisis de código** no tiene ningún efecto en los analizadores basados en Roslyn, incluidos los analizadores de FxCop basados en Roslyn.

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>¿La propiedad de proyecto de msbuild RunCodeAnalysis ejecuta los analizadores?

No. La propiedad **RunCodeAnalysis** en un archivo de proyecto (por ejemplo, *.csproj*) solo se usa para ejecutar FxCop heredado. Ejecuta una tarea de msbuild posterior a la compilación que invoca **FxCopCmd.exe**. Esto equivale a seleccionar **Analizar** > **Ejecutar análisis de código** en Visual Studio.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>¿En ese caso, cómo puedo ejecutar analizadores de FxCop?

Para ejecutar los analizadores de FxCop, primero [instale el paquete NuGet](install-fxcop-analyzers.md) para ellos. Después, compile el proyecto o solución en Visual Studio o con msbuild. Las advertencias y errores que generan los analizadores de FxCop aparecerán en la **Lista de errores** o la ventana de comandos.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>Aparece una advertencia CA0507 incluso después de instalar el paquete de NuGet de los analizadores de FxCop

Si ha instalado los analizadores de FxCop, pero sigue apareciendo la advertencia CA0507 **"'Ejecutar análisis de código' se ha dejado de usar en favor de los analizadores de FxCop, que se ejecutan durante la compilación"**, puede que sea necesario establecer la propiedad **RunCodeAnalysis** de msbuild del archivo del proyecto en **false**. En caso contrario, el análisis de código estático se ejecutará después de cada compilación.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="see-also"></a>Vea también

- [Introducción a los analizadores de .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Introducción a los analizadores](fxcop-analyzers.yml)
- [Instalar analizadores de FxCop](install-fxcop-analyzers.md)

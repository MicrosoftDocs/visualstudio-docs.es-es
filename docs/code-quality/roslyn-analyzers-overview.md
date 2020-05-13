---
title: Análisis de código mediante analizadores de Roslyn
ms.date: 10/03/2019
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 78a47cb2a5aefd7d20e0b8087f5f3ad735716175
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2020
ms.locfileid: "79431285"
---
# <a name="overview-of-source-code-analyzers"></a>Información general de los analizadores de código fuente

Los analizadores de código de .NET Compiler Platform ("Roslyn") revisan el estilo, la calidad, el mantenimiento y el diseño del código de C# o Visual Basic, además de otros problemas.

- Algunos analizadores están integrados en Visual Studio. El identificador de diagnóstico, o código, de estos analizadores tiene el formato IDExxxx, por ejemplo, IDE0067. La mayoría de estos analizadores integrados revisan el [estilo del código](../ide/code-styles-and-code-cleanup.md), y puede configurar las preferencias en la [página de opciones del editor de texto](../ide/code-styles-and-code-cleanup.md) o en un [archivo EditorConfig](../ide/editorconfig-code-style-settings-reference.md). Algunos analizadores integrados examinan la calidad del código.

- Puede instalar más analizadores como un paquete NuGet o una extensión de Visual Studio. Por ejemplo:

  - [Analizadores de FxCop](../code-quality/install-fxcop-analyzers.md), que son los analizadores de calidad de código que Microsoft recomienda
  - Analizadores de terceros, como [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), los [analizadores de XUnit](https://www.nuget.org/packages/xunit.analyzers/) o el [analizador Sonar](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

Si un analizador detecta infracciones de reglas, se notifican en el editor de código (como un *subrayado ondulado* bajo el código infractor) y en la ventana Lista de errores.

Muchas reglas de los analizadores, o *diagnósticos*, tienen una o más *correcciones de código* asociadas que se pueden aplicar para corregir el problema. Los diagnósticos de los analizadores que están integrados en Visual Studio tienen una corrección de código asociada. Las correcciones de código se muestran en el menú del icono de bombilla junto con otros tipos de [Acciones rápidas](../ide/quick-actions.md). Para obtener información sobre estas correcciones de código, vea [Acciones rápidas comunes](../ide/common-quick-actions.md).

![Infracción de analizador y corrección de código de Acción rápida](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="source-code-analysis-versus-legacy-analysis"></a>Análisis de código fuente frente a análisis heredado

El análisis de código fuente de los analizadores de Roslyn reemplaza el [análisis heredado](../code-quality/code-analysis-for-managed-code-overview.md) de código administrado. Muchas de las reglas de análisis heredado ya se han reescrito analizadores de código de Roslyn. En el caso de las plantillas de proyecto más recientes, como los proyectos de .NET Core y .NET Standard, el análisis heredado ni siquiera está disponible.

Al igual que las infracciones de las reglas de análisis heredados, las infracciones de análisis de código fuente se muestran en la ventana Lista de errores de Visual Studio. Además, las infracciones de análisis de código fuente también se muestran en el editor de código como *subrayados ondulados* bajo el código infractor. El color del subrayado ondulado depende del [valor de gravedad](../code-quality/use-roslyn-analyzers.md#rule-severity) de la regla. En la siguiente imagen se muestran tres infracciones, a saber, una roja, una verde y una gris:

![Subrayados ondulados en el editor de código en Visual Studio](media/diagnostics-severity-colors.png)

Los analizadores de código revisan código en el tiempo de compilación (al igual que el análisis heredado, si está habilitado), pero también en vivo a medida que se escribe. El análisis de código activo se puede configurar para que su ámbito de ejecución sea el documento actual, todos los documentos abiertos o toda la solución. Vea [Cómo: Configurar el ámbito del análisis de código activo](./configure-live-code-analysis-scope-managed-code.md).

> [!TIP]
> Los errores y las advertencias de tiempo de compilación de los analizadores de código se muestran solo si los analizadores están instalados como paquetes NuGet. Los analizadores integrados (por ejemplo, IDE0067 e IDE0068) nunca se ejecutan durante una compilación.

Los analizadores de código de Roslyn no solo notifican los mismos tipos de problemas que el análisis heredado, sino que también facilitan la corrección de una o todas las repeticiones de la infracción en el archivo o proyecto. Estas acciones se denominan *correcciones de código*. Las correcciones de código son específicas del IDE; en Visual Studio, se implementan como [Acciones rápidas](../ide/quick-actions.md). No todos los diagnósticos de los analizadores tienen una corrección de código asociada.

> [!NOTE]
> En las versiones anteriores a Visual Studio 2019 16.5, la opción de menú **Analizar** > **Ejecutar análisis de código** ejecuta análisis heredado. A partir de Visual Studio 2019 16.5, la opción de menú **Ejecutar análisis de código** ejecuta analizadores basados en Roslyn para el proyecto o la solución seleccionados.

Para diferenciar entre infracciones de analizadores de código e infracciones de análisis heredado en la lista de errores, examine la columna **Herramienta**. Si el valor Herramienta coincide con uno de los ensamblados del analizador del **Explorador de soluciones**, por ejemplo **Microsoft.CodeQuality.Analyzers**, la infracción procederá de un analizador código. De lo contrario, la infracción se habrá originado en el análisis heredado.

![Columna Herramienta de Lista de errores](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> La propiedad **RunCodeAnalysis** de MSBuild de un archivo del proyecto es válida únicamente en los análisis heredados. Si instala analizadores, establezca **RunCodeAnalysis** en **false** en el archivo del proyecto para evitar que el análisis heredado se ejecute después de la compilación.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>Paquete NuGet frente a extensión VSIX

Los analizadores de código de Roslyn se pueden instalar por proyecto a través de un paquete NuGet. Algunos de estos analizadores están disponibles también como una extensión de Visual Studio, en cuyo caso son válidos en cualquier solución que se abra en Visual Studio. Hay algunas diferencias de comportamiento fundamentales entre estos dos métodos de [instalación de analizadores](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Ámbito

Si instala analizadores como una extensión de Visual Studio, se aplican en el nivel de solución y en todas las instancias de Visual Studio. Si instala los analizadores como un paquete NuGet, que es el método recomendado, se aplican únicamente al proyecto donde se ha instalado el paquete NuGet. En entornos de equipo, los analizadores instalados como paquetes NuGet son para *todos los desarrolladores* que trabajan en ese proyecto.

### <a name="build-errors"></a>Errores de compilación

Para aplicar las reglas en tiempo de compilación, lo que incluye por medio de la línea de comandos o como parte de una compilación de integración continua (CI), instale los analizadores como un paquete NuGet. Los errores y las advertencias del analizador no se muestran en el informe de compilación si instala los analizadores como una extensión.

En la siguiente imagen se muestra la salida de compilación de línea de comandos de la compilación de un proyecto que contiene una infracción de regla de analizador:

![Salida de MSBuild con infracción de regla](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravedad de las reglas

No se puede configurar la gravedad de las reglas de los analizadores que se han instalado como una extensión de Visual Studio. Para configurar la [gravedad de las reglas](../code-quality/use-roslyn-analyzers.md#rule-severity), instale los analizadores como paquetes NuGet.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Instalación de analizadores de código en Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Uso de analizadores de código en Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Vea también

- [Preguntas más frecuentes sobre analizadores](analyzers-faq.md)
- [Escritura de analizadores de código propios](../extensibility/getting-started-with-roslyn-analyzers.md)
- [SDK de .NET Compiler Platform](/dotnet/csharp/roslyn-sdk/)

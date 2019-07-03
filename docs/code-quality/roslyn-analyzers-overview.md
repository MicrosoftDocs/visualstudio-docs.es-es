---
title: Análisis de código mediante analizadores de Roslyn
ms.date: 03/26/2018
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: befbb09d347043ae304702618506d193344e23ba
ms.sourcegitcommit: fd5a5b057df3d733f5224c305096907989811f85
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/18/2019
ms.locfileid: "67195246"
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>Introducción a los analizadores de .NET Compiler Platform

Los analizadores de .NET Compiler Platform ("Roslyn") analizan el estilo, la calidad, el mantenimiento y el diseño del código, además de otros problemas. Visual Studio incluye un conjunto integrado de analizadores que analizan el código de C# o Visual Basic a medida que escribe. Puede configurar las preferencias de estos analizadores integrados en la página [Opciones del editor de texto](../ide/code-styles-and-code-cleanup.md) o en un [archivo .editorconfig](../ide/editorconfig-code-style-settings-reference.md). Puede instalar analizadores adicionales como una extensión de Visual Studio o un paquete de NuGet.

Si un analizador detecta infracciones de reglas, se notifican en el editor de código (como un *subrayado ondulado* bajo el código infractor) y en la ventana **Lista de errores**.

Muchas reglas de los analizadores, o *diagnósticos*, tienen una o más *correcciones de código* asociadas que se pueden aplicar para corregir el problema. Los diagnósticos de los analizadores que están integrados en Visual Studio tienen una corrección de código asociada. Las correcciones de código se muestran en el menú del icono de bombilla junto con otros tipos de [Acciones rápidas](../ide/quick-actions.md). Para obtener información sobre estas correcciones de código, vea [Acciones rápidas comunes](../ide/common-quick-actions.md).

![Infracción de analizador y corrección de código de Acción rápida](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Analizadores de Roslyn frente a análisis de código estático

Los analizadores de .NET Compiler Platform ("Roslyn") van a sustituir al [análisis de código estático](../code-quality/code-analysis-for-managed-code-overview.md) para el código administrado. Muchas de las reglas de análisis de código estático ya se han reescrito como diagnósticos de analizadores de Roslyn.

Al igual que las infracciones de reglas de análisis de código estático, las infracciones de analizadores de Roslyn aparecen en la **Lista de errores**. Además, las infracciones de analizadores de Roslyn también se muestran en el editor de código como *subrayados ondulados* bajo el código infractor. El color del subrayado ondulado depende del [valor de gravedad](../code-quality/use-roslyn-analyzers.md#rule-severity) de la regla. La captura de pantalla siguiente muestra tres infracciones: una roja, una verde y una gris:

![Subrayados ondulados en el editor de código](media/diagnostics-severity-colors.png)

Los analizadores de Roslyn analizan el código en tiempo de compilación, al igual que el análisis de código estático si está habilitado, pero también en vivo a medida que se escribe. Si se habilita el [análisis de la solución completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis), los analizadores de Roslyn también proporcionan análisis en tiempo de diseño de los archivos de código que no están abiertos en el editor.

> [!TIP]
> Los errores y las advertencias de tiempo de compilación de los analizadores de Roslyn se muestran solo si los analizadores están instalados como paquetes NuGet.

Los analizadores de Roslyn no solo notifican los mismos tipos de problemas que el análisis de código estático, sino que también facilitan la corrección de una o todas las repeticiones de la infracción en el archivo o proyecto. Estas acciones se denominan *correcciones de código*. Las correcciones de código son específicas del IDE; en Visual Studio, se implementan como [Acciones rápidas](../ide/quick-actions.md). No todos los diagnósticos de los analizadores tienen una corrección de código asociada.

> [!NOTE]
> Las siguientes opciones de la interfaz de usuario se aplican solo a análisis de código estático:
>
> - La opción de menú **Analizar** > **Ejecutar análisis de código**.
> - Las casillas **Habilitar análisis de código en la compilación** y **Suprimir resultados del código generado** de la pestaña **Análisis de código** de las páginas de propiedades de un proyecto (estas opciones no tienen ningún efecto en los analizadores de Roslyn).

Para diferenciar entre las infracciones de los analizadores de Roslyn y del análisis de código estático en la **Lista de errores**, examine la columna **Herramienta**. Si el valor Herramienta coincide con uno de los ensamblados del analizador del **Explorador de soluciones**, por ejemplo **Microsoft.CodeQuality.Analyzers**, la infracción procede de un analizador de Roslyn. De lo contrario, la infracción se origina en el análisis de código estático.

![Columna Herramienta de Lista de errores](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> La propiedad **RunCodeAnalysis** de msbuild de un archivo del proyecto se aplica solo a análisis de código estático. Si instala los analizadores, establezca **RunCodeAnalysis** en **false** en el archivo del proyecto para evitar que el análisis de código estático se ejecute después de la compilación.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>Paquete NuGet frente a extensión VSIX

Los analizadores de .NET Compiler Platform se pueden instalar por proyecto mediante un paquete NuGet o en todo Visual Studio como una extensión de Visual Studio. Hay algunas diferencias de comportamiento fundamentales entre estos dos métodos de [instalación de analizadores](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Ámbito

Si instala los analizadores como una extensión de Visual Studio, se aplican en el nivel de solución a todas las instancias de Visual Studio. Si instala los analizadores como un paquete NuGet, que es el método recomendado, se aplican únicamente al proyecto donde se ha instalado el paquete NuGet. En entornos de equipo, los analizadores instalados como paquetes NuGet son para *todos los desarrolladores* que trabajan en ese proyecto.

### <a name="build-errors"></a>Errores de compilación

Para aplicar las reglas en tiempo de compilación, lo que incluye por medio de la línea de comandos o como parte de una compilación de integración continua (CI), instale los analizadores como un paquete NuGet. Los errores y las advertencias del analizador no se muestran en el informe de compilación si instala los analizadores como una extensión.

La captura de pantalla siguiente muestra la salida de compilación de línea de comandos de la compilación de un proyecto que contiene una infracción de regla de analizador:

![Salida de MSBuild con infracción de regla](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravedad de las reglas

No se puede establecer la gravedad de las reglas de los analizadores que se han instalado como una extensión de Visual Studio. Para configurar la [gravedad de las reglas](../code-quality/use-roslyn-analyzers.md#rule-severity), instale los analizadores como paquetes NuGet.

### <a name="categories"></a>Categorías

A continuación se muestran los distintos tipos de analizadores que ayudan a analizar el código. 

- Analizadores recomendados de Microsoft: [Analizadores de FxCop](../code-quality/fxcop-analyzers.yml)
- Analizadores IDE de Visual Studio: [EditorConfig](../ide/code-styles-and-code-cleanup.md)
- Analizadores de terceros: [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator/), [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/) y [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Instalar analizadores de Roslyn en Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Usar analizadores de Roslyn en Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Vea también

- [Preguntas más frecuentes sobre analizadores](analyzers-faq.md)
- [Introducción a los analizadores de Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
- [SDK de .NET Compiler Platform](/dotnet/csharp/roslyn-sdk/)

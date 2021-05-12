---
title: Análisis de código mediante analizadores de Roslyn
ms.date: 09/01/2020
description: Familiarícese con el análisis de código fuente en Visual Studio. Obtenga información sobre las correcciones de código, y los distintos tipos de analizadores de diagnóstico y niveles de gravedad.
ms.custom: SEO-VS-2020
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c3a7192ac55dc4138746e3e1e1abe4eaa6928395
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798341"
---
# <a name="overview-of-source-code-analysis"></a>Información general sobre el análisis de código fuente

Los analizadores de .NET Compiler Platform (Roslyn) inspeccionan el estilo, la calidad, el mantenimiento y el diseño del código de C# o de Visual Basic, además de otros problemas. Esta inspección o análisis se realiza durante el tiempo de diseño en todos los archivos abiertos.

Los analizadores se pueden dividir en los grupos siguientes:

- Los analizadores del [estilo del código](/dotnet/fundamentals/code-analysis/code-style-rule-options?preserve-view=true&view=vs-2019#convention-categories) están integrados en Visual Studio. El identificador de diagnóstico, o código, de estos analizadores tiene el formato IDExxxx, por ejemplo, IDE0067. Puede configurar las preferencias en la [página de opciones del editor de texto](../ide/code-styles-and-code-cleanup.md) o en un [archivo EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options). A partir de .NET 5.0, los analizadores del estilo de código se incluyen en el SDK de .NET y se pueden aplicar estrictamente como errores o advertencias de compilación. Para más información, consulte [esta página](/dotnet/fundamentals/productivity/code-analysis#code-style-analysis).

- Los analizadores de la [calidad del código](/dotnet/fundamentals/code-analysis/quality-rules/index) ahora se incluyen en el SDK de .NET 5 y están habilitadas de manera predeterminada. El identificador de diagnóstico, o código, de estos analizadores tiene el formato CAxxxx, por ejemplo, CA1822. Para más información, consulte la [información general del análisis de la calidad del código .NET](/dotnet/fundamentals/productivity/code-analysis#code-quality-analysis).

- Los analizadores de terceros se pueden instalar como paquete NuGet o como extensión de Visual Studio. Analizadores de terceros, como [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/) y [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/).

## <a name="severity-levels-of-analyzers"></a>Niveles de gravedad de los analizadores

Cada analizador tiene uno de los niveles de gravedad siguientes:

| Gravedad (Explorador de soluciones) | Gravedad (archivo .editorconfig) | Comportamiento en tiempo de compilación | Comportamiento del editor |
|-|-|-|
| Error | `error` | Las infracciones aparecen como *Errores* en la Lista de errores y en la salida de compilación de la línea de comandos, e impiden que las compilaciones se lleven a cabo.| El código infractor se subraya con un subrayado ondulado de color rojo y se marca con un pequeño cuadro rojo en la barra de desplazamiento. |
| Advertencia | `warning` | Las infracciones aparecen como *Advertencias* en la Lista de errores y en la salida de compilación de la línea de comandos, pero no impiden que las compilaciones se lleven a cabo. | El código infractor se subraya con un subrayado ondulado de color verde y se marca con un pequeño cuadro verde en la barra de desplazamiento. |
| Información | `suggestion` | Las infracciones aparecen como *Mensajes* en la Lista de errores, pero no se incluyen en la salida de compilación de la línea de comandos. | El código infractor se subraya con un subrayado ondulado de color gris y se marca con un pequeño cuadro gris en la barra de desplazamiento. |
| Hidden | `silent` | No es visible para el usuario. | No es visible para el usuario, pero el diagnóstico se notifica al motor de diagnóstico del IDE. |
| Ninguno | `none` | Se suprime por completo. | Se suprime por completo. |
| Default | `default` | Corresponde a la gravedad predeterminada de la regla. Para averiguar cuál es el valor predeterminado de una regla, consulte la ventana Propiedades. | Corresponde a la gravedad predeterminada de la regla. |

Si un analizador detecta infracciones de reglas, se notifican en el editor de código (como un *subrayado ondulado* bajo el código infractor) y en la ventana Lista de errores.

![Infracción de analizadores en la ventana Lista de errores](../code-quality/media/code-analysis-error-list.png)

Las infracciones de analizadores informadas en la lista de errores coincide con el [valor del nivel de gravedad](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) de la regla. Las infracciones de analizadores también se muestran en el editor de código como subrayados ondulados debajo del código infractor. En la imagen siguiente se muestran tres infracciones&mdash;un error (subrayado ondulado rojo), una advertencia (subrayado ondulado verde) y una sugerencia (tres puntos grises):

![Subrayados ondulados en el editor de código en Visual Studio](media/diagnostics-severity-colors.png)

Muchas reglas de los analizadores, o *diagnósticos*, tienen una o más *correcciones de código* asociadas que se pueden aplicar para corregir la infracción de la regla. Las correcciones de código se muestran en el menú del icono de bombilla junto con otros tipos de [Acciones rápidas](../ide/quick-actions.md). Para obtener información sobre estas correcciones de código, vea [Acciones rápidas comunes](../ide/quick-actions.md).

![Infracción de analizador y corrección de código de Acción rápida](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="configure-analyzer-severity-levels"></a>Configuración de los niveles de gravedad de los analizadores

Puede configurar la gravedad de las reglas de los analizadores, o *diagnósticos*, en un [archivo EditorConfig](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file) o desde el [menú de bombilla](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu).

Los analizadores también se pueden configurar para inspeccionar el código tanto en tiempo de compilación como en tiempo real, a medida que escribe. El análisis de código activo se puede configurar para que su ámbito de ejecución sea el documento actual, todos los documentos abiertos o toda la solución. Vea [Cómo: Configurar el ámbito del análisis de código activo](./configure-live-code-analysis-scope-managed-code.md).

> [!TIP]
> Los errores y las advertencias de tiempo de compilación de los analizadores de código se muestran solo si los analizadores están instalados como paquetes NuGet. Los analizadores integrados (por ejemplo, IDE0067 e IDE0068) nunca se ejecutan durante una compilación.

## <a name="nuget-package-versus-vsix-extension"></a>Paquete NuGet frente a extensión VSIX

Los analizadores de terceros se pueden instalar por proyecto a través de un paquete NuGet. Algunos de estos analizadores están disponibles también como una extensión de Visual Studio, en cuyo caso son válidos en cualquier solución que se abra en Visual Studio. Hay algunas diferencias de comportamiento fundamentales entre estos dos métodos de [instalación de analizadores](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Ámbito

Si instala analizadores como una extensión de Visual Studio, se aplican en el nivel de solución y en todas las instancias de Visual Studio. Si instala los analizadores como un paquete NuGet, que es el método recomendado, se aplican únicamente al proyecto donde se ha instalado el paquete NuGet. En entornos de equipo, los analizadores instalados como paquetes NuGet son para *todos los desarrolladores* que trabajan en ese proyecto.

### <a name="build-errors"></a>Errores de compilación

Para aplicar las reglas en tiempo de compilación, lo que incluye por medio de la línea de comandos o como parte de una compilación de integración continua (CI), puede elegir una de las opciones siguientes:

- Cree un proyecto de .NET 5.0 que incluya analizadores de manera predeterminada en el SDK de .NET. De forma predeterminada, el análisis de código está habilitado para los proyectos que tienen como destino .NET 5.0 o una versión posterior. Puede habilitar el análisis de código en los proyectos que tengan como destino versiones anteriores de .NET estableciendo la propiedad [EnableNETAnalyzers](/dotnet/core/project-sdk/msbuild-props#enablenetanalyzers) en true.

- Instale los analizadores como paquete NuGet. Los errores y las advertencias del analizador no se muestran en el informe de compilación si instala los analizadores como una extensión.

En la siguiente imagen se muestra la salida de compilación de línea de comandos de la compilación de un proyecto que contiene una infracción de regla de analizador:

![Salida de MSBuild con infracción de regla](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravedad de las reglas

No se puede configurar la gravedad de las reglas de los analizadores que se han instalado como una extensión de Visual Studio. Para configurar la [gravedad de las reglas](../code-quality/use-roslyn-analyzers.md#configure-severity-levels), instale los analizadores como paquetes NuGet.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Instalación de analizadores de código en Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Uso de analizadores de código en Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Vea también

- [Preguntas más frecuentes sobre analizadores](analyzers-faq.yml)
- [Escritura de analizadores de código propios](../extensibility/getting-started-with-roslyn-analyzers.md)
- [SDK de la plataforma del compilador de .NET](/dotnet/csharp/roslyn-sdk/)
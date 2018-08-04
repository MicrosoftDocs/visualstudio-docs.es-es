---
title: Analizadores de Roslyn en Visual Studio
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3d5836c0522ef97a634f44799934aab2750b3a45
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511427"
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>Información general de los analizadores de .NET Compiler Platform

Visual Studio 2017 incluye un conjunto integrado de analizadores de .NET Compiler Platform que analizar el código de C# o Visual Basic a medida que escribe. Puede instalar analizadores adicionales como una extensión de Visual Studio o en cada proyecto como un paquete de NuGet. Busque analizadores en estilo de código, la calidad del código y mantenimiento, diseño de código y otros problemas.

Si se detectan infracciones de reglas mediante un analizador, se notifican tanto en el editor de código como un *ondulada* bajo el código incorrecto y en el **lista de errores**.

Muchas reglas del analizador, o *diagnósticos*, tiene uno o más asociados *correcciones de código* que se pueden aplicar para corregir el problema. Los diagnósticos de analizador que están integrados en Visual Studio tienen una corrección de código asociado. Las correcciones de código se muestran en el menú de icono de bombilla junto con otros tipos de *acciones rápidas*. Para obtener información acerca de estas correcciones de código, vea [acciones rápidas comunes](../ide/common-quick-actions.md).

![Infracción del analizador y corrección de código de acción rápida](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Analizadores de Roslyn frente a análisis de código estático

Reemplazarán finalmente a los analizadores de .NET compiler Platform («Roslyn») [análisis de código estático](../code-quality/code-analysis-for-managed-code-overview.md) para código administrado. Ya se han reescrito muchas de las reglas de análisis de código estático como diagnósticos de analizador de Roslyn.

Al igual que las infracciones de reglas de análisis de código estático, las infracciones del analizador de Roslyn aparecen en la **lista de errores**. Además, las infracciones del analizador de Roslyn también se muestran en el editor de código como *detectores* bajo el código incorrecto. El color de la línea ondulada depende el [configuración de gravedad](../code-quality/use-roslyn-analyzers.md#rule-severity) de la regla. Captura de pantalla siguiente muestra tres infracciones&mdash;uno rojo, uno verde y un gris:

![Detectores en el editor de código](media/diagnostics-severity-colors.png)

Analizadores de Roslyn analizar el código en tiempo de compilación, como el análisis de código estático si está habilitado, pero también en vivo a medida que escribe. Analizadores de Roslyn también pueden proporcionar análisis en tiempo de diseño de los archivos de código que no están abiertos en el editor si habilita [completa de análisis de la solución](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis).

> [!NOTE]
> Errores de tiempo de compilación y advertencias de analizadores de Roslyn se muestran solo si los analizadores se instalan como un paquete de NuGet.

No solo hacen analizadores de Roslyn notifican los mismos tipos de problemas que realiza el análisis de código estático, pero facilitan para corregir una o todas, las apariciones de la infracción en el archivo o proyecto. Estas acciones se denominan *correcciones de código*. Las correcciones de código son específicos del IDE; en Visual Studio, se implementan como [acciones rápidas](../ide/quick-actions.md). No todos los diagnósticos de analyzer tienen una corrección de código asociado.

> [!NOTE]
> La opción de menú **analizar** > **ejecutar análisis de código** se aplica el análisis de código estático sólo a. Además, en un proyecto **análisis de código** página de propiedades, el **Habilitar análisis de código al compilar** y **Suprimir resultados del código generado** casillas de verificación solo es aplicable a análisis de código estático. No tienen ningún efecto en los analizadores de Roslyn.

Para diferenciar entre las infracciones de los analizadores de Roslyn y análisis de código estático en el **lista de errores**, examine el **herramienta** columna. Si el valor de la herramienta coincide con uno de los ensamblados del analizador en **el Explorador de soluciones**, por ejemplo **Microsoft.CodeQuality.Analyzers**, la infracción procede de un analizador Roslyn. En caso contrario, la infracción se origina en análisis de código estático.

![Columna de la herramienta en la lista de errores](media/code-analysis-tool-in-error-list.png)

## <a name="nuget-package-versus-vsix-extension"></a>Paquete de NuGet en lugar de extensión VSIX

Pueden ser analizadores de .NET compiler Platform instalado por proyecto a través de un paquete de NuGet, o todo Visual Studio como una extensión de Visual Studio. Hay algunas diferencias de comportamiento clave entre estos dos métodos de [instalar analizadores](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Ámbito

Si instala los analizadores como una extensión de Visual Studio, se aplican en el nivel de solución, todas las instancias de Visual Studio. Si instala los analizadores como un paquete de NuGet, que es el método preferido, se aplican únicamente al proyecto donde se instaló el paquete de NuGet. En entornos de equipo, los analizadores que se instala como paquetes de NuGet están en ámbito para *todos los desarrolladores* que trabaja en ese proyecto.

### <a name="build-errors"></a>Errores de compilación

Para disponer de reglas que se aplican en tiempo de compilación, incluidos a través de la línea de comandos o como parte de la integración continua (CI) de compilación, instale los analizadores como un paquete de NuGet. Errores y advertencias del analizador no se muestran en el informe de compilación si instala los analizadores como una extensión.

Captura de pantalla siguiente muestra la salida de compilación de línea de comandos desde la creación de un proyecto que contiene una infracción de regla de analizador:

![Salida de MSBuild con infracción de regla](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravedad de regla

No se puede establecer la gravedad de las reglas de los analizadores que se instalaron como una extensión de Visual Studio. Para configurar [gravedad de la regla](../code-quality/use-roslyn-analyzers.md#rule-severity), instalar los analizadores como un paquete de NuGet.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Instalar analizadores de Roslyn en Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Usar los analizadores de Roslyn en Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Vea también

- [Acciones rápidas en Visual Studio](../ide/quick-actions.md)
- [Escribir su propio analizador de Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
- [SDK de .NET compiler Platform](/dotnet/csharp/roslyn-sdk/)
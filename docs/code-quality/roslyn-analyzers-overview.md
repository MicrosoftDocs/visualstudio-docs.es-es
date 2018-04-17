---
title: Analizadores de Roslyn en Visual Studio | Documentos de Microsoft
ms.date: 03/26/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 35b9893372435da154a0be0933af4c1ad65d4ef3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>Información general de los analizadores de .NET Compiler Platform

2017 de Visual Studio incluye un conjunto integrado de analizadores de .NET Compiler Platform que analizar el código de C# o Visual Basic a medida que escribe. Puede instalar analizadores adicionales como una extensión de Visual Studio o en una base por proyecto como un paquete de NuGet. Analizadores de un vistazo el estilo de código, la calidad del código y mantenimiento, diseño de código y otros problemas.

Si se detectan infracciones de reglas mediante un analizador, se notifican tanto en el editor de código como un *onduladas* bajo el código incorrecto y en el **lista de errores**.

Muchas de las reglas de analizador, o *diagnósticos*, tienen uno o más asociados *correcciones del código* que puede aplicar para corregir el problema. Los diagnósticos de analizador que están integrados en Visual Studio tienen una revisión de código asociado. Correcciones de código se muestran en el menú del icono de bombilla, junto con otros tipos de *acciones rápidas*. Para obtener información acerca de estas revisiones de código, vea [acciones rápidas comunes](../ide/common-quick-actions.md).

![Infracción de analizador y revisión de código de acción rápida](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Analizadores de Roslyn frente a análisis de código estático

Reemplazarán finalmente a los analizadores de .NET compiler Platform («Roslyn») [análisis de código estático](../code-quality/code-analysis-for-managed-code-overview.md) para código administrado. Muchas de las reglas de análisis de código estático ya se han reescrito como diagnósticos de analizador de Roslyn.

Al igual que infracciones de reglas de análisis de código estático, infracciones de analizador Roslyn aparecen en la **lista de errores**. Además, las infracciones de analizador Roslyn también aparecen en el editor de código como *detectores* bajo el código incorrecto. El color de la onduladas depende el [valor de gravedad](../code-quality/use-roslyn-analyzers.md#rule-severity) de la regla. Captura de pantalla siguiente muestra tres infracciones&mdash;uno rojo, uno verde y uno gris:

![Detectores en el editor de código](media/diagnostics-severity-colors.png)

Analizadores de Roslyn analizar el código en tiempo de compilación, como el análisis de código estático si está habilitado, pero también en vivo a medida que escribe. Analizadores de Roslyn también pueden proporcionar análisis en tiempo de diseño de los archivos de código que no estén abiertos en el editor si habilita [completa de análisis de la solución](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis).

> [!NOTE]
> Errores en tiempo de compilación y las advertencias de analizadores de Roslyn se muestran solo si los analizadores se instalan como un paquete de NuGet.

No sólo hacen Roslyn analizadores notifican los mismos tipos de problemas que realiza el análisis de código estático, pero facilitan la corregir una o todas las apariciones de la infracción en el archivo o proyecto. Estas acciones se denominan *correcciones del código*. Correcciones de código son específicas del IDE; en Visual Studio, se implementan como [acciones rápidas](../ide/quick-actions.md). No todos los diagnósticos de analizador tienen una revisión de código asociado.

> [!NOTE]
> La opción de menú **analizar** > **ejecutar análisis de código** se aplica a análisis de código estático solo a. Además, en un proyecto **análisis de código** página de propiedades, el **Habilitar análisis de código al compilar** y **Suprimir resultados del código generado** casillas solo es aplicable a análisis de código estático. No tienen ningún efecto en Roslyn analizadores.

Para diferenciar las infracciones de analizadores de Roslyn y análisis de código estático en el **lista de errores**, mire el **herramienta** columna. Si el valor de la herramienta coincide con uno de los ensamblados de analizador en **el Explorador de soluciones**, por ejemplo **Microsoft.CodeQuality.Analyzers**, la infracción procede de un analizador de Roslyn. En caso contrario, la infracción se origina en análisis de código estático.

![Columna de la herramienta en la lista de errores](media/code-analysis-tool-in-error-list.png)

## <a name="nuget-package-vs-extension"></a>Paquete de NuGet frente a la extensión

.NET compiler Platform analizadores pueden ser instalado por proyecto a través de un paquete NuGet o todo el Visual Studio como una extensión de Visual Studio. Hay algunas diferencias de comportamiento de la tecla entre estos dos métodos de [instalar analizadores de](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Ámbito

Si instala analizadores como una extensión de Visual Studio, se aplican en el nivel de solución, todas las instancias de Visual Studio. Si instala los analizadores como un paquete de NuGet, que es el método preferido, se aplican únicamente al proyecto donde se instaló el paquete de NuGet. En entornos de equipo, analizadores instalados como paquetes de NuGet pertenecen al ámbito de *todos los programadores* que funcionan en ese proyecto.

### <a name="build-errors"></a>Errores de compilación

Para disponer de reglas que se aplican en tiempo de compilación, incluyendo a través de la línea de comandos o como parte de la integración continua (CI) de compilación, instale los analizadores como un paquete de NuGet. Errores y advertencias de analizador no aparecen en el informe de compilación si instala los analizadores de como una extensión.

Captura de pantalla siguiente muestra la salida de compilación de línea de comandos de la creación de un proyecto que contenga una infracción de regla de analizador:

![Salida de MSBuild con infracción de regla](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Gravedad de regla

No se puede establecer la gravedad de las reglas de los analizadores que se instalaron como una extensión de Visual Studio. Para configurar [regla gravedad](../code-quality/use-roslyn-analyzers.md#rule-severity), instale los analizadores como un paquete de NuGet.

## <a name="next-steps"></a>Pasos siguientes

- [Instalar analizadores de Roslyn en Visual Studio](../code-quality/install-roslyn-analyzers.md)
- [Usar los analizadores de Roslyn de Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Vea también

- [Acciones rápidas en Visual Studio](../ide/quick-actions.md)
- [Escribir su propio analizador Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)
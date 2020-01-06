---
title: Desactivar el análisis de código
ms.date: 10/03/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d25254cabecd88c6e876646c3c276503aadf7eb7
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587672"
---
# <a name="how-to-disable-source-code-analysis-for-managed-code"></a>Cómo deshabilitar el análisis de código fuente para código administrado

::: moniker range=">=vs-2019"

Esta página le ayuda a deshabilitar el análisis de código en Visual Studio. Existen limitaciones en lo que se puede deshabilitar y el procedimiento para desactivar el análisis de código difiere en función de algunos factores:

- Tipo de proyecto (.NET Core/estándar frente a .NET Framework)

  Los proyectos de .NET Core y .NET Standard tienen opciones en su página de propiedades de análisis de código que permiten desactivar el análisis de código de los analizadores instalados como un paquete NuGet. Para obtener más información, vea [proyectos de .net Core y .net Standard](#net-core-and-net-standard-projects). Para desactivar el análisis de código fuente para proyectos de .NET Framework, vea [proyectos de .NET Framework](#net-framework-projects).

- Paquete del analizador de NuGet frente a VSIX o analizadores integrados

  Actualmente, no se puede deshabilitar el análisis de código activo para los analizadores integrados, por ejemplo, el identificador de regla IDE0067. Del mismo modo, no se puede deshabilitar el análisis de código activo para los analizadores que se instalaron como parte de una extensión de Visual Studio (VSIX). Para suprimir los errores y las advertencias de los analizadores integrados y basados en VSIX, elija **analizar** > **compilar y suprimir problemas activos** en la barra de menús. *Puede* deshabilitar el análisis en directo y en tiempo real de los analizadores instalados como parte de un paquete NuGet.

- Análisis de origen frente al análisis heredado

  Este tema se aplica al análisis de código fuente y no al análisis heredado (binario). Para obtener información sobre cómo deshabilitar el análisis heredado, vea [Cómo: habilitar y deshabilitar el análisis de código heredado](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="net-core-and-net-standard-projects"></a>Proyectos de .NET Core y .NET Standard

A partir de la versión 16,3 de Visual Studio 2019, hay dos casillas disponibles en la página Propiedades de análisis de código que permiten controlar si los analizadores basados en NuGet se ejecutan en tiempo de compilación y en tiempo de diseño. Estas opciones son específicas del proyecto.

![Habilitar o deshabilitar el análisis de código activo o compilar en Visual Studio](media/run-on-build-run-live-analysis.png)

Para abrir esta página, haga clic con el botón secundario en el nodo del proyecto en **Explorador de soluciones** y seleccione **propiedades**. Seleccione la pestaña **análisis de código** .

- Para deshabilitar el análisis de origen en tiempo de compilación, desactive la opción **ejecutar al compilar** .
- Para deshabilitar el análisis de código fuente en directo, desactive la opción **ejecutar análisis en vivo** .

> [!NOTE]
> Los analizadores integrados y basados en VSIX seguirán proporcionando análisis en vivo del código, aunque se desactive la **ejecución en el análisis en vivo** . Si desea suprimir errores y advertencias de estos analizadores, elija **analizar** > **compilar y suprimir problemas activos** en la barra de menús.

## <a name="net-framework-projects"></a>Proyectos de .NET Framework

Para desactivar el análisis de código fuente para los analizadores instalados como parte de un paquete NuGet, agregue una o varias de las siguientes propiedades de MSBuild al [archivo de proyecto](../ide/solutions-and-projects-in-visual-studio.md#project-file).

| Propiedad de MSBuild | Descripción | Predeterminado |
| - | - | - |
| `RunAnalyzersDuringBuild` | Controla si los analizadores basados en NuGet se ejecutan en tiempo de compilación. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Controla si los analizadores basados en NuGet analizan el código en tiempo de diseño. | `true` |
| `RunAnalyzers` | Deshabilita los analizadores basados en NuGet en tiempo de compilación y de diseño. Esta propiedad tiene prioridad sobre `RunAnalyzersDuringBuild` y `RunAnalyzersDuringLiveAnalysis`. | `true` |

Ejemplos:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Análisis de código fuente

No se puede desactivar el [análisis de código fuente](roslyn-analyzers-overview.md) en Visual Studio 2017. Si desea borrar los errores del analizador del Lista de errores, puede suprimir todas las infracciones actuales eligiendo **analizar** > **Ejecutar Análisis de código y suprimir problemas activos** en la barra de menús. Para obtener más información, vea [suprimir infracciones](use-roslyn-analyzers.md#suppress-violations).

A partir de la versión 16,3 de Visual Studio 2019, puede desactivar el análisis de código fuente basado en NuGet. Considere la posibilidad de actualizar a Visual Studio 2019.

## <a name="legacy-analysis"></a>Análisis heredado

Puede deshabilitar el análisis heredado en tiempo de compilación en la página Propiedades de **análisis de código** . Para obtener más información, vea [Cómo: habilitar y deshabilitar el análisis de código heredado](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

::: moniker-end

## <a name="see-also"></a>Vea también

- [Suprimir infracciones](use-roslyn-analyzers.md#suppress-violations)
- [Cómo: habilitar y deshabilitar el análisis de código heredado](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)

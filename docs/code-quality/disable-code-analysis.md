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
ms.openlocfilehash: 8db6ad7bed4b1526d87112f33d3586728728d7f5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431402"
---
# <a name="how-to-disable-source-code-analysis-for-managed-code"></a>Cómo deshabilitar el análisis de código fuente para el código administrado

::: moniker range=">=vs-2019"

Esta página le ayuda a deshabilitar el análisis de código en Visual Studio. Hay limitaciones en lo que puede deshabilitar, y el procedimiento para desactivar el análisis de código difiere en función de algunos factores:

- Tipo de proyecto (.NET Core/Standard frente a .NET Framework)

  Los proyectos de .NET Core y .NET Standard tienen opciones en su página de propiedades Análisis de código que permiten desactivar el análisis de código de los analizadores instalados como un paquete NuGet. Para obtener más información, vea [Proyectos de .NET Core y .NET Standard](#net-core-and-net-standard-projects). Para desactivar el análisis de código fuente para proyectos de .NET Framework, vea Proyectos de [.NET Framework](#net-framework-projects).

- Análisis de origen frente al análisis heredado

  Este tema se aplica al análisis de código fuente y no al análisis heredado (binario). Para obtener información sobre cómo deshabilitar el análisis heredado, consulte [Cómo: Habilitar y deshabilitar](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)el análisis de código heredado.

## <a name="net-core-and-net-standard-projects"></a>Proyectos de .NET Core y .NET Standard

A partir de Visual Studio 2019 versión 16.3, hay dos casillas de verificación disponibles en la página de propiedades Análisis de código que le permiten controlar si los analizadores se ejecutan en tiempo de compilación y tiempo de diseño. Estas opciones son específicas del proyecto.

![Habilitar o deshabilitar el análisis de código en vivo o en la compilación en Visual Studio](media/run-on-build-run-live-analysis.png)

Para abrir esta página, haga clic con el botón derecho en el nodo del proyecto en el **Explorador** de soluciones y seleccione **Propiedades**. Seleccione la pestaña **Análisis** de código.

- Para deshabilitar el análisis de origen en tiempo de compilación, desactive la opción **Ejecutar en compilación.**
- Para deshabilitar el análisis de origen en vivo, desactive la opción **Ejecutar en análisis en vivo.**

> [!NOTE]
> A partir de Visual Studio 2019 versión 16.5, si prefiere el flujo de trabajo de ejecución de análisis de código a petición, puede deshabilitar la ejecución del analizador durante el análisis en vivo o compilar y desencadenar manualmente el análisis de código una vez en un proyecto o una solución a petición. Para obtener información sobre cómo ejecutar el análisis de código manualmente, vea [Cómo: Ejecutar](how-to-run-code-analysis-manually-for-managed-code.md)el análisis de código manualmente para código administrado .  

## <a name="net-framework-projects"></a>Proyectos de .NET Framework

Para desactivar el análisis de código fuente para analizadores, agregue una o varias de las siguientes propiedades de MSBuild al archivo de [proyecto.](../ide/solutions-and-projects-in-visual-studio.md#project-file)

| Propiedad de MSBuild | Descripción | Valor predeterminado |
| - | - | - |
| `RunAnalyzersDuringBuild` | Controla si los analizadores se ejecutan en tiempo de compilación. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Controla si los analizadores analizan el código en tiempo de diseño. | `true` |
| `RunAnalyzers` | Deshabilita los analizadores tanto en tiempo de compilación como de diseño. Esta propiedad tiene `RunAnalyzersDuringBuild` `RunAnalyzersDuringLiveAnalysis`prioridad sobre y . | `true` |

Ejemplos:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Análisis de código fuente

No se puede desactivar el [análisis](roslyn-analyzers-overview.md) de código fuente en Visual Studio 2017. Si desea borrar los errores del analizador de la lista de errores, puede suprimir todas las infracciones actuales seleccionando **Analizar** > análisis de código de**ejecución y Suprimir problemas activos** en la barra de menús. Para obtener más información, consulte [Suprimir infracciones](use-roslyn-analyzers.md#suppress-violations).

A partir de Visual Studio 2019 versión 16.3, puede desactivar el análisis de código fuente o ejecutarlo a petición. Considere la posibilidad de actualizar a Visual Studio 2019.

## <a name="legacy-analysis"></a>Análisis heredado

Puede deshabilitar el análisis en tiempo de compilación heredado en la página de propiedades **Análisis** de código. Para obtener más información, consulte [Cómo: Habilitar y deshabilitar](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)el análisis de código heredado.

::: moniker-end

## <a name="see-also"></a>Consulte también

- [Suprimir infracciones](use-roslyn-analyzers.md#suppress-violations)
- [Cómo: Habilitar y deshabilitar el análisis de código heredado](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)

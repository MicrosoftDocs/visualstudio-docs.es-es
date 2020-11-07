---
title: Desactivar el análisis de código
ms.date: 09/01/2020
description: Obtenga información sobre cómo desactivar el análisis de código fuente de Visual Studio en proyectos de .NET Core, .NET Standard y .NET Framework.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.openlocfilehash: e808cb623fa47c9971e1cdceb15a02b5bf46e901
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348559"
---
# <a name="disable-source-code-analysis-for-net"></a>Deshabilitar análisis de código fuente para .NET

::: moniker range=">=vs-2019"

Esta página le ayuda a deshabilitar el análisis de código en Visual Studio. Existen limitaciones en lo que se puede deshabilitar y el procedimiento para desactivar el análisis de código difiere en función de algunos factores:

- Tipo de proyecto (.NET Core/estándar frente a .NET Framework)

  Los proyectos de .NET Core y .NET Standard tienen opciones en su página de propiedades de análisis de código que permiten desactivar el análisis de código de los analizadores instalados como un paquete NuGet. Para obtener más información, vea [proyectos de .net Core y .net Standard](#net-core-and-net-standard-projects). Para desactivar el análisis de código fuente para proyectos de .NET Framework, vea [proyectos de .NET Framework](#net-framework-projects).

- Análisis de origen frente al análisis heredado

  Este tema se aplica al análisis de código fuente y no al análisis heredado (binario). Para obtener información sobre cómo deshabilitar el análisis heredado, vea [Cómo: habilitar y deshabilitar el análisis de código heredado](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="net-core-and-net-standard-projects"></a>Proyectos de .NET Core y .NET Standard

A partir de la versión 16,3 de Visual Studio 2019, hay dos casillas disponibles en la página Propiedades de análisis de código que permiten controlar si los analizadores se ejecutan en tiempo de compilación y en tiempo de diseño. Estas opciones son específicas del proyecto.

![Habilitar o deshabilitar el análisis de código activo o compilar en Visual Studio](media/run-on-build-run-live-analysis.png)

Para abrir esta página, haga clic con el botón secundario en el nodo del proyecto en **Explorador de soluciones** y seleccione **propiedades**. Seleccione la pestaña **análisis de código** .

- Para deshabilitar el análisis de origen en tiempo de compilación, desactive la opción **ejecutar al compilar** .
- Para deshabilitar el análisis de código fuente en directo, desactive la opción **ejecutar análisis en vivo** .

> [!NOTE]
> A partir de la versión 16,5 de Visual Studio 2019, si prefiere el flujo de trabajo de ejecución del análisis de código a petición, puede deshabilitar la ejecución del analizador durante el análisis en vivo o compilar y desencadenar manualmente el análisis de código una vez en un proyecto o una solución a petición. Para obtener información sobre cómo ejecutar el análisis de código manualmente, vea [Cómo: ejecutar el análisis de código manualmente para código administrado](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="net-framework-projects"></a>Proyectos de .NET Framework

Para desactivar el análisis de código fuente de los analizadores, agregue una o varias de las siguientes propiedades de MSBuild al [archivo de proyecto](../ide/solutions-and-projects-in-visual-studio.md#project-file).

| Propiedad de MSBuild | Descripción | Valor predeterminado |
| - | - | - |
| `RunAnalyzersDuringBuild` | Controla si los analizadores se ejecutan en tiempo de compilación. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Controla si los analizadores analizan el código en tiempo de diseño. | `true` |
| `RunAnalyzers` | Deshabilita los analizadores en tiempo de compilación y de diseño. Esta propiedad tiene prioridad sobre `RunAnalyzersDuringBuild` y `RunAnalyzersDuringLiveAnalysis` . | `true` |

Ejemplos:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Análisis de código fuente

No se puede desactivar el [análisis de código fuente](roslyn-analyzers-overview.md) en Visual Studio 2017. Si desea borrar los errores del analizador del **lista de errores** , puede suprimir todas las infracciones actuales seleccionando **analizar**  >  **Ejecutar Análisis de código y suprimir problemas activos** en la barra de menús. Para obtener más información, vea [suprimir infracciones](use-roslyn-analyzers.md#suppress-violations).

A partir de la versión 16,3 de Visual Studio 2019, puede desactivar el análisis de código fuente o ejecutarlo a petición. Considere la posibilidad de actualizar a Visual Studio 2019.

## <a name="legacy-analysis"></a>Análisis heredado

Puede deshabilitar el análisis heredado en tiempo de compilación en la página Propiedades de **análisis de código** . Para obtener más información, vea [Cómo: habilitar y deshabilitar el análisis de código heredado](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

::: moniker-end

## <a name="see-also"></a>Vea también

- [Suprimir infracciones](use-roslyn-analyzers.md#suppress-violations)
- [Cómo: habilitar y deshabilitar el análisis de código heredado](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)

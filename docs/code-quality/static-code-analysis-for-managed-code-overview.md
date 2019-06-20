---
title: Análisis de código para código administrado
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6c2202103bbff9de75921fba18f842f633419587
ms.sourcegitcommit: fd5a5b057df3d733f5224c305096907989811f85
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/18/2019
ms.locfileid: "67196394"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Información general de análisis de código para código administrado en Visual Studio

Visual Studio puede realizar análisis de código del código administrado de dos maneras: con [analizadores binarios](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), también conocido como FxCop de análisis estático de los ensamblados administrados y con la versión más moderna [analizadores de Roslyn](../code-quality/roslyn-analyzers-overview.md). En este tema se trata los análisis de código estático de FxCop. Para más información acerca del análisis de código mediante el uso de los analizadores de código fuente, consulte [analizadores de información general de Roslyn](../code-quality/roslyn-analyzers-overview.md).

Análisis de código para código administrado analiza los ensamblados administrados y proporciona información sobre los ensamblados, como las infracciones de las reglas de programación y diseño estipuladas en las [las directrices de diseño de .NET](/dotnet/standard/design-guidelines/).

La herramienta de análisis representa las comprobaciones que realiza durante un análisis como mensajes de advertencias. Los mensajes de advertencia identifican cualquier problema pertinente de programación y diseño y, cuando es posible, proporcionan información sobre la solución del problema.

> [!NOTE]
> Análisis de código estático no se admite para los proyectos de .NET Core y .NET Standard en Visual Studio. Ejecutar análisis de código en un proyecto .NET Core o .NET Standard como parte de msbuild, verá un error similar al **error: CA0055: No se pudo identificar la plataforma para \<your.dll >** . Para analizar el código en proyectos de .NET Core o .NET Standard, use [analizadores de Roslyn](../code-quality/roslyn-analyzers-overview.md) en su lugar.

## <a name="ide-integrated-development-environment-integration"></a>Integración del IDE (entorno de desarrollo integrado)

Puede ejecutar análisis de código en el proyecto de forma manual o automática.

Para ejecutar análisis de código cada vez que se compila un proyecto, seleccione **Habilitar análisis de código al compilar** en la página de propiedades del proyecto. Para obtener más información, vea [Cómo: Habilitar y deshabilitar el análisis de código automático](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Para ejecutar análisis de código manualmente en un proyecto, en la barra de menús elija **analizar** > **ejecutar análisis de código** > **ejecutar análisis de código en \<proyecto >** .

## <a name="rule-sets"></a>Conjuntos de reglas

Las reglas de análisis del código administrado se agrupan en [conjuntos de reglas](../code-quality/using-rule-sets-to-group-code-analysis-rules.md). Puede usar uno de los conjuntos de reglas estándar de Microsoft, o bien puede [crear un conjunto de reglas personalizado](../code-quality/how-to-create-a-custom-rule-set.md) para satisfacer una necesidad concreta.

## <a name="suppress-warnings"></a>Suprimir advertencias

Normalmente, resulta útil indicar que una advertencia no es aplicable. De este modo, informa al desarrollador y a cualquier otra persona que pudiera revisar el código en el futuro de que se ha investigado una advertencia y se ha suprimido u omitido.

La supresión de advertencias en el código fuente se implementa a través de atributos personalizados. Para suprimir una advertencia, agregue el atributo `SuppressMessage` al código fuente como se muestra en el ejemplo siguiente:

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Para obtener más información, consulte [Suprimir advertencias](../code-quality/in-source-suppression-overview.md).

> [!NOTE]
> Si migra un proyecto de Visual Studio 2017 o Visual Studio de 2019, podría encontrarse, de repente, con un gran número de advertencias de análisis de código. Si no está listo para solucionar las advertencias y quieran ser más productivos inmediatamente, puede *baseline* el estado de análisis de su proyecto. Desde el **analizar** menú, seleccione **ejecutar análisis de código y suprimir problemas activos**.

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Ejecutar el análisis de código como parte de la directiva de inserción en el repositorio

En una organización, puede ser necesario exigir que todas las protecciones cumplan determinadas directivas. En particular, es importante asegurarse de que se respeten estas directivas:

- No hay ningún error de compilación en el código que se protege.

- Análisis de código se ejecuta como parte de la compilación más reciente.

Para conseguirlo, se especifican las directivas de protección. Para obtener más información, consulte [mejorar la calidad del código con directivas de protección del proyecto](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md).

## <a name="team-build-integration"></a>Integración de Team build

Puede utilizar las características integradas del sistema de generación para ejecutar la herramienta de análisis como parte del proceso de generación. Para obtener más información, consulte [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Vea también

- [Información general de los analizadores de Roslyn](../code-quality/roslyn-analyzers-overview.md)
- [Usar conjuntos de reglas para agrupar reglas de análisis de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Cómo: Habilitar y deshabilitar el análisis de código automático](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)

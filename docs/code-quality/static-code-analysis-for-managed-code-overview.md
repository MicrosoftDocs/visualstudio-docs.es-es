---
title: Análisis heredado para código administrado
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
ms.openlocfilehash: 18c4ebf61e7136d908ad1e444616b0af7ac59a48
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238379"
---
# <a name="overview-of-legacy-analysis-for-managed-code-in-visual-studio"></a>Información general sobre el análisis heredado para código administrado en Visual Studio

Visual Studio puede realizar análisis de código de código administrado de dos maneras: con el [análisis heredado](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), también conocido como análisis estático de FxCop de ensamblados administrados, y con los [analizadores de código](../code-quality/roslyn-analyzers-overview.md)más modernos basados en .net Compiler Platform. En este tema se trata el análisis heredado. Para obtener más información sobre el análisis de código basado en .NET Compiler Platform, consulte [información general de los analizadores basados en .net Compiler Platform](../code-quality/roslyn-analyzers-overview.md).

El análisis de código para código administrado analiza los ensamblados administrados e informa de la información sobre los ensamblados, como las infracciones de las reglas de programación y diseño establecidas en las [instrucciones de diseño de .net](/dotnet/standard/design-guidelines/).

La herramienta de análisis representa las comprobaciones que realiza durante un análisis como mensajes de advertencias. Los mensajes de advertencia identifican cualquier problema pertinente de programación y diseño y, cuando es posible, proporcionan información sobre la solución del problema.

> [!NOTE]
> Los proyectos de .NET Core y .NET Standard de Visual Studio no admiten el análisis heredado (análisis de código estático). Si ejecuta el análisis de código en un proyecto de .NET Core o .NET Standard como parte de MSBuild, verá un error similar al **siguiente: CA0055: no se pudo identificar la \<your.dll> plataforma para **. Para analizar el código en proyectos de .NET Core o .NET Standard, use [analizadores de código](../code-quality/roslyn-analyzers-overview.md) en su lugar.

## <a name="ide-integrated-development-environment-integration"></a>Integración del IDE (entorno de desarrollo integrado)

Puede ejecutar el análisis de código en el proyecto de forma manual o automática.

Para ejecutar el análisis de código cada vez que compile un proyecto, seleccione la opción en la página de propiedades **análisis de código** del proyecto. Para obtener más información, vea [Cómo: habilitar y deshabilitar el análisis de código automático](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Para ejecutar el análisis de código manualmente en un proyecto, en la barra de menús, elija **analizar**  >  **Ejecutar**análisis  >  **de \<project> código ejecutar análisis de código en **.

## <a name="rule-sets"></a>Conjuntos de reglas

Las reglas de análisis del código administrado se agrupan en [conjuntos de reglas](../code-quality/using-rule-sets-to-group-code-analysis-rules.md). Puede usar uno de los conjuntos de reglas estándar de Microsoft, o puede [crear un conjunto de reglas personalizado](../code-quality/how-to-create-a-custom-rule-set.md) para satisfacer una necesidad concreta.

## <a name="suppress-warnings"></a>Suprimir advertencias

Normalmente, resulta útil indicar que una advertencia no es aplicable. De este modo, informa al desarrollador y a cualquier otra persona que pudiera revisar el código en el futuro de que se ha investigado una advertencia y se ha suprimido u omitido.

La supresión en el código fuente de las advertencias se implementa a través de atributos personalizados. Para suprimir una advertencia, agregue el atributo `SuppressMessage` al código fuente como se muestra en el ejemplo siguiente:

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Para obtener más información, vea [suprimir advertencias](../code-quality/in-source-suppression-overview.md).

::: moniker range="vs-2017"

> [!NOTE]
> Si migra un proyecto a Visual Studio 2017, es posible que se enfrente a un gran número de advertencias de análisis de código. Si no está listo para corregir las advertencias, puede suprimir todas ellas eligiendo **analizar**  >  **Ejecutar Análisis de código y suprimir problemas activos**.
>
> ![Ejecutar análisis de código y suprimir problemas en Visual Studio](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Si migra un proyecto a Visual Studio 2019, es posible que se enfrente a un gran número de advertencias de análisis de código. Si no está listo para corregir las advertencias, puede suprimir todas ellas eligiendo **analizar**  >  **compilación y suprimir problemas activos**.

::: moniker-end

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Ejecutar el análisis de código como parte de la directiva de inserción en el repositorio

En una organización, puede ser necesario exigir que todas las protecciones cumplan determinadas directivas. En particular, es importante asegurarse de que se respeten estas directivas:

- No hay ningún error de compilación en el código que se está protegiendo.

- El análisis de código se ejecuta como parte de la compilación más reciente.

Para conseguirlo, se especifican las directivas de protección. Para obtener más información, vea [mejorar la calidad del código con directivas de inserción en el repositorio del proyecto](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md).

## <a name="team-build-integration"></a>Integración de Team Build

Puede utilizar las características integradas del sistema de generación para ejecutar la herramienta de análisis como parte del proceso de generación. Para obtener más información, consulte [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Vea también

- [Información general de los analizadores basados en .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md)
- [Usar conjuntos de reglas para agrupar reglas de análisis de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Cómo: Habilitar y deshabilitar el análisis de código automático](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)

---
title: Análisis de código administrado de Visual Studio de código | Documentos de Microsoft
ms.date: 03/26/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 6d654cb3a7f0d0e952b447337603718c20eaee3e
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2018
---
# <a name="overview-of-code-analysis-for-managed-code"></a>Información general de análisis de código para código administrado

Visual Studio de 2017 analiza el código administrado de dos maneras: con heredado *FxCop* análisis estático de los ensamblados administrados y con .NET Compiler Platform *analizadores*. Este tema tratan los análisis de código estático de FxCop. Para más información acerca del análisis de código mediante el uso de los analizadores de .NET Compiler Platform, consulte [analizadores de información general de Roslyn](../code-quality/roslyn-analyzers-overview.md).

En el análisis de código administrado se analizan los ensamblados administrados y se muestra información sobre dichos ensamblados, como por ejemplo las infracciones de las reglas de programación y las reglas de diseño estipuladas en las instrucciones de diseño de Microsoft .NET Framework.

La herramienta de análisis representa las comprobaciones que realiza durante un análisis como mensajes de advertencias. Los mensajes de advertencia identifican cualquier problema pertinente de programación y diseño y, cuando es posible, proporcionan información sobre la solución del problema.

## <a name="ide-integrated-development-environment-integration"></a>Integración de IDE (entorno de desarrollo integrado)

Puede ejecutar análisis de código en el proyecto de forma manual o automática.

Para ejecutar el análisis de código cada vez que compile un proyecto, seleccione **Habilitar análisis de código al compilar** en la página de propiedades del proyecto. Para obtener más información, consulte [Cómo: habilitar y deshabilitar el análisis de código automático](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Para ejecutar el análisis de código manualmente en un proyecto, en la barra de menús, elija **analizar** > **ejecutar análisis de código** > **ejecutar análisis de código en \<proyecto >**.

## <a name="rule-sets"></a>Conjuntos de reglas

Reglas de análisis de código para código administrado se agrupan en [conjuntos de reglas](../code-quality/using-rule-sets-to-group-code-analysis-rules.md). Puede usar uno de los conjuntos de reglas estándar de Microsoft, o bien puede [crear un conjunto de reglas personalizado](../code-quality/how-to-create-a-custom-rule-set.md) para satisfacer una necesidad concreta.

## <a name="suppress-warnings"></a>Suprimir advertencias

Normalmente, resulta útil indicar que una advertencia no es aplicable. De este modo, informa al desarrollador y a cualquier otra persona que pudiera revisar el código en el futuro de que se ha investigado una advertencia y se ha suprimido u omitido.

La supresión de advertencias en el código fuente se implementa mediante atributos personalizados. Para suprimir una advertencia, agregue el atributo `SuppressMessage` al código fuente como se muestra en el ejemplo siguiente:

```csharp
[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Para obtener más información, consulte [Suprimir advertencias](../code-quality/in-source-suppression-overview.md).

> [!NOTE]
> Si migra un proyecto en Visual Studio de 2017, de repente puede encontrar con un gran número de advertencias de análisis de código. Si no está preparado para solucionar las advertencias y deseen ser más productivos inmediatamente, puede *previsto* el estado de análisis del proyecto. Desde el **analizar** menú, seleccione **ejecutar análisis de código y suprimir problemas activos**.

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Ejecutar el análisis de código como parte de la directiva de inserción en el repositorio

En una organización, puede ser necesario exigir que todas las protecciones cumplan determinadas directivas. En particular, es importante asegurarse de que se respeten estas directivas:

- No hay ningún error de compilación en el código que se protege.

- Análisis de código se ejecuta como parte de la compilación más reciente.

Para conseguirlo, se especifican las directivas de inserción en el repositorio. Para obtener más información, consulte [mejorar la calidad del código con directivas de protección del proyecto de equipo](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).

## <a name="team-build-integration"></a>Integración de Team build

Puede utilizar las características integradas del sistema de generación para ejecutar la herramienta de análisis como parte del proceso de generación. Para obtener más información, consulte [de compilación y de la versión (VSTS)](/vsts/build-release/index).

## <a name="see-also"></a>Vea también

- [Información general de los analizadores de Roslyn](../code-quality/roslyn-analyzers-overview.md)
- [Usar conjuntos de reglas para agrupar reglas de análisis de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Cómo: habilitar y deshabilitar el análisis de código automático](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)

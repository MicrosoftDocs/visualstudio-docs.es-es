---
title: "Análisis de código para código administrado Introducción | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
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
ms.openlocfilehash: 5d30f84194ef7a48de106698c9ad4569e947923c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="code-analysis-for-managed-code-overview"></a>Análisis de código para información general del código administrado

En el análisis de código administrado se analizan los ensamblados administrados y se muestra información sobre dichos ensamblados, como por ejemplo las infracciones de las reglas de programación y las reglas de diseño estipuladas en las instrucciones de diseño de Microsoft .NET Framework.

La herramienta de análisis representa las comprobaciones que realiza durante un análisis como mensajes de advertencias. Los mensajes de advertencia identifican cualquier problema pertinente de programación y diseño y, cuando es posible, proporcionan información sobre la solución del problema.

## <a name="ide-integrated-development-environment-integration"></a>Integración de IDE (entorno de desarrollo integrado)

Puede ejecutar análisis de código en el proyecto de forma manual o automática.

Para ejecutar el análisis de código cada vez que compile un proyecto, seleccione **Habilitar análisis de código al compilar** en la página de propiedades del proyecto. Para obtener más información, consulte [Cómo: habilitar y deshabilitar el análisis de código automático](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Para ejecutar el análisis de código manualmente en un proyecto, en la barra de menús, elija **analizar** > **ejecutar análisis de código** > **ejecutar análisis de código en <project>** . Para obtener más información, consulte [Cómo: habilitar y deshabilitar el análisis de código automático](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="rule-sets"></a>Conjuntos de reglas

Reglas de análisis de código para código administrado se agrupan en *conjuntos de reglas*. Puede usar uno de los conjuntos de reglas estándar de Microsoft o puede crear un conjunto de reglas personalizado para satisfacer una necesidad concreta. Para obtener más información, consulte [utilizando conjuntos de reglas para agrupar reglas de análisis de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).

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
> Si migra un proyecto en Visual Studio de 2017, de repente puede encontrar con un número excesivo de advertencias de análisis de código. Si no está preparado para solucionar las advertencias y desea desactivar temporalmente el análisis de código, abra páginas de propiedades del proyecto (**proyecto** > ***proyecto* propiedades...** ) y vaya a la **análisis de código** ficha. Anule la selección de **Habilitar análisis de código al compilar**y, a continuación, recompile el proyecto. Como alternativa, puede seleccionar una regla distintas, menor configurada para ejecutarse en el código. No olvide activar el análisis de código nuevo cuando esté preparado para solucionar las advertencias.

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Ejecutar el análisis de código como parte de la directiva de inserción en el repositorio

En una organización, puede ser necesario exigir que todas las protecciones cumplan determinadas directivas. En particular, es importante asegurarse de que se respeten estas directivas:

- No hay ningún error de compilación en el código que se protege.

- Análisis de código se ejecuta como parte de la compilación más reciente.

Para conseguirlo, se especifican las directivas de inserción en el repositorio. Para obtener más información, consulte [mejorar la calidad del código con directivas de protección del proyecto de equipo](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).

## <a name="team-build-integration"></a>Integración de Team build

Puede utilizar las características integradas del sistema de generación para ejecutar la herramienta de análisis como parte del proceso de generación. Para obtener más información, consulte [de compilación y de la versión (VSTS)](/vsts/build-release/index).

## <a name="see-also"></a>Vea también

[Utilizar conjuntos de reglas para agrupar reglas de análisis de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
[Cómo: habilitar y deshabilitar el análisis de código automático](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)

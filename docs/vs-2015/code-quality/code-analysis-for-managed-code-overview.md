---
title: Análisis de código para obtener información general de código administrado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: overview
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 33ab4a000fac75c51c32e8a6d37de62e006160b3
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2020
ms.locfileid: "72610072"
---
# <a name="code-analysis-for-managed-code-overview"></a>Análisis de código para obtener información general de código administrado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En el análisis de código administrado se analizan los ensamblados administrados y se muestra información sobre dichos ensamblados, como por ejemplo las infracciones de las reglas de programación y las reglas de diseño estipuladas en las instrucciones de diseño de Microsoft .NET Framework.

 La herramienta de análisis representa las comprobaciones que realiza durante un análisis como mensajes de advertencias. Los mensajes de advertencia identifican cualquier problema pertinente de programación y diseño y, cuando es posible, proporcionan información sobre la solución del problema.

## <a name="ide-integrated-development-environment-integration"></a>Integración del entorno de desarrollo integrado (IDE)
 Como desarrollador, puede ejecutar automáticamente el análisis de código en su proyecto o ejecutarlo manualmente.

 Para ejecutar el análisis de código cada vez que compile un proyecto, seleccione **Habilitar análisis de código al compilar (define la constante CODE_ANALYSIS)** en la página Propiedades del proyecto. Para obtener más información, vea [Cómo: Habilitar y deshabilitar el análisis de código automático](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

 Para ejecutar el análisis de código de un proyecto manualmente, en el menú **Analizar**, haga clic en **Ejecutar análisis de código en**_NombredeProyecto_. Para obtener más información, vea [Cómo: Habilitar y deshabilitar el análisis de código automático](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="rule-sets"></a>Conjuntos de reglas
 Las reglas de análisis del código administrado se agrupan en *conjuntos de reglas*. Puede usar uno de los conjuntos de reglas estándar de Microsoft o puede crear un conjunto de reglas personalizado para satisfacer una necesidad concreta. Para más información, vea [Usar conjuntos de reglas para agrupar reglas de análisis de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).

## <a name="in-source-suppression"></a>Supresión en el código fuente
 Normalmente, resulta útil indicar que una advertencia no es aplicable. De este modo, informa al desarrollador y a cualquier otra persona que pudiera revisar el código en el futuro de que se ha investigado una advertencia y se ha suprimido u omitido.

 La supresión de advertencias en el código fuente se implementa mediante atributos personalizados. Para suprimir una advertencia, agregue el atributo `SuppressMessage` al código fuente como se muestra en el ejemplo siguiente:

 ```csharp
 [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
 Public class MyClass
 {
     // code
 }
 ```

 Para más información, vea [Suprimir advertencias mediante el atributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Ejecutar el análisis de código como parte de la directiva de inserción en el repositorio
 En una organización, puede ser necesario exigir que todas las protecciones cumplan determinadas directivas. En particular, es importante asegurarse de que se respeten estas directivas:

- No hay ningún error de compilación en el código que se protege.

- Se ejecutó un análisis de código como parte de la compilación más reciente.

  Para conseguirlo, se especifican las directivas de protección. Para más información, vea [Mejorar la calidad del código con directivas de protección de equipo](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).

## <a name="team-build-integration"></a>Integración de Team Build
 Puede utilizar las características integradas del sistema de generación para ejecutar la herramienta de análisis como parte del proceso de generación. Para obtener más información, consulte [Compilar la aplicación](/azure/devops/pipelines/index).

## <a name="see-also"></a>Vea también
 [Utilizar conjuntos de reglas para agrupar reglas de análisis de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) [ Habilitar y deshabilitar el análisis de código automático](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)

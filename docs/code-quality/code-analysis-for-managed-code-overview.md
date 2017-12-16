---
title: "Análisis de código para código administrado Introducción | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5d42d7c7a78d6bde2560f6e5cf5538a93585870b
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2017
---
# <a name="code-analysis-for-managed-code-overview"></a>Análisis de código para obtener información general de código administrado
En el análisis de código administrado se analizan los ensamblados administrados y se muestra información sobre dichos ensamblados, como por ejemplo las infracciones de las reglas de programación y las reglas de diseño estipuladas en las instrucciones de diseño de Microsoft .NET Framework.  
  
 La herramienta de análisis representa las comprobaciones que realiza durante un análisis como mensajes de advertencias. Los mensajes de advertencia identifican cualquier problema pertinente de programación y diseño y, cuando es posible, proporcionan información sobre la solución del problema.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integración del entorno de desarrollo integrado (IDE)  
 Como desarrollador, puede ejecutar automáticamente el análisis de código en su proyecto o ejecutarlo manualmente.  
  
 Para ejecutar el análisis de código cada vez que compile un proyecto, seleccione **Habilitar análisis de código al compilar (define la constante CODE_ANALYSIS)** en la página de propiedades del proyecto. Para obtener más información, consulte [Cómo: habilitar y deshabilitar el análisis de código automático](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
 Para ejecutar análisis de código de forma manual en un proyecto, en la **analizar** menú, haga clic en **ejecutar análisis de código en***ProjectName*. Para obtener más información, consulte [Cómo: habilitar y deshabilitar el análisis de código automático](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
## <a name="rule-sets"></a>Conjuntos de reglas  
 Reglas de análisis de código para código administrado se agrupan en *conjuntos de reglas*. Puede usar uno de los conjuntos de reglas estándar de Microsoft o puede crear un conjunto de reglas personalizado para satisfacer una necesidad concreta. Para obtener más información, consulte [utilizando conjuntos de reglas para agrupar reglas de análisis de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).  
  
## <a name="in-source-suppression"></a>Supresión en el código fuente  
 Normalmente, resulta útil indicar que una advertencia no es aplicable. De este modo, informa al desarrollador y a cualquier otra persona que pudiera revisar el código en el futuro de que se ha investigado una advertencia y se ha suprimido u omitido.  
  
 La supresión de advertencias en el código fuente se implementa mediante atributos personalizados. Para suprimir una advertencia, agregue el atributo `SuppressMessage` al código fuente como se muestra en el ejemplo siguiente:  
  
 `[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 `Public class MyClass`  
  
 `{`  
  
 `// code`  
  
 `}`  
  
 Para obtener más información, consulte [Suprimir advertencias usando el atributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Ejecutar el análisis de código como parte de la directiva de inserción en el repositorio  
 En una organización, puede ser necesario exigir que todas las protecciones cumplan determinadas directivas. En particular, es importante asegurarse de que se respeten estas directivas:  
  
-   No hay ningún error de compilación en el código que se protege.  
  
-   Se ejecutó un análisis de código como parte de la compilación más reciente.  
  
 Para conseguirlo, se especifican las directivas de inserción en el repositorio. Para obtener más información, consulte [mejorar la calidad del código con directivas de protección del proyecto de equipo](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).  
  
## <a name="team-build-integration"></a>Integración de Team Build  
 Puede utilizar las características integradas del sistema de generación para ejecutar la herramienta de análisis como parte del proceso de generación. Para obtener más información, consulte [de compilación y la versión](/vsts/build-release/index).  
  
## <a name="see-also"></a>Vea también  
 [Utilizar conjuntos de reglas para agrupar reglas de análisis de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
 [Cómo: habilitar y deshabilitar el análisis de código automático](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
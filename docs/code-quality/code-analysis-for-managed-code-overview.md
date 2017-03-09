---
title: "An&#225;lisis de c&#243;digo para obtener informaci&#243;n general de c&#243;digo administrado | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.projectpropertypages.codeanalysis"
helpviewer_keywords: 
  - "análisis de código, código administrado"
  - "código administrado, análisis de código"
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: 35
caps.handback.revision: 35
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# An&#225;lisis de c&#243;digo para obtener informaci&#243;n general de c&#243;digo administrado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En el análisis de código administrado se analizan los ensamblados administrados y se muestra información sobre dichos ensamblados, como por ejemplo las infracciones de las reglas de programación y las reglas de diseño estipuladas en las instrucciones de diseño de Microsoft .NET Framework.  
  
 La herramienta de análisis representa las comprobaciones que realiza durante un análisis como mensajes de advertencias.  Los mensajes de advertencia identifican cualquier problema pertinente de programación y diseño y, cuando es posible, proporcionan información sobre la solución del problema.  
  
## Integración del entorno de desarrollo integrado \(IDE\)  
 Como desarrollador, puede ejecutar automáticamente el análisis de código en su proyecto o ejecutarlo manualmente.  
  
 Para ejecutar el análisis de código cada vez que compile un proyecto, seleccione **Habilitar análisis de código al compilar \(define la constante CODE\_ANALYSIS\)** en la página de propiedades del proyecto.  Para obtener más información, vea [Cómo: Habilitar y deshabilitar el análisis de código automático](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
 Para ejecutar el análisis de código de un proyecto manualmente, en el menú **Analizar**, haga clic en **Ejecutar análisis de código en** *ProjectName*.  Para obtener más información, vea [Cómo: Habilitar y deshabilitar el análisis de código automático](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
## Conjuntos de reglas  
 Las reglas de análisis del código administrado se agrupan en *conjuntos de reglas*.  Puede usar uno de los conjuntos de reglas estándar de Microsoft o puede crear un conjunto de reglas personalizado para satisfacer una necesidad concreta.  Para obtener más información, vea [Utilizar conjuntos de reglas para agrupar reglas de análisis de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).  
  
## Supresión en el código fuente  
 Normalmente, resulta útil indicar que una advertencia no es aplicable.  De este modo, informa al desarrollador y a cualquier otra persona que pudiera revisar el código en el futuro de que se ha investigado una advertencia y se ha suprimido u omitido.  
  
 La supresión de advertencias en el código fuente se implementa mediante atributos personalizados.  Para suprimir una advertencia, agregue el atributo `SuppressMessage` al código fuente como se muestra en el ejemplo siguiente:  
  
 `[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 `Public class MyClass`  
  
 `{`  
  
 `// code`  
  
 `}`  
  
 Para obtener más información, vea [Suprimir advertencias mediante el atributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
## Ejecutar el análisis de código como parte de la directiva de protección  
 En una organización, puede ser necesario exigir que todas las protecciones cumplan determinadas directivas.  En particular, es importante asegurarse de que se respeten estas directivas:  
  
-   No hay ningún error de compilación en el código que se protege.  
  
-   Se ejecutó un análisis de código como parte de la compilación más reciente.  
  
 Para conseguirlo, se especifican las directivas de protección.  Para obtener más información, vea [Mejorar la calidad del código con directivas de protección de equipo](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).  
  
## Integración de Team Build  
 Puede utilizar las características integradas del sistema de generación para ejecutar la herramienta de análisis como parte del proceso de generación.  Para obtener más información, vea [Compilar la aplicación](../Topic/Build%20the%20application.md).  
  
## Vea también  
 [Utilizar conjuntos de reglas para agrupar reglas de análisis de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
 [Cómo: Habilitar y deshabilitar el análisis de código automático](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
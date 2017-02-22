---
title: "C&#243;mo: Especificar conjuntos de reglas de c&#243;digo administrado para varios proyectos de una soluci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.solution"
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Especificar conjuntos de reglas de c&#243;digo administrado para varios proyectos de una soluci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

De forma predeterminada, todos los proyectos administrados de una solución tienen asignado el *conjunto de reglas* de análisis de código Reglas mínimas recomendadas de Microsoft.  Puede cambiar los conjuntos de reglas que se asignan a los proyectos de una solución en el cuadro de diálogo de propiedades de la solución.  
  
> [!NOTE]
>  De forma predeterminada, el análisis de código del proyecto no se ejecuta como un paso de compilación.  Para habilitar el análisis de código como un paso de compilación, vea [Cómo: Configurar el análisis de código para un proyecto de código administrado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).  
  
### Para especificar un conjunto de reglas para varios proyectos de una solución de código administrado  
  
1.  En [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  En [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] o [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], abra la solución.  
  
2.  En el menú **Analizar**, haga clic en **Configurar análisis de código para la solución**.  
  
3.  Si es necesario, expanda **Propiedades comunes** y, a continuación, haga clic en **Configuración de análisis de código**.  
  
4.  Puede especificar un conjunto de reglas para uno o varios proyectos.  
  
    -   Para especificar un conjunto de reglas para un proyecto individual, haga clic en el nombre del proyecto.  
  
    -   Para especificar un conjunto de reglas para varios proyectos, mantenga presionada la tecla CTRL y haga clic en los nombres de proyecto.  
  
    -   Para especificar todos los proyectos de la solución, mantenga presionada la tecla MAYÚS y haga clic en la lista de proyectos.  
  
5.  Haga clic en el campo **Conjunto de reglas** de un proyecto y, a continuación, haga clic en el nombre del conjunto de reglas que desea aplicar.
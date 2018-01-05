---
title: "Cómo: especificar conjuntos de reglas de código administrado para varios proyectos en una solución | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 346ddadef815f4926b0a87a924a502ab2184de3e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Cómo: Especificar conjuntos de reglas de código administrado para varios proyectos de una solución
De forma predeterminada, todos los proyectos administrados de una solución se asignan el análisis de código reglas mínimas recomendadas de Microsoft *conjunto de reglas*. Puede cambiar los conjuntos de reglas que se asignan a los proyectos de una solución en el cuadro de diálogo de propiedades de la solución.  
  
> [!NOTE]
>  De forma predeterminada, el análisis de código del proyecto no se ejecuta como un paso de compilación. Para habilitar el análisis de código como un paso de compilación, consulte [Cómo: configurar el análisis de código para un proyecto de código administrado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).  
  
### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>Para especificar un conjunto de reglas para varios proyectos de una solución de código administrado  
  
1.  En [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]. En [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] o [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], abra la solución.  
  
2.  En el **analizar** menú, haga clic en **configurar análisis de código para la solución**.  
  
3.  Si es necesario, expanda **propiedades comunes**y, a continuación, haga clic en **configuración de análisis de código**.  
  
4.  Puede especificar un conjunto de reglas para uno o varios proyectos.  
  
    -   Para especificar un conjunto de reglas para un proyecto individual, haga clic en el nombre del proyecto.  
  
    -   Para especificar un conjunto de reglas para varios proyectos, mantenga presionada la tecla CTRL y haga clic en los nombres de proyecto.  
  
    -   Para especificar todos los proyectos de la solución, mantenga presionada la tecla MAYÚS y haga clic en la lista de proyectos.  
  
5.  Haga clic en el **conjunto de reglas** campo de un proyecto y, a continuación, haga clic en el nombre de la regla que desea aplicar.
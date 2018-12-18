---
title: 'Cómo: especificar conjuntos de reglas de código administrado para varios proyectos en una solución | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d2469491eeb5419c70e208bbf6e1ed7809657dbc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218704"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Cómo: Especificar conjuntos de reglas de código administrado para varios proyectos de una solución
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

De forma predeterminada, todos los proyectos administrados de una solución se asignan el análisis de código reglas mínimas recomendadas de Microsoft *conjunto de reglas*. Puede cambiar los conjuntos de reglas que se asignan a los proyectos de una solución en el cuadro de diálogo de propiedades de la solución.  
  
> [!NOTE]
>  De forma predeterminada, el análisis de código del proyecto no se ejecuta como un paso de compilación. Para habilitar el análisis de código como un paso de compilación, véase [Cómo: configurar el análisis de código para un proyecto de código administrado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).  
  
### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>Para especificar un conjunto de reglas para varios proyectos de una solución de código administrado  
  
1.  En [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]. En [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] o [!INCLUDE[vsPro](../includes/vspro-md.md)], abra la solución.  
  
2.  En el **analizar** menú, haga clic en **configurar análisis de código para solución**.  
  
3.  Si es necesario, expanda **propiedades comunes**y, a continuación, haga clic en **configuración de análisis de código**.  
  
4.  Puede especificar un conjunto de reglas para uno o varios proyectos.  
  
    -   Para especificar un conjunto de reglas para un proyecto individual, haga clic en el nombre del proyecto.  
  
    -   Para especificar un conjunto de reglas para varios proyectos, mantenga presionada la tecla CTRL y haga clic en los nombres de proyecto.  
  
    -   Para especificar todos los proyectos de la solución, mantenga presionada la tecla MAYÚS y haga clic en la lista de proyectos.  
  
5.  Haga clic en el **Pravidel** campo de un proyecto y, a continuación, haga clic en el nombre de la regla establece que desea aplicar.




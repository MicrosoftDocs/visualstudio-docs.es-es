---
title: "CA1501: Evite una herencia excesiva | Microsoft Docs"
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
  - "CA1501"
  - "AvoidExcessiveInheritance"
helpviewer_keywords: 
  - "AvoidExcessiveInheritance"
  - "CA1501"
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1501: Evite una herencia excesiva
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveInheritance|  
|Identificador de comprobación|CA1501|  
|Categoría|Microsoft.Maintainability|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo tiene más de cuatro niveles de profundidad en su jerarquía de herencia.  
  
## Descripción de la regla  
 Las jerarquías de tipos con demasiados niveles de anidación pueden resultar difíciles de seguir, comprender y mantener.  Esta regla limita el análisis a las jerarquías que se encuentran en el mismo módulo.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, derive el tipo de un tipo base que tenga menor profundidad en la jerarquía de herencia, o bien elimine algunos de los tipos base intermedios.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla.  Sin embargo, el código podría ser más difícil de mantener.  Tenga en cuenta que, según la visibilidad de los tipos base, al resolver infracciones de esta regla, se podrían crear cambios problemáticos.  Por ejemplo, quitar los tipos base públicos constituye un cambio problemático.  
  
## Ejemplo  
 El siguiente ejemplo muestra un tipo que infringe la regla.  
  
 [!code-cs[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]
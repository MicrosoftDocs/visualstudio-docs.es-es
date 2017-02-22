---
title: "CA1506: Evite el acoplamiento excesivo de clases | Microsoft Docs"
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
  - "AvoidExcessiveClassCoupling"
  - "CA1506"
helpviewer_keywords: 
  - "AvoidExcessiveClassCoupling"
  - "CA1506"
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1506: Evite el acoplamiento excesivo de clases
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveClassCoupling|  
|Identificador de comprobación|CA1506|  
|Categoría|Microsoft.Maintainability|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo o método se acoplan con muchos otros tipos.  
  
## Descripción de la regla  
 Esta regla mide el acoplamiento de clase contando el número de referencias de tipo únicas que contiene un tipo o método.  
  
 Los tipos y métodos que tienen un alto grado de acoplamiento de clases pueden resultar difíciles de mantener.  Es una buena práctica para tener tipos y métodos que exhiban acoplamiento bajo y una cohesión alta.  
  
## Cómo corregir infracciones  
 Para corregir esta infracción, intente volver a diseñar el tipo o método con el fin de reducir el número de tipos a los que se acopla.  
  
## Cuándo suprimir advertencias  
 Excluya esta advertencia cuando el tipo o el método se siga considerando fácil de mantener a pesar de su gran número de dependencias en otros tipos.  
  
## Vea también  
 [Advertencias de mantenimiento](../code-quality/maintainability-warnings.md)   
 [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
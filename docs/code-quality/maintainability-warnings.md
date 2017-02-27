---
title: "Advertencias de mantenimiento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.maintainabilityrules"
helpviewer_keywords: 
  - "advertencias, mantenimiento"
  - "advertencias de análisis de código administrado, advertencias de mantenimiento"
  - "advertencias de mantenimiento"
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# Advertencias de mantenimiento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las advertencias de mantenimiento son compatibles con el mantenimiento de la biblioteca y de la aplicación.  
  
## En esta sección  
  
|Regla|Descripción|  
|-----------|-----------------|  
|[CA1500: Los nombres de las variables no deben coincidir con los nombres de los campos](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Un método de instancia declara un parámetro o una variable local cuyo nombre coincide con un campo de instancia del tipo declarativo, lo que da lugar a errores.|  
|[CA1501: Evite una herencia excesiva](../code-quality/ca1501-avoid-excessive-inheritance.md)|Un tipo tiene más de cuatro niveles de profundidad en su jerarquía de herencia.  Las jerarquías de tipos con demasiados niveles de anidación pueden resultar difíciles de seguir, comprender y mantener.|  
|[CA1502: Evite la excesiva complejidad](../code-quality/ca1502-avoid-excessive-complexity.md)|Esta regla mide el número de rutas de acceso independientes de forma lineal a través del método, que es determinado por el número y la complejidad de bifurcaciones condicionales.|  
|[CA1504: Revise los nombres de campos erróneos](../code-quality/ca1504-review-misleading-field-names.md)|El nombre de un campo de instancia empieza por "s\_", o el nombre de un campo estático \(Shared en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) empieza por "m\_".|  
|[CA1505: Evitar el código difícil de mantener](../code-quality/ca1505-avoid-unmaintainable-code.md)|Un tipo o método tiene un valor del índice de mantenimiento bajo.  Un índice de mantenimiento bajo indica que un tipo o método resulta probablemente difícil de mantener y se debería volver a diseñar.|  
|[CA1506: Evite el acoplamiento excesivo de clases](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Esta regla mide el acoplamiento de clase contando el número de referencias de tipo únicas que contiene un tipo o método.|  
  
## Vea también  
 [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
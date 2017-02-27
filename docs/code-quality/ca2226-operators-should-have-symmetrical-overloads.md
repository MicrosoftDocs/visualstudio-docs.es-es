---
title: "CA2226: Los operadores deben tener sobrecargar sim&#233;tricas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OperatorsShouldHaveSymmetricalOverloads"
  - "CA2226"
helpviewer_keywords: 
  - "CA2226"
  - "OperatorsShouldHaveSymmetricalOverloads"
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2226: Los operadores deben tener sobrecargar sim&#233;tricas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OperatorsShouldHaveSymmetricalOverloads|  
|Identificador de comprobación|CA2226|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Un tipo implementa el operador de igualdad o de desigualdad y no implementa el operador opuesto.  
  
## Descripción de la regla  
 No hay ninguna circunstancia en la que la igualdad o desigualdad sea aplicable a las instancias de un tipo y el operador opuesto sea indefinido.  Los tipos normalmente implementan el operador de desigualdad devolviendo el valor negativo del operador de igualdad.  
  
 El compilador de C\# emite un error para las infracciones de esta regla.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, implemente los operadores de igualdad y de desigualdad o quite el que está presente.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  Su tipo no funcionará de manera coherente con [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Reglas relacionadas  
 [CA1046: No sobrecargar el operador de igualdad en los tipos de referencia](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: Las sobrecargas del operador tienen alternativas con nombre](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2224: Reemplazar Equals al sobrecargar operadores de igualdad](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: Reemplazar el método GetHashCode al reemplazar el método Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: Sobrecargar el operador de igualdad al reemplazar el tipo de valor de igualdad](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
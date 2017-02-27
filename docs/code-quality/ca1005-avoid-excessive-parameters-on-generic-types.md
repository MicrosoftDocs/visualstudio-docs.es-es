---
title: "CA1005: Evite par&#225;metros excesivos en tipos gen&#233;ricos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidExcessiveParametersOnGenericTypes"
  - "CA1005"
helpviewer_keywords: 
  - "AvoidExcessiveParametersOnGenericTypes"
  - "CA1005"
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1005: Evite par&#225;metros excesivos en tipos gen&#233;ricos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveParametersOnGenericTypes|  
|Identificador de comprobación|CA1005|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo genérico visible externamente tiene más de dos parámetros type.  
  
## Descripción de la regla  
 Cuantos más parámetros type contenga un tipo genérico, más difícil resulta saber y recordar qué representa cada uno de ellos.  Normalmente, esto resulta evidente con los parámetros de tipo, como en `List<T>`, y en algunos casos con dos parámetros de tipo, como en `Dictionary<TKey, TValue>`.  Si existen más de dos tipos de parámetros, la dificultad se vuelve demasiado grande para la mayoría de los usuarios \(por ejemplo, `TooManyTypeParameters<T, K, V>` en C\# o `TooManyTypeParameters(Of T, K, V)` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el diseño de modo que no se utilicen más de dos parámetros type.  
  
## Cuándo suprimir advertencias  
 No suprima ninguna advertencia de esta regla a menos que el diseño requiera absolutamente más de dos parámetros type.  Al proporcionar genéricos con una sintaxis fácil de entender y utilizar se reduce el tiempo necesario de aprendizaje y se aumenta la velocidad de adopción de nuevas bibliotecas.  
  
## Reglas relacionadas  
 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: Utilizar instancias genéricas de controlador de eventos](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Utilizar valores genéricos cuando sea posible](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Vea también  
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)
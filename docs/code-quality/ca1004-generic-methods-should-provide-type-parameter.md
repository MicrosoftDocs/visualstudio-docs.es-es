---
title: "CA1004: Los m&#233;todos gen&#233;ricos deben proporcionar un par&#225;metro de tipo | Microsoft Docs"
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
  - "CA1004"
  - "GenericMethodsShouldProvideTypeParameter"
helpviewer_keywords: 
  - "CA1004"
  - "GenericMethodsShouldProvideTypeParameter"
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1004: Los m&#233;todos gen&#233;ricos deben proporcionar un par&#225;metro de tipo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|GenericMethodsShouldProvideTypeParameter|  
|Identificador de comprobación|CA1004|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 La firma del parámetro de un método genérico visible externamente no contiene tipos que corresponden a todos los parámetros type del método.  
  
## Descripción de la regla  
 La inferencia es el modo en que se determina el argumento de tipo de un método genérico partiendo del tipo de argumento pasado al método, en lugar de especificar directamente el argumento de tipo.  Para habilitar la inferencia, la firma de parámetro de un método genérico debe incluir un parámetro del mismo tipo que el parámetro type del método.  En este caso, no es necesario especificar el argumento de tipo.  Cuando utiliza la inferencia para todos los parámetros de tipo, la sintaxis para llamar a los métodos de instancia genéricos y no genéricos es la misma.  Así se simplifica el uso de los métodos genéricos.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el diseño de modo que la firma del parámetro contenga el mismo tipo para cada uno de los parámetros de tipo del método.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  Al proporcionar genéricos con una sintaxis fácil de entender y utilizar se reduce el tiempo necesario de aprendizaje y se aumenta la velocidad de adopción de nuevas bibliotecas.  
  
## Ejemplo  
 El ejemplo siguiente muestra la sintaxis para llamar a dos métodos genéricos.  El argumento de tipo de `InferredTypeArgument` se infiere, y el argumento de tipo de `NotInferredTypeArgument` se debe especificar de manera explícita.  
  
 [!code-vb[FxCop.Design.Inference#1](../code-quality/codesnippet/VisualBasic/ca1004-generic-methods-should-provide-type-parameter_1.vb)]
 [!code-cs[FxCop.Design.Inference#1](../code-quality/codesnippet/CSharp/ca1004-generic-methods-should-provide-type-parameter_1.cs)]  
  
## Reglas relacionadas  
 [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1003: Utilizar instancias genéricas de controlador de eventos](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Utilizar valores genéricos cuando sea posible](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Vea también  
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)
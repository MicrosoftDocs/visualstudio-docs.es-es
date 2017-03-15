---
title: "CA1006: No anidar tipos gen&#233;ricos en firmas de miembro | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotNestGenericTypesInMemberSignatures"
  - "CA1006"
helpviewer_keywords: 
  - "CA1006"
  - "DoNotNestGenericTypesInMemberSignatures"
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1006: No anidar tipos gen&#233;ricos en firmas de miembro
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotNestGenericTypesInMemberSignatures|  
|Identificador de comprobación|CA1006|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un miembro visible externamente tiene una firma que contiene un argumento de tipo anidado.  
  
## Descripción de la regla  
 Un argumento de tipo anidado es un argumento de tipo que también es un tipo genérico.  Para llamar a un miembro cuya firma contenga un argumento de tipo anidado, el usuario debe crear instancias de un tipo genérico y pasar este tipo al constructor de un segundo tipo genérico.  El procedimiento y la sintaxis necesarios para ello son complejos, por lo que es preferible evitarlo.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el diseño a fin de quitar el argumento de tipo anidado.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  Al proporcionar genéricos con una sintaxis fácil de entender y utilizar se reduce el tiempo necesario de aprendizaje y se aumenta la velocidad de adopción de nuevas bibliotecas.  
  
## Ejemplo  
 El ejemplo siguiente muestra un método que infringe la regla y la sintaxis que es necesaria para llamar al método infractor.  
  
 [!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
 [!code-cs[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]  
  
## Reglas relacionadas  
 [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: Utilizar instancias genéricas de controlador de eventos](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Utilizar valores genéricos cuando sea posible](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Vea también  
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)
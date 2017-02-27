---
title: "CA1007: Utilizar valores gen&#233;ricos cuando sea posible | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1007"
  - "UseGenericsWhereAppropriate"
helpviewer_keywords: 
  - "CA1007"
  - "UseGenericsWhereAppropriate"
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1007: Utilizar valores gen&#233;ricos cuando sea posible
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseGenericsWhereAppropriate|  
|Identificador de comprobación|CA1007|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método visible externamente contiene un parámetro de referencia de tipo <xref:System.Object?displayProperty=fullName> y el ensamblado que lo contiene está dirigido a [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].  
  
## Descripción de la regla  
 Un parámetro de referencia es un parámetro que se modifica utilizando la palabra clave `ref` \(`ByRef` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  El tipo del argumento proporcionado para un parámetro de referencia debe coincidir exactamente con el tipo del parámetro de referencia.  Para utilizar un tipo que se deriva del tipo del parámetro de referencia, es preciso convertir dicho tipo en primer lugar y asignárselo a una variable del tipo del parámetro de referencia.  El uso de un método genérico permite pasar al método todos los tipos, sujeto a las restricciones que puedan ser de aplicación, sin convertirlos antes al tipo del parámetro de referencia.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, haga que todos los métodos sean genéricos y reemplace el parámetro <xref:System.Object> utilizando un parámetro type.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El ejemplo siguiente muestra una rutina de intercambio de uso general implementada como método no genérico y genérico.  Observe la eficacia con que se intercambian las cadenas utilizando el método genérico, en comparación con el método no genérico.  
  
 [!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
 [!code-cs[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]  
  
## Reglas relacionadas  
 [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: Utilizar instancias genéricas de controlador de eventos](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
## Vea también  
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)
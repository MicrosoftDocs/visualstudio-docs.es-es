---
title: "CA1000: No declarar miembros est&#225;ticos en tipos gen&#233;ricos | Microsoft Docs"
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
  - "CA1000"
  - "DoNotDeclareStaticMembersOnGenericTypes"
helpviewer_keywords: 
  - "CA1000"
  - "DoNotDeclareStaticMembersOnGenericTypes"
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1000: No declarar miembros est&#225;ticos en tipos gen&#233;ricos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|  
|Identificador de comprobación|CA1000|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo genérico visible externamente contiene un miembro `static` \(`Shared` en Visual Basic\).  
  
## Descripción de la regla  
 Cuando se llama a un miembro `static` de un tipo genérico, se debe especificar el argumento de tipo correspondiente a ese tipo.  Cuando se llama a un miembro de instancia genérico que no admite la interferencia, se debe especificar el argumento de tipo para el miembro.  La sintaxis para especificar el argumento de tipo en estos dos casos es diferente y resulta fácil confundirse, como se muestra en las llamadas siguientes:  
  
```vb  
' Shared method in a generic type.  
GenericType(Of Integer).SharedMethod()  
  
' Generic instance method that does not support inference.  
someObject.GenericMethod(Of Integer)()  
```  
  
```c#  
// Static method in a generic type.  
GenericType<int>.StaticMethod();  
  
// Generic instance method that does not support inference.  
someObject.GenericMethod<int>();  
```  
  
 En general, las dos declaraciones anteriores deben evitarse, para que no sea necesario llamar al argumento de tipo cuando se llame al miembro.  Esto produce una sintaxis para llamar a los miembros de los tipos genéricos que no se diferencia de la sintaxis de los tipos no genéricos.  Para obtener más información, vea [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md).  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el miembro estático o cámbielo por un miembro de instancia.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  Al proporcionar genéricos con una sintaxis fácil de entender y utilizar se reduce el tiempo necesario de aprendizaje y se aumenta la velocidad de adopción de nuevas bibliotecas.  
  
## Reglas relacionadas  
 [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: Utilizar instancias genéricas de controlador de eventos](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Utilizar valores genéricos cuando sea posible](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Vea también  
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)
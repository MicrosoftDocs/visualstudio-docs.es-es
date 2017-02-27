---
title: "CA1010: Las colecciones deben implementar la interfaz gen&#233;rica | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1010"
  - "CollectionsShouldImplementGenericInterface"
helpviewer_keywords: 
  - "CA1010"
  - "CollectionsShouldImplementGenericInterface"
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# CA1010: Las colecciones deben implementar la interfaz gen&#233;rica
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CollectionsShouldImplementGenericInterface|  
|Identificador de comprobación|CA1010|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un tipo visible externamente implementa la interfaz <xref:System.Collections.IEnumerable?displayProperty=fullName> pero no la interfaz <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>, y el ensamblado que lo contiene está diseñado para [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].  Esta regla omite los tipos que implementan <xref:System.Collections.IDictionary?displayProperty=fullName>.  
  
## Descripción de la regla  
 Para ampliar la utilidad de una colección, implemente una de las interfaces de colección genéricas.  A continuación, la colección se puede utilizar para rellenar tipos de colecciones genéricas, como los siguientes:  
  
-   <xref:System.Collections.Generic.List%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, implemente una de las interfaces de colección genéricas siguientes:  
  
-   <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.IList%601?displayProperty=fullName>  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla; sin embargo, la colección tendrá un uso más limitado.  
  
## Infracción de ejemplo  
  
### Descripción  
 El ejemplo siguiente muestra una clase \(tipo de referencia\) que deriva de la clase no genérica `CollectionBase`, que infringe esta regla.  
  
### Código  
 [!code-cs[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]  
  
### Comentarios  
 Para corregir una infracción de esta infracción, debe implementar las interfaces genéricas o cambiar la clase base a un tipo que implemente tanto las interfaces genéricas como las no genéricas, como por ejemplo la clase `Collection<T>`.  
  
## Corregir por cambio de clase base  
  
### Descripción  
 En el ejemplo siguiente se corrige la infracción cambiando la clase base de la colección de la clase no genérica `CollectionBase` a la clase genérica `Collection<T>` \(`Collection(Of T)` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
### Código  
 [!code-cs[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]  
  
### Comentarios  
 Si se cambia la clase base de una clase que ya se ha liberado, se considera un cambio importante para los consumidores.  
  
## Corregir por implementación de interfaz  
  
### Descripción  
 En el siguiente ejemplo se corrige la infracción implementado estas interfaces genéricas `IEnumerable<T>`, `ICollection<T>` y `IList<T>` \(`IEnumerable(Of T)`, `ICollection(Of T)` y `IList(Of T)` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
### Código  
 [!code-cs[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]  
  
## Reglas relacionadas  
 [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: Utilizar instancias genéricas de controlador de eventos](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Utilizar valores genéricos cuando sea posible](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Vea también  
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)
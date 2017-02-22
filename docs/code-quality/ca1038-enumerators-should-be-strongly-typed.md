---
title: "CA1038: Los enumeradores deben estar fuertemente tipados | Microsoft Docs"
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
  - "EnumeratorsShouldBeStronglyTyped"
  - "CA1038"
helpviewer_keywords: 
  - "CA1038"
  - "EnumeratorsShouldBeStronglyTyped"
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1038: Los enumeradores deben estar fuertemente tipados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EnumeratorsShouldBeStronglyTyped|  
|Identificador de comprobación|CA1038|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo público o protegido implementa <xref:System.Collections.IEnumerator?displayProperty=fullName> pero no proporciona una versión fuertemente tipada de la propiedad <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName>.  Los tipos que se derivan de los tipos siguientes están exentos de esta regla:  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
## Descripción de la regla  
 Esta regla requiere implementaciones de <xref:System.Collections.IEnumerator> para proporcionar una versión fuertemente tipada de la propiedad <xref:System.Collections.IEnumerator.Current%2A> para que los usuarios no tengan que convertir el valor devuelto en un tipo inflexible cuando utilicen la funcionalidad proporcionada por la interfaz.  Esta regla supone que el tipo que implementa <xref:System.Collections.IEnumerator> contiene una colección de instancias de un tipo de mayor prioridad que <xref:System.Object>.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, implemente explícitamente la propiedad de la interfaz \(declárela como `IEnumerator.Current`\).  Agregue una versión pública de la propiedad fuertemente tipada, declarada como `Current`, y haga que se devuelva un objeto fuertemente tipado.  
  
## Cuándo suprimir advertencias  
 Suprima una advertencia de esta regla cuando implemente un enumerador basado en objetos para utilizarlo con una colección basada en objetos, como un árbol binario.  Los tipos que extienden la nueva colección definirán el enumerador fuertemente tipado y expondrán la propiedad fuertemente tipada.  
  
## Ejemplo  
 El ejemplo siguiente muestra la manera correcta de implementar un tipo <xref:System.Collections.IEnumerator> fuertemente tipado.  
  
 [!code-cs[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]  
  
## Reglas relacionadas  
 [CA1035: Las implementaciones de ICollection tienen miembros fuertemente tipados](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1039: Las listas están fuertemente tipadas](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## Vea también  
 <xref:System.Collections.IEnumerator?displayProperty=fullName>   
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
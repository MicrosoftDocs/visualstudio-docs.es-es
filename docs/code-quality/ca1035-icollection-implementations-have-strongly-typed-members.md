---
title: "CA1035: Las implementaciones de ICollection tienen miembros fuertemente tipados | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ICollectionImplementationsHaveStronglyTypedMembers"
  - "CA1035"
helpviewer_keywords: 
  - "CA1035"
  - "ICollectionImplementationsHaveStronglyTypedMembers"
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1035: Las implementaciones de ICollection tienen miembros fuertemente tipados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|  
|Identificador de comprobación|CA1035|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo público o protegido implementa <xref:System.Collections.ICollection?displayProperty=fullName> pero no proporciona un método fuertemente tipado para <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>.  La versión fuertemente tipada de <xref:System.Collections.ICollection.CopyTo%2A> debe aceptar dos parámetros y no puede tener una <xref:System.Array?displayProperty=fullName> o una matriz de <xref:System.Object?displayProperty=fullName> como su primer parámetro.  
  
## Descripción de la regla  
 Esta regla requiere que las implementaciones de <xref:System.Collections.ICollection> proporcionen miembros fuertemente tipados para que los usuarios no necesiten convertir los argumentos en el tipo <xref:System.Object> cuando utilicen la funcionalidad proporcionada por la interfaz.  Esta regla supone que el tipo que implementa <xref:System.Collections.ICollection> lo hace para administrar una colección de instancias de un tipo que es más segura que <xref:System.Object>.  
  
 <xref:System.Collections.ICollection> implementa la interfaz <xref:System.Collections.IEnumerable?displayProperty=fullName>.  Si los objetos de la colección extienden <xref:System.ValueType?displayProperty=fullName>, debe proporcionar un miembro fuertemente tipado para que <xref:System.Collections.IEnumerable.GetEnumerator%2A> evite la disminución de rendimiento que se produce aplicando la conversión boxing.  Esto no se requiere cuando los objetos de la colección son un tipo de referencia.  
  
 Para implementar una versión fuertemente tipada de un miembro de interfaz, implemente los miembros de interfaz utilizando explícitamente los nombres en el formulario `InterfaceName.InterfaceMemberName`, como <xref:System.Collections.ICollection.CopyTo%2A>.  Los miembros de la interfaz explícitos utilizan los tipos de datos declarados por la interfaz.  Implemente los miembros fuertemente tipados utilizando el nombre del miembro de la interfaz, como <xref:System.Collections.ICollection.CopyTo%2A>.  Declare los miembros fuertemente tipados como públicos, y declare los parámetros y valores devueltos para que sean del tipo seguro que administra la colección.  Los tipos con establecimiento inflexible reemplazan a los tipos más débiles como <xref:System.Object> y <xref:System.Array> declarados por la interfaz.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, implemente explícitamente el miembro de la interfaz \(declárela como <xref:System.Collections.ICollection.CopyTo%2A>\).  Agregue el miembro fuertemente tipado público, declarado como `CopyTo`, y pase una matriz fuertemente tipada como su primer parámetro.  
  
## Cuándo suprimir advertencias  
 Suprima una advertencia de esta regla si implementa una colección nueva basada en objetos, como un árbol binario, donde los tipos que extienden la nueva colección determinan el establecimiento inflexible de tipos.  Estos tipos deberían cumplir esta regla y exponer los miembros fuertemente tipados.  
  
## Ejemplo  
 El ejemplo siguiente muestra la manera correcta de implementar <xref:System.Collections.ICollection>.  
  
 [!code-cs[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]  
  
## Reglas relacionadas  
 [CA1038: Los enumeradores deben estar fuertemente tipados](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
 [CA1039: Las listas están fuertemente tipadas](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## Vea también  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>
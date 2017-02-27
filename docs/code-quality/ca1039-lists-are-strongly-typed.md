---
title: "CA1039: Las listas est&#225;n fuertemente tipadas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1039"
  - "ListsAreStronglyTyped"
helpviewer_keywords: 
  - "CA1039"
  - "ListsAreStronglyTyped"
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1039: Las listas est&#225;n fuertemente tipadas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ListsAreStronglyTyped|  
|Identificador de comprobación|CA1039|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 El tipo público o protegido implementa <xref:System.Collections.IList?displayProperty=fullName> pero no proporciona un método fuertemente tipado para uno o más de los siguientes:  
  
-   IList.Item  
  
-   IList.Add  
  
-   IList.Contains  
  
-   IList.IndexOf  
  
-   IList.Insert  
  
-   IList.Remove  
  
## Descripción de la regla  
 Esta regla requiere que las implementaciones de <xref:System.Collections.IList> proporcionen miembros fuertemente tipados para que los usuarios no necesiten convertir los argumentos en el tipo <xref:System.Object?displayProperty=fullName> cuando utilicen la funcionalidad proporcionada por la interfaz.  Las colecciones de objetos a los que se puede tener acceso por medio del índice implementan la interfaz <xref:System.Collections.IList>.  Esta regla supone que el tipo que implementa <xref:System.Collections.IList> contiene una colección de instancias de un tipo que es más fuerte que <xref:System.Object>.  
  
 <xref:System.Collections.IList> implementa las interfaces <xref:System.Collections.ICollection?displayProperty=fullName> y <xref:System.Collections.IEnumerable?displayProperty=fullName>.  Si implementa <xref:System.Collections.IList>, debe proporcionar los miembros fuertemente tipados necesarios para <xref:System.Collections.ICollection>.  Si los objetos de la colección extienden <xref:System.ValueType?displayProperty=fullName>, deberá proporcionar un miembro fuertemente tipado para <xref:System.Collections.IEnumerable.GetEnumerator%2A> para evitar disminuir el rendimiento provocado por la conversión boxing; esto no es necesario si los objetos de la colección son un tipo de referencia.  
  
 Para cumplir esta regla, implemente los miembros de la interfaz utilizando explícitamente los nombres en el formulario InterfaceName.InterfaceMemberName, como <xref:System.Collections.IList.Add%2A>.  Los miembros de la interfaz explícitos utilizan los tipos de datos declarados por la interfaz.  Implemente los miembros fuertemente tipados utilizando el nombre del miembro de la interfaz, como `Add`.  Declare los miembros fuertemente tipados como públicos, y declare los parámetros y valores devueltos para que sean del tipo seguro que administra la colección.  Los tipos con establecimiento inflexible reemplazan a los tipos más débiles como <xref:System.Object> y <xref:System.Array> declarados por la interfaz.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, explícitamente implemente los miembros <xref:System.Collections.IList> y proporcione las alternativas fuertemente tipadas para los miembros anteriormente mencionados.  Para obtener el código que implementa correctamente la interfaz <xref:System.Collections.IList> y proporciona los miembros fuertemente tipados necesarios, vea el ejemplo siguiente.  
  
## Cuándo suprimir advertencias  
 Suprima una advertencia de esta regla si implementa una colección nueva basada en objetos, como una lista vinculada, donde los tipos que extienden la nueva colección determinan el establecimiento inflexible de tipos.  Estos tipos deberían cumplir esta regla y exponer los miembros fuertemente tipados.  
  
## Ejemplo  
 En el ejemplo siguiente, el tipo `YourType` extiende <xref:System.Collections.CollectionBase?displayProperty=fullName>, como deberían todas las colecciones fuertemente tipadas.  Observe que <xref:System.Collections.CollectionBase> proporciona la implementación explícita de la interfaz <xref:System.Collections.IList> para usted.  Por consiguiente, solo debe proporcionar los miembros fuertemente tipados para <xref:System.Collections.IList> y <xref:System.Collections.ICollection>.  
  
 [!code-cs[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]  
  
## Reglas relacionadas  
 [CA1035: Las implementaciones de ICollection tienen miembros fuertemente tipados](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1038: Los enumeradores deben estar fuertemente tipados](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
## Vea también  
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.IList?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>
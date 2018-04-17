---
title: 'CA1039: Las listas están fuertemente tipadas | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a52479c5c89cf2098ac90e3f755110fb81bb2697
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Las listas están fuertemente tipadas
|||  
|-|-|  
|TypeName|ListsAreStronglyTyped|  
|Identificador de comprobación|CA1039|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Tipo de público o protegido implementa <xref:System.Collections.IList?displayProperty=fullName> , pero no proporciona un método fuertemente tipado para una o varias de las siguientes acciones:  
  
-   IList.Item  
  
-   IList.Add  
  
-   IList.Contains  
  
-   IList.IndexOf  
  
-   IList.Insert  
  
-   IList.Remove  
  
## <a name="rule-description"></a>Descripción de la regla  
 Esta regla requiere que <xref:System.Collections.IList> las implementaciones proporcionen fuertemente tipados miembros para que los usuarios no necesiten convertir los argumentos en la <xref:System.Object?displayProperty=fullName> escriba cuando utilicen la funcionalidad proporcionada por la interfaz. El <xref:System.Collections.IList> interfaz se implementa mediante colecciones de objetos que se pueden tener acceso por índice. Esta regla supone que el tipo que implementa <xref:System.Collections.IList> lo hace para administrar una colección de instancias de un tipo que es más fuerte que <xref:System.Object>.  
  
 <xref:System.Collections.IList> implementa el <xref:System.Collections.ICollection?displayProperty=fullName> y <xref:System.Collections.IEnumerable?displayProperty=fullName> interfaces. Si implementa <xref:System.Collections.IList>, debe proporcionar los miembros fuertemente tipados necesarios para <xref:System.Collections.ICollection>. Si los objetos de la colección extienden <xref:System.ValueType?displayProperty=fullName>, debe proporcionar un miembro fuertemente tipado para <xref:System.Collections.IEnumerable.GetEnumerator%2A> para evitar la disminución del rendimiento debida a la conversión boxing; esto no es necesario cuando los objetos de la colección son un tipo de referencia.  
  
 Para cumplir con esta regla, implemente los miembros de interfaz explícitamente mediante el uso de nombres en el formulario InterfaceName.InterfaceMemberName, como <xref:System.Collections.IList.Add%2A>. Los miembros de interfaz explícita utilicen los tipos de datos que se declaran por la interfaz. Implemente los miembros fuertemente tipados mediante el nombre de miembro de interfaz, como `Add`. Declara a los miembros fuertemente tipados como públicos y declare los parámetros y devuelven valores para que sea de tipo inflexible administrado por la colección. Los tipos seguros reemplazan los tipos más débiles como <xref:System.Object> y <xref:System.Array> que se declaran mediante la interfaz.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, implemente explícitamente <xref:System.Collections.IList> miembros y proporcionan alternativas fuertemente tipados para los miembros que se han registrado previamente. Para el código que implementa correctamente el <xref:System.Collections.IList> de interfaz y proporciona los miembros fuertemente tipados, vea el ejemplo siguiente.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Suprima las advertencias de esta regla al implementar una nueva colección basada en objetos, como una lista vinculada, donde los tipos que extienden la nueva colección determinan el establecimiento inflexible de tipos. Estos tipos deben cumplir con esta regla y exponer miembros fuertemente tipados.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, el tipo de `YourType` extiende <xref:System.Collections.CollectionBase?displayProperty=fullName>, así como todas las colecciones fuertemente tipadas. Tenga en cuenta que <xref:System.Collections.CollectionBase> proporciona la implementación explícita de la <xref:System.Collections.IList> interfaz automáticamente. Por lo tanto, debe proporcionar solo los miembros fuertemente tipados para <xref:System.Collections.IList> y <xref:System.Collections.ICollection>.  
  
 [!code-csharp[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1035: Las implementaciones de ICollection tienen miembros fuertemente tipados](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1038: Los enumeradores deben estar fuertemente tipados](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.IList?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>
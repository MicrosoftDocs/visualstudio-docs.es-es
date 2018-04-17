---
title: 'CA1038: Los enumeradores deben estar fuertemente tipados | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 01b194864f559ff095d8727ff11a4906377aa482
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Los enumeradores deben estar fuertemente tipados
|||  
|-|-|  
|TypeName|EnumeratorsShouldBeStronglyTyped|  
|Identificador de comprobación|CA1038|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo público o protegido implementa <xref:System.Collections.IEnumerator?displayProperty=fullName> pero no proporciona una versión fuertemente tipada de la <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> propiedad. Tipos que se derivan de los tipos siguientes están exentos de esta regla:  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
## <a name="rule-description"></a>Descripción de la regla  
 Esta regla requiere que <xref:System.Collections.IEnumerator> implementaciones para proporcionar una versión fuertemente tipada de la <xref:System.Collections.IEnumerator.Current%2A> propiedad para que los usuarios no necesiten convertir el valor devuelto en un tipo inflexible cuando utilicen la funcionalidad proporcionada por la interfaz. Esta regla supone que el tipo que implementa <xref:System.Collections.IEnumerator> contiene una colección de instancias de un tipo que es más fuerte que <xref:System.Object>.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, implemente explícitamente la propiedad de interfaz (declárela como `IEnumerator.Current`). Agregar una versión fuertemente tipada pública de la propiedad, que se declara como `Current`, y que devuelva un objeto fuertemente tipado.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Suprima las advertencias de esta regla al implementar un enumerador basado en objetos para su uso con una colección basada en objetos, como un árbol binario. Tipos que extienden la nueva colección definirá el enumerador fuertemente tipado y exponer la propiedad fuertemente tipada.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra la forma correcta de implementar un fuertemente tipado <xref:System.Collections.IEnumerator> tipo.  
  
 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1035: Las implementaciones de ICollection tienen miembros fuertemente tipados](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1039: Las listas están fuertemente tipadas](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Collections.IEnumerator?displayProperty=fullName>   
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
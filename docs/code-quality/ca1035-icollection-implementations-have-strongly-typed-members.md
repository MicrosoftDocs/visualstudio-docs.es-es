---
title: 'CA1035: Las implementaciones de ICollection tienen miembros fuertemente tipados'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f9cda0790128bb279d30a15f75080c375ec68aa1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31898330"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: Las implementaciones de ICollection tienen miembros fuertemente tipados
|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|Identificador de comprobación|CA1035|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público o protegido implementa <xref:System.Collections.ICollection?displayProperty=fullName> pero no proporciona un método fuertemente tipado para <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>. La versión fuertemente tipada de <xref:System.Collections.ICollection.CopyTo%2A> debe aceptar dos parámetros y no puede tener un <xref:System.Array?displayProperty=fullName> o una matriz de <xref:System.Object?displayProperty=fullName> como su primer parámetro.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla requiere que <xref:System.Collections.ICollection> las implementaciones proporcionen fuertemente tipados miembros para que los usuarios no necesiten convertir los argumentos en la <xref:System.Object> escriba cuando utilicen la funcionalidad proporcionada por la interfaz. Esta regla supone que el tipo que implementa <xref:System.Collections.ICollection> hace así para administrar una colección de instancias de un tipo que es más fuerte que <xref:System.Object>.

 <xref:System.Collections.ICollection> implementa la interfaz <xref:System.Collections.IEnumerable?displayProperty=fullName>. Si los objetos de la colección extienden <xref:System.ValueType?displayProperty=fullName>, debe proporcionar un miembro fuertemente tipado para <xref:System.Collections.IEnumerable.GetEnumerator%2A> para evitar la disminución de rendimiento que se produjo por la conversión boxing. Esto no es necesario cuando los objetos de la colección son un tipo de referencia.

 Para implementar una versión fuertemente tipada de un miembro de interfaz, implemente los miembros de interfaz explícitamente mediante el uso de nombres en el formulario `InterfaceName.InterfaceMemberName`, como <xref:System.Collections.ICollection.CopyTo%2A>. Los miembros de interfaz explícita utilicen los tipos de datos que se declaran por la interfaz. Implemente los miembros fuertemente tipados mediante el nombre de miembro de interfaz, como <xref:System.Collections.ICollection.CopyTo%2A>. Declara a los miembros fuertemente tipados como públicos y declare los parámetros y devuelven valores para que sea de tipo inflexible administrado por la colección. Los tipos seguros reemplazan los tipos más débiles como <xref:System.Object> y <xref:System.Array> que se declaran mediante la interfaz.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, implemente explícitamente el miembro de interfaz (declárela como <xref:System.Collections.ICollection.CopyTo%2A>). Agregar público fuertemente tipado declarado el miembro, como `CopyTo`, y que lleve a cabo una matriz fuertemente tipada como su primer parámetro.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima las advertencias de esta regla si implementa una nueva colección basada en objetos, como un árbol binario, donde los tipos que extienden la nueva colección determinan el establecimiento inflexible de tipos. Estos tipos deben cumplir con esta regla y exponer miembros fuertemente tipados.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra la forma correcta de implementar <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1038: Los enumeradores deben estar fuertemente tipados](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

 [CA1039: Las listas están fuertemente tipadas](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Vea también
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName> <xref:System.Collections.ICollection?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>
---
title: 'CA1035: Las implementaciones de ICollection tienen miembros fuertemente tipados'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a20feb514b87f2906fd4db32dfb38d3d9b661999
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922826"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: Las implementaciones de ICollection tienen miembros fuertemente tipados

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|Identificador de comprobación|CA1035|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un tipo público o protegido implementa <xref:System.Collections.ICollection?displayProperty=fullName> pero no proporciona un método fuertemente tipado para. <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName> La versión fuertemente tipada de <xref:System.Collections.ICollection.CopyTo%2A> debe aceptar dos parámetros y no puede <xref:System.Array?displayProperty=fullName> tener o una matriz de <xref:System.Object?displayProperty=fullName> como su primer parámetro.

## <a name="rule-description"></a>Descripción de la regla
Esta regla requiere <xref:System.Collections.ICollection> que las implementaciones proporcionen miembros fuertemente tipados para que los usuarios no tengan que convertir los <xref:System.Object> argumentos al tipo cuando utilicen la funcionalidad proporcionada por la interfaz. Esta regla supone que el tipo que implementa <xref:System.Collections.ICollection> lo hace para administrar una colección de instancias de un tipo que es más seguro que. <xref:System.Object>

 <xref:System.Collections.ICollection> implementa la interfaz <xref:System.Collections.IEnumerable?displayProperty=fullName>. Si los objetos de la colección se <xref:System.ValueType?displayProperty=fullName>extienden, debe proporcionar un miembro fuertemente tipado <xref:System.Collections.IEnumerable.GetEnumerator%2A> para para evitar la disminución del rendimiento que se debe a la conversión boxing. Esto no es necesario cuando los objetos de la colección son un tipo de referencia.

Para implementar una versión fuertemente tipada de un miembro de interfaz, implemente los miembros de interfaz explícitamente utilizando nombres `InterfaceName.InterfaceMemberName`en el formulario <xref:System.Collections.ICollection.CopyTo%2A>, como. Los miembros de interfaz explícitos usan los tipos de datos declarados por la interfaz. Implemente los miembros fuertemente tipados mediante el nombre del miembro de interfaz, <xref:System.Collections.ICollection.CopyTo%2A>como. Declare los miembros fuertemente tipados como públicos y declare los parámetros y los valores devueltos para que sean del tipo seguro administrado por la colección. Los tipos seguros reemplazan a los tipos más <xref:System.Object> débiles <xref:System.Array> como y que se declaran mediante la interfaz.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, implemente explícitamente el miembro de interfaz <xref:System.Collections.ICollection.CopyTo%2A>(declárela como). Agregue el miembro con establecimiento inflexible de tipos, `CopyTo`declarado como, y haga que tome una matriz fuertemente tipada como su primer parámetro.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Suprima una advertencia de esta regla si implementa una nueva colección basada en objetos, como un árbol binario, donde los tipos que extienden la nueva colección determinan el tipo seguro. Estos tipos deben cumplir esta regla y exponer miembros fuertemente tipados.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra la manera correcta <xref:System.Collections.ICollection>de implementar.

[!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
[CA1038: Los enumeradores deben tener establecimiento inflexible de tipos](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

[CA1039: Las listas están fuertemente tipadas](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Vea también

- <xref:System.Array?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>
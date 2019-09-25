---
title: 'CA1039: Las listas están fuertemente tipadas'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fcc399457f4dde1c65836d9c9498c782ba92ecc2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235985"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Las listas están fuertemente tipadas

|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|Identificador de comprobación|CA1039|
|Categoría|Microsoft.Design|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo

El tipo público o protegido implementa <xref:System.Collections.IList?displayProperty=fullName> pero no proporciona un método fuertemente tipado para uno o varios de los siguientes elementos:

- IList. Item

- IList. Add

- IList. Contains

- IList. IndexOf

- IList. Insert

- IList. Remove

## <a name="rule-description"></a>Descripción de la regla

Esta regla requiere <xref:System.Collections.IList> que las implementaciones proporcionen miembros fuertemente tipados para que los usuarios no tengan que convertir los argumentos <xref:System.Object?displayProperty=fullName> al tipo cuando utilicen la funcionalidad proporcionada por la interfaz. La <xref:System.Collections.IList> interfaz la implementan colecciones de objetos a los que se puede tener acceso por índice. Esta regla supone que el tipo que implementa <xref:System.Collections.IList> administra una colección de instancias de un tipo que es más seguro <xref:System.Object>que.

<xref:System.Collections.IList>implementa las <xref:System.Collections.ICollection?displayProperty=fullName> interfaces y <xref:System.Collections.IEnumerable?displayProperty=fullName> . Si implementa <xref:System.Collections.IList>, debe proporcionar los miembros fuertemente tipados necesarios para <xref:System.Collections.ICollection>. Si los objetos de la colección se <xref:System.ValueType?displayProperty=fullName>extienden, debe proporcionar un miembro fuertemente tipado <xref:System.Collections.IEnumerable.GetEnumerator%2A> para para evitar la disminución del rendimiento que se debe a la conversión boxing; esto no es necesario cuando los objetos de la colección son un tipo de referencia.

Para cumplir esta regla, implemente los miembros de interfaz explícitamente utilizando nombres con el formato InterfaceName. Nombredemiembrodeinterfaz, <xref:System.Collections.IList.Add%2A>como. Los miembros de interfaz explícitos usan los tipos de datos declarados por la interfaz. Implemente los miembros fuertemente tipados mediante el nombre del miembro de interfaz, `Add`como. Declare los miembros fuertemente tipados como públicos y declare los parámetros y los valores devueltos para que sean del tipo seguro administrado por la colección. Los tipos seguros reemplazan a los tipos más <xref:System.Object> débiles <xref:System.Array> como y que se declaran mediante la interfaz.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, implemente <xref:System.Collections.IList> explícitamente los miembros y proporcione alternativas fuertemente tipadas para los miembros que se han mencionado anteriormente. Para el código que implementa correctamente la <xref:System.Collections.IList> interfaz y proporciona los miembros fuertemente tipados necesarios, vea el ejemplo siguiente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Suprima una advertencia de esta regla al implementar una nueva colección basada en objetos, como una lista vinculada, donde los tipos que extienden la nueva colección determinan el tipo seguro. Estos tipos deben cumplir esta regla y exponer miembros fuertemente tipados.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente, el tipo `YourType` extiende <xref:System.Collections.CollectionBase?displayProperty=fullName>, como todas las colecciones fuertemente tipadas. <xref:System.Collections.CollectionBase>proporciona la implementación explícita de la <xref:System.Collections.IList> interfaz. Por consiguiente, solo debe proporcionar los miembros fuertemente tipados para <xref:System.Collections.IList> y <xref:System.Collections.ICollection>.

[!code-csharp[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
[CA1035: Las implementaciones de ICollection tienen miembros fuertemente tipados](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

[CA1038: Los enumeradores deben tener establecimiento inflexible de tipos](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Vea también

- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.IList?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>
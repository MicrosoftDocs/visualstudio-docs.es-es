---
title: 'CA1038: Los enumeradores deben estar fuertemente tipados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2dae77bf7783edc165305f9b3ba60969d4f126a8
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922892"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Los enumeradores deben estar fuertemente tipados

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|Identificador de comprobación|CA1038|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un tipo público o protegido implementa <xref:System.Collections.IEnumerator?displayProperty=fullName> , pero no proporciona una versión fuertemente tipada de la <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> propiedad. Los tipos que se derivan de los tipos siguientes están exentos de esta regla:

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Descripción de la regla
Esta regla requiere <xref:System.Collections.IEnumerator> que las implementaciones proporcionen también una versión fuertemente tipada <xref:System.Collections.IEnumerator.Current%2A> de la propiedad para que los usuarios no tengan que convertir el valor devuelto al tipo seguro cuando utilicen la funcionalidad proporcionada por la interfaz. Esta regla supone que el tipo que implementa <xref:System.Collections.IEnumerator> contiene una colección de instancias de un tipo que es más seguro que. <xref:System.Object>

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, implemente explícitamente la propiedad de interfaz `IEnumerator.Current`(declárela como). Agregue una versión pública fuertemente tipada de la propiedad, declarada como `Current`, y haga que devuelva un objeto fuertemente tipado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Suprima una advertencia de esta regla al implementar un enumerador basado en objetos para usarlo con una colección basada en objetos, como un árbol binario. Los tipos que extienden la nueva colección definirán el enumerador fuertemente tipado y expondrán la propiedad fuertemente tipada.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra la manera correcta de implementar un <xref:System.Collections.IEnumerator> tipo fuertemente tipado.

[!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
[CA1035: Las implementaciones de ICollection tienen miembros fuertemente tipados](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

[CA1039: Las listas están fuertemente tipadas](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Vea también

- <xref:System.Collections.IEnumerator?displayProperty=fullName>
- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.DictionaryBase?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
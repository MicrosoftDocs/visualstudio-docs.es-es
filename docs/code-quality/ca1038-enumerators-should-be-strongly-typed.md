---
title: 'CA1038: Los enumeradores deben estar fuertemente tipados'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22cc84a0cdc8d4fdb86f6890ae0ebd25eb65beb8
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45545494"
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

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Descripción de la regla
 Esta regla requiere <xref:System.Collections.IEnumerator> implementaciones para proporcionar una versión fuertemente tipada de la <xref:System.Collections.IEnumerator.Current%2A> propiedad para que los usuarios no tienen que convertir el valor devuelto en un tipo inflexible cuando utilicen la funcionalidad proporcionada por la interfaz. Esta regla supone que el tipo que implementa <xref:System.Collections.IEnumerator> contiene una colección de instancias de un tipo que es más fuerte que <xref:System.Object>.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, implemente explícitamente la propiedad de interfaz (declararlo como `IEnumerator.Current`). Agregar una versión pública fuertemente tipada de la propiedad, que se declara como `Current`, y que devuelva un objeto fuertemente tipado.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Suprima una advertencia de esta regla al implementar un enumerador basado en objetos para su uso con una colección de objetos, como un árbol binario. Tipos que extienden la nueva colección definirá el enumerador fuertemente tipado y exponer la propiedad fuertemente tipada.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra la forma correcta para implementar un fuertemente tipado <xref:System.Collections.IEnumerator> tipo.

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1035: Las implementaciones de ICollection tienen miembros fuertemente tipados](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039: Las listas están fuertemente tipadas](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Vea también

- <xref:System.Collections.IEnumerator?displayProperty=fullName>
- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.DictionaryBase?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
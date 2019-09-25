---
title: 'CA2218: Invalidar el método GetHashCode al invalidar el método Equals'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2218
- OverrideGetHashCodeOnOverridingEquals
helpviewer_keywords:
- OverrideGetHashCodeOnOverridingEquals
- CA2218
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8699e3434dc9c4cf9d3eccc37916c20ff7f34015
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231186"
---
# <a name="ca2218-override-gethashcode-on-overriding-equals"></a>CA2218: Invalidar el método GetHashCode al invalidar el método Equals

|||
|-|-|
|TypeName|OverrideGetHashCodeOnOverridingEquals|
|Identificador de comprobación|CA2218|
|Categoría|Microsoft.Usage|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo
Un tipo público invalida <xref:System.Object.Equals%2A?displayProperty=fullName> pero no invalida. <xref:System.Object.GetHashCode%2A?displayProperty=fullName>

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.Object.GetHashCode%2A>Devuelve un valor, basado en la instancia actual, que es adecuado para algoritmos hash y estructuras de datos como una tabla hash. Dos objetos que son del mismo tipo y son iguales deben devolver el mismo código hash para asegurarse de que las instancias de los tipos siguientes funcionan correctamente:

- <xref:System.Collections.Hashtable?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>

- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>

- Tipos que implementan<xref:System.Collections.Generic.IEqualityComparer%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, proporcione una implementación <xref:System.Object.GetHashCode%2A>de. Para un par de objetos del mismo tipo, debe asegurarse de que la implementación devuelve el mismo valor si la implementación de <xref:System.Object.Equals%2A> devuelve `true` para el par.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="class-example"></a>Ejemplo de clase

### <a name="description"></a>Descripción
En el ejemplo siguiente se muestra una clase (tipo de referencia) que infringe esta regla.

### <a name="code"></a>Código
[!code-csharp[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]

### <a name="comments"></a>Comentarios
En el ejemplo siguiente se corrige la infracción <xref:System.Object.GetHashCode>mediante la invalidación de.

### <a name="code"></a>Código
[!code-csharp[FxCop.Usage.GetHashCodeFixedClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]

## <a name="structure-example"></a>Ejemplo de estructura

### <a name="description"></a>Descripción
En el ejemplo siguiente se muestra una estructura (tipo de valor) que infringe esta regla.

### <a name="code"></a>Código
[!code-csharp[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]

### <a name="comments"></a>Comentarios
En el ejemplo siguiente se corrige la infracción <xref:System.Object.GetHashCode>mediante la invalidación de.

### <a name="code"></a>Código
[!code-csharp[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_4.cs)]

## <a name="related-rules"></a>Reglas relacionadas
[CA1046: No sobrecargar el operador Equals en los tipos de referencia](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225 Las sobrecargas de operador tienen alternativas con nombre](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226: Los operadores deben tener sobrecargas simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2224 Invalidar Equals al sobrecargar el operador Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

[CA2231: sobrecargar el operador equals al invalidar ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

## <a name="see-also"></a>Vea también

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- <xref:System.Object.GetHashCode%2A?displayProperty=fullName>
- <xref:System.Collections.Hashtable?displayProperty=fullName>
- [Operadores de igualdad](/dotnet/standard/design-guidelines/equality-operators)
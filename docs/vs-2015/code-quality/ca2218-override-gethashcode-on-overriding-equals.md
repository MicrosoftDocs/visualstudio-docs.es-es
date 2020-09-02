---
title: 'CA2218: invalide GetHashCode al reemplazar Equals | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2218
- OverrideGetHashCodeOnOverridingEquals
helpviewer_keywords:
- OverrideGetHashCodeOnOverridingEquals
- CA2218
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8083edf04aa799c8031fbcd1b53a2e17104dd4a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538806"
---
# <a name="ca2218-override-gethashcode-on-overriding-equals"></a>CA2218: Invalidar el método GetHashCode al invalidar el método Equals
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|OverrideGetHashCodeOnOverridingEquals|
|Identificador de comprobación|CA2218|
|Category|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Un tipo público invalida pero no <xref:System.Object.Equals%2A?displayProperty=fullName> invalida <xref:System.Object.GetHashCode%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.Object.GetHashCode%2A> Devuelve un valor, basado en la instancia actual, que es adecuado para algoritmos hash y estructuras de datos como una tabla hash. Dos objetos que son del mismo tipo y son iguales deben devolver el mismo código hash para asegurarse de que las instancias de los tipos siguientes funcionan correctamente:

- <xref:System.Collections.Hashtable?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>

- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>

- Tipos que implementan <xref:System.Collections.Generic.IEqualityComparer%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, proporcione una implementación de <xref:System.Object.GetHashCode%2A> . Para un par de objetos del mismo tipo, debe asegurarse de que la implementación devuelve el mismo valor si la implementación de <xref:System.Object.Equals%2A> devuelve `true` para el par.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="class-example"></a>Ejemplo de clase

### <a name="description"></a>Descripción
 En el ejemplo siguiente se muestra una clase (tipo de referencia) que infringe esta regla.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.GetHashCodeErrorClass#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeErrorClass/cs/FxCop.Usage.GetHashCodeErrorClass.cs#1)]

### <a name="comments"></a>Comentarios
 En el ejemplo siguiente se corrige la infracción mediante la invalidación de <xref:System.Object.GetHashCode> .

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.GetHashCodeFixedClass#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeFixedClass/cs/FxCop.Usage.GetHashCodeFixedClass.cs#1)]

## <a name="structure-example"></a>Ejemplo de estructura

### <a name="description"></a>Descripción
 En el ejemplo siguiente se muestra una estructura (tipo de valor) que infringe esta regla.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.GetHashCodeErrorStruct#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeErrorStruct/cs/FxCop.Usage.GetHashCodeErrorStruct.cs#1)]

### <a name="comments"></a>Comentarios
 En el ejemplo siguiente se corrige la infracción mediante la invalidación de <xref:System.Object.GetHashCode> .

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.GetHashCodeFixedStruct#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeFixedStruct/cs/FxCop.Usage.GetHashCodeFixedStruct.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1046: No sobrecargar el operador de igualdad en los tipos de referencia](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Las sobrecargas del operador tienen alternativas con nombre](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: Los operadores deben tener sobrecargas simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Invalidar Equals al sobrecargar operadores de igualdad](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: Sobrecargar el operador equals al invalidar ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

## <a name="see-also"></a>Consulte también

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- <xref:System.Object.GetHashCode%2A?displayProperty=fullName>
- <xref:System.Collections.Hashtable?displayProperty=fullName>
- [Operadores de igualdad](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
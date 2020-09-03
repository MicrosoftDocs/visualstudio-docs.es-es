---
title: 'CA2231: sobrecargar el operador de igualdad al reemplazar ValueType. Equals | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
- OverrideOperatorEqualsOnOverridingValueTypeEquals
helpviewer_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f01495e4238461d0b1dfe5a13a208b528df1581f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540301"
---
# <a name="ca2231-overload-operator-equals-on-overriding-valuetypeequals"></a>CA2231: Sobrecargar el operador equals al invalidar ValueType.Equals
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|
|Identificador de comprobación|CA2231|
|Category|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Un tipo de valor invalida <xref:System.Object.Equals%2A?displayProperty=fullName> pero no implementa el operador de igualdad.

## <a name="rule-description"></a>Descripción de la regla
 En la mayoría de los lenguajes de programación no hay ninguna implementación predeterminada del operador de igualdad (= =) para los tipos de valor. Si el lenguaje de programación admite sobrecargas de operador, considere la posibilidad de implementar el operador de igualdad. Su comportamiento debe ser idéntico al de <xref:System.Object.Equals%2A> .

 No se puede usar el operador de igualdad predeterminado en una implementación sobrecargada del operador de igualdad. Si lo hace, se producirá un desbordamiento de pila. Para implementar el operador de igualdad, use el método Object. Equals en su implementación de. Por ejemplo:

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, implemente el operador de igualdad.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla. sin embargo, se recomienda proporcionar el operador de igualdad si es posible.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se define un tipo que infringe esta regla.

 [!code-csharp[FxCop.Usage.EqualsGetHashCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.EqualsGetHashCode/cs/FxCop.Usage.EqualsGetHashCode.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1046: No sobrecargar el operador de igualdad en los tipos de referencia](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Las sobrecargas del operador tienen alternativas con nombre](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: Los operadores deben tener sobrecargas simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Invalidar Equals al sobrecargar operadores de igualdad](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Invalidar el método GetHashCode al invalidar el método Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

## <a name="see-also"></a>Consulte también
 <xref:System.Object.Equals%2A?displayProperty=fullName>

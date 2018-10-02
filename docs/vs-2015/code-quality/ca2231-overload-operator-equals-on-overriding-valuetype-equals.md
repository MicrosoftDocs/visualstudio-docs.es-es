---
title: 'CA2231: Sobrecargar el operador equals al invalidar ValueType.Equals | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
- OverrideOperatorEqualsOnOverridingValueTypeEquals
helpviewer_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6220a32400686637023c04297dbf1a96675a37f9
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591698"
---
# <a name="ca2231-overload-operator-equals-on-overriding-valuetypeequals"></a>CA2231: Sobrecargar el operador de igualdad al reemplazar el tipo de valor de igualdad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA2231: sobrecargar el operador equals al invalidar ValueType.Equals](https://docs.microsoft.com/visualstudio/code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals).

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|
|Identificador de comprobación|CA2231|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un tipo de valor invalida <xref:System.Object.Equals%2A?displayProperty=fullName> pero no implementa el operador de igualdad.

## <a name="rule-description"></a>Descripción de la regla
 No hay ninguna implementación predeterminada del operador de igualdad (==) para tipos de valor en la mayoría de lenguajes de programación. Si su lenguaje de programación admite las sobrecargas del operador, considere la posibilidad de implementar el operador de igualdad. Su comportamiento debe ser idéntico de <xref:System.Object.Equals%2A>.

 No se puede usar el operador de igualdad predeterminado en una implementación del operador de igualdad sobrecargada. Si lo hace, provocará un desbordamiento de pila. Para implementar el operador de igualdad, utilice el método Object.Equals en su implementación. Por ejemplo:

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
 Es seguro suprimir una advertencia de esta regla; Sin embargo, recomendamos que proporcione el operador de igualdad si es posible.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente define un tipo que infringe esta regla.

 [!code-csharp[FxCop.Usage.EqualsGetHashCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.EqualsGetHashCode/cs/FxCop.Usage.EqualsGetHashCode.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1046: No sobrecargar el operador de igualdad en los tipos de referencia](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Las sobrecargas del operador tienen alternativas con nombre](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: Los operadores deben tener sobrecargar simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Invalidar Equals al sobrecargar operadores de igualdad](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Invalidar el método GetHashCode al invalidar el método Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

## <a name="see-also"></a>Vea también
 <xref:System.Object.Equals%2A?displayProperty=fullName>




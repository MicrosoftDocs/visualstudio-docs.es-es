---
title: 'CA2231: Sobrecargar el operador es igual al reemplazar ValueType.Equals | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
- OverrideOperatorEqualsOnOverridingValueTypeEquals
helpviewer_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9ee207eb3e5c4babb5bcb9f7d88f9afd3908a3c7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca2231-overload-operator-equals-on-overriding-valuetypeequals"></a>CA2231: Sobrecargar el operador de igualdad al reemplazar el tipo de valor de igualdad
|||  
|-|-|  
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|  
|Identificador de comprobación|CA2231|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No trascendental|  
  
## <a name="cause"></a>Motivo  
 Un tipo de valor invalida <xref:System.Object.Equals%2A?displayProperty=fullName> pero no implementa el operador de igualdad.  
  
## <a name="rule-description"></a>Descripción de la regla  
 En la mayoría de lenguajes de programación no hay ninguna implementación predeterminada del operador de igualdad (==) para tipos de valor. Si su lenguaje de programación admite las sobrecargas de operador, considere la posibilidad de implementar el operador de igualdad. Su comportamiento debería ser idéntico a la de <xref:System.Object.Equals%2A>.  
  
 No puede utilizar el operador de igualdad predeterminado en una implementación sobrecargada del operador de igualdad. Si lo hace, provocará un desbordamiento de pila. Para implementar el operador de igualdad, utilice el método Object.Equals en la implementación. Por ejemplo:  
  
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
 Es seguro suprimir una advertencia de esta regla; Sin embargo, se recomienda que proporcione el operador de igualdad si es posible.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se define un tipo que infringe esta regla.  
  
 [!code-csharp[FxCop.Usage.EqualsGetHashCode#1](../code-quality/codesnippet/CSharp/ca2231-overload-operator-equals-on-overriding-valuetype-equals_1.cs)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1046: No sobrecargar el operador de igualdad en los tipos de referencia](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: Las sobrecargas del operador tienen alternativas con nombre](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2226: Los operadores deben tener sobrecargar simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: Invalidar Equals al sobrecargar operadores de igualdad](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: Invalidar el método GetHashCode al invalidar el método Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Object.Equals%2A?displayProperty=fullName>
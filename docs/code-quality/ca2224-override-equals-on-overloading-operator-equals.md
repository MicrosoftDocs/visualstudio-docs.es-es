---
title: 'CA2224: Invalidar Equals al sobrecargar operadores de igualdad'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: af2b1af90620fa595d85f7c26d7e5e2c96041dfc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826093"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: Invalidar Equals al sobrecargar operadores de igualdad

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|Identificador de comprobación|CA2224|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Un tipo público implementa el operador de igualdad, pero no invalida <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla

El operador de igualdad está pensado para ser una manera cómoda sintácticamente para tener acceso a la funcionalidad de la <xref:System.Object.Equals%2A> método. Si implementa el operador de igualdad, su lógica debe ser idéntica de <xref:System.Object.Equals%2A>.

El compilador de C# emite una advertencia si el código infringe esta regla.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, debe quitar la implementación del operador de igualdad, o invalidar <xref:System.Object.Equals%2A> y dispone de los dos métodos que devuelven los mismos valores. Si el operador de igualdad no presenta un comportamiento incoherente, puede corregir la infracción proporcionando una implementación de <xref:System.Object.Equals%2A> que llama el <xref:System.Object.Equals%2A> método en la clase base.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla si el operador de igualdad devuelve el mismo valor que la implementación heredada de <xref:System.Object.Equals%2A>. Los ejemplos de este artículo incluyen un tipo que se puede suprimir una advertencia de esta regla de forma segura.

## <a name="examples-of-inconsistent-equality-definitions"></a>Ejemplos de definiciones de igualdad incoherentes

El ejemplo siguiente muestra un tipo con definiciones incoherentes de igualdad. `BadPoint` Cambie el significado de igualdad proporcionando una implementación personalizada del operador de igualdad, pero no invalida <xref:System.Object.Equals%2A> para que se comporte de forma idéntica.

[!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]

El código siguiente comprueba el comportamiento de `BadPoint`.

[!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]

Este ejemplo produce el siguiente resultado:

```txt
a =  ([0] 1,1) and b = ([1] 2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? No
b == bcopy ? Yes
```

El ejemplo siguiente muestra un tipo que técnicamente infringe esta regla, pero no se comporta de forma incoherente.

[!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]

El código siguiente comprueba el comportamiento de `GoodPoint`.

[!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]

Este ejemplo produce el siguiente resultado:

```txt
a =  (1,1) and b = (2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? Yes
b == bcopy ? Yes
```

## <a name="class-example"></a>Ejemplo de clase

El ejemplo siguiente muestra una clase (tipo de referencia) que infringe esta regla.

[!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]

En el ejemplo siguiente se corrige la infracción invalidando <xref:System.Object.Equals%2A?displayProperty=fullName>.

[!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]

## <a name="structure-example"></a>Ejemplo de estructura

El ejemplo siguiente muestra una estructura (tipo de valor) que infringe esta regla:

[!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]

En el ejemplo siguiente se corrige la infracción invalidando <xref:System.ValueType.Equals%2A?displayProperty=fullName>.

[!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]

## <a name="related-rules"></a>Reglas relacionadas

[CA1046: No sobrecargar el operador de igualdad en los tipos de referencia](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225: Las sobrecargas del operador tienen alternativas con nombre](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226: Los operadores deben tener sobrecargar simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2218: Invalidar el método GetHashCode al invalidar Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

[CA2231: sobrecargar el operador equals al invalidar ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
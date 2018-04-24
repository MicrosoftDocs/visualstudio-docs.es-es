---
title: 'CA2225: Las sobrecargas del operador tienen alternativas con nombre'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b6e95f73fbb037041aadcc95eb7336a5744ee2d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: Las sobrecargas del operador tienen alternativas con nombre
|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|Identificador de comprobación|CA2225|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Se detectó una sobrecarga del operador y no se encontró el método alternativo con el nombre esperado.

## <a name="rule-description"></a>Descripción de la regla
 Sobrecarga de operadores permite el uso de símbolos para representar los cálculos para un tipo. Por ejemplo, un tipo que sobrecarga el símbolo más (+) para la suma normalmente tendría un miembro alternativo denominado 'Add'. El miembro alternativo con nombre proporciona acceso a la misma funcionalidad que el operador y se proporciona para los desarrolladores que programan en lenguajes que no admiten operadores sobrecargados.

 Esta regla examina los operadores que aparecen en la tabla siguiente.

|C#|Visual Basic|C++|Nombre alternativo|
|---------|------------------|-----------|--------------------|
|+ (binario)|+|+ (binario)|Add|
|+=|+=|+=|Add|
|&|Y|&|BitwiseAnd|
|&=|Y =|&=|BitwiseAnd|
|&#124;|O bien|&#124;|BitwiseOr|
|&#124;=|O =|&#124;=|BitwiseOr|
|--|N/D|--|Decremento|
|/|/|/|Dividir|
|/=|/=|/=|Dividir|
|==|=|==|Es igual a|
|^|Xor|^|Xor|
|^=|Xor =|^=|Xor|
|>|>|>|Comparar|
|>=|>=|>=|Comparar|
|++|N/D|++|Incremento|
|<>|!=|Es igual a|
|<<|<<|<<|Viceversa|
|<<=|<<=|<<=|Viceversa|
|<|<|<|Comparar|
|<=|<=|\<=|Comparar|
|&&|N/D|&&|AND lógico|
|&#124;&#124;|N/D|&#124;&#124;|LogicalOr|
|!|N/D|!|LogicalNot|
|%|Mod|%|Mod o Remainder|
|%=|N/D|%=|Mod|
|* (binario)|*|*|Multiplicar|
|*=|N/D|*=|Multiplicar|
|~|No|~|OnesComplement|
|>>|>>|>>|Derecha orden|
=|N/D|>>=|Derecha orden|
|-(binario)|-(binario)|-(binario)|Restar|
|-=|N/D|-=|Restar|
|true|IsTrue|N/D|IsTrue (propiedad)|
|-(unario)|N/D|-|Negativo|
|+ (unario)|N/D|+|signo más|
|False|IsFalse|False|IsTrue (propiedad)|

 N/D == no se pueden sobrecargar en el idioma seleccionado.

 La regla también comprueba los operadores de conversión implícita y explícita de un tipo (`SomeType`) mediante la comprobación métodos denominados `ToSomeType` y `FromSomeType`.

 En C#, cuando se sobrecarga un operador binario, el operador de asignación correspondiente, si existe, es también sobrecargado de modo implícito.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, implemente el método alternativo para el operador. Póngale un nombre con el nombre alternativo recomendado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla si está implementando una biblioteca compartida. Las aplicaciones pueden omitir advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se define una estructura que infringe esta regla. Para corregir el ejemplo, agregar un complemento público `Add(int x, int y)` método a la estructura.

 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1046: No sobrecargar el operador de igualdad en los tipos de referencia](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2226: Los operadores deben tener sobrecargar simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Invalidar Equals al sobrecargar operadores de igualdad](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Invalidar el método GetHashCode al invalidar el método Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Sobrecargar el operador equals al invalidar ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
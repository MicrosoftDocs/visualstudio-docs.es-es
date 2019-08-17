---
title: 'CA2225: Las sobrecargas del operador tienen alternativas con nombre'
ms.date: 03/11/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f427bcdf4ec4e88dcc2842699d738dae7e8e09d
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69546904"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: Las sobrecargas del operador tienen alternativas con nombre

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|Identificador de comprobación|CA2225|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa

Se detectó una sobrecarga de operador y no se encontró el método alternativo con nombre esperado.

De forma predeterminada, esta regla solo examina los tipos visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

La sobrecarga de operadores permite el uso de símbolos para representar los cálculos para un tipo. Por ejemplo, un tipo que sobrecarga el signo más (+) para agregar normalmente tendría un miembro alternativo denominado ' Add '. El miembro alternativo con nombre proporciona acceso a la misma funcionalidad que el operador y se proporciona a los desarrolladores que programan en lenguajes que no admiten operadores sobrecargados.

Esta regla examina los operadores enumerados en la tabla siguiente.

|C#|Visual Basic|C++|Nombre alternativo|
|---------|------------------|-----------|--------------------|
|+ (binario)|+|+ (binario)|Agregar|
|+=|+=|+=|Agregar|
|&|y|&|BitwiseAnd|
|&=|Y =|&=|BitwiseAnd|
|&#124;|O bien|&#124;|BitwiseOr|
|&#124;=|O =|&#124;=|BitwiseOr|
|--|N/D|--|Decremento|
|/|/|/|Dividir|
|/=|/=|/=|Dividir|
|==|=|==|Es igual a|
|^|Xor|^|Xor|
|^=|XOR =|^=|Xor|
|>|>|>|Comparar|
|>=|>=|>=|Comparar|
|++|N/D|++|Incremento|
|<>|!=|Es igual a|
|<<|<<|<<|Mayús Izq|
|<<=|<<=|<<=|Mayús Izq|
|<|<|<|Comparar|
|<=|<=|\<=|Comparar|
|&&|N/D|&&|LogicalAnd|
|&#124;&#124;|N/D|&#124;&#124;|Operador lógico|
|!|N/D|!|LogicalNot|
|%|Mod|%|Mod o resto|
|%=|N/D|%=|Mod|
|* (binario)|*|*|Multiplicar|
|*=|N/D|*=|Multiplicar|
|~|not|~|OnesComplement|
|>>|>>|>>|Mayús Der|
=|N/D|>>=|Mayús Der|
|-(binario)|-(binario)|-(binario)|Restar|
|-=|N/D|-=|Restar|
|true|IsTrue|N/D|IsTrue (propiedad)|
|-(unario)|N/D|-|Negar|
|+ (unario)|N/D|+|Signos|
|false|IsFalse|False|IsTrue (propiedad)|

N/A = = no se puede sobrecargar en el idioma seleccionado.

La regla también comprueba los operadores de conversión implícitos y explícitos`SomeType`de un tipo () comprobando `FromSomeType`los métodos denominados `ToSomeType` y.

En C#, cuando se sobrecarga un operador binario, el operador de asignación correspondiente, si existe, también se sobrecarga implícitamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, implemente el método alternativo para el operador. asígnele el nombre alternativo recomendado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima una advertencia de esta regla si está implementando una biblioteca compartida. Las aplicaciones pueden omitir una advertencia de esta regla.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca2225.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (uso). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se define una estructura que infringe esta regla. Para corregir el ejemplo, agregue un método `Add(int x, int y)` público a la estructura.

[!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA1046: No sobrecargar el operador Equals en los tipos de referencia](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2226: Los operadores deben tener sobrecargas simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)
- [CA2224 Invalidar Equals al sobrecargar el operador Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218: Invalidar GetHashCode al reemplazar Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231: sobrecargar el operador equals al invalidar ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
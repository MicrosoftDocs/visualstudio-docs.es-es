---
title: 'CA1046: No sobrecargar el operador de igualdad en los tipos de referencia'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23358d104c891ff9e230f0daad0f5e6ca57b46c2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235764"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: No sobrecargar el operador de igualdad en los tipos de referencia

|||
|-|-|
|TypeName|DoNotOverrideOperatorEqualsOnReferenceTypes|
|Identificador de comprobación|CA1046|
|Categoría|Microsoft.Design|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo
Un tipo de referencia público público o anidado sobrecarga el operador de igualdad.

## <a name="rule-description"></a>Descripción de la regla
Para los tipos de referencia, la implementación predeterminada del operador de igualdad casi siempre es correcta. De manera predeterminada, dos referencias son iguales sólo si señalan al mismo objeto.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, quite la implementación del operador de igualdad.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla cuando el tipo de referencia se comporta como un tipo de valor integrado. Si es significativo realizar sumas o restas en las instancias del tipo, probablemente sea correcto implementar el operador de igualdad y suprimir la infracción.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra el comportamiento predeterminado cuando se comparan dos referencias.

[!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]

## <a name="example"></a>Ejemplo

En la siguiente aplicación se comparan algunas referencias.

[!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]

Este ejemplo produce el siguiente resultado:

```txt
a = new (2,2) and b = new (2,2) are equal? No
c and a are equal? Yes
b and a are == ? No
c and a are == ? Yes
```

## <a name="related-rules"></a>Reglas relacionadas

[CA1013: Sobrecargar el operador de igualdad en la sobrecarga de suma y resta](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>Vea también

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Operadores de igualdad](/dotnet/standard/design-guidelines/equality-operators)
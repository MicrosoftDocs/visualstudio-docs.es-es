---
title: 'CA1815: Invalidar Equals y el operador Equals en los tipos de valores'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 413119f7cdf473f3038ae212ac812d1987641bb1
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233548"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: Invalidar Equals y el operador Equals en los tipos de valores

|||
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|Identificador de comprobación|CA1815|
|Categoría|Microsoft.Performance|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Un tipo de valor no invalida <xref:System.Object.Equals%2A?displayProperty=fullName> o no implementa el operador de igualdad (= =). Esta regla no comprueba las enumeraciones.

De forma predeterminada, esta regla solo examina los tipos visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

En el caso de los tipos de valor <xref:System.Object.Equals%2A> , la implementación heredada de utiliza la biblioteca de reflexión y compara el contenido de todos los campos. Mediante el cálculo, la reflexión es cara y no es necesario comparar cada campo para comprobar si hay igualdad. Si espera que los usuarios comparen u ordenen instancias, o las usen como claves de tabla hash, el <xref:System.Object.Equals%2A>tipo de valor debe implementar. Si el lenguaje de programación admite la sobrecarga de operadores, también debe proporcionar una implementación de los operadores de igualdad y desigualdad.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, proporcione una implementación <xref:System.Object.Equals%2A>de. Si es posible, implemente el operador de igualdad.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla si las instancias del tipo de valor no se compararán entre sí.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1815.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (rendimiento). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Ejemplo

En el código siguiente se muestra una estructura (tipo de valor) que infringe esta regla:

[!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]

En el código siguiente se corrige la infracción anterior <xref:System.ValueType.Equals%2A?displayProperty=fullName> invalidando e implementando los operadores de igualdad (= =,! =):

[!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA2224 Invalidar Equals al sobrecargar el operador Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2231: sobrecargar el operador equals al invalidar ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
- [CA2226: Los operadores deben tener sobrecargas simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>Vea también

- <xref:System.Object.Equals%2A?displayProperty=fullName>
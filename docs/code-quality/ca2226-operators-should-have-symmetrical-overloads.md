---
title: 'CA2226: Los operadores deben tener sobrecargas simétricas'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d9e486d4193645335189c475fdd3ca220374d96
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231437"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226: Los operadores deben tener sobrecargas simétricas

|||
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|Identificador de comprobación|CA2226|
|Categoría|Microsoft.Usage|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Un tipo implementa el operador de igualdad o de desigualdad y no implementa el operador opuesto.

De forma predeterminada, esta regla solo examina los tipos visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

No hay circunstancias en las que la igualdad o la desigualdad se aplican a las instancias de un tipo, y el operador opuesto es indefinido. Normalmente, los tipos implementan el operador de desigualdad devolviendo el valor negado del operador de igualdad.

El C# compilador emite un error para las infracciones de esta regla.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, implemente los operadores de igualdad y desigualdad, o bien Quite el que está presente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla. Si lo hace, el tipo no funcionará de forma coherente con .NET.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca2226.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (uso). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Reglas relacionadas

- [CA1046: No sobrecargar el operador Equals en los tipos de referencia](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2225 Las sobrecargas de operador tienen alternativas con nombre](../code-quality/ca2225-operator-overloads-have-named-alternates.md)
- [CA2224 Invalidar Equals al sobrecargar el operador Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218: Invalidar GetHashCode al reemplazar Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231: sobrecargar el operador equals al invalidar ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
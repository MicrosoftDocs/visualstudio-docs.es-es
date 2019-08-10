---
title: 'CA1005: Evitar los parámetros excesivos en tipos genéricos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffc94a04d708315cc143afd1556cb8a2f0072e91
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923300"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005: Evitar los parámetros excesivos en tipos genéricos

|||
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|Identificador de comprobación|CA1005|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un tipo genérico visible externamente tiene más de dos parámetros de tipo.

## <a name="rule-description"></a>Descripción de la regla
Cuantos más parámetros type contenga un tipo genérico, más difícil resulta saber y recordar qué representa cada uno de ellos. Normalmente, es obvio con un parámetro de tipo, como `List<T>`en, y en algunos casos con dos parámetros de tipo, `Dictionary<TKey, TValue>`como en. Si existen más de dos parámetros de tipo, la dificultad es demasiado grande para la mayoría de los usuarios `TooManyTypeParameters<T, K, V>` ( C# por `TooManyTypeParameters(Of T, K, V)` ejemplo [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], en o en).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, cambie el diseño para que no use más de dos parámetros de tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima una advertencia de esta regla a menos que el diseño requiera absolutamente más de dos parámetros de tipo. Proporcionar genéricos en una sintaxis que sea fácil de entender y usar reduce el tiempo necesario para aprender y aumentar la tasa de adopción de nuevas bibliotecas.

## <a name="related-rules"></a>Reglas relacionadas
[CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006: No anide tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Usar instancias de controlador de eventos genéricos](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007: Usar genéricos cuando sea necesario](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vea también
[Genéricos](/dotnet/csharp/programming-guide/generics/index)
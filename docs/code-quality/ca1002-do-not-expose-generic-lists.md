---
title: 'CA1002: No exponer listas genéricas'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0612886bf92a4ca6a30e5e15ae1c4a4950d9ddad
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236660"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: No exponer listas genéricas

|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|Identificador de comprobación|CA1002|
|Categoría|Microsoft.Design|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo

Un tipo contiene un miembro visible externamente que es un <xref:System.Collections.Generic.List%601?displayProperty=fullName> tipo, devuelve un <xref:System.Collections.Generic.List%601> tipo o cuya firma incluye un <xref:System.Collections.Generic.List%601> parámetro.

## <a name="rule-description"></a>Descripción de la regla

<xref:System.Collections.Generic.List%601?displayProperty=fullName>es una colección genérica diseñada para el rendimiento y no para la herencia. <xref:System.Collections.Generic.List%601>no contiene miembros virtuales que facilitan el cambio del comportamiento de una clase heredada. Las colecciones genéricas siguientes están diseñadas para la herencia y deben exponerse <xref:System.Collections.Generic.List%601>en lugar de.

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, cambie <xref:System.Collections.Generic.List%601?displayProperty=fullName> el tipo a una de las colecciones genéricas que está diseñada para la herencia.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima una advertencia de esta regla a menos que el ensamblado que genera esta advertencia no esté diseñado para ser una biblioteca reutilizable. Por ejemplo, sería seguro suprimir esta advertencia en una aplicación optimizada para el rendimiento en la que se obtuvo una ventaja de rendimiento del uso de listas genéricas.

## <a name="related-rules"></a>Reglas relacionadas

[CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1006: No anide tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Usar instancias de controlador de eventos genéricos](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007: Usar genéricos cuando sea necesario](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vea también

[Genéricos](/dotnet/csharp/programming-guide/generics/index)

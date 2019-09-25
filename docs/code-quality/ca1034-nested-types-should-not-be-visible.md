---
title: 'CA1034: Los tipos anidados no deben ser visibles'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ead932af202bd1a44464025a1b09baa698acb7b1
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236036"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: Los tipos anidados no deben ser visibles

|||
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|Identificador de comprobación|CA1034|
|Categoría|Microsoft.Design|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo

Un tipo visible externamente contiene una declaración de tipos visible externamente. Las enumeraciones anidadas y los tipos protegidos están exentos de esta regla.

## <a name="rule-description"></a>Descripción de la regla
Un tipo anidado es un tipo declarado dentro del ámbito de otro tipo. Los tipos anidados son útiles para encapsular los detalles de la implementación privada del tipo contenedor. Los tipos anidados, utilizados para este propósito, no deben ser visibles externamente.

No utilice tipos anidados visibles externamente para la Agrupación lógica o para evitar colisiones de nombres; en su lugar, use los espacios de nombres.

Los tipos anidados incluyen la noción de accesibilidad de miembros, que algunos programadores no entienden claramente.

Los tipos protegidos se pueden utilizar en subclases y tipos anidados en escenarios de personalización anticipada.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Si no desea que el tipo anidado esté visible externamente, cambie la accesibilidad del tipo. De lo contrario, quite el tipo anidado de su elemento primario. Si el propósito de la anidación es categorizar el tipo anidado, use un espacio de nombres para crear la jerarquía en su lugar.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un tipo que infringe la regla.

[!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
[!code-csharp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
[!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]
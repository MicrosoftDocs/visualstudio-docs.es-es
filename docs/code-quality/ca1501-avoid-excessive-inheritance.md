---
title: 'CA1501: Evitar una herencia excesiva'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 88464effce80b6957dc8945ad17f5a39b4f449c8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234518"
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501: Evitar una herencia excesiva

|||
|-|-|
|TypeName|AvoidExcessiveInheritance|
|Identificador de comprobación|CA1501|
|Categoría|Microsoft. mantenibilidad|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo

Un tipo tiene más de cuatro niveles de profundidad en su jerarquía de herencia.

## <a name="rule-description"></a>Descripción de la regla

Las jerarquías de tipos con demasiados niveles de anidación pueden resultar difíciles de seguir, comprender y mantener. Esta regla limita el análisis a las jerarquías en el mismo módulo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, derive el tipo de un tipo base que sea menos profundo en la jerarquía de herencia o elimine algunos de los tipos base intermedios.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla. Sin embargo, el código puede ser más difícil de mantener. Tenga en cuenta que, en función de la visibilidad de los tipos base, la resolución de infracciones de esta regla podría crear cambios importantes. Por ejemplo, la eliminación de tipos base públicos es un cambio importante.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un tipo que infringe la regla:

[!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
[!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]
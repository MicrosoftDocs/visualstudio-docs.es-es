---
title: 'CA1034: Los tipos anidados no deben ser visibles'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: cce4f148311c301607c57a77aac46787e0578391
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890948"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: Los tipos anidados no deben ser visibles

|||
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|Identificador de comprobación|CA1034|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

Un tipo visible externamente contiene una declaración de tipos visibles externamente. Las enumeraciones anidadas y los tipos protegidos están exentos de esta regla.

## <a name="rule-description"></a>Descripción de la regla
 Un tipo anidado es un tipo declarado dentro del ámbito de otro tipo. Los tipos anidados son útiles para encapsular los detalles de la implementación privada del tipo contenedor. Los tipos anidados, utilizados para este propósito, no deben ser visibles externamente.

 No utilice tipos anidados visibles externamente para agrupación lógica o para evitar conflictos de nombres; en su lugar, use los espacios de nombres.

 Los tipos anidados incluyen la noción de accesibilidad de miembro, que algunos programadores no entienden con claridad.

 Los tipos protegidos pueden usarse en subclases y los tipos anidados en escenarios de personalización avanzada.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Si no desea que el tipo anidado que esté visible externamente, cambie la accesibilidad del tipo. En caso contrario, quite el tipo anidado de su elemento primario. Si el propósito del anidamiento es clasificar el tipo anidado, utilice un espacio de nombres para crear la jerarquía en su lugar.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que infringe la regla.

 [!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]
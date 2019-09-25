---
title: 'CA2222: No disminuir la visibilidad del miembro heredado'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c737a30569ab4cd59931a3fca0e500ebe96e62de
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230977"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: No disminuir la visibilidad del miembro heredado

|||
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|Identificador de comprobación|CA2222|
|Categoría|Microsoft.Usage|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Un método privado de un tipo no sellado tiene una firma idéntica a un método público declarado en un tipo base. El método privado no es final.

## <a name="rule-description"></a>Descripción de la regla

No cambie el modificador de acceso para los miembros heredados. Cambiando un miembro heredado a privado no evita que los llamadores tengan acceso a la implementación de la clase base del método. Si el miembro se convierte en privado y el tipo no está sellado, los tipos heredados pueden llamar a la última implementación pública del método en la jerarquía de herencia. Si debe cambiar el modificador de acceso, el método debe marcarse como final o su tipo debe estar sellado para evitar que el método se invalide.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, cambie el acceso a no privado. Como alternativa, si el lenguaje de programación lo admite, puede hacer que el método sea final.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un tipo que infringe esta regla.

[!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
[!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]
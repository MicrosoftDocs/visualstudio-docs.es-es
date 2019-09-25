---
title: 'CA1047: No declarar miembros protegidos en tipos sellados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3114ea004c425567ae479343e0449d2cbc3aa669
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235702"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: No declarar miembros protegidos en tipos sellados

|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|Identificador de comprobación|CA1047|
|Categoría|Microsoft.Design|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo
Un tipo público es `sealed` (`NotInheritable` en Visual Basic) y declara un miembro protegido o un tipo anidado protegido. Esta regla no notifica las infracciones <xref:System.Object.Finalize%2A> de los métodos, que deben seguir este patrón.

## <a name="rule-description"></a>Descripción de la regla
Los tipos declaran miembros protegidos para que los tipos heredados puedan obtener acceso o reemplazar el miembro. Por definición, no se puede heredar de un tipo sellado, lo que significa que no se puede llamar a los métodos protegidos en tipos sellados.

El C# compilador emite una advertencia para este error.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, cambie el nivel de acceso del miembro a Private o haga que el tipo sea heredable.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla. Si se deja el tipo en su estado actual, se pueden producir problemas de mantenimiento y no se proporciona ninguna ventaja.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un tipo que infringe esta regla.

[!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
[!code-csharp[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]
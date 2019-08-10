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
ms.openlocfilehash: 5ab7cf2c5a4f17966ed5b4da30657e05a4683738
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922646"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: No declarar miembros protegidos en tipos sellados

|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|Identificador de comprobación|CA1047|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

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
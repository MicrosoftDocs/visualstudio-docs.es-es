---
title: 'CA1047: No declarar miembros protegidos en tipos sellados'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b46e64fb4092f8e0f773671ff13eb401b6b67890
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53912865"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: No declarar miembros protegidos en tipos sellados

|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|Identificador de comprobación|CA1047|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Es un tipo público `sealed` (`NotInheritable` en Visual basic) y declara un miembro protegido o un tipo anidado protegido. Esta regla no informa de las infracciones de <xref:System.Object.Finalize%2A> métodos, que deben seguir este patrón.

## <a name="rule-description"></a>Descripción de la regla
 Los tipos declaran miembros protegidos para que los tipos heredados puedan obtener acceso o reemplazar el miembro. Por definición, no puede heredar de un tipo sealed, lo que significa que los métodos protegidos en tipos sellados no se puede llamar.

 El compilador de C# emite una advertencia para este error.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambiar el nivel de acceso del miembro en privado o hacer que el tipo sea heredable.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla. Lo que deja el tipo en su estado actual puede causar problemas de mantenimiento y no proporciona ninguna ventaja.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que infringe esta regla.

 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-csharp[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]
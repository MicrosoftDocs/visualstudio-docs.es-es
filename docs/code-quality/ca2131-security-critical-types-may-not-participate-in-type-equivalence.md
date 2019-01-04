---
title: 'CA2131: Los tipos críticos para la seguridad no pueden participar en la equivalencia de tipos'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f91f5be2aad41006dacab059db27e9609a4f84f7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913034"
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131: Los tipos críticos para la seguridad no pueden participar en la equivalencia de tipos

|||
|-|-|
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|
|Identificador de comprobación|CA2131|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo participa en la equivalencia de tipos y un el propio tipo o un miembro o campo del tipo, se marca con el <xref:System.Security.SecurityCriticalAttribute> atributo.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla se produce en todos los tipos críticos o en los tipos que contienen métodos o campos críticos que participan en la equivalencia de tipos. Cuando CLR detecta este tipo, se produce un error de carga con una <xref:System.TypeLoadException> en tiempo de ejecución. Normalmente, esta regla solo se desencadena cuando los usuarios implementan la equivalencia de tipos manualmente en lugar de confiar en tlbimp y los compiladores para hacer la equivalencia de tipos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el atributo SecurityCritical.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 Los ejemplos siguientes muestran una interfaz, un método y un campo que hará que esta regla se active.

 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]

## <a name="see-also"></a>Vea también
 [Código transparente en seguridad, nivel 2](/dotnet/framework/misc/security-transparent-code-level-2)
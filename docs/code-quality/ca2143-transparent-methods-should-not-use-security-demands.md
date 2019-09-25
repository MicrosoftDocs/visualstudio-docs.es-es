---
title: 'CA2143: Los métodos transparentes no deben usar peticiones de seguridad'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a182beba738e583fad83c3f51d7efa312761906d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231983"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: Los métodos transparentes no deben usar peticiones de seguridad

|||
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|Identificador de comprobación|CA2143|
|Categoría|Microsoft.Security|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo
Un tipo o método tranparent se marca mediante declaración con una <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` petición o el método llama al <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> método.

## <a name="rule-description"></a>Descripción de la regla
El código transparente en seguridad no debería ser responsable de comprobar la seguridad de una operación y, por consiguiente, no debería exigir permisos. El código transparente en seguridad debería utilizar peticiones completas para tomar decisiones de seguridad y el código crítico para la seguridad no debió confiar en el código transparente al realizar la petición completa. Cualquier código que realice comprobaciones de seguridad, como las demandas de seguridad, debe ser crítico para la seguridad en su lugar.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
En general, para corregir una infracción de esta regla, marque el método con <xref:System.Security.SecuritySafeCriticalAttribute> el atributo. También puede quitar la demanda.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
Los archivos de reglas en el código siguiente porque un método transparente realiza una petición de seguridad declarativa.

[!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]

## <a name="see-also"></a>Vea también
[CA2142: El código transparente no debe protegerse con LinkDemands](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)
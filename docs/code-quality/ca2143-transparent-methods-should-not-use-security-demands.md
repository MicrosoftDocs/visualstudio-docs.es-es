---
title: 'CA2143: Los métodos transparentes no deben usar peticiones de seguridad'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 08a7c4d6d7c71954869311b402eed65492391432
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55043082"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: Los métodos transparentes no deben usar peticiones de seguridad

|||
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|Identificador de comprobación|CA2143|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo o método transparente se marca mediante declaración con un <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` a petición o las llamadas al método el <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> método.

## <a name="rule-description"></a>Descripción de la regla
 El código transparente en seguridad no debería ser responsable de comprobar la seguridad de una operación y, por consiguiente, no debería exigir permisos. El código transparente en seguridad debería utilizar peticiones completas para tomar decisiones de seguridad y el código crítico para la seguridad no debió confiar en el código transparente al realizar la petición completa. Cualquier código que realiza comprobaciones de seguridad, como las peticiones de seguridad, debe ser crítico para la seguridad en su lugar.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 En general, para corregir una infracción de esta regla, marque el método con el <xref:System.Security.SecuritySafeCriticalAttribute> atributo. También puede quitar la demanda.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 La regla de archivos en el código siguiente porque un método transparente realiza una petición de seguridad declarativa.

 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]

## <a name="see-also"></a>Vea también
 [CA2142: El código transparente no debe protegerse con LinkDemands](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)
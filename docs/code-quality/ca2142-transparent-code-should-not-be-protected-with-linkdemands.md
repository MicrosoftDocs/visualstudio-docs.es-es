---
title: 'CA2142: El código transparente no debe protegerse con LinkDemands'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab0f6aaae97a510b0521e10ad607a86988c345a3
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232080"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: El código transparente no debe protegerse con LinkDemands

|||
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|Identificador de comprobación|CA2142|
|Categoría|Microsoft.Security|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo
Un método transparente requiere una <xref:System.Security.Permissions.SecurityAction> u otra demanda de seguridad.

## <a name="rule-description"></a>Descripción de la regla
Esta regla se desencadena en métodos transparentes que requieren LinkDemands para tener acceso a ellos. El código transparente en seguridad no debería ser responsable de comprobar la seguridad de una operación y, por consiguiente, no debería exigir permisos. Dado que se supone que los métodos transparentes son independientes de la seguridad, no deben tomar ninguna decisión de seguridad. Además, el código crítico seguro, que toma decisiones de seguridad, no debe confiar en el código transparente para que previamente haya tomado tal decisión.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, quite la petición de vínculo en el método transparente o marque el <xref:System.Security.SecuritySafeCriticalAttribute> método con el atributo si está realizando comprobaciones de seguridad, como las demandas de seguridad.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente, la regla se desencadena en el método porque el método es transparente y está marcado con una <xref:System.Security.PermissionSet> LinkDemand que <xref:System.Security.Permissions.SecurityAction>contiene.

[!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]

No suprima las advertencias de esta regla.
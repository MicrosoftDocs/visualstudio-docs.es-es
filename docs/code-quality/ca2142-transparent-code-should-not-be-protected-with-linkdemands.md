---
title: 'CA2142: El código transparente no se debería proteger con LinkDemands'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4ce7243630179aede0ce20aba998f6cb5eed0100
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887174"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: El código transparente no se debería proteger con LinkDemands

|||
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|Identificador de comprobación|CA2142|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método transparente requiere un <xref:System.Security.Permissions.SecurityAction> u otra demanda de seguridad.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla se desencadena en los métodos transparentes que requieren LinkDemands tenga acceso a ellos. El código transparente en seguridad no debería ser responsable de comprobar la seguridad de una operación y, por consiguiente, no debería exigir permisos. Porque se supone que los métodos transparentes seguridad neutra, no deberían tomar las decisiones de seguridad. Además, el código crítico seguro, que tomar decisiones sobre seguridad, no debería basarse en el código transparente que haya realizado previamente una decisión.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite la petición de vínculo en el método transparente o marque el método con <xref:System.Security.SecuritySafeCriticalAttribute> comprueba si está realizando la seguridad de atributo, como las peticiones de seguridad.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, la regla se desencadena en el método porque el método es transparente y se marca con LinkDemand <xref:System.Security.PermissionSet> que contiene un <xref:System.Security.Permissions.SecurityAction>.

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]

 No suprima las advertencias de esta regla.
---
title: 'CA2142: El código transparente no se debería proteger con LinkDemands'
ms.date: 11/04/2016
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
ms.openlocfilehash: 58f0c934c029c65a07fd0e89a5822dbbe0849428
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: El código transparente no se debería proteger con LinkDemands
|||
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|Identificador de comprobación|CA2142|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método transparente requiere una <xref:System.Security.Permissions.SecurityAction> u otra demanda de seguridad.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla se desencadena en los métodos transparentes que requieren que las LinkDemand tengan acceso a ellos. El código transparente en seguridad no debería ser responsable de comprobar la seguridad de una operación y, por consiguiente, no debería exigir permisos. Porque los métodos transparentes deben seguridad neutra, no deberían tomar las decisiones de seguridad. Además, el código crítico seguro, que tomar decisiones de seguridad, no debería basarse en el código transparente al que se haya realizado previamente una decisión de este tipo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite la petición de vínculo en el método transparente o marque el método con <xref:System.Security.SecuritySafeCriticalAttribute> comprueba si está realizando la seguridad de atributo, como las peticiones de seguridad.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, la regla se desencadena en el método porque el método es transparente y se marca con una LinkDemand <xref:System.Security.PermissionSet> que contiene un <xref:System.Security.Permissions.SecurityAction>.

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]

 No suprima las advertencias de esta regla.
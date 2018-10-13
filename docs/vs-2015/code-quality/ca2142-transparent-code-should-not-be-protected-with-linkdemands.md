---
title: 'CA2142: El código transparente no debe protegerse con LinkDemands | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 79441a1aaa37e0df564f9021d5106dae1bf8329e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232458"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: El código transparente no se debería proteger con LinkDemands
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|Identificador de comprobación|CA2142|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método transparente requiere un <xref:System.Security.Permissions.SecurityAction> u otra demanda de seguridad.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla se desencadena en los métodos transparentes que requieren que las LinkDemand tengan acceso a ellos. El código transparente en seguridad no debería ser responsable de comprobar la seguridad de una operación y, por consiguiente, no debería exigir permisos. Porque se supone que los métodos transparentes seguridad neutra, no deberían tomar las decisiones de seguridad. Además, el código crítico seguro, que tomar decisiones sobre seguridad, no debería basarse en el código transparente que haya realizado previamente una decisión.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite la petición de vínculo en el método transparente o marque el método con <xref:System.Security.SecuritySafeCriticalAttribute> comprueba si está realizando la seguridad de atributo, como las peticiones de seguridad.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, la regla se desencadena en el método porque el método es transparente y se marca con LinkDemand <xref:System.Security.PermissionSet> que contiene un <xref:System.Security.Permissions.SecurityAction>.

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2142.transparentmethodsshouldnotbeprotectedwithlinkdemands/cs/ca2142 -transparentmethodsshouldnotbeprotectedwithlinkdemands.cs#1)]

 No suprima las advertencias de esta regla.




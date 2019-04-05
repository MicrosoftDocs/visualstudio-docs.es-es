---
title: 'CA2135: Los ensamblados de nivel 2 no deben contener LinkDemands | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cd4b1cb9d69e916a3d5cd547b3ff3714a20a665f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58997386"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: Los ensamblados de nivel 2 no deben contener LinkDemands
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|Identificador de comprobación|CA2135|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Una clase o miembro de clase que está usando un <xref:System.Security.Permissions.SecurityAction> en una aplicación que está utilizando seguridad de nivel 2.

## <a name="rule-description"></a>Descripción de la regla
 LinkDemands está desusado en el conjunto de reglas de seguridad de nivel 2. En lugar de utilizar LinkDemands para exigir la seguridad en tiempo de compilación just-in-time (JIT), marque los métodos, tipos y campos con el <xref:System.Security.SecurityCriticalAttribute> atributo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el <xref:System.Security.Permissions.SecurityAction> y marcar el tipo o miembro con el <xref:System.Security.SecurityCriticalAttribute> atributo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, la <xref:System.Security.Permissions.SecurityAction> debe quitarse y el método marcado con el <xref:System.Security.SecurityCriticalAttribute> atributo.

 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2135.securityrulesetlevel2methodsshouldnotbeprotectedwithlinkdemands/cs/ca2135.cs#1)]

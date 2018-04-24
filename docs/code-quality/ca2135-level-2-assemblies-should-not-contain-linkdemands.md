---
title: 'CA2135: Los ensamblados de nivel 2 no deben contener LinkDemands'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ab929509bca303379eee59e8741f32477fe32f30
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: Los ensamblados de nivel 2 no deben contener LinkDemands
|||
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|Identificador de comprobación|CA2135|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Una clase o miembro de clase está usando un <xref:System.Security.Permissions.SecurityAction> en una aplicación que usa la seguridad de nivel 2.

## <a name="rule-description"></a>Descripción de la regla
 LinkDemands está desusado en el conjunto de reglas de seguridad de nivel 2. En lugar de utilizar LinkDemands para exigir la seguridad en tiempo de compilación just-in-time (JIT), marque los métodos, tipos y campos con el <xref:System.Security.SecurityCriticalAttribute> atributo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el <xref:System.Security.Permissions.SecurityAction> y marque el tipo o miembro con el <xref:System.Security.SecurityCriticalAttribute> atributo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, la <xref:System.Security.Permissions.SecurityAction> debe quitarse y el método se marca con el <xref:System.Security.SecurityCriticalAttribute> atributo.

 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]
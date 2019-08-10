---
title: 'CA2135: Los ensamblados de nivel 2 no deben contener LinkDemands'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d466a508eade835563627a829f937416a24972a0
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920646"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: Los ensamblados de nivel 2 no deben contener LinkDemands

|||
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|Identificador de comprobación|CA2135|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un miembro de clase o clase está usando <xref:System.Security.Permissions.SecurityAction> en una aplicación que usa la seguridad de nivel 2.

## <a name="rule-description"></a>Descripción de la regla
LinkDemands está desusado en el conjunto de reglas de seguridad de nivel 2. En lugar de utilizar LinkDemands para exigir la seguridad en el momento de la compilación Just-in-Time (JIT), marque los métodos, tipos <xref:System.Security.SecurityCriticalAttribute> y campos con el atributo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, quite <xref:System.Security.Permissions.SecurityAction> el y marque el tipo o miembro con <xref:System.Security.SecurityCriticalAttribute> el atributo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente, <xref:System.Security.Permissions.SecurityAction> se debe quitar y el método marcado con el <xref:System.Security.SecurityCriticalAttribute> atributo.

[!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]
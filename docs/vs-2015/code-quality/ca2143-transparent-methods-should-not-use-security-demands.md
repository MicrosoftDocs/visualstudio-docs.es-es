---
title: 'CA2143: los métodos transparentes no deben usar demandas de seguridad | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ca8f049da83b99da7d36ebf74e756dd95f738d64
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546476"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: Los métodos transparentes no deben usar peticiones de seguridad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|Identificador de comprobación|CA2143|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un tipo o método tranparent se marca mediante declaración con una <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` petición o el método llama al <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> método.

## <a name="rule-description"></a>Descripción de la regla
 El código transparente en seguridad no debería ser responsable de comprobar la seguridad de una operación y, por consiguiente, no debería exigir permisos. El código transparente en seguridad debería utilizar peticiones completas para tomar decisiones de seguridad y el código crítico para la seguridad no debió confiar en el código transparente al realizar la petición completa. Cualquier código que realice comprobaciones de seguridad, como las demandas de seguridad, debe ser crítico para la seguridad en su lugar.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 En general, para corregir una infracción de esta regla, marque el método con el <xref:System.Security.SecuritySafeCriticalAttribute> atributo. También puede quitar la demanda.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 Los archivos de reglas en el código siguiente porque un método transparente realiza una petición de seguridad declarativa.

 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2143.transparentmethodsshouldnotdemand/cs/ca2143 - transparentmethodsshouldnotdemand.cs#1)]

## <a name="see-also"></a>Consulte también
 [CA2142: El código transparente no debe protegerse con LinkDemands](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)

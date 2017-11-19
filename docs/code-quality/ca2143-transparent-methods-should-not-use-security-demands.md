---
title: "CA2143: Los métodos transparentes no deben usar peticiones de seguridad | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 22adac09d7890f9d15e0bf50f46235f4b48d73dd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: Los métodos transparentes no deben usar peticiones de seguridad
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotDemand|  
|Identificador de comprobación|CA2143|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo o método transparente se marca mediante declaración con un <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` petición o las llamadas al método el <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> método.  
  
## <a name="rule-description"></a>Descripción de la regla  
 El código transparente en seguridad no debería ser responsable de comprobar la seguridad de una operación y, por consiguiente, no debería exigir permisos. El código transparente en seguridad debería utilizar peticiones completas para tomar decisiones de seguridad y el código crítico para la seguridad no debió confiar en el código transparente al realizar la petición completa. Cualquier código que realice comprobaciones de seguridad, como las peticiones de seguridad, debe ser crítico para la seguridad en su lugar.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 En general, para corregir una infracción de esta regla, marque el método con el <xref:System.Security.SecuritySafeCriticalAttribute> atributo. También puede quitar la demanda.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 La regla se desencadena en el código siguiente porque un método transparente hace una demanda de seguridad declarativa.  
  
 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]  
  
## <a name="see-also"></a>Vea también  
 [CA2142: El código transparente no debe protegerse con LinkDemands](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)
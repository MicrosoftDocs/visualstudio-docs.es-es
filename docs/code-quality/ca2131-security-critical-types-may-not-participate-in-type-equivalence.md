---
title: "CA2131: Los tipos críticos de seguridad no pueden participar en la equivalencia de tipos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2b1ba8aa4584d0d0505c7916d05e7c9bd6f446da
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131: Los tipos críticos para la seguridad no pueden participar en la equivalencia de tipos
|||  
|-|-|  
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|  
|Identificador de comprobación|CA2131|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo participa en la equivalencia de tipos y el tipo propio o un miembro o campo del tipo, se marca con el <xref:System.Security.SecurityCriticalAttribute> atributo.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Esta regla se produce en todos los tipos críticos o en los tipos que contienen métodos o campos críticos que participan en la equivalencia de tipos. Cuando CLR detecta esta clase de tipo, se produce un error de carga con una <xref:System.TypeLoadException> en tiempo de ejecución. Normalmente, esta regla solo se desencadena cuando los usuarios implementan la equivalencia de tipos manualmente en lugar de confiar en tlbimp y los compiladores para hacer la equivalencia de tipos.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el atributo SecurityCritical.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 Los ejemplos siguientes muestran una interfaz, un método y un campo que hará que esta regla se desencadena.  
  
 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]  
  
## <a name="see-also"></a>Vea también  
 [Código transparente en seguridad, nivel 2](/dotnet/framework/misc/security-transparent-code-level-2)
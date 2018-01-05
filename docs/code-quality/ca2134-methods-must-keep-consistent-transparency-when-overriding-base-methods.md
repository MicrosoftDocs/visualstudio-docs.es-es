---
title: "CA2134: Los métodos deben mantener una transparencia coherente cuando reemplazan métodos base | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 62438b49d91f680ae360f1d32f7cfe3b0efa2b75
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: Los métodos deben mantener una transparencia coherente cuando reemplazan métodos base
|||  
|-|-|  
|TypeName|MethodsMustOverrideWithConsistentTransparency|  
|Identificador de comprobación|CA2134|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Esta regla se desencadena cuando un método marcado con el <xref:System.Security.SecurityCriticalAttribute> invalida un método que es transparente o está marcado con el <xref:System.Security.SecuritySafeCriticalAttribute>. La regla también se desencadena cuando un método que es transparente o está marcado con el <xref:System.Security.SecuritySafeCriticalAttribute> invalida un método que se marca con un <xref:System.Security.SecurityCriticalAttribute>.  
  
 Se aplica la regla al invalidar un método virtual o implementar una interfaz.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Esta regla se desencadena en los intentos de cambiar la accesibilidad de seguridad de un método más arriba de la cadena de herencia. Por ejemplo, si un método virtual en una clase base es transparente o crítico para la seguridad, la clase derivada debe invalidarlo con un método transparente o crítico para la seguridad. Por el contrario, si el virtual es crítico para la seguridad, la clase derivada debe invalidarlo con un método crítico de seguridad. La misma regla se aplica al implementar métodos de interfaz.  
  
 Las reglas de transparencia se aplican cuando el código es JIT compilado en lugar de en tiempo de ejecución, por lo que el cálculo de transparencia no tiene información de tipo dinámico. Por lo tanto, el resultado del cálculo de transparencia debe poder determinar únicamente a partir de los tipos estáticos que se compila con JIT, sin tener en cuenta el tipo dinámico.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie la transparencia del método que se reemplace un método virtual o implementar una interfaz para que coincida con la transparencia de la memoria virtual o el método de interfaz.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla. Las infracciones de esta regla dará como resultado un tiempo de ejecución <xref:System.TypeLoadException> para los ensamblados que use la transparencia de nivel 2.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="code"></a>Código  
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods_1.cs)]  
  
## <a name="see-also"></a>Vea también  
 [Código transparente en seguridad, nivel 2](/dotnet/framework/misc/security-transparent-code-level-2)
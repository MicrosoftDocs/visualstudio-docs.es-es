---
title: "CA2134: Los m&#233;todos deben mantener una transparencia coherente cuando reemplazan m&#233;todos base | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2134"
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2134: Los m&#233;todos deben mantener una transparencia coherente cuando reemplazan m&#233;todos base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MethodsMustOverrideWithConsistentTransparency|  
|Identificador de comprobación|CA2134|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Esta regla también se desencadena cuando un método marcado con <xref:System.Security.SecurityCriticalAttribute> invalida un método que es transparente o está marcado con <xref:System.Security.SecuritySafeCriticalAttribute>.  La regla también se desencadena cuando un método que es transparente o está marcado con <xref:System.Security.SecuritySafeCriticalAttribute> invalida un método que está marcado con <xref:System.Security.SecurityCriticalAttribute>.  
  
 Se aplica la regla al invalidar un método virtual o implementar una interfaz.  
  
## Descripción de la regla  
 Esta regla se desencadena en los intentos de cambiar la accesibilidad de seguridad de un método más arriba de la cadena de herencia.  Por ejemplo, si un método virtual de una clase base es transparente o crítico para la seguridad, la clase derivada debe invalidarlo con un método transparente o crítico para la seguridad.  A la inversa, si es el método virtual es crítico para la seguridad, la clase derivada debe invalidarlo con un método crítico para la seguridad.  La misma regla se aplica al implementar métodos de interfaz.  
  
 Las reglas de transparencia se exigen cuando el código es compilado JIT en lugar de en tiempo de ejecución, para que el cálculo de la transparencia no tenga información del tipo dinámico.  Por consiguiente, el resultado del cálculo de la transparencia se debe poder definir solamente a partir de los tipos estáticos a los que se aplica la compilación JIT, sin tener en cuenta el tipo dinámico.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie la transparencia del método que está invalidando un método virtual o está implementando una interfaz para que coincida con la transparencia del método virtual o del método de interfaz.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  Las infracciones de esta regla producirán una <xref:System.TypeLoadException> en tiempo de ejecución para los ensamblados que utilizan la transparencia de nivel 2.  
  
## Ejemplos  
  
### Código  
 [!code-cs[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods_1.cs)]  
  
## Vea también  
 [Security\-Transparent Code, Level 2](../Topic/Security-Transparent%20Code,%20Level%202.md)
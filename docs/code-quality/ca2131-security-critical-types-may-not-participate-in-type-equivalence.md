---
title: "CA2131: Los tipos cr&#237;ticos para la seguridad no pueden participar en la equivalencia de tipos | Microsoft Docs"
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
  - "CA2131"
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2131: Los tipos cr&#237;ticos para la seguridad no pueden participar en la equivalencia de tipos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|  
|Identificador de comprobación|CA2131|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo participa en la equivalencia de tipos y, el propio tipo, o un miembro o campo del tipo, está marcado con el atributo <xref:System.Security.SecurityCriticalAttribute>.  
  
## Descripción de la regla  
 Esta regla se produce en todos los tipos críticos o en los tipos que contienen métodos o campos críticos que participan en la equivalencia de tipos.  Cuando CLR detecta esta clase de tipo, no lo carga con una <xref:System.TypeLoadException> en tiempo de ejecución.  Normalmente, esta regla solo se desencadena cuando los usuarios implementan la equivalencia de tipos manualmente en lugar de confiar en tlbimp y los compiladores para hacer la equivalencia de tipos.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el atributo SecurityCritical.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 En los ejemplos siguientes se muestra una interfaz, un método y un campo que harán que se desencadene esta regla.  
  
 [!code-cs[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]  
  
## Vea también  
 [Security\-Transparent Code, Level 2](../Topic/Security-Transparent%20Code,%20Level%202.md)
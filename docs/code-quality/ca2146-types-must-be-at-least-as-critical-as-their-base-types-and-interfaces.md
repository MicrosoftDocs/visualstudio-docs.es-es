---
title: "CA2146: Los tipos deben ser al menos tan cr&#237;ticos para la seguridad como sus interfaces y tipos base | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2146"
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2146: Los tipos deben ser al menos tan cr&#237;ticos para la seguridad como sus interfaces y tipos base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|  
|Identificador de comprobación|CA2146|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo transparente se deriva de un tipo que está marcado con <xref:System.Security.SecuritySafeCriticalAttribute> o <xref:System.Security.SecurityCriticalAttribute>, o de un tipo que está marcado con el atributo <xref:System.Security.SecuritySafeCriticalAttribute> se deriva de un tipo que está marcado con el atributo <xref:System.Security.SecurityCriticalAttribute>.  
  
## Descripción de la regla  
 Esta regla se desencadena cuando un tipo derivado tiene un atributo de transparencia de seguridad que no es tan crítico como su tipo base o interfaz implementada.  Solo los tipos críticos pueden derivar de los tipos base críticos o implementar interfaces críticas, y solo los tipos críticos o críticos para la seguridad pueden derivar de tipos base críticos para la seguridad o implementar interfaces críticas para la seguridad.  Las infracciones de esta regla en una transparencia de nivel 2 producirán una <xref:System.TypeLoadException> para el tipo derivado.  
  
## Cómo corregir infracciones  
 Para corregir esta infracción, marque el tipo derivado o que implementa con un atributo de transparencia que sea por lo menos tan crítico como el tipo base o la interfaz.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 [!code-cs[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../code-quality/codesnippet/CSharp/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces_1.cs)]
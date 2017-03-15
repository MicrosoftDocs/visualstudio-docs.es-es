---
title: "CA2140: El c&#243;digo transparente no debe hacer referencia a elementos cr&#237;ticos para la seguridad | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2129"
  - "SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode"
  - "CA2140"
helpviewer_keywords: 
  - "CA2129"
  - "CA2140"
  - "SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode"
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA2140: El c&#243;digo transparente no debe hacer referencia a elementos cr&#237;ticos para la seguridad
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|  
|Identificador de comprobación|CA2140|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método transparente:  
  
-   controla un tipo de excepción de seguridad crítico para la seguridad  
  
-   tiene un parámetro que está marcado como un tipo crítico para la seguridad  
  
-   tiene un parámetro genérico con restricciones críticas para la seguridad  
  
-   tiene una variable local de un tipo crítico para la seguridad  
  
-   hace referencia a un tipo que está marcado como crítico para la seguridad  
  
-   llama a un método que está marcado como crítico para la seguridad  
  
-   hace referencia a un campo que está marcado como crítico para la seguridad  
  
-   devuelve un tipo que está marcado como crítico para la seguridad  
  
## Descripción de la regla  
 Un elemento de código que se marca con el atributo <xref:System.Security.SecurityCriticalAttribute> es crítico para la seguridad.  Un método transparente no puede utilizar un elemento crítico para la seguridad.  Si un tipo transparente intenta usar un tipo crítico para la seguridad, se genera una <xref:System.TypeAccessException>, <xref:System.MethodAccessException> o <xref:System.FieldAccessException>.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, haga algo de lo siguiente:  
  
-   Marque el elemento de código que usa el código crítico para la seguridad con el atributo <xref:System.Security.SecurityCriticalAttribute>  
  
     – O bien –  
  
-   Quite el atributo <xref:System.Security.SecurityCriticalAttribute> de los elementos de código marcados como críticos para la seguridad y márquelos con el atributo <xref:System.Security.SecurityTransparentAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute>.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 En los ejemplos siguientes, un método transparente intenta hacer referencia a una colección genérica crítica para la seguridad, un campo crítico para la seguridad y un método crítico para la seguridad.  
  
 [!code-cs[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]  
  
## Vea también  
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityCriticalAttribute>   
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityTreatAsSafeAttribute>   
 <xref:System.Security?displayProperty=fullName>
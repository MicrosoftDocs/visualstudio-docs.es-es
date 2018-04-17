---
title: 'CA2140: El código transparente no debe hacer referencia a elementos críticos para la seguridad | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2129
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2140
helpviewer_keywords:
- CA2140
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2129
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 59fe9c1e88419a9bc0a5f0846e1857931919c213
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: El código transparente no debe hacer referencia a elementos críticos para la seguridad
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|  
|Identificador de comprobación|CA2140|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un método transparente:  
  
-   administre un tipo de excepción de seguridad críticas de seguridad  
  
-   tiene un parámetro que está marcado como un tipo crítico de seguridad  
  
-   tiene un parámetro genérico con un restricciones críticas para la seguridad  
  
-   tiene una variable local de un tipo crítico de seguridad  
  
-   hace referencia a un tipo que está marcado como seguridad crítico  
  
-   llama a un método que está marcado como seguridad crítico  
  
-   hace referencia a un campo que está marcado como seguridad crítico  
  
-   Devuelve un tipo que está marcado como seguridad crítico  
  
## <a name="rule-description"></a>Descripción de la regla  
 Un elemento de código que se marca con el <xref:System.Security.SecurityCriticalAttribute> atributo es crítico para la seguridad. Un método transparente no puede utilizar un elemento crítico para la seguridad. Si un tipo transparente intenta usar un tipo crítico de seguridad para un <xref:System.TypeAccessException>, <xref:System.MethodAccessException> , o <xref:System.FieldAccessException> se genera.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, realice una de las siguientes acciones:  
  
-   Marcar el elemento de código que usa el código crítico de seguridad con el <xref:System.Security.SecurityCriticalAttribute> atributo  
  
     \- o -  
  
-   Quitar el <xref:System.Security.SecurityCriticalAttribute> atributo desde los elementos de código que están marcados como seguridad crítica y márquelos con el <xref:System.Security.SecuritySafeCriticalAttribute> o <xref:System.Security.SecurityTransparentAttribute> atributo.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 En los ejemplos siguientes, un método transparente intenta hacer referencia a una colección genérica de seguridad críticas, un campo crítico de seguridad y un método crítico de seguridad.  
  
 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityCriticalAttribute>   
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityTreatAsSafeAttribute>   
 <xref:System.Security?displayProperty=fullName>
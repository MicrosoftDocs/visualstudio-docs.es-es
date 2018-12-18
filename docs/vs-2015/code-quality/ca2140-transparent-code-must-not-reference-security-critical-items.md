---
title: 'CA2140: El código transparente no debe hacer referencia a elementos críticos para la seguridad | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2129
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2140
helpviewer_keywords:
- CA2140
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2129
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fb6c01fc281384aec28ae46dbb1466686626df8b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892121"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: El código transparente no debe hacer referencia a elementos críticos para la seguridad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|
|Identificador de comprobación|CA2140|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método transparente:

-   controla un tipo de excepción de seguridad críticas de seguridad

-   tiene un parámetro que está marcado como un tipo crítico de seguridad

-   tiene un parámetro genérico con restricciones de seguridad de crítico

-   tiene una variable local de un tipo crítico de seguridad

-   hace referencia a un tipo que está marcado como de seguridad crítico

-   llama a un método que está marcado como de seguridad crítico

-   hace referencia a un campo que está marcado como de seguridad crítico

-   Devuelve un tipo que está marcado como de seguridad crítico

## <a name="rule-description"></a>Descripción de la regla
 Un elemento de código que está marcado con el <xref:System.Security.SecurityCriticalAttribute> atributo es crítico para la seguridad. Un método transparente no puede utilizar un elemento crítico para la seguridad. Si un tipo transparente intenta usar un tipo crítico de seguridad un <xref:System.TypeAccessException>, <xref:System.MethodAccessException> , o <xref:System.FieldAccessException> se genera.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, realice una de las siguientes acciones:

-   Marcar el elemento de código que usa el código crítico de seguridad con el <xref:System.Security.SecurityCriticalAttribute> atributo

     \- o -

-   Quitar el <xref:System.Security.SecurityCriticalAttribute> atributo de los elementos de código que se marcan como seguridad crítica y márquelos con el <xref:System.Security.SecuritySafeCriticalAttribute> o <xref:System.Security.SecurityTransparentAttribute> atributo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En los ejemplos siguientes, un método transparente intenta hacer referencia a una colección genérica de seguridad críticas, un campo crítico de seguridad y un método crítico de seguridad.

 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2140.transparentmethodsmustnotreferencecriticalcode/cs/ca2140 - transparentmethodsmustnotreferencecriticalcode.cs#1)]

## <a name="see-also"></a>Vea también
 <xref:System.Security.SecurityTransparentAttribute> <xref:System.Security.SecurityCriticalAttribute>
 <xref:System.Security.SecurityTransparentAttribute>
 <xref:System.Security.SecurityTreatAsSafeAttribute>
 <xref:System.Security?displayProperty=fullName>




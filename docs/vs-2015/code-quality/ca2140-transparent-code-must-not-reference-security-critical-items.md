---
title: 'CA2140: el código transparente no debe hacer referencia a elementos críticos para la seguridad | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5c3e624e4210e59406fd1d5955cd37c2e83ed79a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602864"
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

- controla un tipo de excepción de seguridad crítica de seguridad

- tiene un parámetro que está marcado como tipo crítico para la seguridad

- tiene un parámetro genérico con restricciones críticas para la seguridad

- tiene una variable local de un tipo crítico para la seguridad

- hace referencia a un tipo marcado como crítico para la seguridad

- llama a un método marcado como crítico para la seguridad

- hace referencia a un campo marcado como crítico para la seguridad

- Devuelve un tipo que está marcado como crítico para la seguridad.

## <a name="rule-description"></a>Descripción de la regla
 Un elemento de código que se marca con el atributo <xref:System.Security.SecurityCriticalAttribute> es crítico para la seguridad. Un método transparente no puede utilizar un elemento crítico para la seguridad. Si un tipo transparente intenta utilizar un tipo crítico para la seguridad, se genera un <xref:System.TypeAccessException>, <xref:System.MethodAccessException> o <xref:System.FieldAccessException>.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, realice una de las siguientes acciones:

- Marque el elemento de código que usa el código crítico para la seguridad con el atributo <xref:System.Security.SecurityCriticalAttribute>

     \- o -

- Quite el atributo <xref:System.Security.SecurityCriticalAttribute> de los elementos de código que estén marcados como críticos para la seguridad y, en su lugar, márquelos con el atributo <xref:System.Security.SecuritySafeCriticalAttribute> o <xref:System.Security.SecurityTransparentAttribute>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En los ejemplos siguientes, un método transparente intenta hacer referencia a una colección genérica crítica de seguridad, un campo crítico para la seguridad y un método crítico para la seguridad.

 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2140.transparentmethodsmustnotreferencecriticalcode/cs/ca2140 - transparentmethodsmustnotreferencecriticalcode.cs#1)]

## <a name="see-also"></a>Vea también
 <xref:System.Security.SecurityTransparentAttribute> <xref:System.Security.SecurityCriticalAttribute>
 <xref:System.Security.SecurityTransparentAttribute>
 <xref:System.Security.SecurityTreatAsSafeAttribute>
 <xref:System.Security?displayProperty=fullName>

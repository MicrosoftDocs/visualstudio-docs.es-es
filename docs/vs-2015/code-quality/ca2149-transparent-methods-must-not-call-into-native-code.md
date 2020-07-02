---
title: 'CA2149: los métodos transparentes no deben llamar a código nativo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5c1e254ae7912efbb6773155ed834e54a1db1832
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546333"
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149: Los métodos transparentes no deben llamar a código nativo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|TransparentMethodsMustNotCallNativeCode|
|Identificador de comprobación|CA2149|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un método llama a una función nativa a través de un código auxiliar de método como P/Invoke.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla se desencadena en cualquier método transparente que llame directamente a código nativo, por ejemplo, a través de P/Invoke. Las infracciones de esta regla conducen a un <xref:System.MethodAccessException> en el modelo de transparencia de nivel 2 y a una demanda completa para <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> en el modelo de transparencia de nivel 1.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, marque el método que llama al código nativo con <xref:System.Security.SecurityCriticalAttribute> el <xref:System.Security.SecuritySafeCriticalAttribute> atributo o.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 [!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2149.transparentmethodsmustnotcallnativecode/cs/ca2149 - transparentmethodsmustnotcallnativecode.cs#1)]

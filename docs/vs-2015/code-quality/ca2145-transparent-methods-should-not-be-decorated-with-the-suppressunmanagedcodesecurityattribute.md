---
title: 'CA2145: Los métodos transparentes no deben ser representativos con el atributo SuppressUnmanagedCodeSecurityAttribute | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b6a7c1b5684181098ef0bec1cde430f401ba1136
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142626"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: Los métodos transparentes no deben ser representativos con el atributo SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|Identificador de comprobación|CA2145|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un método transparente, un método marcado con el <xref:System.Security.SecuritySafeCriticalAttribute> método o un tipo que contiene un método está marcado con el <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo.

## <a name="rule-description"></a>Descripción de la regla
 Los métodos representativos con el <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo tienen una LinkDemand implícita colocada en cualquier método que lo llama. Esta LinkDemand requiere que el código de llamada sea crítico para la seguridad. Marcar el método que utiliza SuppressUnmanagedCodeSecurity con el <xref:System.Security.SecurityCriticalAttribute> atributo hace que este requisito más obvio para los llamadores del método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, marque el método o tipo con el <xref:System.Security.SecurityCriticalAttribute> atributo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2145.transparentmethodsshouldnotusesuppressunmanagedcodesecurity/cs/ca2145.cs#1)]

### <a name="comments"></a>Comentarios

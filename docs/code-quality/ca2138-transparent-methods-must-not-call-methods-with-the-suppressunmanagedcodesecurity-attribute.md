---
title: "CA2138: Los métodos transparentes no deben llamar a métodos con el atributo SuppressUnmanagedCodeSecurity | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cf17c69673649ac1f3af64bafcb718e8c84eb213
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: Los métodos transparentes no deben llamar a métodos con el atributo SuppressUnmanagedCodeSecurity
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|  
|Identificador de comprobación|CA2138|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un método transparente en seguridad llama a un método que se marca con el <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Esta regla se desencadena en cualquier método transparente que llame directamente a código nativo, por ejemplo, mediante el uso de una a través de P/Invoke (invocación de plataforma) llamar. Métodos de interoperabilidad COM y P/Invoke que están marcados con el <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo resultado en un LinkDemand se realiza en el método de llamada. Como código transparente en seguridad no puede satisfacer LinkDemands, el código no puede llamar a métodos que se marcan con el atributo SuppressUnmanagedCodeSecurity, o los métodos de clase que se marca con el atributo SuppressUnmanagedCodeSecurity. Se producirá un error en el método o la demanda se convertirá en una demanda completa.  
  
 Las infracciones de esta regla conducen a una <xref:System.MethodAccessException> en el modelo de transparencia de seguridad de nivel 2 y una demanda completa para <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> en el modelo de transparencia de nivel 1.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> de atributo y marque el método con el <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> atributo.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]
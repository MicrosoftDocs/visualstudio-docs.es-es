---
title: 'CA2138: Los métodos transparentes no deben llamar a métodos con el atributo SuppressUnmanagedCodeSecurity | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: dd12cf43425c863b72c7a77b8ccd8884c0ad7d2d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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
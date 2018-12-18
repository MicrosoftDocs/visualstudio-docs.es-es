---
title: 'CA2138: Los métodos transparentes no deben llamar a métodos con el atributo SuppressUnmanagedCodeSecurity | Microsoft Docs'
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
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7e98fdc2a8807dcca3c730413ac554a8191168e3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922018"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: Los métodos transparentes no deben llamar a métodos con el atributo SuppressUnmanagedCodeSecurity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|Identificador de comprobación|CA2138|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método transparente en seguridad llama a un método marcado con el <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla se desencadena en cualquier método transparente que llame directamente al código nativo, por ejemplo, mediante el uso de una a través de P/Invoke (invocación de plataforma) llamar. Métodos de interoperabilidad COM y P/Invoke que están marcados con el <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo resultado en un LinkDemand que se realiza en el método de llamada. Como código transparente en seguridad no puede satisfacer LinkDemands, el código también no puede llamar a métodos marcados con el atributo SuppressUnmanagedCodeSecurity o métodos de clase que está marcado con el atributo SuppressUnmanagedCodeSecurity. Se producirá un error en el método o la demanda se convertirá en una demanda completa.

 Las infracciones de esta regla una <xref:System.MethodAccessException> en el modelo de transparencia de seguridad de nivel 2 y una demanda completa de <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> en el modelo de transparencia de nivel 1.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> de atributo y marque el método con el <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> atributo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2138.transparentmethodsmustnotcallsuppressunmanagedcodesecuritymethods/cs/ca2138.cs#1)]




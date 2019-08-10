---
title: 'CA2138: Los métodos transparentes no deben llamar a métodos con el atributo SuppressUnmanagedCodeSecurity'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 316aef3b0f1f715857fde8eaf2a6e74b1a49e40f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920572"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: Los métodos transparentes no deben llamar a métodos con el atributo SuppressUnmanagedCodeSecurity

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|Identificador de comprobación|CA2138|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un método transparente en seguridad llama a un método marcado con el <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo.

## <a name="rule-description"></a>Descripción de la regla
Esta regla se desencadena en cualquier método transparente que llame directamente a código nativo, por ejemplo, mediante una llamada P/Invoke (invocación de plataforma). Los métodos de interoperabilidad P/Invoke y com marcados con el <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo dan como resultado una LinkDemand que se realiza en el método de llamada. Dado que el código transparente en seguridad no puede satisfacer LinkDemands, el código tampoco puede llamar a los métodos marcados con el atributo SuppressUnmanagedCodeSecurity o a los métodos de clase marcados con el atributo SuppressUnmanagedCodeSecurity. Se producirá un error en el método o la demanda se convertirá a una demanda completa.

Las infracciones de esta regla conducen <xref:System.MethodAccessException> a un en el modelo de transparencia de seguridad de nivel 2 y <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> una demanda completa para en el modelo de transparencia de nivel 1.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, quite <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> el atributo y marque el método con <xref:System.Security.SecurityCriticalAttribute> el <xref:System.Security.SecuritySafeCriticalAttribute> atributo o.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
[!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]
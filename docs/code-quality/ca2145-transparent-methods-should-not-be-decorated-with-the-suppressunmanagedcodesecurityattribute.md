---
title: 'CA2145: Los métodos transparentes no deben ser representativos con el atributo SuppressUnmanagedCodeSecurityAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c3d2fe5c2c4e75376f88af7679f6838561848c2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53949357"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: Los métodos transparentes no deben ser representativos con el atributo SuppressUnmanagedCodeSecurityAttribute

|||
|-|-|
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|Identificador de comprobación|CA2145|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

Un método transparente, un método marcado con el <xref:System.Security.SecuritySafeCriticalAttribute> método o un tipo que contiene un método está marcado con el <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo.

## <a name="rule-description"></a>Descripción de la regla

Los métodos representativos con el <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo tienen una LinkDemand implícita colocada en cualquier método que lo llama. Esta LinkDemand requiere que el código de llamada sea crítico para la seguridad. Marcar el método que utiliza SuppressUnmanagedCodeSecurity con el <xref:System.Security.SecurityCriticalAttribute> atributo hace que este requisito más obvio para los llamadores del método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, marque el método o tipo con el <xref:System.Security.SecurityCriticalAttribute> atributo.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla.

### <a name="code"></a>Código

[!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]
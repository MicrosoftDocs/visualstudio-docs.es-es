---
title: 'CA2149: Los métodos transparentes no deben llamar a código nativo'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 725bf599d8d13d345767f5af4d38db619263c23d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920381"
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149: Los métodos transparentes no deben llamar a código nativo

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallNativeCode|
|Identificador de comprobación|CA2149|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un método llama a una función nativa a través de un código auxiliar de método como P/Invoke.

## <a name="rule-description"></a>Descripción de la regla
Esta regla se desencadena en cualquier método transparente que llame directamente a código nativo, por ejemplo, a través de P/Invoke. Las infracciones de esta regla conducen <xref:System.MethodAccessException> a un en el modelo de transparencia de nivel 2 y a <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> una demanda completa para en el modelo de transparencia de nivel 1.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, marque el método que llama al código nativo con <xref:System.Security.SecurityCriticalAttribute> el <xref:System.Security.SecuritySafeCriticalAttribute> atributo o.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
[!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../code-quality/codesnippet/CSharp/ca2149-transparent-methods-must-not-call-into-native-code_1.cs)]
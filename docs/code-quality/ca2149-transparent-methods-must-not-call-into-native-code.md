---
title: 'CA2149: Los métodos transparentes no deben llamar a código nativo'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: c14cfff80836ebaeb8b2d0dda2298f91e913083f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149: Los métodos transparentes no deben llamar a código nativo
|||
|-|-|
|TypeName|TransparentMethodsMustNotCallNativeCode|
|Identificador de comprobación|CA2149|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método llama a una función nativa a través de un código auxiliar del método como P/Invoke.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla se desencadena en cualquier método transparente que llame directamente a código nativo, por ejemplo, a través de P/Invoke. Las infracciones de esta regla conducen a una <xref:System.MethodAccessException> en el modelo de transparencia de nivel 2 y una demanda completa para <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> en el modelo de transparencia de nivel 1.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, marque el método que llama al código nativo con el <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> atributo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 [!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../code-quality/codesnippet/CSharp/ca2149-transparent-methods-must-not-call-into-native-code_1.cs)]
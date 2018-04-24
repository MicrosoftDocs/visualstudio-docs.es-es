---
title: 'CA2141: Los métodos transparentes no deben satisfacer LinkDemands'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a64e8acae7e7dd76107bc761a6b035f2963247fe
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141: Los métodos transparentes no deben satisfacer LinkDemands
|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|Identificador de comprobación|CA2141|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método transparente en seguridad llama a un método en un ensamblado que no está marcado con el <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) o un método transparente en seguridad satisface una <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` para un tipo o un método.

## <a name="rule-description"></a>Descripción de la regla
 Satisfacer una LinkDemand es una operación sensible de seguridad que puede producir involuntaria elevación de privilegios. Código transparente en seguridad no debe satisfacer LinkDemands, porque no está sujeto a los mismos requisitos de auditoría de seguridad que el código crítico para la seguridad. Los métodos transparentes en ensamblados de nivel 1 de conjunto de reglas de seguridad hará que todas las LinkDemands que satisfacen se conviertan peticiones completas en tiempo de ejecución, lo que puede provocar problemas de rendimiento. En los ensamblados de nivel 2 de conjunto de reglas de seguridad, métodos transparentes no se compilará en el compilador de just-in-time (JIT) si intentan satisfacer una LinkDemand.

 En los ensamblados que usan seguridad de nivel 2, los intentos de un método transparente en seguridad para satisfacer una LinkDemand o llamar a un método en un ensamblado no APTCA genera un <xref:System.MethodAccessException>; en ensamblados de nivel 1 LinkDemand se convierte en una demanda completa.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, marque el método que obtiene acceso con el <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> de atributo o quite LinkDemand del método de acceso.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En este ejemplo, un método transparente intenta llamar a un método que tiene una LinkDemand. Esta regla se activará en este código.

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]
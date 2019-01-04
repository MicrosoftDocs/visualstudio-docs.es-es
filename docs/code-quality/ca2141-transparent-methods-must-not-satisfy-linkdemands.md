---
title: 'CA2141: Los métodos transparentes no deben satisfacer LinkDemands'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3c92a66fc2f6fe70e8e9c4786bc6d856bd6f1694
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920516"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141: Los métodos transparentes no deben satisfacer LinkDemands

|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|Identificador de comprobación|CA2141|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método transparente en seguridad llama a un método en un ensamblado que no está marcado con el <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) o un método transparente en seguridad satisface un <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` para un tipo o un método.

## <a name="rule-description"></a>Descripción de la regla
 Que satisface un LinkDemand es una operación confidencial de seguridad que puede causar involuntaria elevación de privilegios. Código transparente en seguridad no debe satisfacer LinkDemands, porque no está sujeto a los mismos requisitos de auditoría de seguridad que el código crítico para la seguridad. Los métodos transparentes en ensamblados de nivel 1 del conjunto de reglas de seguridad hará que todas las LinkDemands que satisfacen a convertirse en peticiones completas en tiempo de ejecución, lo que puede causar problemas de rendimiento. En los ensamblados de nivel 2 de conjunto de reglas de seguridad, los métodos transparentes no se compilará en el compilador de just-in-time (JIT), si éstos intentan satisface un LinkDemand.

 En los ensamblados que utilizan la seguridad de nivel 2, los intentos de un método transparente en seguridad para satisfacer una LinkDemand o llamar a un método en un ensamblado APTCA no provoca una <xref:System.MethodAccessException>; en ensamblados de nivel 1 LinkDemand se convierte en una demanda completa.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, marque el método que obtiene acceso con el <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> de atributo o quite LinkDemand del método que se tiene acceso.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En este ejemplo, un método transparente intenta llamar a un método que tiene LinkDemand. Esta regla se activará en este código.

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]
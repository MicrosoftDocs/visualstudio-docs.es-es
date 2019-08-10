---
title: 'CA2141: Los métodos transparentes no deben satisfacer LinkDemands'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24723559988974c51798c3e099ff8c1d86a15db9
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920519"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141: Los métodos transparentes no deben satisfacer LinkDemands

|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|Identificador de comprobación|CA2141|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un método transparente en seguridad llama a un método de un ensamblado que no está <xref:System.Security.AllowPartiallyTrustedCallersAttribute> marcado con el atributo (APTCA) o un método transparente en seguridad <xref:System.Security.Permissions.SecurityAction> satisface un `.LinkDemand` para un tipo o un método.

## <a name="rule-description"></a>Descripción de la regla
Satisfacer una LinkDemand es una operación sensible a la seguridad que puede provocar una elevación involuntaria de privilegios. El código transparente en seguridad no debe cumplir LinkDemands, ya que no está sujeto a los mismos requisitos de auditoría de seguridad que el código crítico para la seguridad. Los métodos transparentes de los ensamblados de nivel 1 de conjunto de reglas de seguridad harán que todos los LinkDemands que cumplan se conviertan en demandas completas en tiempo de ejecución, lo que puede causar problemas de rendimiento. En los ensamblados de nivel 2 de conjunto de reglas de seguridad, los métodos transparentes no se compilarán en el compilador Just-in-Time (JIT) si intentan cumplir una LinkDemand.

En los ensamblados que usan la seguridad de nivel 2, los intentos por un método transparente en seguridad para satisfacer una LinkDemand o llamar a un método en <xref:System.MethodAccessException>un ensamblado no APTCA provocan una; en los ensamblados de nivel 1, LinkDemand se convierte en una demanda completa.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, marque el método de acceso con <xref:System.Security.SecurityCriticalAttribute> el <xref:System.Security.SecuritySafeCriticalAttribute> atributo o o quite LinkDemand del método al que se accede.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
En este ejemplo, un método transparente intenta llamar a un método que tiene LinkDemand. Esta regla se activará en este código.

[!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]
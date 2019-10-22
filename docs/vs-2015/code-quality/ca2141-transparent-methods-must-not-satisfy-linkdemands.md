---
title: 'CA2141: los métodos transparentes no deben cumplir LinkDemands | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5e8e88401a6fbe3ab7dc635dadee9215b049b2d5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602838"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141: Los métodos transparentes no deben satisfacer LinkDemands
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|Identificador de comprobación|CA2141|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método transparente en seguridad llama a un método de un ensamblado que no está marcado con el atributo <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) o un método transparente en seguridad satisface una `.LinkDemand` <xref:System.Security.Permissions.SecurityAction> para un tipo o un método.

## <a name="rule-description"></a>Descripción de la regla
 Satisfacer una LinkDemand es una operación sensible a la seguridad que puede provocar una elevación involuntaria de privilegios. El código transparente en seguridad no debe cumplir LinkDemands, ya que no está sujeto a los mismos requisitos de auditoría de seguridad que el código crítico para la seguridad. Los métodos transparentes de los ensamblados de nivel 1 de conjunto de reglas de seguridad harán que todos los LinkDemands que cumplan se conviertan en demandas completas en tiempo de ejecución, lo que puede causar problemas de rendimiento. En los ensamblados de nivel 2 de conjunto de reglas de seguridad, los métodos transparentes no se compilarán en el compilador Just-in-Time (JIT) si intentan cumplir una LinkDemand.

 En los ensamblados que USEE la seguridad de nivel 2, los intentos por un método transparente en seguridad para satisfacer una LinkDemand o llamar a un método en un ensamblado no APTCA generan un <xref:System.MethodAccessException>; en los ensamblados de nivel 1, LinkDemand se convierte en una demanda completa.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, marque el método de acceso con el <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> atributo, o quite LinkDemand del método al que se accede.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En este ejemplo, un método transparente intenta llamar a un método que tiene LinkDemand. Esta regla se activará en este código.

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2141.transparentmethodsmustnotsatisfylinkdemands/cs/ca2141 - transparentmethodsmustnotsatisfylinkdemands.cs#1)]

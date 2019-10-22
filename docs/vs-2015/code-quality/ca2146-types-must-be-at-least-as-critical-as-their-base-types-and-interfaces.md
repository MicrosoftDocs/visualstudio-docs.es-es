---
title: 'CA2146: los tipos deben ser al menos tan críticos como sus tipos base e interfaces | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ab621ade120a257508eddbf9527f674b5fda8748
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610184"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146: Los tipos deben ser al menos tan críticos para la seguridad como sus interfaces y tipos base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|Identificador de comprobación|CA2146|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo transparente se deriva de un tipo que está marcado con el <xref:System.Security.SecuritySafeCriticalAttribute> o el <xref:System.Security.SecurityCriticalAttribute>, o un tipo marcado con el atributo <xref:System.Security.SecuritySafeCriticalAttribute> se deriva de un tipo marcado con el atributo <xref:System.Security.SecurityCriticalAttribute>.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla se desencadena cuando un tipo derivado tiene un atributo de transparencia de seguridad que no es tan crítico como su tipo base o interfaz implementada. Solo los tipos críticos pueden derivar de los tipos base críticos o implementar interfaces críticas, y solo los tipos críticos o críticos para la seguridad pueden derivar de tipos base críticos para la seguridad o implementar interfaces críticas para la seguridad. Las infracciones de esta regla en la transparencia de nivel 2 dan como resultado un <xref:System.TypeLoadException> para el tipo derivado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir esta infracción, marque el tipo derivado o de implementación con un atributo de transparencia que sea al menos tan crítico como el tipo base o la interfaz.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes/cs/ca2146 - typesmustbeatleastascriticalasbasetypes.cs#1)]

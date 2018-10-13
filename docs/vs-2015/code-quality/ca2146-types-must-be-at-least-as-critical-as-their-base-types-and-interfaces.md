---
title: 'CA2146: Los tipos deben ser al menos tan críticos como sus tipos base e interfaces | Microsoft Docs'
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
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 68c429c3cb2ed3a9addb129fd3225efbf73607cc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207290"
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
 Un tipo transparente se deriva de un tipo que está marcado con el <xref:System.Security.SecuritySafeCriticalAttribute> o <xref:System.Security.SecurityCriticalAttribute>, o un tipo que está marcado con el <xref:System.Security.SecuritySafeCriticalAttribute> atributo se deriva de un tipo que está marcado con el <xref:System.Security.SecurityCriticalAttribute> atributo.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla se desencadena cuando un tipo derivado tiene un atributo de transparencia de seguridad que no es tan crítico como su tipo base o interfaz implementada. Solo los tipos críticos pueden derivar de los tipos base críticos o implementar interfaces críticas, y solo los tipos críticos o críticos para la seguridad pueden derivar de tipos base críticos para la seguridad o implementar interfaces críticas para la seguridad. Dar lugar a infracciones de esta regla de transparencia de nivel 2 en un <xref:System.TypeLoadException> para el tipo derivado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir esta infracción, marque el tipo derivado o implementación con un atributo de transparencia que sea al menos tan crítico como el tipo base o interfaz.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes/cs/ca2146 - typesmustbeatleastascriticalasbasetypes.cs#1)]




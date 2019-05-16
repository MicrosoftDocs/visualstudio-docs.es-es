---
title: 'CA2131: Los tipos críticos de seguridad no pueden participar en la equivalencia de tipos | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6fba07fbfd7f0c36681b7567ad01359df1be88f6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700532"
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131: Los tipos críticos para la seguridad no pueden participar en la equivalencia de tipos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|
|Identificador de comprobación|CA2131|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo participa en la equivalencia de tipos y un el propio tipo o un miembro o campo del tipo, se marca con el <xref:System.Security.SecurityCriticalAttribute> atributo.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla se produce en todos los tipos críticos o en los tipos que contienen métodos o campos críticos que participan en la equivalencia de tipos. Cuando CLR detecta este tipo, se produce un error de carga con una <xref:System.TypeLoadException> en tiempo de ejecución. Normalmente, esta regla solo se desencadena cuando los usuarios implementan la equivalencia de tipos manualmente en lugar de confiar en tlbimp y los compiladores para hacer la equivalencia de tipos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el atributo SecurityCritical.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 Los ejemplos siguientes muestran una interfaz, un método y un campo que hará que esta regla se active.

 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2131.criticaltypesmustnotparticipateintypeequivalence/cs/ca2131 - criticaltypesmustnotparticipateintypeequivalence.cs#1)]

## <a name="see-also"></a>Vea también
 [Código transparente en seguridad, nivel 2](https://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)

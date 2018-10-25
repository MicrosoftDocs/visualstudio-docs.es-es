---
title: 'CA1708: Los identificadores deben diferenciarse por algo más que el caso | Microsoft Docs'
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
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 91e35518fe274255727975d589a32a1b0342e320
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49901780"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|Identificador de comprobación|CA1708|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Los nombres de dos tipos, miembros, parámetros o los espacios de nombres completos son idénticos cuando se convierten a minúsculas.

## <a name="rule-description"></a>Descripción de la regla
 Los identificadores de los espacios de nombres, miembros y parámetros no puede distinguirse sólo por mayúsculas o minúsculas porque los lenguajes que tienen como destino el Common Language Runtime no necesitan distinguir entre mayúsculas y minúsculas. Por ejemplo, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] es un lenguaje ampliamente utilizado entre mayúsculas y minúsculas.

 Esta regla se desencadena en solo los miembros visibles públicamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Seleccione un nombre que sea único cuando se compara con otros identificadores en mayúsculas y minúsculas.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. La biblioteca no podría utilizarse en todos los idiomas disponibles en el [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

## <a name="example-of-a-violation"></a>Ejemplo de una infracción
 El ejemplo siguiente muestra una infracción de esta regla.

 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase/cs/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)




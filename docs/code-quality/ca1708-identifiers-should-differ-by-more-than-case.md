---
title: 'CA1708: Los identificadores se deben diferenciar en algo más que en el uso de mayúsculas y minúsculas'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4fd2ac35d5c6df5e1ffc3d49ea3089bb4ee3ea77
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53833250"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: Los identificadores se deben diferenciar en algo más que en el uso de mayúsculas y minúsculas

|||
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|Identificador de comprobación|CA1708|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Los nombres de dos tipos, miembros, parámetros o los espacios de nombres completos son idénticos cuando se convierten a minúsculas.

## <a name="rule-description"></a>Descripción de la regla
 Los identificadores de los espacios de nombres, miembros y parámetros no puede distinguirse sólo por mayúsculas o minúsculas porque los lenguajes que tienen como destino el Common Language Runtime no necesitan distinguir entre mayúsculas y minúsculas. Por ejemplo, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] es un lenguaje ampliamente utilizado entre mayúsculas y minúsculas.

 Esta regla se desencadena en solo los miembros visibles públicamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Seleccione un nombre que sea único cuando se compara con otros identificadores en mayúsculas y minúsculas.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla. La biblioteca no podría utilizarse en todos los idiomas disponibles en .NET Framework.

## <a name="example-of-a-violation"></a>Ejemplo de una infracción
 El ejemplo siguiente muestra una infracción de esta regla.

 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1709: Los identificadores deberían escribirse correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
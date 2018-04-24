---
title: 'CA2219: No producir excepciones en cláusulas de excepción'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f8b542c88c62230f60b11ba9927873d2593157c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: No producir excepciones en cláusulas de excepción
|||
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|Identificador de comprobación|CA2219|
|Categoría|Microsoft.Usage|
|Cambio problemático|No problemático, problemático|

## <a name="cause"></a>Motivo
 Se produce una excepción desde una `finally`, filtro o la cláusula fault.

## <a name="rule-description"></a>Descripción de la regla
 Cuando se produce una excepción en una cláusula de excepción, aumenta considerablemente la dificultad de depuración.

 Cuando se genera una excepción en un `finally` o la cláusula fault, la nueva excepción oculta la excepción activa, si está presente. Esto hace que el error original sea difícil de detectar y depurar.

 Cuando se produce una excepción en una cláusula de filtro, el tiempo de ejecución en modo silencioso detecta la excepción y hace que el filtro se evalúe como false. No hay ninguna manera de indicar la diferencia entre el filtro que se evalúa como false y una excepción que se inicia desde un filtro. Esto hace más difícil de detectar y depurar los errores en la lógica del filtro.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir esta infracción de esta regla, no produzca explícitamente una excepción desde una `finally`, filtro o la cláusula fault.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. No hay ningún escenario en el que una excepción producida en una cláusula de excepción proporcione alguna ventaja en el código en ejecución.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1065: No producir excepciones en ubicaciones inesperadas](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>Vea también
 [Advertencias de diseño](../code-quality/design-warnings.md)
---
title: 'CA2219: No producir excepciones en cláusulas de excepción'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 49baf6fe645df35949f47f2796197977d428427e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49885972"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: No producir excepciones en cláusulas de excepción

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|Identificador de comprobación|CA2219|
|Categoría|Microsoft.Usage|
|Cambio problemático|No problemático, problemático|

## <a name="cause"></a>Motivo
 Se produce una excepción desde un `finally`, filtro o cláusula fault.

## <a name="rule-description"></a>Descripción de la regla
 Cuando se produce una excepción en una cláusula de excepción, aumenta en gran medida la dificultad de depuración.

 Cuando se produce una excepción en un `finally` o cláusula fault, la nueva excepción oculta la excepción activa, si está presente. Esto hace que el error original sea difícil de detectar y depurar.

 Cuando se produce una excepción en una cláusula de filtro, el tiempo de ejecución en modo silencioso detecta la excepción y hace que el filtro se evalúe como false. No hay ninguna manera de indicar la diferencia entre el filtro que se evalúa como false y una excepción que se inicia desde un filtro. Esto dificulta la detección y depuración de errores en la lógica del filtro.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir esta infracción de esta regla, no explícitamente produzca una excepción desde un `finally`, filtro o cláusula fault.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima una advertencia para esta regla. No hay ningún escenario en el que una excepción en una cláusula de excepción proporcione una ventaja en el código en ejecución.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1065: No producir excepciones en ubicaciones inesperadas](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>Vea también
 [Advertencias de diseño](../code-quality/design-warnings.md)
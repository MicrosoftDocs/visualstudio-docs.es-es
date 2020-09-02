---
title: 'CA2219: no generar excepciones en cláusulas de excepción | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 960c74625a04b209dc9aa251256e994517a3a52f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538533"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: No producir excepciones en cláusulas de excepción
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|Identificador de comprobación|CA2219|
|Category|Microsoft. Usage|
|Cambio problemático|No problemático, problemático|

## <a name="cause"></a>Causa
 Se produce una excepción desde una `finally` cláusula, filtro o error.

## <a name="rule-description"></a>Descripción de la regla
 Cuando se genera una excepción en una cláusula de excepción, aumenta considerablemente la dificultad de la depuración.

 Cuando se produce una excepción en una `finally` cláusula de error o, la nueva excepción oculta la excepción activa, si está presente. Esto hace que el error original sea difícil de detectar y depurar.

 Cuando se genera una excepción en una cláusula de filtro, el tiempo de ejecución detecta la excepción de forma silenciosa y hace que el filtro se evalúe como false. No hay ninguna manera de indicar la diferencia entre el filtro que se evalúa como false y una excepción que se inicia desde un filtro. Esto hace que sea difícil detectar y depurar errores en la lógica del filtro.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir esta infracción de esta regla, no genere explícitamente una excepción a partir de una `finally` cláusula, filtro o error.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una advertencia para esta regla. No hay escenarios en los que una excepción generada en una cláusula de excepción proporciona una ventaja para el código de ejecución.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1065: No producir excepciones en ubicaciones inesperadas](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>Consulte también
 [Advertencias de diseño](../code-quality/design-warnings.md)

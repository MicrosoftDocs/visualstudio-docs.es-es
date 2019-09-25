---
title: 'CA1505: Evitar código que no se puede mantener'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3ba027ef2e663870d0af50bc6d2154133f7980c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234543"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: Evitar código que no se puede mantener

|||
|-|-|
|TypeName|AvoidUnmantainableCode|
|Identificador de comprobación|CA1505|
|Categoría|Microsoft. mantenibilidad|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Un tipo o método tiene un valor del índice de mantenimiento bajo.

## <a name="rule-description"></a>Descripción de la regla

El índice de mantenimiento se calcula con las siguientes métricas: líneas de código, volumen de programa y complejidad ciclomática. El volumen de programa es una medida de la dificultad de comprender un tipo o un método basado en el número de operadores y operandos del código. La complejidad ciclomática es una medida de la complejidad estructural del tipo o método. Puede obtener más información sobre las métricas de código a medida que se reduce [la complejidad y el mantenimiento del código administrado](../code-quality/code-metrics-values.md).

Un índice de mantenimiento bajo indica que un tipo o un método probablemente es difícil de mantener y sería un buen candidato para rediseñar.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir esta infracción, vuelva a diseñar el tipo o método e intente dividirlo en tipos o métodos más pequeños y más centrados.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Puede suprimir esta advertencia cuando el tipo o el método no se pueden dividir o se consideran mantenibles a pesar de su gran tamaño.

## <a name="see-also"></a>Vea también

- [Advertencias de mantenimiento](../code-quality/maintainability-warnings.md)
- [Medir la complejidad y el mantenimiento del código administrado](../code-quality/code-metrics-values.md)
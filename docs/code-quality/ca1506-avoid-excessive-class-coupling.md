---
title: 'CA1506: Evite el acoplamiento excesivo de clases'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d4c36d824fcfe698f8eb7a75b1111ccec03f4064
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2018
ms.locfileid: "53740304"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Evite el acoplamiento excesivo de clases

|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|Identificador de comprobación|CA1506|
|Categoría|Microsoft.Maintainability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo o método está emparejada con muchos otros tipos.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla mide el acoplamiento de clase contando el número de referencias de tipo únicas que contiene un tipo o método.

 Tipos y métodos que tienen un alto grado de acoplamiento de clases pueden ser difíciles de mantener. Es una buena práctica para tener tipos y métodos que exhiban acoplamiento bajo y una cohesión alta.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir esta infracción, intente volver a diseñar el tipo o método para reducir el número de tipos al que está acoplado.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Excluir esta advertencia cuando el tipo o método se sigue considerando fácil de mantener a pesar de su gran número de dependencias en otros tipos.

## <a name="see-also"></a>Vea también

- [Advertencias de mantenimiento](../code-quality/maintainability-warnings.md)
- [Medir la complejidad y el mantenimiento del código administrado](../code-quality/code-metrics-values.md)
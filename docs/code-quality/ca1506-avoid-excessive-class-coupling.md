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
ms.openlocfilehash: a613ecfd339399b161292a75f7fb2abeb972d986
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916682"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Evite el acoplamiento excesivo de clases
|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|Identificador de comprobación|CA1506|
|Categoría|Microsoft.Maintainability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo o método se acopla con muchos otros tipos.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla mide el acoplamiento de clase contando el número de referencias de tipo únicas que contiene un tipo o método.

 Tipos y métodos que tienen un alto grado de acoplamiento de clase pueden ser difíciles de mantener. Es una buena práctica para tener tipos y métodos que exhiban acoplamiento bajo y alto cohesión.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir esta infracción, intente volver a diseñar el tipo o método para reducir el número de tipos a la que esté acoplado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Excluir esta advertencia cuando el tipo o método todavía se considera fácil de mantener a pesar de su gran número de dependencias en otros tipos.

## <a name="see-also"></a>Vea también
 [Advertencias de mantenimiento](../code-quality/maintainability-warnings.md) [medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
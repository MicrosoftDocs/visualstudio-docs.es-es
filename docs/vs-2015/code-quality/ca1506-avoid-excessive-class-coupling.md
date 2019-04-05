---
title: 'CA1506: Evite el acoplamiento excesivo de clases | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1c5a5e070892f7efc096b0f8e24952bb9d139969
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996245"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Evitar el acoplamiento excesivo de clases
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Excluir esta advertencia cuando el tipo o método se sigue considerando fácil de mantener a pesar de su gran número de dependencias en otros tipos.

## <a name="see-also"></a>Vea también
 [Las advertencias de mantenimiento](../code-quality/maintainability-warnings.md) [medir la complejidad y mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)

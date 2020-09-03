---
title: 'CA1506: Evite el acoplamiento excesivo de clases | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 07f19cb9d4aa2ed118898a1816092479cbd16565
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545709"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Evitar el acoplamiento excesivo de clases
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|Identificador de comprobación|CA1506|
|Category|Microsoft. mantenibilidad|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un tipo o un método se acopla con muchos otros tipos.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla mide el acoplamiento de clase contando el número de referencias de tipo únicas que contiene un tipo o método.

 Los tipos y métodos que tienen un alto grado de acoplamiento de clases pueden ser difíciles de mantener. Se recomienda tener tipos y métodos que muestren un acoplamiento bajo y una cohesión alta.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir esta infracción, intente rediseñar el tipo o el método para reducir el número de tipos a los que está acoplado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Excluya esta advertencia cuando el tipo o el método se sigan considerando manteniéndose a pesar de su gran número de dependencias en otros tipos.

## <a name="see-also"></a>Consulte también
 [Advertencias de mantenimiento](../code-quality/maintainability-warnings.md) que [miden la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)

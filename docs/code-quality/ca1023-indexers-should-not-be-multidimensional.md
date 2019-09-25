---
title: 'CA1023: Los indizadores no deben ser multidimensionales'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f788ded21ef5dd9c84d218cedb55ec8dcf7eff2d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236164"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: Los indizadores no deben ser multidimensionales

|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|Identificador de comprobación|CA1023|
|Categoría|Microsoft.Design|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo
Un tipo público o protegido contiene un indexador público o protegido que usa más de un índice.

## <a name="rule-description"></a>Descripción de la regla
Los indexadores, es decir, las propiedades indizadas, deben usar un solo índice. Los indexadores multidimensionales pueden reducir significativamente la facilidad de uso de la biblioteca. Si el diseño requiere varios índices, reconsidere si el tipo representa un almacén de datos lógico. Si no es así, use un método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, cambie el diseño para usar un índice de cadena o entero solitario, o bien use un método en lugar del indexador.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Suprima una advertencia de esta regla solo después de considerar detenidamente la necesidad del indexador no estándar.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un `DayOfWeek03`tipo,, con un indexador multidimensional que infringe la regla. El indizador se puede ver como un tipo de conversión y, por tanto, se expone más adecuadamente como un método. El tipo se ha rediseñado en `RedesignedDayOfWeek03` para satisfacer la regla.

[!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
[!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
[!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
[CA1043: Usar el argumento integral o de cadena para los indizadores](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

[CA1024: Usar propiedades cuando corresponda](../code-quality/ca1024-use-properties-where-appropriate.md)
---
title: 'CA1023: Los indizadores no deben ser multidimensionales'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3864cbef5a5ba6c013d05112af46d641aa3c1634
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: Los indizadores no deben ser multidimensionales
|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|Identificador de comprobación|CA1023|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público o protegido contiene un indizador público o protegido que utiliza más de un índice.

## <a name="rule-description"></a>Descripción de la regla
 Los indizadores, es decir, las propiedades indizadas, deben utilizar un índice único. Los indizadores multidimensionales pueden reducir significativamente la facilidad de uso de la biblioteca. Si el diseño requiere varios índices, reconsidere si el tipo representa un almacén de datos lógico. Si no es así, utilice un método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el diseño para utilizar un solo entero o un índice de cadena, o utilice un método en lugar del indizador.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla después de considerar cuidadosamente la necesidad del indizador no estándar.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo, `DayOfWeek03`, con un indizador multidimensional que infringe la regla. El indizador se puede considerar como un tipo de conversión y, por tanto, es más apropiado exponerlo como un método. El tipo se ha rediseñado en `RedesignedDayOfWeek03` para cumplir la regla.

 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1043: Utilizar argumento integral o de cadena para los indizadores](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024: Utilizar las propiedades donde corresponda](../code-quality/ca1024-use-properties-where-appropriate.md)
---
title: 'CA1814: Preferir matrices escalonadas antes que multidimensionales'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6d3dc26964a62c952b9c8d18c710e6163bf8ab08
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796922"
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814: Preferir matrices escalonadas antes que multidimensionales

|||
|-|-|
|TypeName|PreferJaggedArraysOverMultidimensional|
|Identificador de comprobación|CA1814|
|Categoría|Microsoft.Performance|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un miembro se declara como una matriz multidimensional.

## <a name="rule-description"></a>Descripción de la regla
 Una matriz escalonada es una matriz cuyos elementos son matrices. Las matrices que constituyen los elementos pueden ser de tamaños diferentes, reduciendo el espacio desaprovechado para algunos conjuntos de datos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie la matriz multidimensional a una matriz escalonada.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Suprima una advertencia de esta regla si la matriz multidimensional no desaprovecha espacio.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra declaraciones de matrices multidimensionales y escalonadas.

 [!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
 [!code-csharp[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]
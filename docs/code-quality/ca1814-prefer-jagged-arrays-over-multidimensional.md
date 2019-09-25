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
ms.openlocfilehash: 2dca4a038dcd5809863037daf7a96811fb60df05
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233572"
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814: Preferir matrices escalonadas antes que multidimensionales

|||
|-|-|
|TypeName|PreferJaggedArraysOverMultidimensional|
|Identificador de comprobación|CA1814|
|Categoría|Microsoft.Performance|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo
Un miembro se declara como una matriz multidimensional.

## <a name="rule-description"></a>Descripción de la regla
Una matriz escalonada es una matriz cuyos elementos son matrices. Las matrices que constituyen los elementos pueden ser de tamaños diferentes, reduciendo el espacio desaprovechado para algunos conjuntos de datos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, cambie la matriz multidimensional a una matriz escalonada.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Suprima una advertencia de esta regla si la matriz multidimensional no desperdicia espacio.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestran las declaraciones de matrices escalonadas y multidimensionales.

[!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
[!code-csharp[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]
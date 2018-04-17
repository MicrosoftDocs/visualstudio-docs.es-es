---
title: 'CA1814: Preferir las matrices escalonadas multidimensionales | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2f87c0141b437cebce2531b5b1ec4cd983fa1822
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814: Preferir las matrices escalonadas antes que multidimensionales
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
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Suprimir una advertencia de esta regla si la matriz multidimensional no desaprovecha espacio.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra declaraciones de matrices escalonadas y multidimensionales.  
  
 [!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
 [!code-csharp[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]
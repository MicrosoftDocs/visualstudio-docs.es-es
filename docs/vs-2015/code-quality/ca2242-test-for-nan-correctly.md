---
title: 'CA2242: Prueba para NaN correcta | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 17a98ce3d213c5d9ae85bb5132a0a44e50112037
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987071"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Comprobar NaN correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|Identificador de comprobación|CA2242|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Una expresión prueba un valor respecto <xref:System.Single.NaN?displayProperty=fullName> o <xref:System.Double.NaN?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.Double.NaN?displayProperty=fullName>, que representa un elemento no numérico, se produce cuando una operación aritmética es indefinida. Cualquier expresión que comprueba la igualdad entre un valor y <xref:System.Double.NaN?displayProperty=fullName> siempre devuelve `false`. Cualquier expresión que comprueba la desigualdad entre un valor y <xref:System.Double.NaN?displayProperty=fullName> siempre devuelve `true`.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla y determinar con precisión si representa un valor <xref:System.Double.NaN?displayProperty=fullName>, utilice <xref:System.Single.IsNaN%2A?displayProperty=fullName> o <xref:System.Double.IsNaN%2A?displayProperty=fullName> para probar el valor.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra dos expresiones que prueban incorrectamente un valor contra <xref:System.Double.NaN?displayProperty=fullName> y una expresión que se utiliza correctamente <xref:System.Double.IsNaN%2A?displayProperty=fullName> para probar el valor.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]

---
title: 'CA2242: Prueba para NaN correcta'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c742c73d73802a21ea7a21a426cf815ee4e34e2d
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45545624"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Prueba para NaN correcta

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

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra dos expresiones que prueban incorrectamente un valor contra <xref:System.Double.NaN?displayProperty=fullName> y una expresión que se utiliza correctamente <xref:System.Double.IsNaN%2A?displayProperty=fullName> para probar el valor.

 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]
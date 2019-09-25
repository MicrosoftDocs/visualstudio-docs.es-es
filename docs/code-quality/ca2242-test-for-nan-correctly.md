---
title: 'CA2242: Comprobar NaN correctamente'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0e74ec49667a4fe66c399bd15e8b24aa6589ce88
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237842"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Comprobar NaN correctamente

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|Identificador de comprobación|CA2242|
|Categoría|Microsoft.Usage|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo
Una expresión prueba un valor con <xref:System.Single.NaN?displayProperty=fullName> o <xref:System.Double.NaN?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.Double.NaN?displayProperty=fullName>, que representa un valor no numérico, se produce cuando una operación aritmética no está definida. Cualquier expresión que comprueba la igualdad entre un valor <xref:System.Double.NaN?displayProperty=fullName> y siempre `false`devuelve. Cualquier expresión que comprueba la desigualdad entre un valor y <xref:System.Double.NaN?displayProperty=fullName> siempre devuelve `true`.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla y determinar con precisión si un valor <xref:System.Double.NaN?displayProperty=fullName>representa, <xref:System.Single.IsNaN%2A?displayProperty=fullName> use <xref:System.Double.IsNaN%2A?displayProperty=fullName> o para probar el valor.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestran dos expresiones que prueban incorrectamente un <xref:System.Double.NaN?displayProperty=fullName> valor en y una expresión que <xref:System.Double.IsNaN%2A?displayProperty=fullName> usa correctamente para probar el valor.

[!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
[!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]
---
title: 'CA2104: No declarar tipos de referencia mutable de solo lectura'
ms.date: 11/01/2018
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8f4f165b4b00f46b478907c9affca672b4c7f113
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232951"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: No declarar tipos de referencias mutables de solo lectura

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|Identificador de comprobación|CA2104|
|Categoría|Microsoft.Security|
|Cambio importante|Poco problemático|

> [!NOTE]
> La regla CA2104 está obsoleta y se quitará en una versión futura de Visual Studio. No se implementará como [analizador](roslyn-analyzers-overview.md) debido al análisis complicado necesario para determinar la inmutabilidad real de un tipo.

## <a name="cause"></a>Motivo

Un tipo visible externamente contiene un campo de sólo lectura visible externamente que es un tipo de referencia que se puede cambiar.

## <a name="rule-description"></a>Descripción de la regla

Un tipo que mutable es un tipo cuyos datos de instancia se pueden modificar. La <xref:System.Text.StringBuilder?displayProperty=fullName> clase es un ejemplo de un tipo de referencia mutable. Contiene miembros que pueden cambiar el valor de una instancia de la clase. Un ejemplo de un tipo de referencia inmutable <xref:System.String?displayProperty=fullName> es la clase. Una vez creada la instancia, su valor nunca puede cambiar.

El modificador de solo lectura ([ReadOnly](/dotnet/csharp/language-reference/keywords/readonly) in C#, [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) in Visual Basic y [const](/cpp/cpp/const-cpp) in C++) en un campo de tipo de referencia (o puntero C++en) impide que el campo se reemplace por otra instancia del tipo de referencia. Sin embargo, el modificador no impide que los datos de instancia del campo se modifiquen a través del tipo de referencia.

Esta regla puede mostrar accidentalmente una infracción de un tipo que es, de hecho, inmutable. En ese caso, es seguro suprimir la advertencia.

Los campos de matriz de solo lectura están exentos de esta regla pero, en su lugar [, provocan una infracción de CA2105: Los campos de matriz no deben ser](../code-quality/ca2105-array-fields-should-not-be-read-only.md) reglas de solo lectura.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, quite el modificador de solo lectura o, si es aceptable un cambio importante, reemplace el campo por un tipo inmutable.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla si el tipo de campo es inmutable.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra una declaración de campo que provoca una infracción de esta regla:

[!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
[!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
[!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]
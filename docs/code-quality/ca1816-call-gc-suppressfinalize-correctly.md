---
title: 'CA1816: Llamar a GC.SuppressFinalize correctamente'
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3fdd20df37586e50b5236872f1d84de48d08c87a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233525"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: Llamar a GC.SuppressFinalize correctamente

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|Identificador de comprobación|CA1816|
|Categoría|Microsoft. Uso|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Las infracciones de esta regla pueden deberse a:

- Un método que es una implementación de <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> y no llama <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>a.

- Un método que no es una implementación de <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> y llama <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>a.

- Un método que llama <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> a y pasa un valor distinto de [thisC#()](/dotnet/csharp/language-reference/keywords/this) o [me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="rule-description"></a>Descripción de la regla

El <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> método permite a los usuarios liberar recursos en cualquier momento antes de que el objeto esté disponible para la recolección de elementos no utilizados. Si se <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> llama al método, libera los recursos del objeto. Esto hace que la finalización sea innecesaria. <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>debe llamar <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> a para que el recolector de elementos no utilizados no llame al finalizador del objeto.

Para evitar que los tipos derivados con finalizadores tengan que volver <xref:System.IDisposable> a implementar y llamarlos, los tipos no sellados sin los finalizadores <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>deben seguir llamando a.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla:

- Si el método es una implementación de <xref:System.IDisposable.Dispose%2A>, agregue una llamada a <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Si el método no es una implementación de <xref:System.IDisposable.Dispose%2A>, quite la llamada a <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> o muévala a la implementación del <xref:System.IDisposable.Dispose%2A> tipo.

- Cambie todas las llamadas <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> a para pasar [thisC#()](/dotnet/csharp/language-reference/keywords/this) o [me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Solo debe suprimir una advertencia de esta regla si usa <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> deliberadamente para controlar la duración de otros objetos. No suprima una advertencia de esta regla si una implementación <xref:System.IDisposable.Dispose%2A> de no <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>llama a. En esta situación, si no se puede suprimir la finalización, se degrada el rendimiento y no se proporciona ninguna ventaja.

## <a name="example-that-violates-ca1816"></a>Ejemplo que infringe CA1816

Este código muestra un método que llama <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>a, pero no pasa [thisC#()](/dotnet/csharp/language-reference/keywords/this) o [me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me). Como resultado, este código infringe la regla CA1816.

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]

## <a name="example-that-satisfies-ca1816"></a>Ejemplo que satisface CA1816

Este ejemplo muestra un método que llama <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> correctamente a pasando [this (C#)](/dotnet/csharp/language-reference/keywords/this) o [me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA2215 Los métodos Dispose deben llamar a Dispose de la clase base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)
- [CA2216: Los tipos descartables deben declarar el finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Vea también

- [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)
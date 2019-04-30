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
ms.openlocfilehash: 2c14f9ed8803c02d1570ac2a3dee82fbdfca5f01
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796785"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: Llamar a GC.SuppressFinalize correctamente

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|Identificador de comprobación|CA1816|
|Categoría|Microsoft. Uso|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Las infracciones de esta regla pueden deberse a:

- Un método que es una implementación de <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> y no llama a <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Un método que no es una implementación de <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> y llama a <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Un método que llama a <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> y pasa algo distinto [este (C#)](/dotnet/csharp/language-reference/keywords/this) o [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="rule-description"></a>Descripción de la regla

El <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> método permite a los usuarios liberar los recursos en cualquier momento antes que el objeto se encuentre disponible para la recolección de elementos. Si el <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> se llama al método, libera los recursos del objeto. Esto hace que la finalización innecesaria. <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> debe llamar a <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> por lo que el recolector de elementos no utilizados no llame al finalizador del objeto.

Para impedir que los tipos derivados con finalizadores tengan que volver a <xref:System.IDisposable> y para llamarlo, los tipos no sellados los finalizadores deben llamar a <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla:

- Si el método es una implementación de <xref:System.IDisposable.Dispose%2A>, agregue una llamada a <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Si el método no es una implementación de <xref:System.IDisposable.Dispose%2A>, quite la llamada a <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> o muévalo a la del tipo <xref:System.IDisposable.Dispose%2A> implementación.

- Cambiar todas las llamadas a <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> pasar [este (C#)](/dotnet/csharp/language-reference/keywords/this) o [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Sólo suprima una advertencia de esta regla si usas deliberadamente <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> para controlar la duración de otros objetos. No suprima una advertencia de esta regla si una implementación de <xref:System.IDisposable.Dispose%2A> no llama a <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>. En esta situación, no se puede suprimir la finalización disminuye el rendimiento y no ofrece ninguna ventaja.

## <a name="example-that-violates-ca1816"></a>Ejemplo que infringe CA1816

Este código muestra un método que llama a <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>, pero no pasa [este (C#)](/dotnet/csharp/language-reference/keywords/this) o [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me). Como resultado, este código infringe la regla CA1816.

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]

## <a name="example-that-satisfies-ca1816"></a>Ejemplo que cumple CA1816

En este ejemplo se muestra un método que correctamente las llamadas <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> pasando [este (C#)](/dotnet/csharp/language-reference/keywords/this) o [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA2215: Los métodos Dispose deben llamar al método dispose de clase base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)
- [CA2216: Los tipos descartables deben declarar el finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Vea también

- [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)
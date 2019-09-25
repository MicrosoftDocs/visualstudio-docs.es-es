---
title: 'CA2216: Los tipos descartables deben declarar el finalizador'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1616e889b3892aa656692a3e5b0895d4b131b7f1
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231252"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216: Los tipos descartables deben declarar el finalizador

|||
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|Identificador de comprobación|CA2216|
|Categoría|Microsoft.Usage|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Un tipo que implementa <xref:System.IDisposable?displayProperty=fullName>, y tiene campos que sugieren el uso de recursos no administrados, no implementa un finalizador tal como se describe en. <xref:System.Object.Finalize%2A?displayProperty=fullName>

## <a name="rule-description"></a>Descripción de la regla

Se genera una infracción de esta regla si el tipo descartable contiene campos de los siguientes tipos:

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, implemente un finalizador que <xref:System.IDisposable.Dispose%2A> llame a su método.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla si el tipo no implementa <xref:System.IDisposable> para liberar recursos no administrados.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un tipo que infringe esta regla.

[!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas

[CA2115 Llame a GC. KeepAlive al usar recursos nativos](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816: Llame a GC. SuppressFinalize correctamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

[CA1049: Los tipos que poseen recursos nativos deben ser descartables](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>Vea también

- <xref:System.IDisposable?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)
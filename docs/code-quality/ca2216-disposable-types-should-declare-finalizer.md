---
title: 'CA2216: Los tipos descartables deben declarar el finalizador'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f53f91a6a4775fb17e273fb87c4c669f74ad45e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826002"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216: Los tipos descartables deben declarar el finalizador

|||
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|Identificador de comprobación|CA2216|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Un tipo que implementa <xref:System.IDisposable?displayProperty=fullName>y tiene campos que sugieren el uso de recursos no administrados, no implementa un finalizador descrito por <xref:System.Object.Finalize%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla

Una infracción de esta regla se notifica si el tipo desechable contiene campos de los siguientes tipos:

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, implemente un finalizador que llama a su <xref:System.IDisposable.Dispose%2A> método.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla si el tipo no implementa <xref:System.IDisposable> con el fin de liberar recursos no administrados.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra un tipo que infringe esta regla.

[!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas

[CA2115: Llamar a GC. KeepAlive cuando se utilicen recursos nativos](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816: Llamar a GC. SuppressFinalize correctamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

[CA1049: Los tipos que poseen recursos nativos deben ser descartables](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>Vea también

- <xref:System.IDisposable?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)
---
title: 'CA1049: Los tipos que poseen recursos nativos deben ser descartables'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- cplusplus
ms.openlocfilehash: ef7b72eade7ea8e4486d5c317c06026bb4d0b95f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235744"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: Los tipos que poseen recursos nativos deben ser descartables

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|Identificador de comprobación|CA1049|
|Categoría|Microsoft.Design|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Un tipo hace referencia <xref:System.IntPtr?displayProperty=fullName> a un campo <xref:System.UIntPtr?displayProperty=fullName> , un campo o <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> un campo, pero no implementa <xref:System.IDisposable?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla

Esta regla presupone que <xref:System.IntPtr>los <xref:System.UIntPtr>campos, <xref:System.Runtime.InteropServices.HandleRef> y almacenan punteros a recursos no administrados. Los tipos que asignan recursos no administrados <xref:System.IDisposable> deben implementar para permitir que los llamadores liberen esos recursos a petición y acortar la duración de los objetos que contienen los recursos.

El patrón de diseño recomendado para limpiar los recursos no administrados es proporcionar un medio implícito y explícito para liberar esos recursos mediante el <xref:System.Object.Finalize%2A?displayProperty=fullName> método y el <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> método, respectivamente. El recolector de elementos <xref:System.Object.Finalize%2A> no utilizados llama al método de un objeto en un momento indeterminado después de que se determine que el objeto ya no es accesible. Después <xref:System.Object.Finalize%2A> de llamar a, se necesita una recolección de elementos no utilizados adicional para liberar el objeto. El <xref:System.IDisposable.Dispose%2A> método permite al llamador liberar explícitamente los recursos a petición, antes de que se liberen los recursos si se dejan en el recolector de elementos no utilizados. Después de limpiar los recursos no administrados, <xref:System.IDisposable.Dispose%2A> debe <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> llamar al método para que el recolector de elementos no <xref:System.Object.Finalize%2A> utilizados sepa que ya no tiene que llamarse; Esto elimina la necesidad de la recolección de elementos no utilizados adicional y acorta el duración del objeto.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, <xref:System.IDisposable>implemente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla si el tipo no hace referencia a un recurso no administrado. De lo contrario, no suprima una advertencia de esta regla porque el <xref:System.IDisposable> error de implementación puede hacer que los recursos no administrados dejen de estar disponibles o no se utilicen.

## <a name="example"></a>Ejemplo
<xref:System.IDisposable> En el ejemplo siguiente se muestra un tipo que implementa para limpiar un recurso no administrado.

[!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
[!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
[CA2115 Llame a GC. KeepAlive al usar recursos nativos](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816: Llame a GC. SuppressFinalize correctamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

[CA2216: Los tipos descartables deben declarar el finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

[CA1001: los tipos que poseen campos descartables deben ser descartables](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Vea también

- [Limpieza de recursos no administrados](/dotnet/standard/garbage-collection/unmanaged)
- [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)
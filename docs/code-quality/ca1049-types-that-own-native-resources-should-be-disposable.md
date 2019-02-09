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
ms.openlocfilehash: 41ab039d33155769eac13469a65f2a35c8ed7324
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922620"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: Los tipos que poseen recursos nativos deben ser descartables

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|Identificador de comprobación|CA1049|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo

Un tipo hace referencia a un <xref:System.IntPtr?displayProperty=fullName> campo, un <xref:System.UIntPtr?displayProperty=fullName> campo, o un <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> campo, pero no implementa <xref:System.IDisposable?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla

Esta regla supone que <xref:System.IntPtr>, <xref:System.UIntPtr>, y <xref:System.Runtime.InteropServices.HandleRef> campos almacenan punteros a los recursos no administrados. Tipos que asignan recursos no administrados deberían implementar <xref:System.IDisposable> para permitir que los llamadores liberen estos recursos a petición y acortar la duración de los objetos que contienen los recursos.

El patrón de diseño recomendado para limpiar los recursos no administrados es proporcionar tanto implícita como una forma explícita para liberar dichos recursos mediante el uso de la <xref:System.Object.Finalize%2A?displayProperty=fullName> método y el <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> método, respectivamente. El recolector de elementos no utilizados llame al <xref:System.Object.Finalize%2A> método de un objeto en algún momento indeterminado después de que el objeto se determina que ya no es accesible. Después de <xref:System.Object.Finalize%2A> se llama, adicional necesario recolección para liberar el objeto. El <xref:System.IDisposable.Dispose%2A> método permite al llamador libere recursos a petición, anteriores a los recursos se liberaba si se deja al recolector de elementos no utilizados de forma explícita. Después de que limpia los recursos no administrados, <xref:System.IDisposable.Dispose%2A> debe llamar a la <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> método para que el recolector de elementos no utilizados sepa que <xref:System.Object.Finalize%2A> ya no tiene que llamarse; Esto elimina la necesidad de la colección de elementos no utilizados adicionales y reduce el duración del objeto.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, implemente <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el tipo no hace referencia a un recurso no administrado. En caso contrario, no suprima una advertencia de esta regla porque si no se implementan <xref:System.IDisposable> puede provocar que los recursos no administrados se convierten en no disponibles o infrautilizados.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que implementa <xref:System.IDisposable> para limpiar un recurso no administrado.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2115: Llamar a GC. KeepAlive cuando se utilicen recursos nativos](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: Llamar a GC. SuppressFinalize correctamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: Los tipos descartables deben declarar el finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: los tipos que poseen campos descartables deben ser descartables](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Vea también

- [Limpieza de recursos no administrados](/dotnet/standard/garbage-collection/unmanaged)
- [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)
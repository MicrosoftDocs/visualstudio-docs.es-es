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
ms.openlocfilehash: a39d1e03da062f3030571820e98898d5122d495f
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349100"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: Los tipos que poseen recursos nativos deben ser descartables

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|Identificador de comprobación|CA1049|
|Categoría|Microsoft. Design|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Un tipo hace referencia a un campo @no__t 0, un campo <xref:System.UIntPtr?displayProperty=fullName> o un campo @no__t 2, pero no implementa <xref:System.IDisposable?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla

Esta regla presupone que los campos <xref:System.IntPtr>, <xref:System.UIntPtr> y <xref:System.Runtime.InteropServices.HandleRef> almacenan punteros a recursos no administrados. Los tipos que asignan recursos no administrados deben implementar <xref:System.IDisposable> para permitir a los autores de llamadas liberar esos recursos a petición y acortar la duración de los objetos que contienen los recursos.

El patrón de diseño recomendado para limpiar los recursos no administrados es proporcionar un medio implícito y explícito para liberar esos recursos mediante el método <xref:System.Object.Finalize%2A?displayProperty=fullName> y el método <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>, respectivamente. El recolector de elementos no utilizados llama al método <xref:System.Object.Finalize%2A> de un objeto en un tiempo indeterminado después de que se determine que el objeto ya no es accesible. Después de llamar a <xref:System.Object.Finalize%2A>, se necesita una recolección de elementos no utilizados adicional para liberar el objeto. El método <xref:System.IDisposable.Dispose%2A> permite que el autor de la llamada libere explícitamente los recursos a petición, antes de que se liberaran los recursos si se dejan al recolector de elementos no utilizados. Después de limpiar los recursos no administrados, <xref:System.IDisposable.Dispose%2A> debe llamar al método <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> para que el recolector de elementos no utilizados sepa que <xref:System.Object.Finalize%2A> ya no tiene que llamarse; Esto elimina la necesidad de la recolección de elementos no utilizados adicional y acorta la duración del objeto.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, implemente <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla si el tipo no hace referencia a un recurso no administrado. De lo contrario, no suprima una advertencia de esta regla porque un error al implementar <xref:System.IDisposable> puede hacer que los recursos no administrados dejen de estar disponibles o no estén en uso.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un tipo que implementa <xref:System.IDisposable> para limpiar un recurso no administrado.

[!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
[!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
[CA2115: Llamar a GC.KeepAlive cuando se utilicen recursos nativos](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816: Llame a GC.SuppressFinalize correctamente](../code-quality/ca1816.md)

[CA2216: Los tipos descartables deben declarar el finalizador](../code-quality/ca2216.md)

[CA1001: Los tipos que poseen campos descartables deben ser descartables](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Vea también

- [Limpieza de recursos no administrados](/dotnet/standard/garbage-collection/unmanaged)
- [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)
---
title: 'CA1049: los tipos que poseen recursos nativos deben ser descartables | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aaaf95346c51e2cb5cadb01a39e482bb508bc764
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668906"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: Los tipos que poseen recursos nativos deben ser descartables
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|Identificador de comprobación|CA1049|
|Categoría|Microsoft. Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo hace referencia a un campo de <xref:System.IntPtr?displayProperty=fullName>, un campo de <xref:System.UIntPtr?displayProperty=fullName> o un campo de <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>, pero no implementa <xref:System.IDisposable?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla presupone que los campos <xref:System.IntPtr>, <xref:System.UIntPtr> y <xref:System.Runtime.InteropServices.HandleRef> almacenan punteros a recursos no administrados. Los tipos que asignan recursos no administrados deben implementar <xref:System.IDisposable> para permitir a los autores de llamadas liberar esos recursos a petición y acortar la duración de los objetos que contienen los recursos.

 El patrón de diseño recomendado para limpiar los recursos no administrados es proporcionar un medio implícito y explícito para liberar esos recursos mediante el método <xref:System.Object.Finalize%2A?displayProperty=fullName> y el método <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>, respectivamente. El recolector de elementos no utilizados llama al método <xref:System.Object.Finalize%2A> de un objeto en un tiempo indeterminado después de que se determine que el objeto ya no es accesible. Una vez que se llama a <xref:System.Object.Finalize%2A>, se necesita una recolección de elementos no utilizados adicional para liberar el objeto. El método <xref:System.IDisposable.Dispose%2A> permite al llamador liberar explícitamente los recursos a petición, antes de que se liberen los recursos si se dejan al recolector de elementos no utilizados. Después de limpiar los recursos no administrados, <xref:System.IDisposable.Dispose%2A> debe llamar al método <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> para que el recolector de elementos no utilizados sepa que <xref:System.Object.Finalize%2A> ya no tiene que llamarse; Esto elimina la necesidad de la recolección de elementos no utilizados adicional y acorta la duración del objeto.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, implemente <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el tipo no hace referencia a un recurso no administrado. De lo contrario, no suprima una advertencia de esta regla porque un error al implementar <xref:System.IDisposable> puede hacer que los recursos no administrados dejen de estar disponibles o no estén en uso.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo que implementa <xref:System.IDisposable> para limpiar un recurso no administrado.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/cs/FxCop.Design.UnmanagedResources.cs#1)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/vb/FxCop.Design.UnmanagedResources.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2115: Llamar a GC.KeepAlive cuando se utilicen recursos nativos](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: Llame a GC.SuppressFinalize correctamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: Los tipos descartables deben declarar el finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: Los tipos que poseen campos descartables deben ser descartables](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Vea también
  [Patrón de Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)

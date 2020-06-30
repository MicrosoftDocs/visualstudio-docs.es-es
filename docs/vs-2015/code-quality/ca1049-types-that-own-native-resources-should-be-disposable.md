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
ms.openlocfilehash: 49c56b98e3be01675c2c21cd11c2961dd75f4877
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546814"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: Los tipos que poseen recursos nativos deben ser descartables
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|Identificador de comprobación|CA1049|
|Category|Microsoft. Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Un tipo hace referencia a un <xref:System.IntPtr?displayProperty=fullName> campo, un <xref:System.UIntPtr?displayProperty=fullName> campo o un <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> campo, pero no implementa <xref:System.IDisposable?displayProperty=fullName> .

## <a name="rule-description"></a>Descripción de la regla
 Esta regla presupone que <xref:System.IntPtr> <xref:System.UIntPtr> <xref:System.Runtime.InteropServices.HandleRef> los campos, y almacenan punteros a recursos no administrados. Los tipos que asignan recursos no administrados deben implementar <xref:System.IDisposable> para permitir que los llamadores liberen esos recursos a petición y acortar la duración de los objetos que contienen los recursos.

 El patrón de diseño recomendado para limpiar los recursos no administrados es proporcionar un medio implícito y explícito para liberar esos recursos mediante el <xref:System.Object.Finalize%2A?displayProperty=fullName> método y el <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> método, respectivamente. El recolector de elementos no utilizados llama al <xref:System.Object.Finalize%2A> método de un objeto en un momento indeterminado después de que se determine que el objeto ya no es accesible. Después de <xref:System.Object.Finalize%2A> llamar a, se necesita una recolección de elementos no utilizados adicional para liberar el objeto. El <xref:System.IDisposable.Dispose%2A> método permite al llamador liberar explícitamente los recursos a petición, antes de que se liberen los recursos si se dejan en el recolector de elementos no utilizados. Después de limpiar los recursos no administrados, <xref:System.IDisposable.Dispose%2A> debe llamar al <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> método para que el recolector de elementos no utilizados sepa que ya <xref:System.Object.Finalize%2A> no tiene que llamarse; Esto elimina la necesidad de la recolección de elementos no utilizados adicional y acorta la duración del objeto.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, implemente <xref:System.IDisposable> .

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el tipo no hace referencia a un recurso no administrado. De lo contrario, no suprima una advertencia de esta regla porque el error de implementación <xref:System.IDisposable> puede hacer que los recursos no administrados dejen de estar disponibles o no se utilicen.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo que implementa <xref:System.IDisposable> para limpiar un recurso no administrado.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/cs/FxCop.Design.UnmanagedResources.cs#1)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/vb/FxCop.Design.UnmanagedResources.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2115: Llamar a Call GC.KeepAlive cuando se utilicen recursos nativos](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: Llamar a GC.SuppressFinalize correctamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: Los tipos descartables deben declarar el finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: Los tipos que poseen campos descartables deben ser descartables](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Consulte también
  [Patrón de Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)

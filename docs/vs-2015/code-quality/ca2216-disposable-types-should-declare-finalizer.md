---
title: 'CA2216: los tipos descartables deben declarar el finalizador | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 082afacba1ccf4c982e5ddceec37d2a1567efd7a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651649"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216: Los tipos descartables deben declarar el finalizador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|Identificador de comprobación|CA2216|
|Categoría|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un tipo que implementa <xref:System.IDisposable?displayProperty=fullName>, y tiene campos que sugieren el uso de recursos no administrados, no implementa un finalizador tal y como se describe en <xref:System.Object.Finalize%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla
 Se genera una infracción de esta regla si el tipo descartable contiene campos de los siguientes tipos:

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, implemente un finalizador que llame a su método de <xref:System.IDisposable.Dispose%2A>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el tipo no implementa <xref:System.IDisposable> con el fin de liberar recursos no administrados.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo que infringe esta regla.

 [!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DisposeNoFinalize/cs/FxCop.Usage.DisposeNoFinalize.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2115: Llamar a GC.KeepAlive cuando se utilicen recursos nativos](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: Llame a GC.SuppressFinalize correctamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA1049: Los tipos que poseen recursos nativos deben ser descartables](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>Vea también
 <xref:System.IDisposable?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 [Patrón de Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)

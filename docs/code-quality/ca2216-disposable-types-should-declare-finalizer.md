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
ms.openlocfilehash: 3ac52bdb17aeb7d04e434d2b02ff9a905eab49a2
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305918"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216: Los tipos descartables deben declarar el finalizador

|||
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|Identificador de comprobación|CA2216|
|Category|Microsoft.Usage|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Un tipo que implementa <xref:System.IDisposable?displayProperty=fullName>, y tiene campos que sugieren el uso de recursos no administrados, no implementa un finalizador tal y como se describe en <xref:System.Object.Finalize%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla

Se genera una infracción de esta regla si el tipo descartable contiene campos de los siguientes tipos:

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, implemente un finalizador que llame al método <xref:System.IDisposable.Dispose%2A>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla si el tipo no implementa <xref:System.IDisposable> con el fin de liberar recursos no administrados.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un tipo que infringe esta regla.

[!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas

@NO__T 0CA2115: Llame a GC. KeepAlive al usar recursos nativos @ no__t-0

[CA1816: Llame a GC. SuppressFinalize correctamente @ no__t-0

[CA1049: Los tipos que poseen recursos nativos deben ser descartables @ no__t-0

## <a name="see-also"></a>Vea también

- <xref:System.IDisposable?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)
---
title: 'CA2115: Llamar a Call GC.KeepAlive cuando se utilicen recursos nativos'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 8307c9cd133671d5cc1e1c32fc257965198f0a9e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023673"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: Llamar a Call GC.KeepAlive cuando se utilicen recursos nativos

|||
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|Identificador de comprobación|CA2115|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Un método declarado en un tipo con un finalizador hace referencia a un <xref:System.IntPtr?displayProperty=fullName> o <xref:System.UIntPtr?displayProperty=fullName> campo, pero no llama a <xref:System.GC.KeepAlive%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla

Recolección finaliza un objeto si no hay ninguna referencia a ella más en código administrado. No administradas referencias a objetos no impiden la recolección de elementos. Esta regla detecta errores que pueden haberse producido porque se finaliza un recurso no administrado mientras todavía se utiliza en código no administrado.

Esta regla supone que <xref:System.IntPtr> y <xref:System.UIntPtr> campos almacenan punteros a los recursos no administrados. Dado que es el propósito de un finalizador liberar recursos no administrados, la regla supone que el finalizador liberará el recurso no administrado que apunta a los campos de puntero. Esta regla también se supone que el método hace referencia el campo de puntero para pasar el recurso no administrado a código no administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, agregue una llamada a <xref:System.GC.KeepAlive%2A> al método, pasando la instancia actual (`this` en C# y C++) como argumento. Coloque la llamada después de la última línea del código donde se debe proteger el objeto de colección de elementos no utilizados. Inmediatamente después de llamar a <xref:System.GC.KeepAlive%2A>, el objeto nuevo se considera preparado para la recolección suponiendo que no hay ninguna referencia administrada a él.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Esta regla hace algunas suposiciones que pueden dar lugar a falsos positivos. Puede suprimir de forma segura una advertencia de esta regla si:

- El finalizador no libera el contenido de la <xref:System.IntPtr> o <xref:System.UIntPtr> campo al que hace referencia al método.

- El método no pasa la <xref:System.IntPtr> o <xref:System.UIntPtr> campo a código no administrado.

Revise cuidadosamente otros mensajes antes de excluirlos. Esta regla detecta errores que son difíciles de reproducir y depurar.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente, `BadMethod` no incluye una llamada a `GC.KeepAlive` y, por tanto, infringe la regla. `GoodMethod` contiene el código corregido.

> [!NOTE]
> En este ejemplo es el pseudocódigo. Aunque el código se compila y ejecuta, no se desencadena la advertencia porque no se creó o se libera un recurso no administrado.

[!code-csharp[FxCop.Security.IntptrAndFinalize#1](../code-quality/codesnippet/CSharp/ca2115-call-gc-keepalive-when-using-native-resources_1.cs)]

## <a name="see-also"></a>Vea también

- <xref:System.GC.KeepAlive%2A?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)
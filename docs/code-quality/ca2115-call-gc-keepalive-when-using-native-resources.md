---
title: 'CA2115: Llamar a Call GC.KeepAlive cuando se utilicen recursos nativos'
ms.date: 11/04/2016
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
ms.openlocfilehash: eb6d28e15870907034479e698ba8e7464f4f5159
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232720"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: Llamar a Call GC.KeepAlive cuando se utilicen recursos nativos

|||
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|Identificador de comprobación|CA2115|
|Categoría|Microsoft.Security|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Un método declarado en un tipo con un finalizador hace referencia <xref:System.IntPtr?displayProperty=fullName> a <xref:System.UIntPtr?displayProperty=fullName> un campo o, pero no <xref:System.GC.KeepAlive%2A?displayProperty=fullName>llama a.

## <a name="rule-description"></a>Descripción de la regla

La recolección de elementos no utilizados finaliza un objeto si no hay más referencias a él en el código administrado. Las referencias no administradas a objetos no impiden la recolección de elementos no utilizados. Esta regla detecta errores que pueden haberse producido porque se finaliza un recurso no administrado mientras todavía se utiliza en código no administrado.

Esta regla presupone que <xref:System.IntPtr> los <xref:System.UIntPtr> campos y almacenan punteros a recursos no administrados. Dado que el propósito de un finalizador es liberar recursos no administrados, la regla presupone que el finalizador liberará el recurso no administrado al que apuntan los campos de puntero. Esta regla también supone que el método hace referencia al campo de puntero para pasar el recurso no administrado a código no administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, agregue una llamada <xref:System.GC.KeepAlive%2A> a al método, pasando la instancia actual (`this` en C# y C++) como argumento. Coloque la llamada después de la última línea de código donde se debe proteger el objeto de la recolección de elementos no utilizados. Inmediatamente después de la llamada <xref:System.GC.KeepAlive%2A>a, el objeto se considera como listo para la recolección de elementos no utilizados, suponiendo que no hay ninguna referencia administrada a él.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Esta regla realiza algunas suposiciones que pueden provocar falsos positivos. Puede suprimir de forma segura una advertencia de esta regla si:

- El finalizador no libera el contenido del <xref:System.IntPtr> campo o <xref:System.UIntPtr> al que hace referencia el método.

- El método no pasa el <xref:System.IntPtr> campo o <xref:System.UIntPtr> a código no administrado.

Revise cuidadosamente otros mensajes antes de excluirlos. Esta regla detecta errores que son difíciles de reproducir y depurar.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente, `BadMethod` no incluye una llamada a `GC.KeepAlive` y, por tanto, infringe la regla. `GoodMethod`contiene el código corregido.

> [!NOTE]
> Este ejemplo es pseudo-Code. Aunque el código se compila y se ejecuta, la advertencia no se desencadena porque no se crea o libera un recurso no administrado.

[!code-csharp[FxCop.Security.IntptrAndFinalize#1](../code-quality/codesnippet/CSharp/ca2115-call-gc-keepalive-when-using-native-resources_1.cs)]

## <a name="see-also"></a>Vea también

- <xref:System.GC.KeepAlive%2A?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)
---
title: 'CA2115: llama a GC. KeepAlive al usar recursos nativos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c668172ca318000068fb4e90f4848e456c32208d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543629"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: Llamar a Call GC.KeepAlive cuando se utilicen recursos nativos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|Identificador de comprobación|CA2115|
|Category|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Un método declarado en un tipo con un finalizador hace referencia a un <xref:System.IntPtr?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName> campo o, pero no llama a <xref:System.GC.KeepAlive%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Descripción de la regla
 La recolección de elementos no utilizados finaliza un objeto si no hay más referencias a él en el código administrado. Las referencias no administradas a objetos no impiden la recolección de elementos no utilizados. Esta regla detecta errores que pueden haberse producido porque se finaliza un recurso no administrado mientras todavía se utiliza en código no administrado.

 Esta regla presupone que <xref:System.IntPtr> <xref:System.UIntPtr> los campos y almacenan punteros a recursos no administrados. Dado que el propósito de un finalizador es liberar recursos no administrados, la regla presupone que el finalizador liberará el recurso no administrado al que apuntan los campos de puntero. Esta regla también supone que el método hace referencia al campo de puntero para pasar el recurso no administrado a código no administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue una llamada a al <xref:System.GC.KeepAlive%2A> método, pasando la instancia actual ( `this` en C# y C++) como argumento. Coloque la llamada después de la última línea de código donde se debe proteger el objeto de la recolección de elementos no utilizados. Inmediatamente después de la llamada a <xref:System.GC.KeepAlive%2A> , el objeto se considera como listo para la recolección de elementos no utilizados, suponiendo que no hay ninguna referencia administrada a él.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Esta regla realiza algunas suposiciones que pueden provocar falsos positivos. Puede suprimir de forma segura una advertencia de esta regla si:

- El finalizador no libera el contenido del <xref:System.IntPtr> <xref:System.UIntPtr> campo o al que hace referencia el método.

- El método no pasa el <xref:System.IntPtr> campo o <xref:System.UIntPtr> a código no administrado.

  Revise cuidadosamente otros mensajes antes de excluirlos. Esta regla detecta errores que son difíciles de reproducir y depurar.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, no `BadMethod` incluye una llamada a `GC.KeepAlive` y, por tanto, infringe la regla. `GoodMethod` contiene el código corregido.

> [!NOTE]
> Este ejemplo es pseudo-Code, aunque el código se compila y ejecuta, la advertencia no se desencadena porque no se crea o libera un recurso no administrado.

 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.IntptrAndFinalize/cs/FxCop.Security.IntptrAndFinalize.cs#1)]

## <a name="see-also"></a>Consulte también
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 [Patrón de Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)

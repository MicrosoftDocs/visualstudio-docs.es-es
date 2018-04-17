---
title: 'CA2115: Llamar a GC. KeepAlive cuando se utilicen recursos nativos | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 5ea82194eced9caed52e75216091060ff9350379
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: Llamar a GC.KeepAlive cuando se utilicen recursos nativos
|||  
|-|-|  
|TypeName|CallGCKeepAliveWhenUsingNativeResources|  
|Identificador de comprobación|CA2115|  
|Categoría|Microsoft.Security|  
|Cambio problemático|No trascendental|  
  
## <a name="cause"></a>Motivo  
 Un método declarado en un tipo con un finalizador hace referencia a un <xref:System.IntPtr?displayProperty=fullName> o <xref:System.UIntPtr?displayProperty=fullName> campo, pero no llama a <xref:System.GC.KeepAlive%2A?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Colección de elementos no utilizados finaliza un objeto si no hay ninguna referencia más a él en el código administrado. No administradas referencias a objetos impedir la recolección. Esta regla detecta errores que pueden haberse producido porque se finaliza un recurso no administrado mientras todavía se utiliza en código no administrado.  
  
 Esta regla supone que <xref:System.IntPtr> y <xref:System.UIntPtr> campos almacenan punteros a los recursos no administrados. Dado que el propósito de un finalizador es liberar recursos no administrados, la regla supone que el finalizador liberará el recurso no administrado que señala a los campos de puntero. Esta regla también se da por supuesto que el método hacen referencia al campo de puntero para pasar el recurso no administrado a código no administrado.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, agregue una llamada a <xref:System.GC.KeepAlive%2A> al método, pasando la instancia actual (`this` en C# y C++) como argumento. Coloque la llamada después de la última línea de código donde se debe proteger el objeto de colección de elementos no utilizados. Inmediatamente después de llamar a <xref:System.GC.KeepAlive%2A>, el objeto se considera de nuevo listo para la recolección suponiendo que no hay ninguna referencia administrada a él.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Esta regla hace algunas suposiciones que pueden dar lugar a falsos positivos. Puede suprimir de forma segura una advertencia de esta regla si:  
  
-   El finalizador no libera el contenido de la <xref:System.IntPtr> o <xref:System.UIntPtr> campo al que hace referencia el método.  
  
-   El método no pasa la <xref:System.IntPtr> o <xref:System.UIntPtr> campo a código no administrado.  
  
 Revise cuidadosamente otros mensajes antes de excluirlos. Esta regla detecta errores que son difíciles de reproducir y depurar.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, `BadMethod` no incluye una llamada a `GC.KeepAlive` y, por tanto, infringe la regla. `GoodMethod` contiene el código corregido.  
  
> [!NOTE]
>  En este ejemplo es pseudocódigo aunque el código se compila y se ejecuta, no se desencadena la advertencia porque no se creó o se libera un recurso no administrado.  
  
 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../code-quality/codesnippet/CSharp/ca2115-call-gc-keepalive-when-using-native-resources_1.cs)]  
  
## <a name="see-also"></a>Vea también  
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName>   
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>   
 [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)
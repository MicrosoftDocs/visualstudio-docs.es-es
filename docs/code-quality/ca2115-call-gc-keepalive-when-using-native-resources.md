---
title: "CA2115: Llamar a GC.KeepAlive cuando se utilicen recursos nativos | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CallGCKeepAliveWhenUsingNativeResources"
  - "CA2115"
helpviewer_keywords: 
  - "CA2115"
  - "CallGCKeepAliveWhenUsingNativeResources"
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2115: Llamar a GC.KeepAlive cuando se utilicen recursos nativos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallGCKeepAliveWhenUsingNativeResources|  
|Identificador de comprobación|CA2115|  
|Categoría|Microsoft.Security|  
|Cambio problemático|No|  
  
## Motivo  
 Un método declarado en un tipo con un finalizador hace referencia a <xref:System.IntPtr?displayProperty=fullName> o al campo <xref:System.UIntPtr?displayProperty=fullName>, pero no llama a <xref:System.GC.KeepAlive%2A?displayProperty=fullName>.  
  
## Descripción de la regla  
 La recolección de elementos no utilizados finaliza un objeto si no hay ninguna referencia más a él en el código administrado.  Las referencias no administradas a los objetos no evitan la recolección de elementos no utilizados.  Esta regla detecta errores que pueden haberse producido porque se finaliza un recurso no administrado mientras todavía se utiliza en código no administrado.  
  
 Esta regla supone que <xref:System.IntPtr> y el almacén de campos<xref:System.UIntPtr> apuntan a los recursos no administrados.  Puesto que el propósito de un finalizador es liberar recursos no administrados, la regla supone que el finalizador liberará el recurso no administrado al que apuntan los campos de puntero.  Esta regla también supone que el método hace referencia al campo de puntero para pasar el recurso no administrado al código no administrado.  
  
## Cómo corregir infracciones  
 Para corregir esta infracción de la regla, agregue al método una llamada a <xref:System.GC.KeepAlive%2A>, pasando una instancia actual \(`this` en C\# y C\+\+\) como el argumento.  Coloque la llamada después de la última línea de código donde el objeto se debe proteger de la recolección de elementos no utilizados.  Inmediatamente después de la llamada a <xref:System.GC.KeepAlive%2A>, el objeto se considera de nuevo listo para la recolección de elementos no utilizados suponiendo que no hay ninguna referencia administrada a él.  
  
## Cuándo suprimir advertencias  
 Esta regla hace algunas suposiciones que pueden dar lugar a falsos positivos.  Puede suprimir sin ningún riesgo una advertencia de esta regla si:  
  
-   El finalizador no libera el contenido de <xref:System.IntPtr> o el campo <xref:System.UIntPtr> al que hace referencia el método.  
  
-   El método no pasa <xref:System.IntPtr> ni el campo <xref:System.UIntPtr> al código no administrado.  
  
 Revise cuidadosamente otros mensajes antes de excluirlos.  Esta regla detecta errores que son difíciles de reproducir y depurar.  
  
## Ejemplo  
 En el siguiente ejemplo, `BadMethod` no se incluye una llamada a `GC.KeepAlive` y por consiguiente no infringe la regla.  `GoodMethod` contiene el código corregido.  
  
> [!NOTE]
>  El ejemplo es un seudocódigo aunque el código se compila y se ejecuta, la advertencia no se activa porque un recurso no administrado no se crea ni se libera.  
  
 [!code-cs[FxCop.Security.IntptrAndFinalize#1](../code-quality/codesnippet/CSharp/ca2115-call-gc-keepalive-when-using-native-resources_1.cs)]  
  
## Vea también  
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName>   
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>   
 [Patrón de Dispose](../Topic/Dispose%20Pattern.md)
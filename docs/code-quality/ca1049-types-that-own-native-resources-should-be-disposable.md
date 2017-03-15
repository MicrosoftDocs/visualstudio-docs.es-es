---
title: "CA1049: Los tipos que poseen recursos nativos deben ser descartables | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1049"
  - "TypesThatOwnNativeResourcesShouldBeDisposable"
helpviewer_keywords: 
  - "TypesThatOwnNativeResourcesShouldBeDisposable"
  - "CA1049"
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1049: Los tipos que poseen recursos nativos deben ser descartables
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|  
|Identificador de comprobación|CA1049|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un tipo hace referencia a un campo <xref:System.IntPtr?displayProperty=fullName>, un campo <xref:System.UIntPtr?displayProperty=fullName> o un campo <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>, pero no implementa <xref:System.IDisposable?displayProperty=fullName>.  
  
## Descripción de la regla  
 Esta regla supone que <xref:System.IntPtr>, <xref:System.UIntPtr> y el almacén de campos <xref:System.Runtime.InteropServices.HandleRef> apunta a los recursos no administrados.  Los tipos que se asignan a recursos no administrados deberían implementar <xref:System.IDisposable> para permitir que los llamadores liberen estos recursos a petición y reduzcan el período de duración de los objetos que contienen los recursos.  
  
 El modelo de diseño recomendado para limpiar los recursos no administrados es proporcionar un modo implícito y otro explícito para liberar esos recursos mediante el método <xref:System.Object.Finalize%2A?displayProperty=fullName> y el método <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> respectivamente.  El recolector de elementos no utilizados llama al método <xref:System.Object.Finalize%2A> de un objeto en algún momento indeterminado después de que el objeto se establezca como no alcanzable.  Después de llamar a <xref:System.Object.Finalize%2A>, es necesario que la recolección de elementos no utilizados libere el objeto.  El método <xref:System.IDisposable.Dispose%2A> permite que el llamador libere explícitamente recursos a petición, antes de que los recursos sean liberados si acaban en el recolector de elementos no utilizados.  Después que limpia los recursos no administrados, <xref:System.IDisposable.Dispose%2A> debe llamar al método <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> para permitir que el recolector de elementos no utilizados sepa que ya no es necesario llamar a <xref:System.Object.Finalize%2A>; esto evita que sea necesaria la recolección de elementos no utilizados y reduce el período de duración del objeto.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, implemente <xref:System.IDisposable>.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si el tipo no hace referencia a un recurso no administrado.  En caso contrario, no suprima ninguna advertencia de esta regla, porque si no se implementa <xref:System.IDisposable> puede hacer que los recursos no administrados queden no disponibles o infrautilizados.  
  
## Ejemplo  
 El ejemplo siguiente muestra un tipo que implementa <xref:System.IDisposable> para limpiar un recurso no administrado.  
  
 [!code-cs[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]  
  
## Reglas relacionadas  
 [CA2115: Llamar a GC.KeepAlive cuando se utilicen recursos nativos](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)  
  
 [CA1816: Llamar a GC.SuppressFinalize correctamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA2216: Los tipos descartables deben declarar el finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA1001: Los tipos que poseen campos descartables deben ser descartables](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)  
  
## Vea también  
 [Cleaning Up Unmanaged Resources](../Topic/Cleaning%20Up%20Unmanaged%20Resources.md)   
 [Patrón de Dispose](../Topic/Dispose%20Pattern.md)
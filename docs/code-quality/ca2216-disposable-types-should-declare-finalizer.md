---
title: "CA2216: Los tipos descartables deben declarar el finalizador | Microsoft Docs"
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
  - "DisposableTypesShouldDeclareFinalizer"
  - "CA2216"
helpviewer_keywords: 
  - "CA2216"
  - "DisposableTypesShouldDeclareFinalizer"
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2216: Los tipos descartables deben declarar el finalizador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposableTypesShouldDeclareFinalizer|  
|Identificador de comprobación|CA2216|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Un tipo que implementa <xref:System.IDisposable?displayProperty=fullName> y tiene campos que sugieren el uso de recursos no administrados, no implementa un finalizador descrito por <xref:System.Object.Finalize%2A?displayProperty=fullName>.  
  
## Descripción de la regla  
 Se crea informe relativo a una infracción de esta regla si el tipo disponible contiene campos de los tipos siguientes:  
  
-   <xref:System.IntPtr?displayProperty=fullName>  
  
-   <xref:System.UIntPtr?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, implemente un finalizador que llama a su método <xref:System.IDisposable.Dispose%2A>.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si el tipo no implementa <xref:System.IDisposable> con el propósito de liberar los recursos no administrados.  
  
## Ejemplo  
 El siguiente ejemplo muestra un tipo que infringe esta regla.  
  
 [!code-cs[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]  
  
## Reglas relacionadas  
 [CA2115: Llamar a GC.KeepAlive cuando se utilicen recursos nativos](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)  
  
 [CA1816: Llamar a GC.SuppressFinalize correctamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA1049: Los tipos que poseen recursos nativos deben ser descartables](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)  
  
## Vea también  
 <xref:System.IDisposable?displayProperty=fullName>   
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 [Patrón de Dispose](../Topic/Dispose%20Pattern.md)
---
title: "CA1816: Llamar a GC.SuppressFinalize correctamente | Microsoft Docs"
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
  - "CA1816"
  - "DisposeMethodsShouldCallSuppressFinalize"
helpviewer_keywords: 
  - "CA1816"
  - "DisposeMethodsShouldCallSuppressFinalize"
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1816: Llamar a GC.SuppressFinalize correctamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallGCSuppressFinalizeCorrectly|  
|Identificador de comprobación|CA1816|  
|Categoría|Microsoft.  Uso|  
|Cambio problemático|No|  
  
## Motivo  
  
-   Un método que es una implementación de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> no llama a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
-   Un método que no es una implementación de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> llama a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
-   Un método llama a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> y pasa algo distinto de esto \(Me en Visual Basic\).  
  
## Descripción de la regla  
 El método <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> permite a los usuarios liberar los recursos en cualquier momento antes de que el objeto se encuentre disponible para la recolección de elementos no utilizados.  Si se llama al método <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>, este método libera los recursos del objeto.  Esto hace la finalización innecesaria.  <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> debe llamar a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> para que el recolector de elementos no utilizados no llame al finalizador del objeto.  
  
 Para evitar que los tipos derivados con finalizadores tengan que implementar de nuevo [System.IDisposable](assetId:///System.IDisposable?qualifyHint=True&autoUpgrade=False) y tengan que llamarlo, los tipos no sellados deben llamar a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla:  
  
 Si el método es una implementación de <xref:System.IDisposable.Dispose%2A>, agregue una llamada a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 Si el método no es ninguna implementación de <xref:System.IDisposable.Dispose%2A>, quite la llamada a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> o muévala a la implementación <xref:System.IDisposable.Dispose%2A> del tipo.  
  
 Cambie todas las llamadas por <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> para pasar esto \(Me en Visual Basic\).  
  
## Cuándo suprimir advertencias  
 Únicamente debe suprimir una advertencia de esta regla si está utilizando de forma deliberada <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> para controlar la duración de otros objetos.  No suprima una advertencia de esta regla si una implementación de <xref:System.IDisposable.Dispose%2A> no llama a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  En esta situación, si se suprime la finalización erróneamente, se reduce el rendimiento y no se obtienen ventajas.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra un método que llama a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> incorrectamente.  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
 [!code-cs[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]  
  
## Ejemplo  
 En el ejemplo siguiente se muestra un método que llama a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> correctamente.  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
 [!code-cs[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]  
  
## Reglas relacionadas  
 [CA2215: Los métodos Dispose deben llamar a Dispose de clase base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA2216: Los tipos descartables deben declarar el finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
## Vea también  
 [Patrón de Dispose](../Topic/Dispose%20Pattern.md)
---
title: "CA2215: Los m&#233;todos Dispose deben llamar a Dispose de clase base | Microsoft Docs"
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
  - "CA2215"
  - "DisposeMethodsShouldCallBaseClassDispose"
  - "Dispose methods should call base class dispose"
helpviewer_keywords: 
  - "DisposeMethodsShouldCallBaseClassDispose"
  - "CA2215"
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2215: Los m&#233;todos Dispose deben llamar a Dispose de clase base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposeMethodsShouldCallBaseClassDispose|  
|Identificador de comprobación|CA2215|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Un tipo que implementa <xref:System.IDisposable?displayProperty=fullName> hereda de un tipo que también implementa <xref:System.IDisposable>.  El método <xref:System.IDisposable.Dispose%2A> del tipo heredado no llama al método <xref:System.IDisposable.Dispose%2A> del tipo primario.  
  
## Descripción de la regla  
 Si un tipo hereda de un tipo disponible, debe llamar al método <xref:System.IDisposable.Dispose%2A> del tipo base desde su propio método <xref:System.IDisposable.Dispose%2A>.  Llamar al método de tipo base Dispone asegura que se liberan los recursos creados por el tipo base.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, llame a `base`.<xref:System.IDisposable.Dispose%2A> desde su método <xref:System.IDisposable.Dispose%2A>.  
  
## Cuándo suprimir advertencias  
 Se puede suprimir de forma segura una advertencia de esta regla si la llamada a `base`.<xref:System.IDisposable.Dispose%2A> se produce en un nivel de llamada más profundo que el de las comprobaciones de la regla.  
  
## Ejemplo  
 El ejemplo siguiente muestra un tipo `TypeA` que implementa <xref:System.IDisposable>.  
  
 [!code-cs[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]  
  
## Ejemplo  
 El ejemplo siguiente muestra un tipo `TypeB` que hereda del tipo `TypeA` y llama correctamente a su método <xref:System.IDisposable.Dispose%2A>.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]  
  
## Vea también  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Patrón de Dispose](../Topic/Dispose%20Pattern.md)
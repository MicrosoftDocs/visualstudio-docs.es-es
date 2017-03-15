---
title: "CA2220: Los finalizadores deben llamar al finalizador de la clase base | Microsoft Docs"
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
  - "CA2220"
  - "FinalizersShouldCallBaseClassFinalizer"
helpviewer_keywords: 
  - "CA2220"
  - "FinalizersShouldCallBaseClassFinalizer"
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2220: Los finalizadores deben llamar al finalizador de la clase base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|FinalizersShouldCallBaseClassFinalizer|  
|Identificador de comprobación|CA2220|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Un tipo que reemplaza <xref:System.Object.Finalize%2A?displayProperty=fullName> no llama al método <xref:System.Object.Finalize%2A> en su clase base.  
  
## Descripción de la regla  
 La finalización se debe difundir a través de la jerarquía de herencia.  Para garantizar esto, los tipos deben llamar al método <xref:System.Object.Finalize%2A> de su clase base desde su propio método <xref:System.Object.Finalize%2A>.  El compilador de C\# agrega automáticamente la llamada al finalizador de clase base.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, llame al método <xref:System.Object.Finalize%2A> del tipo base desde su método <xref:System.Object.Finalize%2A>.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  Algunos compiladores que tienen como destino que el Common Language Runtime inserte una llamada al finalizador del tipo base dentro del lenguaje intermedio de Microsoft \(MSIL\).  Si se crea informe relacionado con una advertencia de esta regla, el compilador no inserta la llamada y debe agregarlo al código.  
  
## Ejemplo  
 El siguiente ejemplo de Visual Basic muestra un tipo `TypeB` que llama correctamente al método <xref:System.Object.Finalize%2A> en su clase base.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]  
  
## Vea también  
 [Patrón de Dispose](../Topic/Dispose%20Pattern.md)
---
title: "El m&#233;todo &#39;&lt;nombreDeM&#233;todo1&gt;&#39; no puede implementar el m&#233;todo parcial &#39;&lt;nombreDeM&#233;todo2&gt;&#39; porque &#39;&lt;nombreDeM&#233;todo3&gt;&#39; ya lo implementa | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31434"
  - "bc31434"
helpviewer_keywords: 
  - "BC31434"
ms.assetid: 61cba19e-db11-4a06-89d6-4244d411588c
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El m&#233;todo &#39;&lt;nombreDeM&#233;todo1&gt;&#39; no puede implementar el m&#233;todo parcial &#39;&lt;nombreDeM&#233;todo2&gt;&#39; porque &#39;&lt;nombreDeM&#233;todo3&gt;&#39; ya lo implementa
El método '\<nombreDeMétodo1\>' no puede implementar el método parcial '\<nombreDeMétodo2\>' porque '\<nombreDeMétodo3\>' ya lo implementa. Solo un método puede implementar un método parcial.  
  
 No es posible tener dos métodos parciales que implementan la misma declaración de método parcial. El código siguiente causa este error.  
  
```vb#  
Partial Class Product ' Declaration of the partial method. Partial Private Sub ValueChanged() End Sub End Class  
```  
  
```vb#  
Partial Class Product ' First implementation of the partial method. Private Sub ValueChanged() MsgBox(Value was changed to " & Me.Quantity) End Sub ' Second implementation of the partial method causes this error. 'Private Sub ValueChanged() '    Console.WriteLine("Quantity was changed to " & Me.Quantity) 'End Sub End Class  
```  
  
 **Identificador de error:** BC31434  
  
## Vea también  
 [Métodos Partial](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)
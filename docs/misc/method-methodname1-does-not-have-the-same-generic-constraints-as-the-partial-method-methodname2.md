---
title: "El m&#233;todo &#39;&lt;nombreM&#233;todo1&gt;&#39; no tiene las mismas restricciones gen&#233;ricas que el m&#233;todo parcial &#39;&lt;nombreM&#233;todo2&gt;&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31438"
  - "vbc31438"
helpviewer_keywords: 
  - "BC31438"
ms.assetid: ea092f0c-661b-49db-80c1-76401fc8bc0b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El m&#233;todo &#39;&lt;nombreM&#233;todo1&gt;&#39; no tiene las mismas restricciones gen&#233;ricas que el m&#233;todo parcial &#39;&lt;nombreM&#233;todo2&gt;&#39;.
Ha definido una implementación de método parcial que tiene restricciones genéricas que difieren de las restricciones en la declaración de método parcial. En el código siguiente, se ilustra el error.  
  
```vb#  
Partial Class Class1 Partial Private Sub Test(Of T As Class)(ByVal arg As T) End Sub End Class Partial Class Class1 '' The error occurs here, for Test. 'Private Sub Test(Of T As Structure)(ByVal arg As T) 'End Sub End Class  
```  
  
 **Identificador de error:** BC31438  
  
## Vea también  
 [Métodos Partial](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)   
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)
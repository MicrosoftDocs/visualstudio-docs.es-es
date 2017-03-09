---
title: "El nombre de par&#225;metro &#39;&lt;nombreDePar&#225;metro1&gt;&#39; no coincide con el nombre del par&#225;metro correspondiente, &#39;nombreDePar&#225;metro2&#39;, definido en la declaraci&#243;n de m&#233;todo parcial &#39;&lt;nombreDeM&#233;todo&gt;&#39;. | Microsoft Docs"
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
  - "vbc31442"
  - "bc31442"
helpviewer_keywords: 
  - "BC31442"
ms.assetid: 7f097bb2-071a-42ec-b7af-40da04f602f2
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El nombre de par&#225;metro &#39;&lt;nombreDePar&#225;metro1&gt;&#39; no coincide con el nombre del par&#225;metro correspondiente, &#39;nombreDePar&#225;metro2&#39;, definido en la declaraci&#243;n de m&#233;todo parcial &#39;&lt;nombreDeM&#233;todo&gt;&#39;.
Cuando se proporcionan parámetros para la declaración y la implementación de un método parcial, los nombres de los parámetros correspondientes deben coincidir. Por ejemplo, el código siguiente causa este error.  
  
```vb#  
Partial Class Product  
  
    ' Declaration of the partial method.  
    Partial Private Sub valueChanged(ByVal newVal As Integer)  
    End Sub  
End Class  
```  
  
```vb#  
Partial Class Product  
  
    ' Implementation of the partial method. This error is  
    ' reported for parameter val.  
    ' Private Sub valueChanged(ByVal val As Integer)  
    '     MsgBox(Value was changed to " & Me.Quantity)  
    ' End Sub  
  
End Class  
```  
  
 **Identificador de error:** BC31442  
  
### Para corregir este error  
  
1.  Cambie el nombre del parámetro o los nombres de la declaración o la implementación para que los parámetros correspondientes tengan el mismo nombre.  
  
## Vea también  
 [Métodos Partial](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)
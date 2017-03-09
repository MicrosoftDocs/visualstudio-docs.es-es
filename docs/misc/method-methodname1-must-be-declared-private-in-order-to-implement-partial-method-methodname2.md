---
title: "El m&#233;todo &#39;&lt;nombreDeM&#233;todo1&gt;&#39; se debe declarar como &#39;Private&#39; para poder implementar el m&#233;todo parcial &#39;&lt;nombreDeM&#233;todo2&gt;&#39; | Microsoft Docs"
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
  - "vbc31441"
  - "bc31441"
helpviewer_keywords: 
  - "BC31441"
ms.assetid: 4d8d19ad-0c3b-4eba-ada8-2cfa6ae795c4
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El m&#233;todo &#39;&lt;nombreDeM&#233;todo1&gt;&#39; se debe declarar como &#39;Private&#39; para poder implementar el m&#233;todo parcial &#39;&lt;nombreDeM&#233;todo2&gt;&#39;
La implementación de un método parcial debe declararse `Private`. Por ejemplo, el código siguiente causa este error.  
  
```vb#  
Partial Class Product ' Declaration of the partial method. Partial Private Sub valueChanged() End Sub End Class  
```  
  
```vb#  
Partial Class Product ' Implementation of the partial method, with Private missing, ' causes this error. 'Sub valueChanged() '    MsgBox(Value was changed to " & Me.Quantity) 'End Sub End Class  
```  
  
 **Identificador de error:** BC31441  
  
### Para corregir este error  
  
1.  Use el modificador de acceso `Private` en la implementación del método parcial, tal como se muestra en el ejemplo siguiente.  
  
    ```vb#  
    Private Sub valueChanged() MsgBox(Value was changed to " & Me.Quantity) End Sub  
    ```  
  
## Vea también  
 [Métodos Partial](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)   
 [Niveles de acceso en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)
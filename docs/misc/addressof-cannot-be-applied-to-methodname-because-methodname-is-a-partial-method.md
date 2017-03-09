---
title: "No se puede aplicar &#39;AddressOf&#39; en &#39;nombreM&#233;todo&#39; porque &#39;nombreM&#233;todo&#39; es un m&#233;todo parcial. | Microsoft Docs"
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
  - "vbc31440"
  - "bc31440"
helpviewer_keywords: 
  - "BC31440"
ms.assetid: 924dbada-3e0a-4004-a3ae-a209b7c3d1fa
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede aplicar &#39;AddressOf&#39; en &#39;nombreM&#233;todo&#39; porque &#39;nombreM&#233;todo&#39; es un m&#233;todo parcial.
Se ha pasado un método parcial al operador `AddressOf`. Los métodos parciales son valores no válidos para el operador `AddressOf`.  
  
 **Identificador de error:** BC31440  
  
### Para corregir este error  
  
1.  Agregue un método de implementación para el método parcial. El método de implementación es un valor válido para el operador `AddressOf`. En el ejemplo siguiente se muestra una firma de método parcial y su implementación.  
  
    ```vb#  
    ' Definition of the partial method signature.  
    Partial Private Sub OnNameChanged()  
        ' The body of the signature is empty.  
    End Sub  
  
    ' Implementation of the partial method.  
    Private Sub OnNameChanged()  
        MsgBox("Name was changed to " & Me.Name)  
    End Sub  
    ```  
  
## Vea también  
 [AddressOf \(Operador\)](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [Métodos Partial](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)
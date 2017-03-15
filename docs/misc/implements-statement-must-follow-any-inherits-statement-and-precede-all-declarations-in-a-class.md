---
title: "La instrucci&#243;n &#39;Implements&#39; debe ir detr&#225;s de cualquier instrucci&#243;n &#39;Inherits&#39; y delante de todas las declaraciones de una clase | Microsoft Docs"
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
  - "bc31053"
  - "vbc31053"
helpviewer_keywords: 
  - "BC31053"
ms.assetid: 8036a1a1-7e31-4c49-b74b-01601a548f3e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La instrucci&#243;n &#39;Implements&#39; debe ir detr&#225;s de cualquier instrucci&#243;n &#39;Inherits&#39; y delante de todas las declaraciones de una clase
Se encontró una instrucción `Implements` en una ubicación no válida.  
  
 **Identificador de error:** BC31053  
  
### Para corregir este error  
  
-   Coloque las instrucciones `Implements` inmediatamente después de todas las instrucciones `Inherits`, pero antes de todas la declaraciones. Por ejemplo:  
  
    ```  
    Class Derived Inherits Base Implements One Sub SubOne() Implements One.Method1 ' Add code to implement the method. End Sub End Class  
    ```  
  
## Vea también  
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)
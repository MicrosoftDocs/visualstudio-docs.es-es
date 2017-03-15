---
title: "Las instrucciones &#39;ReDim&#39; ya no se pueden usar para declarar variables de matriz. | Microsoft Docs"
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
  - "bc30811"
  - "vbc30811"
helpviewer_keywords: 
  - "BC30811"
ms.assetid: 9227a06e-a997-4b16-9977-19e2bce9035b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las instrucciones &#39;ReDim&#39; ya no se pueden usar para declarar variables de matriz.
`ReDim` solo puede usarse para cambiar el tamaño de una matriz existente.  
  
 **Identificador de error:** BC30811  
  
### Para corregir este error  
  
-   Especifique el tamaño de las matrices al declararlas; por ejemplo:  
  
    ```  
    Dim X(20) As Integer  
    ```  
  
## Vea también  
 [Resumen de matrices](/dotnet/visual-basic/language-reference/keywords/arrays-summary)   
 [ReDim \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [ReDim Statement Changes in Visual Basic](http://msdn.microsoft.com/es-es/b4da14db-ff23-490f-b3c6-d7ae1b649532)
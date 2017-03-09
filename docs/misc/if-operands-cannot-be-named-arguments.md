---
title: "Los operandos &#39;If&#39; no pueden ser argumentos con nombre | Microsoft Docs"
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
  - "bc33105"
  - "vbc33105"
helpviewer_keywords: 
  - "BC33105"
ms.assetid: 596baeb6-a44f-4d92-beb7-06624b60c00d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los operandos &#39;If&#39; no pueden ser argumentos con nombre
No se pueden usar argumentos con nombre en los operandos del operador `If`. El ejemplo siguiente causa este error:  
  
```  
Dim i As Integer Dim result As String ' Not valid. ' result = (If(i > 0, TruePart:="positive", FalsePart:="not positive")  
```  
  
 Esto difiere de la función `IIf`, que permite argumentos con nombre, como se muestra en el código siguiente:  
  
```  
' Valid. IIf(i > 0, TruePart:="positive", FalsePart:="not positive")  
```  
  
 **Identificador de error:** BC33105  
  
### Para corregir este error  
  
-   Quitar las asignaciones de nombre de los operandos, como se muestra en el código siguiente.  
  
    ```  
    result = If(i > 0, "positive", "not positive")  
    ```  
  
## Vea también  
 [If \(operador\)](/dotnet/visual-basic/language-reference/operators/if-operator)   
 [Pasar argumentos por posición o por nombre](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)
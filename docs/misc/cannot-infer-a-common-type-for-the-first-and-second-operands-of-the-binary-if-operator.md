---
title: "No se puede inferir un tipo com&#250;n para los operandos primero y segundo del operador &#39;If&#39; binario | Microsoft Docs"
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
  - "vbc33110"
  - "bc33110"
helpviewer_keywords: 
  - "BC33110"
ms.assetid: f46873aa-f6cd-4cc9-9e8e-e668bddf0980
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede inferir un tipo com&#250;n para los operandos primero y segundo del operador &#39;If&#39; binario
No se puede inferir un tipo común para los operandos primero y segundo del operador 'If' binario. Uno debe tener una conversión de ampliación al otro.  
  
 El operador `If` binario requiere que exista una conversión de ampliación entre uno de los argumentos y el otro. Por ejemplo, como no existe una conversión de ampliación en ninguna dirección entre `Integer` y `String`, el código siguiente provoca este error.  
  
```vb#  
Dim first? As Integer  
Dim second As String = "First is Nothing"  
'' Not valid.  
' Console.WriteLine(If(first, second))  
```  
  
 **Identificador de error:** BC33110  
  
### Para corregir este error  
  
-   Proporcione una conversión explícita para uno de los operandos, si es posible en el código:  
  
    ```  
    Console.WriteLine(If(first, CInt(second)))   
    ```  
  
-   Vuelva a escribir el código mediante una construcción condicional diferente.  
  
    ```  
    If first IsNot Nothing Then  
        Console.WriteLine(first)  
    Else  
        Console.WriteLine(second)  
    End If  
    ```  
  
## Vea también  
 [If \(operador\)](/dotnet/visual-basic/language-reference/operators/if-operator)   
 [Conversiones de ampliación y de restricción](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [If...Then...Else \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)
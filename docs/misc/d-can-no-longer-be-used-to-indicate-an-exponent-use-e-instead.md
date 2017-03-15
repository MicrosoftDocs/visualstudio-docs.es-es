---
title: "&#39;D&#39; ya no se puede usar para indicar un exponente, use &#39;E&#39; en su lugar | Microsoft Docs"
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
  - "vbc30827"
  - "bc30827"
helpviewer_keywords: 
  - "BC30827"
ms.assetid: 577f8c0b-9e8a-433f-b504-9ddaa936c250
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;D&#39; ya no se puede usar para indicar un exponente, use &#39;E&#39; en su lugar
El carácter 'D' no se puede usar para indicar exponenciación.  
  
 **Identificador de error:** BC30827  
  
### Para corregir este error  
  
-   Use el operador `^` o los caracteres `E+` para indicar que un exponente está presente. Por ejemplo:  
  
    ```  
    Const Mole = 6.02E+23 ' Same as 6.02D23 Const Mole2 = 6.02 * 10 ^ 23 ' Same as 6.02D23  
    ```  
  
## Vea también  
 [^ \(Operador\)](/dotnet/visual-basic/language-reference/operators/exponentiation-operator)   
 [Tipos de datos numéricos](/dotnet/visual-basic/programming-guide/language-features/data-types/numeric-data-types)
---
title: "Option Strict On requiere que los par&#225;metros de la expresi&#243;n lambda se declaren con una cl&#225;usula &#39;As&#39; si no se puede inferir su tipo. | Microsoft Docs"
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
  - "bc36642"
  - "vbc36642"
helpviewer_keywords: 
  - "BC36642"
ms.assetid: 2aaa62b8-49c9-4ae8-b0f5-08e3f0b5ad10
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On requiere que los par&#225;metros de la expresi&#243;n lambda se declaren con una cl&#225;usula &#39;As&#39; si no se puede inferir su tipo.
Se ha declarado un parámetro en una expresión lambda sin usar una cláusula `As`, con `Option Strict` activado.  
  
```  
' Not valid when Option Strict is on. ' Dim increment1 = Function (n) n + 1  
```  
  
 La declaración anterior es válida si se puede deducir el tipo de `n`. Por ejemplo, si va a asignar la expresión lambda anterior a un delegado de función, `Del`:  
  
```  
Delegate Function Del(ByVal p As Integer) As Integer  
```  
  
 Ahora el tipo de `n` puede deducirse a partir del parámetro `p`:  
  
```  
Dim increment2 as Del = Function(n) n + 1  
```  
  
 **Identificador de error:** BC36642  
  
### Para corregir este error  
  
-   Agregar una cláusula `As` a la declaración de parámetro:  
  
    ```  
    Dim increment3 = Function (n As Integer) n + 1  
    ```  
  
## Vea también  
 [Expresiones lambda](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)
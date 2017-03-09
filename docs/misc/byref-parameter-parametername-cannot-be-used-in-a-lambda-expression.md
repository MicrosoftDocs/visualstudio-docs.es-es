---
title: "El par&#225;metro &#39;&lt;nombreDePar&#225;metro&gt;&#39; de &#39;ByRef&#39; no se puede usar en una expresi&#243;n lambda | Microsoft Docs"
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
  - "bc36639"
  - "vbc36639"
helpviewer_keywords: 
  - "BC36639"
ms.assetid: 5913f9b6-2929-4c05-8dd1-00b10fcd5a83
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El par&#225;metro &#39;&lt;nombreDePar&#225;metro&gt;&#39; de &#39;ByRef&#39; no se puede usar en una expresi&#243;n lambda
Una expresión lambda se declarada dentro de una declaración `Sub` o una función no puede usar cualquier parámetros `ByRef` de dicha `Sub` o función. Por ejemplo, el siguiente código provocará este error porque el parámetro `n` de `ByRef` se usa en la expresión lambda.  
  
```  
'' Not valid.   
'Sub ExampleSub(ByRef n As Integer)  
  
'    Dim lambda = Function(p As Integer) p + n  
  
'End Sub  
```  
  
 **Identificador de error:** BC36639  
  
### Para corregir este error  
  
-   Asigne el parámetro de `ByRef` a una variable local y use la variable local en la expresión lambda, como se muestra en el código siguiente:  
  
    ```  
    Sub ExampleSub(ByRef n As Integer)  
  
        Dim temp = n  
        Dim lambda = Function(p As Integer) p + temp  
  
    End Sub  
    ```  
  
## Vea también  
 [Expresiones lambda](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)
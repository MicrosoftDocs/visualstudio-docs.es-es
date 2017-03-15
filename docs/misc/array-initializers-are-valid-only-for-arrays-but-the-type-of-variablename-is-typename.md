---
title: "Los inicializadores de matrices solo son v&#225;lidos para las matrices, pero el tipo de &#39;&lt;variablename&gt;&#39; es &#39;&lt;typename&gt;&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30679"
  - "vbc30679"
helpviewer_keywords: 
  - "BC30679"
ms.assetid: 3cf34882-7a58-4074-8ebb-52e58199a506
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los inicializadores de matrices solo son v&#225;lidos para las matrices, pero el tipo de &#39;&lt;variablename&gt;&#39; es &#39;&lt;typename&gt;&#39;.
Se intentó inicializar una variable que no es de matriz con una lista de valores.  
  
 **Identificador de error:** BC30679  
  
### Para corregir este error  
  
-   Declare e inicialice la variable como una matriz. Por ejemplo:  
  
     `Dim intarray As Integer() = {1, 5, 9}`  
  
-   Inicialice la variable como un solo valor; por ejemplo:  
  
     `Dim intvalue As Integer = 1`  
  
## Vea también  
 [Dim \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Declaración de variable](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)   
 [Matrices](/dotnet/visual-basic/programming-guide/language-features/arrays/index)
---
title: "Option Strict On requiere que todos los par&#225;metros del m&#233;todo tengan una cl&#225;usula &#39;As&#39; | Microsoft Docs"
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
  - "vbc30211"
  - "bc30211"
helpviewer_keywords: 
  - "BC30211"
ms.assetid: 855795ce-8499-4525-a1de-cbb8ba364cd7
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On requiere que todos los par&#225;metros del m&#233;todo tengan una cl&#225;usula &#39;As&#39;
Un método contiene un parámetro sin una cláusula `As`. Si `Option Strict` está activado, cada variable, propiedad, argumento de procedimiento y valor devuelto de función debe declararse con una cláusula `As` para especificar su tipo de datos; por ejemplo, `Sub GetData(ByVal filter As String)`.  
  
 **Identificador de error:** BC30211  
  
### Para corregir este error  
  
-   Compruebe si la palabra clave `As` está mal escrita.  
  
-   Facilite una cláusula `As` para la variable declarada o desactive `Option Strict`.  
  
## Vea también  
 [Option Strict \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Sub \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/sub-statement)   
 [Function \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/function-statement)
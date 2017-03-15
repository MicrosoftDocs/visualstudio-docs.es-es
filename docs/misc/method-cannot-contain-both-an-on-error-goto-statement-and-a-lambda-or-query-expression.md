---
title: "El m&#233;todo no puede contener una instrucci&#243;n &#39;On Error GoTo&#39; y una expresi&#243;n lambda o de consulta | Microsoft Docs"
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
  - "bc36595"
  - "vbc36595"
helpviewer_keywords: 
  - "BC36595"
ms.assetid: 4e7cc11e-f53d-4481-afb4-653a81d54483
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El m&#233;todo no puede contener una instrucci&#243;n &#39;On Error GoTo&#39; y una expresi&#243;n lambda o de consulta
Un método contiene una instrucción `On Error Goto` y una expresión lambda o una consulta LINQ. No puede incluir una instrucción `On Error Goto` con una expresión lambda o una consulta LINQ en un método.  
  
 **Identificador de error:** BC36595  
  
### Para corregir este error  
  
1.  Reemplace el código de control de excepciones que usa la instrucción `On Error Goto` por una instrucción `Try...Catch`.  
  
## Vea también  
 [Introducción al control de excepciones \(Visual Basic\)](http://msdn.microsoft.com/es-es/9792f16a-0cd2-40bd-ace2-f7a4344c0e52)   
 [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Introducción a LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [Expresiones lambda](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [On Error \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/on-error-statement)
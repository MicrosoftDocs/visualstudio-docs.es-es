---
title: "Error del compilador CS1002 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1002"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1002"
ms.assetid: 659b7abf-9311-40c9-9594-5372464c6148
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1002
Se esperaba ;  
  
 El compilador detectó que falta un punto y coma. Se requiere un punto y coma al final de cada una de las instrucciones de C\#. Una instrucción puede abarcar más de una línea.  
  
 El ejemplo siguiente genera la advertencia CS1002:  
  
```  
// CS1002.cs namespace x { abstract public class clx { int i   // CS1002, missing semicolon public static int Main() { return 0; } } }  
```  
  
## Vea también  
 [Instrucciones](/dotnet/csharp/programming-guide/statements-expressions-operators/statements)
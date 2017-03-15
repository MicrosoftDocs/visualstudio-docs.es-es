---
title: "Error del compilador CS1515 | Microsoft Docs"
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
  - "CS1515"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1515"
ms.assetid: 17d9dbbe-14a0-4c80-a942-82fa6ec2b0b0
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1515
Se esperaba 'in'  
  
 En una instrucción [foreach, in](/dotnet/csharp/language-reference/keywords/foreach-in), falta la parte "in".  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1515:  
  
```  
using System; class Driver { static void Main() { int[] arr = new int[] {1, 2, 3}; // try the following line instead // foreach (int x in arr) foreach (int x arr)      // CS1515, "in" is missing { Console.WriteLine(x); } } }  
```
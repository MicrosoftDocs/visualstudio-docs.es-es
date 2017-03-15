---
title: "Error del compilador CS0020 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0020"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0020"
ms.assetid: 7a54db39-6530-4e34-aa17-a90f85223d08
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0020
División entre constante cero  
  
 Una expresión usa un valor literal \(no variable\) de cero en el denominador de una operación de división. División por cero no está definida y, por tanto, no es válida.  
  
 El ejemplo siguiente genera la advertencia CS0020:  
  
```  
// CS0020.cs namespace x { public class b { public static void Main() { 1 / 0;   // CS0020 } } }  
```  
  
## Vea también  
 [Operadores](/dotnet/csharp/programming-guide/statements-expressions-operators/operators)
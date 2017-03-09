---
title: "Error del compilador CS0568 | Microsoft Docs"
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
  - "CS0568"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0568"
ms.assetid: dc9e1263-f58d-4c95-9165-27ba7757bc7b
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0568
Los structs no pueden contener constructores explícitos sin parámetros  
  
 Cada [struct](/dotnet/csharp/language-reference/keywords/struct) ya tiene un constructor predeterminado que inicializa el objeto a cero. Por lo tanto, los constructores que se pueden crear para un struct deben tener uno o varios parámetros.  
  
 El ejemplo siguiente genera la advertencia CS0568:  
  
```  
// CS0568.cs public struct ClassY { public int field1; public ClassY(){}   // CS0568, cannot have no param constructor // Try following instead: // public ClassY(int i) // { //    field1 = i; // } } public class ClassX { public static void Main() { } }  
```
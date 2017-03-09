---
title: "Error del compilador CS0128 | Microsoft Docs"
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
  - "CS0128"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0128"
ms.assetid: 35db9025-2bed-437f-a78a-f2862766bde2
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0128
Ya se ha definido una variable local denominada 'variable' en este ámbito  
  
 El compilador detectó declaraciones de dos variables locales con el mismo nombre. Para obtener más información, consulta [Métodos](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
 El ejemplo siguiente genera la advertencia CS0128:  
  
```  
// CS0128.cs namespace MyNamespace { public class MyClass { public static void Main() { char i; int i;   // CS0128 } } }  
```
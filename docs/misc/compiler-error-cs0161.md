---
title: "Error del compilador CS0161 | Microsoft Docs"
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
  - "CS0161"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0161"
ms.assetid: c2731a6c-0285-4558-9e62-a7fd480ab0cf
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0161
'method': no todas las rutas de código devuelven un valor  
  
 Un método que devuelve un valor debe tener una instrucción `return` en todas las rutas de código. Para obtener más información, consulta [Métodos](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
 El ejemplo siguiente genera la advertencia CS0161:  
  
```  
// CS0161.cs public class Test { public static int Main() // CS0161 { int i = 10; if (i < 10) { return i; } else { // uncomment the following line to resolve // return 1; } } }  
```
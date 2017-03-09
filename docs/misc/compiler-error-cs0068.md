---
title: "Error del compilador CS0068 | Microsoft Docs"
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
  - "CS0068"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0068"
ms.assetid: 9c9ac915-e12f-4ceb-8eb0-806790f11a09
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0068
'evento': el evento de una interfaz no puede tener un inicializador  
  
 Un evento de una interfaz no puede tener un inicializador. Para obtener más información, consulte [Interfaces](/dotnet/csharp/programming-guide/interfaces/index).  
  
 El ejemplo siguiente genera la advertencia CS0068:  
  
```  
// CS0068.cs delegate void MyDelegate(); interface I { event MyDelegate d = new MyDelegate(M.f);   // CS0068 // try the following line instead // event MyDelegate d2; } class M { event MyDelegate d = new MyDelegate(M.f); public static void f() { } public static void Main() { } }  
```
---
title: "Error del compilador CS0066 | Microsoft Docs"
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
  - "CS0066"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0066"
ms.assetid: 9b50b49b-78b8-4562-8839-d59e5edbec6b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0066
'evento': el evento debe ser de tipo delegado  
  
 La palabra clave event requiere un tipo [delegate](/dotnet/csharp/language-reference/keywords/delegate). Para obtener más información, vea [Eventos](/dotnet/csharp/programming-guide/events/index) y [Delegados](/dotnet/csharp/programming-guide/delegates/index).  
  
 El ejemplo siguiente genera la advertencia CS0066:  
  
```  
// CS0066.cs using System; public class EventHandler { } // to fix the error, remove the event declaration and the // EventHandler class declaration, and uncomment the following line // public delegate void EventHandler(); public class a { public event EventHandler Click;   // CS0066 private void TestMethod() { if (Click != null) Click(); } public static void Main() { } }  
```
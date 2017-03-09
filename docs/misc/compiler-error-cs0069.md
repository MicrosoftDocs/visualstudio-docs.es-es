---
title: "Error del compilador CS0069 | Microsoft Docs"
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
  - "CS0069"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0069"
ms.assetid: a1b32906-7773-47c6-8515-162a201a9be5
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0069
Un evento de una interfaz no puede tener los descriptores de acceso add y remove  
  
 No se pueden definir funciones de descriptor de acceso de un evento en una [interfaz](/dotnet/csharp/language-reference/keywords/interface). Para obtener más información, consulte [Eventos](/dotnet/csharp/programming-guide/events/index) y [Interfaces](/dotnet/csharp/programming-guide/interfaces/index).  
  
 El ejemplo siguiente genera la advertencia CS0069:  
  
```  
// CS0069.cs // compile with: /target:library public delegate void EventHandler(); public interface a { event EventHandler Click { remove {} }   // CS0069 event EventHandler Click2;   // OK }  
```
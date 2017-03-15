---
title: "Error del compilador CS0245 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0245"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0245"
ms.assetid: 3f2beb2f-a510-4568-9d11-bb1f65066acd
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0245
Los destructores y object.Finalize no se pueden llamar directamente. Considere llamar a IDisposable.Dispose si está disponible.  
  
 Para obtener más información, consulte [Fundamentos de programación para la recolección de elementos no utilizados](../Topic/Garbage%20Collection.md) y [Destructores](/dotnet/csharp/programming-guide/classes-and-structs/destructors).  
  
 El ejemplo siguiente genera la advertencia CS0245:  
  
```  
// CS0245.cs using System; using System.Collections; class MyClass // : IDisposable { /* public void Dispose() { // cleanup code goes here } */ void m() { this.Finalize();   // CS0245 // this.Dispose(); } public static void Main() { } }  
```
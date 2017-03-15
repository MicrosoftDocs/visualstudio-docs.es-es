---
title: "Error del compilador CS0185 | Microsoft Docs"
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
  - "CS0185"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0185"
ms.assetid: d6546e10-0af3-4860-8e6f-2da7dbeb3d28
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0185
'type' no es el tipo de referencia que requiere la instrucción lock  
  
 La instrucción [lock](/dotnet/csharp/language-reference/keywords/lock-statement) solo puede evaluar tipos de referencia. Para obtener más información, consulte [Sincronización de subprocesos](../Topic/Thread%20Synchronization%20\(C%23%20and%20Visual%20Basic\).md) y [Tipos de referencia](/dotnet/csharp/language-reference/keywords/reference-types).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0185:  
  
```  
// CS0185.cs public class MainClass { public static void Main () { lock (1)   // CS0185 // try the following lines instead // MainClass x = new MainClass(); // lock(x) { } } }  
```
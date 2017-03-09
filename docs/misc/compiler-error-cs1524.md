---
title: "Error del compilador CS1524 | Microsoft Docs"
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
  - "CS1524"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1524"
ms.assetid: a7b80bbc-a2de-4718-b0f0-4c9526726525
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1524
Se esperaba catch o finally  
  
 Un bloque `try` debe ir seguido de un bloque `catch` o `finally`.  
  
 Para más información sobre excepciones, vea [Instrucciones para el control de excepciones](/dotnet/csharp/language-reference/keywords/exception-handling-statements).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1524:  
  
```  
// CS1524.cs class x { public static void Main() { try { // Code here } catch { } try { // Code here } finally { } try { // Code here } }     // CS1524, missing catch or finally }  
```
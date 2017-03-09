---
title: "Error del compilador CS1655 | Microsoft Docs"
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
  - "CS1655"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1655"
ms.assetid: 041e9daa-c026-494f-b086-0db9a23c969b
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1655
No se pueden pasar los campos de 'variable' como argumentos out o ref porque es 'readonly variable type'  
  
 Este error se produce si intenta pasar un miembro de una variable [foreach](/dotnet/csharp/language-reference/keywords/foreach-in), una variable [using](/dotnet/csharp/language-reference/keywords/using-statement) o una variable [fixed](/dotnet/csharp/language-reference/keywords/fixed-statement) a una función como un parámetro ref o out. Como estas variables se consideran de solo lectura en estos contextos, esto no está permitido.  
  
 El ejemplo siguiente genera la advertencia CS1655:  
  
```  
// CS1655.cs struct S { public int i; } class CMain { static void f(ref int iref) { } public static void Main() { S[] sa = new S[10]; foreach(S s in sa) { CMain.f(ref s.i);  // CS1655 } } }  
```
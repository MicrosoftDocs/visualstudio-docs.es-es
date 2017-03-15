---
title: "Error del compilador CS0502 | Microsoft Docs"
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
  - "CS0502"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0502"
ms.assetid: 6cd6deda-73a1-42d8-893b-45a685e63380
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0502
'member' no puede ser abstract y sealed  
  
 Un miembro de clase no puede ser [abstract](/dotnet/csharp/language-reference/keywords/abstract) y [sealed](/dotnet/csharp/language-reference/keywords/sealed).  
  
 El ejemplo siguiente genera la advertencia CS0502:  
  
```  
// CS0502.cs public class B { abstract public void F(); } public class C : B { abstract sealed override public void F()   // CS0502 { } } public class CMain { public static void Main() { } }  
```
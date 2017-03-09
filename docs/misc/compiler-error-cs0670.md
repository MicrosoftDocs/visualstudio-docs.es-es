---
title: "Error del compilador CS0670 | Microsoft Docs"
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
  - "CS0670"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0670"
ms.assetid: 59379171-284f-4d55-8741-af6a97879abc
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0670
El campo no puede tener un tipo void  
  
 Se declaró un campo de tipo [void](/dotnet/csharp/language-reference/keywords/void).  
  
 El ejemplo siguiente genera la advertencia CS0670:  
  
```  
// CS0670.cs class C { void f;   // CS0670 // try the following line instead // public int f; public static void Main() { C myc = new C(); myc.f = 0; } }  
```
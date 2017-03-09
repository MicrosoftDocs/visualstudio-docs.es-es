---
title: "Error del compilador CS0239 | Microsoft Docs"
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
  - "CS0239"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0239"
ms.assetid: 2e07bbc2-03a9-44b2-b321-477ca95fff8c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0239
'miembro': no se puede invalidar el miembro heredado 'miembro heredado' porque es de tipo sealed  
  
 Un miembro no puede invalidar \([override](/dotnet/csharp/language-reference/keywords/override)\) un miembro heredado [sealed](/dotnet/csharp/language-reference/keywords/sealed). Para obtener más información, consulte [Checked y unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked).  
  
 El ejemplo siguiente genera la advertencia CS0239:  
  
```  
// CS0239.cs abstract class MyClass { public abstract void f(); } class MyClass2 : MyClass { public static void Main() { } public override sealed void f() { } } class MyClass3 : MyClass2 { public override void f()   // CS0239 // Try the following definition instead: // public new void f() { } }  
```
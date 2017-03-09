---
title: "Error del compilador CS0113 | Microsoft Docs"
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
  - "CS0113"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0113"
ms.assetid: 43c5c0b7-67c0-45c1-8363-21c844c094f3
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0113
Un miembro 'function' marcado como override no se puede marcar como new o virtual.  
  
 Es mutuamente excluyente marcar un método con las palabras clave [new](/dotnet/csharp/language-reference/keywords/new) y [override](/dotnet/csharp/language-reference/keywords/override).  
  
 El ejemplo siguiente genera la advertencia CS0113:  
  
```  
// CS0113.cs namespace MyNamespace { abstract public class MyClass { public abstract void Foo(); } public class MyClass2 : MyClass { override new public void Foo()   // CS0113, remove new keyword { } public static int Main() { return 0; } } }  
```
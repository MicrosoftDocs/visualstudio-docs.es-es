---
title: "Error del compilador CS0060 | Microsoft Docs"
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
  - "CS0060"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0060"
ms.assetid: ae6d4fb7-5ff9-4883-82c3-f55b190f439a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0060
Incoherencia de accesibilidad: la clase base 'class1' es menos accesible que la clase 'class2'.  
  
 La accesibilidad de la clase debe ser coherente entre la clase base y la clase heredada.  
  
 El ejemplo siguiente genera la advertencia CS0060:  
  
```  
// CS0060.cs class MyClass // try the following line instead // public class MyClass { } public class MyClass2 : MyClass   // CS0060 { public static void Main() { } }  
```  
  
## Vea también  
 [Modificadores de acceso](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers)
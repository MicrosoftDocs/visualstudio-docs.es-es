---
title: "Advertencia del compilador (nivel 3) CS0219 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0219"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0219"
ms.assetid: 7945c497-4bfa-4695-9166-815a2ad0c8e7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 3) CS0219
La variable 'variable' está asignada, pero su valor nunca se usa.  
  
 El compilador emite una advertencia de nivel tres al declarar y asignar una variable, pero sin usarla.  
  
 El ejemplo siguiente genera la advertencia CS0219:  
  
```  
// CS0219.cs // compile with: /W:3 public class MyClass { public static void Main() { int a = 0;   // CS0219 } }  
```
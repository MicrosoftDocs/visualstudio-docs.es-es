---
title: "Error del compilador CS2017 | Microsoft Docs"
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
  - "CS2017"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2017"
ms.assetid: 16fd0c3b-018f-4734-809d-8d98d05a254c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS2017
No se puede especificar \/main si se compila un módulo o una biblioteca  
  
 No se puede especificar un punto de entrada principal cuando se está generando [\/target:library](../Topic/-target:library%20\(C%23%20Compiler%20Options\).md).  
  
 El ejemplo siguiente genera la advertencia CS2017:  
  
```  
// CS2017.cs // compile with: /main:MyClass /target:library // CS2017 expected class MyClass { public static void Main() { } }  
```
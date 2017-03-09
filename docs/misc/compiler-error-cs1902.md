---
title: "Error del compilador CS1902 | Microsoft Docs"
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
  - "CS1902"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1902"
ms.assetid: 120c5978-9ebc-4ec1-bcec-f840af6fdf5d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1902
Opción 'option' no válida para \/debug; debe ser full o pdbonly  
  
 Se pasó una opción no válida a la opción del compilador [\/debug](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).  
  
 El ejemplo siguiente genera la advertencia CS1902:  
  
```  
// CS1902.cs // compile with: /debug:x // CS1902 expected class x { public static void Main() { } }  
```
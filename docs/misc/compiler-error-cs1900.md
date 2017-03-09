---
title: "Error del compilador CS1900 | Microsoft Docs"
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
  - "CS1900"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1900"
ms.assetid: 08141138-bfea-4af3-a9a0-ec54cf2caa13
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1900
El nivel de advertencia debe estar en el intervalo 0\-4  
  
 La opción [\/warn](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option) del compilador solo puede tomar uno de los cinco valores posibles \(0, 1, 2, 3 o 4\). Cualquier otro valor pasado a **\/warn** producirá el error CS1900.  
  
 El ejemplo siguiente genera la advertencia CS1900:  
  
```  
// CS1900.cs // compile with: /W:5 // CS1900 expected class x { public static void Main() { } }  
```
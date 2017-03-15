---
title: "Advertencia del compilador (nivel 1) CS0184 | Microsoft Docs"
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
  - "CS0184"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0184"
ms.assetid: 55e73f76-f502-4d15-88fc-bd5757b512a4
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS0184
La expresión dada no es nunca del tipo proporcionado \('tipo'\)  
  
 La expresión nunca puede ser **true** porque la variable que está probando no está declarada como ***tipo*** ni se deriva de ***tipo***.  
  
 El ejemplo siguiente genera la advertencia CS0184:  
  
```  
// CS0184.cs // compile with: /W:1 class MyClass { public static void Main() { int i = 0; if (i is string)   // CS0184 i++; } }  
```
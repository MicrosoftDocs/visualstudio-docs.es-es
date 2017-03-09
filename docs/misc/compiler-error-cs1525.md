---
title: "Error del compilador CS1525 | Microsoft Docs"
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
  - "CS1525"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1525"
ms.assetid: 7913f589-2f2e-40bc-a27e-0b6930336484
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1525
Término de la expresión 'character' no válido  
  
 El compilador detectó un carácter no válido en una expresión.  
  
 El ejemplo siguiente genera la advertencia CS1525:  
  
```  
// CS1525.cs class x { public static void Main() { int i = 0; i = i +   // OK - identifier 'c' +     // OK - character (5) +     // OK - parenthesis [ +       // CS1525, operator not a valid expression element throw +   // CS1525, keyword not allowed in expression void;     // CS1525, void not allowed in expression } }  
```  
  
 Una etiqueta vacía también puede generar el error CS1525, como en el ejemplo siguiente:  
  
```  
// CS1525b.cs using System; public class MyClass { public static void Main() { goto FoundIt; FoundIt:      // CS1525 // Uncomment the following line to resolve: // System.Console.Write("Hello"); } }  
```
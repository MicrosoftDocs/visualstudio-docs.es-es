---
title: "Error del compilador CS0023 | Microsoft Docs"
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
  - "CS0023"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0023"
ms.assetid: 7a30073c-99de-41fa-ac6d-4a0dfbb76de9
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0023
El operador 'operator' no se puede aplicar al operando del tipo 'tipo'  
  
 Se intentó aplicar un operador a una variable cuyo tipo no se diseñó para funcionar con el operador. Para obtener más información, consulte [Tipos](/dotnet/csharp/programming-guide/types/index) y [operadores de C\#](/dotnet/csharp/language-reference/operators/index).  
  
 El ejemplo siguiente genera la advertencia CS0023:  
  
```  
// CS0023.cs namespace x { public class a { public static void Main() { string s = "hello"; s = -s;   // CS0023, minus operator not allowed on strings } } }  
```
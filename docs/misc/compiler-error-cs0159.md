---
title: "Error del compilador CS0159 | Microsoft Docs"
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
  - "CS0159"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0159"
ms.assetid: 9fde7ffa-aed7-4a9d-8f47-ea67bc9df9e4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0159
No existe la etiqueta 'label' en el ámbito de la instrucción goto  
  
 La etiqueta a la que hace referencia la instrucción [goto](/dotnet/csharp/language-reference/keywords/goto) no se encontró en el ámbito de la instrucción `goto`.  
  
 El ejemplo siguiente genera la advertencia CS0159:  
  
```  
// CS0159.cs public class Class1 { public static void Main() { int i = 0; switch (i) { case 1: goto case 3;   // CS0159, case 3 label does not exist case 2: break; } goto NOWHERE;   // CS0159, NOWHERE label does not exist } }  
```
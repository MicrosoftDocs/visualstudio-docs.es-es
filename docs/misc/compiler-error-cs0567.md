---
title: "Error del compilador CS0567 | Microsoft Docs"
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
  - "CS0567"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0567"
ms.assetid: 90aefbf9-d216-4eb4-96d4-44926fa23b1e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0567
Las interfaces no pueden contener operadores  
  
 Los operadores no están permitidos en definiciones de [interfaz](/dotnet/csharp/language-reference/keywords/interface).  
  
 El ejemplo siguiente genera la advertencia CS0567:  
  
```  
// CS0567.cs interface IA { int operator +(int aa, int bb);   // CS0567 } class Sample { public static void Main() { } }  
```
---
title: "Error del compilador CS1011 | Microsoft Docs"
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
  - "CS1011"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1011"
ms.assetid: d4568471-b0f8-4c24-89f3-9c543521d1d8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1011
Literal de carácter vacío  
  
 Se declaró [char](/dotnet/csharp/language-reference/keywords/char) y se inicializó como null. La inicialización de `char` debe especificar un carácter.  
  
 El ejemplo siguiente genera la advertencia CS1011:  
  
```  
// CS1011.cs class Sample { public char CharField = '';   // CS1011 }  
```
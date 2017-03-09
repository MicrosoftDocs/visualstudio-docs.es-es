---
title: "Error del compilador CS1530 | Microsoft Docs"
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
  - "CS1530"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1530"
ms.assetid: 3844b5ef-e0ec-42df-9267-72689020f128
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1530
No se permite el uso de la palabra clave 'new' en elementos definidos en un espacio de nombres  
  
 No es necesario especificar la palabra clave [new](/dotnet/csharp/language-reference/keywords/new) en ninguna construcción que se encuentre en un [espacio de nombres](/dotnet/csharp/language-reference/keywords/namespace).  
  
 El ejemplo siguiente genera la advertencia CS1530:  
  
```  
// CS1530.cs namespace a { new class i   // CS1530 { } // try the following instead class ii { public static void Main() { } } }  
```
---
title: "Error del compilador CS0138 | Microsoft Docs"
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
  - "CS0138"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0138"
ms.assetid: 970545f8-5ee5-428e-921a-3aa29f68d16d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0138
Una directiva de espacio de nombres using solo se puede aplicar a espacios de nombres. 'tipo' es un tipo, no un espacio de nombres.  
  
 Una directiva [using](/dotnet/csharp/language-reference/keywords/using) solo puede tomar el nombre de un espacio de nombres como parámetro. Para obtener más información, consulte [Espacios de nombres](/dotnet/csharp/programming-guide/namespaces/index).  
  
 El ejemplo siguiente genera la advertencia CS0138:  
  
```  
// CS0138.cs using System.Object;   // CS0138  
```
---
title: "Error del compilador CS1513 | Microsoft Docs"
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
  - "CS1513"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1513"
ms.assetid: 28dacbb5-bf60-49ac-878e-c0ce469114eb
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1513
Se esperaba }  
  
 El compilador esperaba una llave de cierre \(`}`\) que no se encontró.  
  
 El ejemplo siguiente genera la advertencia CS1513:  
  
```  
// CS1513 namespace y   // CS1513, no close curly brace { class x { public static void Main() { } }  
```
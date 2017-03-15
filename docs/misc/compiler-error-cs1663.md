---
title: "Error del compilador CS1663 | Microsoft Docs"
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
  - "CS1663"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1663"
ms.assetid: 013f36ac-8925-4cee-9008-54fa7ad1324b
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1663
El tipo de búfer de tamaño fijo debe pertenecer a uno de los tipos siguientes: bool, byte, short, int, long, char, sbyte, ushort, uint, ulong, float o double  
  
 Un búfer de tamaño fijo no puede ser de ningún tipo no incluido en la lista. Para evitar este error, use otro tipo o no use una matriz fija.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1663.  
  
```  
// CS1663.cs // compile with: /unsafe /target:library unsafe struct C { fixed string ab[10];   // CS1663 }  
```
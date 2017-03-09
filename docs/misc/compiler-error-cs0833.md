---
title: "Error del compilador CS0833 | Microsoft Docs"
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
  - "CS0833"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0833"
ms.assetid: 4ae32454-265f-47aa-bf2a-ee1d702330b7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0833
Un tipo anónimo no puede tener varias propiedades con el mismo nombre.  
  
 Un tipo anónimo, igual que cualquier tipo, no puede tener dos propiedades con el mismo nombre.  
  
### Para corregir este error  
  
1.  Asigne un nombre único a cada propiedad del tipo.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS0833:  
  
```  
// cs0833.cs using System; public class C { public static int Main() { var c = new { p1 = 1, p1 = 2 }; // CS0833 return 1; } }  
```  
  
## Vea también  
 [Tipos anónimos](/dotnet/csharp/programming-guide/classes-and-structs/anonymous-types)
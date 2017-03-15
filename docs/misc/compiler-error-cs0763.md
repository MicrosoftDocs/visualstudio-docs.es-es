---
title: "Error del compilador CS0763 | Microsoft Docs"
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
  - "CS0763"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0763"
ms.assetid: 940870ba-1250-4365-acaa-7f968ee96c5b
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0763
Ambas declaraciones de método parcial deben ser estáticas o ninguna de ellas puede ser estática.  
  
 Una declaración de método parcial no puede tener una parte estática y la otra parte no estática.  
  
### Para corregir este error  
  
1.  Asegúrese de ambas partes sean estáticas o no estáticas.  
  
## Ejemplo  
 El código siguiente genera el error CS0763:  
  
```  
// cs0763.cs using System; public partial class C { static partial void Part(); partial void Part() // CS0763 { } public static int Main() { return 1; } }  
```  
  
## Vea también  
 [Clases y métodos parciales](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [static](/dotnet/csharp/language-reference/keywords/static)
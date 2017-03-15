---
title: "Error del compilador CS1104 | Microsoft Docs"
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
  - "CS1104"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1104"
ms.assetid: 65bfe85f-8dd1-4aed-bcd1-1f7e0635868c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1104
Una matriz de parámetros no se puede usar con el modificador 'this' en un método de extensión.  
  
 El primer parámetro de un método de extensión no puede ser una matriz de parámetros.  
  
### Para corregir este error  
  
1.  Recuerde que el primer parámetro de una definición de método de extensión especifica el tipo de método que se "ampliará". No se trata de un parámetro de entrada. Por lo tanto, no tiene sentido tener una matriz de parámetros en esta ubicación. Si tiene que pasar una matriz de parámetros, debe ser el segundo parámetro.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS1104:  
  
```  
// cs1104.cs // Compile with: /target:library public static class Extensions { public static void Test<T>(this params T[] tArr) {} // CS1104 }   
```  
  
## Vea también  
 [Métodos de extensión](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)   
 [params](/dotnet/csharp/language-reference/keywords/params)
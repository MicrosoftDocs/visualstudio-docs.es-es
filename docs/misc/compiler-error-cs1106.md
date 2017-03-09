---
title: "Error del compilador CS1106 | Microsoft Docs"
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
  - "CS1106"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1106"
ms.assetid: 3585600a-6b2c-47aa-a418-ef049f07c107
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1106
Los métodos de extensión deben definirse en una clase estática no genérica.  
  
 Los métodos de extensión se deben definir como métodos estáticos en una clase estática no genérica.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS1106 porque la clase `Extensions` no está definida como `static`:  
  
```  
// cs1106.cs public class Extensions // CS1106 { public  static void Test<T>(this System.String s) {} }  
```  
  
## Vea también  
 [Métodos de extensión](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)   
 [static](/dotnet/csharp/language-reference/keywords/static)
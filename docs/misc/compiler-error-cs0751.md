---
title: "Error del compilador CS0751 | Microsoft Docs"
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
  - "CS0751"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0751"
ms.assetid: 2ebaed5f-d3ca-452f-8fce-f3299b84360a
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0751
Un método parcial debe declararse dentro de una clase parcial o una estructura parcial  
  
 No es posible declarar un método [parcial](/dotnet/csharp/language-reference/keywords/partial-method) a menos que se encapsule dentro de una clase parcial o una estructura parcial.  
  
### Para corregir este error  
  
1.  Quite el modificador `partial` del método y proporcione una implementación, o bien agregue el modificador `partial` a la clase o la estructura envolvente.  
  
## Ejemplo  
 El siguiente ejemplo genera el error CS0751:  
  
```  
// cs0751.cs using System; public class C { partial void Part(); // CS0751 public static int Main() { return 1; } }  
```  
  
## Vea también  
 [Clases y métodos parciales](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)
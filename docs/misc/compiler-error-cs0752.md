---
title: "Error del compilador CS0752 | Microsoft Docs"
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
  - "CS0752"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0752"
ms.assetid: f9a373d6-31ed-42db-8206-80cbe9b8c546
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0752
Un método parcial no puede tener parámetros out  
  
 Un método parcial no puede tener un parámetro [out](/dotnet/csharp/language-reference/keywords/out). Los parámetros out no se permiten porque si el compilador quita el método parcial, no hay ninguna garantía de que se asigne el parámetro out.  
  
### Para corregir este error  
  
1.  Quite el modificador out del parámetro y el valor devuelto del método en su lugar, o bien quite el modificador parcial de la declaración del método.  
  
## Ejemplo  
 El código siguiente genera el error CS0752:  
  
```  
// cs0752.cs public partial class C { partial void Part(out int num); // CS0752 // try the following line instead // partial void Part(int num); public static int Main() { return 1; } }  
```  
  
## Vea también  
 [Clases y métodos parciales](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)
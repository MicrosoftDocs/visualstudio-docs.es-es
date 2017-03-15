---
title: "Error del compilador CS1113 | Microsoft Docs"
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
  - "CS1113"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1113"
ms.assetid: ef2d828f-b5ee-4be9-ba2e-36df5502cc5a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1113
Los métodos de extensión 'name' definidos en el tipo de valor 'name' no se pueden usar para crear delegados.  
  
 Los métodos de extensión definidos en los tipos de clase se pueden usar para crear delegados. No se pueden usar los métodos de extensión definidos para los tipos de valor con este fin.  
  
### Para corregir este error  
  
1.  Asocie el método de extensión con un tipo de clase.  
  
2.  Haga que el método sea un método normal en la estructura.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS1113:  
  
```  
// cs1113.cs using System; public static class Extensions { public static S ExtMethod(this S s) { return s; } } public struct S { } public class Test { static int Main() { Func<S> f = new S().ExtMethod; // CS1113 return 1; } }  
  
```  
  
## Vea también  
 [Métodos de extensión](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)
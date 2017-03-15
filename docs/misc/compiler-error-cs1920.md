---
title: "Error del compilador CS1920 | Microsoft Docs"
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
  - "CS1920"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1920"
ms.assetid: efb4782f-a222-4fb5-9e79-8bd2d380520b
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1920
El inicializador de elemento no puede estar vacío.  
  
 Un inicializador de colección consta de una secuencia de inicializadores de elemento. Los inicializadores de elemento no deben incluirse entre llaves a menos que contengan una expresión de asignación. Sin embargo, si incluye llaves, estas no pueden estar vacías. Si el inicializador de elemento es un inicializador de objeto, las llaves pueden estar vacías siempre que el inicializador contenga una expresión de creación de objeto nuevo.  
  
### Para corregir este error  
  
-   Agregue la expresión que falta entre las llaves.  
  
-   Si la expresión va a ser un inicializador de objeto, agregue la expresión de creación de objeto nuevo delante de las llaves.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS1920:  
  
```  
// cs1920.cs using System.Collections.Generic; public class Test { public static int Main() { // Error. Empty initializer // for inner list. List<List<int>> collection = new List<List<int>>() { { } }; // CS1920 // OK. No initializer for inner list. List<List<int>> collection2 = new List<List<int>>() {  }; // OK. Inner list is initialized // to one List<int> with zero elements. List<List<int>> collection3 = new List<List<int>>() { new List<int> { } }; return 0; } }  
```  
  
## Vea también  
 [Inicializadores de objeto y colección](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)
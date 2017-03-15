---
title: "Error del compilador CS1950 | Microsoft Docs"
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
  - "CS1950"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1950"
ms.assetid: e37fb5b1-09e0-47a6-9db5-a48f90ea7bbb
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1950
El mejor método Add sobrecargado 'nombre' del inicializador de colección tiene algunos argumentos no válidos.  
  
 Para admitir los inicializadores de colección, una clase debe implementar IEnumerable y tener un método `Add` público. Para inicializar el tipo con un inicializador de colección, el parámetro de entrada del método `Add` debe ser compatible con el tipo del objeto que está intentando agregar.  
  
### Para corregir este error  
  
-   Use un tipo compatible en el inicializador de colección.  
  
-   Modifique el parámetro de entrada o la accesibilidad del método `Add` en el tipo de colección.  
  
-   Agregue un nuevo método `Add` con un parámetro de entrada que coincida con lo que está pasando.  
  
-   Haga que la clase de colección sea genérica, para que pueda tener un método `Add` que acepte cualquier tipo que pase.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS1950:  
  
```  
// cs1950.cs using System.Collections; class TestClass : CollectionBase { public void Add(int c) { } } class Test { static void Main() { TestClass t = new TestClass { "hi" }; // CS1950 } }  
```  
  
## Vea también  
 [Inicializadores de objeto y colección](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)
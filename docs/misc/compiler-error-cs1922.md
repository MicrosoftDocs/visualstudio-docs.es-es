---
title: "Error del compilador CS1922 | Microsoft Docs"
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
  - "CS1922"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1922"
ms.assetid: a4098a25-6581-4966-b61d-318cd12f76d3
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1922
El inicializador de colección requiere que su tipo 'type' implemente System.Collections.IEnumerable.  
  
 Para usar un inicializador de colección con un tipo, el tipo debe implementar `IEnumerable`. Este error puede producirse si se usa accidentalmente sintaxis de inicializador de colección cuando se pretendía usar un inicializador de objeto.  
  
### Para corregir este error  
  
-   Si el tipo no representa ninguna colección, use la sintaxis de inicializador de objeto en lugar de la sintaxis del inicializador de colección.  
  
-   Si el tipo representa una colección, modifíquelo para implementar `IEnumerable` antes de usar inicializadores de colección para inicializar objetos de ese tipo.  
  
-   Si el tipo representa una colección y no tiene acceso al código fuente, simplemente se inicializan sus elementos mediante el uso de sus constructores de clases u otros métodos de inicialización.  
  
## Ejemplo  
 El código siguiente produce el error CS1922:  
  
```  
// cs1922.cs public class Test { public static void Main() { // Collection initializer. var tc = new TestClass  {1,"hello"} ; // CS1922 // Object initalizer. var tc2 = new TestClass { memberA = 1, memberB = "hello" }; // OK } } public class TestClass { public int memberA { get; set; } public string memberB { get; set; } }  
  
```  
  
## Vea también  
 [Inicializadores de objeto y colección](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)
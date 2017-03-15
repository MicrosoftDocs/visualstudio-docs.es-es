---
title: "Error del compilador CS0452 | Microsoft Docs"
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
  - "CS0452"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0452"
ms.assetid: 50a87734-fe07-4bce-891d-a76e131db6cc
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0452
El tipo 'nombre de tipo' debe ser un tipo de referencia para poder usarlo como el parámetro 'nombre de parámetro' en el tipo o método genérico 'identificador de genérico'.  
  
 Este error se produce cuando se pasa un tipo de valor como `struct` o `int` como un parámetro a un tipo o método genérico que tiene una restricción de tipo de referencia.  
  
## Ejemplo  
 El código siguiente genera el error CS0452.  
  
```  
// CS0452.cs using System; public class BaseClass<S> where S : class { } public class Derived1 : BaseClass<int> { } // CS0452 public class Derived2<S> : BaseClass<S> where S : struct { } // CS0452  
```  
  
## Vea también  
 [Restricciones de tipos de parámetros](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)
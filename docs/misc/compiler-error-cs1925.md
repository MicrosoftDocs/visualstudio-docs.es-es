---
title: "Error del compilador CS1925 | Microsoft Docs"
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
  - "CS1925"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1925"
ms.assetid: b60806a5-2ccf-47f5-873b-7ac2292fdb54
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1925
No se puede inicializar el objeto de tipo 'tipo' con un inicializador de colección.  
  
 Solo se permiten inicializadores de colección para las clases de colección que cumplen determinados criterios. Para obtener más información, consulta [Inicializadores de objeto y colección](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers). Este error también se produce al intentar usar la forma abreviada de un inicializador de matriz anidado dentro de un inicializador de colección.  
  
### Para corregir este error  
  
1.  Inicialice el objeto llamando a sus constructores y métodos.  
  
## Ejemplo  
 El código siguiente genera el error CS1925:  
  
```  
// cs1925.cs public class Student { public int[] Scores; } class Test { static void Main(string[] args) { Student student = new Student { Scores = { 1, 2, 3 } }; // CS1925 } }  
```
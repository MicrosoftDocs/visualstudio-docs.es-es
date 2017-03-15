---
title: "Error del compilador CS1938 | Microsoft Docs"
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
  - "CS1938"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1938"
ms.assetid: fc8de996-f7a1-46e8-b07b-aea520b391b9
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1938
El nombre 'nombre' no está dentro del ámbito en el lado derecho de 'equals'. Considere la posibilidad de intercambiar las expresiones en ambos lados de 'equals'.  
  
 La palabra clave `equals` es un operador especial que se usa en una cláusula `join` para determinar la igualdad entre dos expresiones. La variable de rango para la secuencia de origen del lado izquierdo está dentro del ámbito en el lado izquierdo de equals y la variable de rango para el origen del lado derecho solo está dentro del ámbito en el lado izquierdo de equals. Para comprobarlo, puede experimentar con IntelliSense en el siguiente ejemplo de código.  
  
### Para corregir este error  
  
1.  Cambie la posición de las dos variables de rango tal como se muestra en la línea comentada en el ejemplo siguiente:  
  
## Ejemplo  
 El código siguiente genera el error CS1938:  
  
```  
// cs1938.cs using System.Linq; class Test { static void Main() { int[] sourceA = { 1, 2, 3, 4, 5 }; int[] sourceB = { 3, 4, 5, 6, 7 }; var query = from a in sourceA join b in sourceB on b equals a // CS1938 // Try the following line instead. // join b in sourceB on a equals b select new { a, b }; } }  
```  
  
## Vea también  
 [join \(cláusula\)](/dotnet/csharp/language-reference/keywords/join-clause)
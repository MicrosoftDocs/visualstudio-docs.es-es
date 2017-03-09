---
title: "Error del compilador CS1937 | Microsoft Docs"
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
  - "CS1937"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1937"
ms.assetid: f13e8dc9-8c20-477e-8b74-7192848e08a2
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1937
El nombre 'name' no está en el ámbito en el lado izquierdo de 'equals'. Considere la posibilidad de intercambiar las expresiones en ambos lados de 'equals'.  
  
 La palabra clave `equals` es un operador especial que se usa en una cláusula `join` para determinar la igualdad entre dos expresiones. La variable de rango de la secuencia de origen para el lado izquierdo está dentro del ámbito en el lado izquierdo de equals y la variable de rango para el origen del lado derecho solo está dentro del ámbito en el lado izquierdo de equals. Para comprobarlo, puede experimentar con IntelliSense en el siguiente ejemplo de código.  
  
### Para corregir este error  
  
1.  Cambie la posición de las dos variables de rango tal como se muestra en la línea comentada en el ejemplo siguiente:  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS1937:  
  
```  
// cs1937.cs using System.Linq; class Test { static void Main() { int[] sourceA = { 1, 2, 3, 4, 5 }; int[] sourceB = { 3, 4, 5, 6, 7 }; var query = from a in sourceA join b in sourceB on b equals a // CS1937 // Try the following line instead. //join b in sourceB on a equals b select new { a, b }; } }  
```  
  
 El lado izquierdo se denomina generalmente el lado "externo" y la derecha se denomina generalmente el lado "interno".  
  
## Vea también  
 [join \(cláusula\)](/dotnet/csharp/language-reference/keywords/join-clause)
---
title: "Error del compilador CS1934 | Microsoft Docs"
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
  - "CS1934"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1934"
ms.assetid: 18624be3-d534-4695-bafd-cc664fcde15e
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1934
No se encontró ninguna implementación del patrón de consulta para el tipo de origen 'type'. 'method' no encontrado. Considere la posibilidad de especificar el tipo de la variable de rango 'name' de forma explícita.  
  
 Este error se produce si una expresión de consulta especifica un origen de datos para el que no se implementaron operadores de consulta estándar. Una manera de generar este error consiste en especificar una variable `ArrayList` sin proporcionar un tipo explícito para la variable de rango.  
  
### Para corregir este error  
  
1.  En el ejemplo siguiente, la solución es simplemente especificar el tipo de la variable de rango:  
  
    ```  
    var q = from int x in list  
    ```  
  
## Ejemplo  
 En el siguiente ejemplo se muestra una forma de generar el error CS1934:  
  
```  
// cs1934.cs using System.Linq; using System.Collections; static class Test { public static void Main() { var list = new ArrayList { 0, 1, 2, 3, 4, 5 }; var q = from x in list // CS1934 select x + 1; } }  
```  
  
## Vea también  
 [How to: Query an ArrayList with LINQ](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ.md)
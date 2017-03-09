---
title: "Error del compilador CS1935 | Microsoft Docs"
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
  - "CS1935"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1935"
ms.assetid: d5dda801-fbf3-4340-bfe1-f9409f2d344d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1935
No se encontró ninguna implementación del patrón de consulta para el tipo de origen 'type'. 'method' no encontrado. Compruebe si falta una referencia o una directiva using para 'System.Linq'.  
  
 El tipo de origen de una consulta debe ser `IEnumerable`, `IEnumerable<T>` o un tipo derivado, o bien un tipo para el que usted u otra persona ha implementado los operadores de consulta estándar. Si el tipo de origen es `IEnumerable` o `IEnumerable<T>`, debe agregar una referencia a system.core.dll y una directiva `using` para el espacio de nombres System.Linq para devolver los métodos de extensión del operador de consulta estándar en el ámbito. Las implementaciones personalizadas de los operadores de consulta estándar se deben incluir en el ámbito de la misma manera, con una directiva `using` y, si es necesario, una referencia al ensamblado.  
  
### Para corregir este error  
  
1.  Agregue las directivas using y las referencias al proyecto.  
  
## Ejemplo  
 El código siguiente genera el error CS1935 porque la directiva `using` para System.Linq está comentada:  
  
```  
// cs1935.cs // CS1935 using System; using System.Collections.Generic; // using System.Linq; class Test { static int Main() { int[] nums = {0,1,2,3,4,5}; IEnumerable<int> e = from n in nums where n > 3 select n; return 0; } }  
```  
  
## Vea también  
 [Standard Query Operators Overview](../Topic/Standard%20Query%20Operators%20Overview.md)
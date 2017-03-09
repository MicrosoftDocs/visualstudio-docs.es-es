---
title: "Error del compilador CS0747 | Microsoft Docs"
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
  - "CS0747"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0747"
ms.assetid: dc1b7e38-cee5-406c-b193-a60ec4faebe1
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0747
Declarador de miembro de inicializador no válido.  
  
 Un inicializador de objeto se usa para asignar valores a propiedades o campos. Cualquier expresión que no sea una asignación a una propiedad o campo es un error en tiempo de compilación.  
  
### Para corregir este error  
  
1.  Asegúrese de que todas las expresiones en el inicializador son asignaciones a propiedades o campos del tipo. En el ejemplo siguiente, la segunda expresión es un error porque el valor `1` no está asignado a ninguna propiedad o campo de `List<int>`.  
  
## Ejemplo  
 El código siguiente genera el error CS0747:  
  
```  
// cs0747.cs using System.Collections.Generic; public class C { public static int Main() { var t = new List<int> { Capacity = 2, 1 }; // CS0747 return 1; } }  
```  
  
## Vea también  
 [Inicializadores de objeto y colección](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)
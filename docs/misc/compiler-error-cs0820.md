---
title: "Error del compilador CS0820 | Microsoft Docs"
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
  - "CS0820"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0820"
ms.assetid: 38c05162-ef20-42a8-9611-02698360dec5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0820
No se puede asignar un inicializador de matriz a una variable local con tipo implícito  
  
 Una matriz con tipo implícito es una matriz cuyo tipo de elemento deduce el compilador. Se debe inicializar con el modificador `new`\[\] como se muestra en el ejemplo de código.  
  
### Para corregir este error  
  
-   Utilice el modificador `new`\[\] con el inicializador de matriz.  
  
-   No use una variable local con tipo implícito.  
  
## Ejemplo  
 El código siguiente genera el error CS0820 y muestra cómo inicializar correctamente una matriz con tipo implícito:  
  
```  
//cs0820.cs class G { public static int Main() { var a = { 1,2,3}; //CS0820 // Try using one of the following lines instead. // var b = new[] { 1, 2, 3 }; //int[] b = {1, 2, 3}; return -1; } }  
```  
  
## Vea también  
 [Variables locales con asignación implícita de tipos](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
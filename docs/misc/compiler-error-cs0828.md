---
title: "Error del compilador CS0828 | Microsoft Docs"
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
  - "CS0828"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0828"
ms.assetid: e18ffe72-2fcc-436d-be7f-8c8365b86129
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0828
No se puede asignar 'expression' a una propiedad de tipo anónimo.  
  
 No se puede inicializar un tipo anónimo con un valor null o un tipo no seguro, o un grupo de métodos o una función anónima.  
  
### Para corregir este error  
  
1.  Agregue una declaración de tipo al lado izquierdo de la asignación o cambie la expresión del lado derecho para que tenga un tipo aceptable.  
  
## Ejemplo  
 El código siguiente genera CS0828 porque no se puede inicializar un miembro de un tipo anónimo con un valor null.  
  
```  
// cs0828.cs using System; public class C { public static int Main() { var a = 1; var c = new { p1 = null }; // CS0828 return 1; } }  
```  
  
## Vea también  
 [Variables locales con asignación implícita de tipos](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
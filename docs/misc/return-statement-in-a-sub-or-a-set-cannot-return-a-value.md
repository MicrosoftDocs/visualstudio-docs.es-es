---
title: "Una instrucci&#243;n &#39;Return&#39; en Sub o Set no puede devolver un valor | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30647"
  - "vbc30647"
helpviewer_keywords: 
  - "BC30647"
ms.assetid: d4c05c28-d650-4f49-976e-650d84802036
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Una instrucci&#243;n &#39;Return&#39; en Sub o Set no puede devolver un valor
Los procedimientos `Sub` y la propiedad `Set` no pueden devolver valores.  
  
 **Identificador de error:** BC30647  
  
### Para corregir este error  
  
-   Cambie el procedimiento actual a una función o a un procedimiento de propiedad `Get` si el procedimiento actual es parte de una propiedad.  
  
-   Puede devolver valores de manera eficaz desde procedimientos `Sub` modificando el valor de los parámetros que se pasan por referencia mediante la palabra clave `ByRef`.  
  
## Vea también  
 [Return \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/return-statement)   
 [Procedimientos Sub](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Procedimientos Function](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)   
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)
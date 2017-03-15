---
title: "Error de resoluci&#243;n de sobrecarga porque ninguna de las funciones &#39;&lt;genericprocedurename&gt;&#39; a las que se tiene acceso acepta este n&#250;mero de argumentos. | Microsoft Docs"
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
  - "bc32087"
  - "vbc32087"
helpviewer_keywords: 
  - "BC32087"
ms.assetid: a3eaafd3-80f6-4b7d-9b75-47b043fe17b5
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Error de resoluci&#243;n de sobrecarga porque ninguna de las funciones &#39;&lt;genericprocedurename&gt;&#39; a las que se tiene acceso acepta este n&#250;mero de argumentos.
No se puede resolver una llamada a un procedimiento genérico sobrecargado porque el compilador no puede tener acceso a ninguna versión sobrecargada con el número apropiado de parámetros de tipo.  
  
 Cuando se llama a un procedimiento genérico, debe proporcionar un argumento de tipo para cada parámetro de tipo. Como alternativa, puede no proporcionar ningún argumento de tipo y dejar que el compilador intente hacer la *inferencia de tipos*. Para obtener más información, vea "Inferencia de tipos" en [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures).  
  
 **Identificador de error:** BC32087  
  
### Para corregir este error  
  
1.  Asegúrese de que la versión que piensa llamar está accesible para el código de llamada. Vea [Niveles de acceso en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels).  
  
2.  Agregue o quite los argumentos de tipo del código que realiza la llamada para que la lista de argumentos de tipo coincida con la lista de parámetros de tipo de la versión que piensa llamar.  
  
     O bien  
  
     Quite todos los argumentos de tipo del código que realiza la llamada y permita que el compilador intente realizar la inferencia de tipos. Tenga en cuenta que la inferencia de tipos puede fallar si hay conflictos o ambigüedades.  
  
## Vea también  
 [Propiedades y métodos sobrecargados](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods)   
 [Resolución de sobrecargas](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)
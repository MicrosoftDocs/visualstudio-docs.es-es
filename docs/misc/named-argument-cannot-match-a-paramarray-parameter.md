---
title: "Un argumento con nombre no puede coincidir con un par&#225;metro ParamArray. | Microsoft Docs"
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
  - "bc30587"
  - "vbc30587"
helpviewer_keywords: 
  - "BC30587"
ms.assetid: aff179af-96f2-4157-971e-881d8e08f5f2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Un argumento con nombre no puede coincidir con un par&#225;metro ParamArray.
Ha proporcionado un argumento con nombre \(especificado con el nombre declarado del argumento seguido de dos puntos y un signo igual, seguido por el valor del argumento\); sin embargo, no puede pasar una matriz de parámetros por nombre. Cuando se llama al procedimiento, se proporciona un número indefinido de argumentos separados por comas para la matriz de parámetros y el compilador no puede asociar más de un argumento con un nombre único.  
  
 **Identificador de error:** BC30587  
  
### Para corregir este error  
  
-   Pase el argumento por posición, en lugar de por nombre.  
  
## Vea también  
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)   
 [Pasar argumentos por posición o por nombre](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)
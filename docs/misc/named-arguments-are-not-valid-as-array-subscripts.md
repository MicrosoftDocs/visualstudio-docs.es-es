---
title: "Los argumentos con nombre no son v&#225;lidos como sub&#237;ndices de matriz | Microsoft Docs"
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
  - "vbc30075"
  - "bc30075"
helpviewer_keywords: 
  - "BC30075"
ms.assetid: a25025c9-0763-4c19-9e9b-cffb9aacaa8a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los argumentos con nombre no son v&#225;lidos como sub&#237;ndices de matriz
Se especifica un índice de matriz con la sintaxis para pasar un argumento de procedimiento por nombre, por ejemplo `Array(Index := 10)`. Esta sintaxis no es válida para los subíndices de matriz.  
  
 **Id. de error:** BC30075  
  
### Para corregir este error  
  
-   Use una expresión de constante o de variable normal como el índice de la matriz, por ejemplo `Array(10)`.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Información general sobre matrices en Visual Basic](http://msdn.microsoft.com/es-es/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [Pasar argumentos por posición o por nombre](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)
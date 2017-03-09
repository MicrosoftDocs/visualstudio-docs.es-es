---
title: "&#39;ReDim&#39; no puede cambiar el n&#250;mero de dimensiones de una matriz. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30415"
  - "bc30415"
helpviewer_keywords: 
  - "BC30415"
ms.assetid: 8ce97188-ff96-4e8c-917c-efc2f94173a3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReDim&#39; no puede cambiar el n&#250;mero de dimensiones de una matriz.
Ha intentado usar `ReDim` para cambiar el rango \(número de dimensiones\) de una matriz. La instrucción `ReDim` puede cambiar el tamaño de una o más dimensiones de una matriz que ya se han declarado formalmente, pero no puede cambiar el rango de la matriz.  
  
 **Identificador de error:** BC30415  
  
### Para corregir este error  
  
-   Asegúrese de que intenta cambiar el rango en lugar de los tamaños de la matriz y, si es posible, use `Dim` para declarar una nueva matriz con el rango que quiere.  
  
## Vea también  
 [ReDim \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [Dim \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [NOTINBUILD Información general de matrices en Visual Basic](http://msdn.microsoft.com/es-es/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)
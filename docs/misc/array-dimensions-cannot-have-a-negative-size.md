---
title: "Las dimensiones de la matriz no pueden ser de tama&#241;o negativo. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30611"
  - "vbc30611"
helpviewer_keywords: 
  - "BC30611"
ms.assetid: e310bd0d-f221-4b02-87f3-02124f4de87c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las dimensiones de la matriz no pueden ser de tama&#241;o negativo.
Uno o varios de los límites de matriz especificados son un número negativo. Puede especificar un subíndice negativo solo al usar un límite superior de \-1 para declarar una matriz vacía. Dicha matriz tiene cero elementos, pero no es `Nothing`.  
  
 **Identificador de error:** BC30611  
  
### Para corregir este error  
  
-   Reemplace la matriz negativa enlazada con un número positivo.  
  
## Vea también  
 [Matrices](/dotnet/visual-basic/programming-guide/language-features/arrays/index)
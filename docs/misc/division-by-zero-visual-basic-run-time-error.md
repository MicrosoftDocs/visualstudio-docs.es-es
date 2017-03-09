---
title: "Divisi&#243;n por cero (error en tiempo de ejecuci&#243;n de Visual Basic) | Microsoft Docs"
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
  - "vbrID11"
ms.assetid: 5b9bc5d6-792e-48bc-a974-012e07ad95f3
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Divisi&#243;n por cero (error en tiempo de ejecuci&#243;n de Visual Basic)
Una expresión que se está usando como divisor tiene un valor de cero.  
  
### Para corregir este error  
  
1.  Compruebe la ortografía de las variables de la expresión. Un nombre de variable mal escrito puede crear implícitamente una variable numérica que se inicialice en cero.  
  
2.  Compruebe las operaciones anteriores en las variables de la expresión, especialmente las que se pasaron al procedimiento como argumentos de otros procedimientos.  
  
## Vea también  
 [Pasar argumentos por valor y por referencia](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [Parameter Passing Mechanism Changes in Visual Basic](http://msdn.microsoft.com/es-es/0fa2b0dc-aa1c-4797-bbd6-aa13c611cab2)
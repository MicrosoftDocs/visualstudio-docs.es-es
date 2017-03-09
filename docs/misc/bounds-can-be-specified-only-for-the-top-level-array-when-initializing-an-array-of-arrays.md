---
title: "Los l&#237;mites solo se pueden especificar para la matriz de nivel superior al inicializar una matriz de matrices | Microsoft Docs"
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
  - "bc32014"
  - "vbc32014"
helpviewer_keywords: 
  - "BC32014"
ms.assetid: d8d7155d-82d1-4a25-b9bb-1883e1586383
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los l&#237;mites solo se pueden especificar para la matriz de nivel superior al inicializar una matriz de matrices
La inicialización de una matriz escalonada \(matriz de matrices\) define la longitud inicial de uno de los niveles inferiores. Solo se puede especificar la longitud de la matriz de nivel superior en la instrucción de declaración de matriz.  
  
 **Identificador de error:** BC32014  
  
### Para corregir este error  
  
1.  Quite todas las especificaciones de longitud excepto la de la matriz de nivel superior.  
  
2.  Defina la longitud inicial de las matrices de nivel inferior en instrucciones de asignación posteriores mediante la palabra clave `New`.  
  
## Vea también  
 [NOTINBUILD Una variable de matriz](http://msdn.microsoft.com/es-es/c2da78bd-6928-46ba-805f-44f819dfaf93)   
 [NOTINBUILD Información general sobre matrices irregulares en Visual Basic](http://msdn.microsoft.com/es-es/05c12439-ee8f-4fef-ba75-b35402b67ab9)   
 [New \(Operador\)](/dotnet/visual-basic/language-reference/operators/new-operator)
---
title: "La variable de recursos &#39;Using&#39; debe tener una inicializaci&#243;n expl&#237;cita | Microsoft Docs"
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
  - "vbc36011"
  - "bc36011"
helpviewer_keywords: 
  - "BC36011"
ms.assetid: 5db996a6-0802-4b67-91f1-4aa9c3dd6b09
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La variable de recursos &#39;Using&#39; debe tener una inicializaci&#243;n expl&#237;cita
Una instrucción `Using` especifica al menos un recurso que no se inicializa con una cláusula `New`.  
  
 Si aún no ha obtenido el recurso antes de pasar el control al bloque `Using`, la instrucción `Using` debe obtener el recurso. Para ello, debe crear un objeto a partir de la clase especificada, que requiere una cláusula `New`.  
  
 **Identificador de error:** BC36011  
  
### Para corregir este error  
  
-   Si ya obtuvo el recurso, use una expresión o una variable de referencia en la instrucción `Using` que se evalúa como el recurso obtenido.  
  
     `Dim newFont As New System.Drawing.Font`  
  
     `Using newFont`  
  
-   Si aún no obtuvo el recurso, agregue una cláusula `New` a la instrucción `Using`.  
  
     `Using newFont as`   `New`   `System.Drawing.Font`  
  
## Vea también  
 [Using \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/using-statement)   
 [New \(Operador\)](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Cómo: Deshacerse de un recurso del sistema](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)
---
title: "Los l&#237;mites inferiores de la matriz solo pueden ser &#39;0&#39; | Microsoft Docs"
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
  - "bc32059"
  - "vbc32059"
helpviewer_keywords: 
  - "BC32059"
ms.assetid: 273b69df-910e-45d2-acac-632005d24c5a
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los l&#237;mites inferiores de la matriz solo pueden ser &#39;0&#39;
Una instrucción de declaración o una cláusula `New` especifica una matriz con un límite inferior distinto de 0.  
  
 Al crear o inicializar una variable de matriz, puede especificar el límite superior de cada dimensión. Si lo hace, la longitud de esa dimensión se convierte en el límite superior más uno, porque el límite inferior es siempre cero. También tiene la posibilidad de especificar el límite inferior, pero debe especificar 0. La ventaja de hacerlo es que el código sea más fácil de leer.  
  
 **Identificador de error:** BC32059  
  
### Para corregir este error  
  
-   Cambie la especificación del límite inferior a 0 o quítelo por completo.  
  
## Vea también  
 [Matrices](/dotnet/visual-basic/programming-guide/language-features/arrays/index)   
 [NO ESTÁ EN LA COMPILACIÓN Cómo: especificar el límite inferior cero de una matriz](http://msdn.microsoft.com/es-es/20ffd49a-64f7-4634-8ed0-46ba1049d935)
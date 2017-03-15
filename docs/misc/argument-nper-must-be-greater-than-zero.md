---
title: "El argumento &#39;NPer&#39; debe ser mayor que cero | Microsoft Docs"
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
  - "vbrRate_NPerMustBeGTZero"
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El argumento &#39;NPer&#39; debe ser mayor que cero
La función `NPer`, que devuelve un `Double` que especifica el número de períodos de una anualidad basada en pagos fijos periódicos y en tipo de interés fijo, requiere un argumento mayor que cero.  
  
### Para corregir este error  
  
-   Compruebe la ortografía de los argumentos de la expresión. Un nombre de variable mal escrito puede crear implícitamente una variable numérica que se inicializa a cero.  
  
-   Compruebe las operaciones anteriores sobre variables de la expresión, especialmente las que se pasan al procedimiento como argumentos de otros procedimientos.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Función NPer](http://msdn.microsoft.com/es-es/56567d16-29f7-4928-b05f-b4cd56d4fd42)   
 [Pasar argumentos por valor y por referencia](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)
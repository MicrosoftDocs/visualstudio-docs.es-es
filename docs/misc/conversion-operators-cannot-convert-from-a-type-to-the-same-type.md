---
title: "Los operadores de conversi&#243;n no pueden convertir de un tipo al mismo tipo | Microsoft Docs"
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
  - "bc33024"
  - "vbc33024"
helpviewer_keywords: 
  - "BC33024"
ms.assetid: 4b47bcb0-4f0c-4d1c-9274-cce5b8e2b370
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los operadores de conversi&#243;n no pueden convertir de un tipo al mismo tipo
Un operador de conversión está declarado con el mismo tipo para el parámetro y el valor devuelto.  
  
 No tiene sentido realizar una conversión de un tipo a sí mismo.  
  
 **Identificador de error:** BC33024  
  
### Para corregir este error  
  
-   Cambie el tipo del parámetro o del valor devuelto. Uno de ellos debe ser del tipo de la clase o estructura en la que está definido este operador. El otro debe ser de un tipo diferente.  
  
-   Si necesita realizar una transformación en el contenido del parámetro, use una [Function \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/function-statement) para definir un procedimiento `Function` en lugar de un operador.  
  
## Vea también  
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)
---
title: "Los operadores no se pueden declarar en los m&#243;dulos. | Microsoft Docs"
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
  - "bc33018"
  - "vbc33018"
helpviewer_keywords: 
  - "BC33018"
ms.assetid: 10a8fd2d-2af7-4f90-9f2a-50c07ebf7589
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los operadores no se pueden declarar en los m&#243;dulos.
Un [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement) aparece en una definición de módulo.  
  
 Puede definir un operador como parte de una clase o una estructura que se está definiendo. El operador debe tomar esa clase o estructura como al menos uno de sus operandos.  
  
 Un operador debe usar una instancia de un elemento de programación como uno de sus operandos, y solo las clases y estructuras tienen instancias. Por lo tanto, no se puede definir un operador como parte de cualquier otro elemento de programación.  
  
 **Identificador de error:** BC33018  
  
### Para corregir este error  
  
-   Si necesita una operación en el módulo, use un [Function \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/function-statement) para definir un procedimiento `Function` que realice la operación.  
  
-   También puede definir una clase o estructura dentro del módulo y definir un operador en esa clase o estructura. Sin embargo, el operador debe tomar una instancia de esa clase o estructura como al menos uno de sus operandos.  
  
## Vea también  
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)
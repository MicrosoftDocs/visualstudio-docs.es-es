---
title: "El operador no es sobrecargable | Microsoft Docs"
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
  - "vbc33002"
  - "bc33002"
helpviewer_keywords: 
  - "BC33002"
ms.assetid: 8628ea42-57d8-41ca-8bdc-5e4c27be543e
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El operador no es sobrecargable
Solo determinados operadores son aptos para la sobrecarga. En la tabla siguiente se enumeran los operadores que se pueden definir.  
  
|Tipo|Operadores|  
|----------|----------------|  
|Unario|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|Binary|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Conversión \(unaria\)|`CType`|  
  
 Observe que el operador `=` de la lista binaria es el operador de comparación, no el de asignación.  
  
 **Identificador de error:** BC33002  
  
### Para corregir este error  
  
1.  Seleccione un operador del conjunto de operadores sobrecargables.  
  
2.  Si necesita la función de sobrecarga de un operador que no se puede sobrecargar directamente, cree un procedimiento `Function` que tome los parámetros adecuados y devuelva el valor adecuado.  
  
## Vea también  
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Function \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/function-statement)
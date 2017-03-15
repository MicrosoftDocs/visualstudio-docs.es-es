---
title: "Los operadores se deben declarar como &#39;Public&#39; | Microsoft Docs"
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
  - "vbc33011"
  - "bc33011"
helpviewer_keywords: 
  - "BC33011"
ms.assetid: 67fc0dee-4ef5-4afc-a63a-f7d20bce7954
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los operadores se deben declarar como &#39;Public&#39;
[Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement) no incluye la palabra clave [Public](/dotnet/visual-basic/language-reference/modifiers/public).  
  
 Un procedimiento `Operator` necesita las palabras clave `Public` y [Shared](/dotnet/visual-basic/language-reference/modifiers/shared), y un operador de conversión también necesita las palabras clave [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) o [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing).  
  
 **Id. de error:** BC33011  
  
### Para corregir este error  
  
-   Agregue la palabra clave `Public` a la instrucción `Operator`.  
  
## Vea también  
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)
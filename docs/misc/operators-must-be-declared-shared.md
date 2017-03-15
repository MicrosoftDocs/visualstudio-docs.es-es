---
title: "Los operadores se deben declarar como &#39;Shared&#39; | Microsoft Docs"
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
  - "vbc33012"
  - "bc33012"
helpviewer_keywords: 
  - "BC33012"
ms.assetid: 5ad97616-4032-46cd-aaf7-517db5d1195f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los operadores se deben declarar como &#39;Shared&#39;
[Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement) no incluye la palabra clave [Shared](/dotnet/visual-basic/language-reference/modifiers/shared).  
  
 Un procedimiento `Operator` necesita las palabras clave [Public](/dotnet/visual-basic/language-reference/modifiers/public) y `Shared`, y un operador de conversión también necesita las palabras clave [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) o [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing).  
  
 **Identificador de error:** BC33012  
  
### Para corregir este error  
  
-   Agregue la palabra clave `Shared` a la instrucción `Operator`.  
  
## Vea también  
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)
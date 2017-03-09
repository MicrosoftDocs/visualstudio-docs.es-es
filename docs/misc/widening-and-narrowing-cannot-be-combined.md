---
title: "&#39;Widening&#39; y &#39;Narrowing&#39; no se pueden combinar | Microsoft Docs"
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
  - "bc33001"
  - "vbc33001"
helpviewer_keywords: 
  - "BC33001"
ms.assetid: 1c576344-083c-45ad-bc71-0489bd3976be
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Widening&#39; y &#39;Narrowing&#39; no se pueden combinar
Una [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement) especifica [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) y [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing).  
  
 Al definir un operador de conversión, debe declararlo como `Widening` o `Narrowing`. Se trata de características mutuamente excluyentes, por lo que no se pueden especificar ambas.  
  
 **Identificador de error:** BC33001  
  
### Para corregir este error  
  
-   Quite la palabra clave `Widening` o `Narrowing` de la instrucción `Operator`. Debe especificar una u otra.  
  
## Vea también  
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)
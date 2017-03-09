---
title: "Se necesita un operador &#39;&lt;operatorsymbol1&gt;&#39; coincidente para &#39;&lt;operatorsymbol2&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33033"
  - "vbc33033"
helpviewer_keywords: 
  - "BC33033"
ms.assetid: d2805e4f-08a8-4760-9539-565f51b88d13
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se necesita un operador &#39;&lt;operatorsymbol1&gt;&#39; coincidente para &#39;&lt;operatorsymbol2&gt;&#39;
Un operador se define cuando su operador correspondiente necesario no está definido.  
  
 A continuación se describen operadores que deben definirse como combinaciones coincidentes:  
  
-   `=` y `<>`  
  
-   `>` y `<`  
  
-   `>=` y `<=`  
  
-   `IsTrue` y `IsFalse`  
  
 Si define cualquiera de estos operadores en una clase o estructura, también deberá definir su operador correspondiente en la misma clase o estructura.  
  
 Incluso si no usa el operador correspondiente de manera explícita, es posible que [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] necesite usarlo. Por ejemplo, si se define una clase o estructura que use como variable de contador en la instrucción [For...Next \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/for-next-statement), [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] requiere tanto el operador `>=` como  `<=` \(así como el operador `+`\).  
  
 **Id. de error:** BC33033  
  
### Para corregir este error  
  
-   Defina el operador correspondiente en la misma clase o estructura. Haga todo lo posible por definirlo de forma significativa, ya que [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] podría usarlo en una situación que no puede prever.  
  
## Vea también  
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Operadores y expresiones](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/index)
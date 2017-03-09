---
title: "El operador &#39;&lt;operador&gt;&#39; debe tener un segundo par&#225;metro de tipo &#39;Integer&#39; | Microsoft Docs"
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
  - "BC33041"
  - "vbc33041"
helpviewer_keywords: 
  - "BC33041"
ms.assetid: 5cd56f6d-2f0f-49de-a8e6-59bdb57bdb1d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El operador &#39;&lt;operador&gt;&#39; debe tener un segundo par&#225;metro de tipo &#39;Integer&#39;
Un operador de desplazamiento de bits se declaró con el segundo parámetro de un tipo distinto de `Integer`.  
  
 Cuando se usa el operador de desplazamiento a la derecha \(`>>`\) o de desplazamiento a la izquierda \(`<<`\) en una expresión, se especifica la cantidad de desplazamiento en el segundo operando. Para este operando, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] permite proporcionar cualquier tipo de datos que se amplíe a `Integer`. Sin embargo, la definición del segundo operando es estrictamente `Integer`. Si define una clase o una estructura con un operador de desplazamiento bits en esa clase o estructura, la definición debe especificar `Integer` para el segundo operando.  
  
 **Identificador de error:** BC33041  
  
### Para corregir este error  
  
-   Cambie la definición del operador de desplazamiento bits para devolver un valor `Integer`.  
  
## Vea también  
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Operadores de desplazamiento](/dotnet/visual-basic/language-reference/operators/bit-shift-operators)
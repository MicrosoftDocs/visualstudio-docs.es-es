---
title: "El operador &#39;&lt;operador&gt;&#39; debe tener un par&#225;metro. | Microsoft Docs"
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
  - "bc33014"
  - "vbc33014"
helpviewer_keywords: 
  - "BC33014"
ms.assetid: 512a5724-a6c5-4437-a608-7d6b10e68d49
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El operador &#39;&lt;operador&gt;&#39; debe tener un par&#225;metro.
Un operador unario está definido sin parámetros o con más de un parámetro.  
  
 Un operador unario debe tener exactamente un parámetro.  
  
 **Identificador de error:** BC33014  
  
### Para corregir este error  
  
-   Ajuste la definición para especificar exactamente un parámetro.  
  
-   Si necesita dos parámetros, debe definir un operador binario.  
  
-   Si no se necesita ningún parámetro o se necesitan más de dos, debe usar la [Function \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/function-statement) para definir un procedimiento `Function` en lugar de un operador.  
  
## Vea también  
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)
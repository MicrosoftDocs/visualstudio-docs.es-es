---
title: "El operador &#39;&lt;operator&gt;&#39; debe tener uno o dos par&#225;metros. | Microsoft Docs"
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
  - "bc33016"
  - "vbc33016"
helpviewer_keywords: 
  - "BC33016"
ms.assetid: 70f43905-037e-4040-83c0-f39334b3e07a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El operador &#39;&lt;operator&gt;&#39; debe tener uno o dos par&#225;metros.
Un operador que puede ser unario o binario se define sin parámetros o con más de dos parámetros.  
  
 Un operador unario\/binario debe tener uno o dos parámetros.  
  
 **Identificador de error:** BC33016  
  
### Para corregir este error  
  
-   Ajuste la definición para especificar uno o dos parámetros.  
  
-   Si no se necesita ningún parámetro o si necesita más de dos, debe usar [Function \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/function-statement) para definir un procedimiento `Function` en lugar de un operador.  
  
## Vea también  
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)
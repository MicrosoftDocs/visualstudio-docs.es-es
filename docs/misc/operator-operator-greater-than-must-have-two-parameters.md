---
title: "El operador &#39;&lt;operador&gt;&#39; debe tener dos par&#225;metros | Microsoft Docs"
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
  - "bc33015"
  - "vbc33015"
helpviewer_keywords: 
  - "BC33015"
ms.assetid: 506ea996-8abe-4dbe-aff4-d3910bf4399e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El operador &#39;&lt;operador&gt;&#39; debe tener dos par&#225;metros
Un operador binario está definido con menos de dos o más de dos parámetros.  
  
 Un operador binario debe tener exactamente dos parámetros.  
  
 **Identificador de error:** BC33015  
  
### Para corregir este error  
  
-   Ajuste la definición para especificar exactamente dos parámetros.  
  
-   Si necesita solo un parámetro, debe definir un operador unario.  
  
-   Si no necesita ningún parámetro o si necesita más de dos, debe usar [Function \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/function-statement) para definir un procedimiento `Function` en lugar de un operador.  
  
## Vea también  
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)
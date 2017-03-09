---
title: "Los operadores de conversi&#243;n no pueden convertir de un tipo a su tipo base | Microsoft Docs"
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
  - "bc33026"
  - "vbc33026"
helpviewer_keywords: 
  - "BC33026"
ms.assetid: 3533cf71-6a52-4fd0-a1f2-127c4ecd56ae
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los operadores de conversi&#243;n no pueden convertir de un tipo a su tipo base
Un operador de conversión se declara con un tipo de valor devuelto del que deriva el tipo de parámetro.  
  
 En tiempo de compilación, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] considera que existe una conversión predefinida de cualquier tipo de referencia a cualquier tipo de su jerarquía de herencia, es decir, a cualquier tipo del que derive o que derive de él. Este tipo de conversión puede producir un error en tiempo de ejecución, pero el compilador no puede predecir los resultados en tiempo de ejecución, por lo que permite que estas conversiones se compilen.  
  
 Como el compilador considera que esta conversión ya está definida, no permite redefinirla.  
  
 **Id. de error:** BC33026  
  
### Para corregir este error  
  
-   Quite completamente esta definición de operador. Ya está predefinido.  
  
## Vea también  
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)
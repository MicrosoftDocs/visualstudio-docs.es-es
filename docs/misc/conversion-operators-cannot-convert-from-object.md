---
title: "Los operadores de conversi&#243;n no pueden convertirse de Object | Microsoft Docs"
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
  - "bc33032"
  - "vbc33032"
helpviewer_keywords: 
  - "BC33032"
ms.assetid: 877f626f-7aa1-41d8-b7ca-eb4337d012d1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los operadores de conversi&#243;n no pueden convertirse de Object
Un operador de conversión está declarado con un parámetro de [Object \(Tipo de datos\)](/dotnet/visual-basic/language-reference/data-types/object-data-type).  
  
 En el tiempo de compilación, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] considera que existe una conversión predefinida desde cualquier tipo de referencia a cualquier tipo de su jerarquía de herencia, es decir, cualquier tipo del que este derive o que derive de este.`Object` es el tipo de datos universal de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], por lo que cada tipo se deriva de `Object`.  
  
 Dado que el compilador considera que esta conversión ya está definida, no permite redefinirla.  
  
 **Identificador de error:** BC33032  
  
### Para corregir este error  
  
-   Quite la definición de este operador completamente. Ya está predefinido.  
  
## Vea también  
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Object como tipo de datos universal \(Visual Basic\)](http://msdn.microsoft.com/es-es/5315bf21-2b22-45ab-98cd-5631dffbcb2f)
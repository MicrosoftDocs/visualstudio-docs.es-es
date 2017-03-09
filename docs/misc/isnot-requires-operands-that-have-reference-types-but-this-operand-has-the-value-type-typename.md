---
title: "&#39;IsNot&#39; requiere operandos que tengan tipos de referencia, pero este operando tiene el tipo de valor &#39;&lt;nombreDeTipo&gt;&#39;. | Microsoft Docs"
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
  - "bc31419"
  - "vbc31419"
helpviewer_keywords: 
  - "BC31419"
ms.assetid: c44d2936-8c07-443a-b320-ac2bfbc1e9ec
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;IsNot&#39; requiere operandos que tengan tipos de referencia, pero este operando tiene el tipo de valor &#39;&lt;nombreDeTipo&gt;&#39;.
Una expresión usa el [IsNot \(Operador\)](/dotnet/visual-basic/language-reference/operators/isnot-operator) con un operando de tipo de valor como mínimo.  
  
 El operador `IsNot` determina si dos referencias de objeto hacen referencia a objetos diferentes. Compara los valores de puntero de los tipos de referencia y no tiene sentido con los tipos de valor.  
  
 **Identificador de error:** BC31419  
  
### Para corregir este error  
  
-   Si tiene previsto comparar los valores de dos tipos de valor, use el operador de comparación `=` o `<>`.  
  
-   Si prevé comparar los punteros de dos tipos de referencia, asegúrese de que está usando referencias de objeto para ambos operandos. Puede usar variables de referencia o elementos, como la palabra clave [Me](http://msdn.microsoft.com/es-es/a65973c7-cf06-4547-9b25-9fba885525c2), que se comportan como variables de referencia.  
  
## Vea también  
 [Operadores de comparación en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)   
 [Cómo: Comprobar si dos objetos son iguales](../Topic/How%20to:%20Test%20Whether%20Two%20Objects%20Are%20the%20Same%20\(Visual%20Basic\).md)
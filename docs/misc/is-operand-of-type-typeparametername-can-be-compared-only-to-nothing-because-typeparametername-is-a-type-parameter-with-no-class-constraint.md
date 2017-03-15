---
title: "El operando &#39;Is&#39; del tipo &#39;&lt;typeparametername&gt;&#39; &#250;nicamente se puede comparar con &#39;Nothing&#39; porque &#39;&lt;typeparametername&gt;&#39; es un par&#225;metro de tipo sin restricci&#243;n de clase. | Microsoft Docs"
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
  - "vbc32052"
  - "bc32052"
helpviewer_keywords: 
  - "BC32052"
ms.assetid: 0bbf2249-eb0d-4b74-a555-8868c7ebe91d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El operando &#39;Is&#39; del tipo &#39;&lt;typeparametername&gt;&#39; &#250;nicamente se puede comparar con &#39;Nothing&#39; porque &#39;&lt;typeparametername&gt;&#39; es un par&#225;metro de tipo sin restricci&#243;n de clase.
Se usa un parámetro de tipo como operando para [Is \(Operador\)](/dotnet/visual-basic/language-reference/operators/is-operator) cuando está definido el parámetro de tipo sin la palabra clave [Class \(Visual Basic\)](http://msdn.microsoft.com/es-es/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) o un nombre de clase específico en su lista de restricciones.  
  
 `Is` compara dos tipos de referencia para determinar si señalan a la misma instancia de objeto en memoria. No puede tomar un operando que no es un tipo de referencia, a menos que el otro operando sea [Nothing](/dotnet/visual-basic/language-reference/nothing).  
  
 **Identificador de error:** BC32052  
  
### Para corregir este error  
  
-   Si puede requerir que el argumento de tipo proporcionado a este parámetro de tipo siempre sea un tipo de referencia, agregue la palabra clave `Class` o un nombre de clase específico a la lista de restricciones del parámetro de tipo.  
  
-   Si no se requiere que el argumento de tipo proporcionado a este parámetro de tipo siempre sea un tipo de referencia, quítelo de la expresión `Is`. No se puede comparar con otros tipos de referencia con el operador `Is`.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Tipos de valor y tipos de referencia](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [Operadores de comparación en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)
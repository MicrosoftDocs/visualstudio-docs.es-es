---
title: "La clase base &#39;&lt;baseclassname1&gt;&#39; especificada para la clase &#39;&lt;partialclassname&gt;&#39; no puede ser distinta de la clase base &#39;&lt;baseclassname2&gt;&#39; de otro de sus tipos parciales. | Microsoft Docs"
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
  - "BC30928"
  - "vbc30928"
helpviewer_keywords: 
  - "BC30928"
ms.assetid: da464f09-1016-4dec-beb7-3202cacd8e1e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La clase base &#39;&lt;baseclassname1&gt;&#39; especificada para la clase &#39;&lt;partialclassname&gt;&#39; no puede ser distinta de la clase base &#39;&lt;baseclassname2&gt;&#39; de otro de sus tipos parciales.
Se ha definido una clase en dos o más declaraciones parciales que contienen más de una [Inherits \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/inherits-statement) que especifica más de una clase base.  
  
 Cuando se divide la definición de una clase entre varias declaraciones parciales, el compilador trata a la clase tipo como la unión de todas sus declaraciones parciales. Esto se aplica no solo a los miembros, sino también a la implementación, la herencia y el nivel de acceso.  
  
 Una clase puede implementar más de una interfaz, pero no puede heredar de más de una clase base. Por lo tanto, todas las instrucciones `Inherits` deben especificar la misma clase base.  
  
 **Identificador de error:** BC30928  
  
### Para corregir este error  
  
-   Decida qué clase debe ser la clase base de la clase parcial y quite de sus declaraciones parciales cualquier instrucción `Inherits` que especifica una clase base diferente.  
  
## Vea también  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Inherits \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Fundamentos de la herencia](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
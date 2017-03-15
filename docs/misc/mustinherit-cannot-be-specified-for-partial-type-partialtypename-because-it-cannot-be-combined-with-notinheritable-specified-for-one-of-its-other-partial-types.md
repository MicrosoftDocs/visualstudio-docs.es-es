---
title: "No se puede especificar &#39;MustInherit&#39; para un tipo parcial &#39;&lt;nombreDeTipoParcial&gt;&#39; porque no se puede combinar con &#39;NotInheritable&#39; especificado para uno de sus otros tipos parciales. | Microsoft Docs"
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
  - "vbc30926"
  - "BC30926"
helpviewer_keywords: 
  - "BC30926"
ms.assetid: 59a0b5d9-f53c-4234-88f4-dfc66342f143
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede especificar &#39;MustInherit&#39; para un tipo parcial &#39;&lt;nombreDeTipoParcial&gt;&#39; porque no se puede combinar con &#39;NotInheritable&#39; especificado para uno de sus otros tipos parciales.
Una clase está definida en varias declaraciones parciales; una de ellas especifica `MustInherit` y la otra, `NotInheritable`.  
  
 Cuando se divide la definición de una clase en varias declaraciones parciales, el compilador trata a la clase como la unión de todas sus declaraciones parciales. Esto se aplica no solo a los miembros, sino también a la implementación, la herencia y el nivel de acceso.  
  
 Una clase no puede ser *abstract* y *sealed* a la vez, es decir, no puede requerir y prohibir la herencia simultáneamente. Por lo tanto, no se pueden especificar ambos, `MustInherit` y `NotInheritable`, para la misma clase.  
  
 **Identificador de error:** BC30926  
  
### Para corregir este error  
  
-   Decida si la clase debe requerir la herencia, prohibir la herencia o ninguna de ellas y quite las palabras clave que son inadecuadas para su decisión.  
  
## Vea también  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)   
 [Fundamentos de la herencia](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
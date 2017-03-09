---
title: "&#39;MustOverride&#39; no se puede especificar en &#39;&lt;nombreDeProcedimiento&gt;&#39; porque se encuentra en un tipo parcial que se declar&#243; como &#39;NotInheritable&#39; en otra definici&#243;n parcial. | Microsoft Docs"
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
  - "vbc30927"
  - "BC30927"
helpviewer_keywords: 
  - "BC30927"
ms.assetid: 5798dfda-3d7b-4f30-9715-40cbf52d6dc4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;MustOverride&#39; no se puede especificar en &#39;&lt;nombreDeProcedimiento&gt;&#39; porque se encuentra en un tipo parcial que se declar&#243; como &#39;NotInheritable&#39; en otra definici&#243;n parcial.
Se declaró un procedimiento o una propiedad como `MustOverride` dentro de una clase definida en varias declaraciones parciales, pero una de estas definiciones parciales especifica `NotInheritable` para la clase.  
  
 Cuando se divide la definición de una clase en varias declaraciones parciales, el compilador trata a la clase como la unión de todas sus declaraciones parciales. Esto se aplica no solo a los miembros, sino también a la implementación, la herencia y el nivel de acceso.  
  
 Para invalidar un procedimiento o una propiedad, una clase debe heredar dicho procedimiento o propiedad de una clase base. Por lo tanto, para especificar `MustOverride` para un procedimiento o una propiedad en una clase base, se debe especificar `MustInherit` para la clase. Dado que son mutuamente contradictorios, no es posible especificar ambos, `MustInherit` y `NotInheritable`, para la misma clase.  
  
 **Identificador de error:** BC30927  
  
### Para corregir este error  
  
-   Si se debe invalidar la propiedad o el procedimiento, quite la palabra clave `NotInheritable` de la declaración parcial en la que aparece.  
  
-   Si la clase debe ser `NotInheritable`, quite la palabra clave `MustOverride` del procedimiento o la propiedad. No puede invalidar el procedimiento o la propiedad porque no es posible heredar la clase.  
  
## Vea también  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)   
 [Fundamentos de la herencia](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
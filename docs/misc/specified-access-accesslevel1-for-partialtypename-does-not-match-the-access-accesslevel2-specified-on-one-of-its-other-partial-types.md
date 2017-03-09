---
title: "Acceso especificado &#39;&lt;accesslevel1&gt;&#39; para &#39;&lt;partialtypename&gt;&#39; no coincide con el acceso &#39;&lt;accesslevel2&gt;&#39; especificado en uno de sus otros tipos parciales | Microsoft Docs"
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
  - "vbc30925"
  - "BC30925"
helpviewer_keywords: 
  - "BC30925"
ms.assetid: aabe0f4a-dc02-4828-a837-20cd47a7bd43
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Acceso especificado &#39;&lt;accesslevel1&gt;&#39; para &#39;&lt;partialtypename&gt;&#39; no coincide con el acceso &#39;&lt;accesslevel2&gt;&#39; especificado en uno de sus otros tipos parciales
Se define una clase o estructura en varias declaraciones parciales con especificaciones de nivel de acceso en conflicto.  
  
 Cuando se divide la definición de una clase o estructura entre varias declaraciones parciales, el compilador trata al tipo como la unión de todas sus declaraciones parciales. Esto se aplica no solo a los miembros, sino también a la implementación, la herencia y el nivel de acceso.  
  
 No se pueden mezclar niveles de acceso en la definición de una clase o estructura. Incluso la combinación `Protected Friend` solo se permite cuando las palabras clave son contiguas en la misma instrucción de declaración.  
  
 **Identificador de error:** BC30925  
  
### Para corregir este error  
  
-   Decida cuál será el nivel de acceso de la clase y quite cualquier especificación de nivel de acceso en conflicto.  
  
## Vea también  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Niveles de acceso en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Class \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Structure \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [NO ESTÁ EN LA COMPILACIÓN: Clases: planos para objetos](http://msdn.microsoft.com/es-es/2c86373d-0333-4616-a7d8-4790c4e89f7b)   
 [Estructuras](/dotnet/visual-basic/programming-guide/language-features/data-types/structures)
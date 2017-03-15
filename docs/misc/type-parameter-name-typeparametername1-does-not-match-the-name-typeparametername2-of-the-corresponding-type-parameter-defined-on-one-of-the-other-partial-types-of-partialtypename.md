---
title: "El nombre de par&#225;metro de tipo &#39;&lt;nombreDePar&#225;metroDeTipo1&gt;&#39; no coincide con el nombre &#39;&lt;nombreDePar&#225;metroDeTipo2&gt;&#39; del par&#225;metro de tipo correspondiente definido en uno de los otros tipos parciales de &#39;&lt;nombreDeTipoParcial&gt;&#39; | Microsoft Docs"
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
  - "vbc30931"
  - "bc30931"
helpviewer_keywords: 
  - "BC30931"
ms.assetid: 01b053c3-d1b5-4e69-b908-3d5cfc73913b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El nombre de par&#225;metro de tipo &#39;&lt;nombreDePar&#225;metroDeTipo1&gt;&#39; no coincide con el nombre &#39;&lt;nombreDePar&#225;metroDeTipo2&gt;&#39; del par&#225;metro de tipo correspondiente definido en uno de los otros tipos parciales de &#39;&lt;nombreDeTipoParcial&gt;&#39;
Hay una clase o una estructura definida en varias declaraciones parciales con especificaciones de parámetro de tipo en conflicto.  
  
 Cuando se divide la definición de una clase o una estructura entre varias declaraciones parciales, el compilador trata al tipo como la unión de todas sus declaraciones parciales. Esto se aplica no solo a los miembros, sino también a la implementación, la herencia y el nivel de acceso.  
  
 No se pueden especificar varios nombres para cualquier parámetro de tipo en la definición de una clase o una estructura genéricas.  
  
 **Identificador de error:** BC30931  
  
### Para corregir este error  
  
-   Decida qué nombre debe tener el parámetro de tipo y use el mismo nombre en cada declaración parcial.  
  
## Vea también  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Class \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Structure \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [NO ESTÁ EN LA COMPILACIÓN: Clases: como planos para objetos](http://msdn.microsoft.com/es-es/2c86373d-0333-4616-a7d8-4790c4e89f7b)   
 [Estructuras](/dotnet/visual-basic/programming-guide/language-features/data-types/structures)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)
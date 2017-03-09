---
title: "&#39;Inherits&#39; solo puede aparecer una vez dentro de una instrucci&#243;n &#39;Class&#39; y solo puede especificar una clase | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30121"
  - "bc30121"
helpviewer_keywords: 
  - "BC30121"
ms.assetid: 4ac5b018-5632-4661-8ac6-dbda2f8c4dfe
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Inherits&#39; solo puede aparecer una vez dentro de una instrucci&#243;n &#39;Class&#39; y solo puede especificar una clase
Más de una instrucción `Inherits` aparece en la misma clase, o una instrucción `Inherits` especifica más de una clase. Una clase puede heredar de una clase base solamente.  
  
 **Identificador de error:** BC30121  
  
### Para corregir este error  
  
-   Quite cualquier instrucción `Inherits` adicional y asegúrese de que la instrucción `Inherits` restante solo especifica una clase base.  
  
## Vea también  
 [Inherits \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Fundamentos de la herencia](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
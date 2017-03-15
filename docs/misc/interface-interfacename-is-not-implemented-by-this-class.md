---
title: "Esta clase no ha implementado la interfaz &#39;&lt;nombreDeInterfaz&gt;&#39; | Microsoft Docs"
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
  - "bc31035"
  - "vbc31035"
helpviewer_keywords: 
  - "BC31035"
ms.assetid: 99ddabb5-20e0-4cf6-a8d4-1ca91f3c7511
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Esta clase no ha implementado la interfaz &#39;&lt;nombreDeInterfaz&gt;&#39;
Un miembro de esta clase o estructura intenta implementar un miembro de una interfaz que la clase o al estructura no implementan.  
  
 **Identificador de error:** BC31035  
  
### Para corregir este error  
  
-   Agregue una instrucción `Implements` al principio de la clase o la estructura para que implemente la interfaz adecuada.  
  
-   Quite la palabra clave `Implements` del miembro que provoca el error.  
  
## Vea también  
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [Implements \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/implements-statement)
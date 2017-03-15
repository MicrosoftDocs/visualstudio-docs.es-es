---
title: "&lt;error&gt;: &#39;&lt;nombreDeClase1&gt;&#39; hereda de &#39;&lt;nombreDeClase2&gt;&#39; | Microsoft Docs"
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
  - "bc30256"
  - "vbc30256"
helpviewer_keywords: 
  - "BC30256"
ms.assetid: 170a12ee-87ef-4a49-8c84-ebf57fac435e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;error&gt;: &#39;&lt;nombreDeClase1&gt;&#39; hereda de &#39;&lt;nombreDeClase2&gt;&#39;
Se detectó una jerarquía de herencia circular. Una clase está designada como heredera de sí misma o de otra clase que hereda directa o indirectamente de esta.  
  
 Este mensaje puede aparecer más de una vez para realizar un seguimiento de la ruta de herencia circular.  
  
 **Identificador de error:** BC30256  
  
### Para corregir este error  
  
-   Para romper la circularidad quite al menos una instrucción `Inherits` de la ruta de herencia circular.  
  
## Vea también  
 [Fundamentos de la herencia](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
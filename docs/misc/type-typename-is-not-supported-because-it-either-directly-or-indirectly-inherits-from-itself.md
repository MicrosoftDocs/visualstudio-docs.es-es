---
title: "El tipo &#39;&lt;typename&gt;&#39; no se admite porque hereda directa o indirectamente de s&#237; mismo | Microsoft Docs"
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
  - "bc30916"
  - "vbc30916"
helpviewer_keywords: 
  - "BC30916"
ms.assetid: cea33daf-1971-4b70-a01d-7d8b5c9e4269
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo &#39;&lt;typename&gt;&#39; no se admite porque hereda directa o indirectamente de s&#237; mismo
Una clase o interfaz hereda de sí misma o de otra clase o interfaz que finalmente hereda de ella.  
  
 Visual Basic no admite la herencia circular.  
  
 **Id. de error:** BC30916  
  
### Para corregir este error  
  
-   Cambie la estructura de herencia para que se base en una clase base o una interfaz que no herede de ninguna otra clase o interfaz.  
  
## Vea también  
 [Fundamentos de la herencia](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
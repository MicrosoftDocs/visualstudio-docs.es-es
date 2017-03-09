---
title: "No se puede usar un modificador que acepte valores NULL con una variable cuyo tipo impl&#237;cito sea &#39;Object&#39;. | Microsoft Docs"
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
  - "bc33112"
  - "vbc33112"
helpviewer_keywords: 
  - "BC33112"
ms.assetid: 50b2a2ad-248d-4faa-820d-bcdf0e8b4aad
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede usar un modificador que acepte valores NULL con una variable cuyo tipo impl&#237;cito sea &#39;Object&#39;.
Una declaración de variable incluye el modificador de tipo que acepta valores NULL \(?\), pero no especifica un tipo ni infiere un tipo asignando un valor a la variable declarada.  
  
 **Identificador de error:** BC33112  
  
### Para corregir este error  
  
-   Especifique un tipo al declarar la variable que acepta valores NULL. El tipo no puede ser <xref:System.Object>.  
  
-   Asigne un valor al declarar la variable que acepta valores NULL. El tipo de la variable que acepta valores NULL se inferirá del valor asignado. El tipo del valor no puede ser <xref:System.Object>.  
  
## Vea también  
 [Tipos de valor que aceptan valores NULL](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)
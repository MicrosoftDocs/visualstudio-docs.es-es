---
title: "Las restricciones de este par&#225;metro de tipo no coinciden con las restricciones del par&#225;metro de tipo correspondiente definido en uno de los otros tipos parciales de &#39;|1&#39; | Microsoft Docs"
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
  - "vbc30932"
  - "bc30932"
helpviewer_keywords: 
  - "BC30932"
ms.assetid: a38ca4ad-6bbf-421e-a0d7-c5e0a9029160
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las restricciones de este par&#225;metro de tipo no coinciden con las restricciones del par&#225;metro de tipo correspondiente definido en uno de los otros tipos parciales de &#39;|1&#39;
Cuando se divide la definición de una clase o estructura entre varias declaraciones, el compilador trata la clase o estructura como la unión de todas sus declaraciones parciales. Por este motivo, no se puede definir ninguna lista de parámetros de tipo o modificadores en conflicto en las distintas declaraciones parciales.  
  
 **Id. de error:** BC30932  
  
### Para corregir este error  
  
1.  Determine la lista de parámetros de tipo deseada para la clase o estructura. Esto incluye los parámetros, su orden y sus listas de restricciones.  
  
2.  Asegúrese de que todas las definiciones parciales utilizan la misma lista de parámetros de tipo.  
  
## Vea también  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)
---
title: "Los m&#233;todos o eventos que implementan miembros de interfaz no se pueden declarar como &#39;Shared&#39; | Microsoft Docs"
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
  - "bc30505"
  - "vbc30505"
helpviewer_keywords: 
  - "BC30505"
ms.assetid: a24937c5-aeac-47de-a08b-d8696dd8221a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los m&#233;todos o eventos que implementan miembros de interfaz no se pueden declarar como &#39;Shared&#39;
Ha intentado declarar `Shared` como un método o un evento que implementa un miembro de interfaz. Los métodos y eventos que se implementan en una clase no pueden designarse como `Shared` o `Private`, excepto en una clase no heredable.  
  
 **Id. de error:** BC30505  
  
### Para corregir este error  
  
-   Quite la palabra clave `Shared`.  
  
## Vea también  
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)
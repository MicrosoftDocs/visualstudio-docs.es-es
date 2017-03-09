---
title: "El constructor debe declararse como Sub y no como Function. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30493"
  - "vbc30493"
helpviewer_keywords: 
  - "BC30493"
ms.assetid: bcacfd4b-cac0-4ad3-a6df-5fb37c189e8f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El constructor debe declararse como Sub y no como Function.
Intentó declarar `Function New`. Los constructores deben declararse como `Sub New`.  
  
 **Identificador de error:** BC30493  
  
### Para corregir este error  
  
-   Use `Sub` en lugar de `Function`.  
  
## Vea también  
 [Sub \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/sub-statement)
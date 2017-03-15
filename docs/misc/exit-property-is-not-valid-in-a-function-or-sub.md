---
title: "La instrucci&#243;n &#39;Exit Property&#39; no es v&#225;lida en Function o Sub | Microsoft Docs"
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
  - "vbc30066"
  - "bc30066"
helpviewer_keywords: 
  - "BC30066"
ms.assetid: 09e7e766-e35d-4282-b949-d227f733f950
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La instrucci&#243;n &#39;Exit Property&#39; no es v&#225;lida en Function o Sub
`Exit Property` aparece en un procedimiento `Function` o un procedimiento `Sub`. Una instrucción `Exit` debe coincidir con el bloque en el que se produce.  
  
 **Identificador de error:** BC30066  
  
### Para corregir este error  
  
-   Reemplace `Exit Property` con la instrucción `Exit Function` o `Exit Sub` según corresponda.  
  
## Vea también  
 [Procedimientos Sub](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Procedimientos Function](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)   
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)
---
title: "La instrucci&#243;n &#39;Exit Sub&#39; no es v&#225;lida en Function o Property | Microsoft Docs"
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
  - "bc30065"
  - "vbc30065"
helpviewer_keywords: 
  - "BC30065"
ms.assetid: d6426861-ba64-4dca-9100-262c6c058bd9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La instrucci&#243;n &#39;Exit Sub&#39; no es v&#225;lida en Function o Property
`Exit Sub` aparece en un procedimiento `Function` o un procedimiento `Property`. Una instrucción `Exit` debe coincidir con el bloque en el que se produce.  
  
 **Identificador de error:** BC30065  
  
### Para corregir este error  
  
-   Reemplace `Exit Sub` con la instrucción `Exit Function` o `Exit Property` según corresponda.  
  
## Vea también  
 [Procedimientos Sub](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Procedimientos Function](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)   
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)
---
title: "La instrucci&#243;n &#39;Exit Function&#39; no es v&#225;lida en Sub o Property | Microsoft Docs"
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
  - "vbc30067"
  - "bc30067"
helpviewer_keywords: 
  - "BC30067"
ms.assetid: 207fef65-4383-4120-9e5a-e0e14d168a72
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La instrucci&#243;n &#39;Exit Function&#39; no es v&#225;lida en Sub o Property
`Exit Function` aparece en un procedimiento `Sub` o un procedimiento `Property`. Una instrucción `Exit` debe coincidir con el bloque en el que se produce.  
  
 **Identificador de error:** BC30067  
  
### Para corregir este error  
  
-   Reemplace la función `Exit Function` por la instrucción `Exit Sub` o `Exit Property` según corresponda.  
  
## Vea también  
 [Procedimientos Sub](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Procedimientos Function](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)   
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)
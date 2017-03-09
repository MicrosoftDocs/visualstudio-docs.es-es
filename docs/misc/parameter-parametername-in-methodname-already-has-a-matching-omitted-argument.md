---
title: "El par&#225;metro &#39;&lt;nombreDePar&#225;metro&gt;&#39; de &#39;&lt;nombreDeM&#233;todo&gt;&#39; ya tiene un argumento omitido coincidente | Microsoft Docs"
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
  - "vbc32021"
  - "bc32021"
helpviewer_keywords: 
  - "BC32021"
ms.assetid: f51d29ba-c5b3-4731-a426-4c5ba11b4e1f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El par&#225;metro &#39;&lt;nombreDePar&#225;metro&gt;&#39; de &#39;&lt;nombreDeM&#233;todo&gt;&#39; ya tiene un argumento omitido coincidente
Una llamada a procedimiento proporciona un argumento por nombre después de omitir el mismo argumento por posición; por ejemplo:  
  
```  
Public Sub ABC(ByVal X As Byte, Optional ByVal Y As Byte = 0, _ Optional ByVal Z As Byte = 0) ' ... Call ABC(6, , Y:=3)   ' Argument Y omitted by position, supplied by name.  
```  
  
 **Identificador de error:** BC32021  
  
### Para corregir este error  
  
-   Proporcione el argumento por posición o quite la coma que lo omite.  
  
## Vea también  
 [Pasar argumentos por posición o por nombre](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)
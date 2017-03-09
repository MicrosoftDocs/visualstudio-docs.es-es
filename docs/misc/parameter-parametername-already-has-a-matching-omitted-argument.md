---
title: "El par&#225;metro &#39;&lt;nombrePar&#225;metro&gt;&#39; ya tiene un argumento omitido coincidente. | Microsoft Docs"
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
  - "vbc36566"
  - "bc36566"
helpviewer_keywords: 
  - "BC36566"
ms.assetid: b37af6bc-abd0-4436-bf8a-a467e3603342
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El par&#225;metro &#39;&lt;nombrePar&#225;metro&gt;&#39; ya tiene un argumento omitido coincidente.
Una llamada a procedimiento proporciona un argumento por nombre después de omitir el mismo argumento por posición. A continuación se muestra un ejemplo:  
  
```vb#  
Public Sub ABC(ByVal X As Byte, Optional ByVal Y As Byte = 0, _ Optional ByVal Z As Byte = 0) ' ... ' Argument Y is omitted by position, but supplied by name. Call ABC(6, , Y:=3)     
```  
  
 **Identificador de error:** BC36566  
  
### Para corregir este error  
  
-   Proporcione el argumento por posición o quite la coma que lo omite.  
  
## Vea también  
 [Pasar argumentos por posición o por nombre](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)
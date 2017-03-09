---
title: "&#39;System.Runtime.InteropServices.DllImportAttribute&#39; no se puede aplicar a &#39;Get&#39; o &#39;Set&#39; | Microsoft Docs"
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
  - "vbc31524"
  - "bc31524"
helpviewer_keywords: 
  - "BC31524"
ms.assetid: 3603e33a-a80b-448d-83e0-e5dbc9af4dcf
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Runtime.InteropServices.DllImportAttribute&#39; no se puede aplicar a &#39;Get&#39; o &#39;Set&#39;
El atributo `DllImportAttribute` se aplicó a un procedimiento de propiedad `Get` o `Set`.  
  
 **Id. de error:** BC31524  
  
### Para corregir este error  
  
1.  Quite `DllImportAttribute` de los procedimientos de propiedad `Get` y `Set`.  
  
## Vea también  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)
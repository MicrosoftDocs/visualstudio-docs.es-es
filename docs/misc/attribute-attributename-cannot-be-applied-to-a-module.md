---
title: "El atributo &#39;&lt;nombreAtributo&gt;&#39; no se puede aplicar a un m&#243;dulo. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30549"
  - "bc30549"
helpviewer_keywords: 
  - "BC30549"
ms.assetid: b38fea31-6b0b-4c54-9518-b59226505802
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El atributo &#39;&lt;nombreAtributo&gt;&#39; no se puede aplicar a un m&#243;dulo.
Intentó aplicar un atributo a un módulo cuyo `AttributeUsageAttribute` no especifica `AttributeTargets.Module`. Cuando se declaró el atributo, no se definió para aplicarse a un módulo.  
  
 **Identificador de error:** BC30549  
  
### Para corregir este error  
  
1.  Compruebe la declaración de atributo y especifique `AttributeTargets.Module`o`AttributeTargets.All`.  
  
## Vea también  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeTargets>
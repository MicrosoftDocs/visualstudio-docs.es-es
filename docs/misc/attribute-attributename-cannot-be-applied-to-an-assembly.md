---
title: "El atributo &#39;&lt;nombreDeAtributo&gt;&#39; no se puede aplicar a un ensamblado | Microsoft Docs"
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
  - "bc30548"
  - "vbc30548"
helpviewer_keywords: 
  - "BC30548"
ms.assetid: bc36f094-626a-4907-b80b-f195155fa5db
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El atributo &#39;&lt;nombreDeAtributo&gt;&#39; no se puede aplicar a un ensamblado
Intentó aplicar un atributo a un ensamblado cuyo `AttributeUsageAttribute` no especifica `AttributeTargets.Assembly`. Cuando se declaró el atributo, no se definió para aplicarse a un ensamblado.  
  
 **Identificador de error:** BC30548  
  
### Para corregir este error  
  
1.  Compruebe la declaración de atributo y especifique `AttributeTargets.Assembly` o `AttributeTargets.All`.  
  
## Vea también  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeTargets>
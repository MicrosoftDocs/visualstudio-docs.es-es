---
title: "&#39;&lt;attributename&gt;&#39; no se puede aplicar m&#225;s de una vez a un ensamblado. | Microsoft Docs"
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
  - "bc31521"
  - "vbc31521"
helpviewer_keywords: 
  - "BC31521"
ms.assetid: 7312570f-8afb-4afe-992f-b6f7796f5f26
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;attributename&gt;&#39; no se puede aplicar m&#225;s de una vez a un ensamblado.
El atributo especificado solo se puede aplicar una vez a un atributo.  
  
 **Identificador de error:** BC31521  
  
### Para corregir este error  
  
1.  Quite las aplicaciones redundantes de este atributo.  
  
2.  Si usa un atributo personalizado que ha desarrollado, modifique `AttributeUsageAttribute` y establezca la propiedad `AllowMultiple` en `True`.  
  
## Vea también  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=fullName>
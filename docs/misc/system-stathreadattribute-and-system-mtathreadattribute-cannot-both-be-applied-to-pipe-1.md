---
title: "&#39;System.STAThreadAttribute&#39; y &#39;System.MTAThreadAttribute&#39; no se pueden aplicar a la vez a &#39;|1&#39; | Microsoft Docs"
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
  - "bc31513"
  - "vbc31513"
helpviewer_keywords: 
  - "BC31513"
ms.assetid: 7efb4c8e-d31c-4273-9d85-8cd2bef4d120
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.STAThreadAttribute&#39; y &#39;System.MTAThreadAttribute&#39; no se pueden aplicar a la vez a &#39;|1&#39;
Los atributos `System.STAThreadAttribute` y `System.MTAThreadAttribute` son mutuamente excluyentes.  
  
 **Identificador de error:** BC31513  
  
### Para corregir este error  
  
1.  Aplique `System.MTAThreadAttribute` o `System.STAThreadAttribute`, pero no ambos.  
  
## Vea también  
 <xref:System.STAThreadAttribute>   
 <xref:System.MTAThreadAttribute>   
 [NO ESTÁ EN LA COMPILACIÓN: Atributos en Visual Basic](http://msdn.microsoft.com/es-es/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)
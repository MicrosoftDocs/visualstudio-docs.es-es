---
title: "No se ha declarado &#39;&lt;rsetstmt&gt;&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30821"
  - "vbc30821"
helpviewer_keywords: 
  - "BC30821"
ms.assetid: 7936e3ef-7ac6-4a71-af55-acc2c5cd8754
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se ha declarado &#39;&lt;rsetstmt&gt;&#39;.
No se ha declarado '\<rsetstmt\>'. Ya no se admiten instrucciones RSet; use Microsoft.VisualBasic.RSeten su lugar.  
  
 Varias funciones que eran intrínsecas a [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] en versiones anteriores se han movido al espacio de nombres <xref:Microsoft.VisualBasic?displayProperty=fullName>. Esto hace que sus funciones estén disponibles de manera más general para todos los lenguajes de programación.  
  
 **Identificador de error:** BC30821  
  
### Para corregir este error  
  
-   Use la función `RSet` en el espacio de nombres `Microsoft.VisualBasic` en su lugar.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Función NSet](http://msdn.microsoft.com/es-es/534514e5-dee9-4dfd-993b-da09731eece5)   
 [Programming Element Support Changes Summary](http://msdn.microsoft.com/es-es/0483590a-6309-449c-a2fa-effa26a03b95)
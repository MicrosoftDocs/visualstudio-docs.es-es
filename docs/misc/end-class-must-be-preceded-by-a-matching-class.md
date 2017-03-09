---
title: "&#39;End Class&#39; debe ir precedida de la instrucci&#243;n &#39;Class&#39; correspondiente. | Microsoft Docs"
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
  - "vbc30460"
  - "bc30460"
helpviewer_keywords: 
  - "BC30460"
ms.assetid: 0e6989da-f281-4ac4-8579-b6d627be8de8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Class&#39; debe ir precedida de la instrucci&#243;n &#39;Class&#39; correspondiente.
`End Class` se usa para completar un bloque `Class`; por lo tanto, solo puede aparecer una vez al final del bloque. O bien hay un elemento `End Class` redundante, o la instrucción `End Class` aparece fuera de los límites de su bloque `Class` correspondiente.  
  
 **Identificador de error:** BC30460  
  
### Para corregir este error  
  
-   Busque y quite cualquier instrucciones `End Class` redundantes.  
  
-   Mueva la instrucción `End Class` a la ubicación adecuada del código.  
  
## Vea también  
 [End \<palabra clave\> \(Instrucción\)](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)
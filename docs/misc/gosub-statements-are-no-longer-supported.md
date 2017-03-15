---
title: "Ya no se admiten instrucciones &#39;GoSub&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30814"
  - "bc30814"
helpviewer_keywords: 
  - "BC30814"
ms.assetid: fef2d78f-39ba-4aad-93b3-c7a08df9f805
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ya no se admiten instrucciones &#39;GoSub&#39;.
`GoSub` no se puede usar para llamar a un procedimiento.  
  
 **Identificador de error:** BC30814  
  
### Para corregir este error  
  
-   Llame a procedimientos directamente sin usar `GoSub`; por ejemplo:  
  
    ```  
    CalculateInterest(Amount, Rate, Time)  
    ```  
  
## Vea también  
 [Procedimientos](/dotnet/visual-basic/programming-guide/language-features/procedures/index)
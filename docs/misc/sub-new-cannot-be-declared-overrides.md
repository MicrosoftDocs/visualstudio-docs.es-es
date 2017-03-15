---
title: "&#39;Sub New&#39; no se puede declarar como &#39;Overrides&#39;. | Microsoft Docs"
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
  - "vbc30283"
  - "bc30283"
helpviewer_keywords: 
  - "BC30283"
ms.assetid: 0e71cdcb-b62e-4a36-8829-83de5c453c74
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Sub New&#39; no se puede declarar como &#39;Overrides&#39;.
Un constructor indica que invalida a un constructor heredado. Los constructores no se pueden invalidar.  
  
 **Identificador de error:** BC30283  
  
### Para corregir este error  
  
-   Quite la palabra clave `Overrides` de la declaración `Sub`.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Invalidar propiedades y métodos](http://msdn.microsoft.com/es-es/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [NO ESTÁ EN LA COMPILACIÓN: Usar constructores y destructores](http://msdn.microsoft.com/es-es/548eebe1-86c4-4377-b2f5-447cb8be3d90)
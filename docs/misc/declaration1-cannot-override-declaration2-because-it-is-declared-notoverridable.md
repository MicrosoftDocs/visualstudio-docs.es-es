---
title: "&#39;&lt;declaraci&#243;n1&gt;&#39; no puede reemplazar &#39;&lt;declaraci&#243;n2&gt;&#39; porque se declar&#243; &#39;NotOverridable&#39; | Microsoft Docs"
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
  - "bc30267"
  - "vbc30267"
helpviewer_keywords: 
  - "BC30267"
ms.assetid: fb1f6797-4e49-442e-a660-59d602132631
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;declaraci&#243;n1&gt;&#39; no puede reemplazar &#39;&lt;declaraci&#243;n2&gt;&#39; porque se declar&#243; &#39;NotOverridable&#39;
Una declaración de propiedad o procedimiento intenta reemplazar un elemento heredado que tiene el mismo nombre, pero el elemento heredado está especificado como `NotOverridable`.  
  
 **Identificador de error:** BC30267  
  
### Para corregir este error  
  
-   Quite la palabra clave `NotOverridable` de la declaración del elemento heredado o quite la declaración de reemplazo.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Reemplazar propiedades y métodos](http://msdn.microsoft.com/es-es/2167e8f5-1225-4b13-9ebd-02591ba90213)
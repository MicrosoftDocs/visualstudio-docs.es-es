---
title: "&#39;&lt;declaration1&gt;&#39; no puede reemplazar &#39;&lt;declaration2&gt;&#39; porque se declar&#243; como &#39;Shared&#39; | Microsoft Docs"
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
  - "vbc30268"
  - "bc30268"
helpviewer_keywords: 
  - "BC30268"
ms.assetid: d011fb26-6236-462e-9173-622f8bbeb536
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;declaration1&gt;&#39; no puede reemplazar &#39;&lt;declaration2&gt;&#39; porque se declar&#243; como &#39;Shared&#39;
Una declaración de propiedad o procedimiento intenta reemplazar un elemento heredado que tiene el mismo nombre, pero el elemento heredado se especifica como `Shared`. Los elementos compartidos no están asociados a ninguna instancia de la clase, por lo que no pueden reemplazarse.  
  
 **Id. de error:** BC30268  
  
### Para corregir este error  
  
-   Quite la palabra clave `Shared` del elemento heredado o quite la declaración de reemplazo.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Reemplazar propiedades y métodos](http://msdn.microsoft.com/es-es/2167e8f5-1225-4b13-9ebd-02591ba90213)
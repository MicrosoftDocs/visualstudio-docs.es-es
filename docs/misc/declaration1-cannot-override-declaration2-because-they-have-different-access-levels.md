---
title: "&#39;&lt;declaration1&gt;&#39; no puede reemplazar a &#39;&lt;declaration2&gt;&#39; porque tienen niveles de acceso diferentes | Microsoft Docs"
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
  - "bc30266"
  - "vbc30266"
helpviewer_keywords: 
  - "BC30266"
ms.assetid: c9c5c14e-876c-430d-ab98-5087c19efae7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;declaration1&gt;&#39; no puede reemplazar a &#39;&lt;declaration2&gt;&#39; porque tienen niveles de acceso diferentes
Una declaración de procedimiento o propiedad intenta reemplazar un elemento heredado con el mismo nombre, pero especifica una accesibilidad diferente a la del elemento heredado. La accesibilidad del elemento heredado, como por ejemplo `Public` o `Private`, debe conservarse en el reemplazo.  
  
 **Id. de error:** BC30266  
  
### Para corregir este error  
  
-   Cambie la accesibilidad del elemento que reemplaza para que coincida con la del elemento heredado.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Reemplazar propiedades y métodos](http://msdn.microsoft.com/es-es/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Niveles de acceso en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)
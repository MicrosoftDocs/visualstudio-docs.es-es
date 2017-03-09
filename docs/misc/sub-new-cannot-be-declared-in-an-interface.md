---
title: "&#39;Sub New&#39; no se puede declarar en una interfaz | Microsoft Docs"
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
  - "bc30363"
  - "vbc30363"
helpviewer_keywords: 
  - "BC30363"
ms.assetid: 371d9aa8-a935-48ce-ada2-0a69ba20e070
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Sub New&#39; no se puede declarar en una interfaz
Ha intentado declarar `Sub New` dentro de una interfaz. Como se trata de un constructor, `Sub New` solo puede ejecutarse una vez cuando se crea una clase. No es posible llamarlo explícitamente desde ningún lugar que no sea la primera línea del código de otro constructor de la misma clase o una clase derivada.  
  
 **Id. de error:** BC30363  
  
### Para corregir este error  
  
-   Quite el elemento `Sub New` o muévalo a un lugar más adecuado en el código.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Usar constructores y destructores](http://msdn.microsoft.com/es-es/548eebe1-86c4-4377-b2f5-447cb8be3d90)
---
title: "La llamada a un constructor solo es v&#225;lida como la primera instrucci&#243;n de un constructor de instancia | Microsoft Docs"
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
  - "vbc30282"
  - "bc30282"
helpviewer_keywords: 
  - "BC30282"
ms.assetid: c51b172f-fbd7-4ef5-8276-01a4bf6ed35b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La llamada a un constructor solo es v&#225;lida como la primera instrucci&#243;n de un constructor de instancia
Una llamada a `New()` se produce después de la primera instrucción de un constructor. Si un constructor llama a otro explícitamente, debe hacerlo en la instrucción inmediatamente posterior a la instrucción `Sub New()`.  
  
 **Id. de error:** BC30282  
  
### Para corregir este error  
  
-   Quite la llamada a `New()` o muévala al principio del constructor.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Usar constructores y destructores](http://msdn.microsoft.com/es-es/548eebe1-86c4-4377-b2f5-447cb8be3d90)
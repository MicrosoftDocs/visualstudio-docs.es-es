---
title: "No se puede establecer el valor de una variable local para un m&#233;todo que no est&#225; en la parte superior de la pila. | Microsoft Docs"
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
  - "bc30711"
  - "vbc30711"
helpviewer_keywords: 
  - "BC30711"
ms.assetid: b2aa290f-3311-448a-af46-ff2a2add5788
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede establecer el valor de una variable local para un m&#233;todo que no est&#225; en la parte superior de la pila.
Solo puede modificar variables si están en la parte superior de la pila de llamadas. Por ejemplo, si `procedure1` llama a `procedure2` y se encuentra en `procedure1`, no puede modificar las variables de `procedure2`.  
  
 **Identificador de error:** BC30711  
  
### Para corregir este error  
  
-   Modifique las variables que se encuentran en la parte superior de la pila de llamadas.  
  
## Vea también  
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)
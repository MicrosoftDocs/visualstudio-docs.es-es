---
title: "Las instrucciones &#39;GoTo&#39; no son v&#225;lidas en la ventana Inmediato. | Microsoft Docs"
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
  - "bc30133"
  - "vbc30133"
helpviewer_keywords: 
  - "BC30133"
ms.assetid: e5901616-6aec-4718-b452-90b2143301b0
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las instrucciones &#39;GoTo&#39; no son v&#225;lidas en la ventana Inmediato.
La instrucción `GoTo` realiza una bifurcación y no está permitida en un contexto de depuración.  
  
 **Identificador de error:** BC30133  
  
### Para corregir este error  
  
-   No emita una instrucción `GoTo` en la ventana **Inmediato**.  
  
## Vea también  
 [Ventana Inmediato](../ide/reference/immediate-window.md)
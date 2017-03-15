---
title: "&#39;&lt;membername&gt;&#39; no est&#225; declarado | Microsoft Docs"
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
  - "vbc30816"
  - "bc30816"
helpviewer_keywords: 
  - "BC30816"
ms.assetid: d6704bed-bb76-47c6-ac28-09608d5e6912
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;membername&gt;&#39; no est&#225; declarado
'`<membername>`' no está declarado. La funcionalidad del objeto `Debug` se encuentra disponible en `System.Diagnostics.Debug` en el ensamblado `System`.  
  
 No se pudo encontrar el nombre del miembro especificado.  
  
 **Identificador de error:** BC30816  
  
### Para corregir este error  
  
1.  Compruebe la ortografía del miembro.  
  
2.  Use una instrucción `Imports` o miembros completamente calificados definidos en otros espacios de nombres. Por ejemplo, la función `WriteLine` está declarada en el espacio de nombres `System.Diagnostics.Debug`.  
  
## Vea también  
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)
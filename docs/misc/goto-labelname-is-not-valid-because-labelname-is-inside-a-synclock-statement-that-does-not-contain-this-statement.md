---
title: "&#39;GoTo &lt;nombreEtiqueta&gt;&#39; no es v&#225;lida porque &#39;&lt;nombreEtiqueta&#39; est&#225; dentro de una instrucci&#243;n &#39;SyncLock&#39; que no contiene esta instrucci&#243;n. | Microsoft Docs"
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
  - "bc30755"
  - "vbc30755"
helpviewer_keywords: 
  - "BC30755"
ms.assetid: 95fb48c1-4982-45fc-81f0-f30cf0df173f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;GoTo &lt;nombreEtiqueta&gt;&#39; no es v&#225;lida porque &#39;&lt;nombreEtiqueta&#39; est&#225; dentro de una instrucci&#243;n &#39;SyncLock&#39; que no contiene esta instrucci&#243;n.
No se puede bifurcar en un bloque `SyncLock`.  
  
 **Identificador de error:** BC30755  
  
### Para corregir este error  
  
-   Reestructure el código para que la etiqueta preceda al bloque `SyncLock`.  
  
## Vea también  
 [SyncLock \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/synclock-statement)
---
title: "Hora de sincronizaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.synchronization"
helpviewer_keywords: 
  - "Visualizador de simultaneidad, Hora de sincronización"
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Hora de sincronizaci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Estos segmentos de la escala de tiempo están asociados a tiempos de bloqueo que se clasifican como Sincronización.  Cuando un subproceso se marca como bloqueado en la sincronización, significa una de estas cosas:  
  
-   Puede que la ejecución del subproceso haya dado lugar a una llamada a una API de sincronización de subprocesos conocida, como `EnterCriticalSection()` o `WaitForSingleObject()`.  
  
-   El algoritmo de coincidencia de API no puede ser totalmente exhaustivo y, por consiguiente, podrían aparecer como sincronización algunas API que podrían estar asignadas a otras categorías, si se da el caso de que un marco de la pila de llamadas ha alcanzado un primitivo de bloqueo de un kernel subyacente que se había asignado a esta categoría.  
  
 Para entender la causa subyacente de un evento de bloqueo de subproceso, estudie atentamente las pilas de llamadas de bloqueo y los informes de perfil.  
  
## Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)
---
title: "Tiempo de suspensi&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.sleep"
helpviewer_keywords: 
  - "Visualizador de simultaneidad, Tiempo de suspensión"
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Tiempo de suspensi&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Estos segmentos de la escala de tiempo están asociados al tiempo de bloqueo que se clasifica como Suspensión.  La categoría de suspensión implica que un subproceso ha cedido voluntariamente a su núcleo lógico y no está realizando ningún trabajo.  Durante este período de tiempo, un subproceso se ha bloqueado en una API que el visualizador de simultaneidad identifica como Suspensión.  Las API como `Sleep()` y `SwitchToThread()` se incluyen en este grupo.  
  
## Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)
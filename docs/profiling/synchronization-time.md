---
title: Hora de sincronización | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f3236530c1a7b92fd1cba1bdd61e3e1c0973b58c
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35669254"
---
# <a name="synchronization-time"></a>Hora de sincronización
Estos segmentos de la escala de tiempo están asociados a tiempos de bloqueo que se clasifican como Sincronización. Cuando un subproceso se marca como bloqueado en la sincronización, se presupone una de estas cosas:  
  
-   La ejecución del subproceso puede haber producido una llamada a una API de sincronización de subproceso bien conocida como `EnterCriticalSection()` o `WaitForSingleObject()`.  
  
-   El algoritmo de coincidencia de la API no puede ser totalmente exhaustivo y, por tanto, algunas API que se podrían asignar a otras categorías también pueden aparecer como sincronización, porque un marco de la pila de llamadas ha alcanzado finalmente a una primitiva de bloqueo de kernel subyacente que estaba asignada a esta categoría.  
  
 Para entender la causa subyacente de un evento de bloqueo de subprocesos, examine con cuidado las pilas de llamadas de bloqueo y los informes de perfil.  
  
## <a name="see-also"></a>Vea también  
 [Vista Subprocesos](../profiling/threads-view-parallel-performance.md)
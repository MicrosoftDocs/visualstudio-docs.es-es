---
title: Hora de sincronización | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b1ca6b7a0d6e7f7c3be41bb091674a3526edf53
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582381"
---
# <a name="synchronization-time"></a>Hora de sincronización
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [tiempo de sincronización](https://docs.microsoft.com/visualstudio/profiling/synchronization-time).  
  
Estos segmentos de la escala de tiempo están asociados a tiempos de bloqueo que se clasifican como Sincronización. Cuando un subproceso se marca como bloqueado en la sincronización, se presupone una de estas cosas:  
  
-   La ejecución del subproceso puede haber producido una llamada a una API de sincronización de subproceso bien conocida como `EnterCriticalSection()` o `WaitForSingleObject()`.  
  
-   El algoritmo de coincidencia de la API no puede ser totalmente exhaustivo y, por tanto, algunas API que se podrían asignar a otras categorías también pueden aparecer como sincronización, porque un marco de la pila de llamadas ha alcanzado finalmente a una primitiva de bloqueo de kernel subyacente que estaba asignada a esta categoría.  
  
 Para entender la causa subyacente de un evento de bloqueo de subprocesos, examine con cuidado las pilas de llamadas de bloqueo y los informes de perfil.  
  
## <a name="see-also"></a>Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)




---
title: Tiempo de ejecución (vista de subprocesos) | Microsoft Docs
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
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b25048fdeeea6e1c5724ecc313993cbf74b617be
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579205"
---
# <a name="execution-time-threads-view"></a>Tiempo de ejecución (Vista de subprocesos)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [tiempo de ejecución (vista subprocesos)](https://docs.microsoft.com/visualstudio/profiling/execution-time-threads-view).  
  
Estos segmentos de la escala de tiempo de la vista de subprocesos representan el tiempo de ejecución, cuando el subproceso está realizando activamente una tarea en un núcleo lógico en el sistema.  
  
 Los cambios en el estado del subproceso se detectan mediante eventos de cambio de contexto de kernel. El seguimiento de eventos para Windows (ETW) captura pilas de muestras cada milisegundo. En un segmento verde muy corto, es posible que no se tome ninguna muestra. Por lo tanto, puede que algunos segmentos de ejecución cortos no muestren ninguna pila de llamadas.  
  
 Al hacer clic en un segmento de ejecución, el visualizador de simultaneidad muestra la pila de muestras más cercana a la ubicación del clic. La ubicación de esa pila de muestras se indica mediante una flecha negra, o un símbolo de intercalación, sobre la escala de tiempo y la pila de muestras aparece en la pestaña **Actual**.  
  
 Para ver un perfil de muestreo tradicional para todos los segmentos de ejecución en la vista actual, haga clic en **Ejecución** en el perfil de escala de tiempo visible.  
  
## <a name="see-also"></a>Vea también  
 [Informe del perfil de ejecución](../profiling/execution-profile-report.md)   
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)




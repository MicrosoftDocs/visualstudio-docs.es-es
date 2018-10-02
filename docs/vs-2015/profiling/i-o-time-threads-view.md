---
title: Tiempo de E/S (Vista de subprocesos) | Microsoft Docs
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
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d25512da43fc32b42c2a1f79e3c8dbe992ea30ce
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582268"
---
# <a name="io-time-threads-view"></a>Tiempo de E/S (Vista de subprocesos)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [e/s (vista subprocesos) tiempo](https://docs.microsoft.com/visualstudio/profiling/i-o-time-threads-view).  
  
Estos segmentos de la escala de tiempo están asociados a tiempos de bloqueo que se clasifican como E/S. Esto significa que un subproceso está esperando a que una operación de E/S finalice. El subproceso puede haberse bloqueado en una API o en una espera de kernel relacionada con una operación de E/S que el visualizador de simultaneidad identifica como E/S. Las API como `CreateFile()`, `ReadFile()`, y `WSARecv()` se incluyen en este grupo.  
  
## <a name="see-also"></a>Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)




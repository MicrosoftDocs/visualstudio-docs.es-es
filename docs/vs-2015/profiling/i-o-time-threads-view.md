---
title: Tiempo de E/S (Vista de subprocesos) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 55050ad6ed805c2996cfc52561b17e2614a6ee12
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236800"
---
# <a name="io-time-threads-view"></a>Tiempo de E/S (Vista de subprocesos)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Estos segmentos de la escala de tiempo están asociados a tiempos de bloqueo que se clasifican como E/S. Esto significa que un subproceso está esperando a que una operación de E/S finalice. El subproceso puede haberse bloqueado en una API o en una espera de kernel relacionada con una operación de E/S que el visualizador de simultaneidad identifica como E/S. Las API como `CreateFile()`, `ReadFile()`, y `WSARecv()` se incluyen en este grupo.  
  
## <a name="see-also"></a>Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)




---
title: Tiempo de E/S (Vista de subprocesos) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf64339f25e392d4e5790673d77d078b84d02c7c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826616"
---
# <a name="io-time-threads-view"></a>Tiempo de E/S (Vista de subprocesos)
Estos segmentos de la escala de tiempo están asociados a tiempos de bloqueo que se clasifican como E/S. Esto significa que un subproceso está esperando a que una operación de E/S finalice. El subproceso puede haberse bloqueado en una API o en una espera de kernel relacionada con una operación de E/S que el visualizador de simultaneidad identifica como E/S. Las API como `CreateFile()`, `ReadFile()`, y `WSARecv()` se incluyen en este grupo.  
  
## <a name="see-also"></a>Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)
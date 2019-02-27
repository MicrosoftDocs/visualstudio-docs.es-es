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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d7ba29383ddddc02160967a90b56046128d2f19
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56625457"
---
# <a name="io-time-threads-view"></a>Tiempo de E/S (Vista de subprocesos)
Estos segmentos de la escala de tiempo están asociados a tiempos de bloqueo que se clasifican como E/S. Esto significa que un subproceso está esperando a que una operación de E/S finalice. El subproceso puede haberse bloqueado en una API o en una espera de kernel relacionada con una operación de E/S que el visualizador de simultaneidad identifica como E/S. Las API como `CreateFile()`, `ReadFile()`, y `WSARecv()` se incluyen en este grupo.

## <a name="see-also"></a>Vea también
- [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)
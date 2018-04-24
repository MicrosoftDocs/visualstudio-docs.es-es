---
title: Tiempo de suspensión | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b9a3894097c553d8505fd61f15fbdec8c188e79
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="sleep-time"></a>Tiempo de suspensión
Estos segmentos de la escala de tiempo se asocian al tiempo de bloqueo que se clasifica como Suspensión. La categoría de suspensión implica que un subproceso ha renunciado voluntariamente a su núcleo lógico y no está realizando ningún trabajo. Durante este tiempo, un subproceso se ha bloqueado en una API que el visualizador de simultaneidad está contando como Suspensión. Las API como `Sleep()` y `SwitchToThread()` se incluyen en este grupo.  
  
## <a name="see-also"></a>Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)
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
ms.openlocfilehash: b94b1695eb36aa8f55847c21a14d72357d51a405
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35669519"
---
# <a name="sleep-time"></a>Tiempo de suspensión
Estos segmentos de la escala de tiempo se asocian al tiempo de bloqueo que se clasifica como Suspensión. La categoría de suspensión implica que un subproceso ha renunciado voluntariamente a su núcleo lógico y no está realizando ningún trabajo. Durante este tiempo, un subproceso se ha bloqueado en una API que el visualizador de simultaneidad está contando como Suspensión. Las API como `Sleep()` y `SwitchToThread()` se incluyen en este grupo.  
  
## <a name="see-also"></a>Vea también  
 [Vista Subprocesos](../profiling/threads-view-parallel-performance.md)
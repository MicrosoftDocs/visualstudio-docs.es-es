---
title: Tiempo de suspensión | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be2d566228367e2cdb07aecc2d73eaf82a6d961f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56637690"
---
# <a name="sleep-time"></a>Tiempo de suspensión
Estos segmentos de la escala de tiempo se asocian al tiempo de bloqueo que se clasifica como Suspensión. La categoría de suspensión implica que un subproceso ha renunciado voluntariamente a su núcleo lógico y no está realizando ningún trabajo. Durante este tiempo, un subproceso se ha bloqueado en una API que el visualizador de simultaneidad está contando como Suspensión. Las API como `Sleep()` y `SwitchToThread()` se incluyen en este grupo.

## <a name="see-also"></a>Vea también
- [Vista Subprocesos](../profiling/threads-view-parallel-performance.md)
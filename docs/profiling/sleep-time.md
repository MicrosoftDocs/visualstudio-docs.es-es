---
title: Tiempo de suspensión | Microsoft Docs
description: Obtenga más información sobre el hecho de que la categoría de suspensión implica que un subproceso ha renunciado voluntariamente a su núcleo lógico y no está realizando ningún trabajo.
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
ms.openlocfilehash: e66e62c2f7d78003581b12121844090c9754c2cc
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720064"
---
# <a name="sleep-time"></a>Tiempo de suspensión
Estos segmentos de la escala de tiempo se asocian al tiempo de bloqueo que se clasifica como Suspensión. La categoría de suspensión implica que un subproceso ha renunciado voluntariamente a su núcleo lógico y no está realizando ningún trabajo. Durante este tiempo, un subproceso se ha bloqueado en una API que el visualizador de simultaneidad está contando como Suspensión. Las API como `Sleep()` y `SwitchToThread()` se incluyen en este grupo.

## <a name="see-also"></a>Vea también
- [Vista Subprocesos](../profiling/threads-view-parallel-performance.md)
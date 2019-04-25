---
title: Tiempo de suspensión | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8a79bbca9f6275f115105cc2ba6b001ac0ca7d44
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54774625"
---
# <a name="sleep-time"></a>Tiempo de suspensión
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Estos segmentos de la escala de tiempo se asocian al tiempo de bloqueo que se clasifica como Suspensión. La categoría de suspensión implica que un subproceso ha renunciado voluntariamente a su núcleo lógico y no está realizando ningún trabajo. Durante este tiempo, un subproceso se ha bloqueado en una API que el visualizador de simultaneidad está contando como Suspensión. Las API como `Sleep()` y `SwitchToThread()` se incluyen en este grupo.  
  
## <a name="see-also"></a>Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)

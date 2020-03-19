---
title: Tiempo de adelantamiento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de7a02f7247e09876bc4598d44fc1c395161ebc2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "62935898"
---
# <a name="preemption-time"></a>Tiempo de adelantamiento
Estos segmentos de la escala de tiempo están asociados al tiempo de bloqueo que se clasifica como Adelantamiento. Esta categoría implica que se sale de un subproceso debido a una de estas razones:

- El programador lo reemplazó utilizando un subproceso de prioridad más alta.

- El cuanto de ejecución del subproceso expiró y había otros subprocesos listos para ejecutarse.

  Durante este tiempo, una razón de espera de kernel ha bloqueado un subproceso que el Visualizador de simultaneidad está contando como adelantamiento. Los segmentos de adelantamiento se inician cuando un subproceso se expulsa de un núcleo lógico y termina cuando ese subproceso reanuda la ejecución.

  La información sobre herramientas de un segmento preferente muestra el nombre del proceso o subproceso que produjo el adelantamiento. Sin embargo, esto no implica que el proceso o subproceso que se adelantó se ejecutara durante todo el período de adelantamiento.

## <a name="see-also"></a>Vea también
- [Vista Subprocesos](../profiling/threads-view-parallel-performance.md)
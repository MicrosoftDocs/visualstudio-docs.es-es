---
title: Tiempo de adelantamiento | Microsoft Docs
description: Obtenga más información sobre el tiempo de adelantamiento y profundice en el hecho de que estos segmentos de la escala de tiempo están asociados al tiempo de bloqueo que se clasifica como adelantamiento.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b8515043b228deb4fbcbf43c0e75b9826912f059
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957327"
---
# <a name="preemption-time"></a>Tiempo de adelantamiento
Estos segmentos de la escala de tiempo están asociados al tiempo de bloqueo que se clasifica como Adelantamiento. Esta categoría implica que se sale de un subproceso debido a una de estas razones:

- El programador lo reemplazó utilizando un subproceso de prioridad más alta.

- El cuanto de ejecución del subproceso expiró y había otros subprocesos listos para ejecutarse.

  Durante este tiempo, una razón de espera de kernel ha bloqueado un subproceso que el Visualizador de simultaneidad está contando como adelantamiento. Los segmentos de adelantamiento se inician cuando un subproceso se expulsa de un núcleo lógico y termina cuando ese subproceso reanuda la ejecución.

  La información sobre herramientas de un segmento preferente muestra el nombre del proceso o subproceso que produjo el adelantamiento. Sin embargo, esto no implica que el proceso o subproceso que se adelantó se ejecutara durante todo el período de adelantamiento.

## <a name="see-also"></a>Vea también
- [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)
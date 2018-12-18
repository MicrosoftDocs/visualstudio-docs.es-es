---
title: Tiempo de adelantamiento | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d0959f5e2725401424d0231ccd286b7835a7315
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894396"
---
# <a name="preemption-time"></a>Tiempo de adelantamiento
Estos segmentos de la escala de tiempo están asociados al tiempo de bloqueo que se clasifica como Adelantamiento. Esta categoría implica que se sale de un subproceso debido a una de estas razones:  
  
- El programador lo reemplazó utilizando un subproceso de prioridad más alta.  
  
- El cuanto de ejecución del subproceso expiró y había otros subprocesos listos para ejecutarse.  
  
  Durante este tiempo, una razón de espera de kernel ha bloqueado un subproceso que el Visualizador de simultaneidad está contando como adelantamiento. Los segmentos de adelantamiento se inician cuando un subproceso se expulsa de un núcleo lógico y termina cuando ese subproceso reanuda la ejecución.  
  
  La información sobre herramientas de un segmento preferente muestra el nombre del proceso o subproceso que produjo el adelantamiento. Sin embargo, esto no implica que el proceso o subproceso que se adelantó se ejecutara durante todo el período de adelantamiento.  
  
## <a name="see-also"></a>Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)
---
title: Tiempo de adelantamiento | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e1ddd0f239317021d38017ec159de46ecbc2aa77
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721400"
---
# <a name="preemption-time"></a>Tiempo de adelantamiento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Estos segmentos de la escala de tiempo están asociados al tiempo de bloqueo que se clasifica como Adelantamiento. Esta categoría implica que se sale de un subproceso debido a una de estas razones:  
  
- El programador lo reemplazó utilizando un subproceso de prioridad más alta.  
  
- El cuanto de ejecución del subproceso expiró y había otros subprocesos listos para ejecutarse.  
  
  Durante este tiempo, una razón de espera de kernel ha bloqueado un subproceso que el Visualizador de simultaneidad está contando como adelantamiento. Los segmentos de adelantamiento se inician cuando un subproceso se expulsa de un núcleo lógico y termina cuando ese subproceso reanuda la ejecución.  
  
  La información sobre herramientas de un segmento preferente muestra el nombre del proceso o subproceso que produjo el adelantamiento. Sin embargo, esto no implica que el proceso o subproceso que se adelantó se ejecutara durante todo el período de adelantamiento.  
  
## <a name="see-also"></a>Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)




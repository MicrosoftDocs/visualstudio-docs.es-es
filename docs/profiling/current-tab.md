---
title: Pestaña Actual | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.reportnav.current
helpviewer_keywords:
- Concurrency Visualizer, Callstack at Selection Point
ms.assetid: 2c7b1ae5-3756-4795-bc59-f6bb113f2ba5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7855ddd258faf6b5c7b4b7825a67171d0fce0818
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="current-tab"></a>Pestaña actual
Si hace clic en la pestaña **Actual**, puede ver una pila de llamadas (si está disponible) que está más cerca del punto de selección actual en la escala de tiempo si se selecciona un segmento de subproceso de CPU.  En este caso, el punto de selección se representa mediante una flecha negra, o un símbolo de intercalación, sobre la escala de tiempo. Cuando se selecciona un segmento de bloqueo, el símbolo de intercalación no se muestra porque no se ha producido ninguna ejecución. Sin embargo, el segmento todavía está resaltado y se muestra una pila de llamadas.  
  
 En la pestaña **Actual** también se muestra información sobre los segmentos de actividad de DirectX, marcadores y acceso de E/S.  Para los segmentos de actividad de DirectX, se muestra información sobre la forma en que la cola de hardware procesa los paquetes DMA.  Para los marcadores, se muestra información sobre la descripción y el tipo de marcador.  Para el acceso de E/S, se muestra información sobre el archivo y el número de bytes leídos o escritos.  
  
## <a name="see-also"></a>Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)
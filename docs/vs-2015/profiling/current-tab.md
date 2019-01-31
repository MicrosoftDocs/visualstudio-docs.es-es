---
title: Pestaña Actual | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.reportnav.current
helpviewer_keywords:
- Concurrency Visualizer, Callstack at Selection Point
ms.assetid: 2c7b1ae5-3756-4795-bc59-f6bb113f2ba5
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b3c901803d8ab2b35624d185e62588c72a3586ca
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54787909"
---
# <a name="current-tab"></a>Pestaña actual
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si hace clic en la pestaña **Actual**, puede ver una pila de llamadas (si está disponible) que está más cerca del punto de selección actual en la escala de tiempo si se selecciona un segmento de subproceso de CPU.  En este caso, el punto de selección se representa mediante una flecha negra, o un símbolo de intercalación, sobre la escala de tiempo. Cuando se selecciona un segmento de bloqueo, el símbolo de intercalación no se muestra porque no se ha producido ninguna ejecución. Sin embargo, el segmento todavía está resaltado y se muestra una pila de llamadas.  
  
 En la pestaña **Actual** también se muestra información sobre los segmentos de actividad de DirectX, marcadores y acceso de E/S.  Para los segmentos de actividad de DirectX, se muestra información sobre la forma en que la cola de hardware procesa los paquetes DMA.  Para los marcadores, se muestra información sobre la descripción y el tipo de marcador.  Para el acceso de E/S, se muestra información sobre el archivo y el número de bytes leídos o escritos.  
  
## <a name="see-also"></a>Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)

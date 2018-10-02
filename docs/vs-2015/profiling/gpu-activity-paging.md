---
title: Actividad de GPU (paginación) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c11bd0fd8f348ff90e95660e5df03a4aa591d96
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567314"
---
# <a name="gpu-activity-paging"></a>Actividad de GPU (Paginación)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [actividad GPU (paginación)](https://docs.microsoft.com/visualstudio/profiling/gpu-activity-paging).  
  
Los segmentos **Actividad de GPU (paginación)** en la pestaña Subprocesos representan los momentos en que la GPU estaba procesando solicitudes de paginación.  La longitud de un segmento representa la cantidad de tiempo que la GPU estuvo procesando un paquete de paginación de acceso a memoria directa (DMA). Normalmente, los paquetes de paginación se asocian a la transferencia de memoria entre la CPU y la GPU.  
  
 Al seleccionar este tipo de segmento de paginación de GPU, el informe en la pestaña **Actual** muestra información sobre el paquete de DMA que se procesó. La información incluye la cantidad de tiempo que ha esperado en la cola de hardware asociada al motor de DirectX, el proceso que envió el paquete de DMA y el tiempo necesario para procesar el paquete.  
  
## <a name="see-also"></a>Vea también  
 [Vista de uso](../profiling/utilization-view.md)




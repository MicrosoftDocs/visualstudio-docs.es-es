---
title: Actividad de GPU (paginación) | Microsoft Docs
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
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 015fa34d2bb87cf98a64fb3431a6440202cf729b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195863"
---
# <a name="gpu-activity-paging"></a>Actividad de GPU (Paginación)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los segmentos **Actividad de GPU (paginación)** en la pestaña Subprocesos representan los momentos en que la GPU estaba procesando solicitudes de paginación.  La longitud de un segmento representa la cantidad de tiempo que la GPU estuvo procesando un paquete de paginación de acceso a memoria directa (DMA). Normalmente, los paquetes de paginación se asocian a la transferencia de memoria entre la CPU y la GPU.  
  
 Al seleccionar este tipo de segmento de paginación de GPU, el informe en la pestaña **Actual** muestra información sobre el paquete de DMA que se procesó. La información incluye la cantidad de tiempo que ha esperado en la cola de hardware asociada al motor de DirectX, el proceso que envió el paquete de DMA y el tiempo necesario para procesar el paquete.  
  
## <a name="see-also"></a>Vea también  
 [Vista de uso](../profiling/utilization-view.md)




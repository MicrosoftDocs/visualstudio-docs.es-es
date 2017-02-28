---
title: "Actividad de GPU (paginación) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 10a4f9a0c83e18da6fb9f45a2ac4fded913d2723
ms.lasthandoff: 02/22/2017

---
# <a name="gpu-activity-paging"></a>Actividad de GPU (Paginación)
Los segmentos **Actividad de GPU (paginación)** en la pestaña Subprocesos representan los momentos en que la GPU estaba procesando solicitudes de paginación.  La longitud de un segmento representa la cantidad de tiempo que la GPU estuvo procesando un paquete de paginación de acceso a memoria directa (DMA). Normalmente, los paquetes de paginación se asocian a la transferencia de memoria entre la CPU y la GPU.  
  
 Al seleccionar este tipo de segmento de paginación de GPU, el informe en la pestaña **Actual** muestra información sobre el paquete de DMA que se procesó. La información incluye la cantidad de tiempo que ha esperado en la cola de hardware asociada al motor de DirectX, el proceso que envió el paquete de DMA y el tiempo necesario para procesar el paquete.  
  
## <a name="see-also"></a>Vea también  
 [Vista de uso](../profiling/utilization-view.md)

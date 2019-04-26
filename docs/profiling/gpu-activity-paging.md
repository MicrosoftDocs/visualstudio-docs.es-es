---
title: Actividad de GPU (paginación) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8bd28c7b41a01992ad52fa343b098b0a02460806
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969620"
---
# <a name="gpu-activity-paging"></a>Actividad de GPU (Paginación)
Los segmentos **Actividad de GPU (paginación)** en la pestaña **Subprocesos**  representan los momentos en que la GPU estaba procesando solicitudes de paginación.  La longitud de un segmento representa la cantidad de tiempo que la GPU estuvo procesando un paquete de paginación de acceso a memoria directa (DMA). Normalmente, los paquetes de paginación se asocian a la transferencia de memoria entre la CPU y la GPU.

 Al seleccionar este tipo de segmento de paginación de GPU, el informe en la pestaña **Actual** muestra información sobre el paquete de DMA que se procesó. La información incluye la cantidad de tiempo que ha esperado en la cola de hardware asociada al motor de DirectX, el proceso que envió el paquete de DMA y el tiempo necesario para procesar el paquete.

## <a name="see-also"></a>Vea también
- [Vista Utilización](../profiling/utilization-view.md)